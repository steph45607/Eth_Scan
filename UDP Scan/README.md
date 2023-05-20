# UDP Scanning

What is UDP Scanning?



## UDP scan with Nmap
```
nmap -sU <ip>
nmap -sU -p <port> <ip>
```

## Iptables prevention
```
iptables -A INPUT -p udp -j DROP
```
to reset (flush and delete chains)
```
iptables -F
iptables -X
```