# Marketplace Contract User Guide

The `Marketplace` contract, built on the  Fraxtal network, offers a comprehensive platform for minting, buying, selling, renting NFTs, and managing subscriptions. This guide covers each method, organized by functionality, to help you navigate and utilize the contract effectively.

## Contract Initialization

### Constructor

- **Purpose**: Initializes the contract with the market owner and sets up the NFT collection name and symbol.
- **Parameters**:
  - `_contractOwner`: The address of the marketplace owner.

## NFT Minting

### `mintNFT`

- **Purpose**: Mints a new NFT with a specified URI and art status.
- **Parameters**:
  - `tokenURI`: URI for the NFT metadata.
  - `isArt`: Boolean indicating if the NFT is art.

### `mintAndListNFT`

- **Purpose**: Mints a new NFT and immediately lists it for sale.
- **Parameters**:
  - `tokenURI`: URI for the NFT metadata.
  - `price`: Sale price of the NFT.
  - `isArt`: Boolean indicating if the NFT is art.

## Sales Management

### `listNFTForSale`

- **Purpose**: Lists an owned NFT for sale.
- **Parameters**:
  - `tokenId`: The ID of the NFT to list.
  - `price`: The sale price.

### `relistNFT`

- **Purpose**: Relists an NFT with a new price.
- **Parameters**:
  - `tokenId`: The ID of the NFT to relist.
  - `price`: The new sale price.

### `unlistNFT`

- **Purpose**: Removes an NFT from being listed for sale.
- **Parameters**:
  - `tokenId`: The ID of the NFT to unlist.

### `purchaseNFT`

- **Purpose**: Allows a user to purchase a listed NFT.
- **Parameters**:
  - `tokenId`: The ID of the NFT to purchase.

## Auction Management

### `startNFTAuction`

- **Purpose**: Starts an auction for an NFT.
- **Parameters**:
  - `tokenId`, `startPrice`, `minimumPrice`, `discountRate`, `duration`: Auction parameters.

### `cancelNFTAuction`

- **Purpose**: Cancels an ongoing auction.
- **Parameters**:
  - `tokenId`: The ID of the NFT auction to cancel.

### `buyNFTFromAuction`

- **Purpose**: Purchases an NFT from an ongoing auction.
- **Parameters**:
  - `tokenId`: The ID of the NFT to buy.

## Rental Management

### `listNFTForRent`

- **Purpose**: Lists an NFT for rent.
- **Parameters**:
  - `tokenId`: The ID of the NFT.
  - `dailyPrice`: The daily rental price.

### `unlistNFTFromRental`

- **Purpose**: Removes an NFT from rental listings.
- **Parameters**:
  - `tokenId`: The ID of the NFT.

### `rentNFT`

- **Purpose**: Rents an available NFT.
- **Parameters**:
  - `tokenId`: The ID of the NFT to rent.
  - `duration`: Rental duration in days.

## Subscription Management

### `purchaseStandardPass`, `purchasePremiumPass`

- **Purpose**: Purchases a subscription pass (Standard or Premium).
- **Parameters**:
  - `duration`: The duration of the pass (Monthly, Annual).

### `purchaseRentAddOn`

- **Purpose**: Purchases an add-on for rental access.
- **No parameters**.

## Withdrawals and Earnings

### `withdrawFunds`

- **Purpose**: Allows users to withdraw their earnings or refunds.
- **No parameters**.

## Utility Functions

- **`getNFTStatusPrice`**, **`fetchNFTDetails`**, **`fetchAllNFTs`**, etc.: Various methods for retrieving NFT details, status, and user-specific listings.

## Events

- Detailed descriptions of events such as `MarketItemCreated`, `NFTMinted`, `AuctionPurchaseLog`, etc., providing insights into contract activities.
