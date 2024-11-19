# FCT Miner

A simple Facet transaction miner for the Sepolia network, designed to generate and send transactions on L1 to mine Facet Compute Token (FCT) on Facet. This tool can execute a set number of transactions or run indefinitely, depending on user preferences and remaining ETH balance.

## Features

- Sends Facet transactions using the provided wallet.
- Monitors ETH balance to ensure mining stops if it drops below a user-specified threshold.
- Logs transaction hashes, remaining ETH balance, and FCT earned (soon).
- Supports both single-run and recursive mining modes.

---

## Installation

### Prerequisites

- [Node.js](https://nodejs.org) installed (tested with Node.js v18+).
- An Ethereum wallet with some Sepolia ETH (testnet ETH).
- A `.env` file with your private key, RPC endpoint, and minimum ETH balance threshold.

### Steps

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/fct-miner.git
   cd fct-miner
2. Install dependencies:
   ```bash
   npm install
3. Create a `.env` file in the project directory with the following content:
   ```bash
   PRIVATE_KEY=0xYOUR_PRIVATE_KEY
   FACET_RPC=https://sepolia.facet.org
   ETH_THRESHOLD=5000000000000000 # Minimum ETH balance in wei before stopping (example: 0.005 ETH)
4. Ensure you have Sepolia ETH in your wallet for transaction fees.
5. Run the miner script with:
   ```bash
   node miner.js
### Mining Options

When you run the miner, you'll be prompted to choose between:
- Fixed Number of Transactions: Specify how many transactions to send.
- Recursive Mining: Automatically send transactions until either you run out of ETH (per threshold set in `.env`) OR you manually stop the script.

Example Output:
For each transaction, the miner logs:
- L1 Transaction Hash
- Facet Transaction Hash
- ETH balance remaining
- FCT earned per transaction (planned)

## License
This project is open-source and available under the MIT License.

## Notes
- This tool is designed for the Sepolia testnet and is not suitable for production use.
- Verify your .env settings carefully to avoid exposing private keys.
- The FCT issuance rate (per calldata gas unit) changes over time (read docs here: https://docs.facet.org/3.-technical-details/facets-gas-mechanism).
