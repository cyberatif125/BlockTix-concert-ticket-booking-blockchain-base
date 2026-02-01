# Concert Ticket Blockchain Platform

This project is a Web3 dApp for buying and reselling concert tickets using NFTs on Polygon Amoy.

## Tech Stack
- **Smart Contract**: Solidity (ERC-721)
- **Frontend**: Next.js + Tailwind CSS + Ethers.js
- **Network**: Polygon Amoy Testnet (Chain ID 80002)

## Prerequisites
- Node.js installed
- MetaMask extension
- Test MATIC (from [Polygon Faucet](https://faucet.polygon.technology/))

## Setup Instructions

1. **Install Dependencies**
   ```bash
   npm install
   cd frontend
   npm install
   ```

2. **Environment Configuration**
   - Create a `.env` file in the root directory:
     ```
     PRIVATE_KEY=your_metamask_private_key
     POLYGON_AMOY_RPC=https://rpc-amoy.polygon.technology/
     ```
   - Create `frontend/.env.local`:
     ```
     NEXT_PUBLIC_CONTRACT_ADDRESS=deployed_contract_address
     ```

## Deployment Guide (Polygon Amoy)

1. **Configure Hardhat**
   Ensure `hardhat.config.js` includes the Amoy network settings (Already configured in project if checking config, else see below).

   *Update `hardhat.config.js` if needed:*
   ```javascript
   require("@nomicfoundation/hardhat-toolbox");
   require("dotenv").config();

   module.exports = {
     solidity: "0.8.20",
     networks: {
       amoy: {
         url: process.env.POLYGON_AMOY_RPC || "https://rpc-amoy.polygon.technology/",
         accounts: [process.env.PRIVATE_KEY],
         chainId: 80002
       }
     }
   };
   ```

2. **Deploy Contract**
   ```bash
   npx hardhat run scripts/deploy.js --network amoy
   ```
   Copy the deployed address.

3. **Verify Contract (Optional)**
   ```bash
   npx hardhat verify --network amoy <CONTRACT_ADDRESS>
   ```

## Running the Frontend

1. Update `frontend/.env.local` with the new contract address.
2. Start the dev server:
   ```bash
   cd frontend
   npm run dev
   ```
3. Open http://localhost:3000

## Features
- **Admin**: Go to `/admin` to create concerts.
- **Shop**: Home page lists concerts. Buy tickets with MATIC.
- **Profile**: Go to `/profile` to view and resell tickets.

## Local Testing
To interact with the app locally, import this **Account #0** into MetaMask:
- **Private Key**: `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80`
- **Address**: `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266`
- **Balance**: 10,000 ETH
- **Network**: Localhost 8545 (Chain ID 31337 or 1337)
