## Service Configuration Files

- cat /etc/nginx/nginx.conf - This command shows all the configuration files for Nginx(HTTP and Reverse Proxy Server), which is a lightweight webserver of Linux.
- cat /etc/ntp.conf - This command shows the configuration file for Network Time Protocol
- cat /etc/snort/snort.conf - This command shows the configuration file for Snort, Linux-based Intrusion Detection System(IDS)



## Monitoring Service Logs
- /var/log/messages - Generic computer activity logs
- /var/log/auth.log - It contains all authentication informations of all Ubuntu and Linux-Servers
- /var/log/secure - Used by RedHat and CentOS to for the same purpose of authentication. It can be also used to detect sudo logins,SSH logins
- /var/log/boot.log - Contains boot information
- /var/log/dmesg - Information related to hardware and their drivers are stored here
- /var/log/kern.log - Contains information logged by kernal
- /var/log/cron - Is a service to schedule automated tasks in Linux and this directory stores the information of it.
- /var/log/mysqld.log - This is a MySQL file. All the information related to mysql. 


## The File System Types in Linux
- ext2 (second extended file system) - was the default file system in several major Linux Distribution.
- ex3 (third extended file system) - is a journaled file system designed to improve the existing ex2 file system. The maximum file size in ex3 is 32TB.
- ex4 (fourth extended file system) - designed as a successor of ex2 and ex3 based on the extensions. It increases supported file sizes.
- NFS (Network File System) - is a network-based file system, allowing file access over the network. It is an open standard which allows anyone to implement it.
- CDFS (Compact Disc File System) - was created specifically for optical disk media.
- Swap File System -  swap file system is used by Linux when it runs out of RAM. It is a swap partition that does not have a specific file system, but it is relevant to the file system discussion. 
- 
