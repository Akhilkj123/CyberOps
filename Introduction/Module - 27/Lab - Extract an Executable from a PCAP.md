## Part 1: Analyze Pre-Captured Logs and Traffic Captures
a. Change directory to the lab.support.files/pcaps folder, and get a listing of files using the ls –l command.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/78b86769-9920-403d-98c5-179f1df72d2f)

b. Issue the command below to open the nimda.download.pcap file in Wireshark.

c. The nimda.download.pcap file contains the packet capture related to the malware download performed
in a previous lab. The pcap contains all the packets sent and received while tcpdump was running.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0834f1c8-6a78-432b-89c8-cd58fd2dda4f)

d. Packets one through three are the TCP handshake. The fourth packet shows the request for the malware
file. Confirming what was already known, the request was done over HTTP, sent as a GET request.

e. Because HTTP runs over TCP, it is possible to use Wireshark’s Follow TCP Stream feature to rebuild
the TCP transaction. Select the first TCP packet in the capture, a SYN packet. Right-click it and choose
Follow > TCP Stream.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6b96e5b3-15fe-4fba-ac0d-d521dfbeb7eb)

f. Wireshark displays another window containing the details for the entire selected TCP flow.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/03d908eb-b604-44d9-9cc5-d6be808734dc)

What are all those symbols shown in the Follow TCP Stream window? Are they connection noise? Data?
Explain.
- The symbols shown in the "Follow TCP Stream" window represent the actual data transmitted in a TCP connection. They can include a mixture of printable text, non-printable characters, control characters, binary data, and protocol headers, but may also contain noise or encrypted/compressed data that's not immediately human-readable.

There are a few readable words spread among the symbols. Why are they there?
 - The presence of readable words among the symbols in network packet captures is a reflection of the diverse nature of network traffic.

g. Click Close in the Follow TCP Stream window to return to the Wireshark nimda.download.pcap file.

## Part 2: Extract Downloaded Files from PCAP

a. In that fourth packet in the nimda.download.pcap file, notice that the HTTP GET request was generated
from 209.165.200.235 to 209.165.202.133. The Info column also shows this is in fact the GET request for
the file.

b. With the GET request packet selected, navigate to File > Export Objects > HTTP, from Wireshark’s
menu.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0ce63aa1-a5be-4b92-89aa-fcd7b329e5ff)

c. Wireshark will display all HTTP objects present in the TCP flow that contains the GET request. In this
case, only the W32.Nimda.Amm.exe file is present in the capture. It will take a few seconds before the
file is displayed.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c3403363-1967-462a-a1a9-d357bc06ed8a)

Why is W32.Nimda.Amm.exe the only file in the capture?
- That was the only file downoaded in the HTTP traffic

d. In the HTTP object list window, select the W32.Nimda.Amm.exe file and click Save As at the bottom of
the screen.

e. Click the left arrow until you see the Home button. Click Home and then click the analyst folder (not the
analyst tab). Save the file there.

f. Return to your terminal window and ensure the file was saved

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cb313114-1120-4dae-b3f5-bb1640434f9c)

Was the file saved?
- Yes

g. The file command gives information on the file type. Use the file command to learn a little more about the
malware, as show below:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8d57233b-91a0-43c3-93eb-5350e352711e)

As seen above, W32.Nimda.Amm.exe is indeed a Windows executable file.

- Perform static analysis by examining the file's characteristics, such as file type, size, metadata, and strings, to gather initial insights into its potential threat.
