## Deposit Management

The backstop contract allows user's to deposit backstop tokens and allocate them towards different pools.

### Deposits

User's deposit backstop tokens into the backstop contract using the `deposit` function which accepts a deposit amount and a pool address. The specified amount will be sent to the backstop contract, and recorded as a user's deposit in the specified pool. The deposit amount is accounted for as a number of shares calculated as:

$$
shares_issued = deposit_amount * \frac{total_shares}{total_tokens}
$$

The number of backstop tokens each share is worth increases when the associated pool pays interest to the backstop and decreases when deposit's are used to cover bad debt realized by the pool as these change the pool's total_tokens without changing it's total_shares.

Once the deposit is finalized the pool's `total_tokens` will be increased by the deposit amount and the pool's `total_shares` will be increased by the number of shares issued.

### Withdrawals

Backstop withdrawals are handled in two steps.

1. The user calls `queue_withdrawal` with the amount they wish to withdraw and the pool they wish to withdraw from. This will queue a withdrawal for the specified amount of tokens from the specified pool. The user must wait 21 days before they can withdraw the shares.

Note: At any point the user can cancel a queued withdrawal using the `cancel_withdrawal` function.

2. After 21 days the user can call `withdraw` to withdraw the shares. This will transfer the tokens to the user and reduce the pool's `total_tokens` and `total_shares` accordingly.
