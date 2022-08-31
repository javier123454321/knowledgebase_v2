# The Network Layer

### 
Nodes Communicate through the MAC addresses

MAC Addressing doesnt scale well. There is no way of knowing where a specific MAC address isin the world. 

### IP Addresses
32 bit numbers made up of 4 octets (Dotted Decimal Notation) 

Distributed in large sections to companies. Easier to own and manage than MAC addresses
IBM owns all of the IP addresses that start with a 9. 

IP is different in each network, and independent to the device. 

Dynamic Host Configuration Protocol

Static IP Addresses are reserved for [[Servers]] and network devices, dynamic ones are reserved for clients.

### IP datagrams and encapsulations
Under the IP protocol, a packet is referred to as a datagram

Header and Payload

Header in IP has more data than an ethernet header

- the first part is what version (IPV4, IPV6)
- header length 20 bytes
- Quality of Service, routers make decisions as to which are more important than others.
- Total length
- Identification field 
- Flag is the datagram fragmented
	Fragmentation is splitting of a datagram into smaller packet
- Fragmentation offset
- Time to live (how many routes the datagram can traverse)
	To stop an endness loop.
- Protocol 8 bit field of the transport layer protocol TCP/UDP
- Header Checksum field changes at each node
- Source IP Address
- Destination IP Address
- Options 
- Padding zeroes to ensure the header is the correct size

Size of a datagram is 2^16

Each layer is needed to the one above it.

### IP Address Class

Network id vs Host id
9 .    100.     100.     100
^      ^        ^        ^
Network Host    Host     Host

Class A - 0 (0-127) first bit 
Class B - 10 (128-191) first Bit
Class C - 110 (192-223) first bit

class D - 1110 (224-239)

CIDR replasses the class system.

### Address Resolution Protocol

ARP is a protocol used to discover the hardware address of a node with an IP Address

All network connected devices have an ARP table (IP address and MAC address mapping)

To send a request to 10.20.20.30 
client sendsan ARP message to the IP (F:FF:FF:FF)
client sends an ARP response with the MAC address for client to add to the ethernet request
the client stores this info in an ARP table (which expires every so often)

### Subnetting 

making a large network into smaller networks

Address classes break down the global IP namespace into subnets
a 9.\*.\*.\* ip address gets sent to the Class A 

### Subnet ID
Some bits that would comprise the host ID comprise the Sub ID
at the internet level, core routers only care about the network id, and use it to send the datagram to theappropriate gateway router,

the gateway router has information as to what other router to send the request.

Finally the last router usesthe host id to deliver the datagram

Subnet Masks are 32 bit numbers comparable to the IP address

## Subnet Masks

Address   9         . 100       . 100       . 100
in binary 0000 1001 . 0110 0110 . 0110 0110 . 0110 0110 
Mask      1111 1111 . 1111 1111 . 1111 1111 . 0000 0000

The part with ones is the subnet id.
The size of a subnet is defined by the subnet mask

A subnet mask of 255.255.255.0 has 255 possible hosts available (The size of the subnet is 255 - really it is only the 1-254)

A subnet mask of 255.255.255.224 
in binary 11111111 11111111 11111111 1110000
it has 5 bits of host space and 27 bits of space that is already defined to complete the 32 bit size)

It could also be referred to as 9.100.100.100/27

Subnet Masks use AND operators to determine that the address is in its network

#### CIDR
Address classes were the first  attempt at splitting the internet's IP space

Subnetting was introduced when it became clear that adress classes were insufficient.

With subnetting and clases there were only class A, B, or C
That is a lot of networks in a C (2^24 ip namespaces)
The sizing of the tables can be innappropriate
254 max hosts for a class C is insufficient. 
but class b can be too large, 

CIDR - Classless Inter Domain Routing
approach to expand classes
Demarcation Point - the point that a Network ends and another begins
In CIDR the network and subnet id are together.

CIDR abandons the concep pf classes

Networks can be 
  9.100.100.100
255.255.255.0  
  9.100.100.10 /24

The network mask tells us that the 9.100.100 is the only thing necessary to find a network id. CIDR allows for different size networks.

