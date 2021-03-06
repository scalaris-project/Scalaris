Scalaris
=====================================

https://scalaris.info

Welcome to the Scalaris repository. This repo is for the Scalaris Protocol, a 2nd layer blockchain interoperability protocol that enables communication, interaction, and exchange between different blockchains. This allows for the development of multi-chain applications and blockchain microservices, creating exponentially more capabilities and possibilities for the blockchain ecosystem.

[Contributors are welcome!](https://github.com/scalaris-project/scalaris/blob/master/CONTRIBUTING.md)

[Website](https://scalaris.info) | [API](https://api.scalaris.info) | [Documentation](https://docs.scalaris.info) | [Discord](https://discord.gg/HKbdGANbZA) | [Telegram](https://t.me/scalaris_project)
-------------|-------------|-------------|-------------

Scalaris
-------

Started in 2021, [Scalaris](https://docs.scalaris.info/project/introduction) is a decentralized, community-governed, self-funded, open-source project that serves as a connector between different blockchains, markets, and communities. 

The Scalaris Protocol
-------

Bassed  at the [Blocknet Protocol](https://github.com/blocknetdx) enables decentralized communication and exchange between different blockchains in a permissionless and trustless manner through the use of the TCP/IP networking layer for communication, P2P atomic swaps using BIP65 for exchange, and a DHT overlay network ([Service Nodes](https://docs.scalaris.info/service-nodes/introduction)) to host the full nodes of compatible blockchains, host microservices, audit interactions, and perform anti-spam and anti-DOS measures for the network. 

Scalaris DX
-------

[Scalaris DX](https://docs.scalaris.info/scalarisdx/introduction) is a completely decentralized and trustless exchange built on the Blocknet Protocol that mimics a centralized exchange experience and enables traders to conduct exchanges directly from the wallets of the coins being traded. View Repo: [https://github.com/scalaris-project/scalaris-dx]

Scalaris Specifications:
-------

| Scalaris Detail          |                    |
------------------------|--------------------
Creation Date           | March 5th, 2021
Release Method          | ITO, AirDrops , PoW at start.
Proof Type              | Proof of Work (PoW): blocks 0-5000, Proof of Stake (PoS): blocks 5001+
Algo                    | Quark
Block Time              | 60 seconds
Block Reward / Fees     | 1.0 BLOCK awarded to stakers <br>0.01 BLOCK awarded to Service Nodes on DX trades <br>XRouter fees awarded to Service Nodes (customizable)
Superblock              | Up to 30,000 BLOCK
Difficulty              | Adjusted per block
Staking Requirement     | No minimum ( but realy you most have at least 1 SCA , more = better)
Service Node Requirement| 2500 SCA (SPV)
Service Node Reward     | xBridge fixed 0.01 SCA (Taker side) , for xRoute and xCloud can be configurated or even use 0 fee at all.
Deffault P2P Port	    | 42500
Deffault RPC Port	    | 42510
P2SH Prefix	            | S ( 63 )
SCRIPT Prefix	        | A ( 23 )
SuperBlock Period	    | Every 42000 blocks.
Maturity Time	        | 100 +1 blocks.
Stack Min Age	        | 3600
Vote Require Min Ammount| 2500 SCA + 1 extra fee by separate input's.
Circulation             | [View on explorer](https://explorer.scalaris.info/)
Max Supply              | No maximum supply (PoS), but there is a maximum to [inflation](https://docs.scalaris.info/blockchain/introduction/#inflation)


Decentralized Atomic Swap Algo Summary
-------

```Step1.
Initiator creates secret X, and hashes it to create H(X). Initiator also creates public private key pair (pubkey i1,i2 / privkey i2,i2). Responder creates public private key pair (pubkey r1,r2 / privkey r1,r2).

Step 2.
Initiator shares H(X) and pubkey i2 with responder. Responder shares pubkey r1 with intiator.

Step 3.
Initiator creates TxAb. TxAb can be redeemed after time T2 with privkey i1. At any time TxAb can redeemed with signature from privkey r1 and reveal of secret X. Initiator broadcasts TxAb onto the network.

Step 4.
Responder confirms TxAb. Responder creates TxBb. TxBb can be redeemed after T1 time with privkey r2. At any time TxBb can be redeemed with signature fom privkey i2 and reveal of secret X. Responder broadcasts TxBb onto the network.

Step 5.
Initiator creates TxBp which spends TxBb using privkey i2 and secret X. With the revealed secret, responder can create TxAp which spends TxAb with privkey r1 and secret X.
```

License
-------

Scalaris is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

The MIT License (MIT)

Copyright (c) 2020-2021 The Scalaris Developers

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

Development Process
-------------------

The `master` branch is stable and will match the latest release. Development 
branches are indicated by the version number and may or may not be stable.
[Tags](https://github.com/scalaris-project/scalaris/tags) are created
regularly to indicate new official, stable release versions of Scalaris.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md)
and useful hints for developers can be found in [doc/developer-notes.md](doc/developer-notes.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and macOS, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.
