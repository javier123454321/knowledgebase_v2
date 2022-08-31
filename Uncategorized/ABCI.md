We draw an analogy with the well-known cryptocurrency Bitcoin. Bitcoin is a cryptocurrency blockchain where each node maintains a fully audited Unspent Transaction Output (UTXO) database. If one wanted to create a Bitcoin-like system on top of ABCI, Tendermint BFT would be responsible for

-   Sharing blocks and transactions between nodes
-   Establishing a canonical/immutable order of transactions (the blockchain)

Meanwhile, the ABCI application would be responsible for

-   Maintaining the UTXO database
-   Validating cryptographic signatures of transactions
-   Preventing transactions from spending non-existent funds
-   Allowing clients to query the UTXO database

Tendermint is able to decompose the blockchain design by offering a very simple API between the application process and consensus process.