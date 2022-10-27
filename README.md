# Install Node
Install Node Version Manager 
Linux | MacOS -> https://github.com/nvm-sh/nvm
Windows -> https://github.com/coreybutler/nvm-windows

```
nvm install 16
```
```
nvm use 16
```

# Install dependences
```
npm install -g yarn
```

```
yarn install
```

# Deploy on Eth Goerli testnet
## 1 Add private key on .env file
DEPLOYER_PKY_KEY=ab24af....

## 2 Create merkle root from holders file
ts-node scripts/createMerkleTree.ts
```
npx hardhat run scripts/createMerkleTree.ts --network goerli
```

## 3 Paste merkle root on .env file
MERKLE_ROOT=0xeF13....

## 4 Run deploy script
### Testnet
```
npx hardhat run scripts/deployPoorPlebFromRoot.ts --network goerli
```
### Mainnet
```
npx hardhat run scripts/deployPoorPlebFromRoot.ts --network mainnet
```

# Run tests
## 1. Run local eth node
```
npx hardhat node --fork https://eth-goerli.nodereal.io/v1/703500179cfc4348b90bebc0b3fba854
```
## 2. Run test file
```
npx hardhat test test/TestAll.test.ts --network localhost
```

## 3. Listen tests changes
```
nodemon --watch test/TestAll.test.ts --exec 'npx hardhat test test/TestAll.test.ts --network localhost'
```





