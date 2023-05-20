# ICMP Scanning
* Arish Madataly (2502049706) L4AC
* Leonardo Richie (2502005856) L4AC
* Raissa Azaria (2502005805) L4AC

## 1. Install GNS3
For this tutorial, we will be using GNS3 to make the testbed

**Refer to this link for a GNS3 installation tutorial:** <br />
https://staniswinata.notion.site/GNS3-Installation-on-Ubuntu-22-04-21556bbde7224b20825714f50cd085d9

## 2. Making a testbed
### Create a New Project
Open GNS3 and create a new project. You can do this by clicking on "File" -> "New Blank Project".

### Add Devices to the Project
Drag and drop the devices you want to use into the main GNS3 workspace.
The devices we use for this testbed are:
* 2 Kali Linux CLI
* 1 Router
* 1 NAT

### Connect Devices
Connect the devices together by dragging a cable from the output port of one device to the input port of another.


### Save and Run the Testbed 
Once you have finished configuring the devices in your testbed, save the project. Then, click on the "Play" button to start the simulation. This will open a terminal for each device

### Connect Devices & Configure Devices
-allow the router to connect to the internet by adding the 192.168.122.1 route to it
-confirm by attempting to ping 1.1.1.1
-assign an ip address to the first kali Linux CLI in eth0: in our example 192.168.14.2
-assign an ip address to the second kali Linux CLI in eth0: in our example 192.168.15.2
-allow these subnets into the router by adding them to its ip table
-make sure this work by pinging the 192.168.14.1 from CLI 1 and 192.168.15.1 from CLI 2
-add 192.168.15.1  as a default gateway via dev eth0 in CLI 2 and add 192.168.14.1  as a default gateway via dev eth0
-now to allow the internet to send back a reply, you need to add the subnets into your host machine
-so now if your network firewall allows it, you should be able to ping the internet
