# Backstopping

### What is a Backstopping?

Each Blend lending pool has a backstop module, these backstop module's protect their lending pool from bad debt. In the case that a user incurs bad debt because their positions aren't liquidated quickly enough, their bad debt is transferred to the backstop module which pays it off by auctioning off it's deposits.\
\
User's can backstop pools by depositing into their backstop module, thus participating in insuring the lending pool.&#x20;

### Why Would a User Backstop a Pool?

Backstop module depositors receive a percent of interest paid by pool borrowers in exchange for insuring pools. The percent they are paid depends on a Backstop Take Rate which is set on pool creation. So if a backstop take rate is set at 25%, backstop module depositors will receive 25% of all interest paid by borrowers from that pool. This interest is transferred to backstop module depositors as BLND:USDC 80:20 liquidity pool shares.

In addition, pool's require a minimum amount of backstop deposits to be activated. User's who wish to see a certain pool activated may choose to backstop it in order to help it reach this minimum.

Finally, if the lending pool the user is backstopping is in the reward zone, backstop module depositors receive BLND emissions. This is to allow them to continue curating and insuring more pools in the Blend protocol.

### How do User's Backstop Pools?

Users can backstop pools by depositng 80/20 weighted BLND:USDC liquidity pool shares in the pools backstop module. They should note that if they wish to withdraw these deposits they will have to queue them for withdrawal and wait for a 30 day withdrawal queue period to end.&#x20;

### What are the Risks of Backstopping?

Backstop depositors act as first loss capital for lending pools. If the pool incurs bad debt their deposits will be auctioned off to cover it. Losses incurred by covering bad debt are shared proportionally between backstop module depositors.&#x20;

### How do Backstoppers Claim Earned Interest and Emissions?

Pool backstoppers can claim earned interest and emissions at any point. When they claim them they are deposited into the BLND:USDC 80:20 liquidity pool, and the shares are added to the users backstop module deposits.&#x20;
