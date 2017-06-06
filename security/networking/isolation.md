#### Network Isolation

#### ARP Spoofing
In LAN only Mac Addresses are used. Address Resolution Protocol. Attacker fakes to be the default gateway.
ARP is IP to MAC Address resolution => Data Link Layer.
If a device on a LAN wants to connect to another device on the LAN there is an ARP request to resolve. It's a broadcast to all devices to resolve the address. This process can be fooled:
-arpspoof
-ehtercap
-cain and able
arp has no authentication and therefore is vulnerable. 0 security.

#### Isolation
![](images/isolation.png)
DMZ (Demilitarized Zone) => Devices for Port Forwarding (Webserver, Synology, IP Cam) 

VLANS => Logical Separation => VLANS work at Layer2
DMZ => Physical Separation

VLAN Hopping Techniques exist => Yersinia in Kali