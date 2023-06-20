# Lending

## Lending

### How does lending work on Blend?

Lenders provide assets to the lending pool and receive interest in return. Borrowers can borrow these assets by posting collateral and paying interest at loan repayment.

Lenders can withdraw lent assets from the protocol at any time as long as two conditions are met:

* The lending pool the tokens are lent to must have sufficient liquidity - this means that borrowers cannot have borrowed all of the pools assets. If they have it's not a big deal as Blend's interest rate model will ensure that either borrowers repay, are liquidated, or more lenders step up to receive the high interest rates. TODO: link to interest rate stuff.
* The lender must be in good standing with the pool post-withdrawal - lenders have the option of using lent funds as collateral to borrow other pool assets. If they choose to do so they are only allowed to withdraw lent funds if the withdrawal maintains a health factor above 1. Otherwise they must repay the borrowed funds before they can withdraw.

### What are pool tokens?

If lenders choose not to use the funds they lent as collateral they will recieve pool tokens from the lending pool that represent their deposit. These tokens are fungible so users can transfer them to other network participants, use them in liquidity pools, and more.

### Why would users lend on Blend?

In exchange for lending with Blend, lenders receive interest from borrowers and BLND issuance from the protocol (if their pool is in the reward zone and is allocating emissions to lenders). In addition, when lending on Blend, users retain control of their funds. The protocol is decentralized, trust-free, and non-custodial. Only the protocol smart contracts have control over user funds, and users can withdraw their funds at any time.

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
