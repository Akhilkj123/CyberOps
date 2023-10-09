## Part 1: Exploring Nmap
a. Start CyberOps Workstation VM.

b. Open a terminal.

c. At the terminal prompt, enter man nmap.
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c84261a5-9da1-4707-b8bb-cb8d4a133a68)

What is Nmap? What is nmap used for?
- Nmap, short for Network Mapper, is a free and open source tool used for vulnerability checking, port scanning and, of course, network mapping.

d. While in the man page, you can use the up and down arrow keys to scroll through the pages. You can
also press the space bar to forward one page at a time.
To search for a specific term or phrase use enter a forward slash (/) or question mark (?) followed by the
term or phrase. The forward slash searches forward through the document, and the question mark
searches backward through the document. The key n moves to the next match.
Type /example and press ENTER. This will search for the word example forward through the man page.

e. In the first instance of example, you see three matches. To move to the next match, press n.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/ed63c6ec-6538-44f1-ac5d-cfea238f7c88)

What is the nmap command used?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8f356028-5639-4403-a42f-871d3da0ff55)

Use the search function to answer the following questions.
Questions:
What does the switch -A do? 
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4e92d6b5-17a8-4b65-be0f-2b9799bd41ca)

What does the switch -T4 do?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/497dd443-fa8b-4e15-bd7a-ebc49681f0dc)

## Part 2: Scanning for Open Ports
### Step 1: Scan your localhost.
a. If necessary, open a terminal on the VM. At the prompt, enter nmap -A -T4 localhost. Depending on your
local network and devices, the scan will take anywhere from a few seconds to a few minutes.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b1db78a1-8ddb-4a2e-b98b-aeb461231a5d)

b. Review the results and answer the following questions.
Questions:
Which ports and services are opened?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1d556126-3d9a-4281-8527-6c693afcd595)

### Step 2: Scan your network.
a. At the terminal command prompt, enter ip address to determine the IP address and subnet mask for this
host. For this example, the IP address for this VM is 10.0.2.15 and the subnet mask is 255.255.255.0.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7a1b96f7-4754-4204-be64-3a32fdd98a8c)

Which network does your VM belong to?
- NAT network

b. To locate other hosts on this LAN, enter nmap -A -T4 network address/prefix. The last octet of the IP
address should be replaced with a zero. For example, in the IP address 10.0.2.15, the .15 is the last
octet. Therefore, the network address is 10.0.2.0. The /24 is called the prefix and is a shorthand for the
netmask 255.255.255.0. If your VM has a different netmask, search the internet for a “CIDR conversion
table” to find your prefix. For example, 255.255.0.0 would be /16. The network address 10.0.2.0/24 is
used in this example 

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4dcfde1a-29cc-4662-8db0-481011db62ad)

How many hosts are up?
- 1 host up

From your Nmap results, list the IP addresses of the hosts that are on the same LAN as your VM. List
some of the services that are available on the detected hosts.
- IP addresses:- 10.0.2.15
- Services - ftp, ssh

### Step 3: Scan a remote server.
a. Open a web browser and navigate to scanme.nmap.org. Please read the message posted.
Question:
What is the purpose of this site?
- The set up this machine to help folks learn about Nmap and also to test and make sure that their Nmap installation (or Internet connection) is working properly. 

b. At the terminal prompt, enter nmap -A -T4 scanme.nmap.org.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d6adbae3-e813-486f-9c44-e8b5f48e5b53)

c. Review the results and answer the following questions.

Which ports and services are opened?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/efff8574-dcd2-4715-a63f-92413cf63614)

Which ports and services are filtered?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/dca8e831-826d-4397-9732-46364b1c0a7a)

What is the IP address of the server?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4844c097-225c-495e-9edb-df38be674a34)

What is the operating system?
- Linux

Nmap is a powerful tool for network exploration and management. How can Nmap help with network security?
How can Nmap be used by a threat actor as a nefarious tool?
- Threat actors misuse Nmap for reconnaissance, vulnerability scanning, and evading detection during attacks.
