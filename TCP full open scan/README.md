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
Configuration of the test bed:
1. Allow the router to connect to the internet by adding the 192.168.122.1 route to it
2. Confirm by attempting to ping 1.1.1.1
3. Assign an ip address to the first kali Linux CLI in eth0: in our example 192.168.10.2
4. Assign an ip address to the second kali Linux CLI in eth0: in our example 192.168.20.2
5. Allow these subnets into the router by adding them to its ip table
6. Make sure this work by pinging the 192.168.10.1 from CLI 1 and 192.168.20.1 from CLI 2
7. Add 192.168.15.1  as a default gateway via dev eth0 in CLI 2 and add 192.168.10.1  as a default gateway via dev eth0
8. Now to allow the internet to send back a reply, you need to add the subnets into your host machine
9. So now if your network firewall allows it, you should be able to ping the internet

### list of command for nmap:
-nmap -T4 -sT -p80 192.168.20.2 --> to scan port 80 with TCP full scan <br />
-iptables -F --> flush iptables <br />
-iptables -X --> erase user-defined chain  <br />
### Testing the nmap:
-open port 80 on target machine by running a web server: python -m SimpleHTTPServer 80 <br />
-listen to that port using nmap <br />
-capture the traffic with wireshar <br />

## Documentation
### Topology
<img src="https://cdn.discordapp.com/attachments/1109466596738613291/1109845230502547617/image.png">

## Before IP table config
<img src="https://cdn.discordapp.com/attachments/1109466596738613291/1109857218653868133/image.png">

## After IP table config
<img src ="https://cdn.discordapp.com/attachments/1109466596738613291/1109855577540136980/image.png">

## Result of nmap before iptable
<img src ="https://cdn.discordapp.com/attachments/1109466596738613291/1109902015884173372/image.png">

## Result of nmap after iptable 
<img src ="https://cdn.discordapp.com/attachments/1109466596738613291/1109902285611483147/image.png">
        
