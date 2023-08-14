
## Part 1: Prepare the Hosts to Capture the Traffic
a. Start the CyberOps VM. Log in with username analyst and the password cyberops.

b. Start Mininet.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/75d2a039-11e0-4fe8-8d89-4df9efe32fcf)

c. Start host H1 and H4 in Mininet.
d. Start the web server on H4

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/992d2894-a899-4fe3-8c18-e5976860fef2)

e. For security purposes, you are not able to run Firefox from the root user account. On host H1, use the
switch user command to switch from the root user to the analyst user account:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0fac5f52-cd9f-4b3a-a68f-e207b8d760d7)

f. Start the web browser on H1. This will take a few moments.
g. After the Firefox window opens, start a tcpdump session in the terminal Node: H1 and send the output to
a file called capture.pcap. With the -v option, you can watch the progress. This capture will stop after
capturing 50 packets, as it is configured with the option -c 50.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a3aef39c-2dd9-4fb0-a3a1-3108bf9a8e05)

h. After the tcpdump starts, quickly navigate to 172.16.0.40 in the Firefox web browser.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/40e137fc-59f3-477c-85c2-04ee85e8bdbd)

## Part 2: Analyze the Packets using Wireshark
### Step 1: Apply a filter to the saved capture.
a. Press ENTER to see the prompt. Start Wireshark on Node: H1. Click OK when prompted by the warning
regarding running Wireshark as superuser.

b. In Wireshark, click File > Open. Select the saved pcap file located at /home/analyst/capture.pcap.

c. Apply a tcp filter to the capture. In this example, the first 3 frames are the interested traffic.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fdc87bb3-8941-4742-a9c2-9672e8eacaef)

### Step 2: Examine the information within packets including IP addresses, TCP port numbers, and TCP control flags.
a. In this example, frame 1 is the start of the three-way handshake between the PC and the server on H4. In
the packet list pane (top section of the main window), select the first packet, if necessary.

b. Click the arrow to the left of the Transmission Control Protocol in the packet details pane to expand it and
examine the TCP information. Locate the source and destination port information.

c. Click the arrow to the left of the Flags. A value of 1 means that flag is set. Locate the flag that is set in
this packet.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/923aecaa-7130-4e29-b235-29af4b53080c)

i) What is the TCP source port number?
- 37886

ii) How would you classify the source port?
- This is a 16 bit field that specifies the port number of the sender.

iii) What is the TCP destination port number?
- 80

iv) How would you classify the destination port?
- This is a 16 bit field that specifies the port number of the receiver.

v) Which flag (or flags) is set?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f88da944-7d95-4470-821d-7d78e6dfab40)

vi) What is the relative sequence number set to?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f154ff1d-9ea3-4f34-a3a9-b7c8da940141)

d. Select the next packet in the three-way handshake. In this example, this is frame 2. This is the web server
replying to the initial request to start a session.

i) What are the values of the source and destination ports?
- Source: 80 and Destination: 37886

ii) Which flags are set?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/48eac436-255a-4611-bdd8-054f1fd31965)

iii) What are the relative sequence and acknowledgment numbers set to?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2df7f1f6-0426-46e4-a4e8-2777b62a8f00)

e. Finally, select the third packet in the three-way handshake.

i) Which flag (or flags) is set?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d5b52ce2-dabb-48d9-acb2-13ed31e430b7)

## Part 3: View the packets using tcpdump
a. Open a new terminal window, enter man tcpdump. Note: You may need to press ENTER to see the prompt.

b. In the same terminal, open the capture file using the following command to view the first 3 TCP packets
captured:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/76292bdb-ad9a-4067-92f0-b7415436a0ef)

c. Navigate to the terminal used to start Mininet. Terminate the Mininet by entering quit in the main
CyberOps VM terminal window.

d. After quitting Mininet, enter sudo mn -c to clean up the processes started by Mininet. Enter the password
cyberops when prompted.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/435584bc-2ba5-46e1-b88d-777b5a55be7d)

