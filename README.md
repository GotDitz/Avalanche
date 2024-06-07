# Degen Smart Contract

The `Degen` smart contract is an ERC20 token with additional functionality for a virtual store. Players can redeem items from the store using Degen tokens (DGN). The contract includes mechanisms to ensure items can only be redeemed once per player and enforces a cooldown period between redemptions.

## Table of Contents
- [Contract Overview](#contract-overview)
- [Key Components](#key-components)
  - [Structs](#structs)
  - [State Variables](#state-variables)
  - [Events](#events)
- [Constructor](#constructor)
- [Functions](#functions)
  - [Store Management](#store-management)
  - [Token Management](#token-management)
  - [Redemption and Purchase](#redemption-and-purchase)
  - [Utility](#utility)
- [Deployment](#deployment)
- [Usage](#usage)

## Contract Overview

The `Degen` contract allows for the creation, transfer, and burning of Degen tokens (DGN), as well as the redemption and purchase of items from a virtual store.

## Key Components

### Structs

- **StoreItem**: Represents an item in the store, containing:
  - `itemId`: Unique ID for the item.
  - `name`: Name of the item.
  - `price`: Price of the item in DGN tokens.

### State Variables

- **storeItems**: A mapping of item IDs to `StoreItem` structs, representing the store’s inventory.
- **playerItems**: A mapping of player addresses to arrays of redeemed item IDs, tracking items redeemed by each player.
- **hasRedeemedItem**: A mapping of player addresses to another mapping of item IDs to booleans, indicating if a player has already redeemed a specific item.
- **lastRedemptionTime**: A mapping of player addresses to timestamps, tracking the last time a player redeemed an item.
- **nextItemId**: A counter for generating unique item IDs.
- **cooldownPeriod**: The time period a player must wait before redeeming another item (default is 1 day).

### Events

- **ItemRedeemed**: Emitted when a player successfully redeems an item.
- **ItemPurchased**: Emitted when a player purchases an item from the store.

## Constructor

### `Degen(address initialOwner)`

- Initializes the contract by minting tokens to the initial owner.
- Adds predefined items to the store.

## Functions

### Store Management

- **`addItemToStore(string memory name, uint256 price)`**: Adds a new item to the store. Only the contract owner can call this function.

### Token Management

- **`mint(address to, uint256 amount)`**: Mints new tokens to a specified address. Only the contract owner can call this function.
- **`transfer(address to, uint256 amount)`**: Overrides the ERC20 `transfer` function to enable token transfers.
- **`burn(uint256 amount)`**: Burns a specified amount of tokens from the caller's balance.

### Redemption and Purchase

- **`redeem(uint256 itemId)`**: Allows players to redeem items using their DGN tokens, with the following checks:
  - The item ID must be valid.
  - The player must have enough tokens to redeem the item.
  - The item must not have been redeemed by the player before.
  - The cooldown period since the last redemption must have passed.
  
  On successful redemption, the function:
  - Burns the tokens equivalent to the item price.
  - Records the redemption.
  - Updates the last redemption time.
  - Emits an `ItemRedeemed` event.

- **`buyItemFromStore(uint256 itemId)`**: Allows players to purchase items by transferring the item price in DGN tokens to the store owner. Emits an `ItemPurchased` event for demonstration purposes.

### Utility

- **`balanceOf(address account) public view override returns (uint256)`**: Returns the token balance of an account (overrides the ERC20 `balanceOf` function).
- **`getPlayerItems(address player) public view returns (uint256[] memory)`**: Returns the list of item IDs redeemed by a specific player.
- **`setCooldownPeriod(uint256 _cooldownPeriod) public onlyOwner`**: Allows the owner to update the cooldown period for redemptions.


## Usage

1. **Minting Tokens**: The contract owner can mint new tokens to any address.
2. **Transferring Tokens**: Users can transfer DGN tokens to other addresses.
3. **Redeeming Items**: Users can redeem items from the store if they have enough tokens and meet the cooldown requirements.
4. **Purchasing Items**: Users can purchase items from the store by transferring tokens to the store owner.
5. **Checking Balances and Items**: Users can check their token balance and the items they have redeemed.

