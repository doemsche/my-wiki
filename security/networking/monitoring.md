#### Syslog
Several Linux Distributions use rsyslog (http://rsyslog.com)
Level of severity are standardized = https://en.wikipedia.org/wiki/Syslog

in ddwrt => example Systemlog:
syslogd & remote server
tail -f /var/log/system.log

Mac os conf => /etc/asl.conf
Console => syslog GUI in MAc

#### Network Packets Analyzer
Mac OS && Linux
-tcpdump -h
-tshark => terminal
-wireshark => GUI (cross Platform)

Analyzer must be run on the Router and not the client


##### TCPDUMP
![](_images/tcpdump.png)
```shell
#list interfaces
tcpdump -D

#
tcpdump -i en0

#Monitor whole traffic
tcpdump -i any

#monitor port 80 (internet traffic)
tcpdump -n -i any dst port 80
#monitor port 80 (internet traffic) wifi
tcpdump -n -i en0 dst port 80

#DNS query
tcpdump -i en0 port 53

#check ipv6 traffic
tcpdump -i ppp0 -vv ip6

#check differnet ports
tcpdump -i any port 53 or port 80 or port 443


#Lcok down to IP
#check if anything is connecting to the server excluding internal traffic to the server (mal ware detection)
tcpdump -i any host 192.168.35.200 and not src net 192.168.35.0/24

#looking for anything not comming from the internal network
tcpdump -i any dst net 192.168.35.0/24 and not src net 192.168.35.0/24

#capture traffic to a file
#-s captures whole package tcpdump 
tcpdump -i any -s 65535 -w capturefile.cap

```

#### Wireshark Protocol Analyzer
Command to be on router:
![](_images/ddwrtwireshark.png)

```shell
iptables -t mangle -A PREROUTING -d 192.168.ip.to.mointor -j TEE --gateway 192.168.1.wireshark
iptables -t mangle -A PREROUTING -s 192.168.ip.to.mointor -j TEE --gateway 192.168.1.wireshark
```

or via ssh => more disk space

```shell
#not port 22 prevents from capturing the ssh traffic
ssh root@192.168.0.1 -- "tcpdump -w - -s 65535 'not port 22' " > capture.pcap

#live traffic
ssh root@192.168.0.1 -- tcpdump -U -s 65535 -w - 'not port 22' | wireshark -k -i -

```
![](_images/wireshark_cheat_sheet1.png)
![](_images/wireshark_cheat_sheet2.png)

#### Toolkit
-Network Security Toolkit => NST => Linux distribution
-Netresec => Networkminer => linux & mac os



