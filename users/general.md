# General

## General

### What is Blend?

Blend is a DeFi (decentralized finance) protocol that allows any entity to create or utilize an immutable lending market that fits their needs.

### What is a decentralized finance protocol?

A decentralized finance protocol is a financial application that does not rely on or require its users to trust a central intermediary. This is achieved by building the protocol using immutable smart contracts that run on a distributed network. Blend is made up of a group of immutable smart contracts running on Stellar's Soroban smart contract engine. There is no central organization that controls Blend and no organization Blend relies on to continue operating. This means that Blend is non-custodial, trust-minimized, and censorship-resistant.

### Why should you care about Blend?

Blend is the only app that offers lending pools that are secure, capital efficient, and permissionless. Utilizing it, ecosystem entities will be able to provide a variety of new functionality to the Stellar ecosystem such as real-world-financing, leveraged trading, yield products, and more DeFi apps.

**Security**

All Blend lending pools are isolated from one another. So lenders and borrowers are only exposed to the risk of the pool they're using. Additionally, each lending pool has manditory insurance through the backstop module. TODO: link

**Capital Efficiency**

Blend's reactive interest rate mechanism ensures that there isn't slack capital sitting in the protocol. Lenders and borrowers can expect to experience relatively efficient rates while using Blend.

**Permissionless**

Anyone can use Blend to Lend or Borrow. But more importantly, anyone can deploy a new lending pool as long as they can attract backstop module depositors. This means that all valuable use cases for Blend should be quickly supported rather than having to go through an arduous governance process.

### What are the benefits of Blend for Stellar?

Blend brings a decentralized, on-chain lending markets to the Stellar ecosystem.\
Within the ecosystem, this promises to:

* Increase trading and payment liquidity
* Improve capital productivity
* Reduce reliance on lending intermediaries like banks
* Offer new financial services to a global market

### How do I use Blend?

There is a decentralized web app that allows users to interact with the protocol.

The web app currently supports the following wallets:

* [**Freighter**](https://www.freighter.app)
* [**Albedo**](https://albedo.link)

As other interfaces begin to integrate Blend, a list of these integrations will be shown here!

***

More technical users can also use Blend directly by calling the smart contracts using the Horizon API layer. Please see the Soroban documentation and the technical-docs section for more information. TODO: links

### Does Blend have fees?

Using Blend can incur three kinds of fees:

**Network Fees**

Blend users must pay [Stellar Network fees](https://developers.stellar.org/docs/glossary/fees/) for each transaction.

**Interest Rates**

Borrowers on Blend must pay interest fees to lenders. These fluctuate based on demand.

**Backstop Take Rates**

Blend lenders share a portion of the interest they are paid by borrowers with their lending pools backstop module depositors. In return the backstop module insures them against any lending pool losses.

### Can Blend be changed or upgraded?

No. The closest thing to an upgrade for Blend is an emissions fork - in which case the old version of the protocol still functions as expected it just stops receiving emissions.

### What's a BLND token?

BLND is Blend's platform token. It is issued to those who use the protocol, and can be deposited in the backstop module to insure lending pools.

### Are there risks when using Blend?

Using any application involves risk. There are four main risks user's should consider when using Blend.

**Smart Contract Risk**

Blend functions using smart contracts. If a bug was discovered and exploited it could result in loss of user funds. To mitigate this risk, the Blend Protocol has been audited by third parties.\
Audit Reports:

**Stellar Smart Contract Risk**

Blend's smart contracts are built using the Stellar's Soroban smart contract protocol. If a vulnerability was discovered in Soroban it could result in loss of user funds.

**Stellar Decentralized Ledger Risk**

As with all decentralized ledgers Stellar comes with its unique set of risks. You can read more about the Stellar Consensus Protocol and it's risks [here](https://developers.stellar.org/docs/glossary/scp/).
