# FCT Miner

A simple Facet transaction miner for the Sepolia network, designed to generate and send transactions on L1 to mine Facet Compute Token (FCT) on Facet. This tool can execute a set number of transactions or run indefinitely, depending on user preferences and remaining ETH balance.

## Features

- Sends Facet transactions using the provided wallet.
- Monitors ETH balance to ensure mining halts if it drops below a user-specified threshold.
- Before each transaction, logs Current ETH balance
- After each transaction, logs L1/Facet Transaction Hashes, FCT Mint Amount, and FCT Mint Rate.
- Supports both single-run and recursive mining modes.

---

## Installation & Use

### Prerequisites

- [Node.js](https://nodejs.org) installed (tested with Node.js v18+).
- An Ethereum wallet with some Sepolia ETH (testnet ETH).
- A `.env` file with your private key, RPC endpoint, and minimum ETH balance threshold.

### Setup

1. Open CommandPrompt
2. Create a new folder on your desktop (replacing `<YourUsername>`):
   ```bash
   mkdir "C:\Users\<YourUsername>\Desktop\fct-miner"
3. Change into that folder (replacing `<YourUsername>`):
   ```bash
   cd "C:\Users\<YourUsername>\Desktop\fct-miner"
4. Clone this repository into the current folder (note the `.` at the end to prevent a subfolder from being created):
   ```bash
   git clone https://github.com/0xFacet/fct-miner.git .
5. Install dependencies:
   ```bash
   npm install
6. Create a `.env` file in the project directory with the following content (replacing `0xYOUR_PRIVATE_KEY` - keep the 0x prefix):
   ```bash
   PRIVATE_KEY=0xYOUR_PRIVATE_KEY
   FACET_RPC=https://sepolia.facet.org
   ETH_THRESHOLD=5000000000000000 # Minimum ETH balance in wei before stopping (example: 0.005 ETH)
7. Ensure you have Sepolia ETH in your wallet for transaction fees.

### Usage
1. Run the miner script with:
   ```bash
   node miner.js
Give it a few seconds - eventually you'll be prompted to enter (1) or (2), choosing between:
- (1) Fixed Number of Transactions: Specify how many transactions to send.
- (2) Recursive Mining: Automatically send transactions until either you run out of ETH (per threshold set in `.env`) OR you manually stop the script (by pressing Ctrl+C).

Example Output:
For each transaction, the miner logs:
- Current ETH Balance (before transaction)
- Transaction Count
- L1 Transaction Hash
- Facet Transaction Hash
- FCT Mint Amount
- FCT Mint Rate

## License
This project is open-source and available under the MIT License.

## Notes
- This tool is designed for the Sepolia testnet and is not suitable for production use.
- Verify your `.env` settings carefully to avoid exposing private keys.
- Be warned, if you choose Recursive Mining it's going to continuously send transactions using your ETH balance. Manage your ETH balance accordingly.
- The FCT issuance rate (per calldata gas unit) changes over time, [read docs here](https://docs.facet.org/3.-technical-details/facets-gas-mechanism).
