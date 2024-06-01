# Degen Token Contract

## Overview

The Degen Token Contract is an implementation of the ERC20 token standard with additional functionalities to manage a store of items that users can redeem or purchase using the Degen (DGN) tokens. The contract leverages OpenZeppelin's ERC20 and Ownable contracts for standard token functionalities and access control.

## Features

- **ERC20 Token**: Provides all standard functionalities of an ERC20 token, including minting, burning, and transferring tokens.
- **Ownable**: Restricts certain functions to the contract owner, enhancing security and control.
- **Store Management**: Allows the contract owner to add items to a store. Users can redeem or purchase these items using DGN tokens.
- **Events**: Emits events to log item redemptions and purchases for transparency and tracking.

## Contract Details

### Inherited Contracts

- **ERC20**: Implements the ERC20 token standard, allowing for the creation, transfer, and management of tokens.
- **Ownable**: Provides ownership functionality, restricting access to certain functions to only the contract owner.

### State Variables

- **storeItems**: A mapping that associates unique item IDs with `StoreItem` structs, which contain details such as the item’s ID, name, and price.
- **playerItems**: A mapping that tracks redeemed items for each player, associating player addresses with arrays of item IDs.
- **nextItemId**: A counter used to assign unique IDs to new store items.

### Events

- **ItemRedeemed**: Emitted when a player redeems an item from the store. Logs the player's address, item ID, item name, and item price.
- **ItemPurchased**: Emitted when a player purchases an item from the store. Logs the player's address, item ID, item name, and item price.

### Constructor

The constructor initializes the token with the name "Degen" and the symbol "DGN", mints an initial supply of 1,000,000 DGN tokens to the contract deployer, and adds initial items to the store.

### Functions

- **addItemToStore**: Allows the owner to add a new item to the store by specifying the item's name and price.
- **mint**: Allows the owner to mint new DGN tokens to a specified address.
- **transfer**: Enables the transfer of DGN tokens to another address.
- **redeem**: Allows users to redeem an item from the store by burning the required amount of DGN tokens from their balance.
- **buyItemFromStore**: Allows users to purchase an item from the store by transferring the required amount of DGN tokens to the owner's balance.
- **burn**: Allows users to burn a specified amount of DGN tokens from their balance.
- **balanceOf**: Returns the balance of DGN tokens for a specified address.
- **getPlayerItems**: Returns a list of item IDs that a specific player has redeemed.

## Usage

### Deploying the Contract

1. Deploy the contract with the initial owner's address as a parameter.
2. The contract mints an initial supply of 1,000,000 DGN tokens to the deployer's address.
3. Initial items are added to the store automatically upon deployment.

### Interacting with the Contract

1. **Minting Tokens**: Only the contract owner can mint new tokens to a specified address.
2. **Adding Store Items**: The contract owner can add new items to the store by specifying their names and prices.
3. **Redeeming Items**: Users can redeem store items by burning the corresponding amount of DGN tokens from their balance.
4. **Purchasing Items**: Users can purchase store items by transferring the corresponding amount of DGN tokens to the owner's balance.

## Author

Sean Ydnar A. Abellanosa

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
