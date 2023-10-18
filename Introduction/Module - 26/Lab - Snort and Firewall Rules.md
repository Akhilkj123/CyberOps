## Part 1: Preparing the Virtual Environment
a. Launch Oracle VirtualBox and change the CyberOps Workstation for Bridged mode, if necessary.
Select Machine > Settings > Network. Under Attached To, select Bridged Adapter (or if you are using
WiFi with a proxy, you may need NAT adapter) and click OK.

b. Launch the CyberOps Workstation VM, open a terminal and configure its network by executing the
configure_as_dhcp.sh script.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/aa2aa322-1783-465b-87a5-526e98d1d62e)

c. Use the ifconfig command to verify CyberOps Workstation VM now has an IP address on your local
network. You can also test connectivity to a public webserver by pinging www.cisco.com. Use Ctrl+C to
stop the pings.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cbc02aee-6684-4f56-bb0d-6563dba22f36)

## Part 2: Firewall and IDS Logs
### Step 1: Real-Time IDS Log Monitoring
a. From the CyberOps Workstation VM, run the script to start mininet.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2b937a2e-402c-46ec-9327-5d0d0ee2cd22)

b. From the mininet prompt, open a shell on R1 using the command below:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f0316e7a-cc39-48d6-851a-ce05aea0d713)

The R1 shell opens in a terminal window with black text and white background. What user is logged into
that shell? What is the indicator of this?
- Root user
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0f0c0c45-a6c6-4968-abf4-3f7c62fd063f)

c. From R1’s shell, start the Linux-based IDS, Snort.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/22b07081-e0e8-4592-8bce-83f891c54ffa)

d. From the CyberOps Workstation VM mininet prompt, open shells for hosts H5 and H10.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/27f3c2d3-2377-49d6-a303-2cee48d3da29)

e. H10 will simulate a server on the Internet that is hosting malware. On H10, run the mal_server_start.sh
script to start the server.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/00ce05bd-16c6-4993-9fb8-81ce3d249e96)

f. On H10, use netstat with the -tunpa options to verify that the web server is running. When used as
shown below, netstat lists all ports currently assigned to services:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/78de3e54-d918-44cc-8bb6-2d9bd1afbf03)

g. In the R1 terminal window, an instance of Snort is running. To enter more commands on R1, open
another R1 terminal by entering the xterm R1 again in the CyberOps Workstation VM terminal window.
You may also want to arrange the terminal windows so that you can see and interact with each device.

h. In the new R1 terminal tab, run the tail command with the -f option to monitor the /var/log/snort/alert file
in real-time. This file is where snort is configured to record alerts

i. From H5, use the wget command to download a file named W32.Nimda.Amm.exe. Designed to
download content via HTTP, wget is a great tool for downloading files from web servers directly from the
command line.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d4b87f8c-218e-4686-8145-c696a2c78aa1)

What port is used when communicating with the malware web server? What is the indicator?
- 6666

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5cfb44dd-d9e8-45af-94b1-489b6d2fe740)

Was the file completely downloaded?
- Yes

Did the IDS generate any alerts related to the file download?
- No

j. As the malicious file was transiting R1, the IDS, Snort, was able to inspect its payload. The payload
matched at least one of the signatures configured in Snort and triggered an alert on the second R1
terminal window (the tab where tail -f is running). The alert entry is show below. Your timestamp will be
different:


### Step 2: Tuning Firewall Rules Based on IDS Alerts
a. In the CyberOps Workstation VM, start a third R1 terminal window.

b. In the new R1 terminal window, use the iptables command to list the chains and their rules currently in
use:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1d57f137-fef9-43d1-a521-984e1b1eb150)

What chains are currently in use by R1?
- Chain Forward

c. Connections to the malicious server generate packets that must transverse the iptables firewall on R1.
Packets traversing the firewall are handled by the FORWARD rule and therefore, that is the chain that will
receive the blocking rule. To keep user computers from connecting to the malicious server identified in
Step 1, add the following rule to the FORWARD chain on R1:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/07c0e6b7-15e6-42f0-adde-f5af2ff94bb5)

d. Use the iptables command again to ensure the rule was added to the FORWARD chain. The CyberOps
Workstation VM may take a few seconds to generate the output:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/2b2128e1-1214-471d-bcf3-d1ea78bf73ca)

e. On H5, try to download the file again:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/14d5db2d-848e-440e-a4b0-f3398e15e906)

Was the download successful this time? Explain.
- Yes

 ![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3a62030d-5949-41be-8887-94753f652bb1)

## Part 3: Terminate and Clear Mininet Process
a. Navigate to the terminal used to start Mininet. Terminate the Mininet by entering quit in the main
CyberOps VM terminal window.

b. After quitting Mininet, clean up the processes started by Mininet. Enter the password cyberops when
prompted.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b396b1df-3b15-4e16-ae5e-f4abe8eef059)
