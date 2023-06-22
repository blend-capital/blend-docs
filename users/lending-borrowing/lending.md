# Lending

### How does lending work on Blend?

Lenders supply assets they wish to Blend lending pools, borrowers then may borrow the assets by posting collateral to the pool and paying the lenders interest.

### How do you lend using Blend?

To lend using Blend lenders must first select a lending pool to lend to. When choosing a pool to lend to users should:

* Check the pool supports borrowing of the asset they want to lend - this is easy check for as the asset will have an lending interest rate above 0, and appear to be borrowable.
* Ensure the pool has a well capitalized backstop module.
  * The backstop module is the amount of assets insuring the pool against bad debt, so well capitalized backstop modules point to a pool being relatively safe
  * If a large percentage of the backstop module is queued for withdrawal, that points to the pool being in an unstable state and the user should avoid it for the time being.
* Ensure the assets supported as collateral in the pool are safe collateral assets.
  * Generally, low volatility, high liquidity assets make good collateral.
* Ensure the pools risk parameters are set appropriately
  * The pool should have reasolable collateral and liability factors for supported assets.
* Ensure the pools oracle contract is trustworthy
  * Oracles are crucial for the safety of pools - users should always be sure the oracle for their lending pool is trustworthy.

Lenders provide assets to the lending pool and receive interest in return. Borrowers can borrow these assets by posting collateral and paying interest at loan repayment.

Lenders can withdraw lent assets from the protocol at any time as long as two conditions are met:

* The lending pool the tokens are lent to must have sufficient liquidity - this means that borrowers cannot have borrowed all of the pools assets. If they have it's not a big deal as Blend's interest rate model will ensure that either borrowers repay, are liquidated, or more lenders step up to receive the high interest rates. TODO: link to interest rate stuff.
* The lender must be in good standing with the pool post-withdrawal - lenders have the option of using lent funds as collateral to borrow other pool assets. If they choose to do so they are only allowed to withdraw lent funds if the withdrawal maintains a health factor above 1. Otherwise they must repay the borrowed funds before they can withdraw.

### What are pool tokens?

If lenders choose not to use the funds they lent as collateral they will recieve pool tokens from the lending pool that represent their deposit. These tokens are fungible so users can transfer them to other network participants, use them in liquidity pools, and more.

### Why would users lend on Blend?

In exchange for lending using Blend lending pools, lenders receive interest from borrowers and BLND issuance from the protocol (if their pool is in the reward zone and is allocating emissions to lenders of the asset the user is lending). In addition, when lending on Blend, users retain control of their funds. The protocol is decentralized, trust-free, and non-custodial. Only the protocol smart contracts have control over user funds, and users can withdraw their funds at any time.

### What is the interest rate for lending on Blend?

Lending interest rates equal the _borrowing interest rate_ multiplied by the _utilization ratio_ since interest paid by borrowers is distributed proportionally to lenders. Borrowing interest rates are demand-based and calculated using the utilization ratio. This means borrowing interest rates increase as the percentage of protocol assets lent to borrowers increases. Check out the Interest Rate section to learn more about how this is calculated. TODO: link

### How do lenders receive interest?

When lenders withdraw their lent assets, they also withdraw any interest they have earned.

### Who controls my lent assets?

You do! Assets lent to the protocol are controlled by Blend's smart contracts. Therefore, you can use those smart contracts to withdraw your lent assets at any time.

### What assets can be lent?

Any Stellar-based asset supported by the lending pool you're using can be lent with Blend. If an asset isn't supported a new pool can be created to support it as long as sufficient backstop module depositors will support it.

### How do lenders withdraw lent assets?

Lenders can withdraw assets by using Blend's smart contracts. Doing so will also withdraw all interest the lender has accrued.

### Is there any situation where lenders can't withdraw assets?

If an assets utilization ratio is too high, there may not be sufficient liquidity for a lender to withdraw assets because too much of the asset balance is currently lent out. However, due to Blend's demand-based interest rate model, this is extremely unlikely. Interest rates are typically extremely high (over 100%) at high utilization ratios, which heavily incentivizes borrowers to repay their loans and new entities to lend to the protocol, thus adding liquidity and lowering the utilization ratio.

### Do Lenders Earn BLND Emissions?

Lenders earn BLND emissions if their pool is in the reward zone and the pool creator allocated emissions to lenders of the asset the user is lending. They may claim these emissions at any time at which point they are deposited into the 80:20 BLND:USDC liquidity pool and deposited into the pools backstop module on behalf of the user.
