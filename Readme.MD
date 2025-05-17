# EVM Token Template

This is a standard ERC20 token implementation with safe mathematical operations. The contract is designed to be a template for creating new ERC20 tokens on the Ethereum blockchain.

## Contract Overview

The contract consists of three main parts:
1. ERC20Interface - Standard ERC20 interface
2. SafeMath - Safe mathematical operations
3. EvmTokenTemplate - Main token implementation

## Token Details

- **Name**: EvmToken Template
- **Symbol**: ETT
- **Decimals**: 18
- **Total Supply**: 100,000,000 tokens (100 million with 18 decimals)
- **Initial Distribution**: All tokens are initially sent to the contract deployer

## Contract Functions

### ERC20Interface Functions

#### `totalSupply()`
- Returns the total number of tokens in circulation
- Excludes tokens in the zero address (burned tokens)
- View function (doesn't modify state)

#### `balanceOf(address tokenOwner)`
- Returns the token balance of a specific address
- Input: address to check
- Returns: number of tokens held by the address
- View function

#### `allowance(address tokenOwner, address spender)`
- Checks how many tokens a spender is allowed to spend on behalf of the token owner
- Input: token owner address and spender address
- Returns: remaining allowance
- View function

#### `transfer(address to, uint tokens)`
- Transfers tokens from the sender's address to another address
- Input: recipient address and amount of tokens
- Returns: true if transfer is successful
- Emits: Transfer event

#### `approve(address spender, uint tokens)`
- Allows a spender to spend tokens on behalf of the sender
- Input: spender address and amount of tokens
- Returns: true if approval is successful
- Emits: Approval event

#### `transferFrom(address from, address to, uint tokens)`
- Transfers tokens from one address to another
- Can only be called by an approved spender
- Input: sender address, recipient address, and amount of tokens
- Returns: true if transfer is successful
- Emits: Transfer event

### SafeMath Functions

#### `safeAdd(uint a, uint b)`
- Safely adds two numbers
- Checks for overflow
- Returns: sum of the two numbers

#### `safeSub(uint a, uint b)`
- Safely subtracts two numbers
- Checks for underflow
- Returns: difference between the two numbers

#### `safeMul(uint a, uint b)`
- Safely multiplies two numbers
- Checks for overflow
- Returns: product of the two numbers

#### `safeDiv(uint a, uint b)`
- Safely divides two numbers
- Checks for division by zero
- Returns: quotient of the division

### Main Contract Functions (EvmTokenTemplate)

#### Constructor
- Initializes the token with:
  - Name: "EvmToken Template"
  - Symbol: "ETT"
  - Decimals: 18
  - Total Supply: 100,000,000 tokens
- Assigns all tokens to the contract deployer
- Emits a Transfer event

#### State Variables
- `name`: Token name ("EvmToken Template")
- `symbol`: Token symbol ("ETT")
- `decimals`: Number of decimals (18)
- `_totalSupply`: Total supply of tokens
- `balances`: Mapping of address to token balance
- `allowed`: Mapping of address to address to allowance

#### Events
- `Transfer(address indexed from, address indexed to, uint tokens)`
  - Emitted when tokens are transferred
  - Includes sender, recipient, and amount

- `Approval(address indexed tokenOwner, address indexed spender, uint tokens)`
  - Emitted when an approval is set
  - Includes owner, spender, and amount

## Deployment

To deploy this contract:

1. Use Remix IDE (https://remix.ethereum.org/)
2. Create a new file named `token.sol`
3. Copy and paste the contract code
4. Compile with Solidity version 0.5.0
5. Deploy using:
   - MetaMask for mainnet/testnet deployment
   - JavaScript VM for local testing

## Security Features

- SafeMath implementation to prevent overflows and underflows
- Standard ERC20 compliance
- Clear event logging for all transfers and approvals
- Proper access control for token transfers

## Usage Examples

### Transfer Tokens
```solidity
// Transfer 100 tokens to another address
token.transfer(recipientAddress, 100 * 10**18);
```

### Approve Tokens
```solidity
// Approve another address to spend 1000 tokens
token.approve(spenderAddress, 1000 * 10**18);
```

### Transfer From (after approval)
```solidity
// Transfer 500 tokens from one address to another (requires approval)
token.transferFrom(fromAddress, toAddress, 500 * 10**18);
```

## License

This contract is open source and available under the MIT License.

## Disclaimer

This contract is provided as a template. Always audit the code and test thoroughly before deploying to mainnet. Consider using a more recent Solidity version for new deployments.
