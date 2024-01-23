## Emission Distribution

The backstop contract is responsible for distributing emissions to backstop depositors and lending pools after it receives them from the emitter contract.

### Reward Zone

Emissions are only distributed to pool's in a Reward Zone, which the backstop contract manages, and backstop depositors designating their deposits to those pools.

#### Reward Zone Length

The number of pools that can be added to the reward zone starts at 10 and increases by one approximately every 3 months. This is done to prevent liquidity fragmentation by ensuring only a select number of pools receive emissions.

#### Adding Pools to the Reward Zone

Pools can be added to the Reward Zone by calling the `add_reward()` function.

If the reward zone has enough space, the pool will be added, if it doesn't, the pool will replace the pool specified by the `to_remove` parameter in the `add_reward()` function if it has more backstop tokens than the pool being replaced.

Note: If the pool being added to the reward zone has not met the minimum backstop threshold(link) the function will fail.

Note: If the to_remove pool is not in the reward zone, `add_reward()` will fail.

Note: If the pool is already in the reward zone, `add_reward()` will fail.

### Emission Management

The backstop contract facilitates both emission distribution and backstop emissions claims.

#### Emission Distribution

Emissions are distributed to backstop depositors and pools through a few steps:

1. `gulp_emissions()` is called which:
   Note: Any party can call this function 1. Calculates the `new_emissions` received - equal to `emitter_last_distribution_time - backstop_last_distribution_time`
   Note: One hour must have passed between the emitter contracts last distribution time and the backstops last distribution time or this function will fail. This is to prevent rounding issues 2. Calculates the amount of emissions to allocate to backstop depositors and pools - Backstop depositors get 70% of new emissions - Pools get 30% of new emissions 3. Sets emissions per second for backstop depositors - equal to `(backstop_emissions * pool_backstop_tokens / total_backstop_tokens_in_reward_zone_pools) + remaining_emissions /  7 days)`
   Note: This EPS will expire in 7 days, so emissions must be gulped every 7 days or backstop depositors will stop receiving emissions until emissions are gulped again. Emissions not distributed during a gulp gap will be accrued in the next gulp call.
   Note: Backstop deposits queued for withdrawal will not count towards the emission distribution calculation 4. Sets emissions earned by each pool - equal to `pool_emissions * pool_backstop_tokens / total_backstop_tokens_in_reward_zone_pools`
   Note: Backstop deposits queued for withdrawal will not count towards the emission distribution calculation

2. Pool's can now claim their emissions using the `gulp_pool_emissions()` function which makes an `approve()` call on the blend token contract to allow pool's to transfer their earned emissions out of the backstop contract.
   Note: This function can only be called by the associated lending pool contract or it will fail.

#### Emission Claims

The backstop facilitates emission claims by backstop depositors. Backstop depositors can claim their emissions by calling the `claim()` function which transfers the user's earned emissions for all input pool addresses to the user and reduces the user's accrued emissions to 0.

All claimed emissions are automatically deposited into the backstop and allocated to the pool they were earned in.

Note: User's can claim their emissions and deposit them on behalf of another user by specifying the user in the `to` parameter in the `claim()` function.
Note: This function can only be called by the associated user or it will fail.
