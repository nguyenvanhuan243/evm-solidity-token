# EVM Token Template (ETT)

This is a standard ERC-20 token implementation on the Ethereum blockchain. The contract provides a basic template for creating fungible tokens that follow the ERC-20 standard.

## Contract Overview

The contract consists of three main components:

1. **ERC20Interface**: Defines the standard ERC-20 interface with required functions and events
2. **SafeMath**: Provides safe mathematical operations to prevent overflows and underflows
3. **EvmTokenTemplate**: The main token contract implementing the ERC-20 standard

## Token Details

- **Name**: EvmToken Template
- **Symbol**: ETT
- **Decimals**: 18
- **Total Supply**: 100,000,000 ETT (100 million tokens with 18 decimals)

## Features

The contract implements all standard ERC-20 functions:

- `totalSupply()`: Returns the total token supply
- `balanceOf(address)`: Returns the token balance of a specified address
- `allowance(address, address)`: Returns the remaining tokens that a spender can spend on behalf of an owner
- `approve(address, uint256)`: Allows a spender to spend tokens on behalf of the owner
- `transfer(address, uint256)`: Transfers tokens from the sender to a specified address
- `transferFrom(address, address, uint256)`: Transfers tokens from one address to another using the allowance mechanism

## Security Features

1. **SafeMath Implementation**: All mathematical operations use SafeMath to prevent:
   - Integer overflow
   - Integer underflow
   - Division by zero

2. **Standard ERC-20 Security**: The contract follows the ERC-20 standard which includes:
   - Proper event emission for transfers and approvals
   - Balance checks before transfers
   - Allowance management for delegated transfers

## Events

The contract emits two standard events:

1. `Transfer(address indexed from, address indexed to, uint256 tokens)`: Emitted when tokens are transferred
2. `Approval(address indexed tokenOwner, address indexed spender, uint256 tokens)`: Emitted when an approval is set

## Usage

### Deploying the Contract

When deployed, the contract:
1. Sets the token name, symbol, and decimals
2. Mints the total supply to the deployer's address
3. Emits a Transfer event from the zero address to the deployer

### Transferring Tokens

```solidity
// Direct transfer
token.transfer(recipientAddress, amount);

// Transfer using allowance
token.approve(spenderAddress, amount);
// Spender can then transfer
token.transferFrom(ownerAddress, recipientAddress, amount);
```

## Technical Details

- **Solidity Version**: ^0.5.0
- **License**: Not specified
- **Network**: Compatible with any EVM-compatible blockchain

## Important Notes

1. The contract uses 18 decimals, which is the standard for most ERC-20 tokens
2. All token amounts in the contract are represented in the smallest unit (wei equivalent)
3. The contract includes basic functionality and can be extended with additional features as needed

## Security Considerations

While the contract implements SafeMath and follows the ERC-20 standard, it's recommended to:
1. Have the contract audited before deployment
2. Test thoroughly on test networks
3. Consider adding additional security features like:
   - Pausable functionality
   - Access control
   - Token burning mechanism
   - Minting controls
