#Copy exmaple rename to eth0-static
sudo cp /etc/netctl/examples/ethernet-static /etc/netctl/eth0-static
#Disable DHCP Service
sudo systemctl disable dhcpcd.service
#Enable 
sudo netctl enable eth0-static

REBOOT