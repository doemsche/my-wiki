#VPN

## Anonymizing Services
-TOR
-Jondonym
-SSH tunnels
-Proxies
-Freenet
-I2P
-VPN (Virtual Private Network)

## Setup
VPN-Client
VPN-Server => Exit Node

From Client to the Exit Node (Server) the traffic is encrypted. The higher the bitlength of the encryption the slower the connection.
-Install the VPN Client on a Host Computer
-Install the VPN Client on a Router (traffic is not encrypted from host to router, but from router to exit node) => dd-wrt
-Install VPN Client on a VM
--There is nested VPN Client option

-Accessing a https-Site => traffic encrypted

### Good for
-Can protect against hackers and trackers. They cannot see the traffic in the VPN. ISP can not see where you are going, it only sees, that you go to the exit node.
-Hide your Geolocation => ExitNode is Geo IP
-Provide a degree of anonymity => exit node IP is shared by many

=?: If https is encrypting connections why do we need a VPN? 
=>: You get certificates from the VPN-Provider. Security Authorities are not required as they are with Certificates. VPN Client will only work with the correct public key. SSL-Stripping, fake Certificates are close to impossible. Man in the middle Attacks are mitigated.

## VPN Protocols
-PPTP (Point-toPoint Tunneling Protocol)
(not recommended, microsoft implementation, bad encryption)

-Layer Two Tunneling Protocol (L2TP)
-Internet Protocol Security (IPSec)
L2TP & IPSec in combination (IPSec provides encryption) are supported by os out of the box. Uses fixed ports and protocols => inflexible. easily blocked by NAT Firewalls. => strong evidence that NSA can decrypt (nation state level).

-OpenVPN
Open Source project uses open-ssl, ssl v3, tls1.0.
Protocols and Ports are configurable => runs fastest over udp. Can use tcp sacrifice speed => could emulate normal https web traffic (port:443/tcp), very difficult to tell that it's vpn traffic. 
Supports lots of encryption algorithms. It's not supported by OS's, third pary software must be downloaded and configured.

-Secure Socket Tunneling Protocol (SSTP)
Microsoft Standard => windows only

-Internet Key Exchange (IKEv2)
Cisco and Microsoft => enhanced ability to reconnect => mobile

-SoftEhter
-OpenConnect

## VPN Weaknesses
-VPN is slower (but faster as tor, jondonam...)
-VPN traffic can be detected and blocked
-Fast VPN is not free
-Money Trail
-VPN does not protect you from Client side attacks
-Website Fingerprinting => looking for patterns in VPN traffic
-When VPN is not used always, not using it draws attention since it's obvious for an observer that you do something more private.
-SMTP is often blocked by VPN-Provider because of spammers
-VPN can be blocked by destination (netflix)
-Unless browsers are not hardened it's easy to track with cookie and browser fingerptinting
-Anonymity is not at the core of VPN => use nested VPN => 
-VPN mor for privacy but not for anonymity

## Open VPN Clients

### Configuration Files
.ovpn extension => contains the key
.ovpn => can declare external files as certs and keys

-Windows
opvenvpn.net
OpenVPN/config/

-Mac OSX
Tunnelblick

-IOS
OpenVPN Client

-Linux
sudo apt-get install openvpn
sudo apt-get install openvpntools
sudo apt-get install network-manager-openvpn-gnome

Sometimes all config is in one file that must be extracted to sep files to import into the vpn client

```shell
#error handling
sudo tail -f /var/log/syslog | grep openvpn
```

## VPN data leaks
-DNS leak
-IPv6 leaks

VPN droppes, traffic is sent directly to destination

### Prevent leaks
=> disalbe IPv6
=> enforce all connections to be sent over vpn
=> block non vpn-traffic with host based firewalls

-VPN-Firewall for openvpn
-VPNDemon
-Extra VPN Leaks Problems on Windows 10
www.dnsleaktest.com

## CHoosing a VPN
-What is the threat?

-anonymous payments
-openvpn
-no personal information
-ability to chang passwordd
-run own dns servers
-client software prevents leaking
-enable port forwarding
...
- recommended under circumstances
(air vpn)
(ivpn)
(nordvpn)
(blcakvpn)
(mullwad.net)


## Run an own VPN Server

### Setting up openvpn in a cloud 
=> it's the same as a paid vpn service...
www.turnkeylinux.org
Download Image and deploy to for example AWS

1. login to server
```shell
#on server
openvpn-addclient john john@demo.domain.net
#creates a file in /etc/openvpn/easy-rsa/keys/john.ovpn
#copy this file to localhost => see vpn client
#in this example in linux the keys and certs have to be seperated out
```

2. copy to client
```shell
scp root@domain.net:/etc/openvpn/easy-rsa/keys/xxx.ovpn
```

3. Import into GUI (probably the file has be separated into single files)
 ![](_images/sed_command.png)

4. test it
```shell
curl ifconfig.io
```


### VPN to connect to home network

Run PiVPN => run vpn Server on a Raspberry-PIe
Run VPN on Custom Home Router (dd-wrt)
Run VPN Server on PfSense


### VPN and Tor Routers
VPN => about Privacy and Security
Tor => Privacy, Security and Anonymity

A Router can be configured to enforce a VPN connection over the Tor network for all outgoing clients.

#### Use a Router as a Gateway for Tor and or VPN

Pros:
- All traffic goes through the encrypted tunnel
- Physical isolation

Cons:
-Could leak if connection drops
-DNS leaks, IPv6 leak
-You don't get the benefit of the Tor Browser using a socks proxy





