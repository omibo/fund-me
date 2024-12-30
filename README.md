# Fund Me Smart Contract

A decentralized crowdfunding smart contract built with Solidity that allows users to fund the contract and only permits the owner to withdraw the funds. The contract includes price feed functionality using Chainlink oracles to convert ETH to USD.

## Acknowledgments

This project was developed as part of the [Cyfrin Updraft's Foundry Fundamentals course](https://updraft.cyfrin.io/), an advanced smart contract development curriculum. The course provides comprehensive training in Foundry tooling and Solidity development best practices.

## Features

- ETH to USD conversion using Chainlink Price Feeds
- Minimum funding amount requirement in USD
- Owner-only withdrawal
- Automated fund tracking per contributor
- Gas-optimized using immutable variables and custom errors
- Comprehensive test coverage

## Tools & Technologies

- **Solidity** - Smart contract development
- **Foundry** - Development framework
- **Chainlink** - Price feed oracles

## Prerequisites

- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Foundry](https://book.getfoundry.sh/getting-started/installation)

## Installation

1. Clone the repository
```shell
git clone https://github.com/your-username/fund-me
cd fund-me
```

2. Install dependencies
```shell
forge install
```

3. Build the project
```shell
forge build
```

## Testing

Run the test suite:
```shell
forge test
```

For detailed gas reports:
```shell
forge test --gas-report
```

## Deployment

1. Set up your environment variables:
```shell
cp .env.example .env
```

2. Add your private key and RPC URL to `.env`

3. Deploy to network:
```shell
forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast
```

## Contract Interaction

### Funding
Send ETH to the contract (minimum 5 USD equivalent):
```shell
cast send <CONTRACT_ADDRESS> "fund()" --value 0.1ether --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

### Withdrawal (Owner Only)
Withdraw all funds from the contract:
```shell
cast send <CONTRACT_ADDRESS> "withdraw()" --rpc-url $RPC_URL --private-key $PRIVATE_KEY
```

## Contract Details

### Key Functions

- `fund()`: Allows users to fund the contract with ETH
- `withdraw()`: Enables the owner to withdraw all funds
- `getVersion()`: Returns the price feed version
- `getPrice()`: Gets the latest ETH/USD price
- `getConversion()`: Converts ETH amount to USD
- `getAddressToAmountFunded()`: Returns amount funded by an address
- `getFunder()`: Returns funder at given index
- `getOwner()`: Returns contract owner address

### Security Features

- Owner-only withdrawal using modifier
- Minimum funding amount check
- Chainlink price feed integration
- Withdrawal pattern implementation

## License

This project is licensed under the MIT License.