## Part 1: Capture DNS Traffic
### Step 1: Download and install Wireshark.
### Step 2: Capture DNS traffic.
a. Start Wireshark. Select an active interface with traffic for packet capture.

b. Clear the DNS cache

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4035f9a5-c37d-40ce-91c6-dade8e647cf4)

c. At a command prompt or terminal, type nslookup enter the interactive mode.

d. Enter the domain name of a website. The domain name www.cisco.com is used in this example.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8ba726fb-3039-461c-9be1-019d3db53232)

e. Type exit when finished. Close the command prompt.

f. Click Stop capturing packets to stop the Wireshark capture.

## Part 2: Explore DNS Query Traffic
a. Observe the traffic captured in the Wireshark Packet List pane. Enter udp.port == 53 in the filter box and
click the arrow (or press enter) to display only DNS packets. 

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7e84edab-749f-4bdb-afad-8ec3d182a72a)

b. Select the DNS packet contains Standard query and A www.cisco.com in the Info column.

c. In the Packet Details pane, notice this packet has Ethernet II, Internet Protocol Version 4, User Datagram
Protocol and Domain Name System (query).

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f601374a-6088-4f78-bda8-4e8e50c0cfa2)

What are the source and destination MAC addresses? Which network interfaces are these MAC
addresses associated with?
- **Source MAC Address:-**  6c:5a:b0:0e:c6:f3
- **Destination MAC Address:-** 2a:7c:a2:7b:05:85
- Router(TP-Link)

e. Expand Internet Protocol Version 4. Observe the source and destination IPv4 addresses.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2c1d6efa-3f06-404e-bf7b-e9e41fcae3f1)

What are the source and destination IP addresses? Which network interfaces are these IP addresses
associated with?
- **Source IP Address:-** 192.168.142.61
-  **Destination IP Address:-** 192.168.142.166

f. Expand the User Datagram Protocol. Observe the source and destination ports.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/85c3b675-3e4c-46a6-a79e-2726f76bfe3e)

What are the source and destination ports? What is the default DNS port number?
- Source Port: 54249
- Destination Port: 53

g. Determine the IP and MAC address of the PC.
1) In a Windows command prompt, enter arp –a and ipconfig /all to record the MAC and IP addresses
of the PC.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/95415d1a-9391-4f6d-8688-916e3e5a9f9f)

Question:
Compare the MAC and IP addresses in the Wireshark results to the IP and MAC addresses. What is your
observation?
- The command prompt results and the captured Wireshark results shows the same value of MAC address and IP address.

h. Expand Domain Name System (query) in the Packet Details pane. Then expand the Flags and
Queries.

i. Observe the results. The flag is set to do the query recursively to query for the IP address to
www.cisco.com.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fd72ba08-8f8d-4393-9951-8cc22c53421f)

## Part 3: Explore DNS Response Traffic
a. Select the corresponding response DNS packet has Standard query response and A www.cisco.com
in the Info column.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/16e7138e-4666-4d19-909b-444d7a3f4789)

What are the source and destination MAC and IP addresses and port numbers? How do they compare to
the addresses in the DNS query packets?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d3cf3577-a29b-4ad4-a9ef-94d6c4a26e0b)
- These are the source and destination MAC and IP address and port numbers. The MAC addresses in DNS queries are related to the local network devices involved in the communication, while the IP addresses and port numbers are specific to the DNS query itself and the DNS server being queried.

b. Expand Domain Name System (response). Then expand the Flags, Queries, and Answers.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/eef7fca5-295d-41c5-b87f-a799bafc5bc9)

c. Observe the results.
Question:
Can the DNS server do recursive queries?
- Recursive DNS resolution is crucial for the efficient and accurate functioning of the DNS system because it allows clients to resolve domain names even if they don't have the complete DNS information themselves.

d. Observe the CNAME and A records in the Answers details.
Question:
How do the results compare to nslookup results?
- Non-authoritative server

### Reflection
1. From the Wireshark results, what else can you learn about the network when you remove the filter?
- We can also view the TCP results, ICMP results, ARP results

2. How can an attacker use Wireshark to compromise your network security?
- An attacker can misuse Wireshark to intercept sensitive data, passwords, or perform network analysis if they gain access to the network. Protect your network with encryption and access controls.
