# Data Link layer
Cable networks are still the most widely used methods to connect to the internet.

The ethernet is the most used protocol for Data Linking

The Web Browser has no need for information about how it is connected.

## Ethernet
started in 1980 which compares to what it is today

in the 80s, switchable hubs hadn't been connected. 

Collision domains only allowed for one device to connect at a time (multiple devices would collide and scramble the information)

Ethernet CSMA/CD to tell the network if there is data currently being sent. If a collision is detected, the computers will stop the transfer, and wait a random amount of time to resend the data. 

## MAC Adress
Globally Unique identifyers of a node in a network - Hexadecimal 0-9 a-f?

There are 2^48 possible mac addresses 

#### Organizationally Unique Identifyer OUI (first three octets of the address)
assigned to the [[hardware]] manufaturers

The rest is chosen by the manufacturer so long as it unique

### Transmission

#### Unicast
If the least significant bit in the first octet is 0 it means that ethernet is sent to only one device

#### Multicast
If the octet is set to one it will be sent to all devices, but the hardware MAC address decides whether to pick it up

#### Broadcast 
Uses Address Resolution Protocol to determine what to do with the signal

### The Ethernet Frame

#### Data Packets 
binary data sent accross a network link

All sections of an ethernet frame are mandatory

Preamble is 8 bytes and can be split into 3 sections
the first parts are set up to synchronize

then the Start Frame Deliver

A VLAN header 
if it is present it signifies that the ethernet is coming

A single physical network that operates like multiple LANs.

After is the payload of an Ethernet frame, everything that isnt a header.

Frame Checksequence. Checksum that the receiver uses to check for uncorrupted data

CRC used to verify the checksum on both ends. Ethernet only looks at the transport, not the verification. 


