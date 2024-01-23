## Liquidation Management

The pool contract is used to create and carry out user liquidations which are carried out via auctions.

### Creating Liquidations

Liquidations are created with the `create_user_liquidations()` function. This function creates a liquidation auction which is used to auction off a portion of a user's collateral in exchange for the liquidator assuming a portion of the user's debt.

The creator of the liquidation auction can choose what percent of the user's positions to put up for auction, however, the percent chosen must result in the user's account having a health factor between 1.03 and 1.15 after the liquidation is fully filled.

All a user's positions are involved in every auction - the percentage of each position that is transferred to the liquidator is determined by the number of blocks that have passed since the liquidation started. The percentage of collateral positions transferred increases by .05% every block for the first 200 blocks - and the percentage of debt positions transferred decreases by .05% every block for the second 200 blocks.

### Filling Liquidations

Liquidators can fill liquidations fully or partially. When a liquidation is filled the delinquent user's positions are transferred to the liquidator depending how many blocks have passed since the liquidation started. The liquidator's account must be healthy after they fill the liquidation or the transaction will fail.

### Cancelling Liquidations

If at any point during a liquidation auction the delinquent user's account becomes healthy - the liquidation can be cancelled by anyone.
