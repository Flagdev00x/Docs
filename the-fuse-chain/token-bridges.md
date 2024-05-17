# Token Bridges

We have two bridges as explained below

1. Flag Bridge:  ****The bridge, based on POA's bridge implementation, is used to transfer Flag tokens between the Flag chain and the Ethereum network.
2. FLG20 token bridge: This bridge is used to transfer FLG20 tokens into Flag chain and back. Please not that Flag bridge is not supposed to be used to transfer  . 

The bridge, based on POA's bridge implementation, is used to transfer Flag tokens between the Flag chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Flag or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender.

The validators of the bridge on both network are the Flag chain validators. This means that validators, as part of their governance responsibilities, also need to validate bridge transactions and therefore hold Flag tokens to "approve" bridge transactions on Flag chain and hold ETH to "approve" transactions on Ethereum.

Each bridge transaction must be approved by a majority \(over 50%\) of the validators in order to be processed successfully.

The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Flag tokens between the two networks, the bridge is also responsible for network core functionality events:

**Mint block reward distributed on the Flag chain on Ethereum**

Each cycle the total block reward distributed on Flag chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Flag chain, waiting for all bridge validators on Flag chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

**Update Flag chain validators on Ethereum**

Each cycle the Flag chain validators are selected from a random snapshot of pending validators.

Those validators, being also the bridge validators, need to be updated on Ethereum as well.

This works by listening to the \`InitiateChange\` event emitted by the Consensus contract on Flag chain, waiting for all bridge validators on Flag chain to sign it, and eventually sending a transaction to set the bridge validators on Ethereum \(by the last signing validator\).

{% hint style="info" %}
Flag chain bridge - [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://flagscan.xyz/address/0xd617774b9708f79187dc7f03d3bdce0a623f6988)

Ethereum bridge - [0xF631D903d6C31b606Ec527558e441108B6211af3](https://etherscan.io/address/0xF631D903d6C31b606Ec527558e441108B6211af3)

Flag token on Ethereum - [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d)
{% endhint %}

**Using the bridge**

**Transfering from Ethereum mainnet to Fusenet** - Send your erc20 Flag tokens to the Ethereum bridge for them to be released from the Flag chain bridge and be avaliable in your native Flag wallet.

**Transfering from Fusenet to Ethereum mainnet** - Send your Native Flag tokens to the Flag chain bridge for them to be released from the mainnet bridge and be avaliable in your Mainnet wallet. 

