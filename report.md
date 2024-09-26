# **Proof Of Humanity V2 Audit Competition on Hats.finance** 


## Introduction to Hats.finance


Hats.finance builds autonomous security infrastructure for integration with major DeFi protocols to secure users' assets. 
It aims to be the decentralized choice for Web3 security, offering proactive security mechanisms like decentralized audit competitions and bug bounties. 
The protocol facilitates audit competitions to quickly secure smart contracts by having auditors compete, thereby reducing auditing costs and accelerating submissions. 
This aligns with their mission of fostering a robust, secure, and scalable Web3 ecosystem through decentralized security solutions​.

## About Hats Audit Competition


Hats Audit Competitions offer a unique and decentralized approach to enhancing the security of web3 projects. Leveraging the large collective expertise of hundreds of skilled auditors, these competitions foster a proactive bug hunting environment to fortify projects before their launch. Unlike traditional security assessments, Hats Audit Competitions operate on a time-based and results-driven model, ensuring that only successful auditors are rewarded for their contributions. This pay-for-results ethos not only allocates budgets more efficiently by paying exclusively for identified vulnerabilities but also retains funds if no issues are discovered. With a streamlined evaluation process, Hats prioritizes quality over quantity by rewarding the first submitter of a vulnerability, thus eliminating duplicate efforts and attracting top talent in web3 auditing. The process embodies Hats Finance's commitment to reducing fees, maintaining project control, and promoting high-quality security assessments, setting a new standard for decentralized security in the web3 space​​.

## Proof Of Humanity V2 Overview

A Sybil resistant list of humans.       

## Competition Details


- Type: A public audit competition hosted by Proof Of Humanity V2
- Duration: 9 days
- Maximum Reward: $79,973.6
- Submissions: 170
- Total Payout: $53,734.26 distributed among 10 participants.

## Scope of Audit

## Project overview

Proof Of Humanity is a Sybil resistant list of humans.

People can register by having an already registered user to vouch for them, providing a deposit and submitting a video of themself.
There is a challenge period where potential challengers can put a deposit to create a Kleros dispute.
If no dispute is raised or the dispute is won by the submitter, the profile is registered.
If the dispute is won by the challenger, the profile is rejected and the deposit (minus arbitration fees) is given to the challenger.

There is a similar mechanism to remove a profile.

It is possible to transfer a profile from one platform (Ethereum/Gnosis) to another.
Note that if there is already a profile with the same id, the transferred profile will be lost (this should not happen due to challengers challenging duplicates even through different platforms).

## Attack goals
Contrary to most contracts, the main security risk related to Proof Of Humanity is not about money getting stolen (there are deposits but those are very small), but about someone managing to create multiple profiles (Sybil attack) or to takeover someone else's Humanity Id.

As a hacker, your goals are in this order:
- Find a way to immediately create an arbitrary number of registered profiles.
- Find a way to takeover someone else's Humanity Id.
- Be able to, across time, create multiple profiles illegally.
- Be able to steal user (submitters/challengers/appellants) deposits.



## Audit competition scope


```
|-- proof-of-humanity-v2-contracts/contracts/
     |-- README.md
     |-- ProofOfHumanity.sol
     |-- CrossChainProofOfHumanity.sol
     |-- bridge-gateways
          |-- AMBBridgeGateway.sol
     |-- extending-old
           |-- ForkModule.sol
           |-- ProofOfHumanityExtended.sol
```

## Deployments

Deployed contracts on mainnets (Ethereum and Gnosis)
You can interact with Proof Of Humanity V2 (Origin) with this [frontend](https://v2.proofofhumanity.id/).
Testing attacks on the deployed contracts is permissible before the end of the competition (if bugs are found out we'll redeploy).

### Ethereum

POH: [0x87c5c294C9d0ACa6b9b2835A99FE0c9A444Aacc1](https://etherscan.io/address/0xe8707564d16967e4572d4f02aea404d3118302b2805e6c445f415e0acfe5dbb2)
POH_Implementation: [0xF921b42B541bc53a07067B65207F879c9377bf7F](https://etherscan.io/address/0xF921b42B541bc53a07067B65207F879c9377bf7F)
CROSS_CHAIN: [0xD8D462ac9F3FAD77Af2ae2640fE7F591F1651A2C](https://etherscan.io/address/0xD8D462ac9F3FAD77Af2ae2640fE7F591F1651A2C)
CC_Implementation: [0x064B1132D9A9c43Df269FeAD9e80c195Fb9cd916](https://etherscan.io/address/0x064B1132D9A9c43Df269FeAD9e80c195Fb9cd916)
GATEWAY: [0x290e997D7c46BDFf666Ad38506fcFB3082180DF9](https://etherscan.io/address/0x290e997D7c46BDFf666Ad38506fcFB3082180DF9)
LEGACY: [0xC5E9dDebb09Cd64DfaCab4011A0D5cEDaf7c9BDb (PoH v1)](https://etherscan.io/address/0xC5E9dDebb09Cd64DfaCab4011A0D5cEDaf7c9BDb)
PROXY_ADMIN: [0xf57B69f71DD7499Ca30242390E655e8A6a93b51b](https://etherscan.io/address/0xf57B69f71DD7499Ca30242390E655e8A6a93b51b)
PROXY_ADMIN_CC: [0xec729b0eCf7972236e8926DA4feAAF9BC8F55e65](https://etherscan.io/address/0xec729b0eCf7972236e8926DA4feAAF9BC8F55e65)
FORK_MODULE: [0x116cB4077afbb9B5c7E0dCd5fc4Ce943Ab624dbF](https://etherscan.io/address/0x116cB4077afbb9B5c7E0dCd5fc4Ce943Ab624dbF)

### Gnosis

POH: [0xECd1823b3087acEE3C77928b1959c08d31A8F20e](https://gnosisscan.io/address/0xECd1823b3087acEE3C77928b1959c08d31A8F20e)
POH_Implementation: [0x5efa99c7b0cc04893b2c5551437ff82b19e661c7](https://gnosisscan.io/address/0x5efa99c7b0cc04893b2c5551437ff82b19e661c7)
CROSS_CHAIN: [0xF921b42B541bc53a07067B65207F879c9377bf7F](https://gnosisscan.io/address/0xF921b42B541bc53a07067B65207F879c9377bf7F)
CC_Implementation: [0xc664a8d43601109fc50f3bcf22f29e9119ab2f6d](0xc664a8d43601109fc50f3bcf22f29e9119ab2f6d)
GATEWAY: [0xD8D462ac9F3FAD77Af2ae2640fE7F591F1651A2C](https://gnosisscan.io/address/0xD8D462ac9F3FAD77Af2ae2640fE7F591F1651A2C)
PROXY_ADMIN: [0x60BC555eb5a40b7f934A7345aFA3596Ddd388b2B](https://gnosisscan.io/address/0x60BC555eb5a40b7f934A7345aFA3596Ddd388b2B)
PROXY_ADMIN_CC: [0x36dfBA40eD6DC28f26163548466170b39BE2916D](https://gnosisscan.io/address/0x36dfBA40eD6DC28f26163548466170b39BE2916D)




## Medium severity issues


- **Loophole Allows V1 Users to Bypass Vouching and Appeals When Switching Chains**

  V1 users can sidestep the vouching, challenge, and appeal processes by transferring their humanity to another chain via the `CrossChainProofOfHumanity::transferHumanity` function. This function bypasses the typical steps required for claiming or renewing humanity in the `ProofOfHumanityExtended` contract. Users can switch chains without creating a V2 profile, exploiting default values that allow circumvention of penalties for pending requests, revocations, or malicious vouching. This loophole arises from the incorrect use of the `accountHumanity[_account]` variable, leading to the execution of incomplete data checks. To address this, it's proposed to use the `humanityId` directly and prevent V1 users from switching chains without first creating a V2 profile. The issue has been fixed in a recent code update.


  **Link**: [Issue #134](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/134)


- **Vulnerability allows simultaneous holding of Humanity IDs on multiple chains**

  A vulnerability was identified where a V1 user, after renewing their Humanity ID, can hold the same Humanity ID on both V1 and V2 contracts. This leads to potential issues like the creation of illegitimate Humanity IDs across multiple chains and difficulties in revoking these IDs. Specifically, the process involves calling `ProofOfHumanityExtented::renewHumanity` to extend the ID's expiration in V2, followed by `transferHumanity`, which retains their Humanity ID in both V1 and V2. This enables users to potentially hold Humanity IDs on multiple chains simultaneously. A suggested mitigation involves deleting a user's V1 Humanity ID upon claiming identity in V2. A similar fix has been implemented to address this flaw.


  **Link**: [Issue #126](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/126)


- **Underflow in processVouches Prevents Penalty Application to Malicious Users**

  A critical issue was identified where the `processVouches` function can be disrupted, causing a denial of service (DoS) that affects the `executeRequest` function. The problem occurs if a penalty needs to be applied to a voucher in the `processVouches` function. Specifically, the code subtracts 1 from `voucherHumanity.requestCount[voucherHumanity.owner]`. If `requestCount` for the underlying user is zero, this subtraction will cause the function to revert. This prevents `processVouches` from being executed and, subsequently, the `executeRequest` cannot be performed. This leads to situations where penalties are not applied to users who vouched for malicious requests and causes issues for future users who claim the underlying humanity.


  **Link**: [Issue #114](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/114)


- **Malicious User Can Block Humanity Claims During Vouching State by Funding Requests with Zero Value**

  A vulnerability exists that allows a malicious user to cause a denial-of-service (DoS) on the "claim humanity" process during the vouching state. This is achieved by abusing the `fundRequest` function. The function enables users to fund a request, but a fully funded request can be disrupted if a user calls this function with zero message value. This action sets `round.sideFunded` to `Party.None`, preventing the `advanceState` function from working due to an unmet requirement (`request.challenges[0].rounds[0].sideFunded` being `Party.Requester`). The described scenario can be countered by funding the request with zero value again to reset the status, but this could lead to systematic disruption unless mitigated. A suggested fix has been provided to address this issue.


  **Link**: [Issue #99](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/99)

## Low severity issues


- **Improper Arbitrator Parameter Initialization Causes ProofOfHumanity to Use Wrong Subcourt**

  The Kleros contract is intended to use specific subcourts for different purposes, with court ID 23 meant for ProofOfHumanity disputes. Due to improper initialization of the `_arbitratorExtraData` parameter in the `ProofOfHumanityExtended` contract, the system defaults to subcourt ID 0, potentially misdirecting disputes to the wrong court.


  **Link**: [Issue #149](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/149)


- **Cooldown Period in CrossChainProofOfHumanity Contract is Too Short for Security**

  The `CrossChainProofOfHumanity` contract's cooldown period is currently set to 7 seconds, which is too brief for secure cross-chain operations. This short cooldown can be exploited for rapid transfers, evasion of revocation attempts, and denial of service attacks. It's recommended to increase the period to 1 day for better protection.


  **Link**: [Issue #130](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/130)


- **Exploit allows V1 profiles to bypass penalties by transferring while vouching**

  A vulnerability allows a V1 profile to exploit the system by transferring their humanity to a new chain while vouching on the `ProofOfHumanityExtended` contract. This bypasses the penalty of not renewing their humanity on POHv2. Mitigation involves adding a check for the `vouching` status in the `ccDischargeHumanity` function.


  **Link**: [Issue #129](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/129)


- **Fix needed in executeRequest to handle expired revocation requests properly**

  In the `executeRequest` function of the `ProofOfHumanityExtended` contract, if a revocation request is processed after the user's humanity expiration, the user's humanity is not deleted, and the `pendingRevocation` variable is not set to `false`. This oversight can make a user's profile immune to future revocations after re-entering the registry. The solution involves setting `pendingRevocation` to `false` regardless of whether the humanity has expired.


  **Link**: [Issue #119](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/119)


- **Adjust `renewHumanity` renewal period to 30 days in `ProofOfHumanity` contract**

  In the `ProofOfHumanity` contract, the `renewHumanity` function allows users to renew their registration approximately 11 months before expiry instead of the intended 1 month. This discrepancy is due to an incorrect configuration of the `renewalPeriodDuration` parameter. The recommendation is to change this parameter to 2592000 seconds (30 days).


  **Link**: [Issue #72](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/72)


- **Inconsistent Expiration Time Check in isClaimed, isHuman, and boundTo Functions**

  There's an inconsistency in how a contract checks the expiration time of a humanity across different functions. The `isClaimed` and `boundTo` functions use `>=`, while the `isHuman` function uses `>`. This discrepancy can lead to an off-by-one error, potentially causing unexpected behavior and vulnerabilities. A centralized validation function is recommended.


  **Link**: [Issue #29](https://github.com/hats-finance/Proof-Of-Humanity-V2-0xef0709445d394a22704850c772a28a863bb780b0/issues/29)



## Conclusion

The Hats.finance audit competition for Proof Of Humanity V2, which lasted nine days, attracted 170 submissions and awarded $53,734.26 to 10 participants, with the competition bringing significant improvements to the platform's security. Proof Of Humanity offers a Sybil-resistant list of humans by requiring registration through vouching, deposits, and video submissions, and allowing profile transfers across platforms. The audit revealed medium to low-severity issues regarding profile handling and user identification. Notable medium severity issues included loopholes enabling users to bypass vouching and penalties when switching chains, holding Humanity IDs on multiple chains, and denial of service attacks via zero-value funding requests. Low severity issues involved improper arbitrator parameter initialization, inadequate cooldown periods for cross-chain operations, and inconsistent expiration checks. Fixes have been applied or recommended, and as a whole, the report underscored the effectiveness of Hats.finance's decentralized security strategies in enhancing the robustness of Proof Of Humanity V2.

## Disclaimer


This report does not assert that the audited contracts are completely secure. Continuous review and comprehensive testing are advised before deploying critical smart contracts.


The Proof Of Humanity V2 audit competition illustrates the collaborative effort in identifying and rectifying potential vulnerabilities, enhancing the overall security and functionality of the platform.


Hats.finance does not provide any guarantee or warranty regarding the security of this project. Smart contract software should be used at the sole risk and responsibility of users.

