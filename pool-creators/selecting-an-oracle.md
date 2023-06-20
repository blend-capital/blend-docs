# Selecting an Oracle

Oracles are smart contracts that publish off-chain data on-chain. Blend pools use price oracles to get the prices of their assets.\
\
Pool creators must set a pool's oracle contract when they create a pool. This must be a single contract that can report prices for all assets in the pool.

### Oracle Adapters

In the case where a generalized oracle is not sufficient for a pool, ie. it doesn't support all assets the pool needs prices for, the pool creator may need to use an oracle adaptor. An oracle adaptor is a custom oracle contract which uses custom logic to aggregate multiple oracle feeds or impose desired behavior, such as reporting TWAP prices.&#x20;

#### Types of Price Feeds

Pool creators may find different types of price feeds useful. The two main types used in most lending pools are:

* Spot: Spot price feeds simply report the current price of an asset.
* TWAPs (time-weighted-asset-prices): These price feeds report average asset price over a given time period. These price feeds are more difficult to manipulate than spot price feeds, they are preferrable for high-volatility assets. TWAP's come in two types
  * GM-TWAPS: geometric mean twaps (TODO)
  * AM-TWAPS: arithmatic mean twaps (TODO)

#### Price Feed Aggregation

Ideally, price feeds should be aggregated across multiple sources to make them more resistant to manipulation. For example, a price feed reporting the XLM:USD spot price might aggregate the price by taking the average price from the Stellar DEX, Binance Orderbook, and Coinbase Orderbook.&#x20;

#### Types of Oracles

TODO

#### Well Known Oracles

TODO
