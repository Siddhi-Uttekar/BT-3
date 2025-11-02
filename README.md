https://docs.google.com/document/d/1OzZMfJa0487M9HMoJ5_CRU_I81bLYNr5aWXe0keUWnE/edit?usp=sharing
# 🌊 WavePortal Smart Contract

A simple Ethereum smart contract that allows users to send “waves” — short messages stored on the blockchain.  
Built and deployed using **Remix IDE** on the **Ethereum Sepolia Testnet**.

---

## 🧩 Smart Contract Code

Create a new Solidity file named `WavePortal.sol` in [Remix IDE](https://remix.ethereum.org/) and paste the following code:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract WavePortal {
    struct Wave {
        address waver;      // The address of the user who waved
        string message;     // The message the user sent
        uint256 timestamp;  // The timestamp when the user waved
    }

    Wave[] public waves;          // Array to store all waves
    uint256 public totalWaves;    // Counter for total waves

    event NewWave(address indexed waver, string message, uint256 timestamp);

    constructor() {
        totalWaves = 0;
    }

    function wave(string memory _message) public {
        waves.push(Wave(msg.sender, _message, block.timestamp));
        totalWaves += 1;
        emit NewWave(msg.sender, _message, block.timestamp);
    }

    function getAllWaves() public view returns (Wave[] memory) {
        return waves;
    }

    function getTotalWaves() public view returns (uint256) {
        return totalWaves;
    }
}
⚙️ Setup & Deployment (Remix + MetaMask)
1️⃣ Open Remix
Visit: https://remix.ethereum.org/

Create a new file named WavePortal.sol and paste the code above.

2️⃣ Compile
Go to the Solidity Compiler tab.

Select compiler version 0.8.0 or higher.

Click Compile WavePortal.sol.

3️⃣ Connect Wallet
Open MetaMask and select the Sepolia Test Network.

Copy your wallet address.

4️⃣ Get Test ETH
Visit a Sepolia Faucet (e.g. https://sepoliafaucet.com).

Paste your wallet address to receive test ETH for gas fees.

5️⃣ Deploy Contract
In Remix, go to the Deploy & Run Transactions panel.

Environment: Injected Provider - MetaMask

Contract: WavePortal

Click Deploy and confirm the transaction in MetaMask.

✅ Once deployed, your contract will appear under Deployed Contracts.

💬 Interacting with the Contract
Step 1: Send a Wave
In the Deployed Contracts section:

Find the wave function.

Enter a message (e.g. "Hello Blockchain!")

Click transact and confirm the transaction in MetaMask.

This will store your message on-chain and emit an event.

Step 2: View All Waves
Find the getAllWaves() function.

Click call.

It will show all stored waves in an array format, for example:

csharp
Copy code
0: tuple(address, string, uint256):
   0xabc123...  Hello Blockchain!  1730541400
address: wallet address of sender

string: message sent

uint256: timestamp (Unix seconds)

Step 3: Get Total Waves
Click on getTotalWaves().

You’ll get the total number of waves stored, e.g. 1.

🌐 View on Sepolia Etherscan / Routescan
If you deployed on the Sepolia Testnet, you can verify your transactions:

Step 1: Find Your Contract
Copy your deployed contract address (from Remix).

Paste it into Sepolia Etherscan or Routescan.

Step 2: Check Transactions
Open the Transactions tab.

Click on the latest transaction (the one from wave()).

Scroll to Logs (Events) section — you’ll see:

makefile
Copy code
Event: NewWave
waver: 0xYourAddress
message: Hello Blockchain!
timestamp: 1730541400
✅ This confirms your “wave” was successfully broadcast and recorded on the blockchain.

🧭 Summary of Commands / Steps
bash
Copy code
# 1. Open Remix
https://remix.ethereum.org/

# 2. Create and paste WavePortal.sol code
# 3. Compile the contract
# 4. Connect MetaMask (Injected Provider)
# 5. Get Sepolia ETH from Faucet
# 6. Deploy the contract
# 7. Call the wave("Your message") function
# 8. Call getAllWaves() and getTotalWaves() to view results
# 9. Verify on Sepolia Etherscan
📜 Example Outputs
getTotalWaves():

Copy code
1
getAllWaves():

yaml
Copy code
[
  {
    waver: "0x1234abcd...",
    message: "Hello Blockchain!",
    timestamp: 1730541400
  }
]
✅ Contract Deployed Example
Example Contract Address:
0x2f952D6d7955F3ec5a51454c8361D54E99D8425c

Author: Sid
Network Used: Sepolia Testnet
Tools: Solidity, Remix IDE, MetaMask

🪄 "Every wave you send becomes a part of the blockchain forever!"
