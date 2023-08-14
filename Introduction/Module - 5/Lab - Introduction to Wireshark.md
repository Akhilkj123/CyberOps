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

![Uploading image.png…]()

