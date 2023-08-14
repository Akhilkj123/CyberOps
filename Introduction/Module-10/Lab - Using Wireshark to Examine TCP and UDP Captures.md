## Part 1: Identify TCP Header Fields and Operation Using a Wireshark FTP Session Capture
### Step 1: Start a Wireshark capture.
a. Start and log into the CyberOps Workstation VM. Open a terminal window and start Wireshark. The
ampersand (&) sends the process to the background and allows you to continue to work in the same
terminal.

b. Start a Wireshark capture for the enp0s3 interface

c. Open another terminal window to access an external ftp site. Enter ftp ftp.cdc.gov at the prompt. Log into the FTP site for Centers for Disease Control and Prevention (CDC) with user anonymous and no password.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d5adc465-44b1-4e69-81e9-77a81335c83a)

### Step 2: Download the Readme file
a. Locate and download the Readme file by entering the ls command to list the files.

b. Enter the command get Readme to download the file. When the download is complete, enter the
command quit to exit. (Note: If you are unable to download the file, you can proceed with the rest of the
lab.)

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/e8389c7d-0df7-48ab-bace-865cb5f5c8fd)

c. After the transfer is complete, enter quit to exit ftp

### Step 3: Stop the Wireshark capture.
### Step 4: View the Wireshark main window.
a. Wireshark captured many packets during the FTP session to ftp.cdc.gov. To limit the amount of data for analysis, apply the filter tcp and ip.addr == 198.246.117.106 and click Apply

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/189f119a-1fc8-42ab-b53f-8b1162ff45de)

### Step 5: Analyze the TCP fields.
#### SYN Message
- Source IP address: 192.168.1.7
- Destination IP address: 198.246.117.106
- Source port number: 36182
- Destination port number: 21
- Sequence number: 0
- Acknowledgment number: 0
- Header length: 40 bytes
- Window size: 29200
#### SYN-ACK Message
- Source IP address: 192.168.117.106
- Destination IP address: 198.246.1.7
- Source port number: 21
- Destination port number: 36182
- Sequence number: 0
- Acknowledgment number: 1
- Header length: 40 bytes
- Window size: 8192
- #### SYN Message
- Source IP address: 192.168.1.7
- Destination IP address: 198.246.117.106
- Source port number: 36182
- Destination port number: 21
- Sequence number: 1
- Acknowledgment number: 1
- Header length: 32 bytes
- Window size: 229

## Part 2: Identify UDP Header Fields and Operation Using a Wireshark TFTP Session Capture
### Step 1: Start Mininet and tftpd service.
a. Start Mininet. Enter cyberops as the password when prompted.

b. Start H1 and H2 at the mininet> prompt.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d2112aad-de3e-43dd-b0b0-235a88a5f8a0)

c. In the H1 terminal window, start the tftpd server using the provided script.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/77d7b4f1-7441-4288-bde5-8093bd1c1b52)

### Step 2: Create a file for tftp transfer
a. Create a text file at the H1 terminal prompt in the /srv/tftp/ folder.

b. Verify that the file has been created with the desired data in the folder.

c. Because of the security measure f or this particular tftp server, the name of the receiving file needs to exist
already. On H2, create a file named my_tftp_data.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8b712a9b-a0f6-4f23-8cad-71f5db0dd759)

### Step 3: Capture a TFTP session in Wireshark
a. Start Wireshark in H1.

b. From the Edit menu, choose Preferences and click the arrow to expand Protocols. Scroll down and
select UDP. Click the Validate the UDP checksum if possible check box and click OK.

c. Start a Wireshark capture on the interface H1-eth0.

d. Start a tftp session from H2 to the tftp server on H1 and get the file my_tftp_data.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/59550712-1f5e-436d-b58b-14a086816e17)

e. Stop the Wireshark capture. Set the filter to tftp and click Apply. Use the three TFTP packets to fill in the
table and answer the questions in the rest of this lab.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/afe39d53-16e8-45a0-ad61-b1e3589933fb)

- Source IP address: 10.0.0.11
- Destination IP address: 10.0.0.12
- Source port number: 52710
- Destination port number: 69
- UDP message length: 32
- UDP checksum: 0x1448


- Source IP address: 10.0.0.11
- Destination IP address: 10.0.0.12
- Source port number: 52710
- Destination port number: 69
- UDP message length: 32
- UDP checksum: 0x1448

