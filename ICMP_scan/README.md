# ICMP Scanning

## 1. Install GNS3
For this tutorial, we will be using GNS3 to make the testbed

**Refer to this link for a GNS3 installation tutorial:** <br />
https://mariaclarinblog.notion.site/Computer-Networks-550616572d154cb68cceead03c482703 
https://compnetwilliambinus.blogspot.com/2023/04/tutorial-gns3-in-ubuntu-2204.html

## 2. Making a testbed
### Create a New Project
Open GNS3 and create a new project. You can do this by clicking on "File" -> "New Blank Project".

### Add Devices to the Project
Drag and drop the devices you want to use into the main GNS3 workspace.
The devices we use for this testbed are:
* 2 Kali Linux CLI
* 1 Router
* 1 NAT
### Save and Run the Testbed 
Once you have finished configuring the devices in your testbed, save the project. Then, click on the "Play" button to start the simulation.

### Connect Devices & Configure Devices
Machine 1:
```
> ip a add nya : 192.168.14.2/24 dev eth0
```
Machine 2:
```
> ip nya : 192.168.15.2/24 dev eth0
```
Router: 
```
> config t
> interface f0/0
> ip add 192.168.14.1 255.255.255.0
> no shut
> end

> config t
> interface f1/0
> ip add 192.168.15.1 255.255.255.0
> no shut
> end
```
To show the ip interface connected!
```
> show ip interface brief
```
Machine 2:
```
> ip route add 192.168.14.0/24 dev eth0
```
Machine 1:
```
> ip route show
> ip route add 192.168.15.0/24 dev eth0
> ip route show
// CAPTURE USING WIRESHARK on the cable machine1 to the router
> ping 192.168.15.1 -c 1
//protocol will change to ICMP, there will be request and reply; ICMP means it is connected
```



### Test Connectivity
Verify connectivity between the devices by pinging the IP addresses of each device. You can also use other network diagnostic tools to troubleshoot and test your network configuration.

## 3. ICMP scan/host discovery with Nmap
To conduct ICMP Scan or host discovery with Nmap, type the following command in the terminal of one of the Kali Linux CLI
```
nmap -sn <ip address>
```
After this command, check the terminal and the Nmap command will work immediately and shows the number of hosts that are up, indicating that they responds to our ICMP packets sent to them via the ICMP Scanning.

## 4. ICMP scan iptables prevention
To check your machine's iptables setup, type the following command in the terminal of one of the Kali Linux CLI (this will be your machine that will be protected from ICMP scanning via iptables)
```
iptables  -L --line-numbers
```
Then type the following command to activate the ICMP drop command with iptables 
```
iptables -A INPUT -p icmp -j DROP
```
You can then check again the line numbers of your iptables setup on the machine. To test if the iptables command is working, use the other Kali Linux CLI that is connected to the protected CLI and try to ping the protected CLI
```
ping <ip address>
```
The ping command will then no longer work and you will see the ICMP protocol captures in wireshark. 
