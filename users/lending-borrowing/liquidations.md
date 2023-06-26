# Liquidations

In the case that a user's account becomes delinquent because they exceed their [borrow limit](broken-reference) they can be liquidated. This means their positions will be forcibly closed by another Blend user.

### How do Blend Liquidations Work?

When a Blend user becomes delinquent, any user may initiate a liquidation auction on their account - the liquidator will choose a set of the user's collateral positions to be auctioned off and a set of their liability auctions to be repaid. They cannot auction off more liabilities than are necessary to bring the account back to a healthy state, and the value of collateral auctioned off cannot greatly exceed the value of liabilities being repaid. \
\
As soon as the auction is initiated, it begins. At this point, anyone can fill the auction. The percent of the offered collateral the auction filler receives depends on how long the auction has gone on (the percent grows over time). Once 100% of the offered collateral is available, the percent of the liability that the filler must repay starts decreasing from 100% until it hits 0%. This way, we can be sure that the auction will be filled as soon as a market participant deems it profitable.&#x20;

Since liquidators have autonomy over when to fill the auction, they will typically fill it at a point where the value of the collateral they receive slightly exceeds the value of the liabilities they repay. The premium the liquidator receives is called the Liquidation Premium.

For a full explanation of the liquidation process see the [liquidation section](../../whitepaper/blend-whitepaper.md#liquidations) of the whitepaper.
