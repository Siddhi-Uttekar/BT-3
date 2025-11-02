https://docs.google.com/document/d/1OzZMfJa0487M9HMoJ5_CRU_I81bLYNr5aWXe0keUWnE/edit?usp=sharing

1.Go to https://remix.ethereum.org/

2.Write the following code in .sol

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


3.transfer gas fees to your wallet from - Ethereum Sepolia Faucet - https://cloud.google.com/application/web3/faucet/ethereum/sepolia
   -- copy etherum address from your wallet(receiving address)

4. in remix ide, go to deploy & run transactions -> environment -> browser extenstion -> inject metamask

5. deploy and verify

6. go to link on the terminal to see the transaction details

7. interact call the wave() func In your deployed contract section.
   
