### Part 1: Servers
#### Step 1: Access the command line.
a. Log on to the CyberOps Workstation VM as the analyst, using the password cyberops. The account
analyst is used as the example user account throughout this lab.

b. To access the command line, click the terminal icon located in the Dock, at the bottom of VM screen. The
terminal emulator opens.
#### Step 2: Display the services currently running.
a. Use the ps command to display all the programs running in the background:
[analyst@secOps ~]$ sudo ps –elf

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/b1101d3a-d194-45af-a5ef-c899dbdf8cdd)

- Running the ps command as root (superuser) allows us to view all processes running on the system, regardless of the user who started them.

b. In Linux, programs can also call other programs. The ps command can also be used to display such
process hierarchy. Use –ejH options to display the currently running process tree after starting the nginx
webserver with elevated privileges.
Note: The process information for the nginx service is highlighted. Your PID values will be different.

[analyst@secOps ~]$ sudo /usr/sbin/nginx

[analyst@secOps ~]$ sudo ps –ejH

c. In the terminal window, type netstat.

[analyst@secOps ~]$ netstat

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/7e722d88-49c5-4745-9d63-5ba8cc0baf5a)

d. Use netstat with the –tunap options to adjust the output of netstat. Notice that netstat allows multiple
options to be grouped together under the same “-“ sign.
The information for the nginx server is highlighted.

[analyst@secOps ~]$ sudo netstat -tunap

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/0ff173e6-ff2d-4f2e-98f7-cba4794ee25b)

What is the meaning of the –t, -u, –n, –a and –p options in netstat

- t: This option displays only TCP connections.

- u: This option displays only UDP connections.

- n: This option displays network addresses as numerical values instead of hostnames.

- a: This option displays both listening and non-listening sockets.

- p: This option displays the process ID (PID) and name of the program that is using each socket.
    
The order of the options is generally not important for the netstat command, as long as each option is preceded by a (-) or (--). However, some versions of netstat may have specific requirements for the order of certain options or may interpret options differently depending on their order.

Based on the netstat output shown in item (d), what is the Layer 4 protocol, connection status, and PID
of the process running on port 80?

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/60bb3b54-3716-4dcb-acec-9b4f9da5f89f)

- sshd PID-299, 

While port numbers are just a convention, can you guess what kind of service is running on port 80 TCP?

- Yes, port numbers are assigned to specific services as a convention to make it easier for clients to connect to the correct service on a server. Port 80 is the well-known port number used for HTTP (Hypertext Transfer Protocol) traffic, which is the protocol used for transmitting web pages and other web content over the internet. 

 e. [analyst@secOps ~]$ sudo ps -elf | grep 39

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/5e326641-87ee-4231-bef0-581718fd4961)

What is nginx? What is its function?

- Nginx  is a popular open-source web server software. It's designed to be fast, lightweight, and scalable and is often used as a reverse proxy server, load balancer, and HTTP cache.
As a web server, Nginx is responsible for serving web content over the internet in response to client requests. When a user makes a request to access a website or web application hosted on a server, the request is sent to Nginx, which then retrieves the requested content from the server and sends it back to the user's web browser. Nginx is capable of serving static and dynamic content, such as HTML files, images, videos, and web applications written in various programming languages, such as PHP, Python, and Ruby.

The second line shows that process 396 is owned by a user named http and has process number 395 as
its parent process. What does that mean? Is this common behavior?
- The line indicates that process number 396 is the "master" process of the nginx server, and it's owned by a user named http. The nginx master process is responsible for managing and coordinating the worker processes that handle incoming requests. In this case, the master process is listening on port 80 for incoming connections.

Why is the last line showing grep 395?
- The pipeline is used to filter the output of the netstat command to show only the information related to a specific process or port.

### Part 2: Using Telnet to Test TCP Services

a. [analyst@secOps ~]$ telnet 127.0.0.1 80

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/6faef825-8852-4d72-a2b0-410df5115283)

b. Press a few letters on the keyboard. Any key will work. After a few keys are pressed, press ENTER.
Below is the full output, including the Telnet connection establishment and the random keys pressed
(fdsafsdaf, this case):

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/392a4819-a0c8-4f1a-a003-0f7c83fae1d9)

Thanks to the Telnet protocol, a clear text TCP connection was established, by the Telnet client, directly
to the nginx server, listening on 127.0.0.1 port 80 TCP. This connection allows us to send data directly to
the server. Because nginx is a web server, it does not understand the sequence of random letters sent to
it and returns an error in the format of a web page.
Why was the error sent as a web page?

- The error was most likely sent as a web page because the Telnet client sent a sequence of random letters that were not recognized by the nginx web server. When a web server receives a request that it cannot understand, it typically responds with an HTTP error code and an error page in HTML format.

c. Looking at the netstat output presented earlier, it is possible to see a process attached to port 22. Use
Telnet to connect to it.
Port 22 TCP is assigned to SSH service. SSH allows an administrator to connect to a remote computer
securely.

![image](https://github.com/Akhilkj123/CyberOps/assets/65653010/09c17936-d349-4e23-900b-5170cabf5c5d)

Port 68 is used by the Bootstrap Protocol (BOOTP) and the Dynamic Host Configuration Protocol (DHCP) client service. It is typically used to automatically assign IP addresses to network clients.

- Reflection Questions

1. What are the advantages of using netstat?

Netstat is a useful command-line tool that provides valuable information about network connections and network statistics. Here are some advantages of using netstat:
- Identify network connections: Netstat can be used to identify which network connections are currently active and which network protocols are in use (TCP, UDP, etc.). This information is useful for troubleshooting network issues or monitoring network activity.
- Identify listening ports: Netstat can be used to identify which network services are listening on which ports. This information is useful for identifying potential security risks or for troubleshooting connectivity issues.
- Display network statistics: Netstat can display network statistics such as the number of bytes sent and received, the number of packets transmitted and received, and errors encountered. This information can be useful for monitoring network performance and identifying potential issues.

2. What are the advantages of using Telnet? Is it safe?

Telnet is a protocol that enables users to remotely access and manage network devices, servers, and services. It is a simple and lightweight protocol that has been widely used in the past but is now being replaced by more secure protocols like SSH (Secure Shell).

Advantages of using Telnet:
- Simple to use: Telnet is a simple protocol that is easy to use. It allows users to connect to remote devices and services using a simple command-line interface.
- Cross-platform compatibility: Telnet is a cross-platform protocol that can be used on a wide range of operating systems and devices.
- Network troubleshooting: Telnet can be used to troubleshoot network issues by enabling users to connect to network devices and services and test connectivity and functionality.
- Remote management: Telnet can be used to remotely manage network devices and services, which can be particularly useful for managing devices located in remote or hard-to-reach locations.
