# Guide to Get Started w/ Ankr.js

Ankr.js is a JS library that lets users interact with Ankr's Advanced APIs. In this guide, you'll learn how to retrieve NFTs belonging to a particular user.

## Installation and Setup

Before starting installation, make sure that [Node.js]() or [Yarn]() is installed.

### Install Ankr.js

Start by installing the `ankr.js` package from npm:

```
yarn add @ankr.com/ankr.js
```

### Create a JS File

Create a new file named `main.ts` at the project directory:

```
touch main.js
```

## Code

Start by importing `ankr.js` library:

```javascript
import AnkrProvider from `@ankr.com/ankr.js`
```

Initialize an `AnkrProvider`:

```javascript
const provider = new AnkrProvider('');
```

Build `getNfts()` function:

```javascript
export const getNfts = async (address: string) => {
  const { assets } = await provider.getNFTsByOwner({
    walletAddress: address,
    blockchain: 'eth',
  });
  return {
    nfts: assets,
  };
};
```

It will return the NFTs owned by `address`.