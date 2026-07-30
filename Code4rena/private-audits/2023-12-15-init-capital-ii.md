---
sponsor: "INIT Capital"
slug: "2023-12-initcapital"
date: "2024-01-16"
title: "INIT Capital Invitational"
findings: "https://github.com/code-423n4/2023-12-initcapital-findings/issues"
contest: 313
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the INIT Capital smart contract system written in Solidity. The audit took place between December 15—December 21 2023.

## Wardens

In Code4rena's Invitational audits, the competition is limited to a small group of wardens; for this audit, 5 wardens contributed reports to INIT Capital:

  1. [said](https://code4rena.com/@said)
  2. [0x73696d616f](https://code4rena.com/@0x73696d616f)
  3. [ladboy233](https://code4rena.com/@ladboy233)
  4. [rvierdiiev](https://code4rena.com/@rvierdiiev)
  5. [sashik\_eth](https://code4rena.com/@sashik_eth)

This audit was judged by [hansfriese](https://code4rena.com/@hansfriese).

Final report assembled by PaperParachute.

# Summary

The C4 analysis yielded an aggregated total of 15 unique vulnerabilities. Of these vulnerabilities, 3 received a risk rating in the category of HIGH severity and 12 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 3 reports detailing issues with a risk rating of LOW severity or non-critical. There were also 2 reports recommending gas optimizations.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 INIT Capital repository](https://github.com/code-423n4/2023-12-initcapital), and is composed of 17 smart contracts written in the Solidity programming language and includes 1545 lines of Solidity code.

In addition to the known issues identified by the project team, an [Automated Findings report](https://github.com/code-423n4/2023-12-initcapital/blob/main/4naly3er-report.md) was generated using the [4naly3er bot](https://github.com/Picodes/4naly3er) and all findings therein were classified as out of scope.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (3)
## [[H-01] Liquidations can be prevented by frontrunning and liquidating 1 debt (or more) due to wrong assumption in POS\_MANAGER](https://github.com/code-423n4/2023-12-initcapital-findings/issues/42)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/42)*

Users can avoid being liquidated if they frontrun liquidation calls with a liquidate call with 1 wei. Or, they may do a partial liquidation and avoid being liquidated before the interest reaches the value of the debt pre liquidation. The total interest stored in `__posBorrInfos[_posId].borrExtraInfos[_pool].totalInterest` would also be wrong.

### Proof of Concept

The `POS_MANAGER` stores the total interest in `__posBorrInfos[_posId].borrExtraInfos[_pool].totalInterest`. Function `updatePosDebtShares()` [assumes](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/PosManager.sol#L175) that `ILendingPool(_pool).debtShareToAmtCurrent(currDebtShares)` is always increasing, but this is not the case, as a liquidation may happen that reduces the current debt amount. This leads to calls to `updatePosDebtShares()` reverting.

The most relevant is when liquidating, such that users could liquidate themselves for small amounts (1) and prevent liqudiations in the same block. This is because the debt accrual happens over time, so if the block.timestamp is the same, no debt accrual will happen. Thus, if a liquidate call with 1 amount frontruns a liquidate call with any amount, the second call will revert.

A user could still stop liquidations for as long as the accrued interest doesn't reach the last debt value before liquidation, if the user liquidated a bigger part of the debt.

Add the following test to `TestInitCore.sol`:

```solidity
function test_POC_Liquidate_reverts_frontrunning_PosManager_WrongAssumption() public {
    address poolUSDT = address(lendingPools[USDT]);
    address poolWBTC = address(lendingPools[WBTC]);
    _setTargetHealthAfterLiquidation_e18(1, type(uint64).max); // by pass max health after liquidate capped
    _setFixedRateIRM(poolWBTC, 0.1e18); // 10% per sec

    uint collAmt;
    uint borrAmt;

    {
        uint collUSD = 100_000;
        uint borrUSDMax = 80_000;
        collAmt = _priceToTokenAmt(USDT, collUSD);
        borrAmt = _priceToTokenAmt(WBTC, borrUSDMax);
    }

    address liquidator = BOB;
    deal(USDT, ALICE, collAmt);
    deal(WBTC, liquidator, borrAmt * 2);

    // provides liquidity for borrow
    _fundPool(poolWBTC, borrAmt);

    // create position and collateralize
    uint posId = _createPos(ALICE, ALICE, 1);
    _collateralizePosition(ALICE, posId, poolUSDT, collAmt, bytes(''));

    // borrow
    _borrow(ALICE, posId, poolWBTC, borrAmt, bytes(''));

    // fast forward time and accrue interest
    vm.warp(block.timestamp + 1 seconds);
    ILendingPool(poolWBTC).accrueInterest();

    uint debtShares = positionManager.getPosDebtShares(posId, poolWBTC);

    _liquidate(liquidator, posId, 1, poolWBTC, poolUSDT, false, bytes(''));

    // liquidate all debtShares
    _liquidate(liquidator, posId, 1000, poolWBTC, poolUSDT, false, bytes('panic'));
}
```

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Update the user's last debt position `__posBorrInfos[_posId].borrExtraInfos[_pool].totalInterest` on `_repay()`.

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/42#issuecomment-1872425149)**


**[hansfriese (Judge) commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/42#issuecomment-1872433152):**
 > After discussing internally with the sponsor/warden, we've confirmed the issue.
> Here is a part of the discussion:
> 
> > "When it frontruns the liquidation with 1 share, it removes 1 share and 2 debt.<br>
> > When it calculates the amount again in the following liquidation, the shares will be worth 1 less and it reverts."
> 
> As a mitigation, we can update `extraInfo.totalInterest` only when [debtAmtCurrent > extraInfo.lastDebtAmt](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/core/PosManager.sol#L176).
>
 > ![image](https://github.com/code-423n4/2023-12-initcapital-findings/assets/45533148/c1bd109c-4c8e-4683-b559-055128efb64f)
> 
 > High is appropriate as the main invariant might be broken temporarily while repaying.

***

## [[H-02] wLp tokens could be stolen ](https://github.com/code-423n4/2023-12-initcapital-findings/issues/31)
*Submitted by [sashik\_eth](https://github.com/code-423n4/2023-12-initcapital-findings/issues/31), also found by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/24)*

`PosManager#removeCollateralWLpTo` function allows users to remove collateral wrapped in a wLp token that was previously supplied to the protocol:

```solidity
File: PosManager.sol
249:     function removeCollateralWLpTo(uint _posId, address _wLp, uint _tokenId, uint _amt, address _receiver)
250:         external
251:         onlyCore
252:         returns (uint)
253:     {
254:         PosCollInfo storage posCollInfo = __posCollInfos[_posId];
255:         // NOTE: balanceOfLp should be 1:1 with amt
256:         uint newWLpAmt = IBaseWrapLp(_wLp).balanceOfLp(_tokenId) - _amt;
257:         if (newWLpAmt == 0) { 
258:             _require(posCollInfo.ids[_wLp].remove(_tokenId), Errors.NOT_CONTAIN);
259:             posCollInfo.collCount -= 1;
260:             if (posCollInfo.ids[_wLp].length() == 0) {
261:                 posCollInfo.wLps.remove(_wLp);
262:             }
263:             isCollateralized[_wLp][_tokenId] = false;
264:         }
265:         _harvest(_posId, _wLp, _tokenId);
266:         IBaseWrapLp(_wLp).unwrap(_tokenId, _amt, _receiver);
267:         return _amt;
268:     }
```

This function could be called only from the core contract using the `decollateralizeWLp` and `liquidateWLp` functions. However, it fails to check if the specified `tokenId` belongs to the current position, this check would take place only if removing is full - meaning no lp tokens remain wrapped in the wLp (line 257).

This would allow anyone to drain any other positions with supplied wLp tokens. The attacker only needs to create its own position, supply dust amount in wLp to it, and call `decollateralizeWLp` with the desired 'tokenId', also withdrawn amount should be less than the full wLp balance to prevent check on line 257. An attacker would receive almost all lp tokens and accrued rewards from the victim's wLp.

A similar attack for harvesting the victim's rewards could be done through the `liquidateWLp` function.

### Impact

Attacker could drain any wLp token and harvest all accrued rewards for this token.

### Proof of Concept

The next test added to the `tests/wrapper/TestWLp.sol` file could show an exploit scenario:

```solidity
    function testExploitStealWlp() public {
        uint victimAmt = 100000000;
        // Bob open position with 'tokenId' 1
        uint bobPosId = _openPositionWithLp(BOB, victimAmt);
        // Alice open position with 'tokenId' 2 and dust amount 
        uint alicePosId = _openPositionWithLp(ALICE, 1);
        // Alice successfully de-collateralizes her own position using Bob's 'tokenId' and amounts less than Bob's position by 1 to prevent a revert
        vm.startPrank(ALICE, ALICE);
        initCore.decollateralizeWLp(alicePosId, address(mockWLpUniV2), 1, victimAmt - 1, ALICE);
        vm.stopPrank();

        emit log_uint(positionManager.getCollWLpAmt(bobPosId, address(mockWLpUniV2), 1));
        emit log_uint(IERC20(lp).balanceOf(ALICE));
    }

```

### Recommended Mitigation Steps

Consider adding a check that position holds the specified token into the `removeCollateralWLpTo` function:

```solidity
_require(__posCollInfos[_posId].ids[_wlp].contains(_tokenId), Errors.NOT_CONTAIN);
```

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/31#issuecomment-1870313456)**

***

## [[H-03] `_handleRepay` of `MoneyMarketHook` does not consider the actual debt shares of the `posId` inside the position manager and could lead to a user's tokens getting stuck inside the hook](https://github.com/code-423n4/2023-12-initcapital-findings/issues/28)
*Submitted by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/28)*

When users construct repay operations via `MoneyMarketHook`, it doesn't consider the actual debt shares of the position inside the `InitCore` and `PosManager`. This could lead to users' tokens getting stuck inside the `MoneyMarketHook` contract.

### Proof of Concept

When users want to repay his positions in `MoneyMarketHook`, they can provide the parameters inside `repayParams`, and `MoneyMarketHook` will construct the operation via `_handleRepay` function.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L145-L159>

```solidity
    function _handleRepay(uint _offset, bytes[] memory _data, uint _initPosId, RepayParams[] memory _params)
        internal
        returns (uint, bytes[] memory)
    {
        for (uint i; i < _params.length; i = i.uinc()) {
            address uToken = ILendingPool(_params[i].pool).underlyingToken();
>>>         uint repayAmt = ILendingPool(_params[i].pool).debtShareToAmtCurrent(_params[i].shares);
            _ensureApprove(uToken, repayAmt);
>>>         IERC20(uToken).safeTransferFrom(msg.sender, address(this), repayAmt);
            _data[_offset] =
                abi.encodeWithSelector(IInitCore.repay.selector, _params[i].pool, _params[i].shares, _initPosId);
            _offset = _offset.uinc();
        }
        return (_offset, _data);
    }
```

It can be observed that it calculates the `repayAmt` based on the shares provided by the users and transfers the corresponding amount of tokens from the sender to the hook. However, the actual debt shares of the position can be less than the `_params[i].shares` provided by users. This means that the actual repay amount of tokens needed could be less than the calculated `repayAmt`.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L530-L551>

```solidity
    function _repay(IConfig _config, uint16 _mode, uint _posId, address _pool, uint _shares)
        internal
        returns (address tokenToRepay, uint amt)
    {
        // check status
        _require(_config.getPoolConfig(_pool).canRepay && _config.getModeStatus(_mode).canRepay, Errors.REPAY_PAUSED);
        // get position debt share
>>>     uint positionDebtShares = IPosManager(POS_MANAGER).getPosDebtShares(_posId, _pool);
>>>     uint sharesToRepay = _shares < positionDebtShares ? _shares : positionDebtShares;
        // get amtToRepay (accrue interest)
>>>     uint amtToRepay = ILendingPool(_pool).debtShareToAmtCurrent(sharesToRepay);
        // take token from msg.sender to pool
        tokenToRepay = ILendingPool(_pool).underlyingToken();
>>>     IERC20(tokenToRepay).safeTransferFrom(msg.sender, _pool, amtToRepay);
        // update debt on the position
        IPosManager(POS_MANAGER).updatePosDebtShares(_posId, _pool, -sharesToRepay.toInt256());
        // call repay on the pool
        amt = ILendingPool(_pool).repay(sharesToRepay);
        // update debt on mode
        IRiskManager(riskManager).updateModeDebtShares(_mode, _pool, -sharesToRepay.toInt256());
        emit Repay(_pool, _posId, msg.sender, _shares, amt);
    }
```

Consider a scenario where the user's positions are currently liquidatable, and the user wishes to repay all of the position's debt inside the `MoneyMarketHook`. However, a liquidator front-runs the operation by liquidating the user's position. Now, when the repayment operation executes from `MoneyMarketHook`, it transfers the `repayAmt` to the `MoneyMarketHook` but the amount is not used/fully utilized and becomes stuck inside the contract.

### Recommended Mitigation Steps

Consider to also check the provided shares against the actual debt shares inside the `InitCore`/`PosManager`.

**[fez-init (INIT) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/28#issuecomment-1870322481):**
 > The issue should be medium, since the funds cannot be retrieved by someone else. The hook will be upgradeable, so if funds actually get stuck, it is still retrievable.

**[hansfriese (Judge) commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/28#issuecomment-1871745239):**
 > I agree that this issue is in the middle of Medium and High.
> Users might face a temporary lock on their funds, and the hook should be upgraded every time to unlock them.
>
> Given the high probability of this scenario occurring, I will keep this issue as a valid High.


***
 
# Medium Risk Findings (12)
## [[M-01] repay(), liquidate() and liquidateWLp() receive shares as argument, which may revert if from approval to tx settled blocks have passed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/38)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/38)*

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L151> 

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L282> 

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L317>

`repay()`, `liquidate()` and `liquidateWLp()` transactions revert if users approve the exact repay amount they need in the frontend and only after some blocks have passed is the transaction settled. This happens because the interest accrual is by timestamp, so the debt would have increased since the approval, when the transaction settles.

### Proof of Concept

A test when repaying debt was carried out in `TestInitCore.sol`. The timestamp increased just 1 second, but it was enough to make the transaction revert. It may be possible to request a bigger alowance than expected, but this has other implications.

```solidity
function test_POC_TransferFromFails_DueToDebtAccrual() public {
    uint256 _wbtcAmount = 3e8;
    uint256 _borrowAmount = 1e8;
    address _user = makeAddr("user");
    deal(WBTC, _user, _wbtcAmount);
    
    uint256 _posId = _createPos(_user, _user, 2);
    uint256 shares_ = _mintPool(_user, address(lendingPools[WBTC]), _wbtcAmount, "");
    vm.startPrank(_user);
    lendingPools[WBTC].transfer(address(positionManager), shares_);
    initCore.collateralize(_posId, address(lendingPools[WBTC]));
    vm.stopPrank();

    uint256 _debtShares = _borrow(_user, _posId, address(lendingPools[WBTC]), _borrowAmount, "");

    uint256 _userDebtBalance = lendingPools[WBTC].debtShareToAmtCurrent(_debtShares);

    vm.prank(_user);
    IERC20(WBTC).approve(address(initCore), _userDebtBalance);

    skip(1); 

    vm.prank(_user);
    vm.expectRevert("ERC20: transfer amount exceeds balance");
    initCore.repay(address(lendingPools[WBTC]), _debtShares, _posId);
}
```

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Receive the amount in InitCore as argument instead of the shares on the `repay()`, `liquidate()` and `liquidateWLp()` functions.

**[fez-init (INIT) acknowledged and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/38#issuecomment-1871620933):**
 > The issue should be mitigated with the introduction of hooks, where such additional logic of amount to share conversion can be implemented. 

***

## [[M-02] Decimals of LendingPool don't take into account the offset introduced by VIRTUAL\_SHARES](https://github.com/code-423n4/2023-12-initcapital-findings/issues/36)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/36)*

The impact of this finding is more on the marketing/data fetching side, on exchanges it would appear that the shares are worth less `VIRTUAL_SHARES` than the underlying token. Given that it would influence the perception of the value of the shares token, medium severity seems appropriate.

### Proof of Concept

The Openzeppelin [implementation](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/ERC4626.sol#L106-L108) includes the decimals offset (log10(`VIRTUAL_SHARES`) in LendingPool) in the `decimals()` function. However, INIT only places the decimals of the [underlying](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/lending_pool/LendingPool.sol#L95-L97).

A POC was built, add it to `TestLendingPool.sol`:

```solidity
function test_POC_WrongDecimals() public {
    uint256 _wbtcAmount = 3e8; // 3 BTC
    address _user = makeAddr("user");
    _mintPool(_user, WBTC, _wbtcAmount);
    uint256 _wbtcDecimals = 1e8;
    uint256 VIRTUAL_SHARES = 1e8;
    uint256 _poolDecimals = 10**lendingPools[WBTC].decimals();
    uint256 _userBalance = lendingPools[WBTC].balanceOf(_user);
    assertEq(_userBalance/_poolDecimals, _wbtcAmount/_wbtcDecimals*VIRTUAL_SHARES);
    assertEq(_userBalance/_poolDecimals, 3e8);
    assertEq(_userBalance, _wbtcAmount*VIRTUAL_SHARES);
}
```

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Include the virtual shares decimals in the `decimals()` function:

```solidity
uint private constant VIRTUAL_SHARES = 8;
...
function decimals() public view override returns (uint8) {
    return IERC20Metadata(underlyingToken).decimals() + VIRTUAL_SHARES;
}
...
function _toShares(uint _amt, uint _totalAssets, uint _totalShares) internal pure returns (uint shares) {
    return _amt.mulDiv(_totalShares + 10**VIRTUAL_SHARES, _totalAssets + VIRTUAL_ASSETS);
}
...
function _toAmt(uint _shares, uint _totalAssets, uint _totalShares) internal pure returns (uint amt) {
    return _shares.mulDiv(_totalAssets + VIRTUAL_ASSETS, _totalShares + 10**VIRTUAL_SHARES);
}
```

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/36#issuecomment-1870338593)**


***

## [[M-03] When the `returnNative` parameter is set to true in the `_params` provided to `MoneyMarketHook.execute`, it is not handled properly and could disrupt user expectations](https://github.com/code-423n4/2023-12-initcapital-findings/issues/29)
*Submitted by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/29)*

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L168-L196> 

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L76-L80>

When `param.returnNative` is set to true while calling `MoneyMarketHook.execute`, users expect the returned token from the withdraw operation to be in native form and sent to the caller. However, in the current implementation, this is not considered and could disrupt user expectations.

### Proof of Concept

The withdraw functionality inside `MoneyMarketHook` will process the `WithdrawParams` provided by users and construct the operations using `_handleWithdraw`, which consist of calling `decollateralize` and `burnTo` in `InitCore`, providing the parameters accordingly.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L168-L196>

```solidity
    function _handleWithdraw(uint _offset, bytes[] memory _data, uint _initPosId, WithdrawParams[] calldata _params)
        internal
        view
        returns (uint, bytes[] memory)
    {
        for (uint i; i < _params.length; i = i.uinc()) {
            // decollateralize to pool
            _data[_offset] = abi.encodeWithSelector(
                IInitCore.decollateralize.selector, _initPosId, _params[i].pool, _params[i].shares, _params[i].pool
            );
            _offset = _offset.uinc();
            // burn collateral to underlying token
            address helper = _params[i].rebaseHelperParams.helper;
            address uTokenReceiver = _params[i].to;
            // if need to unwrap to rebase token
            if (helper != address(0)) {
                address uToken = ILendingPool(_params[i].pool).underlyingToken();
                _require(
                    _params[i].rebaseHelperParams.tokenIn == uToken
                        && IRebaseHelper(_params[i].rebaseHelperParams.helper).YIELD_BEARING_TOKEN() == uToken,
                    Errors.INVALID_TOKEN_IN
                );
                uTokenReceiver = helper;
            }
            _data[_offset] = abi.encodeWithSelector(IInitCore.burnTo.selector, _params[i].pool, uTokenReceiver);
            _offset = _offset.uinc();
        }
        return (_offset, _data);
    }
```

As it can be observed, `_handleWithdraw` doesn't check `param.returnNative` and not adjust the `uTokenReceiver` token receiver to `address(this)` when `param.returnNative` is set to true.

Now, when `execute` finish perform the multicall and check that `_params.returnNative` is set to true, it will not work properly as the token is not send to the Hook.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L76-L80>

```solidity
    function execute(OperationParams calldata _params)
        external
        payable
        returns (uint posId, uint initPosId, bytes[] memory results)
    {
        // create position if not exist
        if (_params.posId == 0) {
            (posId, initPosId) = createPos(_params.mode, _params.viewer);
        } else {
            // for existing position, only owner can execute
            posId = _params.posId;
            initPosId = initPosIds[msg.sender][posId];
            _require(IERC721(POS_MANAGER).ownerOf(initPosId) == address(this), Errors.NOT_OWNER);
        }
        results = _handleMulticall(initPosId, _params);
        // check slippage
        _require(_params.minHealth_e18 <= IInitCore(CORE).getPosHealthCurrent_e18(initPosId), Errors.SLIPPAGE_CONTROL);
        // unwrap token if needed
        for (uint i; i < _params.withdrawParams.length; i = i.uinc()) {
            address helper = _params.withdrawParams[i].rebaseHelperParams.helper;
            if (helper != address(0)) IRebaseHelper(helper).unwrap(_params.withdrawParams[i].to);
        }
        // return native token
        if (_params.returnNative) {
>>>         IWNative(WNATIVE).withdraw(IERC20(WNATIVE).balanceOf(address(this)));
>>>         (bool success,) = payable(msg.sender).call{value: address(this).balance}('');
            _require(success, Errors.CALL_FAILED);
        }
    }
```

This could disrupt user expectations. Consider a third-party contract integrated with this hook that can only operate using native balance, doesn't expect, and cannot handle tokens/ERC20. This can cause issues for the integrator.

### Recommended Mitigation Steps

When constructing withdraw operation, check if `_params.returnNative` is set to true, and change `uTokenReceiver` to `address(this`.

<details>

```diff
-    function _handleWithdraw(uint _offset, bytes[] memory _data, uint _initPosId, WithdrawParams[] calldata _params)
+    function _handleWithdraw(uint _offset, bytes[] memory _data, uint _initPosId, WithdrawParams[] calldata _params, bool _returnNative)
        internal
        view
        returns (uint, bytes[] memory)
    {
        for (uint i; i < _params.length; i = i.uinc()) {
            // decollateralize to pool
            _data[_offset] = abi.encodeWithSelector(
                IInitCore.decollateralize.selector, _initPosId, _params[i].pool, _params[i].shares, _params[i].pool
            );
            _offset = _offset.uinc();
            // burn collateral to underlying token
            address helper = _params[i].rebaseHelperParams.helper;
            address uTokenReceiver = _params[i].to;
            // if need to unwrap to rebase token
            if (helper != address(0)) {
                address uToken = ILendingPool(_params[i].pool).underlyingToken();
                _require(
                    _params[i].rebaseHelperParams.tokenIn == uToken
                        && IRebaseHelper(_params[i].rebaseHelperParams.helper).YIELD_BEARING_TOKEN() == uToken,
                    Errors.INVALID_TOKEN_IN
                );
                uTokenReceiver = helper;
            }
+            if (_returnNative && uToken == WNATIVE) {
+                uTokenReceiver = address(this);
+            }
            _data[_offset] = abi.encodeWithSelector(IInitCore.burnTo.selector, _params[i].pool, uTokenReceiver);
            _offset = _offset.uinc();
        }
        return (_offset, _data);
    }
```

```diff
    function _handleMulticall(uint _initPosId, OperationParams calldata _params)
        internal
        returns (bytes[] memory results)
    {
        // prepare data for multicall
        // 1. repay (if needed)
        // 2. withdraw (if needed)
        // 3. change position mode (if needed)
        // 4. borrow (if needed)
        // 5. deposit (if needed)
        bool changeMode = _params.mode != 0 && _params.mode != IPosManager(POS_MANAGER).getPosMode(_initPosId);
        bytes[] memory data;
        {
            uint dataLength = _params.repayParams.length + (2 * _params.withdrawParams.length) + (changeMode ? 1 : 0)
                + _params.borrowParams.length + (2 * _params.depositParams.length);
            data = new bytes[](dataLength);
        }
        uint offset;
        // 1. repay
        (offset, data) = _handleRepay(offset, data, _initPosId, _params.repayParams);
        // 2. withdraw
-        (offset, data) = _handleWithdraw(offset, data, _initPosId, _params.withdrawParams);
+        (offset, data) = _handleWithdraw(offset, data, _initPosId, _params.withdrawParams, _params.returnNative);
        // 3. change position mode
        if (changeMode) {
            data[offset] = abi.encodeWithSelector(IInitCore.setPosMode.selector, _initPosId, _params.mode);
            offset = offset.uinc();
        }
        // 4. borrow
        (offset, data) = _handleBorrow(offset, data, _initPosId, _params.borrowParams);
        // 5. deposit
        (offset, data) = _handleDeposit(offset, data, _initPosId, _params.depositParams);
        // execute multicall
        results = IMulticall(CORE).multicall(data);
    }
```
</details>


**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/29#issuecomment-1870324594)**


***

## [[M-04] `setPosMode` should not allow changing the mode when the new mode's `canRepay` status is disabled](https://github.com/code-423n4/2023-12-initcapital-findings/issues/26)
*Submitted by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/26)*

In the scenario where the mode's `canRepay` status is set to false, positions using that mode cannot be repaid and liquidated. However, users are allowed to change their position's mode to one where the `canRepay` status is currently set to false. This could be exploited when a position owner observes that their position's health is approaching the liquidation threshold, allowing them to prevent liquidation.

### Proof of Concept

It can be observed that when `setPosMode` is called, it checks that `newModeStatus.canBorrow` and `currentModeStatus.canRepay` is set to true. However, it doesn't check the status of `newModeStatus.canRepay` flag.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L203-L204>

<details>

```solidity
    function setPosMode(uint _posId, uint16 _mode)
        public
        virtual
        onlyAuthorized(_posId)
        ensurePositionHealth(_posId)
        nonReentrant
    {
        IConfig _config = IConfig(config);
        // get current collaterals in the position
        (address[] memory pools,, address[] memory wLps, uint[][] memory ids,) =
            IPosManager(POS_MANAGER).getPosCollInfo(_posId);
        uint16 currentMode = _getPosMode(_posId);
        ModeStatus memory currentModeStatus = _config.getModeStatus(currentMode);
        ModeStatus memory newModeStatus = _config.getModeStatus(_mode);
        if (pools.length != 0 || wLps.length != 0) {
            _require(newModeStatus.canCollateralize, Errors.COLLATERALIZE_PAUSED);
            _require(currentModeStatus.canDecollateralize, Errors.DECOLLATERALIZE_PAUSED);
        }
        // check that each position collateral belongs to the _mode
        for (uint i; i < pools.length; i = i.uinc()) {
            _require(_config.isAllowedForCollateral(_mode, pools[i]), Errors.INVALID_MODE);
        }
        for (uint i; i < wLps.length; i = i.uinc()) {
            for (uint j; j < ids[i].length; j = j.uinc()) {
                _require(_config.isAllowedForCollateral(_mode, IBaseWrapLp(wLps[i]).lp(ids[i][j])), Errors.INVALID_MODE);
            }
        }
        // get current debts in the position
        uint[] memory shares;
        (pools, shares) = IPosManager(POS_MANAGER).getPosBorrInfo(_posId);
        IRiskManager _riskManager = IRiskManager(riskManager);
        // check that each position debt belongs to the _mode
        for (uint i; i < pools.length; i = i.uinc()) {
            _require(_config.isAllowedForBorrow(_mode, pools[i]), Errors.INVALID_MODE);
            _require(newModeStatus.canBorrow, Errors.BORROW_PAUSED);
            _require(currentModeStatus.canRepay, Errors.REPAY_PAUSED);
            // update debt on current mode
            _riskManager.updateModeDebtShares(currentMode, pools[i], -shares[i].toInt256());
            // update debt on new mode
            _riskManager.updateModeDebtShares(_mode, pools[i], shares[i].toInt256());
        }
        // update position mode
        IPosManager(POS_MANAGER).updatePosMode(_posId, _mode);
        emit SetPositionMode(_posId, _mode);
    }
```
</details>

As mentioned before, if users see his position's health status is about to reach liquidation threshold and change the mode, this will allow users to prevent their positions from getting liquidated, as both `liquidate` and `liquidateWLp` will check the `canRepay` flag and revert if it's not allowed.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L282-L314><br>
<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L317-L353><br>
<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L587-L599>

```solidity
    /// @dev liquidation internal logic
    function _liquidateInternal(uint _posId, address _poolToRepay, uint _repayShares)
        internal
        returns (LiquidateLocalVars memory vars)
    {
        vars.config = IConfig(config);
        vars.mode = _getPosMode(_posId);

        // check position must be unhealthy
        vars.health_e18 = getPosHealthCurrent_e18(_posId);
        _require(vars.health_e18 < ONE_E18, Errors.POSITION_HEALTHY);

>>>     (vars.repayToken, vars.repayAmt) = _repay(vars.config, vars.mode, _posId, _poolToRepay, _repayShares);
    }
```

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L530-L551>

```solidity
    function _repay(IConfig _config, uint16 _mode, uint _posId, address _pool, uint _shares)
        internal
        returns (address tokenToRepay, uint amt)
    {
        // check status
>>>     _require(_config.getPoolConfig(_pool).canRepay && _config.getModeStatus(_mode).canRepay, Errors.REPAY_PAUSED);
        // get position debt share
        uint positionDebtShares = IPosManager(POS_MANAGER).getPosDebtShares(_posId, _pool);
        uint sharesToRepay = _shares < positionDebtShares ? _shares : positionDebtShares;
        // get amtToRepay (accrue interest)
        uint amtToRepay = ILendingPool(_pool).debtShareToAmtCurrent(sharesToRepay);
        // take token from msg.sender to pool
        tokenToRepay = ILendingPool(_pool).underlyingToken();
        IERC20(tokenToRepay).safeTransferFrom(msg.sender, _pool, amtToRepay);
        // update debt on the position
        IPosManager(POS_MANAGER).updatePosDebtShares(_posId, _pool, -sharesToRepay.toInt256());
        // call repay on the pool
        amt = ILendingPool(_pool).repay(sharesToRepay);
        // update debt on mode
        IRiskManager(riskManager).updateModeDebtShares(_mode, _pool, -sharesToRepay.toInt256());
        emit Repay(_pool, _posId, msg.sender, _shares, amt);
    }
```
### Recommended Mitigation Steps

Add a `canRepay` check status inside `setPosMode`; if it is paused, revert the change. Besides that, the `canRepay` and `canBorrow` checks don't need to be inside the pools check loop.

<details>

```diff
    function setPosMode(uint _posId, uint16 _mode)
        public
        virtual
        onlyAuthorized(_posId)
        ensurePositionHealth(_posId)
        nonReentrant
    {
        IConfig _config = IConfig(config);
        // get current collaterals in the position
        (address[] memory pools,, address[] memory wLps, uint[][] memory ids,) =
            IPosManager(POS_MANAGER).getPosCollInfo(_posId);
        uint16 currentMode = _getPosMode(_posId);
        ModeStatus memory currentModeStatus = _config.getModeStatus(currentMode);
        ModeStatus memory newModeStatus = _config.getModeStatus(_mode);
        if (pools.length != 0 || wLps.length != 0) {
            _require(newModeStatus.canCollateralize, Errors.COLLATERALIZE_PAUSED);
            _require(currentModeStatus.canDecollateralize, Errors.DECOLLATERALIZE_PAUSED);
        }
        // check that each position collateral belongs to the _mode
        for (uint i; i < pools.length; i = i.uinc()) {
            _require(_config.isAllowedForCollateral(_mode, pools[i]), Errors.INVALID_MODE);
        }
        for (uint i; i < wLps.length; i = i.uinc()) {
            for (uint j; j < ids[i].length; j = j.uinc()) {
                _require(_config.isAllowedForCollateral(_mode, IBaseWrapLp(wLps[i]).lp(ids[i][j])), Errors.INVALID_MODE);
            }
        }
        // get current debts in the position
        uint[] memory shares;
        (pools, shares) = IPosManager(POS_MANAGER).getPosBorrInfo(_posId);
        IRiskManager _riskManager = IRiskManager(riskManager);
        // check that each position debt belongs to the _mode
+      _require(newModeStatus.canBorrow, Errors.BORROW_PAUSED);
+      _require(currentModeStatus.canRepay, Errors.REPAY_PAUSED);
+      _require(newModeStatus.canRepay, Errors.REPAY_PAUSED);
        for (uint i; i < pools.length; i = i.uinc()) {
            _require(_config.isAllowedForBorrow(_mode, pools[i]), Errors.INVALID_MODE);
-            _require(newModeStatus.canBorrow, Errors.BORROW_PAUSED);
-            _require(currentModeStatus.canRepay, Errors.REPAY_PAUSED);
            // update debt on current mode
            _riskManager.updateModeDebtShares(currentMode, pools[i], -shares[i].toInt256());
            // update debt on new mode
            _riskManager.updateModeDebtShares(_mode, pools[i], shares[i].toInt256());
        }
        // update position mode
        IPosManager(POS_MANAGER).updatePosMode(_posId, _mode);
        emit SetPositionMode(_posId, _mode);
    }
```

</details>

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/26#issuecomment-1870318447)**

***

## [[M-05] `collateralizeWLp` can be bypassed even when collateralization is paused](https://github.com/code-423n4/2023-12-initcapital-findings/issues/25)
*Submitted by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/25)*

Admin can pause collateralization for a specific mode to prevent users from providing more collateral either via `collateralize` or `collateralizeWLp`. However, due to not properly using internal accounting when tracking wLP collateral, users can still provide more collateral by directly donating tokens to a specific LP `tokenId`.

### Proof of Concept

It can be seen that when `canCollateralize` of certain mode is paused, `collateralizeWLp` should be paused.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L243-L261>

```solidity
    /// @inheritdoc IInitCore
    function collateralizeWLp(uint _posId, address _wLp, uint _tokenId)
        public
        virtual
        onlyAuthorized(_posId)
        nonReentrant
    {
        IConfig _config = IConfig(config);
        uint16 mode = _getPosMode(_posId);
        // check mode status
>>>     _require(_config.getModeStatus(mode).canCollateralize, Errors.COLLATERALIZE_PAUSED);
        // check if the wLp is whitelisted
        _require(_config.whitelistedWLps(_wLp), Errors.TOKEN_NOT_WHITELISTED);
        // check if the position mode supports _wLp
        _require(_config.isAllowedForCollateral(mode, IBaseWrapLp(_wLp).lp(_tokenId)), Errors.INVALID_MODE);
        // update collateral on the position
        uint amtColl = IPosManager(POS_MANAGER).addCollateralWLp(_posId, _wLp, _tokenId);
        emit CollateralizeWLp(_wLp, _tokenId, _posId, amtColl);
    }
```

However, when calculating collateral credit, it will calculate based on balance of LP of specific token inside wLP contract.

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L456>

```solidity
    function getCollateralCreditCurrent_e36(uint _posId) public virtual returns (uint collCredit_e36) {
        address _oracle = oracle;
        IConfig _config = IConfig(config);
        uint16 mode = _getPosMode(_posId);
        // get position collateral
>>>     (address[] memory pools, uint[] memory shares, address[] memory wLps, uint[][] memory ids, uint[][] memory amts)
        = IPosManager(POS_MANAGER).getPosCollInfo(_posId);
        // calculate collateralCredit
        uint collCredit_e54;
        for (uint i; i < pools.length; i = i.uinc()) {
            address token = ILendingPool(pools[i]).underlyingToken();
            uint tokenPrice_e36 = IInitOracle(_oracle).getPrice_e36(token);
            uint tokenValue_e36 = ILendingPool(pools[i]).toAmtCurrent(shares[i]) * tokenPrice_e36;
            TokenFactors memory factors = _config.getTokenFactors(mode, pools[i]);
            collCredit_e54 += tokenValue_e36 * factors.collFactor_e18;
        }
        for (uint i; i < wLps.length; i = i.uinc()) {
            for (uint j; j < ids[i].length; j = j.uinc()) {
                uint wLpPrice_e36 = IBaseWrapLp(wLps[i]).calculatePrice_e36(ids[i][j], _oracle);
                uint wLpValue_e36 = amts[i][j] * wLpPrice_e36;
                TokenFactors memory factors = _config.getTokenFactors(mode, IBaseWrapLp(wLps[i]).lp(ids[i][j]));
                collCredit_e54 += wLpValue_e36 * factors.collFactor_e18;
            }
        }
        collCredit_e36 = collCredit_e54 / ONE_E18;
    }
```

<https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/PosManager.sol#L125>

```solidity
    function getPosCollInfo(uint _posId)
        external
        view
        returns (
            address[] memory pools,
            uint[] memory amts,
            address[] memory wLps,
            uint[][] memory ids,
            uint[][] memory wLpAmts
        )
    {
        PosCollInfo storage posCollInfo = __posCollInfos[_posId];
        pools = posCollInfo.collTokens.values();
        amts = new uint[](pools.length);
        for (uint i; i < pools.length; i = i.uinc()) {
            amts[i] = posCollInfo.collAmts[pools[i]];
        }
        wLps = posCollInfo.wLps.values();
        ids = new uint[][](wLps.length);
        wLpAmts = new uint[][](wLps.length);
        for (uint i; i < wLps.length; i = i.uinc()) {
            ids[i] = posCollInfo.ids[wLps[i]].values();
            wLpAmts[i] = new uint[](ids[i].length);
            for (uint j; j < ids[i].length; j = j.uinc()) {
>>>             wLpAmts[i][j] = IBaseWrapLp(wLps[i]).balanceOfLp(ids[i][j]);
            }
        }
    }
```

It should be noted that most DEXs (e.g., Uniswap) allow any user to provide liquidity to any other users position. In practice, this bypasses the collateralization paused functionality.

### Recommended Mitigation Steps

Implement internal accounting for wLP inside the `PosManager`.

**[fez-init (INIT) acknowledged and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/25#issuecomment-1870315217):**
 > Internal accounting shall be ensured in wLp.

**[hansfriese (Judge) commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/25#issuecomment-1871323396):**
 > Medium is appropriate as the admin's action can be bypassed.

***

## [[M-06] setPosMode function doesn't check if wLp is whitelisted](https://github.com/code-423n4/2023-12-initcapital-findings/issues/22)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/22), also found by [sashik\_eth](https://github.com/code-423n4/2023-12-initcapital-findings/issues/32)*

Using `setPosMode` function owner of position can change it's mode. When the function is called, then there are a lot of checks, like if current mode allows to decollateralize and if new mode allows to collateralize.

Also it's checked, that all position collateral is used by the new mode. It's done [for the pools](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L189) and [for the wLp tokens](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L193).

In order to be able to use wLp tokens as collateral, then wLp should be whitelisted. It is checked in several places in the code, [like here](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L255). It's also possible that after some time wLp token will be blacklisted. In this case it should not be allowed to migrate blacklisted wLp token to the new mode, however there is no such check in the setPosMode function.

As result user can provide blacklisted collateral to the new mode.
I understand that borrowing factor for such collateral will be likely about 0, however if you would try to collateralize such token, then [it will be denied](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L255), thus setMode function breaks this invariant.

### Impact

Non whitelisted collateral can be moved to the new mode.

### Tools Used

VsCode

### Recommended Mitigation Steps

Do not allow user to move blacklisted collateral to the new mode.

**[fez-init (INIT) confirmed and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/22#issuecomment-1870308603):**
 > Will add whitelist check.

***

## [[M-07] Malicious user can steal native tokens of MoneyMarketHook caller](https://github.com/code-423n4/2023-12-initcapital-findings/issues/19)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/19)*

MoneyMarketHook allows user to chain some actions into one multicall to the InitCore. In the end user can get all wrapped native tokens that he withdrew [in a form of native token](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L76-L80). Note, that this part of code withdraws all balance from wrapped token and the sends all balance to the `msg.sender`. In case if balance of contract is 0, then the call will still succeed.

One type of actions that caller can do using `execute` function [is withdraw](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L124). In case if caller needs to repay funds to other address then he can provide it [as `to` param](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L181). So as result, `IInitCore.burnTo` will transfer pool tokens [to the provided recipient](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L192). And in case if token has a hook, like erc777 or erc677, then receiver will be triggered and he has execution control now.

User can have [multiple withdraws in same multicall](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L173). And it's possible that first withdraw is wrapped native token withdraw(which user would like to receive as native) and next withdraw is with erc777 token and other recipient.

In such case, when first withdraw is done, then wrapped token is already on MoneyMarketHook balance. And then when second withdraw is handled and attacker get hook, then he can call MoneyMarketHook.execute(it doesn't have reentrancy check) again with any params that just should pass and `_params.returnNative` as true. Then all wrapped token balance will be sent to the attacker and then execution will return back to the victim and it will send 0 amount as native token to the victim.

As result attacker is able to steal user's native tokens.

From the readme, it's clear that only fee on transfer tokens are not supported and erc777 are supported:

> Please list specific ERC20 that your protocol is anticipated to interact with. Could be "any" (literally anything, fee on transfer tokens, ERC777 tokens and so forth) or a list of tokens you envision using on launch.<br>
> No fee-on-transfer tokens

### Impact

It's possible to steal user's funds.

### Tools Used

VsCode

### Recommended Mitigation Steps

Add reentrancy check to the `execute` function.

**[fez-init (INIT) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/19#issuecomment-1870299489):**
 > This should be a medium issue. There are multiple things that needs to be aligned, including:
 >
> - supporting of ERC777. We did not intend to support ERC777, but acknowledge that it may not be communicated clearly.
> - the victim needs to specify a certain malicious `to` contract for the attack to happen.

 > We will add reentrancy check to the execute function to prevent this kind of scenario anyways.

**[hansfriese (Judge) decreased severity to Medium and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/19#issuecomment-1870758513):**
 > I agree Medium is appropriate due to this requirement: "the victim needs to specify a certain malicious `to` contract for the attack to happen".

***

## [[M-08] `TRST-M-8` from previous audit still present](https://github.com/code-423n4/2023-12-initcapital-findings/issues/17)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/17), also found by [said](https://github.com/code-423n4/2023-12-initcapital-findings/issues/27) and [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/20)*

Interest accruing is not paused, when repaying is not allowed.

### Proof of Concept

TRST-M-8 from previous audit describes the fact, that when repaying is paused, then pool still continue accruing interests. Usually this is not considered as a medium bug anymore.
However, protocol team has stated that they have fixed everything.

I should say that TRST-M-8 still exists and in case repayment will be paused and user will not be able to reduce their debt, their debt shares will continue to accrue interest.

### Tools Used

VsCode

### Recommended Mitigation Steps

You can implement the logic that will pause all interest accruing as well, but I am not sure this is indeed needed.

**[fez-init (INIT) acknowledged and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/17#issuecomment-1870188388):**
 > There might have been miscommunications with this issue being resolved. This issue from Trust should be communicated as acknowledged.

**[hansfriese (Judge) commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/17#issuecomment-1871329916):**
 > According to the sponsor's comment, it's worth keeping it as a valid medium.

***

## [[M-09] If wLP is blacklisted, then user will not be able to withdraw it](https://github.com/code-423n4/2023-12-initcapital-findings/issues/13)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/13), also found by [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/47) and [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/41)*

When users deposit wLP tokens as collateral, then they are checked [to be whitelisted](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L255).

Later, it's possible that for some reason wLP token [will be blacklisted](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/Config.sol#L145) by governor. And once it's done, then users who already used that wLP token as collateral [will not be able to withdraw them](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L275).

Also same thing exists for the `liquidateWLp` function, which means that in case if position, that is collateralized with wLP that is blacklisted, will become unhealthy, then liquidators [will not be able to liquidate it](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L327).

Sponsor said that blacklisting flow will be as following.

*   Decrease collateral factor for blacklisted wLp until it becomes 0
*   then blacklist wLp

Considering this fact I realize that for liquidation this will not be an issue as wLp will have 0 collateralization power when it will be blacklisted. However it's still possible that some users will not decollateralize their wLp tokens yet for some reasom and thus they will not be able to withdraw them later.

### Impact

User can't withdraw previously deposited wLP tokens after they were blacklisted.

### Tools Used

VsCode

### Recommended Mitigation Steps

Even if wLP token is blacklisted now, you still should allow user to withdraw them. After all you have health check function that will guarantee that position has enough collateral.

**[fez-init (INIT) acknowledged and commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/13#issuecomment-1870294773):**
 > We will use unwhitelisting with care.


***

## [[M-10] Lack of way to handle not fully repaid bad debt after liquidation after the lending pool share or WLP are fully seized](https://github.com/code-423n4/2023-12-initcapital-findings/issues/9)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/9), also found by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/15)*

When user has bad debt, user's borrow credit > collateral credit. Liqudiator can step in and liquidate and seize user's share or seize user WLP and repay the debt.

While the liquidate function aims to let liqudiator take the min share available for bad debt repayment.

```solidity
// take min of what's available (for bad debt repayment)
shares = shares.min(IPosManager(POS_MANAGER).getCollAmt(_posId, _poolOut)); // take min of what's available
_require(shares >= _minShares, Errors.SLIPPAGE_CONTROL);
```

After the user's pool share is transferred out, or after user's WLP is seized, the rest of unpaid debt becomes bad debt permanently. For example, user's borrow 1000 USDT and has debt 1000 USDT. His share is only worth 500 USD as collateral price drops. Because the code lets liquidator take min of what's available for both lending pool share and take min of what's available (for bad debt repayment) for WLP amount. The liqudiator can repay 800 USD and seize share of 500 USD. However, there are 200 USD remaining debt. When other liquidators (even this liquidator belongs to protocol) writes to repay and erase the rest 200 USD bad debt, he cannot because [removeCollateralTo validates share > 0, if share is 0, revert](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/core/PosManager.sol#L235).

```solidity
_require(_shares > 0, Errors.ZERO_VALUE);
```

If the underlying collateral is WLP, the second liquidation aims to write off bad debt does not work as well because if all WLP is transfered out, calling [\_harvest and unwrap again is likely to revert](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/core/PosManager.sol#L265).

```solidity
_harvest(_posId, _wLp, _tokenId);
IBaseWrapLp(_wLp).unwrap(_tokenId, _amt, _receiver);
```

The bad permanently inflates the totalAssets() in lending pool and inflates the total debt to not let other users borrow from protocol because of the borrow cap checks.

Also, the lender suffers the loss because if the bad debt is not repaid, the lender that deposit cash into the lending pool is lost.

### Recommended Mitigation Steps

Add a way to handle not fully repaid bad debt after liquidation after the lending pool share or WLP is fully seized.

Add a function to donate to the lending pool to let user supply asset or add a function to socialize the bad debt as loss explicilty.

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/9#issuecomment-1869836241)**

***

## [[M-11] API3 oracle timestamp can be set to future timestamp and block API3 Oracle usage to make code revert in underflow](https://github.com/code-423n4/2023-12-initcapital-findings/issues/4)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/4), also found by [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/39)*

In the Api3OracleReader.sol, the code assumes tha the timestamp returned from oracle is always in the past.

```solidity
    function getPrice_e36(address _token) external view returns (uint price_e36) {
        // load and check
        DataFeedInfo memory dataFeedInfo = dataFeedInfos[_token];
        _require(dataFeedInfo.dataFeedId != bytes32(0), Errors.DATAFEED_ID_NOT_SET);
        _require(dataFeedInfo.maxStaleTime != 0, Errors.MAX_STALETIME_NOT_SET);

        // get price and token's decimals
        uint decimals = uint(IERC20Metadata(_token).decimals());
        // return price per token with 1e18 precisions
        // e.g. 1 BTC = 35000 * 1e18 in USD_e18 unit
        (int224 price, uint timestamp) = IApi3ServerV1(api3ServerV1).readDataFeedWithId(dataFeedInfo.dataFeedId);

        // check if the last updated is not longer than the max stale time
        _require(block.timestamp - timestamp <= dataFeedInfo.maxStaleTime, Errors.MAX_STALETIME_EXCEEDED);

        // return as [USD_e36 per wei unit]
        price_e36 = (price.toUint256() * ONE_E18) / 10 ** decimals;
    }
```

Note the check:

```solidity
// e.g. 1 BTC = 35000 * 1e18 in USD_e18 unit
(int224 price, uint timestamp) = IApi3ServerV1(api3ServerV1).readDataFeedWithId(dataFeedInfo.dataFeedId);

// check if the last updated is not longer than the max stale time
_require(block.timestamp - timestamp <= dataFeedInfo.maxStaleTime, Errors.MAX_STALETIME_EXCEEDED);
```

If timestamp is greater than block.timestamp, the transaction will revert and block oracle lookup on APi3OracleReader.sol.

The relayer on api3 side can update both oracle price timestamp and value.

Let us go over how the price is updated in Api3 code:

The function readDataFeedWithID basically just read the data from struct \_dataFeeds\[beaconId], [in this function](https://github.com/api3dao/airnode-protocol-v1/blob/fa95f043ce4b50e843e407b96f7ae3edcf899c32/contracts/api3-server-v1/DataFeedServer.sol#L75)

```solidity
    /// @notice Reads the data feed with ID
    /// @param dataFeedId Data feed ID
    /// @return value Data feed value
    /// @return timestamp Data feed timestamp
    function _readDataFeedWithId(
        bytes32 dataFeedId
    ) internal view returns (int224 value, uint32 timestamp) {
        DataFeed storage dataFeed = _dataFeeds[dataFeedId];
        (value, timestamp) = (dataFeed.value, dataFeed.timestamp);
        require(timestamp > 0, "Data feed not initialized");
    }
```

When the relayer updates the oracle data, first we are calling [processBeaconUpdate](https://github.com/api3dao/airnode-protocol-v1/blob/fa95f043ce4b50e843e407b96f7ae3edcf899c32/contracts/api3-server-v1/BeaconUpdatesWithSignedData.sol#L41).

Note that is a [modifier onlyValidateTimestamp](https://github.com/api3dao/airnode-protocol-v1/blob/fa95f043ce4b50e843e407b96f7ae3edcf899c32/contracts/api3-server-v1/DataFeedServer.sol#L115).

```solidity
  function processBeaconUpdate(
        bytes32 beaconId,
        uint256 timestamp,
        bytes calldata data
    )
        internal
        onlyValidTimestamp(timestamp)
        returns (int224 updatedBeaconValue)
    {
        updatedBeaconValue = decodeFulfillmentData(data);
        require(
            timestamp > _dataFeeds[beaconId].timestamp,
            "Does not update timestamp"
        );
        _dataFeeds[beaconId] = DataFeed({
            value: updatedBeaconValue,
            timestamp: uint32(timestamp)
        });
    }
```

The [check](https://github.com/api3dao/airnode-protocol-v1/blob/fa95f043ce4b50e843e407b96f7ae3edcf899c32/contracts/api3-server-v1/DataFeedServer.sol#L30) ensures that only when the timstamp is from more than 1 hour, the update reverts.

```solidity
    /// @dev Reverts if the timestamp is from more than 1 hour in the future
    modifier onlyValidTimestamp(uint256 timestamp) virtual {
        unchecked {
            require(
                timestamp < block.timestamp + 1 hours,
                "Timestamp not valid"
            );
        }
        _;
    }
```

What does this mean?

The timestamp of an oracle can be set to the future within an hour, the relayer does not have to be malicious, it is a normal part of updating data.

Suppose the current timestamp is 10000

1 hour = 3600 seconds

If the relayer set timestamp to 12000, the price update will go through

But the code:

```solidity
_require(block.timestamp - timestamp <= dataFeedInfo.maxStaleTime, Errors.MAX_STALETIME_EXCEEDED);
```

Will revert when current timestamp is 10001.

10001 - 12000 will revert in underflow.

### Recommended Mitigation Steps

If the oracle timestamp comes from the future, the code should consider it not stale.

Can change the code to:

    if (block.timestamp > timestamp) {
     _require(block.timestamp - timestamp <= dataFeedInfo.maxStaleTime, Errors.MAX_STALETIME_EXCEEDED);
    }


**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/4#issuecomment-1869777419)**


***

## [[M-12] Admin configuration isAllowedForCollateral(mode, pool) can be bypassed by donating asset to the pool directly and then trigger sync cash via flashloan](https://github.com/code-423n4/2023-12-initcapital-findings/issues/3)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/3), also found by [rvierdiiev](https://github.com/code-423n4/2023-12-initcapital-findings/issues/16)*

In the current implementation, after user deposits funds into lending pool and mint lending pool shares, user can call collateralize function to add collateral:

```solidity
    function collateralize(uint _posId, address _pool) public virtual onlyAuthorized(_posId) nonReentrant {
        IConfig _config = IConfig(config);
        // check mode status
        uint16 mode = _getPosMode(_posId);
        _require(_config.getModeStatus(mode).canCollateralize, Errors.COLLATERALIZE_PAUSED);
        // check if the position mode supports _pool
        _require(_config.isAllowedForCollateral(mode, _pool), Errors.INVALID_MODE);
        // update collateral on the position
        uint amtColl = IPosManager(POS_MANAGER).addCollateral(_posId, _pool);
        emit Collateralize(_posId, _pool, amtColl);
    }
```

There is a validation:

```solidity
 _require(_config.isAllowedForCollateral(mode, _pool), Errors.INVALID_MODE);
```

Let us consider the case:

The mode supports three pools, USDC lending pool, WETH lending pool and a token A lending pool.

The token A is subject to high volatility, the admin decides to disalllow token A lending pool added as collateral.

But then the token A is hacked.

The attacker can mint the token A infinitely.

There is a relevant hack in the past:

1.  <https://ciphertrace.com/infinite-minting-exploit-nets-attacker-4-4m/>

Attacker exploited logical and math error to mint token infinitely.

2.  <https://www.coindesk.com/business/2022/10/10/binance-exec-bnb-smart-chain-hack-could-have-been-worse-if-validators-hadnt-sprung-into-action/>

Attacker exploited cryptographical logic to mint token infinitely.

But even when admin disallow a mode from further collaterize or disallow the lending pool from further collaterize, the hacker can donate the token to the lending pool and inflate the share worth to borrow all fund out.

1.  hacker transfers the infinitely minted token to the lending pool
2.  then hacker can call the [function flash](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/core/InitCore.sol#L383)

This would trigger the function syncCash, which update the cash amount in the lending pool to make sure the donated token count into the token worth

```solidity
// execute callback
IFlashReceiver(msg.sender).flashCallback(_pools, _amts, fees, _data);
// sync cash
for (uint i; i < _pools.length; i = i.uinc()) {
	uint poolCash = ILendingPool(_pools[i]).syncCash();
```

[Sync cash is called](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/lending_pool/LendingPool.sol#L148)

```solidity
   /// @inheritdoc ILendingPool
    function syncCash() external accrue onlyCore returns (uint newCash) {
        newCash = IERC20(underlyingToken).balanceOf(address(this));
        _require(newCash >= cash, Errors.INVALID_AMOUNT_TO_REPAY); // flash not repay
        cash = newCash;
    }
```

Basically by using the flash function and then trigger syncCash, user can always donate the token to the pool to inflate share worth.

Then in the collateral credit calculation, we are [converting shares worth to amount worth](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/core/InitCore.sol#L462)

```solidity
            uint tokenValue_e36 = ILendingPool(pools[i]).toAmtCurrent(shares[i]) * tokenPrice_e36;
```

Which calls the function [toAmt](https://github.com/code-423n4/2023-12-initcapital/blob/a53e401529451b208095b3af11862984d0b32177/contracts/lending_pool/LendingPool.sol#L266)

```solidity
   function _toAmt(uint _shares, uint _totalAssets, uint _totalShares) internal pure returns (uint amt) {
        return _shares.mulDiv(_totalAssets + VIRTUAL_ASSETS, _totalShares + VIRTUAL_SHARES);
    }
}
```

Assume shares do not change.<br>
Assume total shares does not change.

Clearly inflating the total asset (which is \_cash + debt) inflates share worth.

Again, in the case of infinite token minting, hacker can donate the token to the lending pool to inflate the collateral credit and borrow all fund out and create large bad debt.

### Recommended Mitigation Steps

Use internal balance to track the cash amount and do not allow user to indirectly access the sync cash function via flash loan.

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/3#issuecomment-1869762110)**

***

# Low Risk and Non-Critical Issues

For this audit, 3 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2023-12-initcapital-findings/issues/35) by **0x73696d616f** received the top score from the judge.

*The following wardens also submitted reports: [sashik\_eth](https://github.com/code-423n4/2023-12-initcapital-findings/issues/46) and [ladboy233](https://github.com/code-423n4/2023-12-initcapital-findings/issues/8).*

## [L-01] reserveFactor in LendingPool should be capped at 1e18
[`setReserveFactor()_e18`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/lending_pool/LendingPool.sol#L239-L241) does not check the reserveFactor, which if bigger than `1e18`, will make [`accrueInterest()`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/lending_pool/LendingPool.sol#L155) always underflow, DoSing the lending pool functions that depend on the [`accrue()`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/lending_pool/LendingPool.sol#L55) modifier. It should ideally be capped at a lower value, but this is more of a centralization risk.

## [L-02] `setBorrFactors_e18()` could check for duplicate `_pools` as an additional check to make sure that no incorrect factors are set
If 2 duplicates are sent, only the latter will take effect, which could have very dangerous implications.

## [L-03] excess ETH in [`InitCore:Multicall()`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L389) and [`InitCore:callback()`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L505) could be refunded

## [N-01]  [`execute()`](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/hook/MoneyMarketHook.sol#L53) could check leftover balances in all interacted tokens
Users could make mistakes and tokens beside `ETH` could be left in the contract. The refund mechanism could be extended to other tokens as well.

## [N-02] missing a way to remove `collTokens` from `Config.sol`, which could be dangerous in the long run as some token could go rogue (or an upgrade).

**[fez-init (INIT) acknowledged](https://github.com/code-423n4/2023-12-initcapital-findings/issues/35#issuecomment-1870331709)**

**[hansfriese (Judge) commented](https://github.com/code-423n4/2023-12-initcapital-findings/issues/35#issuecomment-1872449403):**
 > These 3 submissions were downgraded to low/non-critical and also considered in warden 0x73696d616f's score:
> - [RebaseHelperParams.rebaseHelperParams.helper is not whitelisted, which could lead to user mistakes or phishing attacks](https://github.com/code-423n4/2023-12-initcapital-findings/issues/45)
> - [Possible price manipulation in InitOracle due to lack of checks](https://github.com/code-423n4/2023-12-initcapital-findings/issues/44)
> - [Liquidations can possibly be prevented if a liquidate call frontruns another one with a partial liquidation](https://github.com/code-423n4/2023-12-initcapital-findings/issues/43)


***

# Gas Optimizations

For this audit, 2 reports were submitted by wardens detailing gas optimizations. The [report highlighted below](https://github.com/code-423n4/2023-12-initcapital-findings/issues/23) by **rvierdiiev** received the top score from the judge.

*The following wardens also submitted reports: [0x73696d616f](https://github.com/code-423n4/2023-12-initcapital-findings/issues/34).*

## [G-01] `setPosMode` function loops through all borrowed pools and checks [if it is allowed to borrow in new mode and repay in old pool](https://github.com/code-423n4/2023-12-initcapital/blob/main/contracts/core/InitCore.sol#L203-L204) inside the loop 

It's possible to do that only 1 time outside the loop in case if pools length is not 0. This will save gas and will reduce those 2 lines calculation for n times to 1.

**[fez-init (INIT) confirmed](https://github.com/code-423n4/2023-12-initcapital-findings/issues/23#issuecomment-1870309323)**

***

# Audit Analysis

An analysis report examines the codebase as a whole, providing observations and advice on such topics as architecture, mechanism, or approach. The [report highlighted below](https://github.com/code-423n4/2023-12-initcapital-findings/issues/7) by **ladboy233** received the top score from the judge.

### Overview
The INIT project introduces a comprehensive framework designed to revolutionize the way users interact with digital assets and lending markets. Key features of the project include a multi-silo position system, innovative use of flashloans, multicall capabilities, LP tokens as collateral, and a dynamic interest rate model.

### Key Components and Features

1. **Multi-Silo Positioning**: This unique feature allows individual wallet addresses to manage multiple, isolated positions, each identified by a separate position id. This structure enhances flexibility and control for users.

2. **Flashloan Integration**: Flashloans are integrated into the system, providing users with advanced financial tools for various trading and arbitrage strategies.

3. **Multicall Functionality**: Users can execute a batched sequence of actions through multicall, enabling complex transactions like borrowing first and collateralizing later, simplifying the transaction process.

4. **LP Tokens and Collateral**: The system allows for the use of LP tokens as collateral by employing wrapped LPs, broadening the scope of usable assets within the platform.

5. **Interest Rate Model**: A sophisticated model is in place to manage interest rates, contributing to a balanced and fair lending environment.

### Core Components

- **InitCore**: The central interface for user interactions. It includes essential actions like minting and burning tokens, collateralization, borrowing, and repaying loans. The multicall feature allows for batching of these actions for efficiency.

- **LendingPool**: Manages the supply of tokens and the total debt share, playing a pivotal role in the liquidity of the system.

- **PosManager**: Responsible for managing individual positions, including debt shares and collaterals.

- **LiqIncentiveCalculator**: This component calculates liquidation incentives, primarily based on the health of a position.

- **MoneyMarketHook**: Implements standard money market actions like deposit, withdrawal, borrowing, and repayment.

- **InitOracle**: Aggregates oracle prices from primary and secondary sources for accurate asset valuation.

- **RiskManager**: Addresses potential risks in the money market, particularly focusing on issues like price impact from concentrated collateralization. The implementation of a debt ceiling per mode is a notable risk mitigation measure.

### Pending Integrations and Future Developments

- **WLp Contract**: Although not currently in scope, this wrapped LP contract is anticipated to integrate with certain DEXs and handle reward calculations, signifying a future expansion of the platform's capabilities.

### Summary of Centralization Dependency and Configuration Risks in the INIT Protocol

**Centralization Risks**

1. **Config.sol**: The administrative authority in `Config.sol` carries a significant centralization risk. The admin has the power to modify protocol configurations without any limitations. This includes changing collateral and borrow factors at will, potentially triggering unintended liquidations for users. Furthermore, the admin can alter the mode status, directly impacting users' ability to engage in key functions like collateralizing and borrowing.

2. **IncentiveCalculator.sol**: In the `IncentiveCalculator.sol` component, unrestricted administrative control also poses centralization risks. The admin can adjust the maxIncentiveMultiplier arbitrarily. Excessive maxIncentiveMultipliers could lead to disproportionate losses for users undergoing liquidation.

3. **InitCore.sol**: The `InitCore.sol` also suffers from centralization issues due to unrestricted admin access. The admin can change critical configurations, such as the config address, potentially leading to configurations that compromise user security and interests.

4. **LendingPool.sol**: Similar centralization risks exist in `LendingPool.sol`, where the admin can arbitrarily alter the reserveFactor. Such changes can lead to an uneven distribution of interests, favoring the treasury disproportionately.

5. **Oracle Components (Api3OracleReader.sol/PythOracleReader.sol/InitOracle.sol)**: In these components, the admin can modify oracle addresses without restrictions, introducing centralization risks. Inaccurate oracle addresses can lead to incorrect price reporting, potentially draining the liquidity of the lending pool.

**Systemic Risks**

1. **Oracle Reliability**: The protocol relies on oracles for accurate price reporting of underlying tokens in the LendingPool. If these oracles fail to report correct prices, it could lead to miscalculations in the value of collateral and debts. This scenario may cause unwarranted liquidations or enable effectively uncollateralized loans.

2. **Sharp Drop in Collateral**: The protocol assumes sufficient liquidity for collateral liquidation before incurring bad debts. However, if highly volatile tokens are used as collateral and they depreciate rapidly, it could result in significant bad debts. This situation is exacerbated by the absence of a collateral cap check in the current implementation.

**Administrative Control Over Debt Ceiling and Lending Pools**

- The admin also has the authority to update the debt ceiling in the risk manager for each mode.
- Additionally, they possess the ability to enable, disable, or modify support for specific lending pools or Wrapped LP (WLP) contracts.

These additional administrative controls further underscore the centralization risks within the INIT protocol, where significant power is vested in the hands of a central administrative authority.

### Suggestions for the INIT Protocol Based on Identified Needs

1. **Diversifying LP Tokens as Collateral**:
   - **Strategy**: Develop a framework to support a variety of LP tokens as collateral. This should include a comprehensive analysis of each LP token's market behavior, liquidity, and volatility.
   - **Implementation**: Set up a process for periodically reviewing and updating the list of supported LP tokens to ensure relevance and stability.

2. **Implementing WLP Oracles with Manipulation Resistance**:
   - **Approach**: Although the implementation of WLP (Wrapped LP) is not currently in scope, it is crucial to design WLP oracles that are robust against market manipulation.
   - **Action**: Utilize multiple, independent oracles for price feeds to diminish the impact of any single source being manipulated. Implement additional checks and balances, such as price feed deviation limits, to further strengthen resistance against manipulation.

3. **Ensuring Fair Compensation for Liquidators**:
   - **Objective**: To maintain a healthy protocol ecosystem, liquidators should be adequately incentivized to clear bad debt.
   - **Method**: Design a liquidation reward system that offers competitive compensation based on the risk and capital involved in liquidation processes. Regularly adjust incentives in line with market conditions to maintain attractiveness and effectiveness.

4. **Careful Management of Protocol Configuration**:
   - **Focus**: Effective management of protocol configurations is essential to maintain system stability and user trust.
   - **Tactics**:
     - Implement a governance system for major configuration changes, involving a wider community or stakeholder vote, ensuring decisions are not centralized.
     - Establish a transparent change management process, where any updates to the protocol configurations are clearly communicated to users beforehand.
     - Conduct regular audits and stress tests on configuration changes to assess their impact under various scenarios.

### Time spent:
25 hours

**[fez-init (INIT) acknowledged](https://github.com/code-423n4/2023-12-initcapital-findings/issues/7#issuecomment-1869826974)**

***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
