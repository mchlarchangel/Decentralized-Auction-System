# Auction Smart Contract

This repository contains a Solidity-based smart contract implementing an auction system. The project is part of the **Smart Contracts course by the University at Buffalo & The State University of New York** on Coursera. It provides a hands-on learning experience in developing decentralized applications (dApps) on the Ethereum blockchain.

---

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Smart Contract Workflow](#smart-contract-workflow)
- [Functions Explained](#functions-explained)
- [Testing and Deployment](#testing-and-deployment)
- [Important Notes](#important-notes)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## 📖 Overview
![Cuplikan layar 2025-01-17 091117](https://github.com/user-attachments/assets/4e7bdc95-5793-400b-beef-56598fdc1286)

This smart contract simulates a simple auction system where:
1. Users can register as bidders.
2. Bidders receive a fixed number of tokens to bid on items.
3. Bidders can place bids on available items using their tokens.
4. The contract owner (beneficiary) can reveal the winners for each item based on a pseudo-random selection process.

The primary goal of this project is to deepen understanding of Solidity programming concepts, including:
- Structs and mappings
- Access control using modifiers
- Arrays and dynamic data structures
- Randomization (pseudo-random) in smart contracts

---

## ✨ Features

1. **User Registration**: Allows users to register as bidders, initializing their accounts with a predefined number of tokens.
2. **Token-Based Bidding**: Bidders can allocate tokens to bid on specific auction items.
3. **Winner Selection**: The contract owner can reveal the winners for each item using a random selection mechanism.
4. **Transparency**: Bidders can query their remaining tokens and details of the items they bid on.
5. **Owner Access Control**: Only the contract owner can perform specific actions like revealing the winners.

---

## 🛠️ Technologies Used

- **Solidity (v0.4.17)**: Programming language for Ethereum smart contracts.
- **Remix IDE**: Browser-based development environment for writing and testing smart contracts.
- **Ethereum Blockchain**: Platform for deploying the smart contract.
- **Metamask**: Wallet for interacting with the Ethereum network.
- **Ganache/Testnets**: For local or testnet deployment and testing.

---

## 🚀 Getting Started

### Prerequisites
- Install [MetaMask](https://metamask.io/) for managing accounts.
- Access the [Remix IDE](https://remix.ethereum.org/) for writing and deploying the contract.
- Set up a local Ethereum environment (e.g., Ganache) or connect to a testnet like Sepolia or Goerli.

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/mchlarchangel/Decentralized-Auction-System.git
   ```
2. Open `Auction.sol` in Remix IDE.
3. Ensure the compiler version is set to `v0.4.17`.
4. Compile the contract.
5. Deploy the contract using an Ethereum account as the owner (beneficiary).

---

## 🏗️ Smart Contract Workflow

### 1. Deploying the Contract
- Deploy the contract using the `Auction` constructor.
- The account used for deployment becomes the `beneficiary` (contract owner).

### 2. Registering Bidders
- Call the `register()` function from bidder accounts.
- Each bidder is initialized with 5 tokens.
- Only four bidders are allowed (based on the implementation).

### 3. Placing Bids
- Use the `bid(uint _itemId, uint _count)` function to place bids on items.
  - `_itemId`: ID of the item (0, 1, or 2).
  - `_count`: Number of tokens to bid.
- Tokens used for bidding are deducted from the bidder's remaining tokens.

### 4. Revealing Winners
- The `revealWinners()` function is called by the contract owner.
- Winners for each item are selected randomly based on token allocations.

---

## 📜 Functions Explained

### `register()`
Registers a bidder with the following properties:
- `personId`: Unique ID for the bidder.
- `remainingTokens`: Initializes with 5 tokens.
- Adds the bidder to the `bidders` array and updates the `tokenDetails` mapping.

### `bid(uint _itemId, uint _count)`
Allows bidders to place bids on items:
- Deducts the specified number of tokens (`_count`) from the bidder's account.
- Adds the bidder's ID to the item's `itemTokens` array.

### `revealWinners()`
Selects winners for each item:
- Uses the block number and token allocation to generate a pseudo-random index.
- Assigns the winner's address to the `winners` array.

### `getPersonDetails(uint id)`
Returns the details of a bidder:
- `remainingTokens`
- `personId`
- Ethereum `address`

### `beneficiary()`
Returns the address of the contract owner.

---

## 🧪 Testing and Deployment

### Testing Steps
1. Deploy the contract using Remix IDE.
2. Register four accounts as bidders by calling `register()` from different accounts.
3. Use `bid()` to place bids on items with various token counts.
4. Verify token balances using `getPersonDetails(uint id)`.
5. Call `revealWinners()` as the owner and check the `winners` array for results.

### Deployment on a Testnet
1. Connect Remix to MetaMask.
2. Switch MetaMask to a testnet (e.g., Sepolia or Goerli).
3. Deploy the contract and interact with it using MetaMask accounts.

---

## ⚠️ Important Notes

- **Pseudo-Randomness**: The winner selection relies on `block.number`, which is not truly random. This approach should not be used for production-grade applications.
- **Token Limits**: Each bidder starts with 5 tokens, and the system supports only four bidders.
- **Owner Privileges**: Only the owner can reveal winners, ensuring control over the auction process.

---

## 📜 License

This project is licensed under the MIT License. You can find the license terms in the `LICENSE` file.

---

## 🙏 Acknowledgments
![Cuplikan layar 2025-01-17 092453](https://github.com/user-attachments/assets/79ac24f2-0b79-4277-a264-e967febee68f)

This project was developed as part of the **Smart Contracts course by the University at Buffalo & The State University of New York** on Coursera. Special thanks to the course instructors for providing invaluable insights into blockchain development and smart contract programming.

---
