## Fund Management

The lending pool allows user's and liquidators to manipulate the user funds it stores.

### Requests

All fund management is carried out using `Request` structs which are input into a single `submit()` function. Multiple requests can be bundled together to carry out actions atomically (e.g. supply and borrow in the same transaction). The `submit()` function will simply revert if the user's account is unhealthy after the requests are processed.

The following request types are supported:

- `Deposit` (enum 0): Deposits funds into the pool. These funds are not collateralized.
  Note: User's may want to deposit funds and not collateralize them if they do not want these funds to be liquidated in the event their account becomes delinquent, or if they do not want the position to count towards their position limit.
- `Withdraw` (enum 1): Withdraws uncollateralized funds from the pool.
- `Deposit Collateral` (enum 2): Deposits collateral into the pool.
- `Withdraw Collateral` (enum 3): Withdraws collateral from the pool.
- `Borrow` (enum 4): Borrows funds from the pool.
- `Repay` (enum 5): Repays borrowed funds.
- `Fill Liquidation` (enum 6): Fills a user liquidation.
  Note: Liquidations are filled using requests because liquidations are filled by transferring a portion of the delinquent user's positions directly into the liquidators positions. This is more gas efficient and capital efficient than normal liquidations. It also allows liquidators to delay repaying the user's delinquent debt by ensuring their account has enough collateral to cover the additional debt. Supporting this lowers the risk of liquidation cascades and also allows liquidators to slowly unwind positions rather than having to repay them immediately which lowers capital requirements.
- `Fill Bad Debt Auction` (enum 7): Fills a bad debt auction. This involves transferring bad debt stored in the backstops positions to the liquidators positions.
- `Fill Interest Auction` (enum 8): Fills an interest auction. This involves transferring interest stored in the backstops positions to the liquidators positions.

Requests are flexible in that they can be carried out on behalf of other users utilizing the `spender` `from` and `to` parameters on the `submit()` function. This allows users to delegate fund management to other users or contracts.

Note: the addresses input into `from` and `to` are required to authorize the `submit()` call or it will fail.

Note: if the pool status is `6` (setup) all requests will fail, if it's `4 or 5` (frozen) borrows, deposits, and liquidation cancellations will fail, and if it's `2 or 3` (on ice) liquidations will fail.
