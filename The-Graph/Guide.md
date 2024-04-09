# Guide to Get Started w/ Subgraphs

A subgraph extracts data from a blockchain, processing it and storing it so that it can be easily queried via GraphQL.

The subgraph definition consists of a few files:

- **subgraph.yaml:** a YAML file containing the subgraph manifest,

- **schema.graphql:** a GraphQL schema that defines what data is stored for your subgraph, and how to query it via GraphQL,

- **AssemblyScript Mappings:** AssemblyScript code that translates from the event data to the entities defined in your schema (e.g. mapping.ts file).

## Installation and Setup

Before starting installation, make sure that [Node.js](https://nodejs.org/en) or [Yarn](https://yarnpkg.com/) is installed.

### Install Graph CLI

Start by installing `@graphprotocol/graph-cli`:

```
yarn global add @graphprotocol/graph-cli
```

### Initialize the Subgraph

```
graph init \
  --product subgraph-studio
  --from-contract <CONTRACT_ADDRESS> \
  [--network <ETHEREUM_NETWORK>] \
  [--abi <FILE>] \
  <SUBGRAPH_SLUG> [<DIRECTORY>]
```

## Code

### GraphQL Schema

```graphql
type Gravatar @entity(immutable: true) {
  id: Bytes!
  owner: Bytes
  displayName: String
  imageUrl: String
  accepted: Boolean
}
```

### Manifest

```yaml
dataSources:
  - kind: ethereum/contract
    name: ExampleSource
    network: mainnet
    source:
      address: 'CONTRACT_ADDRESS'
      abi: ExampleContract
      startBlock: 6627917
    mapping:
      kind: ethereum/events
      apiVersion: 0.0.6
      language: wasm/assemblyscript
      file: ./src/mappings/mapping.ts
      entities:
        - User
      abis:
        - name: ExampleContract
          file: ./abis/ExampleContract.json
      eventHandlers:
        - event: NewGravatar(...)
          handler: handleNewGravatar
        - event: UpdatedGravatar(...)
          handler: handleUpdatedGravatar
```

### Mapping

```javascript
import { NewGravatar, UpdatedGravatar } from '../generated/Gravity/Gravity'
import { Gravatar } from '../generated/schema'

export function handleNewGravatar(event: NewGravatar): void {
  let gravatar = new Gravatar(event.params.id)
  gravatar.owner = event.params.owner
  gravatar.displayName = event.params.displayName
  gravatar.imageUrl = event.params.imageUrl
  gravatar.save()
}

export function handleUpdatedGravatar(event: UpdatedGravatar): void {
  let id = event.params.id
  let gravatar = Gravatar.load(id)
  if (gravatar == null) {
    gravatar = new Gravatar(id)
  }
  gravatar.owner = event.params.owner
  gravatar.displayName = event.params.displayName
  gravatar.imageUrl = event.params.imageUrl
  gravatar.save()
}
```

This basic subgraph tracks the following two events of Gravatar contract:
- NewGravatar(),
- UpdatedGravatar().

### Code Generation

```
yarn codegen
```

### Build

```
yarn build
```

### Deploy

```
yarn deploy
```

You just deployed your subgraph! Now, you can make GraphQL queries on the interface of The Graph.