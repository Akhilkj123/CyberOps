- **File Server -** The file server stores corporate and user files in a central location.
- **Web Server -** The web server runs web server software that allows many computers to access web pages.
- **Email Server -** The email server runs email server software that enables emails to be sent and received.

 ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5223fa1f-3ade-4f35-9575-710ac7077fd2)

### What are Protocols?
- Network protocols specify many features of network communication such as

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a79eb169-58f7-4637-89a5-b25cba2ce194)

### The TCP/IP Protocol Suite

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a11458f1-0707-4fee-a22f-ea24457035ce)

#### Application Layer

- **DNS -** Domain Name System. Translates domain names such as cisco.com, into IP addresses.
Host Config
- **DHCPv4 -** Dynamic Host Configuration Protocol for IPv4. A DHCPv4 server dynamically assigns IPv4 addressing information to DHCPv4 clients at start-up and allows the addresses to be re-used when no longer needed.
- **DHCPv6 -** Dynamic Host Configuration Protocol for IPv6. DHCPv6 is similar to DHCPv4. A DHCPv6 server dynamically assigns IPv6 addressing information to DHCPv6 clients at start-up.
- **SLAAC -** Stateless Address Autoconfiguration. A method that allows a device to obtain its IPv6 addressing information without using a DHCPv6 server.
Email
- **SMTP -** Simple Mail Transfer Protocol. Enables clients to send email to a mail server and enables servers to send email to other servers.
- **POP3 -** Post Office Protocol version 3. Enables clients to retrieve email from a mail server and download the email to the client's local mail application.
- **IMAP -** Internet Message Access Protocol. Enables clients to access email stored on a mail server as well as maintaining email on the server.

#### File Transfer

- **FTP -** File Transfer Protocol. Sets the rules that enable a user on one host to access and transfer files to and from another host over a network. FTP is a reliable, connection-oriented, and acknowledged file delivery protocol.
- **SFTP -** SSH File Transfer Protocol. As an extension to Secure Shell (SSH) protocol, SFTP can be used to establish a secure file transfer session in which the file transfer is encrypted. SSH is a method for secure remote login that is typically used for accessing the command line of a device.
- **TFTP -** Trivial File Transfer Protocol. A simple, connectionless file transfer protocol with best-effort, unacknowledged file delivery. It uses less overhead than FTP.

#### Web and Web Service

- **HTTP -** Hypertext Transfer Protocol. A set of rules for exchanging text, graphic images, sound, video, and other multimedia files on the World Wide Web.
- **HTTPS -** HTTP Secure. A secure form of HTTP that encrypts the data that is exchanged over the World Wide Web.
- **REST -** Representational State Transfer. A web service that uses application programming interfaces (APIs) and HTTP requests to create web applications.

#### Transport layer

- **TCP -** Transmission Control Protocol. Enables reliable communication between processes running on separate hosts and provides reliable, acknowledged transmissions that confirm successful delivery.
- **UDP -** User Datagram Protocol. Enables a process running on one host to send packets to a process running on another host. However, UDP does not confirm successful datagram transmission.

#### Internet Layer

- **IPv4 -** Internet Protocol version 4. Receives message segments from the transport layer, packages messages into packets, and addresses packets for end-to-end delivery over a network. IPv4 uses a 32-bit address.
- **IPv6 -** IP version 6. Similar to IPv4 but uses a 128-bit address.
- **NAT -** Network Address Translation. Translates IPv4 addresses from a private network into globally unique public IPv4 addresses.
- **ICMPv4 -** Internet Control Message Protocol for IPv4. Provides feedback from a destination host to a source host about errors in packet delivery.
- **ICMPv6 -** ICMP for IPv6. Similar functionality to ICMPv4 but is used for IPv6 packets.
- **ICMPv6 ND -** ICMPv6 Neighbor Discovery. Includes four protocol messages that are used for address resolution and duplicate address detection.
- **OSPF -** Open Shortest Path First. Link-state routing protocol that uses a hierarchical design based on areas. OSPF is an open standard interior routing protocol.
- **EIGRP -** EIGRP - Enhanced Interior Gateway Routing Protocol. An open standard routing protocol developed by Cisco that uses a composite metric based on bandwidth, delay, load and reliability.
- **BGP -** Border Gateway Protocol. An open standard exterior gateway routing protocol used between Internet Service Providers (ISPs). BGP is also commonly used between ISPs and their large private clients to exchange routing information.

#### Network Access Layer
- **ARP -** Address Resolution Protocol. Provides dynamic address mapping between an IPv4 address and a hardware address.
- **Ethernet -** Defines the rules for wiring and signaling standards of the network access layer.
- **WLAN -** Wireless Local Area Network. Defines the rules for wireless signaling across the 2.4 GHz and 5 GHz radio frequencies.

- **Unicast** - A one-to-one delivery option is referred to as a unicast, meaning there is only a single destination for the message.
- **Multicast** - When a host needs to send messages using a one-to-many delivery option, it is referred to as a multicast.
- **Broadcast** - If all hosts on the network need to receive the message at the same time, a broadcast may be used. Broadcasting represents a one-to-all message delivery option.



![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/e7850a8a-c6eb-45a9-bdfa-80aa23510906)

### The OSI Reference Model

- **7 - Application -** The application layer contains protocols used for process-to-process communications.
- **6 - Presentation -** The presentation layer provides for common representation of the data transferred between application layer services.
- **5 - Session -** The session layer provides services to the presentation layer to organize its dialogue and to manage data exchange.
- **4 - Transport -** The transport layer defines services to segment, transfer, and reassemble the data for individual communications between the end devices.
- **3 - Network -** The network layer provides services to exchange the individual pieces of data over the network between identified end devices.
- **2 - Data Link-** The data link layer protocols describe methods for exchanging data frames between devices over a common media
- **1 - Physical-** The physical layer protocols describe the mechanical, electrical, functional, and procedural means to activate, maintain, and de-activate physical connections for a bit transmission to and from a network device.

### The TCP/IP Protocol Model
- **4 - Application -** Represents data to the user, plus encoding and dialog control.
- **3 - Transport -** Supports communication between various devices across diverse networks.
- **2 - Internet -** Determines the best path through the network.
- **1 - Network Access -** Controls the hardware devices and media that make up the network.

## Data Encapsulation
### Segmenting Messages

This leads to segmenting messages having two primary benefits:

- **Increases speed -** Because a large data stream is segmented into packets, large amounts of data can be sent over the network without tying up a communications link. This allows many different conversations to be interleaved on the network called multiplexing.
- **Increases efficiency -** If a single segment fails to reach its destination due to a failure in the network or network congestion, only that segment needs to be retransmitted instead of resending the entire data stream.


### Sequencing
- Each segment of the message must go through a similar process to ensure that it gets to the correct destination and can be reassembled into the content of the original message, as shown in the figure. TCP is responsible for sequencing the individual segments.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d74810ae-2bf1-4115-8282-281fc5ef578e)

### Protocol Data Units
- As application data is passed down the protocol stack on its way to be transmitted across the network media, various protocol information is added at each level. This is known as the encapsulation process. The form that a piece of data takes at any layer is called a protocol data unit (PDU). During encapsulation, each succeeding layer encapsulates the PDU that it receives from the layer above in accordance with the protocol being used.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b63e51fb-ff5b-4f1d-a501-622c9d2cee71)

### Three Addresses
- Network protocols require that addresses be used for network communication. Addressing is used by the client to send requests and other data to a server. The server uses the client’s address to return the requested data to the client that requested it. The OSI transport, network, and data link layers all use addressing in some form. The transport layer uses protocol addresses in the form of port numbers to identify network applications that should handle client and server data.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d48f9dc6-fd72-42c6-8fb0-0a0134241369)


