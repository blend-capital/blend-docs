## Overview

The emitter contract is responsible for distributing Blend to the backstop contract, defining that backstop contract, and swapping it out. Typical user's won't interact with the emitter contract directly, but it is a crucial part of the protocol.

### Structs

### View Methods

#### get_backstop

`fn get_backstop(e: Env) -> Address`

Returns the address of the backstop contract listed on the emitter.

#### get_last_distro

`fn get_last_distro(e: Env) -> i128`

Returns the timestamp of the last distribution of Blend to the backstop contract.

#### get_queued_swap

`fn get_queued_swap(e: Env) -> Option<backstop_manager::Swap>`

Returns `Some(Swap)` if a backstop swap is queued, `None` otherwise.

The `Swap` struct contains the following fields:

| field              | type    | description                                    |
| ------------------ | ------- | ---------------------------------------------- |
| new_backstop       | Address | the address of the new backstop contract       |
| new_backstop_token | Address | the address of the new LP token contract       |
| unlock_time        | i128    | the timestamp of when the swap can be executed |

### Write Methods

#### initialize

`fn initialize(e: Env, blnd_token: Address, backstop: Address, backstop_token: Address) -> i128`

The `initialize` function is used to set up the emitter contract. It sets the address of the blend token contract, the address of the Backstop token contract (the initial liquidity pool token that is deposited in the backstop), the address of the Backstop contract.

Additionally - this function will set the `last_distribution_time` to the current block timestamp - marking when Blend tokens begin being distributed to the backstop.

`initialize` can only be called once - any repeat calls will fail.

| param          | type    | description                                               |
| -------------- | ------- | --------------------------------------------------------- |
| blnd_token     | Address | the address of the Blend token contract                   |
| backstop       | Address | the address of the Backstop contract                      |
| backstop_token | Address | the address of the LP token contract used by the backstop |

#### distribute

`fn distribute(e: Env)`

The `distribute` function mints Blend tokens to the stored backstop contract address. The amount minted is equal to the number of seconds that have passed since the stored last distribution time.

Returns the amount of Blend minted and Emits a `distributed` event containing the backstop address and distribution amount.

No permissions are required to call this function

#### queue_backstop_swap

`fn queue_swap_backstop(e: Env, new_backstop: Address, new_backstop_token: Address)`

The `queue_backstop_swap` function queues a backstop swap.

Emits a `q_swap` event containing a `Swap` struct which lists the new backstop address, the new backstop token address, and the unlock time.

Fails if a swap is already queued.

Fails if the new backstop does not have more backstop tokens than the current backstop

#### cancel_backstop_swap

`fn cancel_swap_backstop(e: Env)`
