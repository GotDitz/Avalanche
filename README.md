# Building-on-Avalanche-ETH-AVAX
Overview

The DegenToken smart contract empowers gaming platforms to oversee a personalized ERC20 token, providing features for creating, transferring, exchanging, eliminating, and verifying balances. It incorporates a system allowing players to exchange their tokens for in-game items at predetermined prices. Security measures are in place by limiting specific actions to the contract owner. Tailored for use on the Avalanche network, it capitalizes on its compatibility with Ethereum smart contracts and cost-efficient transaction fees. It's important to have the requisite development environment configured to engage with the Avalanche network.

## Requirements
* Solidity version 0.8.20
* OpenZeppelin contracts for ERC20 and Ownable functionalities
* Avalanche-compatible development tools (e.g., Avalanche C-Chain, Remix, Truffle, Hardhat)
* MetaMask or other web3 wallets configured for the Avalanche network


## Usage
Minting New Tokens
* Tokens can only be created by the contract owner. Gamers can be rewarded with this in-game.

Transferring Tokens
* With the transferDGN feature, players can give tokens to other players.

Redeeming Tokens
* Tokens can be exchanged for goods in the in-game store by players. Every item has a set price.

Burning Tokens
* Tokens that a player no longer needs can be burned.

Checking Token Balance
* Token balance checks are available to players at all times.

Viewing Shop Items
* Gamers may see the things in the shop that can be redeemed..

## Deployment
* Set up your Avalanche network configuration in your development environment.
* Create the contract with your tool of choice (Hardhat, Remix, etc.).
* Give the Avalanche C-Chain access to the contract.
* Verify the contract on a block explorer (e.g., SnowTrace).

## Authors
Sean Ydnar A. Abellanosa

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
