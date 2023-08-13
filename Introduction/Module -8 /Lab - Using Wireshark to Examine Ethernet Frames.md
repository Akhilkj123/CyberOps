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

