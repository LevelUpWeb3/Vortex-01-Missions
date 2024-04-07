# Aztec

## What is Aztec?

[Aztec](https://aztec.network/) is an L2 that provides programmable privacy to Ethereum.

## Private Smart Contracts

Aztec enables privacy-preserving smart contracts. Such contracts are a collection of functions, written as [zkSNARK](https://consensys.io/blog/introduction-to-zk-snarks) circuits. They can have different modes of execution:

1. **Private Functions:** They can read and write private state, read historical public state, consume or send messages to / from Ethereum, and read Ethereum state. They can call other private functions in the same contract, or other contracts, and can call public functions.

2. **Public Functions:** They can read and write public state, write private state, consume or send messages to / from Ethereum and read Ethereum state. They can call other public functions on the same or other contracts.

3. **Portal Contracts:** These are contracts on Ethereum that can receive messages from Aztec or send messages to Aztec from Ethereum contracts.

## Get Started with Aztec.js

Navigate through our [Guide](./Guide.md) to get started with Aztec.js.