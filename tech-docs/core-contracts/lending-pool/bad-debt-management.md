## Bad Debt Management

The bad debt management module is responsible for assigning bad debt to the backstop - auctioning it off - and socializing it if it cannot be auctioned off.

### Bad Debt Assignment

Bad debt is assigned to the backstop when a user's account no longer has any more collateral.

When a user's account is fully liquidated, if they do not have enough collateral a liquidator may only repay a portion of their debt. After this - the user's account will only have debt and no collateral. Then, anyone can call the `bad_debt()` to transfer all debt from the delinquent user to the backstop. This function will transfer the bad debt by adding it as debt positions to the backstop's pool positions.

### Bad Debt Auctions

Bad debt auctions are used to auction off bad debt to liquidators in exchange for a portion of the backstops deposits. They function the same way as liquidation auctions except they sell backstop deposits instead of collateral.

### Bad Debt Socialization

When bad debt auctions are filled - if the backstop no longer has over 5% of the backstop threshold - the backstops remaining debt positions are burned which socializes the bad debt, reducing the value of all deposits of this asset in the pool.
