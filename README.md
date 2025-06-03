# 🎰 Random Lottery Smart Contract

Welcome to the **Random Lottery** project—a fully decentralized lottery (raffle) built with Solidity and Chainlink VRF!

> Created while following the [Cyfrin Foundry Fundamentals Course](https://github.com/Cyfrin/foundry-fundamentals-f23).

---

## ✨ Overview

This project implements a secure, on-chain random lottery system:

- **Anyone can enter** by sending ETH.
- **A random winner** is selected at regular intervals using Chainlink VRF for provable randomness.
- **Automation via Chainlink Automation** ensures the lottery runs without manual intervention.

---

## 💡 Key Features

✅ **Verifiable Randomness**  
Powered by [Chainlink VRFv2.5](https://docs.chain.link/docs/vrf/v2-5/) to ensure secure and transparent winner selection.

✅ **Automated Execution**  
Integrated with [Chainlink Automation](https://docs.chain.link/chainlink-automation/introduction/) to trigger winner selection automatically.

✅ **Robust State Management**  
Utilizes enums for clear state tracking (`OPEN` and `CALCULATING`).

✅ **Fully Tested**  
Built with [Foundry](https://book.getfoundry.sh/) and includes comprehensive test coverage.

---

## 📦 Project Structure
├── src/ # Core smart contracts (e.g. Raffle.sol)
├── script/ # Deployment and interaction scripts
├── test/ # Test suite (RaffleTest.t.sol)
├── lib/ # External dependencies (Chainlink, Foundry-std, Solmate, etc.)
├── foundry.toml # Foundry configuration file
├── Makefile # Makefile for helpful dev commands
├── .github/ # GitHub Actions workflows
└── README.md # This file!


---

## 🏗️ Smart Contract: `Raffle.sol`



### Core Concepts

| Variable             | Description                                           |
| -------------------- | ----------------------------------------------------- |
| `i_subscriptionId`   | Chainlink VRF subscription ID                         |
| `i_gasLane`          | Chainlink VRF keyHash (gas lane)                      |
| `i_callbackGasLimit` | Gas limit for the VRF callback                        |
| `i_interval`         | Time interval (in seconds) between draws              |
| `i_entranceFee`      | Amount of ETH required to enter the lottery           |
| `s_lastTimeStamp`    | Timestamp of the last draw                            |
| `s_recentWinner`     | Address of the most recent winner                     |
| `s_players`          | Array of all current players                          |
| `s_raffleState`      | Enum (OPEN or CALCULATING) to manage raffle lifecycle |

### Key Functions

- `enterRaffle()`: Players send ETH to enter the lottery.
- `checkUpkeep()`: Called by Automation to check if a new draw is needed.
- `performUpkeep()`: Starts the random winner selection via VRF.
- `fulfillRandomWords()`: Called by VRF to determine the winner and distribute the prize.
- Various getter functions to expose contract data.

---

## 🛠️ Development Setup

1️⃣ **Install dependencies**

```bash
forge install
