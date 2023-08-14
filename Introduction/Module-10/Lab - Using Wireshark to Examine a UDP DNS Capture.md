## Part 1: Record VM's IP Configuration Information
a. Your CyberOps Workstation VM network settings should be set to bridged adapter. To check your network settings go to: Machine > Settings, select Network, the tab Adapter 1, Attached to: Bridged Adapter.

b. Open a terminal in the VM. Enter ifconfig at the prompt to display interface information. If you do not have an IP address on your local network, run the following command in the terminal:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/9f5d692c-1431-4edd-a62e-9020a34c65da)
![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6be36a94-4c82-4b06-a23c-079e29cfab79)

c. At the terminal prompt, enter cat /etc/resolv.conf to determine the DNS server.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/eaaf52f8-8486-46bb-9c69-a3f843db31e3)

d. At the terminal prompt, enter netstat -rn to display the IP routing table to the default gateway IP address.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/69920c83-8411-4a15-9026-b33051da7caa)

## Part 2: Use Wireshark to Capture DNS Queries and Responses
a. In the terminal window, start Wireshark and click OK when prompted.

b. In the Wireshark window, select and double-click enp0s3 from the interface list.

