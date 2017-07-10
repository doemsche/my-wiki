### Networking

#### Router
Router is a term for a collection of components such as:
![](_images/router.png)
Services on Routers:
-DHCP
-DNS
-Port Forwarding
-NAT

1) Swichtes
Send and Receive traffic in CAM Tables (Switches only use Mac Addresses in LAN, no IP), Switches are more secure than hubs because of **Isolated Collision Domains** => Traffic cannot be sniffed, since it only communicates with a dedicated MAC-Address.

2) Firewall
Accepts or rejects traffic based on rules (iptables).

3) Router
Routes traffic from one Network to another based on information in the IP routing table. LAN <=> WAN. (Layer 3). Networks differ in subnets.

4) Modem
Signal Modulation.

5) Wireless Access Point
Simiar to Switch but for wireless devices => uses MAC Addresses.

#### Router Vulnerabilities Check Tools

https://www.shodan.io
https://mxtoolbox.com
http://www.techmonkeys.co.uk/hackcheck/index.php
https://qualys.com

#### Vulnerability Scanners
1. mac & linux: nmap && zenmap (nmap -T4 -F 192.168.0.0/24)
2. windows: superscan
3. mobile: fing
4. zenmap in Kali
5. meta-sploitable
6. openvas.org => on kali (needs configuration)
7. Nessus => windows, linux and mac

#### Custom Firmware
Flashing Router firmware. 
1. OpenWrt
2. busybox
3. gargoyle
4. libreCMC
5. dd-wrt
6. pfSense => Firewall

smallnetbuilder.com => router performance
