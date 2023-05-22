# TCP Half Open Scan Team
* Nicholas Valerianus BUdiman (2502055596) L4AC
* Hansel Faren (2501990350) L4AC
* Benedictus Filbert Federico (2502005263) L4AC

## TCP Half Open Scan 
# What is TCP Half Open Scan
TCP half open scan is a fast and sneaky scan that tries to find potential open ports on a target computer
# How it works
TCP half open scan starts by sending a SYN packet to initiate a communication and establish a connection between the two which on an open port would result in a response of a SYN and ACK packet sending back syncronization and an acknowledgement after this process has been completed instead of sending another ACK packet to complete the TCP connection the attacker would send an RST packet that indicates that they will no longer accept or recieve any more data (basically shuts down the connection). 
![image]()
On a closed port the attacker using TCP half open scan would not get a SYN packet back from the target instead they would recieve an RST packet 
![image]()

## TCP half open scan with Nmap
sudo nmap -sS <target>
sudo nmap -sS -p <port> <targetIP>
  
## Prevent 
Ip table prevention
iptables -A INPUT -p tcp –tcp-flags -j ACCEPT
