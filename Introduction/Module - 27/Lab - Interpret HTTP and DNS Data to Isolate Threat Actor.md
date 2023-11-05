## Part 1: Investigate an SQL Injection Attack
### Step 1: Change the timeframe.
a. Start the Security Onion VM and login with the username analyst and the password cyberops.

b. Enter the sudo so-status command to check the status of services. The status for all the services should
be OK before starting your analysis. This could take a few minutes.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/4ce99ca3-91d0-45af-8516-0784afd043c6)

c. After you log in, open Kibana using the shortcut on the Desktop. Login with the username analyst and
the password cyberops.

d. In the upper-right corner of the window, click Last 24 hours to change the sample Time Range size.
Expand the time range to include the interesting alerts. An SQL injection attack took place in June 2020
so that is what you need to target. Select Absolute under Time Range and edit the From and To times to
include the entire month of June in 2020. Click Go to continue.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/f3bc61b9-4273-4f59-b9cc-5e7033bde08a)

e. Notice the total number of logs for the entire month of June 2020. Your dashboard should be similar to
that shown in the figure. Take a moment to explore the information that is provided by the Kibana
interface.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/117e224e-9e71-45a0-bdf4-821d3d3fbcc4)

### Step 2: Filter for HTTP traffic
a. Because the threat actor accessed data that is stored on a web server, the HTTP filter is used to select
the logs associated with HTTP traffic. Select HTTP under the Zeek Hunting heading, as shown in the
figure.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/a8bcd222-e2a0-46c7-919b-3dc171ee203b)

Scroll through the results and answer the following questions:

What is the source IP address?
- 209.165.200.227

What is the destination IP address?
- 209.165.200.235

What is the destination port number?
- 80

b. Scroll down to the HTTP Logs. The results list the first 10 results.
c. Expand the details of the first result by clicking the arrow that is next to the log entry timestamp. Note the
information that is available.

What is the timestamp of the first result?
- Jun 12th 2020, 21:30:09.445

What is the event type?
- bro_http

What is included in the message field? These are details about the HTTP GET request that was made by
the client to the server. Focus especially on the uri field in the message text.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/cb78dc08-6c84-42fb-9541-2b690c61f218)

What is the significance of this information?
- It provides the information of the pages visited, usernames and passwords also.

### Step 3: Review the results
a. Some of the information for the log entries is hyperlinked to other tools. Click the value in the alert _id
field of the log entry to get a different view on the event.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/216668cf-bc9d-4202-b271-6d1ecc19f009)

b. The result opens in a new web browser tab with information from capME!. capME! tab is a web interface
that allows you to view a pcap transcript. The blue text contains HTTP requests that are sent from the
source (SRC). The red text is responses from the destination web server (DST).

c. In the Log entry section, which is at the beginning of the transcript, notice the portion
username='+union+select+ccid,ccnumber,ccv,expiration,null+from+credit_cards+--+&password=
indicates that someone may have tried to attack the web browser using SQL injection to bypass
authentication. The keywords, union and select, are commands that are used in searching for
information in a SQL database. If the input boxes on a web page are not properly protected from illegal
input, threat actors can inject SQL search strings or other code that can access data contained in
databases that are linked to the web page.

d. Find for the keyword username in the transcript. Use Ctrl-F to open a search box. Use the down arrow
button in the search box to scroll through the occurrences that were found.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/3cd198fb-d42f-4aad-90a2-3ba8a541d9fd)

You can see where the term username was used in the web interface that is displayed to the user.
However, if you look farther down, something unusual can be found.

What do you see later in the transcript as regards usernames?
- There appears to be a list of usernames and passwords that are part of the information that was returned in response to the HTTP GET request.

Give some examples of a username, password, and signature that was exfiltrated.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/98018cf5-2d74-40fc-840f-b6c0ab9c553d)

e. Close the capME! tab and return to Kibana.

## Part 2: Analyze DNS exfiltration.
### Step 1: Filter for DNS traffic.
a. From the top of the Kibana Dashboard, clear any filters and search terms and click Home under the
Navigation section of the Dashboard. The Time period should still include June 2020.

b. In the same area of the Dashboard, click DNS in the Zeek Hunting section. Notice the DNS Log Count
metrics and Destination Port horizontal bar chart.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b5a3ef56-6d09-41f2-b90a-a484af99f068)

### Step 2: Review the DNS-related entries.
a. Scroll down the window. You can see the top DNS query types. You may see address records (A record),
IPv6 address Quad A records (AAAA), NetBIOS records (NB) and a pointer records for resolving the
hostnames (PTR). You can also see the DNS response codes.

b. By Scrolling further down, you can see a list of the top DNS clients and DNS Servers based on their
request and response counts. There is also a metric for number of DNS Phishing attempts, which are
also known as DNS pharming, spoofing, or poisoning.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/8f5fad1d-e14d-453f-847d-e5d6c523288e)

c. Scrolling further down the window you can see a listing of the top DNS queries by domain name. Notice
how some of the queries have unusually long subdomains attached to ns.example.com. The domain
example.com should be investigated further.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/295b300d-6483-4cdf-9b6a-05719ba20460)

d. Scroll back to the top of the window and enter example.com in the search bar to filter for example.com
and click Update. Note that the number of entries in the Log Count is smaller because the display is now
limited to requests to the example.com server.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/da85eb14-257a-4c90-ba56-4a93fe2e3636)

e. Locate information about the DNS - Client and DNS - Server.

Record the IP addresses of DNS client and server.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/73432990-8bbb-4cca-96f8-be84cdb63b97)

### Step 3: Determine the exfiltrated data.

a. Continue to scroll further down to see four unique log entries for DNS queries to example.com. Notice
how the queries are to suspiciously long subdomains attached to ns.example.com. The long strings of
numbers and letters in the subdomains look like text encoded into hexadecimal (0-9, a-f) rather than legitimate subdomain names. Click the Export: Raw download link to download the queries to an
external file. A CSV file is downloaded to the /home/analyst/Downloads folder.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/80563b4b-8b7e-4f1f-bf73-219ee8790c1b)

b. Navigate to the /home/analyst/Downloads folder. Open the file using a text editor, such as gedit. Edit
the file by deleting the text surrounding the hexadecimal portion of the subdomains, leaving only the
hexadecimal characters. Be sure to remove the quotes too. The contents of your file should look like the
information below. Save the edited text file with the original file name.


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/bb4fb897-1b6c-4edc-a3b2-8a3540829409)

c. In a terminal, use the xxd command to decode the text in the CSV file and save it to a file named
secret.txt. Use cat to output the contents of secret.txt to the console. 


![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/fac76251-2e1e-455a-9ee6-fb722ddb76db)

Were the subdomains from the DNS queries subdomains? If not, what is the text?
- The results indicate that the DNS requests were separate, coordinated requests containing hidden content.

What does this result imply about these particular DNS requests? What is the larger significance?
- It is possible that malware has is creating these requests by cycling through documents on the host and encoding their contents in hexadecimal and then creating DNS queries that use the hexadecimal strings as DNS subdomains. 
