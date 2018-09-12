# Health Nexus :: DRS
[![Hex.pm](https://img.shields.io/hexpm/l/plug.svg?style=flat-square)](https://github.com/Health-Nexus/drs/blob/master/LICENSE)
<img align="right" src="./assets/HN_token_transparent.png?raw=true" height="348">

An Ethereum smart-contract for creating a decentralized record service using the EIP 20 token Health Cash (HLTH). This is project is part of phase one of Health Nexus, the public permissioned blockchain for healthcare.<br>

Features:

* Create services by registering service urls
* Create and issue keys for services
* Permission keys for sharing, selling, and trading
* Share keys & services with multiple accounts
* Sell keys for Health Cash (HLTH)
* Trade keys

<details>
<summary><strong>Table of Contents</strong> (click to expand)</summary>

* [Overview](#overview)
* [Installation](#installation)
* [Testing](#️testing)
* [Notes](#notes)
* [Usage](#usage)
* [Credits](#️credits)
* [License](#license)
</details>

## Overview

This smart-contract enables the registration of data services bound to unique endpoint urls. Registering a service creates an immutable record of that service and associated owner. Service owners can then create and issue keys for that service.

Keys are unique ownable records that can be used to verify the identity of valid service consumers though a process that requires authenticating messages signed by the key owner. Service owners can permission keys extending the functionality to enable trading, sharing, and the selling of keys using Health Cash (HLTH).


## Installation

To clone and use this smart contract, you'll need [Git](https://git-scm.com) and [Node.js](https://nodejs.org/en/download/) (which comes with [npm](http://npmjs.com)), [Truffle](http://truffleframework.com/), and a local development Ethereum node on your computer ([Geth](https://github.com/ethereum/go-ethereum), [Parity](https://github.com/paritytech/parity)).

From your command line:

```bash
# Clone this repository
$ git clone https://github.com/Health-Nexus/drs.git

# Go into the repository
$ cd drs

# Install dependencies
$ npm install

# Compile contracts
$ truffle compile

# Deploy contracts
$ truffle migrate
```
## Replace Health Token
Health Token is required for migration of the compiled contracts. For development: Install Health-Nexus/healthcashtoken by following the steps of installation, note a string labeled "healthcashtoken" which can be found in the output obtained after installing the same.

Replace the existing token on line no.2 in 'migrations/2_deploy_contracts.js'with the one obtained from above.

## Testing

Running the the test suite requires your dev node have two unlocked accounts provisioned with sufficient ether to pay the transaction costs. About TestRPC, the tests were not written for TestRPC which handles contract throws differently than geth or parity. This is a known [issue](https://github.com/ethereumjs/testrpc/issues/39).

From your command line:

```bash
# Run Test Suite
$ truffle test
```

## Notes

This repository holds the code for the smart-contract portion of a three-part system consisting of:

* A smart-contract for maintaining decentralized records of trusted entities via issuable keys and auditable access logs.
* Decentralized application that uses this smart-contract for issuing and managing keys and storing related service data for those keys.
* An off-chain service that runs concurrently with an Ethereum node that uses signed transactions and keys to verify and route requests and log data access.

Health DRS is developed with the functionality to support many different dapp/services as most of the key functionality is permissioned. For example, selling, trading, and sharing of keys are all permissioned and left off by default allowing for a simple single-issuer application. In addition allowing the service to set arbitrary key data for each key enables the dapp to extend the provided functionality however needed.

For example, one could create keys with limited uses, or that expired at a specific time, or that required two-factor authentication.

## Usage

For an overview of the smart-contract's functionality review the [wiki](https://github.com/Health-Nexus/drs/wiki).
On day one, users will be able to access this programmatically or through the Mist Ethereum wallet.  An open source server client and UI are also in the works.

## Audit

This smart contract has been audited by Hosho Group.

"We​ ​ are​ ​ grateful​ ​ to​ ​ have​ ​ been​ ​ given​ ​ the​ ​ opportunity​ ​ to​ ​ work​ ​ with​ ​ the​ ​ SimplyVitalHealth​ ​ team​ ​ on
this​ ​ project​ ​ and​ ​ audit.​ ​ They​ ​ have​ ​ been​ ​ very​ ​ receptive​ ​ to​ ​ our​ ​ feedback​ ​ and​ ​ were​ ​ agreeable​ ​ in
correcting​ ​ the​ ​ small​ ​ numbers​ ​ of​ ​ issues​ ​ found.

During​ ​ the​ ​ initial​ ​ static​ ​ analysis,​ ​ several​ ​ possible​ ​ vulnerabilities​ ​ were​ ​ noted,​ ​ and​ ​ the​ ​ SVH​ ​ team
was​ ​ very​ ​ quick​ ​ to​ ​ patch​ ​ these​ ​ and​ ​ return​ ​ the​ ​ updated​ ​ code.​ ​ They​ ​ implemented​ ​ the​ ​ required​ ​ fixes
to​ ​ ensure​ ​ the​ ​ long-term​ ​ health​ ​ and​ ​ stability​ ​ of​ ​ the​ ​ HealthDRS​ ​ system​ ​ as​ ​ it​ ​ works​ ​ within​ ​ the
Ethereum​ ​ ecosystem.​ ​ It​ ​ was​ ​ also​ ​ noted​ ​ that​ ​ there​ ​ were​ ​ some​ ​ code​ ​ paths​ ​ that​ ​ were​ ​ not​ ​ executable
during​ ​ dynamic​ ​ testing​ ​ and​ ​ the​ ​ SVH​ ​ team​ ​ corrected​ ​ these​ ​ to​ ​ a ​ ​ functional​ ​ state.

Even​ ​ beyond​ ​ the​ ​ small​ ​ issues​ ​ found,​ ​ the​ ​ SVH​ ​ team​ ​ implemented​ ​ some​ ​ of​ ​ our​ ​ suggested
improvements.​ ​ We​ ​ wish​ ​ the​ ​ SVH​ ​ team​ ​ well​ ​ with​ ​ the​ ​ HealthDRS​ ​ system​ ​ going​ ​ forwards."

Yo Sub Kwon, Founder Hosho Group

Read the [complete audit report](https://github.com/Health-Nexus/drs/blob/master/SimplyVitalHealthContractAudit.pdf). 
Read the [updated audit report](https://github.com/Health-Nexus/drs/blob/master/SimplyVitalHealthContractAuditUpdatedVersion.pdf). 


## Credits

Major dependencies:

* [Truffle](https://github.com/trufflesuite/truffle)

Contributors:

* **Lucas Hendren** - [lhendre](https://github.com/lhendre)
* **David Akers** - [davidmichaelakers](https://github.com/davidmichaelakers)

## License

[Apache License 2.0](https://github.com/Health-Nexus/drs/blob/master/LICENSE)

