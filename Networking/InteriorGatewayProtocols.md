# Interior Gateway Protocols

Routers use **[[Routing]] Protocols** routers communicate what is the best path to anywhere in the planet/ 

### [[Routing]] Protocols
1. Interior gateway protocols
	- link state [[Routing]] protocols
	- distance vector protocols
1. Exterior Gateway Protocols

### Interior Gateway Protocols

#### Distance Vector Protocols
Routers take its [[Routing]] table and send a list(vector) of hop information (distance) to each other.

Router A can have a bunch of entries.  
i.e. r1 > r2 > r3 > destination router
	if destination router knows of a quicker path ( a router that is next to r1 but closer to the destination router than r3 ) it sends the packet back through the new route.

destination router > r4 > r1 
r1 updates its routing table accordingly

#### Link State protocols
Each router advertises the state of the network
routers broadcast, process, and compute the best way to traverse the network, but are more computationally intensive. Generally, they are replacing Distance Vector Protocols

### Exterior Gateway Protocols
The internet is an enormous mesh  of autonomous systems. Core internet routers need to know about the autonomous system to function

Getting data to the edge of an autonomous system is the priority of routers.

there is an Internet Assigned Numbers Authority handles IP address allocation as well as **Autonomous System Number Allocation (ASN)**

Like single decimal IP address. IP addresses have a need to represent a network + host ID in its address.

An ASN don't need  to change the host


