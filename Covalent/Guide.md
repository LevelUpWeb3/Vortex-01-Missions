# Guide to Get Started w/ Covalent TypeScript SDK

The Covalent SDK is a way to integrate the Unified API for working with blockchain data. The SDK works with all supported chains including mainnets and testnets.

## Installation and Setup

First of all, if you don't have an API key, visit [https://www.covalenthq.com/platform/auth/register/](https://www.covalenthq.com/platform/auth/register/) to get one.

### Install Client SDK

Before starting installation, make sure that [Node.js](https://nodejs.org/en) or [Yarn](https://yarnpkg.com/) is installed.

Then start by installing the `client-sdk` package from npm:

```
yarn add @covalenthq/client-sdk
```

### Create a JS File

Create a new file named `main.js` at the project directory:

```
touch main.js
```

## Code

Start by importing the package:

```javascript
import { CovalentClient } from "@covalenthq/client-sdk";
```
Initialize a function called `ApiServices`:

```javascript
const ApiServices = async () => {

}
```

Initialize the client with your own Covalent API key:

```javascript
const ApiServices = async () => {
    // Replace with your Covalent API key
    const client = new CovalentClient("YOUR_API_KEY");
}
```

Call `BalanceService.getTokenBalancesForWalletAddress()` method:

```javascript
const ApiServices = async () => {
    // Replace with your Covalent API key
    const client = new CovalentClient("YOUR_API_KEY");
    const resp = await client.BalanceService.getTokenBalancesForWalletAddress("eth-mainnet", "WALLET_ADDRESS"); 
    if (!resp.error) {
        console.log(resp.data);
    } else {
        console.log(resp.error_message);
    }
}
```

It will return the token balances of that particular user with address `WALLET_ADDRESS`.