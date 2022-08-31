- # Ethereum Yellow Paper
    - ## Basics
        - Ethereum works as a distributed state machine, which all the nodes agree upon a base state and then perform state transition functions to it. The base state is stored as a [[Merkle Patricia Tree]] - a set of hashed nodes that store hashes of hashes all the way down to prove the integrity of the state before. There is a data store - [[the Ethereum state database]] [Link](https://ethereum.stackexchange.com/questions/359/where-is-the-state-data-stored), which ties the root hash of the state of a block to the state at that block.
        - Users pay for having nodes in the machine compute their arbitrary code by paying gas fees denominated in Wei, this stops arbitrarily large and indefinite computations to clog up resources indefinitely.  Once all the computations have finished in a given block a Proof-of-work consensus mechanism stores the data in the new state as a result of the state transfer function, hashes the new Merkle Patricia Tree, and submits the block for propagation throughout the network.
    - ## Accounts
        - The account state for each address in the blockchain is denominated by four fields:
            - 1. Nonce: number of txs or contracts in the account
            - 1. balance: amount of Wei
            - 1. storageRoot: location of the root node in the Merkle Patricia Tree which decodes the information in the address
            - 1. codeHash (only if the account is a [[smart contract]], there is no differentiation between smart contracts and users in the Ethereum blockchain.) Pointer to the address which retrieves the code for the contract. If the codeHash points to an empty string, it is a regular (non-contract) account.
            - The world state collapse function is:
            - 10) LS(σ) ≡ {p(a) : σ\[a\] != 0}
            - where p(a) is the lookup of all the codeHash for an address KEC(a) and the storage root lookup RLP(a) for each value of the address. :
                - p(a) ≡ (KEC(a), RLP (σ\[a\]n, σ\[a\]b, σ\[a\]s, σ\[a\]))
    - ## Transactions
        - Externally cryptographically signed transaction performed by an actor (could be non-human). Each transaction also has the following fields: 
            - 1. nonce: How many Txs the sender has sent	
            - 2. gasPrice Wei per computation
            - 3. gasLimit
            - 4. to: Adress
            - 5. value: Wei sent to recipient or contract
            - 6. v, r, s: Signature or sender
            - 1. init or data: the allocation of space for the EVM code of the smart contract (init) or a message in the transaction (data).
    - ## Blocks
        - Have information about the chain, the parent block hash, and transactions among other things.
        - Each block has a parent Hash and a state Root hash which ensures the prior state has not been altered
        - To ensure each block's validity
            - 
    - Gas
        - Every transaction allocates a certain amount of gas as the upper limit. This is what allows for turing completeness, as it is proven that it is impossible to know if a particular computation is an infinite loop.
        - The gasLimit is the maximum amount of gas that will be spent in a transaction
        - The gasPrice is how much Wei will cost per gas.
        - Gas ONLY exists within the execution of a transaction, gasPrice is amount of WEI per unit of gas
        - 
    - Transaction Execution
        - Defines the state transition function
        - Contains a **substate** which is a tuple of contents which provide temporary memory allocation and interactions that will be derived from a transaction
            - Self Destruct set: accounts that will be discarded after tx completion
            - Log series: archived and indexable checkpoints that allow contracts to be tracked by third parties outside Ethereum
            - At is the set of touched accounts, excluding empty accounts
            - Ar is the refund balance
        - 
- Ethereum Assembly
    - The EVM is a Last-in First-out (LIFO) stack machine
    - Writing assembly gives you direct control over pointers and other features not available in high level languages.
    - https://ethereum.stackexchange.com/questions/3157/what-are-some-examples-of-how-inline-assembly-benefits-smart-contract-developmen
    - Two types of dev
        - **Inline Assembly : **can use inside Solidity source code.
        - **Standalone Assembly : **can use without solidity.
    - ```javascript
function addition(uint x, uint y) public pure returns (uint) {
     assembly {
          let result := add(x, y)   // x + y
          mstore(0x0, result)       // store result in memory address 0x0
          return(0x0, 32)           // return 32 bytes from memory 
      }
 }```
    - let initiates a space in memory and assigns a 0 to it
    - `let x //<- x = 0` `x := 4`
    - the **let** keyword
        - **Creates a new stack slot**
        - The new slot is **reserved for the variable**.
        - The slot is then automatically removed again when the end of the block is reached.
    - Strings **must** be up to 32 bytes in length
    - To create a new scope, use `{ //block scoped code }`
        - variables inside a block scope get deallocated after the scope ends
    - Variable scope
        - Inline assembly can access varables inside the function where it is being called
        - 
