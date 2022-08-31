Source: https://ethereum.stackexchange.com/questions/359/where-is-the-state-data-stored
[[Ethereum]] has a data store which allows for retrieval of current state based on the root hash of the block. The data is stored in two different ways, as:
-   chain data (the list of blocks forming the chain)
-   state data (the result of each transaction's state transition)
>While all chain data will be needed to ensure the cryptographic chain-of-custody and that nothing has been tampered with, old state data can be discarded (known as "pruning"). This is because state data is _implicit_ data. That is, its value is known only from calculation, not from the actual information communicated. By contrast, chain data is _explicit_ and stored as the block chain itself.
State data is not stored permanently and [pruned on each block,](https://blog.ethereum.org/2015/06/26/state-tree-pruning/) as we only need the latest version for a functioning [[blockchain]]. 
