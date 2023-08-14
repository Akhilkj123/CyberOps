## Part 1: Examine the Header Fields in an Ethernet II Frame
### Step 1: Review the Ethernet II header field descriptions and lengths.
### Step 2: Examine Ethernet frames in a Wireshark capture.
### Step 3: Examine the Ethernet II header contents of an ARP request.

a) What is significant about the contents of the destination address field?
- It is significant because it's used to look up the corresponding MAC address to facilitate communication within the network.

b) Why does the PC send out a broadcast ARP prior to sending the first ping request?
- This process of sending a broadcast ARP request prior to the first ping request ensures that the PC can correctly address and route its network communication.

c) What is the MAC address of the source in the first frame?
- The MAC address of the source in the first frame (ARP request) is the MAC address of Device A(the device which needs the MAC Address), and the destination MAC address is the broadcast MAC address.

d) What is the Vendor ID (OUI) of the Source’s NIC?
- f4:8c:50

e) What portion of the MAC address is the OUI?
- The OUI (Organizationally Unique Identifier) is the first 24 bits (3 octets) of a MAC address

f) What is the Source’s NIC serial number?
- 62:62:6d

## Part 2: Use Wireshark to Capture and Analyze Ethernet Frames
### Step 1: Examine the network configuration of H3.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2d0516ac-31fc-496b-9e44-2ed90c664756)

a) What is the IP address of the default gateway for the host H3?
-_gateway

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ad0e0030-b91e-4bb3-8699-e4c0f746dc9a)

### Step 2: Clear the ARP cache on H3 and start capturing traffic on H3-eth0.
a)  In the terminal window for Node: H3, enter arp -n to display the content of the ARP cache.
b)  In the terminal window for Node: H3, open Wireshark and start a packet capture for H3-eth0 interface.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8c7dbbc0-3577-4e14-a833-d18decaa5634)

### Step 3: Ping H1 from H3.
a) From the terminal on H3, ping the default gateway and stop after send 5 echo request packets.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3cfac8c7-b99d-45fe-ab4e-1a0289b12cf8)

### Step 4: Filter Wireshark to display only ICMP traffic.
### Step 5: Examine the first Echo (ping) request in Wireshark

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/af75a8e7-dc54-4b30-95f8-4ecdc085ca2e)

a. In the Packet List pane (top section), click the first frame listed. You should see Echo (ping) request
under the Info heading. This should highlight the line blue.

b. Examine the first line in the Packet Details pane (middle section). This line displays the length of the
frame; 98 bytes in this example.

c. The second line in the Packet Details pane shows that it is an Ethernet II frame. The source and
destination MAC addresses are also displayed.

i) What is the MAC address of the PC’s NIC?
- 62:de:8b:d2:fa:79

ii) What is the default gateway’s MAC address?
- 33:33:00:00:00:02

d. You can click the arrow at the beginning of the second line to obtain more information about the Ethernet
II frame.

i) What type of frame is displayed?
- Frame 28: 70 bytes on wire (560 bits), 70 bytes captured (560 bits) on interface 0

e. The last two lines displayed in the middle section provide information about the data field of the frame.
Notice that the data contains the source and destination IPv4 address information.

i) What is the source IP address?
- 10.0.0.13

ii) What is the destination IP address?
- 10.0.0.1

f. You can click any line in the middle section to highlight that part of the frame (hex and ASCII) in the
Packet Bytes pane (bottom section). Click the Internet Control Message Protocol line in the middle
section and examine what is highlighted in the Packet Bytes pane.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/9373e2e0-5958-40cf-9baa-d3d0056f39d8)

g. Click the next frame in the top section and examine an Echo reply frame. Notice that the source and
destination MAC addresses have reversed, because this frame was sent from the default gateway router
as a reply to the first ping.

What device and MAC address is displayed as the destination address?
- 62:de:8b:d2:fa:79

### Step 6: Start a new capture in Wireshark.
a. Click the Start Capture icon to start a new Wireshark capture. You will receive a popup window asking if
you would like to save the previous captured packets to a file before starting a new capture. Click
Continue without Saving.

b. In the terminal window of Node: H3, send 5 echo request packets to 172.16.0.40

c. Stop capturing packets when the pings are completed.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b44c1085-23bc-424a-b3ea-335bdf25226f)

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/080ba301-880a-45ce-99e2-f0f0d0692775)

### Step 7: Examine the new data in the packet list pane of Wireshark
a. In the first echo (ping) request frame, what are the source and destination MAC addresses?
- Source: 62:de:8b:d2:fa:79
- Destination: 22:43:36:66:7b:44

b. What are the source and destination IP addresses contained in the data field of the frame?
- Source: 10.0.0.13
- Destination: 172.16.0.40

c. Why has the destination IP address changed, while the destination MAC address remained the same?
- The destination IP address in the original ICMP Echo Request remains constant, the destination IP address in the outer IP headers (used for routing) may change as the packet is forwarded through different routers on its way to the final destination. The destination MAC address remains consistent within the local network segment but changes as the packet is forwarded between network segments via routers.

#### Wireshark does not display the preamble field of a frame header. What does the preamble contain?
- The preamble serves the following purposes:Synchronization, Bit Alignment, Wake-Up Signal
