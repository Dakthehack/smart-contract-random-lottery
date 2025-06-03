Smart Contract Random Lottery 🎲


A robust and secure random lottery system built in Solidity, using Chainlink VRFv2.5 for provable randomness and Chainlink Automation for automated winner selection!

Created by following the Cyfrin Foundry Fundamentals course.

✨ Overview
This project implements a fully on-chain lottery (raffle) system:

Anyone can enter by paying the entrance fee.

A random winner is selected periodically using Chainlink VRF for verifiable randomness.

Automation via Chainlink Keepers ensures the lottery picks a winner after a predefined interval.

🚀 Features
✅ Verifiable Randomness: Utilizes Chainlink VRFv2.5 to securely and transparently select a random winner.
✅ Automated Execution: Integrated with Chainlink Automation for periodic winner selection.
✅ Modular & Secure: Clear error handling, state management via enums, and best-practice design patterns.
✅ Fully tested: Comprehensive test suite built with Foundry.

🧩 Contract: Raffle.sol
This contract implements the entire lottery logic.

Key Variables
Variable	Purpose
i_subscriptionId	Chainlink VRF subscription ID
i_gasLane	Chainlink gas lane keyHash
i_callbackGasLimit	Gas limit for the VRF callback
i_interval	Time interval between lottery rounds
i_entranceFee	Fee required to enter the raffle
s_lastTimeStamp	Last time the raffle was executed
s_recentWinner	Address of the most recent winner
s_players	Array of all participants
s_raffleState	Enum (OPEN or CALCULATING) to manage the raffle lifecycle

Main Functions
enterRaffle(): Allows users to enter the lottery by paying the entrance fee.

checkUpkeep(): Called by Chainlink Automation to determine if a new winner should be picked.

performUpkeep(): Calls Chainlink VRF to request a random winner.

fulfillRandomWords(): Called by Chainlink VRF to select the winner and transfer the prize.

Getter functions: Expose important contract states and configurations.

🏗️ Project Structure
bash
Copy
Edit
├── src/           # Core contracts (Raffle.sol, etc.)
├── test/          # Tests (RaffleTest.t.sol, etc.)
├── script/        # Deployment and interaction scripts
├── lib/           # External dependencies (Chainlink, foundry-devops, solmate)
├── foundry.toml   # Foundry config
├── Makefile       # Helpful dev commands
└── README.md      # This file
🛠️ Setup & Usage
1️⃣ Install Dependencies
Run the following command to install all dependencies:

nginx
Copy
Edit
forge install
2️⃣ Build Contracts
Compile the contracts:

nginx
Copy
Edit
forge build
3️⃣ Run Tests
Execute the full test suite:

bash
Copy
Edit
forge test
4️⃣ Generate Coverage Report
Get a detailed coverage report:

nginx
Copy
Edit
forge coverage
5️⃣ Deploy the Contract
Use the provided Foundry script:

go
Copy
Edit
make deploy ARGS="--network sepolia"
