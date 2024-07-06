# LoanVault Contract User Guide

The `LoanVault` contract integrates with a marketplace to offer a unique platform for securing loans against NFT collateral on the Ethereum blockchain. This guide explains each function within the contract, organized by their functionality, to help users navigate and utilize it effectively.

## Introduction

The `LoanVault` contract allows NFT owners to propose their assets as collateral for loans, while potential lenders can fund these loans under agreed terms. The contract ensures the security of the NFTs, manages loan agreements, and facilitates the transfer of funds between parties.

## Contract Initialization

### Constructor
- **Purpose**: Sets up the `LoanVault` contract with initial values.
- **Parameters**:
  - `marketplaceAddress`: Address of the associated `Marketplace` contract.
  - `_contractOwner`: The address of the contract owner.
  - `_feePercent`: The fee percentage the platform takes from the interest of repaid loans.

## Loan Proposal and Management

### `propose`
- **Purpose**: Allows an NFT owner to propose a loan by locking their NFTs as collateral.
- **Parameters**:
  - `_nfts`: Array of NFT contract addresses used as collateral.
  - `_nftIds`: Corresponding array of NFT IDs.
  - `_reqAmnt`: The amount requested by the borrower.
  - `_toPay`: The total amount the borrower agrees to repay.
  - `_duration`: Loan duration in days.
- **Note**: This function also calculates the total market value of the NFTs to ensure it covers the requested loan amount.

### `retract`
- **Purpose**: Enables a borrower to retract a proposed loan before it's accepted by a lender.
- **Parameters**:
  - `_id`: The unique ID of the loan proposal.

### `payInFull`
- **Purpose**: Allows borrowers to repay their active loans in full.
- **Parameters**:
  - `_id`: The unique ID of the active loan.
- **Note**: This function ensures the loan is marked as paid and returns the NFT collateral to the borrower.

## Lender Functions

### `acceptLoan`
- **Purpose**: Allows a lender to accept a loan proposal and transfer the requested funds to the borrower.
- **Parameters**:
  - `_loanId`: The unique ID of the loan to be funded.

### `liquidate`
- **Purpose**: Enables lenders to claim the collateral NFTs if the borrower defaults on the loan.
- **Parameters**:
  - `_id`: The unique ID of the defaulted loan.
- **Note**: This function is available only after the loan's duration has passed without full repayment.

## Utility Functions

### `withdraw`
- **Purpose**: Allows the contract owner to withdraw all Ether stored in the contract.
- **No Parameters**.

### `getNFTPrice`
- **Purpose**: Retrieves the current market price of a specific NFT using its token ID from the associated marketplace.
- **Parameters**:
  - `tokenId`: The token ID of the NFT.

## Information Retrieval

### `accessPending` and `accessActive`
- **Purpose**: Provide details of pending and active loans, respectively.
- **Parameters**:
  - `_index`: The unique ID of the loan.

### `_fee` and `_owner`
- **Purpose**: Return the fee percentage and the owner address of the contract.
- **No Parameters**.

## Events

- **`PostedLoan`**, **`CeaseLoan`**, **`AcceptedLoan`**, **`LoanPaid`**, **`LoanDefaulted`**: Events emitted to signal significant actions within the contract, such as loan proposals, retractions, acceptances, repayments, and defaults.