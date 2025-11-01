# Arc Testnet Deployment Guide

## 1. Fund Wallet
- Faucet: https://faucet.circle.com
- Select Arc Testnet, request USDC (native gas token)

## 2. Deploy Contract
```bash
source .env && forge create src/HelloArchitect.sol:HelloArchitect \
  --rpc-url $ARC_TESTNET_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast
```
Save the contract address from output.

## 3. Add to .env
```bash
HELLOARCHITECT_ADDRESS="0x..."
```

## 4. Interact
```bash
# Set greeting
source .env && cast send $HELLOARCHITECT_ADDRESS 'setGreeting(string)' 'Welcome to Arc Testnet!' --rpc-url $ARC_TESTNET_RPC_URL --private-key $PRIVATE_KEY

# Get greeting
source .env && cast call $HELLOARCHITECT_ADDRESS 'getGreeting()(string)' --rpc-url $ARC_TESTNET_RPC_URL
```

## 5. Verify
https://testnet.arcscan.app