# Guide to Get Started w/ Aztec.js

Aztec.js is a library that provides APIs for managing accounts and interacting with contracts on the Aztec network.

## Installation

Before starting installation, make sure that [Node.js](https://nodejs.org/en) or [Yarn](https://yarnpkg.com/) is installed.

### Install Aztec.js

Start by installing the `aztec.js` pacakge from npm:

```
yarn add @aztec/aztec.js
```

### Create a JS File

Create a new file named `main.js` at the project directory:

```
touch main.js
```

## Code

Start by importing `aztec.js` library:

```javascript
import { Contract } from '@aztec/aztec.js';
```

### Deploy a Contract

Before diving into the code, see [contract artifacts on the docs](https://docs.aztec.network/developers/contracts/compiling_contracts/artifacts).

```javascript
const contract = await Contract.deploy(wallet, MyContractArtifact, [...consructorArgs]).send().deployed();

console.log(`Contract deployed at ${contract.address}`);
```

### Send a Transaction

```javascript
const contract = await Contract.at(contractAddress, MyContractArtifact, wallet);

const tx = await contract.methods.transfer(amount, recipientAddress).send().wait();

console.log(`Transferred ${amount} to ${recipientAddress} on block ${tx.blockNumber}`);
```

### Call a View Function

```javascript
const contract = await Contract.at(contractAddress, MyContractArtifact, wallet);

const balance = await contract.methods.get_balance(wallet.getAddress()).view();

console.log(`Account balance is ${balance}`);
```