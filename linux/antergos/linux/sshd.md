### Install ssh

```shell
#arch linux
#https://wiki.archlinux.org/index.php/Secure_Shell

#installation
sudo pacman -S openssh

#set up service
sudo systemctl enable sshd.service

#connect to client
ssh {USER}@{HOST}

```

```shell
#amd linux
#https://help.ubuntu.com/community/SSH/OpenSSH/Configuring
sudo apt-get update
sudo apt-get install openssh
```