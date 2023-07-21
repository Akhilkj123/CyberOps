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

#### Name System

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