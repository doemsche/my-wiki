#Wireshark

##Basics

##OSI Reference Model

1. Physical Layer
Electrical Level, Hardeware

2. Data Link
Encoding and Decoding of Data-packets as they are translated into Bits
Error Handling Hardware Layer
Sublayer: MAC-Addressing => Permissions
Sublayer: LOC

3. Network
Switching and Routing. Addressing, Errorhandling

4. Transport
Transfer from host to host (server). Ensuring transparency. Error Recovery. Integrity of Data. TCP (Transmission Control Protocol).

5. Session
Coordinates Communications. Manages Terminates Connections Sessions

6. Presentation
Translating from Application to Network and vice versa. Convert data into suitable format for App.

7. Application
Supports Applications, Qualtiy of Service. HTTP, TELNET, FTP and other Networkservices


## Filters

1. protocol filters
```
#examples
dns 
udp.port == 53 || tcp.port == 53

#
icmp
```


2. more Filters
```
#src = src
#dst = destination

i.addr == ${IPADDR} 

tcp.srcport == 80
tcp.dstport == 80
tcp.port

udp.port == 53

ip.addr == ${IPADDR} && (tcp.port == 53 || udp.port == 53)

```

## Packet Details

Frame => Layer 1 

Ethernet II
Source <=> Destination
[Geo Location] => needs to be configured

IP V4
Request that is sent to Webserver

## Command Line

```shell
# use Wireshark in command line
tshark --help
```

```shell
# list interfaces
tshark -D

# start caputre of interface
tshark -i en0

# record traffic
tshakr -i en0 -w /tmp/myCap.pcap
```




