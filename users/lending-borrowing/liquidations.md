# Liquidations

In the case that a user's account becomes delinquent because they exceed their [borrow limit](broken-reference) they can be liquidated. This means their positions will be forcibly closed by another Blend user.

### How do Blend Liquidations Work?

When a Blend user becomes delinquent, any user may initiate a liquidation auction on their account - the liquidator will choose a set of the user's collateral positions to be auctioned off, and a set of their liability auctions to be repaid. They cannot auction off more liabilities than are necesssary to bring the account back to a healthy state, and the value of collateral auctioned off cannot greatly exceed the value of liabilities being repaid. \
\
As soon as the auction is initiated it begins, at this point anyone can fill the auction. The percent of the offered collateral the auction filler receives depends on how long the auction has gone on (the percent grows over time). Once 100% of the offered collateral is available, the percent of the liability that the filler must repay starts decreasing from 100% until it hits 0%. In this way we can be sure that the auction will be filled as soon as a market participant deems it profitable, and no auction will go unfilled. \


### What if price changes restore solvency to an account being liquidated?

If the market moves and causes a formerly delinquent account to become solvent, by increasing the value of their collateral for example, while an auction liquidation the account is underway any user may cancel the pending liquidation.
