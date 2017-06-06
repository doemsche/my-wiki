
### static ip:
cp /etc/netctl/examples/ethernet-static /etc/netctl/enp1s0


Description='A basic static ethernet connection'
Interface=enp1s0
Connection=ethernet
IP=static
Address=('192.168.0.100/24')
Gateway=('192.168.0.1')
DNS=('192.168.0.1' '8.8.8.8' '8.8.4.4')

### start
sudo netctl start enp1s0
### enable
sudo netctl enable enp1s0

ip link set enp1s0 down
netctl start profile
