# Arc Testnet Deployment Guide

## Step 1: Fund Your Wallet

1. Visit the faucet: https://faucet.circle.com
2. Select Arc Testnet from the network dropdown
3. Paste your wallet address
4. Request testnet USDC (this is Arc's native gas token)

## Step 2: Deploy the Contract

Once your wallet is funded, run this command:

```bash
source .env && forge create src/HelloArchitect.sol:HelloArchitect \
  --rpc-url $ARC_TESTNET_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast
```

After deployment, save the contract address from the output (look for "Deployed to:").

## Step 3: Add Contract Address to .env

Add this line to your `.env` file (replace with your actual deployed address):

```bash
HELLOARCHITECT_ADDRESS="0x..."
```

## Step 4: Interact with Your Contract

Once deployed, you can call the contract:

```bash
source .env && cast send $HELLOARCHITECT_ADDRESS 'setGreeting(string)' 'Welcome to Arc Testnet!' --rpc-url $ARC_TESTNET_RPC_URL --private-key $PRIVATE_KEY
```

```bash
source .env && cast call $HELLOARCHITECT_ADDRESS 'getGreeting()(string)' --rpc-url $ARC_TESTNET_RPC_URL
```

## Step 5: Verify on Block Explorer

Check your deployment transaction on the Arc Testnet Explorer:
https://testnet.arcscan.app