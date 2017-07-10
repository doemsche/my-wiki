##Tor 

### What is Tor
Tor is distributing your internettraffic over several relays. No single point can link you to the destination.
Packets are encrypted and get send from node to node until they reach an exit node where they communicate with a website (Tor Circuit)

xxxxx.onion are hidden services. They do not need an exit node but remain within the tor network (end to end encryption) 
The Client negotiates different encryption keys for each hop from node to node. So no node knows individually who the previous was.

 ![](_images/tor_circuit.png)

 The exit node => Tor to Web is not encrypted (last step)

### Tor Browser
Enables Acces to the Tor-Network.
Most of the Tor Relays operate in Europe
Tor Browser relies on a hardened Firefox.

New Identity: Everything within the browser is wiped
New Tor Circuit: Provides a new circuit and new exit node

https://tor.stackexchange.com/
https://www.torproject.org/docs/faq.html.en
https://blog.torproject.org/
https://trac.torproject.org/projects/tor/wiki

### What does Tor and what not
Without special configuration: It anonymizes the Browser's connection to Websites (Browser only!!) only the Tor Browser uses Tor per default.
It focuses on the protection of data transportation only.

#### It does:
It prevents the ISP and your local Network from knowing which sites you are visiting.
It prevents a site from knowing who you are
It prevents tracking (You are coming from differnt IP's)
Enables to access darknet.

#### It does not:
It does not prevent whoever is watching from knowing you are using Tor. With deep packet inspection Tor traffic can be detected.
Tor exit nodes are known and Tor Browser have a fingerprint.
Tor does not make Applications use Tor Network.
Tor cannot resolve Browser Vulnerabilities.

#### Check your Tor Connection
http://check.torproject.org/

#### Consensus
The Tor Consensus:
https://jordan-wright.com/blog/images/blog/how_tor_works/consensus.png

Per Default Tor chooses 3 random relays:
-Entry-Relay (Guard-Relay)
-Middle-Relay
-Exit-Relay

 ![](_images/tor_relays.png)

### Tor Bridge
If Tor is blocked or dangerous or illegal then use a Tor Bridge
https://bridges.torproject.org/options

Bridges are less reliable and slower then relays.

### Firewall that block Ports
80 and 443 is usually open => Tor networksettings => firewall, assing ports
maybe slower

Deep Packet Inspection (DPI) is hard to pass by => try pluggable transport that change the fingerprint of the packets.
Tor => Networksettings => Ip blocks ... => Connect with provided bridges => transport type => USE in combination with a bridge.

### Tor Configuration File
torrc => torrc Config File
Command line:
https://www.torproject.org/docs/tor-manual.html.en

Examples:
-Change Entry Nodes
```shell
sudo nano .../torrc
#add lines
EntryNodes {de}
ExitNode {gb}
```

-Relay per Fingerpring
https://atlas.torproject.org
Search relay adn copy fingerprint
```shell
sudo nano .../torrc
#add lines
EntryNodes $FINGERPRINT
ExitNode {gb}
```


### Tunnel App traffic through Tor
```shell
watch -d -n1 netstat -tupan

#open tor brwoser
#establish socks proxy

#WAringin: No guarantee that the app does not leak
```

Not all apps have a setting to configure SOCKs Proxy
http://privoxy.org
Can add this to the router

or use whonix


### Tor Weaknesses
-Using Tor makes suscpious
-Tor is complex 
-Tor is not sufficiently isolated 
-Serious Nation State have exploits for Tor Browser
-Lack of Browser non-persistence
-Browser Fingerprint
-using Tor makes you a target
-end-to-end correlation attack
-sybil attack
-DDoS attack

-VPN can geographically be out of bounds of an adversary, Tor cannot since everybody can run Tor Relays

-Tor makes nothing to make private the data sent to an exit node
-When not running Tor all the times, it's clear when you do sth private
-DNS Leaking
-NO Udp on Tor
-Speed and Latency

### Hidden Services
Hidden Service => Relay that runs as well a web service
Whonix could be used to provide a hidden service

with 
http://tor2web.org
https://duskgytldkxiuqc6.onion.to/
add ***.onion.to suffix
This service does not anonymize the viewer of course

#### Finding hidden Service
hidden services are not indexed
Look in **lists**:
pastebin
twitter
reddit
hiddenwiki

ahima.fi

torch search engine

sinbad search engine

the best way to find is **lists**

#### Tor Apps
-Orbot for Android
-Orfox for Android
-Onion Browser IOS
-Tor Messanger
-OnionCat => VPN Adapter









