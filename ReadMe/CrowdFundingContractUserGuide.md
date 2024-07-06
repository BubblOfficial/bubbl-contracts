# CrowdFunding Contract User Guide

The `CrowdFunding` contract offers a straightforward platform for creating, managing, and contributing to crowdfunding campaigns on the Ethereum blockchain. This guide details each function within the contract, organized by their functionality, to help users navigate and utilize it effectively.

## Introduction

The `CrowdFunding` contract enables individuals to launch campaigns for various projects or causes, allowing the community to contribute financially. Each campaign is structured to have a target amount, a deadline, and a unique URI providing detailed information about the campaign.

## Campaign Management

### `createCampaign`
- **Purpose**: Initiates a new crowdfunding campaign.
- **Parameters**:
  - `_owner`: The address owning the campaign.
  - `_target`: The fundraising target for the campaign.
  - `_deadline`: The deadline by which the target amount needs to be raised.
  - `_campaignURI`: A URI containing detailed information about the campaign.
- **Returns**: The unique ID of the newly created campaign.

### `donateToCampaign`
- **Purpose**: Allows users to contribute funds to a specific campaign.
- **Parameters**:
  - `_id`: The unique ID of the campaign to which the donation is being made.
- **Note**: This function requires the transaction to include a `msg.value` indicating the amount of Ether to donate.

## Information Retrieval

### `getDonators`
- **Purpose**: Retrieves a list of addresses that have donated to a campaign and the corresponding amounts they have contributed.
- **Parameters**:
  - `_id`: The unique ID of the campaign.
- **Returns**: Two arrays; the first containing the addresses of the donators, and the second containing the amounts donated by each address, respectively.

### `getCampaigns`
- **Purpose**: Fetches all campaigns created on the platform.
- **Returns**: An array of `Campaign` structs, each containing details about a campaign, including the owner, target, deadline, amount collected, donators, donations, and campaign URI.

## Campaign Structure

Each `Campaign` struct consists of the following fields:
- `owner`: The Ethereum address of the campaign's creator.
- `target`: The target amount of funds to raise for the campaign.
- `deadline`: The timestamp indicating the campaign's fundraising deadline.
- `amountCollected`: The total amount of funds collected for the campaign so far.
- `donators`: An array of addresses that have contributed to the campaign.
- `donations`: An array of amounts donated by each address in the `donators` array.
- `campaignURI`: A URI containing detailed information about the campaign.

## Key Considerations

- When creating a campaign, ensure the `deadline` is set to a future timestamp to allow sufficient time for fundraising.
- Donations are forwarded directly to the campaign owner's address upon receipt. It is crucial for contributors to perform due diligence on campaigns they wish to support.
- The contract does not implement a refund mechanism. Once a donation is made, it is considered final.
