# Pool Management

Pool management encompasses modifying pool status to freeze or unfreeze pools - and modifying pool parameters to add assets or adjust their risk/interest rate parameters.

### Pool Admin

Pool's may set a designated admin that has authority to change pool status' or update asset risk/interest rate parameters. Pool's with Admin's are considered Owned Pools. Alternatively, the pool's admin address can be set to the 0 address which makes the pool Immutable, although it's status can still be changed by the backstop module. Pool's without Admins are Standard Pools. Standard Pools are more decentralized and trustless than Owned pools, but lack the flexibility that may be desired by some pool creators.\
\
Pool creators set the pool admin when they create the pool using the deploy\_pool function on the pool factory contract. \
\
TODO:Github link

### Pool Status

Pool status changes are the primary way that pools can respond to unforeseen risks. Pools have three statuses'.&#x20;

#### Active:

Active pools function normally.

#### On-Ice:

Pools that are On-Ice have borrowing disabled. This status is designed for when the pool is at risk but not defunct. For example, if the pools oracle is suffering liveness issues that will be resolved, the pool should be set to On-Ice.&#x20;

#### Frozen:

Frozen pools have borrowing and depositing disabled. This status is for when a pool is defunct and should no longer be used. For example, if backstop module depositors in a Standard Pool want to move liquidity to a new pool with updated assets and parameters they should coordinate to freeze the old pool.

Pool state can be changed by either the pool manager, or by anyone if the correct backstop state is met.&#x20;

### Backstop State Requirements:

The backstop requirements to set specific pool status are as follows:

#### Active:

* Backstop deposits must exceed the minimum backstop requirement

\-and-&#x20;

* Less than 25% of backstop deposites are queued for withdrawal.

#### On-Ice:

* Backstop deposit fall below the minimum deposit requirement&#x20;

\-or-&#x20;

* Over 25% of backstop deposits arequeued for withdrawal.&#x20;

#### Frozen:

* Over 50% of backstop deposits are queued for withdrawal

In a case where a pool admin sets the pool to a more restrictive status, the backstop-state cannot be used to set a less restrictive state. Similarly, pool admins cannot set less restrictive status' if the pool's backstop's state does not meet the requirements for that status.

### Inital Pool Status

Pool's start in the On-Ice status. This is to limit the creation of unsafe pools by requiring that some insurance capital be put forward before a pool can start being used. The rationale here is a high-risk pool is unlikely to have many people willing to insure it.

### Pool Migration

Standard Pools occasionally need to be updated when oracles need to be changed or asset parameteres require an update. Backstop triggered status changes allow backstop depositors to force borrowers and lenders to move to a new pool. When an updated pool is deployed backstop depositors can coordinate to queue their deposits for withdrawal, then anyone can update pool status to FROZEN - forcing lenders and borrowers to migrate.\
\
Owned Pools also need to be updated when oracles need to be changed as pool admins cannot update the oracle address. Pool migration is simpler in this instance as the admin can just set the pool status to FROZEN without needing to coordinate with backstop depositors.&#x20;

### Risk/Interest Rate Parameters

Pool Admin's can modify asset risk and interest rate parameters, additionally they can add or remove assets from the pool.&#x20;
