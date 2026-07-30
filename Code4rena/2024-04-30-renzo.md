---
sponsor: "Renzo"
slug: "2024-04-renzo"
date: "2024-06-07"
title: "Renzo"
findings: "https://github.com/code-423n4/2024-04-renzo-findings/issues"
contest: 372
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Renzo smart contract system written in Solidity. The audit took place between April 30 — May 8, 2024.

Following the C4 audit, the sponsor's related mitigations were reviewed by the following wardens: [Team LessDupes](https://code4rena.com/@LessDupes) ([3docSec](https://code4rena.com/@3docSec), [sin1st3r\_\_](https://code4rena.com/@sin1st3r__), and [EV\_om](https://code4rena.com/@EV_om)), [Team Fassi\_Security](https://code4rena.com/@Fassi_Security) ([bronze\_pickaxe](https://code4rena.com/@bronze_pickaxe), and [mxuse](https://code4rena.com/@mxuse)), [Bauchibred](https://code4rena.com/@Bauchibred), [grearlake](https://code4rena.com/@grearlake), and [0xCiphky](https://code4rena.com/@0xCiphky). The [mitigation review report](#mitigation-review) is appended below the audit report.

## Wardens

136 Wardens contributed reports to Renzo:

  1. [LessDupes](https://code4rena.com/@LessDupes) ([3docSec](https://code4rena.com/@3docSec), [sin1st3r\_\_](https://code4rena.com/@sin1st3r__) and [EV\_om](https://code4rena.com/@EV_om))
  2. [Fassi\_Security](https://code4rena.com/@Fassi_Security) ([bronze\_pickaxe](https://code4rena.com/@bronze_pickaxe) and [mxuse](https://code4rena.com/@mxuse))
  3. [Bauchibred](https://code4rena.com/@Bauchibred)
  4. [0x73696d616f](https://code4rena.com/@0x73696d616f)
  5. [grearlake](https://code4rena.com/@grearlake)
  6. [0xCiphky](https://code4rena.com/@0xCiphky)
  7. [fyamf](https://code4rena.com/@fyamf)
  8. [oakcobalt](https://code4rena.com/@oakcobalt)
  9. [ilchovski](https://code4rena.com/@ilchovski)
  10. [ladboy233](https://code4rena.com/@ladboy233)
  11. [guhu95](https://code4rena.com/@guhu95)
  12. [Sathish9098](https://code4rena.com/@Sathish9098)
  13. [zzykxx](https://code4rena.com/@zzykxx)
  14. [ZanyBonzy](https://code4rena.com/@ZanyBonzy)
  15. [tapir](https://code4rena.com/@tapir)
  16. [SBSecurity](https://code4rena.com/@SBSecurity) ([Slavcheww](https://code4rena.com/@Slavcheww) and [Blckhv](https://code4rena.com/@Blckhv))
  17. [peanuts](https://code4rena.com/@peanuts)
  18. [GoatedAudits](https://code4rena.com/@GoatedAudits) ([0xjuan](https://code4rena.com/@0xjuan) and [Spearmint](https://code4rena.com/@Spearmint))
  19. [Maroutis](https://code4rena.com/@Maroutis)
  20. [kennedy1030](https://code4rena.com/@kennedy1030)
  21. [KupiaSec](https://code4rena.com/@KupiaSec)
  22. [blutorque](https://code4rena.com/@blutorque)
  23. [bill](https://code4rena.com/@bill)
  24. [RamenPeople](https://code4rena.com/@RamenPeople) ([kimchi](https://code4rena.com/@kimchi) and [wasabi](https://code4rena.com/@wasabi))
  25. [NentoR](https://code4rena.com/@NentoR)
  26. [GalloDaSballo](https://code4rena.com/@GalloDaSballo)
  27. [jokr](https://code4rena.com/@jokr)
  28. [mt030d](https://code4rena.com/@mt030d)
  29. [Aymen0909](https://code4rena.com/@Aymen0909)
  30. [0x007](https://code4rena.com/@0x007)
  31. [eeshenggoh](https://code4rena.com/@eeshenggoh)
  32. [crypticdefense](https://code4rena.com/@crypticdefense)
  33. [gjaldon](https://code4rena.com/@gjaldon)
  34. [gumgumzum](https://code4rena.com/@gumgumzum)
  35. [pauliax](https://code4rena.com/@pauliax)
  36. [t0x1c](https://code4rena.com/@t0x1c)
  37. [p0wd3r](https://code4rena.com/@p0wd3r)
  38. [0xabhay](https://code4rena.com/@0xabhay)
  39. [d3e4](https://code4rena.com/@d3e4)
  40. [zhaojohnson](https://code4rena.com/@zhaojohnson)
  41. [oxwhite](https://code4rena.com/@oxwhite)
  42. [Hajime](https://code4rena.com/@Hajime)
  43. [0xAadi](https://code4rena.com/@0xAadi)
  44. [TECHFUND](https://code4rena.com/@TECHFUND) ([piyushshukla](https://code4rena.com/@piyushshukla), [ravikiranweb3](https://code4rena.com/@ravikiranweb3), [dev0cloo](https://code4rena.com/@dev0cloo), [Gowtham\_Ponnana](https://code4rena.com/@Gowtham_Ponnana), [alternato7368](https://code4rena.com/@alternato7368), [engineer](https://code4rena.com/@engineer), [Ikkun](https://code4rena.com/@Ikkun) and [TECHFUND-inc](https://code4rena.com/@TECHFUND-inc))
  45. [OMEN](https://code4rena.com/@OMEN)
  46. [14si2o\_Flint](https://code4rena.com/@14si2o_Flint)
  47. [inzinko](https://code4rena.com/@inzinko)
  48. [golu](https://code4rena.com/@golu)
  49. [Bigsam](https://code4rena.com/@Bigsam)
  50. [CodeWasp](https://code4rena.com/@CodeWasp) ([slylandro\_star](https://code4rena.com/@slylandro_star), [kuprum](https://code4rena.com/@kuprum) and [audithare](https://code4rena.com/@audithare))
  51. [FastChecker](https://code4rena.com/@FastChecker)
  52. [zigtur](https://code4rena.com/@zigtur)
  53. [bigtone](https://code4rena.com/@bigtone)
  54. [Tendency](https://code4rena.com/@Tendency)
  55. [0rpse](https://code4rena.com/@0rpse)
  56. [adam-idarrha](https://code4rena.com/@adam-idarrha)
  57. [araj](https://code4rena.com/@araj)
  58. [mussucal](https://code4rena.com/@mussucal)
  59. [baz1ka](https://code4rena.com/@baz1ka)
  60. [maxim371](https://code4rena.com/@maxim371)
  61. [0xnightfall](https://code4rena.com/@0xnightfall)
  62. [aman](https://code4rena.com/@aman)
  63. [0xhacksmithh](https://code4rena.com/@0xhacksmithh)
  64. [rbserver](https://code4rena.com/@rbserver)
  65. [josephdara](https://code4rena.com/@josephdara)
  66. [cu5t0mpeo](https://code4rena.com/@cu5t0mpeo)
  67. [carlitox477](https://code4rena.com/@carlitox477)
  68. [umarkhatab\_465](https://code4rena.com/@umarkhatab_465)
  69. [xg](https://code4rena.com/@xg)
  70. [TheFabled](https://code4rena.com/@TheFabled)
  71. [ak1](https://code4rena.com/@ak1)
  72. [0xBeastBoy](https://code4rena.com/@0xBeastBoy)
  73. [honey-k12](https://code4rena.com/@honey-k12)
  74. [MSaptarshi](https://code4rena.com/@MSaptarshi)
  75. [Ocean\_Sky](https://code4rena.com/@Ocean_Sky)
  76. [DanielArmstrong](https://code4rena.com/@DanielArmstrong)
  77. [hunter\_w3b](https://code4rena.com/@hunter_w3b)
  78. [Shaheen](https://code4rena.com/@Shaheen)
  79. [twcctop](https://code4rena.com/@twcctop)
  80. [btk](https://code4rena.com/@btk)
  81. [PNS](https://code4rena.com/@PNS)
  82. [atoko](https://code4rena.com/@atoko)
  83. [Tigerfrake](https://code4rena.com/@Tigerfrake)
  84. [0xDemon](https://code4rena.com/@0xDemon)
  85. [Rhaydden](https://code4rena.com/@Rhaydden)
  86. [WildSniper](https://code4rena.com/@WildSniper)
  87. [underdog](https://code4rena.com/@underdog)
  88. [aslanbek](https://code4rena.com/@aslanbek)
  89. [stonejiajia](https://code4rena.com/@stonejiajia)
  90. [Audinarey](https://code4rena.com/@Audinarey)
  91. [m\_Rassska](https://code4rena.com/@m_Rassska)
  92. [BiasedMerc](https://code4rena.com/@BiasedMerc)
  93. [b0g0](https://code4rena.com/@b0g0)
  94. [lanrebayode77](https://code4rena.com/@lanrebayode77)
  95. [Aamir](https://code4rena.com/@Aamir)
  96. [gesha17](https://code4rena.com/@gesha17)
  97. [kinda\_very\_good](https://code4rena.com/@kinda_very_good)
  98. [carrotsmuggler](https://code4rena.com/@carrotsmuggler)
  99. [MaslarovK](https://code4rena.com/@MaslarovK)
  100. [Neon2835](https://code4rena.com/@Neon2835)
  101. [ADM](https://code4rena.com/@ADM)
  102. [Greed](https://code4rena.com/@Greed)
  103. [0xordersol](https://code4rena.com/@0xordersol)
  104. [ustazz](https://code4rena.com/@ustazz)
  105. [shui](https://code4rena.com/@shui)
  106. [Stefanov](https://code4rena.com/@Stefanov)
  107. [siguint](https://code4rena.com/@siguint)
  108. [0xnev](https://code4rena.com/@0xnev)
  109. [0xPwned](https://code4rena.com/@0xPwned)
  110. [hihen](https://code4rena.com/@hihen)
  111. [oualidpro](https://code4rena.com/@oualidpro)
  112. [K42](https://code4rena.com/@K42)
  113. [kind0dev](https://code4rena.com/@kind0dev)
  114. [adeolu](https://code4rena.com/@adeolu)
  115. [ABAIKUNANBAEV](https://code4rena.com/@ABAIKUNANBAEV)
  116. [ReadyPlayer2](https://code4rena.com/@ReadyPlayer2)
  117. [Sabit](https://code4rena.com/@Sabit)
  118. [Sparrow](https://code4rena.com/@Sparrow)
  119. [0xmystery](https://code4rena.com/@0xmystery)
  120. [jesjupyter](https://code4rena.com/@jesjupyter)
  121. [Limbooo](https://code4rena.com/@Limbooo)

This audit was judged by [alcueca](https://code4rena.com/@alcueca).

Final report assembled by [thebrittfactor](https://twitter.com/brittfactorC4) and [liveactionllama](https://twitter.com/liveactionllama).

# Summary

The C4 analysis yielded an aggregated total of 22 unique vulnerabilities. Of these vulnerabilities, 8 received a risk rating in the category of HIGH severity and 14 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 55 reports detailing issues with a risk rating of LOW severity or non-critical.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Renzo repository](https://github.com/code-423n4/2024-04-renzo), and is composed of 40 smart contracts written in the Solidity programming language and includes 3231 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (8)
## [[H-01] Withdrawals can be locked forever if recipient is a contract](https://github.com/code-423n4/2024-04-renzo-findings/issues/612)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/612), also found by [Bauchibred](https://github.com/code-423n4/2024-04-renzo-findings/issues/602) and [grearlake](https://github.com/code-423n4/2024-04-renzo-findings/issues/52)*

The [`WithdrawQueue`](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Withdraw/WithdrawQueue.sol#L303) contract allows users to request withdrawals of their ezETH tokens in exchange for a selected asset, such as ETH or an ERC20 token. After a cooldown period, users can call the [`claim()`](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Withdraw/WithdrawQueue.sol#L279) function to receive their withdrawn assets.

When the selected asset is ETH, the `claim()` function sends the ETH using the low-level `transfer()` function:

```solidity
payable(msg.sender).transfer(_withdrawRequest.amountToRedeem);
```

However, `transfer()` only forwards 2300 gas, which is not enough for the recipient to execute any non-trivial logic in a `receive()` or fallback function. For instance, it is not enough for Safes (such as [this one](https://etherscan.io/address/0xd1e6626310fd54eceb5b9a51da2ec329d6d4b68a) in use by the protocol) to receive funds, which require `>` 6k gas for the call to reach the implementation contract and emit an event:

*Note: to view the provided image, please see the original submission [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/612).*

In this case, the impact is higher than that reported by [4naly3er](https://github.com/code-423n4/2024-04-renzo/blob/main/4naly3er-report.md#m-4-call-should-be-used-instead-of-transfer-on-an-address-payable) because `claim()` requires the caller to be the same address that initiated the original withdrawal request via `withdraw()`.

If a user calls `withdraw()` from a contract account like a multisig or smart contract wallet that has a `receive()` function requiring `>2300` gas, their subsequent `claim()` call will fail permanently. The withdrawn ETH will be locked in the `WithdrawQueue` contract forever, leading to loss of funds.

### Proof of Concept

1. Alice calls `withdraw()` from her multisig wallet contract to withdraw 10 ETH worth of ezETH. The multisig contract is the `msg.sender` and gets saved as the withdrawal requester.
2. After the cooldown period, Alice tries to call `claim()` from the multisig contract. However, the multisig has a `receive()` function that uses `>2300` gas.
3. When `claim()` executes `payable(msg.sender).transfer(_withdrawRequest.amountToRedeem)`, the multisig's `receive()` fails due to out of gas, and the transaction reverts.
4. The 10 ETH is now permanently locked in `WithdrawQueue`, with no way for Alice to claim it.

### Recommended Mitigation Steps

Use `call()` instead of `transfer()` to send ETH in `claim()`:

    (bool success, ) = payable(msg.sender).call{value: _withdrawRequest.amountToRedeem}("");
    require(success, "ETH transfer failed");

This forwards all available gas and allows contract recipients to execute arbitrary logic.

### Assessed type

ETH-Transfer

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/612#event-12966845207)**

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/612#issuecomment-2138700988):**
 > The [ruling from the Supreme Court](https://docs.code4rena.com/awarding/judging-criteria/supreme-court-decisions-fall-2023#recommendation-standardize-acceptance-of-reports-based-on-automated-findings) is only consultative.
> 
> From my point of view, a bot report that can be reasonably upgraded in severity due to the specific context of the code is a valid finding. Other judges might see this differently, so this ruling shouldn't be seen as authoritative by itself in future audits. Instead, jurisprudence should arise from a broader consensus.
> 
> The [4naly3er](https://github.com/code-423n4/2024-04-renzo/blob/main/4naly3er-report.md#m-4-call-should-be-used-instead-of-transfer-on-an-address-payable) report states that:
> > The use of the deprecated `transfer()` function for an address may make the transaction fail
> 
> That description of impact merits a Medium severity; however, in this case the severity is higher due to the two-step withdrawal process. The withdrawal address is locked in the `withdraw` step, which will work fine for smart contract wallets. However, upon calling `claim`, the transaction will revert.
> 
> The actual impact for the sponsor would be severe. The first few users trying this would have their funds locked. Even after efforts of communication by the team, this would be an ongoing issue that would bring considerable trouble.
> 
> I'm ruling this as a valid High, and all the duplicates that mention the two-step withdrawal process as valid duplicates.

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/612).*

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope):**
> The PR allows contracts like multisigs to be able to claim the withdraw request in Native ETH by sending it through call instead of transfer.

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/8), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/50), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/40), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/17), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/2).



***

## [[H-02] Incorrect calculation of queued withdrawals can deflate TVL and increase ezETH mint rate](https://github.com/code-423n4/2024-04-renzo-findings/issues/395)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/395), also found by [adam-idarrha](https://github.com/code-423n4/2024-04-renzo-findings/issues/394), [araj](https://github.com/code-423n4/2024-04-renzo-findings/issues/314), [zigtur](https://github.com/code-423n4/2024-04-renzo-findings/issues/313), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/312), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/310), [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/309), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/308), [Tendency](https://github.com/code-423n4/2024-04-renzo-findings/issues/307), [p0wd3r](https://github.com/code-423n4/2024-04-renzo-findings/issues/306), [bigtone](https://github.com/code-423n4/2024-04-renzo-findings/issues/305), [maxim371](https://github.com/code-423n4/2024-04-renzo-findings/issues/304), [NentoR](https://github.com/code-423n4/2024-04-renzo-findings/issues/303), [kennedy1030](https://github.com/code-423n4/2024-04-renzo-findings/issues/302), [mussucal](https://github.com/code-423n4/2024-04-renzo-findings/issues/300), [0xnightfall](https://github.com/code-423n4/2024-04-renzo-findings/issues/299), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/298), [baz1ka](https://github.com/code-423n4/2024-04-renzo-findings/issues/297), [aman](https://github.com/code-423n4/2024-04-renzo-findings/issues/296), [0xAadi](https://github.com/code-423n4/2024-04-renzo-findings/issues/295), [0xhacksmithh](https://github.com/code-423n4/2024-04-renzo-findings/issues/292), [0rpse](https://github.com/code-423n4/2024-04-renzo-findings/issues/291), and [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/45)*

The function [`OperatorDelegator.getTokenBalanceFromStrategy()`](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L327) is used by the [`RestakeManager`](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol) to calculate the protocol TVL, which in turn is used to calculate the amount of ezETH to mint against a given value in collateral tokens.

This function, however, incorrectly checks for the queued amount of `address(this)` instead of `address(token)`; therefore, consistently failing to consider collaterals in the withdrawal process for calculation:

```Solidity
File: OperatorDelegator.sol
326:     /// @dev Gets the underlying token amount from the amount of shares + queued withdrawal shares
327:     function getTokenBalanceFromStrategy(IERC20 token) external view returns (uint256) {
328:         return
329:             queuedShares[address(this)] == 0
330:                 ? tokenStrategyMapping[token].userUnderlyingView(address(this))
331:                 : tokenStrategyMapping[token].userUnderlyingView(address(this)) +
332:                     tokenStrategyMapping[token].sharesToUnderlyingView(
333:                         queuedShares[address(token)]
334:                     );
335:     }
```

Within this code, `queuedShares[address(this)]` will always return `0`; therefore, missing the opportunity to count the contribution of `queuedShares[address(token)]`.

### Impact

Any amount of collateral in the `OperatorDelegator` withdrawal process will not be counted for TVL calculation. This causes the TVL to be low, so more ezETH will be minted for the same amount of collateral, unfairly favoring people who mint ezETH during an `OperatorDelegator` withdrawal, penalizing holders, and those who initiate a `RestakeManager` withdraw.

### Proof of Concept

The following PoC in Foundry shows how the issue can lead to a decrease in TVL. The PoC can be run in Foundry by using the setup and mock infra provided [here](<https://gist.github.com/3docSec/a4bc6254f709a6218907a3de370ae84e>).

```Solidity
pragma solidity ^0.8.19;

import "contracts/Errors/Errors.sol";
import "./Setup.sol";

contract H2 is Setup {

    function testH2() public {
        // we'll only be using stETH with unitary price for simplicity
        stEthPriceOracle.setAnswer(1e18);

        // and we start with 0 TVL
        (, , uint tvl) = restakeManager.calculateTVLs();
        assertEq(0, tvl);

        // now we have Alice depositing some stETH
        address alice = address(1234567890);
        stETH.mint(alice, 100e18);
        vm.startPrank(alice);
        stETH.approve(address(restakeManager), 100e18);
        restakeManager.deposit(IERC20(address(stETH)), 100e18);

        // ✅ TVL and balance are as expected
        (, , tvl) = restakeManager.calculateTVLs();
        assertEq(100e18, tvl);
        assertEq(100e18, ezETH.balanceOf(alice));

        // Now some liquidity enters the withdraw sequence
        vm.startPrank(OWNER);

        IERC20[] memory tokens = new IERC20[](1);
        uint256[] memory tokenAmounts = new uint256[](1);

        tokens[0] = IERC20(address(stETH));
        tokenAmounts[0] = 50e18;

        operatorDelegator1.queueWithdrawals(tokens, tokenAmounts);

        // 🚨 The collateral queued for withdrawal does not show up in TVL,
        // so the mint rate is altered
        (, , tvl) = restakeManager.calculateTVLs();
        assertEq(50e18, tvl);
    }
}
```

### Tools Used

Foundry

### Recommended Mitigation Steps

Consider changing the address used for the mapping lookup:

```diff
    /// @dev Gets the underlying token amount from the amount of shares + queued withdrawal shares
    function getTokenBalanceFromStrategy(IERC20 token) external view returns (uint256) {
        return
-           queuedShares[address(this)] == 0
+           queuedShares[address(token)] == 0
                ? tokenStrategyMapping[token].userUnderlyingView(address(this))
                : tokenStrategyMapping[token].userUnderlyingView(address(this)) +
                    tokenStrategyMapping[token].sharesToUnderlyingView(
                        queuedShares[address(token)]
                    );
    }
```

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/395#event-12916027310)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/9), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/51), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/41), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/18), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/3).



***

## [[H-03] ETH withdrawals from EigenLayer always fail due to `OperatorDelegator`'s nonReentrant `receive()`](https://github.com/code-423n4/2024-04-renzo-findings/issues/368)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/368), also found by [blutorque](https://github.com/code-423n4/2024-04-renzo-findings/issues/571), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/570), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/369), [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/367), [kennedy1030](https://github.com/code-423n4/2024-04-renzo-findings/issues/366), and [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/41)*

<https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L269>

<https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L501>

### Vulnerability details

The [`OperatorDelegator.completeQueuedWithdrawal()`](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L265) function is used by admins to finalize previously initiated withdraws of shares from EigenLayer.

We note that both this and the OperatorDelegator's `receive()` functions are `nonReentrant`:

```Solidity
File: OperatorDelegator.sol
265:     function completeQueuedWithdrawal(
266:         IDelegationManager.Withdrawal calldata withdrawal,
267:         IERC20[] calldata tokens,
268:         uint256 middlewareTimesIndex
269:     ) external nonReentrant onlyNativeEthRestakeAdmin {
270:         uint256 gasBefore = gasleft();
271:         if (tokens.length != withdrawal.strategies.length) revert MismatchedArrayLengths();
272: 
273:         // complete the queued withdrawal from EigenLayer with receiveAsToken set to true
274:         delegationManager.completeQueuedWithdrawal(withdrawal, tokens, middlewareTimesIndex, true);
---
501:     receive() external payable nonReentrant {
502:         // check if sender contract is EigenPod. forward full withdrawal eth received
503:         if (msg.sender == address(eigenPod)) {
504:             restakeManager.depositQueue().forwardFullWithdrawalETH{ value: msg.value }();
```

However, the `receive()` function is normally called by the `EigenPod` in the call stack originated by the L274 `completeQueuedWithdrawal()` when `receiveAsTokens == true` like in this case. This particular instance of reentrancy is not only acceptable but also required to allow ETH redemptions from EigenLayer. However, the `nonReentrant` modifier prevents it.

### Impact

All withdrawals that include any amount of ETH will be permanently stuck in EigenLayer and won't be redeemable. Only amounts coming from new deposits can be redeemed and the team will have no way to fill the withdrawal queues. To unblock them, the team will necessarily have to upgrade `OperatorDelegator`.

### Proof of Concept

To prove the concept, it's sufficient to upgrade `OperatorDelegator` on a mainnet fork and initiate a withdrawal that has ETH among the withdrawn strategies.

While it would be too bulky to provide a coded PoC, you can find in [this GH Gist](<https://gist.github.com/assets/145972240/0f2500e1-1f93-4daf-8a5f-509da79f2e96>) the Foundry traces of such failed call on a mainnet fork.

### Tools Used

Foundry

### Recommended Mitigation Steps

Consider removing `nonReentrant` from OperatorDelegator's `receive`, or applying the modifier only in case `msg.sender != eigenPod`.

### Assessed type

Reentrancy

**[jatinj615 (Renzo) confirmed via duplicate Issue \#571](https://github.com/code-423n4/2024-04-renzo-findings/issues/571#event-12785930232)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/10), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/56), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/42), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/19), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/4).



***

## [[H-04] Withdrawals logic allows MEV exploits of TVL changes and zero-slippage zero-fee swaps](https://github.com/code-423n4/2024-04-renzo-findings/issues/326)
*Submitted by [guhu95](https://github.com/code-423n4/2024-04-renzo-findings/issues/326), also found by [cu5t0mpeo](https://github.com/code-423n4/2024-04-renzo-findings/issues/552), [bill](https://github.com/code-423n4/2024-04-renzo-findings/issues/551), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/544), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/513), gjaldon ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/512), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/146)), 0xabhay ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/444), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/260)), WildSniper ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/443), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/261), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/257)), [0rpse](https://github.com/code-423n4/2024-04-renzo-findings/issues/442), GoatedAudits ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/441), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/415), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/414)), honey-k12 ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/440), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/327)), Bauchibred ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/439), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/249)), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/438), blutorque ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/437), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/420)), Tendency ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/436), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/419)), crypticdefense ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/435), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/253)), Fassi\_Security ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/434), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/259)), SBSecurity ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/433), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/418), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/245)), peanuts ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/432), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/423)), tapir ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/422), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/283), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/240)), [MSaptarshi](https://github.com/code-423n4/2024-04-renzo-findings/issues/421), kennedy1030 ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/417), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/243)), [OMEN](https://github.com/code-423n4/2024-04-renzo-findings/issues/416), LessDupes ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/413), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/408)), [0x007](https://github.com/code-423n4/2024-04-renzo-findings/issues/380), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/325), zzykxx ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/321), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/320), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/244)), [gumgumzum](https://github.com/code-423n4/2024-04-renzo-findings/issues/318), [stonejiajia](https://github.com/code-423n4/2024-04-renzo-findings/issues/258), [Audinarey](https://github.com/code-423n4/2024-04-renzo-findings/issues/256), [RamenPeople](https://github.com/code-423n4/2024-04-renzo-findings/issues/255), [Ocean\_Sky](https://github.com/code-423n4/2024-04-renzo-findings/issues/251), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/248), [underdog](https://github.com/code-423n4/2024-04-renzo-findings/issues/247), [josephdara](https://github.com/code-423n4/2024-04-renzo-findings/issues/246), [p0wd3r](https://github.com/code-423n4/2024-04-renzo-findings/issues/242), [aslanbek](https://github.com/code-423n4/2024-04-renzo-findings/issues/241), [d3e4](https://github.com/code-423n4/2024-04-renzo-findings/issues/239), [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/42), grearlake ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/36), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/34)), and [GalloDaSballo](https://github.com/code-423n4/2024-04-renzo-findings/issues/11)*

Deposit and withdrawal requests can be done immediately with no costs or fees, and both use the current oracle prices and TVL calculation ([`deposit`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L499-L504), and [`withdraw`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L217)). Crucially, the [withdrawal amount is calculated at withdrawal request submission time](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L220C1-L224C11) instead of at withdrawal claim time. Any small change in either ezETH value or in the price of a collateral token can be exploited at no cost by MEV. Specifically, if the price increases, a deposit is made before the increase, and a withdrawal request immediately after.

Additionally, in case of a supported LST's sudden change in price (for example, due to price manipulation, an exploit of that LST, due to consensus layer penalties (slashing), or liquidity issues), external holders of that LST may frontrun the change, deposit the LST into Renzo, and immediately request a withdrawal of another asset (e.g., native ETH). In such situations, Renzo functions as a **zero-slippage zero-fees oracle-price-based DEX** for LSTs and ETH up to the TVL cap for the affected LST. Zero-slippage zero-fee oracle-price-based designs are notoriously vulnerable to both oracle manipulation and oracle latency attacks if not carefully prevented.

### Impact

The newly introduced frontrunning vector, due to incurring only gas fees, and no fee that is proportional to the size of the "trade", allows profitably exploiting most TVL and oracle price changes, and exploiting previously exploitable updates (via Balancer's [usage of `getRate()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RateProvider/BalancerRateProvider.sol#L28C1-L41C6)) and even more profitably via the new vector.

The impact is that value, that otherwise should be distributed to ezETH holders, is constantly lost to MEV.

Additionally, ezETH holders lose value due to facilitating asset swaps with no slippage and no fees based on outdated oracle prices.

### Proof of Concept

**Scenario 1 (MEV, price increase):**

1. A transaction that will increase the TVL value without minting or burning ezETH, such as a Chainlink oracle update or EigenLayer rewards withdrawal, is observed.
2. An attacker sandwiches the transaction by depositing asset A right before it (minting ezETH to themselves).
3. The attacker completes the sandwich by submitting a withdrawal request for asset A after the "target" transaction. This sends the ezETH to `WithdrawQueue`, and credits the attacker with a larger amount of A than was just deposited, corresponding to the updated price of ezETH.
4. The attacker realizes an immediate, same block profit - a larger amount of the same asset, due to the price increase and credit of future withdrawal amount, and no fee being charged.
5. Value that would otherwise be distributed to holders of ezETH was lost to the attacker.

**Scenario 2 (malicious):**

1. Asset A experiences a sharp price decline due to slashing, exploit, or other factors.
2. An attacker borrows LST asset A from on-chain lending protocols. This is done to reduce the assets available for others to short the price manipulation of the next step.
3. The attacker buys up even more of the LST on CEX and DEX, running up the price of that asset, such that a manipulated price is reported by oracles.
4. The attacker deposits all asset A into Renzo, being credited with an outsized amount of ezETH due to the inflated price of the collateral.
5. The attacker immediately submits a withdrawal request of asset B, which upon conversion uses the inflated value of asset A in Renzo's TVL.
6. 7 days later, upon withdrawal claiming, the attacker withdraws the inflated amount of asset B.

**Scenario 3 (MEV, price decrease, zero-slippage zero-fees DEX):**

1. A supported LST experiences a sudden change in price due to factors such as price manipulation, an exploit of that LST, consensus layer penalties (slashing), or liquidity issues.
2. Existing external holders of the LST, or arbitrageurs borrowing the asset, frontrun the transaction that changes the oracle price by depositing the LST into Renzo, and immediately requesting a withdrawal of another asset (e.g., native ETH or another LST). Using Renzo as a zero-slippage oracle-price-based DEX.
3. After the withdrawal delay, the attackers claim their withdrawal, receiving the other asset at the pre-change price, effectively exploiting the ezETH holders.

### Recommended Mitigation Steps

The redemption conversion should be performed at both request and claim time. If it results in a lower redeem value, that value should be used for the claim instead of the initial redeem amount. Additionally, a rate limit or a short delay on deposits with similar protection can be added as well.

```diff
function claim(uint256 withdrawRequestIndex) external nonReentrant {
    ...
+   // All the code converting from ezETH amount to amountToRedeem as is done in withdraw()

+   if (amountToRedeem < _withdrawRequest.amountToRedeem) {
+       _withdrawRequest.amountToRedeem = amountToRedeem;
+   }
}
```

### Assessed type

MEV

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/326#issuecomment-2117487124):**
 > The sponsor's comment in [#259](https://github.com/code-423n4/2024-04-renzo-findings/issues/259#issuecomment-2107771002) is relevant here, on why withdrawals are priced on `withdraw`,  and not `claim`. The resulting implementation might have to take a trade-off between being arbitraged one way or another, or opt for a different implementation altogether.

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/326#event-12916111345)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope):**
> The PR reduces the risk of arbitrage at withdraw by calculating the amount of withdrawing asset at time of withdraw as well as claim and returns the min of both amount to user.

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/16), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/58), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/20).



***

## [[H-05] Withdrawals of rebasing tokens can lead to insolvency and unfair distribution of protocol reserves](https://github.com/code-423n4/2024-04-renzo-findings/issues/282)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/282), also found by [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/599), [peanuts](https://github.com/code-423n4/2024-04-renzo-findings/issues/467), guhu95 ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/466), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/285)), [bill](https://github.com/code-423n4/2024-04-renzo-findings/issues/290), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/289), and [RamenPeople](https://github.com/code-423n4/2024-04-renzo-findings/issues/288)*

The [`WithdrawQueue`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol) contract allows users to withdraw their funds in various tokens, including liquid staking derivatives (LSDs) such as stETH. The [`withdraw()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L206) function calculates the amount of the specified `_assetOut` token equivalent to the ezETH being withdrawn [using](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L229) the `renzoOracle.lookupTokenAmountFromValue()` function. This amount is then stored in the `amountToRedeem` field of a new `WithdrawRequest` struct, which is added to the user's `withdrawRequests` array and the token's `claimReserve`.

When the user later calls [`claim()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L279), the contract transfers the `amountToRedeem` to the user via the [`IERC20.transfer()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L305) function.

However, this implementation does not properly handle rebasing tokens like stETH. The stETH balance of the `WithdrawQueue` can change between the time a withdrawal is recorded and when it is claimed, even though the contract's stETH shares remain constant.

If the stETH balance decreases during this period due to a rebasing event (e.g., a slashing of the staked ETH), the `amountToRedeem` stored in the `WithdrawRequest` may exceed the contract's actual stETH balance at the time of claiming. As a result, the withdrawal can fail or result in the user receiving a larger share of the total protocol reserves than intended.

The issue can be illustrated by comparing the behavior of withdrawals for non-rebasing and rebasing LSDs:

1. Non-rebasing LSD (e.g., wBETH):
    - User A requests a withdrawal of 10 wBETH (worth 10 ETH) from the protocol.
    - While the withdrawal is pending, wBETH's underlying staked ETH suffers a 50% slashing event.
    - The price of wBETH drops to 0.5 ETH per token due to the slashing.
    - When User A claims their withdrawal, they receive 10 wBETH, which is now worth only 5 ETH.
    - User A bears the loss from the slashing event.

2. Rebasing LSD (e.g., stETH):
    - User B requests a withdrawal of 10 stETH (worth 10 ETH) from the protocol.
    - While the withdrawal is pending, the underlying staked ETH suffers a 50% slashing event.
    - Everyone's stETH balances are rebased to maintain the ETH peg, so the protocol's stETH balance is halved.
    - When User B claims their withdrawal, they receive the original 10 stETH (still worth 10 ETH) as recorded in the withdrawal request.
    - The protocol bears the loss from the slashing event, as it has sent out more than its fair share of the rebased stETH balance.

### Impact

The current withdrawal mechanism for rebasing tokens like stETH can lead to:

- **Unfair distribution of funds:** Users who claim their withdrawals after a rebasing event that decreases the contract's balance will receive a larger share of the reserves than intended, at the expense of other users.
- **Withdrawal failures:** If the contract's balance falls below the total `amountToRedeem` of all pending withdrawals due to rebasing, users will face transaction failures when attempting to claim their withdrawals.

### Proof of Concept

We can validate the vulnerability through a Foundry test case POC. This test case will simulate the exploit scenario and confirm the issue by performing the following actions:

1. Alice and Bob initiate withdrawals of their ezETH shares for stETH.
2. Simulate a negative rebasing event by transferring 10% of stETH balance from the `withdrawQueue` contract.
3. Alice claims her withdrawal successfully, receiving her original stETH amount.
4. Bob's attempt to claim his withdrawal fails due to insufficient stETH balance.
5. Verify that ezETH supply remains unchanged while TVL is significantly reduced, demonstrating ezETH becoming uncollateralized.

The PoC can be run in Foundry by using the setup and mock infra provided [here](<https://gist.github.com/3docSec/a4bc6254f709a6218907a3de370ae84e>).

<details>

```solidity
pragma solidity ^0.8.19;

import "contracts/Errors/Errors.sol";
import "./Setup.sol";

contract H6 is Setup {

    function testH6() public {
        // we set the buffer to something reasonably high
        WithdrawQueueStorageV1.TokenWithdrawBuffer[] memory buffers = new WithdrawQueueStorageV1.TokenWithdrawBuffer[](2);

        buffers[0] = WithdrawQueueStorageV1.TokenWithdrawBuffer(address(stETH), 100e18 - 1);
        buffers[1] = WithdrawQueueStorageV1.TokenWithdrawBuffer(address(cbETH), 100e18 - 1);

        vm.startPrank(OWNER);
        withdrawQueue.updateWithdrawBufferTarget(buffers);

        // we'll be using stETH and cbETH with unitary price for simplicity
        stEthPriceOracle.setAnswer(1e18);
        cbEthPriceOracle.setAnswer(1e18);

        // and we start with 0 TVL
        (, , uint tvl) = restakeManager.calculateTVLs();
        assertEq(0, tvl);

        // let's then imagine that Alice and Bob hold 90 and 10 ezETH each
        address alice = address(1234567890);
        address bob = address(1234567891);
        stETH.mint(alice, 100e18);
        vm.startPrank(alice);
        stETH.approve(address(restakeManager), 100e18);
        restakeManager.deposit(IERC20(address(stETH)), 100e18);
        ezETH.transfer(bob, 10e18);

        // ✅ TVL and balance are as expected
        (, , tvl) = restakeManager.calculateTVLs();
        assertEq(100e18, tvl);
        assertEq(90e18, ezETH.balanceOf(alice));
        assertEq(10e18, ezETH.balanceOf(bob));

        // Now Bob initiates withdrawal of their shares
        vm.startPrank(bob);
        ezETH.approve(address(withdrawQueue), 10e18);
        withdrawQueue.withdraw(10e18, address(stETH));

        // Alice, too, initiates withdrawal of their shares
        vm.startPrank(alice);
        ezETH.approve(address(withdrawQueue), 90e18 - 1);
        withdrawQueue.withdraw(90e18 - 1, address(stETH));

        // ☢️ time passes, and an stETH negative rebasing happens, wiping
        // 10% of the balance
        vm.startPrank(address(withdrawQueue));
        stETH.transfer(address(1), 10e18);

        vm.warp(block.timestamp + 10 days);

        // 🚨 now, since WithdrawQueue checked availability at withdrawal initiation
        // only and didn not account for the possibility of rebases, the 10% loss
        // has been completely dodged by Alice and is attributed to the last
        // user exiting.
        vm.startPrank(alice);
        withdrawQueue.claim(0);
        assertEq(90e18 - 1, stETH.balanceOf(alice));

        // 🚨 not only Bob can't withdraw
        vm.startPrank(bob);
        vm.expectRevert();
        withdrawQueue.claim(0);

        // 🚨 but ezETH as a whole also became completely uncollateralized
        assertEq(10e18 + 1, ezETH.totalSupply());
        (, , tvl) = restakeManager.calculateTVLs();
        assertEq(1, tvl);
    }
}
```

</details>

### Recommended Mitigation Steps

To address the issue of unfair distribution of funds when withdrawing rebasing tokens like stETH, the `WithdrawQueue` contract should store and transfer the user's withdrawal as stETH shares instead of a fixed stETH amount.

When a user initiates a withdrawal with stETH as the `_assetOut`, the contract should convert the calculated `amountToRedeem` to stETH shares using the `stETH.getSharesByPooledEth()` function:

    uint256 sharesAmount = IStETH(stETHAddress).getSharesByPooledEth(amountToRedeem);

The resulting `sharesAmount` should be stored in the `WithdrawRequest` struct instead of the `amountToRedeem`.

When the user calls `claim()`, the contract should transfer the stETH shares directly to the user using the `stETH.transferShares()` function:

    IStETH(stETHAddress).transferShares(msg.sender, sharesAmount);

By storing and transferring stETH shares instead of a fixed stETH amount, the contract ensures that each user receives their fair share of the stETH balance, regardless of any rebasing events that occur between the time of the withdrawal request and the claim.

To implement this mitigation, the contract should:

1. Check if the `_assetOut` is stETH when processing a withdrawal request.
2. If so, convert the `amountToRedeem` to stETH shares using `stETH.getSharesByPooledEth()` and store the shares amount in the `WithdrawRequest` struct.
3. Update the `claim()` function to check if the withdrawal is in stETH and, if so, transfer the shares directly using `stETH.transferShares()` instead of using the standard `IERC20.transfer()` function.

Note that this mitigation is specific to stETH and may need to be adapted for other rebasing tokens that use a similar shares-based system.

Furthermore, the `claimReserve` and `withdrawalBufferTarget` for stETH would also need to be stored in shares and converted to underlying in TVL and withdraw buffer calculations, respectively.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/282#issuecomment-2133000450):**
 > I'm going to sustain the high severity on the grounds that:
>  - If the stEth balance increases, as it normally does, users lose value in comparison to non-rebasing LSTs.
>  - If the stEth balance decreases, the protocol loses value in comparison to non-rebasing LSTs.
>  - If the stEth balance decreases, the protocol might DoS.
> 
> The users that win in a slashing event are not the same users that lose during normal operation.

**[jatinj615 (Renzo) acknowledged](https://github.com/code-423n4/2024-04-renzo-findings/issues/282#event-13024907465)**



***

## [[H-06] The amount of `xezETH` in circulation will not represent the amount of `ezETH` tokens 1:1](https://github.com/code-423n4/2024-04-renzo-findings/issues/145)
*Submitted by [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/145), also found by [0x007](https://github.com/code-423n4/2024-04-renzo-findings/issues/140), [GoatedAudits](https://github.com/code-423n4/2024-04-renzo-findings/issues/139), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/138), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/137), [mt030d](https://github.com/code-423n4/2024-04-renzo-findings/issues/136), [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/133), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/132), and [GalloDaSballo](https://github.com/code-423n4/2024-04-renzo-findings/issues/14)*

The protocol allows to deposit `ETH`/`WETH` (or the specific chain native currency) on a supported L2 in order to mint `ezETH` tokens, this is the process:

1. User mints `xezETH` on L2s via [`xRenzoDeposit::deposit()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L204) in exchange for either `ETH` or `WETH`. The `xezETH` are minted based on the **current** `ezETH` valuation.
2. After some time the bridge sweepers transfer the `ETH`/`WETH` collected to the L1, via [`xRenzoDeposit::sweep()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L414). The funds are transferred to the `xRenzoBridge` contract on L1 via Connext.
3. Connext calls [`xRenzoBridge::xReceive()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol#L139) on L1 which will receive the `ETH`/`WETH` and deposit them in the protocol via [`RestakeManager::depositETH()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L592). This will mint `ezETH` tokens based on the **current** `ezETH` valuation, the `ezETH` tokens will then be locked in the lockbox in exchange for `xezETH`, which are then immediately burned because an equivalent amount should have already been minted on the L2 during step `1`.

Theoretically, the amount of `xezETH` tokens minted during step `1` should be the same as the amount of `ezETH` tokens minted during step `3`, but because on both steps the tokens are minted at the current valuation, and the valuation changes over time, there will be a discrepancy between the amount of `xezETH` and `ezETH` tokens in circulation.

This is an issue because [`XERC20Lockbox::withdraw()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/xERC20/contracts/XERC20Lockbox.sol#L126-L135) always exchanges `xezETH` for `ezETH` 1:1.

### Impact

The price of `ezETH` is expected to increase over time. This will create a situation where there will be more `xezETH` in circulation than `ezETH`, rendering some `xezETH` worthless and impossible to redeem for `ezETH`.

A situation in which the `ezETH` valuation decreases instead of increasing is also problematic, because the protocol will mint less `xezETH` than it should. 

The discrepancy will become bigger and bigger with time.

### Proof of Concept

As an example, let's assume `ezETH` valuation is currently `1 ETH`:

1. Alice deposits `1 ETH` on L2 and receives `1 xezETH`.
2. Some time passes and the valuation of `ezETH` increases to `2ETH` (unrealistic, but allows simple math).
3. The bridge sweeper calls `sweep()`, transferring the `1 ETH` to the `xRenzoBridge` contract on L1.
4. The `xRenzoBridge` deposits the received `1 ETH` in the `RestakeManager`, which mints `0.5 ezETH` because the `ezETH` valuation doubled.
5. The `0.5 ezETH` is locked in the lockbox, `0.5 xezETH` are minted in return and immediately burned.

The situation now is the following:

- Alice has `1 xezETH` on L2.
- The lockbox contains `0.5 ezETH` on L1.

Alice can at best redeem `0.5 xezETH` in exchange for `0.5 ezETH`, and the remaining `0.5 xezETH` is worthless. The amount of value she can redeem is the correct one, (`1 ETH`), but now there are `xezETH` in circulation that are not backed by `ezETH`.

### Recommended Mitigation Steps

The protocol should track the amount of `xezETH` tokens minted via [`xRenzoDeposit::deposit()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L204) on the L2 and mint the equivalent amount of `ezETH` tokens on L1 when [`xRenzoBridge::xReceive()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol#L139) is executed by passing the necessary data on the [`xcall()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L434-L442) to Connext.

If this is implemented it's possible for the valuation of `ezETH` tokens to change instantly after [`xRenzoBridge::xReceive()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol) is executed, this is because the amount of `ezETH` tokens is not minted based on the current valuation anymore. As explained in other reports, the protocol will be subject to instant `ezETH` valuation changes (increase/decrease) no matter what (rewards, slashing, penalties), and should gracefully handle these situations via appropriate deposit and withdrawals queues.

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/145#issuecomment-2110038561):**
 > Yes, theoretically it is correct. But the protocol tackles this by sending the updated mint rate of ezETH frequently to L2s and also sweeps funds every hour if above batch size keeping the collateralization in place for ezETH. Also the `bridgeRouterFee` (5 bps) deducted on L2 if the transactions goes through slow path (during which mint rate of ezETH can rise) the extra 5 bps routerFee deducted on L2 is accumulated in minting ezETH on L1 in `xRenzoBridge::xReceive` instead of getting deducted by connext routers. 

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/145#issuecomment-2127148545):**
 > The long term effect of this is akin to bad debt in lending protocols. Eventually, the protocol or the (last) users need to assume the losses.

**[0xTenma (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/145#issuecomment-2132084175):**
> I think severity of this issue should be Medium instead of High because there is no direct loss of funds possible here. If the ratio of xezETH to ezETH is not equal 1:1 in any case then it is only possible and the protocol sends the updated mint rate of ezETH frequently to L2s to avoid this situation. 
> Furthermore, According to C4 docs:
> > 2 — Med: Assets not at direct risk, but the function of the protocol or its availability could be impacted, or leak value with a hypothetical attack path with stated assumptions, but external requirements.
> 
> Stated assumptions and external requirement such as oracle delay are required to face to this issue.

**[jatinj615 (Renzo) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/145#issuecomment-2132105899):**
 > @alcueca - to add more to it as I have explained in the comment above and discussion in [#70](https://github.com/code-423n4/2024-04-renzo-findings/issues/70). The ezETH in prod is over collateralised due to the fact that in some cases (when connext routers don't have enough liquidity to process fast path) the 5bps deducted on L2 is used to collateralise ezETH on L1 which is why lockbox currently has more ezETH against the xezETH minted on L1. Team has been monitoring and keeping a track on it. 
 >
 > Considering the above argument, please confirm on the severity. 

**[0xCiphky (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/145#issuecomment-2132318968):**
 > Respectfully, I believe this should remain as High severity:
> 
> - The finding clearly demonstrates a realistic scenario where the system could become insolvent, resulting in a loss of funds for users. Despite the current over-collateralization and precautions, there remains a long-term risk.
> - The audited implementation contains blockages that will affect efforts to maintain collateralization for ezETH. For example, if the MaxTVL is reached, the protocol cannot deposit in L1, causing an accumulation of minted L2 tokens until it becomes possible to deposit again, which could take a significant amount of time.
> - This issue can be intentionally exploited by users whenever the price on the L1 side is higher than on the L2 side.



***

## [[H-07] DOS of `completeQueuedWithdrawal` when ERC20 buffer is filled](https://github.com/code-423n4/2024-04-renzo-findings/issues/87)
*Submitted by [Aymen0909](https://github.com/code-423n4/2024-04-renzo-findings/issues/87), also found by tapir ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/566), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/94), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/92)), [crypticdefense](https://github.com/code-423n4/2024-04-renzo-findings/issues/365), [gjaldon](https://github.com/code-423n4/2024-04-renzo-findings/issues/93), [eeshenggoh](https://github.com/code-423n4/2024-04-renzo-findings/issues/91), [gumgumzum](https://github.com/code-423n4/2024-04-renzo-findings/issues/90), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/89), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/88), [GoatedAudits](https://github.com/code-423n4/2024-04-renzo-findings/issues/85), and [pauliax](https://github.com/code-423n4/2024-04-renzo-findings/issues/25)*

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Delegation/OperatorDelegator.sol#L299-L303>

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Deposits/DepositQueue.sol#L134-L137>

### Issue Description

When the `OperatorDelegator::completeQueuedWithdrawal` function is invoked to finalize a withdrawal from EL, it attempts to utilize the accumulated ERC20 tokens to fill the ERC20 withdrawal buffer, as demonstrated in the code snippet below:

```solidity
function completeQueuedWithdrawal(
    IDelegationManager.Withdrawal calldata withdrawal,
    IERC20[] calldata tokens,
    uint256 middlewareTimesIndex
) external nonReentrant onlyNativeEthRestakeAdmin {
    uint256 gasBefore = gasleft();
    if (tokens.length != withdrawal.strategies.length) revert MismatchedArrayLengths();

    // Complete the queued withdrawal from EigenLayer with receiveAsToken set to true
    delegationManager.completeQueuedWithdrawal(withdrawal, tokens, middlewareTimesIndex, true);

    IWithdrawQueue withdrawQueue = restakeManager.depositQueue().withdrawQueue();
    for (uint256 i; i < tokens.length; ) {
        if (address(tokens[i]) == address(0)) revert InvalidZeroInput();

        // Deduct queued shares for tracking TVL
        queuedShares[address(tokens[i])] -= withdrawal.shares[i];

        // Check if the token is not Native ETH
        if (address(tokens[i]) != IS_NATIVE) {
            // Check the withdrawal buffer and fill if below buffer target
            uint256 bufferToFill = withdrawQueue.getBufferDeficit(address(tokens[i]));

            // Get the balance of this contract
            uint256 balanceOfToken = tokens[i].balanceOf(address(this));
            if (bufferToFill > 0) {
                bufferToFill = (balanceOfToken <= bufferToFill) ? balanceOfToken : bufferToFill;

                // Update the amount to send to the operator Delegator
                balanceOfToken -= bufferToFill;

                // Safely approve for depositQueue
                tokens[i].safeApprove(address(restakeManager.depositQueue()), bufferToFill);

                // Fill the Withdraw Buffer via depositQueue
                restakeManager.depositQueue().fillERC20withdrawBuffer(
                    address(tokens[i]),
                    bufferToFill
                );
            }

            // Deposit remaining tokens back to EigenLayer
            if (balanceOfToken > 0) {
                _deposit(tokens[i], balanceOfToken);
            }
        }
        unchecked {
            ++i;
        }
    }

    // Emit the Withdraw Completed event with withdrawalRoot
    emit WithdrawCompleted(
        delegationManager.calculateWithdrawalRoot(withdrawal),
        withdrawal.strategies,
        withdrawal.shares
    );
    // Record the current spent gas
    _recordGas(gasBefore);
}
```

The function iterates over the withdrawn tokens array and, for each token, checks if the withdrawal buffer needs filling. If required, the function attempts to call the `depositQueue::fillERC20withdrawBuffer` function, which is responsible for directing the ERC20 to the withdrawal queue contract to fill the buffer.

The issue arises because the `depositQueue::fillERC20withdrawBuffer` function can only be accessed by the `RestakeManager` contract, as it enforces the `onlyRestakeManager` modifier, as depicted below:

```solidity
/// @dev Allows only the RestakeManager address to call functions
modifier onlyRestakeManager() {
    if (msg.sender != address(restakeManager)) revert NotRestakeManager();
    _;
}

function fillERC20withdrawBuffer(
    address _asset,
    uint256 _amount
) external nonReentrant onlyRestakeManager {
    ...
}
```

Consequently, when the `completeQueuedWithdrawal` function attempts this call, it reverts because `OperatorDelegator` lacks access to the `depositQueue::fillERC20withdrawBuffer` function. This results in the entire withdrawal completion call reverting, rendering it impossible for the admin to retrieve funds from EL.

In summary, this issue triggers a persistent DOS of the `OperatorDelegator::completeQueuedWithdrawal` function, preventing the protocol and users from withdrawing funds from EL and resulting in a loss of funds.

### Impact

Persistent DOS of the `OperatorDelegator::completeQueuedWithdrawal` function, preventing the protocol from withdrawing funds from EL and leading to fund losses for the protocol and users.

### Tools Used

VS Code

### Recommended Mitigation

The simplest resolution is to grant access to the `depositQueue::fillERC20withdrawBuffer` function to everyone by removing the `onlyRestakeManager` modifier. This adjustment introduces no vulnerabilities to the protocol since any user calling it effectively donates funds to the protocol (to the withdrawal queue).

### Assessed type

DoS

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/87#event-12925535546)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/11), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/57), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/43), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/22), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/5).



***

## [[H-08] Incorrect withdraw queue balance in TVL calculation](https://github.com/code-423n4/2024-04-renzo-findings/issues/28)
*Submitted by [pauliax](https://github.com/code-423n4/2024-04-renzo-findings/issues/28), also found by [BiasedMerc](https://github.com/code-423n4/2024-04-renzo-findings/issues/396), [NentoR](https://github.com/code-423n4/2024-04-renzo-findings/issues/281), [gjaldon](https://github.com/code-423n4/2024-04-renzo-findings/issues/280), [crypticdefense](https://github.com/code-423n4/2024-04-renzo-findings/issues/279), [zhaojohnson](https://github.com/code-423n4/2024-04-renzo-findings/issues/278), [twcctop](https://github.com/code-423n4/2024-04-renzo-findings/issues/277), [bigtone](https://github.com/code-423n4/2024-04-renzo-findings/issues/276), [b0g0](https://github.com/code-423n4/2024-04-renzo-findings/issues/275), [DanielArmstrong](https://github.com/code-423n4/2024-04-renzo-findings/issues/274), [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/273), [GoatedAudits](https://github.com/code-423n4/2024-04-renzo-findings/issues/272), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/270), [zigtur](https://github.com/code-423n4/2024-04-renzo-findings/issues/268), [xg](https://github.com/code-423n4/2024-04-renzo-findings/issues/267), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/266), [lanrebayode77](https://github.com/code-423n4/2024-04-renzo-findings/issues/265), [blutorque](https://github.com/code-423n4/2024-04-renzo-findings/issues/264), [aslanbek](https://github.com/code-423n4/2024-04-renzo-findings/issues/263), [Aamir](https://github.com/code-423n4/2024-04-renzo-findings/issues/262), [araj](https://github.com/code-423n4/2024-04-renzo-findings/issues/226), [TheFabled](https://github.com/code-423n4/2024-04-renzo-findings/issues/225), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/223), [tapir](https://github.com/code-423n4/2024-04-renzo-findings/issues/222), [eeshenggoh](https://github.com/code-423n4/2024-04-renzo-findings/issues/208), [p0wd3r](https://github.com/code-423n4/2024-04-renzo-findings/issues/204), [peanuts](https://github.com/code-423n4/2024-04-renzo-findings/issues/203), [Greed](https://github.com/code-423n4/2024-04-renzo-findings/issues/199), [0xordersol](https://github.com/code-423n4/2024-04-renzo-findings/issues/197), [14si2o\_Flint](https://github.com/code-423n4/2024-04-renzo-findings/issues/196), [guhu95](https://github.com/code-423n4/2024-04-renzo-findings/issues/195), m\_Rassska ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/194), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/169)), [ustazz](https://github.com/code-423n4/2024-04-renzo-findings/issues/179), [maxim371](https://github.com/code-423n4/2024-04-renzo-findings/issues/178), [Fassi\_Security](https://github.com/code-423n4/2024-04-renzo-findings/issues/177), [shui](https://github.com/code-423n4/2024-04-renzo-findings/issues/176), [mt030d](https://github.com/code-423n4/2024-04-renzo-findings/issues/175), [aman](https://github.com/code-423n4/2024-04-renzo-findings/issues/174), [rbserver](https://github.com/code-423n4/2024-04-renzo-findings/issues/173), [mussucal](https://github.com/code-423n4/2024-04-renzo-findings/issues/172), [josephdara](https://github.com/code-423n4/2024-04-renzo-findings/issues/171), [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/170), [honey-k12](https://github.com/code-423n4/2024-04-renzo-findings/issues/168), [0xnightfall](https://github.com/code-423n4/2024-04-renzo-findings/issues/167), [Maroutis](https://github.com/code-423n4/2024-04-renzo-findings/issues/166), [Aymen0909](https://github.com/code-423n4/2024-04-renzo-findings/issues/165), [OMEN](https://github.com/code-423n4/2024-04-renzo-findings/issues/164), [Stefanov](https://github.com/code-423n4/2024-04-renzo-findings/issues/163), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/162), [hunter\_w3b](https://github.com/code-423n4/2024-04-renzo-findings/issues/161), [gesha17](https://github.com/code-423n4/2024-04-renzo-findings/issues/160), [baz1ka](https://github.com/code-423n4/2024-04-renzo-findings/issues/159), [kinda\_very\_good](https://github.com/code-423n4/2024-04-renzo-findings/issues/158), [carlitox477](https://github.com/code-423n4/2024-04-renzo-findings/issues/156), [0xAadi](https://github.com/code-423n4/2024-04-renzo-findings/issues/155), [0rpse](https://github.com/code-423n4/2024-04-renzo-findings/issues/154), [ak1](https://github.com/code-423n4/2024-04-renzo-findings/issues/153), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/152), [0xhacksmithh](https://github.com/code-423n4/2024-04-renzo-findings/issues/151), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/150), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/147), [adam-idarrha](https://github.com/code-423n4/2024-04-renzo-findings/issues/144), [siguint](https://github.com/code-423n4/2024-04-renzo-findings/issues/143), [0xnev](https://github.com/code-423n4/2024-04-renzo-findings/issues/142), [0xPwned](https://github.com/code-423n4/2024-04-renzo-findings/issues/141), [carrotsmuggler](https://github.com/code-423n4/2024-04-renzo-findings/issues/53), [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/43), [grearlake](https://github.com/code-423n4/2024-04-renzo-findings/issues/27), and oakcobalt ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/16), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/15))*

When calculating TVL it iterates over all the operator delegators and inside it iterates over all the collateral tokens. 

```solidity
        for (uint256 i = 0; i < odLength; ) {
            ...

            // Iterate through the tokens and get the value of each
            uint256 tokenLength = collateralTokens.length;
            for (uint256 j = 0; j < tokenLength; ) {
                ...

                // record token value of withdraw queue
                if (!withdrawQueueTokenBalanceRecorded) {
                    totalWithdrawalQueueValue += renzoOracle.lookupTokenValue(
                        collateralTokens[i],
                        collateralTokens[j].balanceOf(withdrawQueue)
                    );
                }

                unchecked {
                    ++j;
                }
            }

            ...

            unchecked {
                ++i;
            }
        }
```

However, the balance of `withdrawQueue` is incorrectly fetched, specifically this line:

```solidity
                    totalWithdrawalQueueValue += renzoOracle.lookupTokenValue(
                        collateralTokens[i],
                        collateralTokens[j].balanceOf(withdrawQueue)
                    );
```

It uses an incorrect index of the outer loop `i` to access the `collateralTokens`. `i` belongs to the operator delegator index, thus the returned value will not represent the real value of the token. For instance, if there is 1 OD and 3 collateral tokens, it will add the balance of the first token 3 times and neglect the other 2 tokens. If there are more ODs than collateral tokens, the the execution will revert (index out of bounds).

This calculation impacts the TVL which is the essential data when calculating mint/redeem and other critical values. A miscalculation in TVL could have devastating results.

### Proof of Concept

A simplified version of the function to showcase that the same token (in this case `address(1)`) is emitted multiple times and other tokens are untouched:

```solidity
contract RestakeManager {

    address[] public operatorDelegators;

    address[] public collateralTokens;

    event CollateralTokenLookup(address token);

    constructor() {
        operatorDelegators.push(msg.sender);

        collateralTokens.push(address(1));
        collateralTokens.push(address(2));
        collateralTokens.push(address(3));
    }

    function calculateTVLs() public {
        // Iterate through the ODs
        uint256 odLength = operatorDelegators.length;

        for (uint256 i = 0; i < odLength; ) {
            // Iterate through the tokens and get the value of each
            uint256 tokenLength = collateralTokens.length;
            for (uint256 j = 0; j < tokenLength; ) {
                emit CollateralTokenLookup(collateralTokens[i]);

                unchecked {
                    ++j;
                }
            }

            unchecked {
                ++i;
            }
        }
    }
}
```

### Recommended Mitigation Steps

Change to `collateralTokens[j]`.

### Assessed type

Math

**[jatinj615 (Renzo) confirmed and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/28#issuecomment-2107661134):**
 > Yeah, the index should be `j` not `i`. 

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/12), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/55), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/44), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/23), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/6).



***

# Medium Risk Findings (14)
## [[M-01] Withdrawals can fail due to deposits reverting in `completeQueuedWithdrawal()`](https://github.com/code-423n4/2024-04-renzo-findings/issues/604)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/604), also found by 0x73696d616f ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/606), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/605))*

The [`OperatorDelegator.completeQueuedWithdrawal()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Delegation/OperatorDelegator.sol#L265) function serves to finalize a queued withdrawal consisting of different tokens, sending the withdrawn tokens to the `WithdrawQueue` contract up to the buffer amount, and depositing any excess tokens back into the corresponding EigenLayer strategy.

The issue is that the [call](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Delegation/OperatorDelegator.sol#L168) to `strategyManager.depositIntoStrategy()` used to deposit any amount of excess tokens back into EigenLayer may revert, which would cause the entire `completeQueuedWithdrawal()` transaction to revert.

There are a couple reasons why `depositIntoStrategy()` may revert:

1. In `StrategyManager.depositIntoStrategy()`, the number of shares returned by the strategy is [verified](https://github.com/Layr-Labs/eigenlayer-contracts/blob/84ca899c715dbc577af1c8db5965188b061fe464/src/contracts/core/StrategyManager.sol#L297) to be `> 0`. If the strategy mints shares at less than a 1:1 ratio, this can cause the transaction to revert, as the amount being deposited back may be as small as 1 wei.
2. EigenLayer's stETH and wBETH [strategies](https://github.com/Layr-Labs/eigenlayer-contracts?tab=readme-ov-file#strategies) both implement per-transaction and total deposit limits ([stETH](https://github.com/Layr-Labs/eigenlayer-contracts/blob/0139d6213927c0a7812578899ddd3dda58051928/src/contracts/strategies/StrategyBaseTVLLimits.sol#L74-L75), [wBETH](https://github.com/Layr-Labs/eigenlayer-contracts/blob/mainnet/src/contracts/strategies/StrategyBaseTVLLimits.sol#L80-L81)):
    - If the deposit limit of a strategy has been reached, attempting to complete a queued withdrawal containing any amount over the `WithdrawQueue`'s buffer of the strategy's token will fail.
    - If the amount being redeposited is large enough, it may surpass the per-deposit limit.

This issue forces the `withdrawQueueAdmin` (which is a separate entity from the `nativeEthRestakeAdmin` affected) to set the buffer for the affected token high enough for the full amount being withdrawn to be transferred to the `WithdrawQueue`. This will require a third party to intervene and the protocol to handle in an unintended way by increasing the withdraw buffer for one or more tokens.

Furthermore, another entry point that calls `strategyManager.depositIntoStrategy()` and will revert under the same conditions is [`RestakeManager.deposit()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L491), the main deposit function for collateral tokens. Also here, the collateral token being deposited is first used to fill the `WithdrawQueue`'s buffer, so the transaction can revert for any of the reasons outlined above.

### Proof of Concept

**Scenario A:**

1. The `nativeEthRestakeAdmin` queues a withdrawal for 10 ETH, 10 stETH and 10 wBETH.
2. After the withdrawal delay passes, `completeQueuedWithdrawal()` is called to process the withdrawals.
3. The 10 ETH are forwarded to the deposit queue.
4. Next, 9 stETH are withdrawn and sent to `WithdrawQueue`, filling its stETH buffer.
5. 1 stETH remains and is attempted to be deposited back into the stETH strategy via `strategyManager.depositIntoStrategy()`.
6. However, the stETH strategy has already reached its total deposit limit.
7. The deposit reverts and causes the entire `completeQueuedWithdrawal()` transaction to revert.

**Scenario B:**

1. A user calls `RestakeManager.deposit()` to deposit 1 wBETH.
2. All wBETH but 1 wei is used to fill the wBETH buffer in the `WithdrawQueue`.
3. The remaining 1 wei is then attempted to be deposited into the wBETH strategy via `strategyManager.depositIntoStrategy()`.
4. However, it is converted into `0` shares by the strategy.
5. `StrategyManager` verifies that the number of shares minted by the strategy is greater than `0`.
6. Since `0` shares were minted, this check fails.
7. The `strategyManager.depositIntoStrategy()` call reverts.
8. This causes the entire `RestakeManager.deposit()` transaction to revert due to no fault of the user's.

### Recommended Mitigation Steps

Consider catching any reverts when depositing excess tokens into strategies. In order to ensure that the excess tokens remain in the system and are accounted for in the TVL, the best option may be to send them to the `WithdrawQueue` in the catch clause, regardless of whether the buffer for the given token is already full.

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/604#issuecomment-2137561894):**
 > There is no max deposit limit on any LSTs in the EigenLayer anymore. All the MaxCaps have been lifted.
 >
 > With 1 wei issue, yes the transaction will revert but  it doesn't affect the funds and will be retried later on. Acknowledging for 1 wei issue.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/604#issuecomment-2138724646):**
 > In general, accepting. Because in any case that EigenLayer puts conditions on deposits, it might make withdrawals fail as well.



***

## [[M-02] Withdrawals and Claims are meant to be pausable, but it is not possible in practice](https://github.com/code-423n4/2024-04-renzo-findings/issues/569)
*Submitted by [zigtur](https://github.com/code-423n4/2024-04-renzo-findings/issues/569), also found by [Sathish9098](https://github.com/code-423n4/2024-04-renzo-findings/issues/595), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/576), [tapir](https://github.com/code-423n4/2024-04-renzo-findings/issues/568), [xg](https://github.com/code-423n4/2024-04-renzo-findings/issues/567), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/565), rbserver ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/564), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/69)), [guhu95](https://github.com/code-423n4/2024-04-renzo-findings/issues/353), [eeshenggoh](https://github.com/code-423n4/2024-04-renzo-findings/issues/131), [TECHFUND](https://github.com/code-423n4/2024-04-renzo-findings/issues/130), [TheFabled](https://github.com/code-423n4/2024-04-renzo-findings/issues/129), [cu5t0mpeo](https://github.com/code-423n4/2024-04-renzo-findings/issues/128), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/127), [ladboy233](https://github.com/code-423n4/2024-04-renzo-findings/issues/126), [NentoR](https://github.com/code-423n4/2024-04-renzo-findings/issues/125), [0xBeastBoy](https://github.com/code-423n4/2024-04-renzo-findings/issues/124), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/123), [bigtone](https://github.com/code-423n4/2024-04-renzo-findings/issues/122), josephdara ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/121), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/120)), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/119), [mt030d](https://github.com/code-423n4/2024-04-renzo-findings/issues/115), [ak1](https://github.com/code-423n4/2024-04-renzo-findings/issues/114), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/112), [Aymen0909](https://github.com/code-423n4/2024-04-renzo-findings/issues/110), and [oakcobalt](https://github.com/code-423n4/2024-04-renzo-findings/issues/24)*

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L13>

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L206>

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L279>

### Impact

Administrator is not able to pause users' withdrawals and claims as expected.

### Proof of Concept

The `WithdrawQueue` contract inherits `PausableUpgradable` to provide pausing capabilities to the administrator on users' withdrawals and claims.
The contract correctly exposes the `_pause()` and `_unpause()` internal functions through access restricted external functions.

However, none of the functions implement the `whenNotPaused` modifier. This is especially problematic for user-accessible functions: `withdraw` and `claim`.

```solidity
// @POC: WithdrawQueue inherits PausableUpgradeable
contract WithdrawQueue is
    Initializable,
    PausableUpgradeable,
    ReentrancyGuardUpgradeable,
    WithdrawQueueStorageV1
{
    // ...

    function initialize(
        IRoleManager _roleManager,
        IRestakeManager _restakeManager,
        IEzEthToken _ezETH,
        IRenzoOracle _renzoOracle,
        uint256 _coolDownPeriod,
        TokenWithdrawBuffer[] calldata _withdrawalBufferTarget
    ) external initializer {

        // ...

        __Pausable_init();

        // ...
    }

    function pause() external onlyWithdrawQueueAdmin {// @POC: pause is accessible to admin
        _pause();
    }

    function unpause() external onlyWithdrawQueueAdmin {// @POC: unpause is accessible to admin
        _unpause();
    }

    function withdraw(uint256 _amount, address _assetOut) external nonReentrant {// @POC: pause has no impact
        // ...
    }

    function claim(uint256 withdrawRequestIndex) external nonReentrant {// @POC: pause has no impact
        // ...
    }
}
```

### Recommended Mitigation Steps

Consider implementing `whenNotPaused` modifier on `claim` and `withdraw` functions. The following patch implements such a fix.

```diff
diff --git a/contracts/Withdraw/WithdrawQueue.sol b/contracts/Withdraw/WithdrawQueue.sol
index 786238c..91ec77b 100644
--- a/contracts/Withdraw/WithdrawQueue.sol
+++ b/contracts/Withdraw/WithdrawQueue.sol
@@ -203,7 +203,7 @@ contract WithdrawQueue is
      * @param   _amount  amount of ezETH to withdraw
      * @param   _assetOut  output token to receive on claim
      */
-    function withdraw(uint256 _amount, address _assetOut) external nonReentrant {
+    function withdraw(uint256 _amount, address _assetOut) whenNotPaused external nonReentrant {
         // check for 0 values
         if (_amount == 0 || _assetOut == address(0)) revert InvalidZeroInput();
 
@@ -276,7 +276,7 @@ contract WithdrawQueue is
      * @dev     revert on claim before cooldown period
      * @param   withdrawRequestIndex  Index of the Withdraw Request user wants to claim
      */
-    function claim(uint256 withdrawRequestIndex) external nonReentrant {
+    function claim(uint256 withdrawRequestIndex) whenNotPaused external nonReentrant {
         // check if provided withdrawRequest Index is valid
         if (withdrawRequestIndex >= withdrawRequests[msg.sender].length)
             revert InvalidWithdrawIndex();
```

*Note: The patch can be applied with `git apply`.*

### Assessed type

Context

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/569#event-12915964089)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/13), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/52), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/45), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/30), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/25).

***

## [[M-03] Fixed hearbeat used for price validation is too stale for some tokens](https://github.com/code-423n4/2024-04-renzo-findings/issues/563)
*Submitted by [Maroutis](https://github.com/code-423n4/2024-04-renzo-findings/issues/563), also found by [ZanyBonzy](https://github.com/code-423n4/2024-04-renzo-findings/issues/600), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/562), and [NentoR](https://github.com/code-423n4/2024-04-renzo-findings/issues/472)*

<https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/Oracle/RenzoOracleL2.sol#L13>

<https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/Oracle/RenzoOracleL2.sol#L52>

### Impact

The stale period `86400 + 60 seconds` used for the oracle price validation is too short for some tokens like `ezETH` for example on Arbitrum. This could lead to the protocol consuming stale prices on Arbitrum.

### Proof of Concept

In both `RenzoOracle` and `RenzoOracleL2`, the hearbeat period `MAX_TIME_WINDOW` is set to `86400 + 60; // 24 hours + 60 seconds`. In the functions `RenzoOracleL2::getMintRate` and `RenzoOracle::lookupTokenValue`, a validation checks sees if the price data fed by Chainlink's price feed aggregators is stale depending if the period of `24 hours + 60 seconds` has passed. Example :

```js
    function getMintRate() public view returns (uint256, uint256) {
        (, int256 price, , uint256 timestamp, ) = oracle.latestRoundData();
        if (timestamp < block.timestamp - MAX_TIME_WINDOW) revert OraclePriceExpired();
```

The problem is that depending on the token and the chain, the same period can be considered too small or too stale.

Let's consider the ezETH/ETH oracles on different chains:

- On Ethereum, the oracle will update the price data every [`~24 hours`](https://data.chain.link/feeds/ethereum/mainnet/ezeth-eth).
- On Arbitrum, the oracle will update the price data every [`~6 hours`](https://data.chain.link/feeds/arbitrum/mainnet/ezeth-eth-exchange-rate).
- On Linea, the oracle will update the price data every [`24 hours`](https://data.chain.link/feeds/linea/mainnet/ezeth-eth).

This means that on Arbitrum, `24 hours` can be considered too large for the stale period which will cause the function `RenzoOracleL2::getMintRate` to return stale data.

### Recommended Mitigation Steps

It is recommended to store a mapping that would record the hearbeat parameter for the stale period of each token and for every different chain.

### Assessed type

Oracle

**[jatinj615 (Renzo) acknowledged](https://github.com/code-423n4/2024-04-renzo-findings/issues/563#event-13001051441)**

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/563).*

***

## [[M-04] Price updating mechanism can break](https://github.com/code-423n4/2024-04-renzo-findings/issues/519)
*Submitted by [Fassi\_Security](https://github.com/code-423n4/2024-04-renzo-findings/issues/519)*

Renzo uses `CCIP` to send price updates from `L1 -> L2` using:

```javascript
    function sendPrice(
        CCIPDestinationParam[] calldata _destinationParam,
        ConnextDestinationParam[] calldata _connextDestinationParam
    ) external payable onlyPriceFeedSender nonReentrant {
    // omitted code
        for (uint256 i = 0; i < _destinationParam.length; ) {
            Client.EVM2AnyMessage memory evm2AnyMessage = Client.EVM2AnyMessage({
                receiver: abi.encode(_destinationParam[i]._renzoReceiver), // ABI-encoded xRenzoDepsot contract address
                data: _callData, // ABI-encoded ezETH exchange rate with Timestamp
                tokenAmounts: new Client.EVMTokenAmount[](0), // Empty array indicating no tokens are being sent
                extraArgs: Client._argsToBytes(
                    // Additional arguments, setting gas limit
                    Client.EVMExtraArgsV1({ gasLimit: 200_000 })
                ),
                // Set the feeToken  address, indicating LINK will be used for fees
                feeToken: address(linkToken)
            });

            // Get the fee required to send the message
            uint256 fees = linkRouterClient.getFee(
                _destinationParam[i].destinationChainSelector,
                evm2AnyMessage
            );

            if (fees > linkToken.balanceOf(address(this)))
                revert NotEnoughBalance(linkToken.balanceOf(address(this)), fees);

            // approve the Router to transfer LINK tokens on contract's behalf. It will spend the fees in LINK
            linkToken.approve(address(linkRouterClient), fees);

            // Send the message through the router and store the returned message ID
->          bytes32 messageId = linkRouterClient.ccipSend(
                _destinationParam[i].destinationChainSelector,
                evm2AnyMessage
            );
    // omitted code
    }
```

The `CCIP` architecture allows for simultaneous `CCIP` calls to be made from one address.

However, there is a caveat. As per [Chainlink Docs](https://docs.chain.link/ccip/concepts/manual-execution#frequently-asked-questions), under the second header:

> If a user sends multiple messages and the first message isn't successfully delivered and goes into a manual execution mode, does that mean all subsequent messages from the user will also be stuck?
> 
> It depends. If a message goes into manual execution mode due to receiver errors (unhandled exceptions or gas limit issues), subsequent messages don't get automatically blocked, unless they would encounter the same error. 
> 
> However, suppose a message goes into manual execution mode after the Smart Execution time window expires (currently 8 hours). In that case, subsequent messages must wait for the first message to be processed to maintain the default sequence.

If a message fails, it can be manually executed, but after the `Smart Execution time window` expires, which is `8 hours` at the moment, all subsequent messages will fail until the `failing message` will succeed.

The problem is that on the `L2` side of things, in `CCIPReceiver.sol`, the reverts are not handled gracefully. This can easily lead to a `CCIP` call that can never be executed, thus resulting in a Denial of Service.

These are the failure points during the `_ccipReceive()` call, that can lead to a `CCIP` call not being able to be delivered, called by a **honest party**, marked by an arrow inside `_updatePrice`:

```javascript

    function _ccipReceive(
        Client.Any2EVMMessage memory any2EvmMessage
    ) internal override whenNotPaused {
        address _ccipSender = abi.decode(any2EvmMessage.sender, (address));
        uint64 _ccipSourceChainSelector = any2EvmMessage.sourceChainSelector;
        // Verify origin on the price feed
        if (_ccipSender != xRenzoBridgeL1) revert InvalidSender(xRenzoBridgeL1, _ccipSender);
        // Verify Source chain of the message
        if (_ccipSourceChainSelector != ccipEthChainSelector)
            revert InvalidSourceChain(ccipEthChainSelector, _ccipSourceChainSelector);
        (uint256 _price, uint256 _timestamp) = abi.decode(any2EvmMessage.data, (uint256, uint256));
        xRenzoDeposit.updatePrice(_price, _timestamp);
        emit MessageReceived(
            any2EvmMessage.messageId,
            _ccipSourceChainSelector,
            _ccipSender,
            _price,
            _timestamp
        );
    }

    function updatePrice(uint256 _price, uint256 _timestamp) external override {
        if (msg.sender != receiver) revert InvalidSender(receiver, msg.sender);
        _updatePrice(_price, _timestamp);
    }

    function _updatePrice(uint256 _price, uint256 _timestamp) internal {
        // Check for 0
        if (_price == 0) {
->            revert InvalidZeroInput();
        }

        // Check for price divergence - more than 10%
        if (
            (_price > lastPrice && (_price - lastPrice) > (lastPrice / 10)) ||
            (_price < lastPrice && (lastPrice - _price) > (lastPrice / 10))
        ) {
->            revert InvalidOraclePrice();
        }

        // Do not allow older price timestamps
        if (_timestamp <= lastPriceTimestamp) {
->            revert InvalidTimestamp(_timestamp);
        }

        // Do not allow future timestamps
        if (_timestamp > block.timestamp) {
->            revert InvalidTimestamp(_timestamp);
        }

        // Update values and emit event
        lastPrice = _price;
        lastPriceTimestamp = _timestamp;

        emit PriceUpdated(_price, _timestamp);
    }
```

For example, if the price deviates more than `10%,` the delivery will fail. If this delivery keeps failing, even after the 8 hours `Smart Execution window` has elapsed, the `CCIP` pathway will be DoS'ed until this `CCIP call` successfully delivers.

The impact is broad - price data will be corrupted, minting prices will not be calculated correctly and updates from `L1` will be DoS'ed.

### Recommended Mitigation Steps

As per the Chainlink docs linked in the report:

```md
Test thoroughly to ensure logical conditions for all paths are gracefully handled in your receiver contract. 
```

Handle the reverts gracefully.

### Assessed type

Timing

**[bronze_pickaxe (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/519#issuecomment-2132259050):**
> Our issue is not a duplicate of this [invalidated finding](https://github.com/code-423n4/2024-04-renzo-findings/issues/522). Our issue describes multiple ways in which the `CCIP path` can be DoS'ed, without the need of a malicious entity. Just regular usage can lead to DoS because failures are not handled gracefully.
> 
> The Sponsor has confirmed that one of the two path ways of updating a price will be used, either CCIP or Oracle [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/117#issuecomment-2122617996), which means that the CCIP pathway being DoS'ed would break the L2 side of things + new data will not be able to go through.
> 
> To reiterate, there is no malicious entity needed for this pathway to be DoS'ed, the reverts marked with an `->` in our issue's are all point of failures.

**[EV\_om (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/519#issuecomment-2133969489):**
 > I believe this finding is also invalid.
> 
> The interpretation of the Chainlink docs is incorrect. The quoted excerpt specifies that if a message goes into manual execution mode due to unhandled exceptions, subsequent messages _don't_ get automatically blocked. The only case in which a message blocks subsequent messages is if it "goes into manual execution mode after the Smart Execution time window expires", which can only happen:
> 
> > If the issue was due to extreme gas spikes or network conditions, and CCIP was not able to successfully transfer the message despite gas bumping for the entire duration of the Smart Execution time window
> 
> This is:
> - Extremely unlikely to happen.
> - Unrelated to the unhandled reverts.
> - An inherent risk of CCIP which will affect all protocols integrating it equally.
> - Avoidable by the admin bumping the gas fee during such period.

**[bronze_pickaxe (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/519#issuecomment-2134097626):**
 > You skipped the following bullet point when copying the Chainlink docs:
> [manual-execution](https://docs.chain.link/ccip/concepts/manual-execution#manual-execution)
> - Unhandled exception (logical error) in the receiver contract: If the receiver contract is [upgradeable](https://blog.chain.link/upgradable-smart-contracts/), developers must correct the logic, re-deploy the logic contract, and then manually execute the same transaction. If the receiver contract is not upgradeable, developers must deploy a new receiver contract, and then users can send a new CCIP message
> 
> If the CCIP path is stuck due to unhandled exceptions, the project would need to re-deploy said contracts.
> 
> For example, if the price would currently deviate more than 10%, every CCIP update would fail for `length = Smart Execution Window` due to this check:
> ```javascript
>         // Check for price divergence - more than 10%
>         if (
>             (_price > lastPrice && (_price - lastPrice) > (lastPrice / 10)) ||
>             (_price < lastPrice && (lastPrice - _price) > (lastPrice / 10))
>         ) {
> ->            revert InvalidOraclePrice();
>         }
> ```
> Bumping the gas here makes no sense.
>
> In [Chainlink docs](https://docs.chain.link/ccip/concepts/manual-execution#ccip-execution), under `CCIP-Execution #6.2`:
> - If the message does not involve token transfers, only arbitrary messaging, and the receiver execution fails due to gas limits or unhandled exceptions, the transaction becomes eligible for manual execution.
> 
> This means that a CCIP call can become eligible for the manual execution `->` smart contract window expiry flow by either having a too low gas limit, which can be fixed by upping the gas, or by unhandled exceptions. 
> 
> Lastly, what you are quoting is when a call becomes eligible for `manual execution`. In manual execution mode, you are allowed to bump the gas. Bumping the gas here will not make the transaction succeed, which will result in a `DoS` and to re-iterate, if it's the case of an unhandled exception.
> 
> New deployment, not bumping the gas fees.
> 
> To summarize:
> - A CCIP call is made at timestamp `k`.
> - This CCIP call will fail due to one of the many unhandled exceptions, lets go with price deviation.
> - Subsequent calls will still fail due to the price deviation.
> - Timestamp is now `k + eligble_for_manual_execution`.
> - Bumping the gas price would not make it succeed.
> - Timestamp is now `k + smart_execution_window_expired`.
> - DoS.

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/519#issuecomment-2137545732):**
 > From the above argument, if there is any issue with the checks, for example, highlighted 10% deviation. As, protocol updates the price feeds on L2 every `6 hours` if the price deviation recorded on L2 is more than that, which means the feed is corrupted. Then, protocol would want to halt the deposit services on L2 until the new receiver is deployed or manually handled by owner through `updatePriceByOwner`.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/519#issuecomment-2138748018):**
 > I'm going to accept this as Medium, quite borderline. Burden of proof falls on the reporting warden, which has done a considerable effort taking into account the lack of facilities provided with the code. While not conclusively proven, the risk of malfunctioning is high enough with the evidence presented. The sponsor is recommended to apply a fix.

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/519).*



***

## [[M-05] `calculateTVL` may run out of gas for modest number of operators and tokens breaking deposits, withdrawals, and trades](https://github.com/code-423n4/2024-04-renzo-findings/issues/514)
*Submitted by [guhu95](https://github.com/code-423n4/2024-04-renzo-findings/issues/514), also found by [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/591), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/577), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/560), and [Bauchibred](https://github.com/code-423n4/2024-04-renzo-findings/issues/2)*

The `calculateTVLs` function in the `RestakeManager` contains [two nested loops](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L289-L310): one loop for each operator delegator (OD), and an internal loop for each token. In each internal loop:

- The [OD's `getTokenBalanceFromStrategy`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L302) function is called for the token, which in turn calls the [Eigenlayer strategy](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Delegation/OperatorDelegator.sol#L332) for the shares balance.
- The [`renzoOracle`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L307) is called for the token value, which in turns [calls the respective oracle](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Oracle/RenzoOracle.sol#L75).
- Additionally, memory is allocated for all the results and intermediate call outputs, incurring high quadratic memory expansion costs.

Due to the the nested loop structure, the gas consumption in the case of several operator delegators, and several tokens used is quadratic: `n-OD x n-Tokens`. Crucially, this method is called in most user flows: [deposits](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L500-L504), [withdrawals](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L217), and [Balancer trades](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RateProvider/BalancerRateProvider.sol#L31).

### Impact

An even small number of operators and supported tokens will render the protocol unusable, up to running out of block gas limit.

Currently, with 1 OD and 2 tokens, `calculateTVLs` consumes approximately 450K gas (see the [example transaction](https://app.blocksec.com/explorer/tx/eth/0x5366d8b097cc2d2c27c45d97266b1fa6d76606e735c4a261efa7b43aff87de42) gas profiling section).

For reasonable values, such as 12 ODs and 12 tokens ([Eigenlayer supports 12 tokens](https://app.eigenlayer.xyz/restake)), there would be **144** nested loop iterations instead of just 2 iterations in the current version and configuration. A simple extrapolation, without adding the cost of operations added in the new version, and without estimating the additional quadratic memory expansion costs, would suggest that 144 iterations, instead of the current 2, would cost 32M gas (`450K * 144 / 2`), exceeding the block gas limit.

However, an earlier limiting factor will be encountered because `calculateTVL` is called in most user interactions with Renzo:  [deposit](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L500-L504), [withdrawal](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L217), and [Balancer trade](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RateProvider/BalancerRateProvider.sol#L31). Thus, exceeding even 1M-2M gas on L1 will render most protocol methods practically unusable for users.

### Proof of Concept

1. With 1 OD and 2 tokens, `calculateTVLs` consumes approximately 450K gas (see the [example transaction](https://app.blocksec.com/explorer/tx/eth/0x5366d8b097cc2d2c27c45d97266b1fa6d76606e735c4a261efa7b43aff87de42) gas profiling section)
2. For reasonable values, such as 12 ODs and 12 tokens currently supported by EigenLayer, there would be **144** nested loop iterations instead of the current 2 .
3. A simple extrapolation, would suggest that 144 iterations, instead of the current 2, would cost 32M gas (`450K * 144 / 2`), exceeding the block gas limit. Moreover, this is an underestimate, due to not adding the cost of operations added in the new version (relative to the deployed one), and without estimating the additional quadratic memory expansion costs.

### Recommended Mitigation Steps

Instead of "pulling" operator delegator token balances, a "pushing" pattern can be used:

- Instead of "pulling" token TVLs from each component, the aggregated TVL sums should be maintained and "pushed" by each OD when its TVL changes (on OD deposits and withdrawals). This way, during admin's OD operations, the RM's TVL cache and each token's total protocol balance is updated.
- Then, total token balances can be used to calculate TVL from `RenzoOracle.lookupTokenValues` once, which will result in a single loop over the tokens only.
- For enabling `chooseOperatorDelegatorForDeposit` a Set of ODs that can accept a deposit (are below allocation) can be maintained via "push" updates.

This will remove all loops during the calculation, except for the loop needed to iterate over the token oracles (once).

Alternatively, an off-chain custom TVL oracle can be used, for example, via a custom Chainlink oracle.

### Assessed type

DoS

**[jatinj615 (Renzo) acknowledged](https://github.com/code-423n4/2024-04-renzo-findings/issues/514#event-12915967118)**



***

## [[M-06] `L1::xRenzoBridge` and `L2::xRenzoBridge` uses the `block.timestamp` as dependency, which can cause issues](https://github.com/code-423n4/2024-04-renzo-findings/issues/502)
*Submitted by [ladboy233](https://github.com/code-423n4/2024-04-renzo-findings/issues/502), also found by [oakcobalt](https://github.com/code-423n4/2024-04-renzo-findings/issues/21)*

In `L1::xRenzoBridge` the `block.timestamp` from L1 is encoded and sent to L2. When the message is delivered from L1 to L2  with `xRenzoBridge::_updatePrice()`, the function checks the `block.timestamp` like this:

```solidity
    if (_timestamp > block.timestamp) {
            revert InvalidTimestamp(_timestamp);
        }
```

This check is done to not allow future timestamps for updating the price But the timestamps between two chains L1 and L2 are different for chain like Arbitrum as there's a possibility that the sequencer fails to post batches on the parent chain (for example, Ethereum) for a period of time.

According to the [Arbitrum docs](<https://docs.arbitrum.io/build-decentralized-apps/arbitrum-vs-ethereum/block-numbers-and-time#block-timestamps-arbitrum-vs-ethereum>):

> **Timestamp boundaries of the sequencer**
>
> As mentioned, block timestamps are usually set based on the sequencer's clock. Because there's a possibility that the sequencer fails to post batches on the parent chain (for example, Ethereum) for a period of time, it should have the ability to slightly adjust the timestamp of the block to account for those delays and prevent any potential reorganisations of the chain. To limit the degree to which the sequencer can adjust timestamps, some boundaries are set, currently to 24 hours earlier than the current time, and 1 hour in the future.

So the issue is that timestamp validation for `_updatePrice()` won't be effective and can reject validation both l2 tiimestamp is not related to l1 timestamp

> Block timestamps on Arbitrum are not linked to the timestamp of the L1 block. They are updated every L2 block based on the sequencer's clock. These timestamps must follow these two rules:
>
> 1. Must be always equal or greater than the previous L2 block timestamp.
> 2. Must fall within the established boundaries (24 hours earlier than the current time or 1 hour in the future). More on this below.
>
> Furthermore, for transactions that are force-included from L1 (bypassing the sequencer), the block timestamp will be equal to either the L1 timestamp when the transaction was put in the delayed inbox on L1 (not when it was force-included), or the L2 timestamp of the previous L2 block, whichever of the two timestamps is greater.

### Proof of Concept

[`xRenzoBridge::sendPrice`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol#L216) is used to send the price feed from L1 to L2. The
`bytes memory _callData = abi.encode(exchangeRate, block.timestamp);` encodes the block.timestamp of L1.

```solidity
    function sendPrice(
        CCIPDestinationParam[] calldata _destinationParam,
        ConnextDestinationParam[] calldata _connextDestinationParam
    ) external payable onlyPriceFeedSender nonReentrant {
        // call getRate() to get the current price of ezETH
        uint256 exchangeRate = rateProvider.getRate();

@>      bytes memory _callData = abi.encode(exchangeRate, block.timestamp);

        ...
        ...
    }
```

Now if we see this function [`xRenzoBridge::_updatePrice()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L345C7-L352C10), the timestamp here is compared to the timestamp of L2 is not effective to check the older price timestamps is greater than `block.timestamp` as both of these timestamps of L1 and L2 are different.

```solidity

    function _updatePrice(uint256 _price, uint256 _timestamp) internal {
        // Check for 0
        if (_price == 0) {
            revert InvalidZeroInput();
        }

        // Check for price divergence - more than 10%
        if (
            (_price > lastPrice && (_price - lastPrice) > (lastPrice / 10)) ||
            (_price < lastPrice && (lastPrice - _price) > (lastPrice / 10))
        ) {
            revert InvalidOraclePrice();
        }

        // Do not allow older price timestamps
        if (_timestamp <= lastPriceTimestamp) {
            revert InvalidTimestamp(_timestamp);
        }

        // Do not allow future timestamps
@>      if (_timestamp > block.timestamp) {
            revert InvalidTimestamp(_timestamp);
        }

        // Update values and emit event
        lastPrice = _price;
        lastPriceTimestamp = _timestamp;

        emit PriceUpdated(_price, _timestamp);
    }
```

### Recommended Mitigation Steps

Remove the timestamp check in in L2 update rate.

### Assessed type

Timing

**[jatinj615 (Renzo) acknowledged](https://github.com/code-423n4/2024-04-renzo-findings/issues/502#event-12915979432)**

**[EV\_om (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/502#issuecomment-2132391915):**
 > @alcueca - I believe this finding must be invalid.
> 
> While it is true that the sequencer can adjust the timestamp of a delayed block to up to 24 hours in the past, I believe this block will only ever include transactions that were received by the sequencer _prior_ to that timestamp.
> 
> I have not been able to find a source to back up this claim, but this seems evident as the opposite would allow exploiting a sequencer downtime to include transactions in blocks with a timestamp in the past, which would have grave consequences for any protocol relying on block timestamps for their operations and allow manipulation of liquidations, governance votes, orders with expiration timestamps, and so on.
> 
> If this was indeed the case, the warden would have found a much more severe vulnerability than the trivial revert here.
> 
> On Optimism, for instance, this check is implemented [here](https://github.com/ethereum-optimism/optimism/blob/7cbda018196b58a71e2c0b4bc9e31a289235074e/packages/contracts-bedrock/src/L2/CrossL2Inbox.sol#L116).

**[ladboy233 (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/502#issuecomment-2132397867):**
 > > On Optimism, for instance, this check is implemented [here](https://github.com/ethereum-optimism/optimism/blob/7cbda018196b58a71e2c0b4bc9e31a289235074e/packages/contracts-bedrock/src/L2/CrossL2Inbox.sol#L116).
> 
> The original report does not really mention optimism. The original report's concern is that the L1 / L2 timestamp is not related and use L1 timestamp to validate against L2 timestamp can revert valid price update.
> 
> ```solidity
> if (_timestamp > block.timestamp) {
>           revert InvalidTimestamp(_timestamp);
>       }
> ```
> 
> The L2 timestamp does not always bigger than L1 timestamp. For example, please free feel to run this POC:
> 
> ```solidity
> from web3 import Web3
> import time
> 
> # Dictionary mapping blockchain names to RPC URLs
> rpc_urls = {
>     'Ethereum Mainnet': 'https://eth.llamarpc.com',
>     "blast": "https://rpc.blastblockchain.com",
> }
> 
> def get_block_timestamp(name, url):
>     try:
>         web3 = Web3(Web3.HTTPProvider(url))
>         latest_block = web3.eth.get_block('latest')
>         return f"{name} block timestamp: {latest_block.timestamp}, block number {latest_block.number}"
>     except Exception as e:
>         return f"{name} Error: {e}"
> 
> # Query each blockchain and print the latest block's timestamp
> for name, url in rpc_urls.items():
>     print(get_block_timestamp(name, url))
> ```
> 
> The L1 `block.timestamp` is greater than blast (optimism fork) `block.timestamp` at the same time.
> 
> Example output:
> 
> ```solidity
> Ethereum Mainnet block timestamp: 1716757859, block number 19956651
> blast block timestamp:            1707500043, block number 2699354
> ```
>
 > From [Arbitrum docs](https://docs.arbitrum.io/build-decentralized-apps/arbitrum-vs-ethereum/block-numbers-and-time#block-timestamps-arbitrum-vs-ethereum):
> 
> > Block timestamps on Arbitrum are not linked to the timestamp of the L1 block. 

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/502#issuecomment-2132708720):**
 > Timestamps in L1 and L2 are not related and it can't be demanded that one or the other is always greater.



***

## [[M-07] Lack of slippage and deadline during withdraw and deposit](https://github.com/code-423n4/2024-04-renzo-findings/issues/484)
*Submitted by [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/484), also found by [ZanyBonzy](https://github.com/code-423n4/2024-04-renzo-findings/issues/598), [hunter\_w3b](https://github.com/code-423n4/2024-04-renzo-findings/issues/592), carlitox477 ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/581), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/348)), umarkhatab\_465 ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/485), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/328)), [btk](https://github.com/code-423n4/2024-04-renzo-findings/issues/483), [ladboy233](https://github.com/code-423n4/2024-04-renzo-findings/issues/482), [ilchovski](https://github.com/code-423n4/2024-04-renzo-findings/issues/481), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/349), [Shaheen](https://github.com/code-423n4/2024-04-renzo-findings/issues/347), [PNS](https://github.com/code-423n4/2024-04-renzo-findings/issues/346), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/345), [MSaptarshi](https://github.com/code-423n4/2024-04-renzo-findings/issues/344), [atoko](https://github.com/code-423n4/2024-04-renzo-findings/issues/343), [Tigerfrake](https://github.com/code-423n4/2024-04-renzo-findings/issues/342), [Maroutis](https://github.com/code-423n4/2024-04-renzo-findings/issues/341), [honey-k12](https://github.com/code-423n4/2024-04-renzo-findings/issues/340), [0xDemon](https://github.com/code-423n4/2024-04-renzo-findings/issues/339), [DanielArmstrong](https://github.com/code-423n4/2024-04-renzo-findings/issues/338), [rbserver](https://github.com/code-423n4/2024-04-renzo-findings/issues/337), [NentoR](https://github.com/code-423n4/2024-04-renzo-findings/issues/335), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/334), [crypticdefense](https://github.com/code-423n4/2024-04-renzo-findings/issues/333), [twcctop](https://github.com/code-423n4/2024-04-renzo-findings/issues/332), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/331), [Ocean\_Sky](https://github.com/code-423n4/2024-04-renzo-findings/issues/330), [Rhaydden](https://github.com/code-423n4/2024-04-renzo-findings/issues/329), and [Bauchibred](https://github.com/code-423n4/2024-04-renzo-findings/issues/7)*

When users call `withdraw()` to burn their `ezETH` and receive redemption amount in return, there is no provision to provide any slippage & deadline params. This is necessary because the `withdraw()` function [uses values from the oracle](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L229) and the users may get a worse rate than they planned for.

Additionally, the `withdraw()` function also makes use of calls to `calculateTVLs()` to fetch the current `totalTVL`. The `calculateTVLs()` function [makes use of oracle prices too](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L317). Note that though there is a `MAX_TIME_WINDOW` inside these oracle lookup functions, the users are forced to rely on this hardcoded value & can't provide a deadline from their side.
These facts are apart from the consideration that users' call to `withdraw()` could very well be unintentionally/intentionally front-run which causes a drop in `totalTVL`. <br>

In all of these situations, users receive less than they bargained for and, hence, a slippage and deadline parameter is necessary.

Similar issue can be seen inside [`deposit()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L565) and [`depositETH()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L605).

### Recommended Mitigation Steps

Allow users to pass a slippage tolerance value and a deadline parameter while calling these functions.

**[jatinj615 (Renzo) disputed and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/484#issuecomment-2110339545):**
 > Oracle updates the value every 24 hours and technically, it creates an arbitrage opportunity which will not be beneficial to users as they will arbitraging 1 days reward share and losing on 7 days rewards due to `coolDownPeriod`. 
>
> We need the warden to provide a POC of delta around `deposit` and `withdraw` considering we will be implementing slashing pricing mechanism at the time of claim specified in [#326](https://github.com/code-423n4/2024-04-renzo-findings/issues/326).  

**[sin1st3r\_\_ (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/484#issuecomment-2132184938):**
 > @alcueca - I believe this should be a QA rather than a Med. You need slippage and deadline when the price can be manipulated like in an AMM. Here, since the price of the exchange is always fair because it can’t be moved by however large user operation, but only by changes in oracle price (that is fair by definition), there is no strong case for the same of level of protection as in AMMs.
 >
> Staking on Lido for example doesn't have slippage or deadline either. See [here](https://etherscan.io/address/0x17144556fd3424edc8fc8a4c940b2d04936d17eb#code).

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/484#issuecomment-2133087448):**
 > The thing is that Renzo is using market oracles, as stated in [#13](https://github.com/code-423n4/2024-04-renzo-findings/issues/13). These oracles can fluctuate more than the actual exchange rate, due to market forces. In some situations the users might be displeased that their withdrawals rended less value because of a temporary spike in the oracle.
> 
> It is quite borderline, because it needs the oracles to have jumps large enough to bother users. However, I do see value to add slippage controls, and let users disable them in volatile conditions when they just want to dump.



***

## [[M-08] Not handling the failure of cross chain messaging](https://github.com/code-423n4/2024-04-renzo-findings/issues/373)
*Submitted by [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/373), also found by [tapir](https://github.com/code-423n4/2024-04-renzo-findings/issues/393), 0xCiphky ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/392), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/287)), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/375), [ladboy233](https://github.com/code-423n4/2024-04-renzo-findings/issues/374), [guhu95](https://github.com/code-423n4/2024-04-renzo-findings/issues/372), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/371), and [grearlake](https://github.com/code-423n4/2024-04-renzo-findings/issues/32)*

If the `xReceive` function fails to handle reverts properly, it could result in funds getting stuck. This can happen for example when:

- Depositing into L2 when protocol on L1 is paused: because pausing is not defined on L2.
- Depositing large amount on L2: because it is not enforced to deposit less than a limit on L2
- Depositing too small amount on L2: because the `ezETH` rate on L1 and L2 could be different.

### Proof of Concept

Failure to handle errors in the `xReceive` function as outlined by Connext can lead to funds becoming inaccessible. See [here](<https://docs.connext.network/developers/guides/handling-failures#reverts-on-receiver-contract>).

This can happen in several scenarios within the `xRenzoBridge` contract:

1. If the deposited amount on L2 exceeds the `maxDepositTVL` limit set on L1, the deposit will fail when bridged to L1. This could occur if an attacker uses a large flash loan of `WETH` to deposit on L2 and then swaps the minted `xezETH` to repay the flash loan.

```solidity
    function xReceive(
        bytes32 _transferId,
        uint256 _amount,
        address _asset,
        address _originSender,
        uint32 _origin,
        bytes memory
    ) external nonReentrant returns (bytes memory) {
        // ...
        restakeManager.depositETH{ value: ethAmount }();
        //....
    }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol#L175>

```solidity
   function deposit(
       IERC20 _collateralToken,
       uint256 _amount,
       uint256 _referralId
   ) public nonReentrant notPaused {
       //....
       if (maxDepositTVL != 0 && totalTVL + collateralTokenValue > maxDepositTVL) {
           revert MaxTVLReached();
       }
       //....
   }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L510>

2. If the protocol on L1 is paused, the deposit made on L2 will be successful and equivalent `xezETH` will be minted, but when it is bridged to L1, it will fail. This is because no pausing mechanism is defined on L2 to be aligned with L1.

```solidity
   function depositETH(
       uint256 _minOut,
       uint256 _deadline
   ) external payable nonReentrant returns (uint256) {
       //....
   }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L168>

```solidity
   function deposit(
       uint256 _amountIn,
       uint256 _minOut,
       uint256 _deadline
   ) external nonReentrant returns (uint256) {
       //....
   }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L204>

3. If the deposited amount on L2 is too low so that when it is bridged to L1, minted amount of `ezETH` becomes zero, it will fail. This can happen if between the deposit on L2 and bridging to L1, the TVL increases while total supply of `ezETH` does not change. By doing so, each `ezETH` is worth more than before. So, when that small amount of `WETH` is going to be deposited into the protocol on L1, it mints less `ezETH` than the amount of `xezETH` minted on L2. If it is zero, it will revert.

```solidity
  function xReceive(
      bytes32 _transferId,
      uint256 _amount,
      address _asset,
      address _originSender,
      uint32 _origin,
      bytes memory
  ) external nonReentrant returns (bytes memory) {
      // ...
      restakeManager.depositETH{ value: ethAmount }();
      //....
  }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L1/xRenzoBridge.sol#L175>

```solidity
  function deposit(
      IERC20 _collateralToken,
      uint256 _amount,
      uint256 _referralId
  ) public nonReentrant notPaused {
      //....
      uint256 ezETHToMint = renzoOracle.calculateMintAmount(
          totalTVL,
          collateralTokenValue,
          ezETH.totalSupply()
      );
      //....
  }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L565>

```solidity
function calculateMintAmount(
        uint256 _currentValueInProtocol,
        uint256 _newValueAdded,
        uint256 _existingEzETHSupply
    ) external pure returns (uint256) {
        //....
        if (mintAmount == 0) revert InvalidTokenAmount();
        //....
    }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Oracle/RenzoOracle.sol#L146>

### Recommended Mitigation Steps

To address these potential failures, it is suggested to:

1. Implement error handling in the `xReceive` function. Specifically, placing the `depositETH` function call within a try/catch block could help manage these failures. Additionally, only authenticated addresses should be allowed to handle these errors.
2. Enforce the deposited amount on L2 to be less than `maxDepositTVL`.
3. Define the pausing mechanism on L2.
4. Allow the `BrdigeSweepr` to define the amount of token to be bridged to L1. By doing so, it can handle the situations where a large amount is deposited on L2.

```solidity
function sweep(uint256 _amount) public payable nonReentrant {
  //...
}
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L414>

### Assessed type

Context

**[jatinj615 (Renzo) acknowledged](https://github.com/code-423n4/2024-04-renzo-findings/issues/373#event-12916082088)**

**[Blckhv (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/373#issuecomment-2131196073):**
 > @alcueca - I think this issue should be of low severity because we can see that `xRenzoBridge` has functions to retrieve the funds that are "stuck", which is exactly what the first paragraph of the provided Connext documentation advises [here](https://docs.connext.network/developers/guides/handling-failures#reverts-on-receiver-contract).
> In all matters, manually distributing failed transactions funds is not an optimal solution, but in the end, funds are not really stuck, since the admin can still process them from the Connext directly.

**[sin1st3r\_\_ (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/373#issuecomment-2131382214):**
> @Blckhv - I'm afraid this is factually incorrect. Connext allows you to re-submit/retry a failed TX only if it failed due to insufficient relayer fee.
> 
> In the case it failed due to the `xReceive()` on the destination chain reverting, then the funds will be stuck. Not to mention that this failure is silent. Meaning that admins may be notified that this call failed on the destination chain very late. 
> 
> That's why the Connext [docs](https://docs.connext.network/developers/guides/handling-failures#reverts-on-receiver-contract) says that the `IXReceiver` contract should be implemented defensively.
> 
> > If the call on the receiver contract (also referred to as "target" contract) reverts, funds sent in with the call will end up on the receiver contract. To avoid situations where user funds get stuck on the receivers, developers should build any contract implementing `IXReceive` defensively.
> >
> > Ultimately, the goal should be to handle any revert-susceptible code and ensure that the logical owner of funds always maintains agency over them.
> 
> Bridging silently failing and admins having to manually recover funds and manually redistribute to other parts of the system is surely Medium severity worthy.

*Note: for full discussion, see [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/373).*



***

## [[M-09] Deposits will always revert if the amount being deposited is less than the `bufferToFill` value](https://github.com/code-423n4/2024-04-renzo-findings/issues/198)
*Submitted by [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/198), also found by [kinda\_very\_good](https://github.com/code-423n4/2024-04-renzo-findings/issues/578), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/238), [adam-idarrha](https://github.com/code-423n4/2024-04-renzo-findings/issues/237), [0x007](https://github.com/code-423n4/2024-04-renzo-findings/issues/236), [bill](https://github.com/code-423n4/2024-04-renzo-findings/issues/235), [inzinko](https://github.com/code-423n4/2024-04-renzo-findings/issues/234), [underdog](https://github.com/code-423n4/2024-04-renzo-findings/issues/233), [baz1ka](https://github.com/code-423n4/2024-04-renzo-findings/issues/232), [bigtone](https://github.com/code-423n4/2024-04-renzo-findings/issues/231), [MaslarovK](https://github.com/code-423n4/2024-04-renzo-findings/issues/230), [0xAadi](https://github.com/code-423n4/2024-04-renzo-findings/issues/229), [RamenPeople](https://github.com/code-423n4/2024-04-renzo-findings/issues/228), [Neon2835](https://github.com/code-423n4/2024-04-renzo-findings/issues/227), [hunter\_w3b](https://github.com/code-423n4/2024-04-renzo-findings/issues/224), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/221), [Shaheen](https://github.com/code-423n4/2024-04-renzo-findings/issues/220), [gesha17](https://github.com/code-423n4/2024-04-renzo-findings/issues/219), [Aymen0909](https://github.com/code-423n4/2024-04-renzo-findings/issues/218), [m\_Rassska](https://github.com/code-423n4/2024-04-renzo-findings/issues/217), [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/216), [mussucal](https://github.com/code-423n4/2024-04-renzo-findings/issues/215), [josephdara](https://github.com/code-423n4/2024-04-renzo-findings/issues/214), [kennedy1030](https://github.com/code-423n4/2024-04-renzo-findings/issues/213), [Fassi\_Security](https://github.com/code-423n4/2024-04-renzo-findings/issues/211), [DanielArmstrong](https://github.com/code-423n4/2024-04-renzo-findings/issues/210), [14si2o\_Flint](https://github.com/code-423n4/2024-04-renzo-findings/issues/209), [0rpse](https://github.com/code-423n4/2024-04-renzo-findings/issues/207), [mt030d](https://github.com/code-423n4/2024-04-renzo-findings/issues/206), [ADM](https://github.com/code-423n4/2024-04-renzo-findings/issues/202), [cu5t0mpeo](https://github.com/code-423n4/2024-04-renzo-findings/issues/201), [Tendency](https://github.com/code-423n4/2024-04-renzo-findings/issues/200), [araj](https://github.com/code-423n4/2024-04-renzo-findings/issues/192), [BiasedMerc](https://github.com/code-423n4/2024-04-renzo-findings/issues/191), [tapir](https://github.com/code-423n4/2024-04-renzo-findings/issues/190), [Aamir](https://github.com/code-423n4/2024-04-renzo-findings/issues/189), [blutorque](https://github.com/code-423n4/2024-04-renzo-findings/issues/188), [ZanyBonzy](https://github.com/code-423n4/2024-04-renzo-findings/issues/187), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/186), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/185), [xg](https://github.com/code-423n4/2024-04-renzo-findings/issues/184), [lanrebayode77](https://github.com/code-423n4/2024-04-renzo-findings/issues/183), [b0g0](https://github.com/code-423n4/2024-04-renzo-findings/issues/182), [gumgumzum](https://github.com/code-423n4/2024-04-renzo-findings/issues/181), [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/180), [carrotsmuggler](https://github.com/code-423n4/2024-04-renzo-findings/issues/56), and [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/44)*

The [`deposit`](https://github.com/code-423n4/2024-04-renzo/blob/1c7cc4e632564349b204b4b5e5f494c9b0bc631d/contracts/RestakeManager.sol#L491) function in the `RestakeManager` contract enables users to deposit ERC20 whitelisted collateral tokens into the protocol. It first checks the withdrawal buffer and fills it up using some or all of the deposited amount if it is below the buffer target. The remaining amount is then transferred to the operator delegator and deposited into EigenLayer.

The current issue with this implementation is that if the amount deposited is less than `bufferToFill`, the full amount will be used to fill the withdrawal buffer, leaving the amount value as zero.

```solidity
    function deposit(IERC20 _collateralToken, uint256 _amount, uint256 _referralId) public nonReentrant notPaused {
        // Verify collateral token is in the list - call will revert if not found
        uint256 tokenIndex = getCollateralTokenIndex(_collateralToken);
	...

        // Check the withdraw buffer and fill if below buffer target
        uint256 bufferToFill = depositQueue.withdrawQueue().getBufferDeficit(address(_collateralToken));
        if (bufferToFill > 0) {
            bufferToFill = (_amount <= bufferToFill) ? _amount : bufferToFill;
            // update amount to send to the operator Delegator
            _amount -= bufferToFill;

            // safe Approve for depositQueue
            _collateralToken.safeApprove(address(depositQueue), bufferToFill);

            // fill Withdraw Buffer via depositQueue
            depositQueue.fillERC20withdrawBuffer(address(_collateralToken), bufferToFill);
        }

        // Approve the tokens to the operator delegator
        _collateralToken.safeApprove(address(operatorDelegator), _amount);

        // Call deposit on the operator delegator
        operatorDelegator.deposit(_collateralToken, _amount);
        ...
    }
```

Subsequently, the function will approve the zero amount to the operator delegator and call `deposit` on the operator delegator. However, as seen in the `OperatorDelegator` contract's [`deposit`](https://github.com/code-423n4/2024-04-renzo/blob/1c7cc4e632564349b204b4b5e5f494c9b0bc631d/contracts/Delegation/OperatorDelegator.sol#L143) function below, a zero deposit will be reverted.

```solidity
    function deposit(IERC20 token, uint256 tokenAmount)
        external
        nonReentrant
        onlyRestakeManager
        returns (uint256 shares)
    {
        if (address(tokenStrategyMapping[token]) == address(0x0) || tokenAmount == 0) {
            revert InvalidZeroInput();
        }

        // Move the tokens into this contract
        token.safeTransferFrom(msg.sender, address(this), tokenAmount);

        return _deposit(token, tokenAmount);
    }
```

### Impact

Severity: Medium. User deposits will always revert if the amount being deposited is less than the `bufferToFill` value.

Likelihood: High. Depending on the set amount for the withdrawal buffer, this could be a common occurrence.

### Recommendation

To address this issue, the `deposit` function can be modified to only approve the amount to the operator delegator and call `deposit` on the operator delegator if the amount is greater than zero.

```solidity
    function deposit(IERC20 _collateralToken, uint256 _amount, uint256 _referralId) public nonReentrant notPaused {
        // Verify collateral token is in the list - call will revert if not found
        uint256 tokenIndex = getCollateralTokenIndex(_collateralToken);
	...
        // Check the withdraw buffer and fill if below buffer target
        uint256 bufferToFill = depositQueue.withdrawQueue().getBufferDeficit(address(_collateralToken));
        if (bufferToFill > 0) {
            bufferToFill = (_amount <= bufferToFill) ? _amount : bufferToFill;
            // update amount to send to the operator Delegator
            _amount -= bufferToFill;

            // safe Approve for depositQueue
            _collateralToken.safeApprove(address(depositQueue), bufferToFill);

            // fill Withdraw Buffer via depositQueue
            depositQueue.fillERC20withdrawBuffer(address(_collateralToken), bufferToFill);
        }
	if (_amount > 0) { // ADD HERE
            // Transfer the tokens to the operator delegator
            _collateralToken.safeApprove(address(operatorDelegator), _amount);

            // Call deposit on the operator delegator
            operatorDelegator.deposit(_collateralToken, _amount);
        }
        ...
    }
```

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/198#event-12916118847)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope)**

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/14), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/53), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/46), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/31), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/26).



***

## [[M-10] Potential arbitrage opportunity in the `xRenzoDeposit` L2 contract](https://github.com/code-423n4/2024-04-renzo-findings/issues/135)
*Submitted by [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/135), also found by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/134)*

The [`sendPrice`](https://github.com/code-423n4/2024-04-renzo/blob/1c7cc4e632564349b204b4b5e5f494c9b0bc631d/contracts/Bridge/L1/xRenzoBridge.sol#L210) function in the `xRenzoBridge` contract calls the [`getRate`](https://github.com/code-423n4/2024-04-renzo/blob/1c7cc4e632564349b204b4b5e5f494c9b0bc631d/contracts/RateProvider/BalancerRateProvider.sol#L29) function to retrieve the current price of ezETH to ETH and broadcasts it to Layer 2 networks. Subsequently, the price is received by either the `ConnextReceiver` or `CCIPReceiver` and invokes the [`updatePrice`](https://github.com/code-423n4/2024-04-renzo/blob/1c7cc4e632564349b204b4b5e5f494c9b0bc631d/contracts/Bridge/L2/xRenzoDeposit.sol#L310) function in the `xRenzoDeposit` contract on L2. However, a potential opportunity exists where a user can monitor the L1 mempool for the `sendPrice` function call, observe the new price, and sandwich it if profitable.

```solidity
    /**
     * @notice  Exposes the price via getRate()
     * @dev     This is required for a balancer pool to get the price of ezETH
     * @return  uint256  .
     */
    function getRate() external view override returns (uint256) {
        return lastPrice;
    }
```

Upon detecting a favourable price change, the user could mint xezETH on L2 before the price adjustment takes effect. Subsequently, when the price change is finalized, the user can sell the xezETH on a protocol that reads the price from the [**getRate**](https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/xRenzoDeposit.sol#L456) function in the **xRenzoDeposit** contract, thus profiting from the price discrepancy.

### Impact

Severity: Medium. This will allow users to exploit price changes by minting xezETH at a favourable rate before the price update is reflected.

Likelihood: High. Given the visibility of transactions in the mempool and the potential for arbitrage opportunities, it is likely that users will attempt to exploit this.

### Recommendation

Since there are two fees associated with L2 deposits, this should help minimize this problem. Additionally, as ezETH is more on the stable side, it is less prone to significant price fluctuations. However, continuous monitoring and adjustment of the update frequency may be necessary to prevent potential exploitation.

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/135#issuecomment-2122609851):**
 > Expected behaviour. 



***

## [[M-11] Fetched price from the oracle is not stored in `xRenzoDeposit`](https://github.com/code-423n4/2024-04-renzo-findings/issues/117)
*Submitted by [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/117), also found by [Fassi\_Security](https://github.com/code-423n4/2024-04-renzo-findings/issues/615)*

Failure to store the fetched price from the oracle in the storage variables of the `xRenzoDeposit` contract can result in several important issues.

### Proof of Concept

**Price Fetching on Deposit**: When a deposit is made in `xRenzoDeposit`, the `getMintRate` function fetches the price of `ezETH`.

```solidity
    function deposit(
        uint256 _amountIn,
        uint256 _minOut,
        uint256 _deadline
    ) external nonReentrant returns (uint256) {
        //....
        return _deposit(_amountIn, _minOut, _deadline);
    }

    function _deposit(
        uint256 _amountIn,
        uint256 _minOut,
        uint256 _deadline
    ) internal returns (uint256) {
        //......
        // Fetch price and timestamp of ezETH from the configured price feed
        (uint256 _lastPrice, uint256 _lastPriceTimestamp) = getMintRate();
        //......
    }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L204>

**Oracle vs. Storage**: If an oracle is defined, the function retrieves the price from the oracle. Otherwise, it reads the price from the storage variable `lastPrice`, which is updated by the `updatePrice` function.

```solidity
    function getMintRate() public view returns (uint256, uint256) {
        // revert if PriceFeedNotAvailable
        if (receiver == address(0) && address(oracle) == address(0)) revert PriceFeedNotAvailable();
        if (address(oracle) != address(0)) {
            (uint256 oraclePrice, uint256 oracleTimestamp) = oracle.getMintRate();
            return
                oracleTimestamp > lastPriceTimestamp
                    ? (oraclePrice, oracleTimestamp)
                    : (lastPrice, lastPriceTimestamp);
        } else {
            return (lastPrice, lastPriceTimestamp);
        }
    }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L286-L301>

```solidity
    function updatePrice(uint256 _price, uint256 _timestamp) external override {
        if (msg.sender != receiver) revert InvalidSender(receiver, msg.sender);
        _updatePrice(_price, _timestamp);
    }

    function _updatePrice(uint256 _price, uint256 _timestamp) internal {
        //.....

        lastPrice = _price;
        lastPriceTimestamp = _timestamp;

        //.....
    }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L303-L359>

**First Issue - Inaccurate Price Usage:** The first issue arises when the oracle is used to fetch the price but is not stored in the storage variables. Subsequent calls to `getMintRate` after the oracle is undefined may use the outdated price from storage instead of the most recent one fetched from the oracle. This leads to inaccurate pricing and potential financial losses. For example:

1. Suppose, the price is updated to 1 ether now, so the storage variables are `lastPrice = 1 ether` and `lastPriceTimestamp = k` (k is the timestamp of now).
2. Now, the oracle is defined by owner.
3. 3 hours later, a deposit is made, so `getMintRate` uses the oracle to fetch the price and returns the values from the oracle. For example the oracle returns `oraclePrice = 1.02 ether` and `oracleTimestamp = k + 3 hours`.
4. The owner sets the orcale undefined again by setting its address to zero.
5. After 2 hours, another deposit is made. So, `getMintRate` uses the storage variable again (because the oracle address is zero) to fetch the price and reads the storage variables. So, it returns `lastPrice = 1 ether` and `lastPriceTimestamp = k`, instead of the recent fetched price by the oracle `1.02 ether` and `k + 3 hours`.

It shows that although the recent fetched price and timestamp is `1.02 ether` and `k + 3 hours`, respectively, `getMintRate` returns the price of the time when they were stored in the storage variables during updating the price about 5 hours before.

**Second Issue - Divergence Check:** Another issue is that when the price is updated, the to-be-updated price is compared with the `lastPrice`. If, the oracle is used to fetch the price in between the updates, since the fetched price from the oracle is not stored in `lastPrice` variable, the to-be-updated price is compared with price stored in the storage variable before the oracle fetch. This undermines the trustworthiness of the divergence check mechanism.

```solidity
function _updatePrice(uint256 _price, uint256 _timestamp) internal {
    //....
    
    // Check for price divergence - more than 10%
        if (
            (_price > lastPrice && (_price - lastPrice) > (lastPrice / 10)) ||
            (_price < lastPrice && (lastPrice - _price) > (lastPrice / 10))
        ) {
            revert InvalidOraclePrice();
        }

    //...
}
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L330C5-L359C6>

**Third Issue - Manual Price Updates:** The third issue arises when the price update fails due to inaccurate divergence checks. For example:

1. Suppose the oracle is already defined and the price is updated to 1 ether now, so: `lastPrice = 1 ether` and `lastPriceTimestamp = k` (k is the timestamp now)
2. After 5 hours, a deposit is made, so `getMintRate` uses the oracle to fetch the price and returns the values from the oracle. For example: `oraclePrice = 1.11 ether` and `oracleTimestamp = k + 5 hours`.
3. After 1 hour, again the update price is called (because the on-chain transactions show that the interval for updates is 6 hours) to update the price. Suppose, this to-be-update price is `1.12 ether`. But, since it compares `1.12 ether` with `1 ether` at time `k`, its divergence is 12 percent, and it will revert. While, in reality, the divergence is between `1.12 ether` and `1.11` ether (the recent price fetched from the oracle) which is 0.9 percent.

In such cases, manual intervention is required by the admin to update the price, which adds complexity and overhead.

```solidity
function updatePriceByOwner(uint256 price) external onlyOwner {
       return _updatePrice(price, block.timestamp);
   }
```

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L320-L322>

### Recommended Mitigation Steps

To address these issues, it's recommended to modify the `getMintRate` function to store the fetched price from the oracle in the storage variables. This ensures that the most recent price is used for calculations.

```solidity
function getMintRate() public view returns (uint256, uint256) {
        // revert if PriceFeedNotAvailable
        if (receiver == address(0) && address(oracle) == address(0)) revert PriceFeedNotAvailable();
        if (address(oracle) != address(0)) {
            (uint256 oraclePrice, uint256 oracleTimestamp) = oracle.getMintRate();
            if(oracleTimestamp > lastPriceTimestamp){
                lastPrice = oraclePrice;
                lastPriceTimestamp = oracleTimestamp;
                return (oraclePrice, oracleTimestamp);
            } else {
                return (lastPrice, lastPriceTimestamp);
            }
        } else {
            return (lastPrice, lastPriceTimestamp);
        }
    }
```

### Assessed type

Oracle

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/117#issuecomment-2127933229):**
 > In practical, we are not using both configurations together. But yeah, can be acknowledged. In my opinion, this is a low severity not a high. 

**[alcueca (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/117#issuecomment-2129004977):**
 > The first issue described by the warden can be described as a governance error.

**[EV\_om (warden) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/117#issuecomment-2132384920):**
 > @alcueca - I agree with @jatinj615 here that this is a QA issue.
> 
> The first issue can be described as a governance issue as you said.
> 
> The second issue would be an issue in case of concurrent use of both the pull and push oracle configurations together as @jatinj615 pointed out, but that was never the intention here. The contract is working as designed, which is by only performing the divergence check _on the push mechanism_, against previous updates via the same mechanism.
> 
> The third issue is an inherent tradeoff of the divergence check - there is no way to prevent this issue while keeping the check, and it can be easily mitigated by the owner calling `updatePriceByOwner()` in incremental steps of 10% as pointed out by the warden.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/117#issuecomment-2132701312):**
 > The first issue is a governance issue, as agreed.
> 
> There is no documentation on the intended use of the code. The assumption from the original warden that both oracles would be used simultaneously is not an outrageous one, I assumed the same. Under that assumption, the second issue pointed out is valid.
> 
> On the third issue, I can see how the code is expected to halt due to large price changes, with an admin calling `updatePriceByOwner` to validate that the changes are real.

*Note: For full discussion, see [here](https://github.com/code-423n4/2024-04-renzo-findings/issues/117).*



***

## [[M-12] Incorrect exchange rate provided to Balancer pools](https://github.com/code-423n4/2024-04-renzo-findings/issues/113)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/113), also found by [Bauchibred](https://github.com/code-423n4/2024-04-renzo-findings/issues/588)*

The [`xRenzoDeposit`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol) contract, apart from being the entry point for deposits on L2s, also acts as a rate provider for Balancer pools on L2s, allowing them to determine the exchange rate between `xezWETH` and `WETH` tokens. Rate providers are crucial for Balancer pools to calculate token prices and determine yield protocol fees during joins and exits, as explained in the [Balancer documentation](https://docs.balancer.fi/reference/contracts/rate-providers.html).

However, the [`getRate()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L456) function in `xRenzoDeposit` does not provide the correct exchange rate. It simply returns the `lastPrice` state variable, which:

- May be stale if `updatePrice()` or `updatePriceByOwner()` have not been called recently.
- May be older than the rate provided by `oracle.getMintRate()`.
- Can be different from the rate at which xezETH are minted in [`_deposit()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Bridge/L2/xRenzoDeposit.sol#L227), which uses the newest of the oracle and internal `lastPrice` values, opening up arbitrage opportunities.

### Impact

By providing an incorrect and potentially outdated exchange rate, `xRenzoDeposit` can cause Balancer pools to misprice `xezWETH` relative to `WETH`. This can lead to incorrect yield calculations and enable manipulation of pool joins and exits.

### Proof of Concept

1. `xRenzoDeposit` is set as the rate provider between `xezWETH` and `WETH` for a Balancer pool.
2. The price of `ezETH` relative to `ETH` changes on L1, but the receiver fails and `updatePrice()` is not called on `xRenzoDeposit`.
3. However, the oracle feed still provides accurate data.
4. A user executes an operation on a WETH/xezETH Balancer pool, which calls `getRate()` on `xRenzoDeposit` to fetch the price.
5. `getRate()` returns the stale price from the internal `lastPrice` variable.
6. The Balancer pool uses this incorrect rate for its calculations, leading to mispricing of `xezWETH` and potential manipulation.

### Recommended Mitigation Steps

Update the `getRate()` function to provide the same exchange rate used when minting `xezETH`. This can be achieved by calling `getMintRate()` instead of returning `lastPrice` directly:

```diff
- return lastPrice;
+ (uint256 rate, uint256 timestamp) = getMintRate();
+ require(block.timestamp <= timestamp + 1 days, "Price is stale");
+ return rate;
```

This ensures that the rate provided to Balancer pools is consistent with the actual minting rate and is not stale.

**[jatinj615 (Renzo) confirmed](https://github.com/code-423n4/2024-04-renzo-findings/issues/113#event-12880180154)**

**[Renzo mitigated](https://github.com/code-423n4/2024-06-renzo-mitigation?tab=readme-ov-file#scope):**
> The PR adds staleness check in `getRate` function for `balancerPools` on L2.

**Status:** Mitigation confirmed. Full details in reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/15), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/54), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/47), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/32), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/29).



***

## [[M-13] Pending withdrawals prevent safe removal of collateral assets](https://github.com/code-423n4/2024-04-renzo-findings/issues/103)
*Submitted by [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/103), also found by [kennedy1030](https://github.com/code-423n4/2024-04-renzo-findings/issues/594), Bauchibred ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/589), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/5)), [ZanyBonzy](https://github.com/code-423n4/2024-04-renzo-findings/issues/587), [inzinko](https://github.com/code-423n4/2024-04-renzo-findings/issues/583), [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/575), [OMEN](https://github.com/code-423n4/2024-04-renzo-findings/issues/573), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/465), [TECHFUND](https://github.com/code-423n4/2024-04-renzo-findings/issues/405), [14si2o\_Flint](https://github.com/code-423n4/2024-04-renzo-findings/issues/404), Hajime ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/403), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/95)), oxwhite ([1](https://github.com/code-423n4/2024-04-renzo-findings/issues/271), [2](https://github.com/code-423n4/2024-04-renzo-findings/issues/100), [3](https://github.com/code-423n4/2024-04-renzo-findings/issues/99), [4](https://github.com/code-423n4/2024-04-renzo-findings/issues/96)), [golu](https://github.com/code-423n4/2024-04-renzo-findings/issues/102), [Bigsam](https://github.com/code-423n4/2024-04-renzo-findings/issues/101), [CodeWasp](https://github.com/code-423n4/2024-04-renzo-findings/issues/98), and [0xAadi](https://github.com/code-423n4/2024-04-renzo-findings/issues/97)*

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L316-L321> 

<https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/Withdraw/WithdrawQueue.sol#L279>

### Vulnerability details

The [`RestakeManager`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol) contract allows the admin to add and remove collateral tokens that are accepted for deposits into the protocol via the [`addCollateralToken()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L220) and [`removeCollateralToken()`](https://github.com/code-423n4/2024-04-renzo/blob/main/contracts/RestakeManager.sol#L244) functions.

From the protocol team:

> (In order to) remove a collateral token we can withdraw full and increase the withdraw buffer to let users withdraw it.

However, since users cannot be forced to claim their withdrawals, it is always possible that a significant amount of the collateral token remains in the `WithdrawQueue` indefinitely in outstanding withdrawals.

In that case, calling `removeCollateralToken()` for that token would break accounting in the protocol. The `ezETH` total supply would still reflect the amounts that were burned to initiate those withdrawals, but the token balance in the `WithdrawQueue` would no longer be counted towards the TVL.

### Impact

The `RestakeManager` admin is unable to safely remove a collateral token. Removing the token anyway would inflate the `ezETH` mint and redeem rate compared to the actual backing collateral value.

### Proof of Concept

Assume `token1` has a balance of `Y` in the `WithdrawQueue` from pending user withdrawals. If `removeCollateralToken(token1)` is called:

1. `token1` is removed from the `collateralTokens` array.
2. `token1` balance of `Y` is still in `WithdrawQueue` but no longer counted in `totalTVL`.
3. Mint rate for `ezETH` increases since `totalTVL` is lower but `ezETH` total supply is unchanged.
4. Redeem rate for `ezETH` also increases since `ezETH` is now redeemable for a larger share of the remaining collateral.

The mint and redeem rates for `ezETH` are now inflated compared to the true value of the collateral backing it, since `Y` worth of `token1` is not accounted for in `totalTVL` but is still effectively backing the `ezETH` that was burned to withdraw it.

### Recommended Mitigation Steps

Consider forcing pending withdrawals of a token to be claimed before that token can be removed as collateral. This could be done by only allowing `removeCollateralToken()` to be called if `claimReserve[token] == 0`.

Alternatively, include the balance of the `WithdrawQueue` in the TVL calculation even for tokens that have been removed, as long as there are still pending withdrawals of that token. This would ensure mint and redeem rates remain correct.

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/103#issuecomment-2142257978):**
 > Will be partially mitigating this by having a sanity check on `removeCollateralToken` to revert if `withdrawQueue` Balance is non zero for the collateral asset getting removed. 
> 
> The force `kickOff` will be implemented later on. 



***

## [[M-14] stETH/ETH feed being used opens up to 2 way `deposit<->withdrawal` arbitrage](https://github.com/code-423n4/2024-04-renzo-findings/issues/13)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2024-04-renzo-findings/issues/13), also found by [0xabhay](https://github.com/code-423n4/2024-04-renzo-findings/issues/614), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/613), [zhaojohnson](https://github.com/code-423n4/2024-04-renzo-findings/issues/429), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/428), [p0wd3r](https://github.com/code-423n4/2024-04-renzo-findings/issues/427), [peanuts](https://github.com/code-423n4/2024-04-renzo-findings/issues/426), [GoatedAudits](https://github.com/code-423n4/2024-04-renzo-findings/issues/425), and [d3e4](https://github.com/code-423n4/2024-04-renzo-findings/issues/424)*

The stETH/ETH oracle is not a exchange rate feed, it's a Market Rate Feed, while other feeds are exchange rate feeds.

This opens up ezETH to be vulnerable to:
- Market Rate Manipulations.
- Sentiment based Price Action.
- Duration based discounts.

### POC

This opens up to arbitrage anytime stETH trades at a discount (see Liquidations on the 13th of April).

Had withdrawals been open, the following could have been possible:
- Deposit stETH before the Depeg (front-run oracle update).
- Get ezETH.
- Withdraw stETH after the depeg (1% a day, around 365% APR).

As well as:
- stETH market depegs.
- Deposit ETH for ezETH.
- Withdraw stETH at premium (about 1% arbitrage, around 365% APR).

### Mitigation

I believe the withdrawal logic needs to be rethought to be denominated in ETH. The suggested architecture would look like the following:
- Deposit of ETH or LSTs, estimated via a pessimistic exchange rate.
- Withdraw exclusively ETH, while pricing in slashing, discounts and operative costs.

### Assessed type

Oracle

**[jatinj615 (Renzo) acknowledged and commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/13#issuecomment-2111193627):**
 > Expected Behaviour.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/13#issuecomment-2119584693):**
 > It is debatable whether the market or exchange rate is the real price. The market price is the price for an instant trade, while the exchange rate is the price for a trade in the terms of the stETH contract. Renzo is not even using a real market price, which would be retrieved from a DEX. Whatever the choice of oracle, there will be some arbitrage opportunities.

**[alcueca (judge) commented](https://github.com/code-423n4/2024-04-renzo-findings/issues/13#issuecomment-2132930547):**
 > Regarding PJQA [here](https://github.com/code-423n4/2024-04-renzo-findings/discussions/596#discussioncomment-9555242), I do actually know of other protocols working on similar topics that have recognized this as a problem and taken significant steps to avoid it.
>
 > Mitigation from sponsor on [#424](https://github.com/code-423n4/2024-04-renzo-findings/issues/424), along with explanation on why both groups should be merged. Namely, that using the market rate for stETH/ETH is what enables arbitraging between different collaterals, and that the fix from this finding will also fix the duplicates.



***

# Low Risk and Non-Critical Issues

For this audit, 55 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2024-04-renzo-findings/issues/557) by **Sathish9098** received the top score from the judge.

*The following wardens also submitted reports: [ZanyBonzy](https://github.com/code-423n4/2024-04-renzo-findings/issues/539), [oakcobalt](https://github.com/code-423n4/2024-04-renzo-findings/issues/30), [kennedy1030](https://github.com/code-423n4/2024-04-renzo-findings/issues/555), [Fassi\_Security](https://github.com/code-423n4/2024-04-renzo-findings/issues/554), [hunter\_w3b](https://github.com/code-423n4/2024-04-renzo-findings/issues/549), [zzykxx](https://github.com/code-423n4/2024-04-renzo-findings/issues/547), [Bauchibred](https://github.com/code-423n4/2024-04-renzo-findings/issues/543), [atoko](https://github.com/code-423n4/2024-04-renzo-findings/issues/541), [LessDupes](https://github.com/code-423n4/2024-04-renzo-findings/issues/515), [honey-k12](https://github.com/code-423n4/2024-04-renzo-findings/issues/511), [fyamf](https://github.com/code-423n4/2024-04-renzo-findings/issues/505), [crypticdefense](https://github.com/code-423n4/2024-04-renzo-findings/issues/500), [GoatedAudits](https://github.com/code-423n4/2024-04-renzo-findings/issues/497), [Sparrow](https://github.com/code-423n4/2024-04-renzo-findings/issues/473), [araj](https://github.com/code-423n4/2024-04-renzo-findings/issues/382), [pauliax](https://github.com/code-423n4/2024-04-renzo-findings/issues/23), [GalloDaSballo](https://github.com/code-423n4/2024-04-renzo-findings/issues/18), [0xCiphky](https://github.com/code-423n4/2024-04-renzo-findings/issues/610), [underdog](https://github.com/code-423n4/2024-04-renzo-findings/issues/608), [b0g0](https://github.com/code-423n4/2024-04-renzo-findings/issues/603), [Rhaydden](https://github.com/code-423n4/2024-04-renzo-findings/issues/559), [hihen](https://github.com/code-423n4/2024-04-renzo-findings/issues/558), [SBSecurity](https://github.com/code-423n4/2024-04-renzo-findings/issues/556), [oualidpro](https://github.com/code-423n4/2024-04-renzo-findings/issues/553), [ladboy233](https://github.com/code-423n4/2024-04-renzo-findings/issues/550), [K42](https://github.com/code-423n4/2024-04-renzo-findings/issues/546), [kind0dev](https://github.com/code-423n4/2024-04-renzo-findings/issues/542), [adeolu](https://github.com/code-423n4/2024-04-renzo-findings/issues/538), [jokr](https://github.com/code-423n4/2024-04-renzo-findings/issues/528), [inzinko](https://github.com/code-423n4/2024-04-renzo-findings/issues/526), [carlitox477](https://github.com/code-423n4/2024-04-renzo-findings/issues/525), [ABAIKUNANBAEV](https://github.com/code-423n4/2024-04-renzo-findings/issues/524), [ReadyPlayer2](https://github.com/code-423n4/2024-04-renzo-findings/issues/523), [kinda\_very\_good](https://github.com/code-423n4/2024-04-renzo-findings/issues/517), [gumgumzum](https://github.com/code-423n4/2024-04-renzo-findings/issues/516), [Sabit](https://github.com/code-423n4/2024-04-renzo-findings/issues/506), [t0x1c](https://github.com/code-423n4/2024-04-renzo-findings/issues/504), [xg](https://github.com/code-423n4/2024-04-renzo-findings/issues/468), [rbserver](https://github.com/code-423n4/2024-04-renzo-findings/issues/401), [0xmystery](https://github.com/code-423n4/2024-04-renzo-findings/issues/397), [lanrebayode77](https://github.com/code-423n4/2024-04-renzo-findings/issues/387), [aslanbek](https://github.com/code-423n4/2024-04-renzo-findings/issues/386), [FastChecker](https://github.com/code-423n4/2024-04-renzo-findings/issues/381), [0x73696d616f](https://github.com/code-423n4/2024-04-renzo-findings/issues/379), [WildSniper](https://github.com/code-423n4/2024-04-renzo-findings/issues/378), [adam-idarrha](https://github.com/code-423n4/2024-04-renzo-findings/issues/377), [gesha17](https://github.com/code-423n4/2024-04-renzo-findings/issues/376), [gjaldon](https://github.com/code-423n4/2024-04-renzo-findings/issues/157), [tapir](https://github.com/code-423n4/2024-04-renzo-findings/issues/149), [BiasedMerc](https://github.com/code-423n4/2024-04-renzo-findings/issues/109), [jesjupyter](https://github.com/code-423n4/2024-04-renzo-findings/issues/79), [grearlake](https://github.com/code-423n4/2024-04-renzo-findings/issues/57), [KupiaSec](https://github.com/code-423n4/2024-04-renzo-findings/issues/50), and [Limbooo](https://github.com/code-423n4/2024-04-renzo-findings/issues/4).*

## Low Findings Summary

| Issue Number | Issue Title |
|---------------|-------------|
| [L-01] | `block.timestamp - _withdrawRequest.createdAt < coolDownPeriod` check breaks the intended functionality |
| [L-02] | Timestamp Verification Discrepancies Between `RenzoOracle` and `_deposit()` Function |
| [L-03] | Risk of Unchecked Oracle Price Anomalies in `lookupTokenValue()` function |
| [L-04] | Risk of Suboptimal Delegator Selection Due to First-Match Approach in `chooseOperatorDelegatorForDeposit()` |
| [L-05] | Replay Attacks and Stale Authorizations Due to Non-Expiring Signatures |
| [L-06] | Risk of Imbalanced Load Distribution Due to Default Selection Bias `chooseOperatorDelegatorForDeposit()` function |
| [L-07] | Unrestricted maximum value in `coolDownPeriod()` |
| [L-08] | `xReceive()` become DOS when `RestakeManager` paused |
| [L-09] | `sweepBatchSize * bridgeFeeShare) / FEE_BASIS` For large deposits protocol loss huge value since the fee calculation is fixed for deposit greater than 32ETH |
| [L-10] | Inconsistency in Price Validation Between `Oracle` and `CCIPReceiver` |
| [L-11] | Untracked `bridgeRouterFeeBps` Fees Compromise Protocol Accounting and Result in Losses |
| [L-12] | Misguided Zero-Value Checks for uint256 |
| [L-13] | Division by Zero in calculateRedeemAmount Function for Zero ezETH Supply |
| [L-14] | Wrong Comment in `setPaused()` function |
| [L-15] | The `_allocationBasisPoints ` declaration contradict with actual implementation |
| [L-16] | Lack of check for `_transferId` uniqueness in `xReceive` function |
| [L-17] | Compromised `WithdrawQueueAdmin` Could Set Excessive `coolDownPeriod` |
| [L-18] | Lack of Clarity in `MAX_TIME_WINDOW` Definition Extending to `24 Hours and 60 Seconds` in `RenzoOracle` |
| [L-19] | Allowing `withdraw()` and `claim()` when contract paused poses unintended consequences |
| [L-20] | Restrictive Cross-Chain Token Address Validation |
| [L-21] | `bridgeTo` function vulnerable to reentrancy attacks |
| [L-22] | Immutable Delegate Address Elevates Security Risk |
| [L-23] | Fund Immobilization Risk Due to Null Strategy Address |
| [L-24] | Automatic ETH Processing and Fee Deduction Without `SenderVerification` |
| [L-25] | Vulnerability to Excessive Gas Cost Refunds Potentially Draining Contract Funds |

## [L-01] `block.timestamp - _withdrawRequest.createdAt < coolDownPeriod` check breaks the intended functionality

The problem arises because the code allows a claim to be processed the exact moment the `coolDownPeriod` equals the time difference between the current time and the request creation time. Claims to be permitted only after the entire `coolDownPeriod` has fully elapsed. Current check `block.timestamp - _withdrawRequest.createdAt < coolDownPeriod` intented functionality. This will allow claims even the coolDownPeriod not fully elapsed.

```solidity
FILE: 2024-04-renzo/contracts/Withdraw/WithdrawQueue.sol

287: if (block.timestamp - _withdrawRequest.createdAt < coolDownPeriod) revert EarlyClaim();
```

### Recommended Mitigation

```solidity
287: if (block.timestamp - _withdrawRequest.createdAt <= coolDownPeriod) revert EarlyClaim();
```

## [L-02] Timestamp Verification Discrepancies Between `RenzoOracle` and `_deposit()` Function

The issue arises from a mismatch in staleness thresholds: the `RenzoOracle` uses a staleness check of "1 day + 60 seconds," whereas the `_deposit` function uses exactly "1 day." This inconsistency in timestamp verification can lead to contradictory behaviors between the two components. 

```solidity
FILE: 2024-04-renzo/contracts/Oracle
/RenzoOracle.sol

 /// @dev The maximum staleness allowed for a price feed from chainlink
26:  uint256 constant MAX_TIME_WINDOW = 86400 + 60; // 24 hours + 60 seconds

76: if (timestamp < block.timestamp - MAX_TIME_WINDOW) revert OraclePriceExpired();
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Oracle/RenzoOracle.sol#L76

```solidity 
FILE: 2024-04-renzo/contracts/Bridge/L2/xRenzoDeposit.sol

52: if (block.timestamp > _lastPriceTimestamp + 1 days) {
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/xRenzoDeposit.sol#L248

## [L-03] Risk of Unchecked Oracle Price Anomalies in `lookupTokenValue()` function

Oracles serve as bridges between external data sources and the blockchain. However, the integrity of the data they provide can be compromised by errors in data feeds, manipulation by attackers, or even technical malfunctions.

### Impact

Sudden, unrealistic spikes or drops in price data can occur, which do not accurately reflect market conditions.

If an attacker can influence the oracle, either directly by tampering with the data source or indirectly through market manipulation, they might feed incorrect prices to the smart contract.

```solidity
FILE: 2024-04-renzo/contracts/Oracle/RenzoOracle.sol

 /// @dev Given a single token and balance, return value of the asset in underlying currency
    /// The value returned will be denominated in the decimal precision of the lookup oracle
    /// (e.g. a value of 100 would return as 100 * 10^18)
    function lookupTokenValue(IERC20 _token, uint256 _balance) public view returns (uint256) {
        AggregatorV3Interface oracle = tokenOracleLookup[_token];
        if (address(oracle) == address(0x0)) revert OracleNotFound();

        (, int256 price, , uint256 timestamp, ) = oracle.latestRoundData();
        if (timestamp < block.timestamp - MAX_TIME_WINDOW) revert OraclePriceExpired();
        if (price <= 0) revert InvalidOraclePrice();

        // Price is times 10**18 ensure value amount is scaled
        return (uint256(price) * _balance) / SCALE_FACTOR;
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Oracle/RenzoOracle.sol#L68-L81

## [L-04] Risk of Suboptimal Delegator Selection Due to First-Match Approach in `chooseOperatorDelegatorForDeposit()` 

Multiple delegators have TVLs (Total Value Locked) below their respective thresholds, the function `chooseOperatorDelegatorForDeposit` will select and return the first delegator that meets this condition as it iterates through the list of delegators. This means that the function does not compare all delegators to find the one with the lowest TVL relative to their threshold but rather returns the first one it encounters that fits the criteria.

### Impact 

The first-match approach may inadvertently favor certain delegators that are consistently earlier in the list. This could introduce a `bias in selection`, disadvantaging other `delegators` . Without considering the full context of each delegator’s current load and capabilities, there's a risk of creating imbalances where some delegators are overwhelmed while others are underutilized. This can lead to inefficiencies and increased wear on certain parts of the system.

```solidity
FILE: 2024-04-renzo/contracts/RestakeManager.sol

 // Otherwise, find the operator delegator with TVL below the threshold
        uint256 tvlLength = tvls.length;
        for (uint256 i = 0; i < tvlLength; ) {
            if (
                tvls[i] <
                (operatorDelegatorAllocations[operatorDelegators[i]] * totalTVL) /
                    BASIS_POINTS /
                    BASIS_POINTS
            ) {
                return operatorDelegators[i];
            }

            unchecked {
                ++i;
            }
        }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol#L375-L384

### Recommended Mitigation

Modify the selection algorithm to assess all delegators, calculating and comparing the difference between their current TVL and the threshold, and selecting the one with the greatest difference.

## [L-05] Replay Attacks and Stale Authorizations Due to Non-Expiring Signatures

Suppose a signature used in the transaction does not include an expiry time. This omission can make it vulnerable to replay attacks where the same transaction (signature) could be submitted repeatedly, potentially leading to unauthorized staking of ETH.

If the signature does not expire, it could be used long after the user’s intentions have changed. For example, a user might initially authorize a staking transaction but later, due to changing market conditions or personal preferences, wish to retract this authorization.

### Impact

The repeated staking can cause financial discrepancies, allocate resources improperly, or disrupt the intended distribution and management of staked assets.

The smart contract would still process the transaction based on the old, now potentially unwanted, authorization, leading to mismanagement of user funds or assets against their current wishes.

```solidity
FILE: 2024-04-renzo/contracts/RestakeManager.sol

/// @dev Called by the deposit queue to stake ETH to a validator
    /// Only callable by the deposit queue
    function stakeEthInOperatorDelegator(
        IOperatorDelegator operatorDelegator,
        bytes calldata pubkey,
        bytes calldata signature,
        bytes32 depositDataRoot
    ) external payable onlyDepositQueue {
        // Verify the OD is in the list
        bool found = false;
        uint256 odLength = operatorDelegators.length;
        for (uint256 i = 0; i < odLength; ) {
            if (operatorDelegators[i] == operatorDelegator) {
                found = true;
                break;
            }

            unchecked {
                ++i;
            }
        }
        if (!found) revert NotFound();

        // Call the OD to stake the ETH
        operatorDelegator.stakeEth{ value: msg.value }(pubkey, signature, depositDataRoot);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol#L618-L643

## [L-06] Risk of Imbalanced Load Distribution Due to Default Selection Bias `chooseOperatorDelegatorForDeposit()` function 

### Impact

There could be a consistent bias towards the first `OperatorDelegator`, especially in scenarios where frequently all `OperatorDelegator`'s exceed their respective thresholds. This can create an uneven distribution of deposits, potentially overloading the first `OperatorDelegator`.

If the first `OperatorDelegator` has significantly different operational characteristics or capacities compared to others, consistently defaulting to it might lead to inefficiencies or increased risks of failure.

The function does not balance the load among `OperatorDelegator`'s effectively if it always falls back to the first. This could defeat the purpose of having multiple `OperatorDelegator`'s, which is typically to distribute workload and reduce risks.

```solidity
FILE: 2024-04-renzo/contracts/RestakeManager.sol

/// @dev Picks the OperatorDelegator with the TVL below the threshold or returns the first one in the list
    /// @return The OperatorDelegator to use
    function chooseOperatorDelegatorForDeposit(
        uint256[] memory tvls,
        uint256 totalTVL
    ) public view returns (IOperatorDelegator) {
        // Ensure OperatorDelegator list is not empty
        if (operatorDelegators.length == 0) revert NotFound();

        // If there is only one operator delegator, return it
        if (operatorDelegators.length == 1) {
            return operatorDelegators[0];
        }

        // Otherwise, find the operator delegator with TVL below the threshold
        uint256 tvlLength = tvls.length;
        for (uint256 i = 0; i < tvlLength; ) {
            if (
                tvls[i] <
                (operatorDelegatorAllocations[operatorDelegators[i]] * totalTVL) /
                    BASIS_POINTS /
                    BASIS_POINTS
            ) {
                return operatorDelegators[i];
            }

            unchecked {
                ++i;
            }
        }

        // Default to the first operator delegator
        return operatorDelegators[0];
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol#L360-L393

## [L-07] Unrestricted maximum value in `coolDownPeriod()` 

Currently the cooldown period is 7 days as per docs. If set maximum values uses can't withdraw their tokes. 

```
 wait the timeout period (7 days on mainnet), 
```

```solidity
FILE: 2024-04-renzo/contracts/Withdraw/WithdrawQueue.sol

/**
     * @notice Updates the coolDownPeriod for withdrawal requests
     * @dev    It is a permissioned call (onlyWithdrawQueueAdmin)
     * @param   _newCoolDownPeriod  new coolDownPeriod in seconds
     */
    function updateCoolDownPeriod(uint256 _newCoolDownPeriod) external onlyWithdrawQueueAdmin {
        if (_newCoolDownPeriod == 0) revert InvalidZeroInput();
        emit CoolDownPeriodUpdated(coolDownPeriod, _newCoolDownPeriod);
        coolDownPeriod = _newCoolDownPeriod;
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Withdraw/WithdrawQueue.sol#L124-L133

## [L-08] `xReceive()` become DOS when `RestakeManager` paused  

When `RestakeManager` is paused, attempting to call `depositETH` will lead to a revert, usually triggered by a require statement checking the paused state. This prevents any new funds from being accepted into the system, safeguarding users’ assets from being locked in a potentially compromised or unstable environment.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L1/xRenzoBridge.sol

// Deposit it into Renzo RestakeManager
        restakeManager.depositETH{ value: ethAmount }();
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L1/xRenzoBridge.sol#L174-L175

```solidity
FILE: 2024-04-renzo/contracts/RestakeManager.sol

592: function depositETH(uint256 _referralId) public payable nonReentrant notPaused {
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol#L592

## [L-09] `sweepBatchSize * bridgeFeeShare) / FEE_BASIS` For large deposits protocol loss huge value since the fee calculation is fixed for deposit greater than 32ETH 

When a user deposits an amount significantly larger than 32 ETH, the system still only deducts the fee equivalent to what would be deducted for 32 ETH. This creates an imbalance where the system may not be collecting sufficient fees proportional to the amount being processed. This could potentially lead to revenue loss for the system if the cost of handling larger transactions (like security, operational costs) scales with the transaction size.

Let's recalculate the fee using the correct bridgeFeeShare of 0.05% for a 1000 ETH deposit, based on your specifications:

### POC

Lets assume,
`sweepBatchSize` = 32 ETH<br>
`bridgeFeeShare` = 5 (which equates to 0.05% fee since `FEE_BASIS` is 10000)<br>
`FEE_BASIS` = 10000<br>
`_amountIn` = 1000 ETH

As per implementation
Fee = `(32 ETH * 5) / 10000 = 160 / 10000 = 0.016 ETH - > 0.0016%`

As per original deposit
Fee = `(1000 ETH * 5) / 10000 = 5000 / 10000 = 0.5 ETH  - > 0.05%`

Loss to Protocol = Fee using proportional mechanism - Fee using current mechanism
Loss to Protocol = 0.5 ETH - 0.016 ETH = 0.484 ETH

Its very huge lose to protocol and This breaks the 0.05% fee invariants.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L2/xRenzoDeposit.sol

/**
     * @notice Function returns bridge fee share for deposit
     * @param _amountIn deposit amount in terms of ETH
     */
    function getBridgeFeeShare(uint256 _amountIn) public view returns (uint256) {
        // deduct bridge Fee share
        if (_amountIn < sweepBatchSize) {
            return (_amountIn * bridgeFeeShare) / FEE_BASIS;
        } else {
            return (sweepBatchSize * bridgeFeeShare) / FEE_BASIS;
        }
    }
``` 

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/xRenzoDeposit.sol#L273C4-L284

### Recommended Mitigation

Implement the 0.05% percent invariant for all deposits.

## [L-10] Inconsistency in Price Validation Between `Oracle` and `CCIPReceiver`

When fetching the price from `RenzoOracleL2`, the system strictly checks that the ezETH price is not less than 1 ether, reverting with `InvalidOraclePrice()` if it is. However, when updating ezETH via `CCIPReceiver`, there is no check to ensure that the price of ezETH meets this criterion. Technically, when fetching price data from `CCIPReceiver`, the `lastPrice` can be below 1 ETH. This represents an inconsistency in the price implementation.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L2/Oracle/RenzoOracleL2.sol

55: if (_scaledPrice < 1 ether) revert InvalidOraclePrice();
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/Oracle/RenzoOracleL2.sol#L55

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L2/xRenzoDeposit.sol

 /**
     * @notice  Updates the price feed
     * @dev     This function will receive the price feed and timestamp from the L1 through CCIPReceiver middleware contract.
     *          It should verify the origin of the call and only allow permissioned source to call.
     * @param   _price The price of ezETH sent via L1.
     * @param   _timestamp The timestamp at which L1 sent the price.
     */
    function updatePrice(uint256 _price, uint256 _timestamp) external override {
        if (msg.sender != receiver) revert InvalidSender(receiver, msg.sender);
        _updatePrice(_price, _timestamp);
    }


/**
     * @notice  Internal function to update price
     * @dev     Sanity checks input values and updates prices
     * @param   _price  Current price of ezETH to ETH - 18 decimal precision
     * @param   _timestamp  The timestamp of the price update
     */
    function _updatePrice(uint256 _price, uint256 _timestamp) internal {
        // Check for 0
        if (_price == 0) {
            revert InvalidZeroInput();
        }

        // Check for price divergence - more than 10%
        if (
            (_price > lastPrice && (_price - lastPrice) > (lastPrice / 10)) ||
            (_price < lastPrice && (lastPrice - _price) > (lastPrice / 10))
        ) {
            revert InvalidOraclePrice();
        }

        // Do not allow older price timestamps
        if (_timestamp <= lastPriceTimestamp) {
            revert InvalidTimestamp(_timestamp);
        }

        // Do not allow future timestamps
        if (_timestamp > block.timestamp) {
            revert InvalidTimestamp(_timestamp);
        }

        // Update values and emit event
        lastPrice = _price;
        lastPriceTimestamp = _timestamp;

        emit PriceUpdated(_price, _timestamp);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/xRenzoDeposit.sol#L330-L359

## [L-11] Untracked `bridgeRouterFeeBps` Fees Compromise Protocol Accounting and Result in Losses

The `bridgeRouterFeeBps` fee is deducted from `amountNextWETH`, but it is not accounted for, and it is unclear what happens to that fee. Although the fee is subtracted from the amount, the protocol does not track this fee, nor is it claimed anywhere within the protocol. It remains unclear what happens to the fee once it is deducted from the amount. This will break the overall protocol accounting.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L2/xRenzoDeposit.sol

 // Subtract the bridge router fee
        if (bridgeRouterFeeBps > 0) {
            uint256 fee = (amountNextWETH * bridgeRouterFeeBps) / 10_000;
            amountNextWETH -= fee;
        }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L2/xRenzoDeposit.sol#L384-L388

## [L-12] Misguided Zero-Value Checks for uint256

Since `uint256` cannot be negative, the check `_amount < 0` is inherently impossible. This leaves only the possibility of _amount being equal to zero as a valid check.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/Connext/integratio/LockboxAdapterBlast.sol

65: if (_amount <= 0) {
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/Connext/integration/LockboxAdapterBlast.sol#L65

### Recommended Mitigation

```solidity
if (_amount == 0) {
```

## [L-13] Division by Zero in `calculateRedeemAmount` Function for Zero ezETH Supply 

The operation `(_currentValueInProtocol * _ezETHBeingBurned) / _existingEzETHSupply` can lead to a division by zero if `_existingEzETHSupply` is zero. 

```solidity
FILE: 2024-04-renzo/contracts/Oracle/RenzoOracle.sol

 function calculateRedeemAmount(
        uint256 _ezETHBeingBurned,
        uint256 _existingEzETHSupply,
        uint256 _currentValueInProtocol
    ) external pure returns (uint256) {
        // This is just returning the percentage of TVL that matches the percentage of ezETH being burned
        uint256 redeemAmount = (_currentValueInProtocol * _ezETHBeingBurned) / _existingEzETHSupply;

        // Sanity check
        if (redeemAmount == 0) revert InvalidTokenAmount();

        return redeemAmount;
    }
``` 

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Oracle/RenzoOracle.sol#L152-L164

## [L-14] Wrong Comment in `setPaused()` function

The comment suggest only restake manager admin to set the paused state. But in actual implementation `onlyDepositWithdrawPauserAdmin` set the paused state.

```diff
FILE: 2024-04-renzo/contracts/RestakeManager.sol

- /// @dev Allows a restake manager admin to set the paused state of the contract
+ /// @dev Allows a DepositWithdrawPauserAdmin to set the paused state of the contract
    function setPaused(bool _paused) external onlyDepositWithdrawPauserAdmin {
        paused = _paused;
    }
```

## [L-15] The `_allocationBasisPoints` declaration contradicts with actual implementation

Declaration suggests this will accept uint256 range of the values. But in actual implementations, this will revert if the value is greater than 10000.

```solidity
FILE: 2024-04-renzo/contracts/RestakeManager.sol

133: uint256 _allocationBasisPoints

146: if (_allocationBasisPoints > (100 * BASIS_POINTS)) revert OverMaxBasisPoints();
``` 

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/RestakeManager.sol#L146

## [L-16] Lack of check for `_transferId` uniqueness in `xReceive` function

Even though `_transferId` is generated using Keccak-256—a cryptographic hashing function. It's worth acknowledging that while extremely rare, the possibility of collisions (two distinct input sets producing the same hash output) theoretically exists. Despite the low probability, the possibility of a collision cannot be completely dismissed, especially as computational power increases or through a breakthrough in cryptographic research.

  
The `EzETHMinted` event is designed to log instances of minting operations for ezETH. However, if the Connext contract calls the function associated with this event multiple times using the same `_transferId` for different transactions, the uniqueness and traceability of these events are compromised. Each event emission with the same `_transferId` but varying other parameters (such as `_amount`, `_origin`, or `_originSender`) could lead to difficulties in accurately tracking each transaction's specifics, potentially confusing event monitoring tools and data consumers.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/L1/xRenzoBridge.sol

function xReceive(
        bytes32 _transferId,
        uint256 _amount,
        address _asset,
        address _originSender,
        uint32 _origin,
        bytes memory
    ) external nonReentrant returns (bytes memory) {

// Emit the event
        emit EzETHMinted(_transferId, _amount, _origin, _originSender, ezETHAmount);
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/L1/xRenzoBridge.sol#L195-L196

##

## [L-17] Compromised `WithdrawQueueAdmin` Could Set Excessive `coolDownPeriod`

The function updateCoolDownPeriod allows a WithdrawQueueAdmin to change the cooldown period, which is a critical parameter affecting the operation of the claim() function. If this period is set to an excessively long duration maliciously or due to a compromise, it can effectively prevent users from claiming their withdrawals, resulting in a Denial of Service (DoS) for all users dependent on this functionality.

```solidity
FILE: 2024-04-renzo/contracts/Withdraw/WithdrawQueue.sol

 function updateCoolDownPeriod(uint256 _newCoolDownPeriod) external onlyWithdrawQueueAdmin {
        if (_newCoolDownPeriod == 0) revert InvalidZeroInput();
        emit CoolDownPeriodUpdated(coolDownPeriod, _newCoolDownPeriod);
        coolDownPeriod = _newCoolDownPeriod;
    }

```
https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Withdraw/WithdrawQueue.sol#L129-L133

## [L-18] Lack of Clarity in `MAX_TIME_WINDOW` Definition Extending to `24 Hours and 60 Seconds` in `RenzoOracle`

In the `RenzoOracle` implementation, the staleness threshold for price feeds is set to 1 day plus 1 minute (86460 seconds), deviating from the typical 1-day period commonly used in other oracles. This deviation is not clearly documented, potentially leading to confusion regarding the freshness criteria of data. Properly documenting and justifying the rationale for this additional 60 seconds is crucial to ensure transparency and prevent misunderstandings about the oracle's data validity period. Clear documentation is also essential for maintaining consistent expectations and operations across systems that depend on this oracle for timely and accurate data.

```solidity
FILE: 2024-04-renzo/contracts/Oracle/RenzoOracle.sol

/// @dev The maximum staleness allowed for a price feed from chainlink
    uint256 constant MAX_TIME_WINDOW = 86400 + 60; // 24 hours + 60 seconds
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Oracle/RenzoOracle.sol#L25-L26

## [L-19] Allowing `withdraw()` and `claim()` when contract paused poses unintended consequences 

If `withdrawal` and `claim` functionalities are allowed during a pause, it could lead to security vulnerabilities being exploited despite the pause, negating the purpose of freezing the contract’s operations. Allowing transactions during a pause can lead to inconsistencies in state, especially if the pause is intended to halt all contract activities for a critical update or fix.

Implement `WhenNotPaused` Modifier for both withdraw and claim functions.

```solidity
FILE: 2024-04-renzo/contracts/Withdraw/WithdrawQueue.sol

206: function withdraw(uint256 _amount, address _assetOut) external nonReentrant {

279: function claim(uint256 withdrawRequestIndex) external nonReentrant {
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Withdraw/WithdrawQueue.sol#L279

## [L-20] Restrictive Cross-Chain Token Address Validation

The contract uses the `IXERC20Registry` interface to fetch the xerc20 address for a given ERC20 token (`_erc20`). This fetched address is then compared to the `_remoteToken` parameter, which is intended to represent the token's address on the destination chain.

By requiring that these addresses match, the contract assumes that the same token must have the same address on both chains. This assumption does not accommodate scenarios where a token’s address on the destination chain might differ due to reasons like:
- Different deployment transactions or contexts.
- Different governance or administrative procedures on another chain.

This check prevents the use of the bridge for cases where tokens are represented differently across chains. It restricts users only to scenarios where the token deployment has been mirrored exactly across chains, which is not always feasible or desirable.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/Connext/integration/LockboxAdapterBlast.sol

 // If using xERC20, the assumption is that the contract should be deployed at same address
        // on both networks.
        if (xerc20 != _remoteToken) {
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/Connext/integration/LockboxAdapterBlast.sol#L77-L79

## [L-21]  `bridgeTo` function vulnerable to reentrancy attacks

The function bridgeTo involves multiple state changes and external calls without a reentrancy guard:

This exposes the function to potential reentrancy attacks, especially since it interacts with multiple external contracts (the ERC20 token, the lockbox, and the bridge). Even though the SafeERC20 library mitigates some risks, comprehensive reentrancy protection is advisable.

```solidity
FILE: 2024-04-renzo/contracts/Bridge/Connext/integration
/LockboxAdapterBlast.sol

 function bridgeTo(
        address _to,
        address _erc20,
        address _remoteToken,
        uint256 _amount,
        uint32 _minGasLimit,
        bytes calldata _extraData
    ) external {
        // Sanity check
        if (_amount <= 0) {
            revert AmountLessThanZero();
        }

        address xerc20 = IXERC20Registry(registry).getXERC20(_erc20);
        address lockbox = IXERC20Registry(registry).getLockbox(xerc20);

        // Sanity check
        if (xerc20 == address(0) || lockbox == address(0)) {
            revert InvalidAddress();
        }

        // If using xERC20, the assumption is that the contract should be deployed at same address
        // on both networks.
        if (xerc20 != _remoteToken) {
            revert InvalidRemoteToken(_remoteToken);
        }

        SafeERC20.safeTransferFrom(IERC20(_erc20), msg.sender, address(this), _amount);
        SafeERC20.safeApprove(IERC20(_erc20), lockbox, _amount);
        IXERC20Lockbox(lockbox).deposit(_amount);
        SafeERC20.safeApprove(IERC20(xerc20), blastStandardBridge, _amount);
        L1StandardBridge(blastStandardBridge).bridgeERC20To(
            xerc20,
            _remoteToken,
            _to,
            _amount,
            _minGasLimit,
            _extraData
        );
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Bridge/Connext/integration/LockboxAdapterBlast.sol#L56-L95

## [L-22] Immutable Delegate Address Elevates Security Risk

If the delegate address becomes compromised (e.g., the private keys are stolen, or the address is otherwise controlled by a malicious actor), the contract has no built-in mechanism to change this address. This immutability could lead to security vulnerabilities, as the compromised delegate might have significant control or influence over the operations intended for delegation.

```solidity
FILE: 2024-04-renzo/contracts/Delegation/OperatorDelegator.sol

/// @dev Sets the address to delegate tokens to in EigenLayer -- THIS CAN ONLY BE SET ONCE
    function setDelegateAddress(
        address _delegateAddress,
        ISignatureUtils.SignatureWithExpiry memory approverSignatureAndExpiry,
        bytes32 approverSalt
    ) external nonReentrant onlyOperatorDelegatorAdmin {
        if (address(_delegateAddress) == address(0x0)) revert InvalidZeroInput();
        if (address(delegateAddress) != address(0x0)) revert DelegateAddressAlreadySet();

        delegateAddress = _delegateAddress;

        delegationManager.delegateTo(delegateAddress, approverSignatureAndExpiry, approverSalt);

        emit DelegationAddressUpdated(_delegateAddress);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L116-L130

## [L-23] Fund Immobilization Risk Due to Null Strategy Address

The `setTokenStrategy` function in the `OperatorDelegator` contract allows for the strategy of a specific ERC20 token to be set to the zero address, effectively disabling the strategy. This operation does not include checks or mechanisms to handle tokens already deposited under the previously active strategy, nor does it facilitate an easy recovery or reactivation path. This can result in tokens being locked within the contract, with no strategy available for managing or withdrawing these assets.

```solidity
2024-04-renzo/contracts/Delegation/OperatorDelegator.sol

/// @dev Sets the strategy for a given token - setting strategy to 0x0 removes the ability to deposit and withdraw token
    function setTokenStrategy(
        IERC20 _token,
        IStrategy _strategy
    ) external nonReentrant onlyOperatorDelegatorAdmin {
        if (address(_token) == address(0x0)) revert InvalidZeroInput();

        tokenStrategyMapping[_token] = _strategy;
        emit TokenStrategyUpdated(_token, _strategy);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Delegation/OperatorDelegator.sol#L105-L114

## [L-24] Automatic ETH Processing and Fee Deduction Without Sender Verification

The `receive()` function does not differentiate the source of the incoming ETH. Whether the ETH is sent as intended protocol rewards, or mistakenly sent by an external user, it is processed in the same manner. 

**Accidental Deposits:** Users who mistakenly send ETH to the contract address will have their funds automatically processed as rewards, with a portion deducted as fees. Since Ethereum transactions are irreversible, once the ETH is sent and processed, recovering it would depend entirely on the actions of the contract administrators, assuming they can identify the transaction as a mistake and choose to return the funds.

**Unintended Fee Deductions:** In cases of accidental ETH sends, not only is the ETH handled as rewards, but a fee is also deducted and sent to the fee address, further complicating the situation for the unintended sender.

```solidity
FILE: 2024-04-renzo/contracts/Deposits/DepositQueue.sol

 receive() external payable nonReentrant {
        uint256 feeAmount = 0;
        // Take protocol cut of rewards if enabled
        if (feeAddress != address(0x0) && feeBasisPoints > 0) {
            feeAmount = (msg.value * feeBasisPoints) / 10000;
            (bool success, ) = feeAddress.call{ value: feeAmount }("");
            if (!success) revert TransferFailed();

            emit ProtocolFeesPaid(IERC20(address(0x0)), feeAmount, feeAddress);
        }
        // update remaining rewards
        uint256 remainingRewards = msg.value - feeAmount;
        // Check and fill ETH withdraw buffer if required
        _checkAndFillETHWithdrawBuffer(remainingRewards);

        // Add to the total earned
        totalEarned[address(0x0)] = totalEarned[address(0x0)] + remainingRewards;

        // Emit the rewards event
        emit RewardsDeposited(IERC20(address(0x0)), remainingRewards);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Deposits/DepositQueue.sol#L163-L183

## [L-25] Vulnerability to Excessive Gas Cost Refunds Potentially Draining Contract Funds

The potential vulnerability in the `_refundGas` function arises from its method of calculating the gas costs for refunding the administrators of the contract. This calculation uses the formula `gasUsed * tx.gasprice`, where `gasUsed` is the difference between the gas available at the start of the transaction (`initialGas`) and the gas left at the point of calculation (`gasleft()`), and `tx.gasprice` is the gas price set by the user who initiated the transaction.

Imagine an administrator or a malicious user initiates a transaction interacting with the contract, and deliberately sets a very high `tx.gasprice`, much higher than the average network gas price.

Calculation:

Suppose the transaction uses 100,000 gas (`gasUsed`).<br>
The user sets `tx.gasprice` to 1,000 gwei, significantly above normal rates.<br>
The refund amount would be `100,000 * 1,000 gwei = 100,000,000` gwei, or 0.1 ether.

If the `_refundGas` function does not cap the refund amount or if the transaction's gas price is exceptionally high, there's a risk that a large portion of the contract's ETH balance could be used to cover these gas costs. This is particularly concerning if the function is called with high frequency or during periods of high gas prices.

```solidity
FILE: 2024-04-renzo/contracts/Deposits/DepositQueue.sol

 /**
     * @notice Internal function used to refund gas to admin accounts if enough balance
     * @param initialGas Initial Gas available
     */
    function _refundGas(uint256 initialGas) internal {
        uint256 gasUsed = (initialGas - gasleft()) * tx.gasprice;
        uint256 gasRefund = address(this).balance >= gasUsed ? gasUsed : address(this).balance;
        (bool success, ) = payable(msg.sender).call{ value: gasRefund }("");
        if (!success) revert TransferFailed();
        emit GasRefunded(msg.sender, gasRefund);
    }
```

https://github.com/code-423n4/2024-04-renzo/blob/519e518f2d8dec9acf6482b84a181e403070d22d/contracts/Deposits/DepositQueue.sol#L279-L289

***

# [Mitigation Review](#mitigation-review)

## Introduction

Following the C4 audit, the sponsor's related mitigations were reviewed by the following wardens: [Team LessDupes](https://code4rena.com/@LessDupes) ([3docSec](https://code4rena.com/@3docSec), [sin1st3r\_\_](https://code4rena.com/@sin1st3r__), and [EV\_om](https://code4rena.com/@EV_om)), [Team Fassi\_Security](https://code4rena.com/@Fassi_Security) ([bronze\_pickaxe](https://code4rena.com/@bronze_pickaxe), and [mxuse](https://code4rena.com/@mxuse)), [Bauchibred](https://code4rena.com/@Bauchibred), [grearlake](https://code4rena.com/@grearlake), and [0xCiphky](https://code4rena.com/@0xCiphky). Additional details can be found within the [C4 Renzo Mitigation Review repository](https://github.com/code-423n4/2024-06-renzo-mitigation).

## Mitigation Review Scope

### Mitigations of High & Medium Severity Issues

- H-01: Withdrawals can be locked forever if recipient is a contract
- H-02: Incorrect calculation of queued withdrawals can deflate TVL and increase ezETH mint rate
- H-03: ETH withdrawals from EigenLayer always fail due to OperatorDelegator's nonReentrant `receive()`
- H-04: Withdrawals logic allows MEV exploits of TVL changes and zero-slippage zero-fee swaps
- H-07: DOS of `completeQueuedWithdrawal` when ERC20 buffer is filled
- H-08: Incorrect withdraw queue balance in TVL calculation
- M-02: Withdrawals and Claims are meant to be pausable, but it is not possible in practice
- M-09: Deposits will always revert if the amount being deposited is less than the `bufferToFill` value
- M-12: Incorrect exchange rate provided to Balancer pools

### Out of Scope

Any findings that were acknowledged, disputed, or in QA reports from the past audit.

- H-05: Withdrawals of rebasing tokens can lead to insolvency and unfair distribution of protocol reserves
- H-06: The amount of xezETH in circulation will not represent the amount of ezETH tokens 1:1
- M-01: Withdrawals can fail due to deposits reverting in `completeQueuedWithdrawal()`
- M-03: Fixed hearbeat used for price validation is too stale for some tokens
- M-04: Price updating mechanism can break
- M-05: `calculateTVL` may run out of gas for modest number of operators and tokens breaking deposits, withdrawals, and trades
- M-06: `L1::xRenzoBridge` and `L2::xRenzoBridge` uses the `block.timestamp` as dependency, which can cause issue
- M-07: Lack of slippage and deadline during withdraw and deposit
- M-08: Not handling the failure of cross chain messaging
- M-10: Potential Arbitrage Opportunity in the `xRenzoDeposit` L2 contract
- M-11: Fetched price from the oracle is not stored in `xRenzoDeposit`
- M-13: Pending withdrawals prevent safe removal of collateral assets
- M-14: stETH/ETH Feed being used opens up to 2 way `deposit <-> withdrawal` arbitrage

## Mitigation Review Summary

As noted in the table below, the participating wardens confirmed the mitigation of each in-scope vulnerability. Further, no new High severity or Medium severity vulnerabilities were uncovered during their review.

| Original Issue | Status | Full Details |
| --- | --- | --- |
| H-01 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/8), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/50), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/40), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/17), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/2) |
| H-02 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/9), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/51), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/41), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/18), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/3) |
| H-03 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/10), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/56), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/42), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/19), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/4) |
| H-04 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/16), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/58), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/20) |
| H-07 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/11), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/57), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/43), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/22), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/5) |
| H-08 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/12), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/55), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/44), [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/23), and [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/6) |
| M-02 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/13), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/52), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/45), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/30), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/25) |
| M-09 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/14), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/53), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/46), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/31), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/26) |
| M-12 |  🟢 Mitigation Confirmed | Reports from [0xCiphky](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/15), [grearlake](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/54), [Fassi\_Security](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/47), [LessDupes](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/32), and [Bauchibred](https://github.com/code-423n4/2024-06-renzo-mitigation-findings/issues/29) |



***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
