### SSH into Virtualbox

Enter Port Forwarding:
```shell
#setup rule
VBoxManage modifyvm ${VMNAME} --natpf1 "ssh,tcp,,3022,,22"
#check rule creation
VBoxManage showvminfo myserver | grep 'Rule'
```

In VM (here example arch linux) enable ssh connections:
```shell
sudo pacman -S openssh && sudo systemctl enable sshd && systemctl start sshd
```

SSH into VM:
```shell
ssh -p 3022 user@127.0.0.1
```
