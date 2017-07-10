#Proxies
A Proxy Server acts in place of another. A Proxy acts as an intermediary between a client and a server.

Proxies are somewhat similar to VPN's without the layer of encryption.
VPN's send all traffic encrypted, whereas proxies onlx the traffic of an application (Application level).

Example Firefox:

1. http-proxy:
understands and interpretes http protocol only

2. ssl-proxy:
same as http with support of ssl (only btw the proxy and the dest)

3. ftp-proxy:
for ftp

4. SOCKS
SOCKS v4 / SOCKS v5
Socks proxies are more flexible since they operate at a lower level than the above protocol proxies. They are not dependent on a protocol.
v4 => does not allow remote DNS (no udp)
v5 => does resolve DNS (udp, ipv6)

Proxies are faster than VPN's since there is no encryption.

A transparent proxy does not hide the ip address
An anonymous proxy hides ip but not the proxy
An elite proxy hides ip and that you are using a proxy
