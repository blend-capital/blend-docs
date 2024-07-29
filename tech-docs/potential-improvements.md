---
description: >-
  This page covers known issues and potential improvements that could be made to
  the codebase if a new version of blend is released.
---

# Potential Improvements

### Known Issues

#### Potential for "stuck" Interest Auctions

Due to a bug in interest auction fill logic, if an interest auction is live for 400 blocks, it becomes impossible to fill the auction. This should never happen in practice as filling the auction will be profitable past 300, however it can occur if no one is monitoring the auctions progress.

If the auction does become stuck a new one can be created after the auction data entry expires (in 45 days). However, Soroban allows anyone to extend data entry time to live, so it would be possible for a bad actor to indefinitely extend the lifetime of this data entry.&#x20;

#### Potential for Unliquidatable Positions

Due to a lack of precision in the `percent_liquidated` parameter of the `new_liquidation_auction()`function (the parameter can only contain 3 digits representing whole percentages), it's possible for a user to be unliquidatable if the contract deems that their acceptable liquidation range is between 99% and 100%. In practice this requires quite extreme collateral and liability factors, as well as the user becoming undercollateralized extremely quickly, so it is quite unlikely. Furthermore, future price fluctuations will remove their position from this state.

#### Withdrawal Dequeuing Order

When a user dequeues a backstop withdrawal, the contract removes queued withdrawals from the front of the queue rather than the back. This results in the user's oldest queues (the one's closest to being unlocked) being dequeued rather than the newest ones.&#x20;

### Recommended Improvements

#### Add \`load\_pool()\` Function

It's annoying to reconstruct current pool and reserve state from ledger entries. Future versions of the protocol should include a `load_pool()` function that returns all reserve data and configurations&#x20;
