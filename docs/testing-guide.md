# Testing Guide

At Protekt we want to invite *every* user, from completely new to DeFi to an experienced developer to test our platform. 

We're building Protekt for you, so today we're inviting you to test it. 🙌

We've put together a short guide covering everything needed, if there are any questions feel free to get in touch on our [telegram](https://t.me/protektdefi) 🚀

We invite you to read our [View Docs](./protektContracts.md) to learn more about how the protocol works.

We would love you feedback and have attached a [feedback form](https://forms.gle/Z8mEvG8RhytJJN3E7) to be filled out after testing ❤️.

## Setting up a decentralised wallet

To access decentralised applications, you will need a decentralised wallet. Our favourite is [MetaMask](https://metamask.io/).

For a quick guide on how to setup a MetaMask wallet take a look [here](https://www.youtube.com/watch?v=yWfZnjkhhhg&t=459s)

After setting up a wallet, you will need to change the network to the Kovan test network.

![Kovan Meta Mask](../img/kovan-meta-mask.png)


## Adding token addresses to your wallet
To add tokens to your address, scroll down to the bottom of your MetaMask wallet and click add Token.

From here, if you are on Kovan, enter the address and the rest of the values will be autofilled.

![Add Token](../img/add-token.png)

- weth address: 0xd0A1E359811322d97991E03f863a0C30C2cF029C
- dai address: 0x4F96Fe3b7A6Cf9725f59d353F723c1bDb64CA6Aa
- cDai address: 0xf0d0eb522cfa50b716b3b1604c4f0fa6f04376ad
- pcDai: 0x0584815FA77F397e79E31E7663FE0543d03a5EDD
- shpcDai: 0x7aD9d1Cd1a392f53Bb8F91A085e20A3c37BEc0e7


## Getting the test tokens
First you need to get some kovan ether (ETH). Ether is used for gas for the transactions and we'll use it to get Dai and Weth.

To get Kovan ether use one of the following faucets:
* [faucet](https://faucet.kovan.network/)
* [glitter faucet](https://gitter.im/kovan-testnet/faucet) *recommended


Next you will need to acquire some kovan Weth (wrapped-ether). To wrap ether, we simply send ether to the weth address.

![Getting WETH](../img/getting-weth.png)

Ensure you set a non 0 value to transfer, and click confirm.

After the transaction has been confirmed, if you added the weth address to your tokens it should now display a value.


Next you will need to acquire some kovan Dai . To do this, we can take a loan out on compound, by depositing some ETH and using it as collateral for the Dai.

First navigate to [Compound](https://app.compound.finance/) and ensure you are on the Kovan network in MetaMask.

Next click on Ether on the left side of the page under supply.

![Compound Supply](../img/compound-supply.png)

Deposit some amount of Ether which we will use as collateral to borrow Dai.

Next we will borrow some Dai using the ether as collateral.

![Compound Borrow](../img/compound-borrow.png)

Congratulations! You have all the tokens you need to test protekt.

## Testing the Contracts

Now you should have all the tokens you need to test Protekt! 🚀

Protekt allows users who want to access protocols like compound and earn yield, insurance on their tokens in the pools if any bugs or hacks were to happen. 

When you deposit Dai in the staking side of protekt, it will be automatically deposited into compound. 

Compound then mints you cDai (compound Dai). Instead of giving you back cDai, we then give you pcDai. (protekted compound Dai). A small fee is taken from the interest earned to pay the insurers of the pooled token. 

Navigate to the Earn Safe Yield tab of [protekt](http://kovan.protekt.finance/earn-yield) to try this!

For users who want to earn yield by shielding pools, we offer a method to stake to shield mine. This is done by depositing weth and in return you recieve a shpcDAI (shield protekt cDai) token that earns returns.

Navigate to the Stake to Shield Mine tab of [protekt](http://kovan.protekt.finance/staking) to try this!

We would love you feedback and have attached a [feedback form](https://forms.gle/Z8mEvG8RhytJJN3E7) for you ❤️.


