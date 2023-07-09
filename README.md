# About
# Getting Started

## Requirments
git
    Run git --version and if you get git version x.x.x as response you are good to go
foundry
    Run forge --version and if you get something like forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z) as a response you are good to go

## Quickstart
    git clone https://github.com/Cyfrin/foundry-fund-me-f23
    cd foundry-fund-me-f23
    forge build

## Optional Gitpod
If you can't or don't want to run and install locally, you can work with this repo in Gitpod. If you do this, you can skip the clone this repo part.

# Usage
    Deploy: 
            forge script scripts/DeployFundMe.s.sol

## Testing
    forge test

    or

    // Only run test functions matching the specified regex pattern.

    "forge test -m testFunctionName" is deprecated. Please use 

    forge test --match-test testFunctionName

    or

    forge test --fork-url $SEPOLIA_RPC_URL

### Test Coverage
    forge coverage

# Deployment to a testnet or mainnet

1.Setup environment variables

You'll want to set your SEPOLIA_RPC_URL and PRIVATE_KEY as environment variables. You can add them to a .env file, similar to what you see in .env.example.

PRIVATE_KEY: The private key of your account (like from metamask). NOTE: FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.

SEPOLIA_RPC_URL: This is url of the sepolia testnet node you're working with. You can get setup with one for free from Alchemy

You can also add your ETHERSCAN_API_KEY if you want to verify your contract on Etherscan.

2.Get testnet ETH

Head over to faucets.chain.link and get some testnet ETH. You should see the ETH show up in your metamask.

3.Deploy

forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY

## Scripts

After deploying to a testnet or local net, you can run the scripts.

Using cast deployed locally example:

cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>

or

forge script script/FundFundMe.s.sol --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast

### Withdraw 

cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>

## Estimate Gas

You can estimate how much gas things cost by running:

forge snapshot

You'll get an output called .gas-snapshot

# Formatting

To run code formatting:

forge fmt