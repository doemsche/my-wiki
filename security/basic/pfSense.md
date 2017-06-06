### Why no Consumer Product:
Cheap Consumer Routers:
-Bad Software
-Bad RAM
-Connections consume RAM on Router

### Pro pfSense
-Configuration
-More RAM
-Updates and Patches
-Scalability
-Network Log

### Hardware

#### CPU
-Networks smaller than 1Gbps => 1.8GHZ Core 2
-pfSense >= 2.2 Multi-threaded

#### Memory
Recommended at least 1 GB RAM 

#### Network Interfaces
-Use only Intel NICS
-One Card for the WAN and one for the LAN
-Each Subnet needs a Network Card
-Gigabit recommended

#### Physical Setup

Modem <==> WAN <==> LAN <==> Switch
![](images/setup.png)

#### VLAN
![](images/vlan.png)
Port mapping with a managed Switch
When to Use VLANs? => When there are more subnets than can be NICs => Managed Switches are expensive

#### WLAN
![](images/wlan.png)
Take Consumer Wireless Routers => Disable Router Functionality


