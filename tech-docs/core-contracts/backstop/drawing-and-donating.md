## Drawing from and Donating to Deposits

Pools interact with backstop deposits allocated to them by drawing from the deposits to cover bad debt and donating a percentage of interest to the deposits.

### Drawing

Pools draw from backstop deposits allocated to them using the `draw()` function. This transfers the requested amount of backstop tokens from a specified pool's backstop deposits to a specified recipient and reduces the pool's `total_tokens` by the amount drawn.

Note: The draw function must be called by the specified pool or it will fail.

### Donating

Pool donations are a two step process

1. Pool's call `donate_usdc()` which transfers usdc to the backstop module and adds it to the input pool's stored `usdc_balance`

Note: the input pool must have been deployed by the pool factory or the `donate_usdc()` function will fail

2. Any party calls `draw_usdc()`
