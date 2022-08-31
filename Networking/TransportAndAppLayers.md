# Transport and Application Layers

We network computers to get the programs running on those computers to communicate to each other

### Transport Layer
Allows traffic to be directed to specific network applications

### Application Layer
Allows these applications to communicate in a way they understand.

## Transport Layer
Include multiplexing and demultiplexing

### Multiplexing
Nodes on a network have the ability to direct traffic to many resources
### Demultiplexing
Receiving multiple signals and directing it to the proper receiving service

### Ports
a 16 bit numnber used to direct traffic to specific services
Handle Multiplexing and Demultiplexing

Server v Client. Different services listen to a port upon request.

If we have a web server at 10.1.1.100 it would be listening at 10.1.1.100:80 (called a socket number)
### **Default Ports**
- HTTP 		:80  - Hypertext Transfer Protocol
- HTTPS 	:443 - Hypertext Transfer Protocol Secure
- FTP		:21  - File Transfer Protocol
- SSH 		:22  - Secure Shell Protocol
- SMTP 		:25  - File Transfer Protocol
- IMAP		:143 - Internet Message Access Protocol
- RDP		:3389 - remote desktop protocol
- DNS 		:53   - Domain Name System
- DHCP		:67, 68 -  Dynamic Host Configuration Protocol


A single server can host multiple services running thanks to multiplexing


### TCP/UDP
