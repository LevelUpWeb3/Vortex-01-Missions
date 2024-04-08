# Guide to Get Started with OpenZeppelin Contracts Wizard

The OpenZeppelin Contracts Wizard is a web tool that helps you build custom ERC smart contracts for Ethereum. In this guide, you'll learn how to create a smart contract for an ERC-20 token.

## Prerequisites

Before you start, make sure you have a basic understanding of smart contracts and the Ethereum blockchain. Familiarity with [Solidity](https://docs.soliditylang.org/) is also recommended.

## Accessing the Contracts Wizard

Navigate to the [OpenZeppelin Contracts Wizard](https://wizard.openzeppelin.com/) to begin creating your custom ERC-20 or ERC-721 token.

## Creating an ERC-20 Token

1. **Select the Token Standard:** Choose ERC-20 for fungible tokens.
2. **Customize Features:** Enable features such as Mintable, Burnable, or Pausable according to your needs.
3. **Set Parameters:** Define your token's name, symbol, and initial supply.
4. **Generate Code:** The wizard will automatically generate the Solidity code for your custom token.

## Integrating with Your Project

### Setting Up Your Environment

Ensure you have [Node.js](https://nodejs.org/en/) installed and then set up [Hardhat](https://hardhat.org/) or [Truffle](https://www.trufflesuite.com/) in your project for smart contract development and testing.

### Installing OpenZeppelin Contracts

Install the OpenZeppelin Contracts library in your project:

```
npm install @openzeppelin/contracts
```

### Importing the Contract

In your Solidity file (e.g., `MyToken.sol`), import the OpenZeppelin contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor() ERC20("MyToken", "MTK") {
        _mint(msg.sender, 1000 * (10 ** uint256(decimals())));
    }
}
```

This example creates an ERC-20 token named MyToken with the symbol MTK and an initial supply of 1000 tokens to the deployer's address.

## Deployment

Deploy your smart contract to a test network using Hardhat or Truffle. Follow the respective documentation for guidance on deploying contracts.

By following these steps, you can quickly and easily create ERC standard tokens using the OpenZeppelin Contracts Wizard, integrating secure and tested smart contract functionality into your blockchain projects.