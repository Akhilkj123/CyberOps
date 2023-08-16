## Part 1: Capture and View HTTP Traffic
### Step 1: Start the virtual machine and log in.
### Step 2: Open a terminal and start tcpdump.
a. Open a terminal application and enter the command ip address.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/e8ed3dd6-53b7-4afb-912f-105d526730fe)

b. List the interfaces and their IP addresses displayed in the ip address output.

c. While in the terminal application, enter the command sudo tcpdump –i enp0s3 –s 0 –w httpdump.pcap. Enter the password cyberops for the user analyst when prompted.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/61e5c249-404d-41dc-839a-11aa7725c10f)

d. Open a web browser from the launch bar within the CyberOps Workstation VM. Navigate to http://www.altoromutual.com/login.jsp. Because this website uses HTTP, the traffic is not encrypted. Click the Password field to see the warning pop up.

e. Enter a username of Admin with a password of Admin and click Login.

f. Close the web browser

g. Return to the terminal window where tcpdump is running. Enter CTRL+C to stop the packet capture.

### Step 3: View the HTTP capture.
a. Click the File Manager icon on the desktop and browse to the home folder for the user analyst. Doubleclick the httpdump.pcap file, in the Open With dialog box scroll down to Wireshark and then click Open

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a244fe48-2910-4ecd-a88b-6fa1c31ce69f)

b. In the Wireshark application, filter for http and click Apply.

c. Browse through the different HTTP messages and select the POST message.


