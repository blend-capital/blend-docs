## Interest Management

The pool contract is used to distribute the backstops share of pool interest to the pool's backstop depositor

### Creating Interest Auctions

Interest is distributed to backstop depositor's through a backstop interest auction. These are similar to Liquidation Auctions except they sell interest instead of collateral and buys backstop LP tokens instead of debt repayment. The backstop interest auction is created by calling the `create_interest_auction()` function and specifying which assets interest should be distributed for. All interest for these assets will be put up for auction and 140% of their value in backstop tokens will be requested return.

Similar to liquidation auctions - the percent of posted interest transferred to the liquidator increases by .05% every block for the first 200 blocks - and the percent of posted backstop tokens transferred to the pool decreases by .05% every block for the second 200 blocks.

### Filling Interest Auctions

When an interest auction is filled, the accrued interest is transferred to the liquidator - and backstop tokens used to fill the auction are transferred to the pool and donated to the backstop. This increases the value of the pools backstop deposits.
