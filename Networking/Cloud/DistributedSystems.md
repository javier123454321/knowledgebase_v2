# Distributed Systems

A group of computers that work together to appear as a single computer to the end user

The Machines have a shared state, but can fail independently.

#### Pros
- **Fault Tolerance** - If there are errors, the system can withstand the failure
- **Scalability** - It can easily serve higher demands
- **Performant** - it can coordinate to yield higher performance

#### Cons 
- **Network Failure** - Adds another point of failure to your system
- **Latency** - The time it takes for data to transmit between systems
- **Observability** - Dificulty in understanding what is happening in each piece and how it connects to the rest of the system
- **Management & Overhead** - You gotta manage everything, changes updates and connections. 

A Number of things in devops can be more difficult, but if the focus is site reliability, it can be better. Centralized [[Servers]] are better fr management and overhead.

### Types of Systems

#### Client Server
Computer that is requesting data (Client) that reaches out to server and displays it to the end user.

#### Three-tier
Information about the client is stored in a middle tier rather than on the client to simplify app deployment. (Web applications)

#### N-tier
Server needs to forward the requests to aditional services on the network

##### P2P
No aditional machines used to provide services or manage resources. Responsibilities are uniformly distributed among machines in the system (peers) which can serve as either client or server.

### Decentralized systems
Different than Distributed systems like load balancer. 

