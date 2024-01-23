## Backstop Management

The Emitter contract defines the backstop contract address that will receive blend tokens. It can switch this address through an emissions swap. This allows the backstop contract to be "upgraded" while retaining it's immutability.

### Setting the Initial Backstop

The backstop contract address is initially set on Emitter initialization. This is done through the `initialize` function. This function can only be called once - any repeat calls will fail.

### Emissions Swaps

Emission swaps can be carried out at any point if a new smart contract (generally an upgraded Backstop contract) contains more backstop_tokens than the current backstop contract. Backstop swaps can be used to upgrade both the backstop contract and the backstop token contract.

The steps to undertake a swap are to:

1. Deploy a new backstop contract

2. Convince existing backstop depositors that it is worthwhile to migrate to the new contract.

Note: If the new backstop contract is using a new backstop token, it must still be able to handle deposits of the current backstop token or the swap will be impossible.

Note: It's possible this will cause disruption for pools as backstop depositors must queue withdrawals from the old backstop contract in order to deposit in the new backstop contract. This could trigger pool status changes, which pool creators wshould be aware of.

3. Once the new contract has more backstop tokens than the current contract, call `queue_backstop_swap` on the Emitter contract with the new backstop contract address and the new backstop token address.

Note: The call will fail if the new backstop contract does not have more backstop tokens than the current backstop contract.

Note: Only one backstop swap can be queued at a time. If a swap is already queued, the call will fail.

4. Wait until the unlock time has passed (takes 31 days).

Note: If at any point during the swap process the new backstop contract has less backstop tokens than the current backstop contract, the swap can be canceled by calling `cancel_backstop_swap` on the Emitter contract.

Note: This queue time is to prevent malicious actors from swapping the backstop contract without giving backstop depositors time to withdraw the LP positions (backstop tokens are liquidity pool tokens) and force the attacker to finalize their trade.

5. Call `swap_backstop` on the Emitter contract.

Note: If the new backstop no longer has more backstop tokens than the original the call will fail

Note: a final Distribute call will be made to the old backstop contract before the swap is executed to ensure no emissions are lost.

Note: The `last_distro_time` for the new backstop will be set to the current ledger timestamp.

The swap is now complete. The old backstop contract will continue functioning as expected. However, backstop depositors in the old contract and user's of pool's associated with that backstop will no longer receive emissions - prompting them to switch to the new contracts.
