# Adware Contract User Guide

The `Adware` contract integrates with the `Marketplace` contract to provide a comprehensive advertising platform on the Fraxtal network. This guide details each method, organized by their functionality, to help users effectively utilize the contract.

## Introduction

The `Adware` contract enables creators and advertisers to engage with digital advertising spaces, including billboard ads and video ad slots, within a decentralized marketplace. It supports dynamic auction systems for billboard advertising and a queue system for video advertisements, catering to a broad spectrum of advertising needs.

## Initialization

### Constructor
- **Purpose**: Sets up the `Adware` contract with initial values and configurations.
- **Parameters**:
  - `_contractOwner`: The address of the contract owner.
  - `_marketplaceAddress`: The address of the associated `Marketplace` contract.
  - `_startingBidPrice`: The initial bid price for billboard ads.
  - `_videoAdSpotPrice`: The price per spot for video ads.

## Configuration Methods

### `setMarketplaceContract`
- **Purpose**: Updates the address of the `Marketplace` contract.
- **Parameters**:
  - `_marketplaceAddress`: The new address of the `Marketplace` contract.

### `modifyStartingBidPrice`
- **Purpose**: Adjusts the starting bid price for billboard ads.
- **Parameters**:
  - `_newAmount`: The new starting bid amount.

### `modifyVideoAdSpotPrice`
- **Purpose**: Alters the price for video ad slots.
- **Parameters**:
  - `_newPrice`: The new price for video ad slots.

## Billboard Advertising

### `bidForBillboardAd`
- **Purpose**: Allows users to place bids for billboard advertising slots.
- **Parameters**:
  - `_adDetailsURL`: The URL containing details of the advertisement.

### `initiateNewBillboardAuction`
- **Purpose**: Starts a new auction cycle for billboard advertising slots.
- **Restrictions**: Can only be called when the current auction cycle ends.

### `resetAuctionEarly`
- **Purpose**: Resets the billboard ad auction cycle before its scheduled end.
- **Restrictions**: Can only be performed by the contract owner.

## Video Advertising

### `buyVideoAdSlots`
- **Purpose**: Enables advertisers to purchase spots for video ads.
- **Parameters**:
  - `spots`: The number of ad spots to purchase.
  - `_adDetailsURL`: The URL containing details of the advertisement.

### `displayNextVideoAd`
- **Purpose**: Displays the next video ad in the queue and distributes earnings.
- **Parameters**:
  - `contentCreator`: The address of the content creator where the ad will be displayed.

## Financial Transactions

### `withdrawMyEarnings`
- **Purpose**: Allows users to withdraw their pending earnings from advertisements.
- **No Parameters**.

## Utility and Information Retrieval

### `retrieveActiveAds`
- **Purpose**: Fetches all active video ads currently in the queue.
- **No Parameters**.

### `getCurrentBillboardDetails`
- **Purpose**: Retrieves details of the current billboard ad auction.
- **No Parameters**.

### `retrieveSpecificUserAds`
- **Purpose**: Fetches all active video ads purchased by a specific user.
- **Parameters**:
  - `user`: The address of the user whose ads are to be retrieved.

### `listTodayTopBid`
- **Purpose**: Returns the highest bid amount for today's billboard ad auction.
- **No Parameters**.

## Events

- **`BillboardBidPlaced`**, **`VideoAdSlotPurchased`**, **`VideoAdPlayed`**: Events that notify when significant actions are taken within the contract, such as placing a bid or purchasing ad slots.