### Part 1: Starting and Stopping the Routing and Remote Access service
You will explore what happens when a service is stopped and then started. In this part, you will use routing
and remote access service as the example service. This service allows the local device to become a router or
a remote access server.

a. Navigate to the Control Panel > Click Network and Sharing Center.
Note: If your Control Panel is set to View by: Category, change it to View by: Large icons or View by:
Small icons. This lab assumes that you are using one of these settings.

b. Click Change adapter settings in the left pane. Reduce the size of the Network Connections window
and leave it open.

c. Navigate to the Administrative Tools. (Navigate to the Control Panel > Click Administrative Tools)

d. In the Administrative Tools window, double-click the Performance Monitor icon.

e. In the Performance Monitor window, make sure Performance Monitor under Monitoring Tool heading in
the left pane is highlighted. Click the Freeze Display icon (pause button) to stop the recording.

![image](https://user-images.githubusercontent.com/65653010/236676851-b2fe497d-cb23-4f06-b91e-7d61e61e6cb9.png)

f. Right-click the graph and select Clear to clear the graph. Leave this window open.

g. Navigate to the Administrative Tools and select Services.

h. Expand the width of the Services window so you have a clear view of the content. Scroll down in the right
pane until you see the service Routing and Remote Access. Double-click Routing and Remote
Access.
![image](https://user-images.githubusercontent.com/65653010/236676942-fe5110c0-2ca5-4fee-a89e-2fa5a4f21248.png)

i. In the Routing and Remote Access Properties (Local Computer) window opens. In the Startup type
drop-down field, select Manual and then click Apply.
![image](https://user-images.githubusercontent.com/65653010/236677028-711dcb29-70a8-4ea0-a9e2-288f2aa9752f.png)

The Start button is now active. Do NOT click the Start button yet. Leave this window open.

j. Navigate to Performance Monitor window. Click the Unfreeze Display icon to start the recording.

k. Click the Routing and Remote Access Properties (Local Computer) window. To start the service, click
Start. A window with a progress bar opens.
![image](https://user-images.githubusercontent.com/65653010/236677428-0f3dcb42-e73f-4080-8944-48d4c591c4c2.png)

l. The Routing and Remote Access Properties (Local Computer) window now shows the Stop and
Pause button active. Leave this window open.

m. Navigate to Network Connections window. Press the function key F5 to refresh the content.

Question:What changes appear in the window after starting the Routing and Remote Access service?

![image](https://user-images.githubusercontent.com/65653010/236677535-c728bdd3-63f4-44db-bdee-cfd783ee5541.png)

n. Navigate to Routing and Remote Access Properties (Local Computer) window and click Stop. 
This was the page when Routing and Remote Access Properties
![image](https://user-images.githubusercontent.com/65653010/236677660-077689dd-163d-4fae-8def-6be76f1b52d1.png)
- Now the Incoming Network Connections got killed.
![image](https://user-images.githubusercontent.com/65653010/236677632-e29dc263-4600-4eac-9e30-dbf63ccfcfe1.png)

### Part 2: Working in the Computer Management Utility

The Computer Management is used to manage a local or remote computer. The tools in this utility are
grouped into three categories: system tools, storage, and services and applications.

a. Click Control Panel > Administrative Tools. Select Computer Management.

b. In the Computer Management window, expand the three categories by clicking on the arrow next to
System Tools.

c. Click the arrow next to Event Viewer then click the arrow next to Windows Logs. Select System.
![image](https://user-images.githubusercontent.com/65653010/236678256-78d04952-eb47-413b-a064-37f60f9a61e1.png)

d. The Event Properties window opens for the first event. Click the down arrow key to locate an event for
Routing and Remote Access. You should find four events that describe the order for starting and
stopping the Routing and Remote Access service.
![image](https://user-images.githubusercontent.com/65653010/236678358-7872b1f2-7052-496b-aca9-19fa13b7d48d.png)

What are the descriptions for each of the four events?
![image](https://user-images.githubusercontent.com/65653010/236678586-014744f1-2c45-4a9e-9fa8-03f7419afca4.png)
![image](https://user-images.githubusercontent.com/65653010/236678612-38b5431c-25a2-4f88-8349-bca92b4f998d.png)
e. Close all open windows.
### Part 3: Configuring Administrative Tools
For the rest of this lab, you will configure Advanced Administrative Tool features and monitor how this affects
the computer.

a. Click Control Panel > Administrative Tools > Performance Monitor. The Performance Monitor window
opens. Expand Data Collector Sets. Right-click User Defined, and select New > Data Collector Set

b. The Create new Data Collector Set window opens. In the Name field, type Memory Logs. Select the
Create manually (Advanced) radio button, and click Next.

c. In the What type of data do you want to include? window, check the Performance counter box then
click Next.

d. In the Which performance counters would you like to log? window, click Add.

e. From the list of available counters, locate and expand Memory. Select Available MBytes and click
Add>>.
![image](https://user-images.githubusercontent.com/65653010/236679033-093c43a9-0ce6-4507-b3a4-c226e98a46c4.png)

f. You should see the Available MBytes counter added in the right pane. Click OK.

g. Set the Sample interval field to 4 seconds. Click Next

h. In the Where would you like the data to be saved? screen, click Browse.

i. In the Browse For Folder window , select your (C:) drive which is Local Disk (C:). Select PerfLogs and
click OK.

j. The Where would you like the data to be saved? window opens with the directory information that you
selected in the previous step. Click Next.

k. In the Create the data collector set? screen, click Finish.

l. Expand User Defined and select Memory Logs. Right-click Data Collector01and select Properties.
![image](https://user-images.githubusercontent.com/65653010/236679226-e671b7f0-7955-4cf8-8517-f13e7ac96d98.png)

m. In the DataCollector01 Properties window, chhange the Log format: field to Comma Separated.
![image](https://user-images.githubusercontent.com/65653010/236679308-f2504c42-678c-4c38-8d1d-34fa839d8c17.png)

n. Click the File tab.

Question:What is the full path name to the example file?
![image](https://user-images.githubusercontent.com/65653010/236679371-39dd4d94-aea8-4d8c-8238-67a58b741c7b.png)


