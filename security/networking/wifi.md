### WiFi WEAKNESSES

#### WEP / IEEE 802.11
A lot of security flaws
-static encryption keys
- lack of packet integrity

WEP should never ever be used

#### WPA2 IEEE 802.11i
AES == CCMP

WPA2-Personal => Home and Small Business Networks
Disadvantage => Everyone uses the same passkey. If the key changes everybody has to change it.

WPA2-Enterprise => Enterprise or Company Networks
Uses Radius Autentication Server
Uses EAP (Extensibel Authentication Protocol)

WPA2 Passwords can be dictionary bruteforce attacked. Strong password is recommended.
Cowpatty in Kali can be used.

Salt Issue => SSID is used as Salt-Value. Salt Value should be randomized.

Church of Wifi => Rainbow tables for cracking Wifi passwords.
Default and Common SSID should not be used.

#### WPS 
Wi-Fi Protected Setup Pin Issue
Pin mode is activated in a lot of Hotspots.
WPS must be turned off

Reever => Kali 

#### Evil Twin
Access Point fakes to be "your" accesspoint.
WPA2-Enterprise can mitigate evil twin beacause of client accesspoints certificate exchange....

http://www.hsc.fr/ressources/articles/hakin9_wifi/hakin9_wifi_EN.pdf


### Wifi Security Testing
Kali needs Wireless Card
Aircrack-ng
cowpatty
reaver
fern wifi cracker

### Wifi Security Sternghtening

#### Isolation
Wireless Networks should be less trusted than wired networks.
Wifi is intrinsically more risky.

Separate different SSID's with different subnets.
-Untrusted Gutest Network 192.168.4.0/24
-Trusted Network 192.168.5.0/24
==> use the same hotspot

-change default SSID
-Avoid TKIP
-Disable WPS
-turn on arpwatch (arpspoof protection)
-choose complex passwords
-don't use wifi when possible

-Disabling the SSID Broadcast prevents certain devices from seeing the SSID, but wifi scanner software will still be able to see it.

-MAC-Address Filtering is not recommended, since an attacker can see MAC Addresses in a network and fake (spoof) them (MAC Addresses are broadcasted)
The Administrative burden is big.

-Limit the Wifi Connections that a hostpot makes

