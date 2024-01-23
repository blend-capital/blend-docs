## Drawing from and Donating to Deposits

Pools interact with backstop deposits allocated to them by drawing from the deposits to cover bad debt and donating a percentage of interest to the deposits.

### Drawing

Pools draw from backstop deposits allocated to them using the `draw()` function. This transfers the requested amount of backstop tokens from a specified pool's backstop deposits to a specified recipient and reduces the pool's `total_tokens` by the amount drawn.

This function is used to allow backstop depositors to cover bad debt it has accumulated.

Note: The draw function must be called by the specified pool or it will fail.

### Donating

Any party can donate to backstop depositors using the `donate()` function. This transfers the specified amount of backstop tokens from the caller to the backstop contract and increases the value of the the deposits allocated to the pool specified by the donator.

This function is used to allow pools to donate a percentage of interest to backstop depositors.
