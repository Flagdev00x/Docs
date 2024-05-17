---
description: >-
  Flag native bridge is used to relay the Flag native token between Flag and
  Ethereum networks
---

# Flag: Ethereum ↔ Flag

Flag native bridge between Ethereum and Flag is used to relay the Flag native token from Flag to Ethereum network

## Architecture Overview

The Flag bridged is based on POA's bridge implementation, it is used to transfer Flag tokens between the Flag chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Flag or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Flag tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Flag chain on Ethereum**

Each cycle the total block reward distributed on Flag chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Flag chain, waiting for all bridge validators on Flag chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Flag network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://flagscan.xyz/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0xF631D903d6C31b606Ec527558e441108B6211af3](https://flagscan.xyz/address/0xF631D903d6C31b606Ec527558e441108B6211af3/transactions)

Flag token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Flag you send native Flag token to the home bridge contract. Then you receive an equal amount of the Flag token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Flag token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Flag native token, sent from the home bridge contract.

#### 

