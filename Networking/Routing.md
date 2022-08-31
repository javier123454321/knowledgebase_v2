# Routing

The way that information gets to multiple places

Routing issues tend to be handled by ISPs and only large companies

A network device that forwards traffic depending on the destination address of that routing

1. Router receives data packet
1. examines destination IP
1. Looks up destination network in routing table
1. forwards that to the router that is closest to the remote network.

Repeated as often as needed to get data to its destination

Network A     >     Router       >       Network B
       192.168.1.1 /      \ 10.0.0.254
          /                     \
Computer A                      Computer B 
192.168.1.100                   10.0.0.10

The router looks up the destination address in its table, and sends it to the nearest router that is closest to the final destination.

### Routing Tables
Routers were computers, and had a routing table that were manually updated.

Routing tables can vary depending on make and class of router.

4 columns

1. **Destination Network** A node for each network that the router knows about, (in CIDR)
When receiving an incoming packet it resolves which destination network it should go to to get to its destination. (Or send it to its catch all address)

1. **Next Hop** The IP address for the next router in the destination Network

1. **Total Hops** Routers try to pick the shortest path to its destination. Because routes are dynamic. The router will have to know how far away the destination is.

1. **Interface**  Router has to know which of its interfaces it should forward traffic out of.

Many core internet routers have millions of rows that are consulted on each request.

 
# Non Routable Address Space
there are 4,000,000,000 ip address spaces.
Ranges of IPs set assigned for anyone that can't be routed. Not every computer needs to connect to every other computer.

RFC 1918 defined 3 network addresses that can't be used by anyone. 

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

Internal systems can route to this, but cannot be routed to externally
