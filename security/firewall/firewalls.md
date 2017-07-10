### Firewalls
ACL to accept or reject traffic based on Port, Protocol and Address.
Allow or restrict access to IP-Addresses or ranges.

Application-Level Firewalls make deep packet inspection.

#### Ingress/Inbound Filtering.
![](_images/inbound.png)

#### Egress/Outbound Filtering. 
![](_images/outbound.png)
http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

#### Network Isolation
![](_images/networkisolation.png)

#### Host-Based Firewalls
Windows-Firewall (or Commodo)
Linux-Iptables
Mac OS pf-Firewall & Application Firewall

Host-Based sit on the same system as the malicious code.

#### Virtual
install pfsense in Virtual box

#### Network-Based
Filter traffic from LAN to WAN and vice versa.
ACL to accept or reject traffic based on Port, Protocol and Address.
Could sit on the router (custom firmware)
**Problem** => Allowed open ports communicate out => provides no outbound protection => Good Networkfirewalls can work on the Application level and make the deep packet inspection.
![](_images/networkfirewall.png.png)

#### Terms and Rules
Main Rule => Deny all
Dynamic Packet Filtering | Stateful Packet Inspection (SPI)

#### Windows

##### Windows Host based Firewall
Disadvantage:
-Defaults to allow all outbound traffic
-does not allow to block microsoft
-the most attacked

=> binsoft.org allows a better GUI (Frontend) Windows Firewall Control
=> third party:
-Comodo
-Glasswire

##### Linux Host based Firewall
All modern linux kernels use net filter. The User Interface for is Iptables.
Iptables is the database of the firewall rules.

iptabels -L

INPUT => inbound
FORWARD => inbout => forward (router)
OUTPUT => outbound

INPUt FORWARD and OUTPUT have all a default policy, which will be applied if no ruleset is defined.
Default Policies: DROP (no response), REJECT (send back response), ACCEPT

iptables rules
```shell
#Flush all rules
iptables -F

#Set default policy
iptables -P INPUT DROP

#
iptables -A INPUT -i lo -j ACCEPT

#see rules that got defined
iptables -S

#save the rules
/sbin/iptables-save

#Delete rule (Line number)
iptables -D OUPUT 5 

```

ip6tables => has own table => how to disable
```
ip6tables -P INPUT DROP
ip6tables -P FORWARD DROP
ip6tables -P OUTPUT DROP
```

https://github.com/meetrp/personalfirewall
https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html

#### GUI and Frontend
UFW => Frontend for iptables
shorewall
GUFW => GUI

Linux Firewalls are not Application aware, which is a disadvantage over Windows and Mac Firewalls

nftabels => project that intends to replace iptables (in beta)

Is it worth having a host-based Firewall?
It depends... Malware communicates out over ports that are anyway open.
Questions to ask:
-is it worth the burden to configure iptabels
-are untrusted devices in the network that firewalls can prevent from communicating out or in?

### Mac OS Firewall
Built in: Mac Firewall is application level but cannot block outgoing connections only incoming
Configuration is in this folder and can be configures manually:
/usr/libexec/AppicationFirewall
can be loaded and unloaded with launchctl
=> Mac Firewall is not particularly useful...

### PF (firewall) 
Equivalent to iptables for open BSD and OSX. 
(Interanlly the OSX Firewall uses PF)

pf.conf
```shell
#config
/etc/pf.conf

#add another anchor do it's not overwritten
...
anchor "org.doemsche.pf"
load anchor "org.doemsche.pf" from "/etc/pf.anchors/org.doemsche.pf"

```


pfctl
```shell
#show ruleset
sudo pfctl -sr

#check if rules work correctly
sudo pfctl -v -n -f /etc/pf.conf

#enable rules
sudo pfctl -f /etc/pf.conf

#put firewall in verbose mode
sudo pfctl -v
#enabel firewall
sudo pfctl -e

#disable firewall
sudo pfctl -d
```

http://www.poenbsd.org/faq/pf
https://calomel.org/pf_config.html
http://murusfirewall.com/Documentation/OS%20X%20PF%20Manual.pdf

### GUIs for PF Firewall
-pflists (simply lists the rules) >10.7
-IceFloor 10.7 - 10.10
-Murus (Lite, Basic and Pro)
-Little Snitch => Application based GUI Firewall


##### Network based Firewall
-pfSense
-openSense
Question is it worth having a network based Firewall?


