#Proxmox
Proxmox is a Type II Hypervisor (has an underlaying OS)
ESXi has no underlying Os is therefore a Type I Hypervisor

```shell
#check amount of processing units
nproc
#find out RAM (used and unused)
free -mt
#check amount of cpu cores
egrep -c '(vmx|svm)' /proc/cpuinfo
#or for amd arch
egrep -c ' lm ' /proc/cpuinfo
```

## Networking

1) Bridge mode: Uses hosts Networkcard but has an own IP address (vNIC) 
2) NAT: Usees hosts Networkcard plus IP address (vm or container not accessible from the network)