# Guide to Get Started w/ Chainlink Data Feeds

Chainlink Data Feeds are the way to connect your smart contracts to the real-world data such as asset prices, reserve balances, NFT floor prices, and L2 sequencer health.

Types of Data Feeds:

1. Price Feeds,
2. Proof of Reserve Feeds,
3. NFT Floor Price Feeds,
4. Rate and Volatility Feeds,
5. L2 Sequencer Uptime Feeds.

## Code

To consume price data, your smart contract should reference `AggregatorV3Interface`, which defines the external functions implemented by Data Feeds:

```solidity
pragma solidity ^0.8.7;

import { AggregatorV3Interface } from "@chainlink/contracts/src/v0.8/shared/interfaces/AggregatorV3Interface.sol";
```

```solidity
contract DataConsumerV3 {
    AggregatorV3Interface internal dataFeed;

    /**
     * Network: Sepolia
     * Aggregator: BTC/USD
     * Address: 0x1b44F3514812d835EB1BDB0acB33d3fA3351Ee43
     */
    constructor() {
        dataFeed = AggregatorV3Interface(
            0x1b44F3514812d835EB1BDB0acB33d3fA3351Ee43
        );
    }

    /**
     * Returns the latest answer.
     */
    function getChainlinkDataFeedLatestAnswer() public view returns (int) {
        // prettier-ignore
        (
            /* uint80 roundID */,
            int answer,
            /*uint startedAt*/,
            /*uint timeStamp*/,
            /*uint80 answeredInRound*/
        ) = dataFeed.latestRoundData();
        return answer;
    }
}
```

The latestRoundData function returns five values representing information about the latest price data. See the [Data Feeds API Reference](https://docs.chain.link/data-feeds/api-reference) for more details.