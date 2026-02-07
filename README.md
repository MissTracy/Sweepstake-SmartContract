# Ξ Sweepstake-SmartContract Ξ

Upgradeable ETH sweepstake smart contract using Chainlink VRF (Sepolia)

This repository contains the core smart contract for **Sweepstake**, an Ethereum-based ETH sweepstake dApp deployed on the **Sepolia testnet**.

Users participate by contributing ETH into a shared pool. At the end of each round, a **provably fair random winner** is selected using **Chainlink VRF**, and the full pool balance is transferred to the winner.

This repository focuses on showcasing the **smart contract logic, security patterns, and upgradeable architecture** behind the application.

---

## Project Overview

Sweepstake operates in time-based rounds:

1. Users join a round by contributing a minimum amount of ETH
2. Each wallet address may only join once per round
3. Rounds remain open for a fixed duration
4. After the round closes, a random winner is selected
5. Randomness is supplied by **Chainlink VRF**
6. The entire ETH pool is paid out to the winning participant
7. A new round can then be started

---

## Key Parameters

- **Round duration:** 10 minutes  
- **Minimum contribution:** 0.01 ETH  
- **Network:** Sepolia Testnet  
- **Randomness provider:** Chainlink VRF v2  

---

## Smart Contract Design

### EthRewardPool.sol

**Core features:**
- Time-based sweepstake rounds
- Secure ETH pooling and payouts
- One entry per address per round
- Verifiable randomness via Chainlink VRF
- Winner history tracked per round

**Architecture & security:**
- Upgradeable contract using the **UUPS proxy pattern**
- Reentrancy protection on ETH transfers
- Owner-restricted administrative functions
- Safe participant state reset between rounds
- No private keys or secrets stored on-chain

---

##  Security Considerations

- ReentrancyGuardUpgradeable prevents reentrancy attacks
- ETH payouts use low-level `call` with success verification
- Winner selection cannot be manipulated by the contract owner
- Participants cannot enter once a round has closed
- Randomness provided by a decentralized oracle (Chainlink)

---

##  Tech Stack

- **Solidity ^0.8.20**
- **OpenZeppelin Upgradeable Contracts**
- **Chainlink VRF**
- **Hardhat**
- **Ethers.js**
- **MetaMask Wallet Integration**

---

## Deployment

- Deployed on **Sepolia Testnet**
- Uses Chainlink VRF subscription for randomness
- Designed to support future upgrades via UUPS

---

## Notes

This repository intentionally includes **only the smart contract layer**.  
Frontend code and environment configuration files are excluded to protect private keys and API credentials.

---

## 👩‍💻 Author

Developed by **Miss Tracy B**  
Web3 / Blockchain Developer

