## Setting up dev environment for deployment / testing

If rust and solana-cli are already installed, skip the first 2 steps.

1. Install rust with the following command:

    ```
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
   Follow the command line instructions.


2. Install Solana CLI tools:

    ```
    sh -c "$(curl -sSfL https://release.solana.com/v1.9.11/install)"
    ```
   Be sure to add the installed `solana` directory to your path


3. Clone target project and cd into directory


4. Set RPC endpoint to use devnet:

    ```
    solana config set --url https://api.devnet.solana.com
    ```

5. Create a new keypair to use for testing:

    ```
    solana-keygen new --force
    ```

6. Airdrop some SOL to the new account on devnet:

    ```
    solana airdrop 5
    ```
   note: you may need to reduce the amount of SOL requested to 2, depending on the response


7. Build BPF bytecode for deployment on Solana devnet:

    ```
    npm run build:program-rust
    ```

8. Deploy program to devnet:

    ```
    npm run deploy:program
    ```
   Output will include program ID.  Search for this on the devnet block-explorer (https://explorer.solana.com/?cluster=devnet) to confirm deployment details.


9. Install node dependencies to use API / client for deployed program and run tests:

     ```
     npm install
     ```