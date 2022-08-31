# Ethereum Yellow Paper
## Basics
Ethereum works as a distributed state machine, which all the nodes agree upon a base state and then perform state transition functions to it. The base state is stored as a [[Merkle Patricia Tree]] - a set of hashed nodes that store hashes of hashes all the way down to prove the integrity of the state before. There is a data store - [[the Ethereum state database]] [Link](https://ethereum.stackexchange.com/questions/359/where-is-the-state-data-stored), which ties the root hash of the state of a block to the state at that block.
Users pay for having nodes in the machine compute their arbitrary code by paying gas fees denominated in Wei, this stops arbitrarily large and indefinite computations to clog up resources indefinitely.  Once all the computations have finished in a given block a Proof-of-work consensus mechanism stores the data in the new state as a result of the state transfer function, hashes the new Merkle Patricia Tree, and submits the block for propagation throughout the network.
## Accounts
The account state for each address in the blockchain is denominated by four fields:
1. Nonce: number of txs or contracts in the account
1. balance: amount of Wei
1. storageRoot: location of the root node in the Merkle Patricia Tree which decodes the information in the address
1. codeHash (only if the account is a [[smart contract]], there is no differentiation between smart contracts and users in the Ethereum blockchain.) Pointer to the address which retrieves the code for the contract. If the codeHash points to an empty string, it is a regular (non-contract) account.
The world state collapse function is:
10) LS(σ) ≡ {p(a) : σ\[a\] != 0}
where p(a) is the lookup of all the codeHash for an address KEC(a) and the storage root lookup RLP(a) for each value of the address. :
 p(a) ≡ (KEC(a), RLP (σ\[a\]n, σ\[a\]b, σ\[a\]s, σ\[a\]))
 ## Transactions
 Externally cryptographically signed transaction performed by an actor (could be non-human). Each transaction also has the following fields: 
 1. nonce: How many Txs the sender has sent	
 2. gasPrice Wei per computation
 3. gasLimit
 4. to: Adress
 5. value: Wei sent to recipient or contract
 6. v, r, s: Signature or sender
1. init or data: the allocation of space for the EVM code of the smart contract (init) or a message in the transaction (data).

## Gas and Payment
A mechanism to avoid endless loops. Every transaction requires gas to be included into the global state. You set up a Gas Limit and Gas Price because any change is returned to the user if the transaction does not consume the entirety of it. 
A miner can choose to ignore the transaction, so a higher price increases the probability of a transaction being included in the next block. 