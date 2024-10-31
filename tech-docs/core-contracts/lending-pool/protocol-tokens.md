# Protocol Tokens

The Blend protocol represents all positions for the pool via a token. This allows the pool to track interest fairly across multiple suppliers and borrowers for a given reserve.

When reading positions for an address via the `get_positions(address: Address)` function, the value returned is a Map of the reserve's index to the BToken or DToken balance.

## BTokens

A BToken is the tokenized representation of a supply made to a Blend pool. Each reserve has a unique BToken per pool, and they are non-transferable.

BTokens are converted to and from underlying assets with the reserve's `b_rate`. The `b_rate` is adjusted when interest is accrued.

$$
b\_tokens = \frac{underlying}{b\_rate}
$$

$$
underlying = b\_rate*b\_tokens
$$

## DTokens

A DToken is the tokenized representation of a liability against a Blend pool. Each reserve has a unique DToken per pool, and they are non-transferable.

DTokens are converted to and from underlying assets with the reserve's `d_rate`. The `d_rate` is adjusted when interest is accrued.

$$
d\_tokens = \frac{underlying}{d\_rate}
$$

$$
underlying = d\_rate*d\_tokens
$$
