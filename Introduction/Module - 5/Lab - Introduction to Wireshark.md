## Part 1: Install and Verify the Mininet Topology
### Step 1: Verify your PC’s interface addresses
### Step 2: Run the Python script to install the Mininet Topology.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dc3f7486-3ed6-43c0-8b80-755a7586a9b9)

### Step 3: Record IP and MAC addresses for H1 and H2.
- Node 1

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dbffedd6-2aa3-4a0a-b333-b8320a13e888)

- Node 2

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/9876a547-0a5c-4333-9555-f4b2bf4d0960)

## Part 2: Capture and Analyze ICMP Data in Wireshark
### Step 1: Examine the captured data on the same LAN.
a. On Node: H1, enter wireshark & to start Wireshark (The pop-up warning is not important for this lab.

b. In the Wireshark window, under the Capture heading, select the H1-eth0 interface. Click Start to capture
the data traffic.

c. On Node: H1, press the Enter key, if necessary, to get a prompt. Then type ping -c 5 10.0.0.12 to ping
H2 five times. The command option -c specifies the count or number of pings. The 5 specifies that five
pings should be sent. The pings will all be successful.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b28eec2c-776f-4154-ab23-0e8468dd98aa)

d. Navigate to the Wireshark window, click Stop to stop the packet capture.

e. A filter can be applied to display only the interested traffic.
Type icmp in the Filter field and click Apply.

f. If necessary, click the first ICMP request PDU frames in the top section of Wireshark. Notice that the
Source column has H1’s IP address, and the Destination column has H2’s IP address.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fb646851-d517-4274-9386-1edd7f05b959)

g. With this PDU frame still selected in the top section, navigate to the middle section. Click the arrow to the
left of the Ethernet II row to view the Destination and Source MAC addresses.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/03438db9-d1a7-42f3-b8e3-107f1181b393)

i) Does the Source MAC address match H1’s interface?
- ba:fb:b5:8b:3a:2d

ii) Does the Destination MAC address in Wireshark match H2’s MAC address?
- aa:ad:de:af:6a:19

### Step 2: Examine the captured data on the remote LAN.
a. At the mininet prompt, start terminal windows on hosts H4 and R1.

b. At the prompt on Node: H4, enter ip address to verify the IPv4 address and record the MAC address. Do
the same for the Node: R1.

c. Start a new Wireshark capture on H1 by selecting Capture > Start. You can also click the Start button or
type Ctrl-E Click Continue without Saving to start a new capture.

d. H4 is a simulated remote server. Ping H4 from H1. The ping should be successful

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/53bafed9-c567-495c-a242-135e5f8406ec)

e. Review the captured data in Wireshark. Examine the IP and MAC addresses that you pinged. Notice that
the MAC address is for the R1-eth1 interface. List the destination IP and MAC addresses.
- IP Address: 10.0.0.11 and MAC Address: 8a:1b:93:91:25:dd

f. In the main CyberOps VM window, enter quit to stop Mininet.

g. To clean up all the processes that were used by Mininet, enter the sudo mn -c command at the prompt.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c775dfb6-387c-488b-b2ec-d1629bfaaaa0)
