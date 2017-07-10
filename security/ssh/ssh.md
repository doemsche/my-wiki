# SSH
Most linux based systems deliver ssh out of the box. Default Port is 22

ssh => client
sshd => daemon

```shell
ssh root@domain
```

To view which devices have ssh running make a nmap scan on port 22

## Remote Port Forwarding

Example Webserver 
```shell
#start server on Client
python -m SimpleHTTPServer 9999
# -R => Forward remote Port via ssh to Server
ssh -R 8080:localhost:9999 root@host
#---------------------------------------------------------------------------
# on remote Server the Service is running via ssh on Port 8080
http://localhost:8080
```

Example Netcat in Combination with Port Forwarding
```shell
#execute bash on port
nc -v -l -p 9999 -e /bin/bash
#
nc domain.name 8080
```

Enable Port forwarding in ssh
```shell
nano /etc/ssh/sshd_conf
...
GatewayPorts yes
```

## Local Port Forwarding
SSH for outbound connections. Using a remote port as if it was a local port. Connecting to the port locally.
```shell
# Create ssh tunnel from local port 8080 to remote port 6666
ssh -L 8080:localhost:6666 root@host
```

## SSH Socks5 Proxy Tunneling with Dynamic Ports

```shell
# -f => send to background (e.g. with private public key auth) (kill it later)
# -N => instructs ssh to not execute a command on the remote machine
# -n => redirects STDIN from dev null prevents reading from STDIN (must be used when -f)
# -D => specifies the local dynamic appliation level port forwarding 
# his works by allocating a socket to listen to a port on the local device
# Whenever a connection is made to this port the connection is forwarded over the secure channel and the application protocol is then used to determine where to connect from the machine

ssh -fNn -D 8080 user@host

#check
ps -ef | grep ssh

# apply settings (see image below)

# kill the service
pkill ssh
kill ${PROC_NUMBER}

#Aside: Issue remote Commands without creating a shell
ssh user@host -- whoami

```
![](_images/socksproxy.png)

If using an application without proxy settings => Linux tsocks

### SSH Fingerprinting
ssh tunnels are fingerprinted (but encrypted). 

## Public Private Key

```shell
#Linux
ssh-keygen -t ed25519 -C "dominik@debian_linux"

#Mac
ssh-keygen -t rsa -b 4096 -C "dominik@mac"

#copy key if ssh-copy-id is not available
cat ~/.ssh/id_ed25519.pub | ssh user@host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
#if avaliable (user name does not matter...)
ssh-copy-id user@host
```

#### Windows
To generate on Windows use:
-putty-key-gen
-start pageant.exe and add private key
-save session in putty
-run pageant

Alternatively use linux and use the generated keys

## SSH Hardening

### Server
https://wiki.mozilla.org/Security/Guidelines/OpenSSH
https://webcache.googleusercontent.com/search?q=cache:XB4wEwKtw7wJ:https://incenp.org/notes/2014/gnupg-for-ssh-authentication.html+&cd=1&hl=en&ct=clnk&gl=hu&client=firefox-b-ab

### Client

Harden the following file
```shell
~/.ssh/config
```




