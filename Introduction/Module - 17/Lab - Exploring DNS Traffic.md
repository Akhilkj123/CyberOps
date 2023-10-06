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
-  
