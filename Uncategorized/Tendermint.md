Uses a supermajority voting mechanism that validators cast to decide which block gets included next in the chain. Part of the [[Cosmos]] ecosystem. The proposer for a round is chosen deterministically from the ordered list of validators, in proportion to their voting power. 

Tendermint BFT is an application-agnostic “consensus engine” that can turn any deterministic blackbox application into a distributedly replicated blockchain.

It is implemented through the [[ABCI]] so it is not platform or project specific, it can be connected and do inter blockchain consensus.

Tendermint is able to decompose the blockchain design by offering a very simple API between the application process and consensus process.