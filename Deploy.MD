# Deployment Guide for EVM Token Template

This guide will walk you through the process of deploying the EVM Token Template contract using Remix IDE.

## Prerequisites

1. **Web Browser**
   - Chrome, Firefox, or any modern web browser
   - MetaMask browser extension installed

2. **MetaMask Setup**
   - Create a MetaMask wallet if you don't have one
   - Add the custom network to MetaMask:
     1. Open MetaMask
     2. Click the network dropdown (usually shows "Ethereum Mainnet")
     3. Click "Add Network"
     4. Click "Add a Network Manually"
     5. Fill in the following details:
        - Network Name: BNW Network
        - RPC URL: http://174.138.18.77:8545
        - Chain ID: 714
        - Currency Symbol: BNW
        - Block Explorer URL: (leave blank if not available)
     6. Click "Save"
   - Ensure you have enough BNW tokens for deployment gas fees

## Network Details
- **Network Name**: BNW Network
- **RPC URL**: http://174.138.18.77:8545
- **Chain ID**: 714
- **Currency Symbol**: BNW
- **Network Type**: EVM Compatible

## Step-by-Step Deployment Guide

### 1. Access Remix IDE

1. Open your web browser
2. Go to [Remix IDE](https://remix.ethereum.org/)
3. Wait for the IDE to load completely

### 2. Create New File

1. In the file explorer (left sidebar), click the "+" icon
2. Name the file `token.sol`
3. Copy and paste the entire contract code from our `token.sol` file

### 3. Compile the Contract

1. Click on the "Solidity Compiler" tab (icon looks like "S")
2. Set the following compiler settings:
   - Compiler Version: 0.5.0 (exact version)
   - Language: Solidity
   - EVM Version: istanbul (or default)
   - Optimization: Enable optimization (200 runs)
3. Click "Compile token.sol"
4. Wait for the compilation to complete
5. Check for any compilation errors in the console

### 4. Deploy the Contract

#### For Local Testing (JavaScript VM):

1. Click the "Deploy & Run Transactions" tab (play button icon)
2. Select "JavaScript VM" from the Environment dropdown
3. Click "Deploy" button
4. The contract will be deployed to a local blockchain
5. You can test all functions immediately

#### For BNW Network Deployment:

1. Click the "Deploy & Run Transactions" tab
2. Select "Injected Provider - MetaMask" from the Environment dropdown
3. Connect your MetaMask wallet when prompted
4. In MetaMask:
   - Select "BNW Network" from the network dropdown
   - Ensure you have sufficient BNW tokens for gas
5. Click "Deploy" button
6. Review the transaction in MetaMask:
   - Check gas fees (in BNW)
   - Verify contract details
7. Confirm the transaction in MetaMask
8. Wait for the transaction to be mined

### 5. Verify Contract Deployment

1. After deployment, the contract will appear under "Deployed Contracts"
2. Click the dropdown to see all available functions
3. Verify the initial setup:
   - Check `name()` - should return "EvmToken Template"
   - Check `symbol()` - should return "ETT"
   - Check `decimals()` - should return 18
   - Check `totalSupply()` - should return 100,000,000 * 10^18
   - Check `balanceOf()` with your address - should show total supply
4. Note down the contract address for future reference

### 6. Interact with the Contract

#### View Functions (No Gas Required):
```solidity
// Check total supply
totalSupply()

// Check your balance
balanceOf(yourAddress)

// Check allowance
allowance(ownerAddress, spenderAddress)
```

#### State-Changing Functions (Requires Gas):
```solidity
// Transfer tokens
transfer(recipientAddress, amount)

// Approve spender
approve(spenderAddress, amount)

// Transfer from (after approval)
transferFrom(fromAddress, toAddress, amount)
```

## Common Issues and Solutions

1. **Compilation Errors**
   - Ensure you're using Solidity version 0.5.0
   - Check for any syntax errors in the code
   - Verify all brackets and semicolons are correct

2. **Deployment Failures**
   - Insufficient gas: Increase gas limit in MetaMask
   - Network issues: Check your internet connection
   - Wrong network: Ensure you're on the correct network in MetaMask

3. **Transaction Failures**
   - Out of gas: Increase gas limit
   - Nonce issues: Reset MetaMask account
   - Network congestion: Wait and try again later

## Gas Optimization Tips

1. **Deployment Gas**
   - Current contract is optimized for 200 runs
   - Deployment typically costs between 2-4 million gas
   - Gas costs are paid in BNW tokens
   - Gas costs vary based on network conditions

2. **Transaction Gas**
   - Transfer: ~65,000 gas
   - Approve: ~46,000 gas
   - TransferFrom: ~75,000 gas
   - All gas fees are paid in BNW tokens

## Security Considerations

1. **Before Deployment**
   - Test thoroughly on testnet if available
   - Verify all functions work as expected
   - Consider getting a security audit
   - Ensure you have the correct network selected in MetaMask

2. **After Deployment**
   - Save the contract address
   - Monitor initial transactions
   - Keep private keys secure
   - Verify contract if block explorer is available

## Contract Verification

If a block explorer is available for the BNW Network:

1. Go to the block explorer
2. Find your contract address
3. Click "Contract" tab
4. Click "Verify & Publish"
5. Fill in the verification details:
   - Contract address
   - Contract name
   - Compiler version (0.5.0)
   - Optimization: Yes (200 runs)
6. Paste the contract code
7. Submit for verification

## Support

If you encounter any issues during deployment:
1. Check the Remix console for error messages
2. Verify your MetaMask connection to BNW Network
3. Ensure you have sufficient BNW tokens for gas
4. Verify the RPC URL is accessible
5. Check if the network is operational

## Network-Specific Notes

1. **BNW Network Characteristics**
   - EVM Compatible
   - Uses BNW as native token for gas
   - Chain ID: 714
   - RPC Endpoint: http://174.138.18.77:8545

2. **Important Considerations**
   - Always verify you're on the correct network before deploying
   - Keep track of your contract address after deployment
   - Monitor gas prices in BNW
   - Ensure RPC endpoint is stable and accessible

## Next Steps

After successful deployment:
1. Add liquidity to DEXs (if available on BNW Network)
2. Create a token website
3. Set up token monitoring
4. Implement additional features if needed
5. Document the contract address and deployment details

Remember: Always verify you're on the BNW Network before making any transactions!
