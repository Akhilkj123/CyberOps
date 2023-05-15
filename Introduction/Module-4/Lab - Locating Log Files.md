### Part 1: Log File Overview
#### Step 1: Web server log file example
a. Use the cat command below to list a web server sample log file. The sample file is located at /var/log:

[analyst@secOps ~]$ cat /var/log/logstash-tutorial.log

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/93f10422-4ace-4892-b410-645fccbd5a7e)

 Explain why the output of the cat command is in a different format than the single entry shown in item.
 - The 'cat' command if being given to a file it lists the contents of a file and if being given to a directory it lists the number of files present in the directory.

#### Step 2: Operating system log file example
a. [analyst@secOps ~]$ sudo more /var/log/messages

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/06b73327-49da-4ad9-ae8b-9a89147bb1ad)

Notice that the events listed above are very different from the web server events. Because the operating
system itself is generating this log, all recorded events are in relation to the OS itself.

b. If necessary, enter Ctrl + C to exit out of the previous command.

c. Log files are very important for troubleshooting. Assume that a user of that specific system reported that
all network operations were slow around 4:20 am on May 19.

Question:
Can you find evidence of that in the log entries shown above? If so, in what lines? Explain.

- To easily find the specific time mentioned, the below listed command can be given:

cat /etc/log/messages | grep "May 19 04:2"
- This command can help in finding the information of the specific time.

### Part 2: Locating Log Files in Unknown Systems
a. When working with new software, the first step is to look at the documentation. It provides important
information about the software, including information about its log files. Use the man command to display
the nginx manual page:

[analyst@secOps ~]$ man nginx

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/796d91db-4da9-4aa4-96b1-0dd04f6eb28f)

b. Scroll down the page to locate the nginx logging section. The documentation makes it clear that nginx
supports logging, with the location of its log files defined at compilation time.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b6f0578f-a44d-483e-a82b-f68e0232ba70)

c. The manual page also contains information on the files used by nginx. Scroll down further to display the
nginx operating files under the Files section:

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/1fd97d0d-b499-43a5-b802-632a121468f9)

d. Before looking for nginx files, use the ps and the grep commands to ensure nginx is running in the VM.

Note: Use man to learn more about ps and grep commands.

[analyst@secOps ~]$ ps ax | grep nginx

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/aad45cfb-c55b-4e9b-8ea0-4d0801482e2d)

e. [analyst@secOps ~]$ ls /etc/

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6daa336b-96e3-4f40-a77f-b802bdd00cd0)

f. Notice the nginx folder under /etc in the output above. Using ls again, we find a number of files, including
one named nginx.conf.

[analyst@secOps ~]$ ls -l /etc/nginx/

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/88ffc613-a3b3-4a24-9848-98ac7f4c9900)

g. Use the cat command to list the contents of /etc/nginx/nginx.conf. You can also use more or less to view
the file and nano or SciTE to edit it. These tools make it easier to navigate through long text files (only
the output of cat is displayed below).

[analyst@secOps ~]$ cat /etc/nginx/nginx.conf

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/873ed657-abe3-48fb-9a7d-eb456624f236)

h. A quick look at the configuration file reveals that it is an nginx configuration file. Because there is no direct
mention to the location of nginx log files, it is very likely that nginx is using default values for it. Following
the convention of storing log files under /var/log, use the ls command to list its contents:

[analyst@secOps ~]$ ls -l /var/log/

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/01c7fe45-e348-4131-aa26-e44fc1946a14)

i. As shown above, the /var/log directory has a subdirectory named nginx. Use the ls command again to
list the contents of /var/log/nginx.

Note: Because the /var/log/nginx belongs to the http user, you must execute ls as root by preceding it
with the sudo command.

[analyst@secOps ~]$ sudo ls -l /var/log/nginx

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/47a043b5-fb08-4bc7-8691-972081bc2582)

### Part 3: Monitoring Log Files in Real Time

#### Step 1: Using the tail command
The tail command displays the end of a text file. By default, tail will display the last ten (10) lines of a text file.
Note: If you do not see any log entries, navigate to 127.0.0.1 in a web browser and refresh the page a few
time.

a. Use the tail command to display the end of the /var/log/nginx/access.log.

[analyst@secOps ~]$ sudo tail /var/log/nginx/access.log

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7e93d80c-1955-4c9b-ab7e-dd6d7e92b4cc)

b. Use the –n option to specify how many lines from the end of a file, tail should display.

[analyst@secOps ~]$ sudo tail -n 5 /var/log/nginx/access.log

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/056d8be3-523e-4732-b0c3-20d2ef315abe)

c. You can use the tail command with the -f option to monitor the nginx access.log in real-time. Short for
follow, -f tells tail to continuously display the end of a given text file. In a terminal window, issue tail with
the –f option:

[analyst@secOps log]$ sudo tail -f /var/log/nginx/access.log

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/c9dfaa03-544e-4b2a-b2ba-f182a3802972)

d. Because the log file is being updated by nginx, we can state with certainty that /var/log/acess.log is in fact
the log file in use by nginx.

e. Enter Ctrl + C to end the tail monitoring session.

#### Step 2: BONUS TOOL: Journalctl

a. In a terminal window in the CyberOps Workstation VM, issue the journalctl command with no options to
display all journal log entries (it can be quite long):

[analyst@secOps ~]$ journalctl

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/d8af1f74-566a-4945-9275-f025db89be93)

How can you run journalctl and see all log entries?

- This can be done by using '**sudo journalctl --no-pager**'

b. journalctl includes options to help in filtering the output. Use the –b option to display boot-related log
entries:

[analyst@secOps ~]$ sudo journalctl -b

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/990499fc-9835-4089-b9d7-b2cd9502d359)

c. To see entries related to the last boot, add the -1 to the command above. To see entries related to the
two last boots, add the -2 option.

[analyst@secOps ~]$ sudo journalctl –b -2






