#Disk Encryption

## Windows 
### BitLocker (Closed source)
Bitlocker Win 19 Enterprise and Pro (not Home)
Supports TPM
-TPM only
-TPM + PIN
-TPM + USB Key
-USB Key
-Password only

### VeraCrypt
Based on TrueCrypt. Offers container encryption or partition.
No TPM Support

Secure Boot in BIOS or UEFI

### OSX
File Vault2
Pro
-Limited impoact on performacne
-pre boot auth
-user friendly
-DMA (Memory Access protection)

Contra
-no multi factor auth
-password = password of operating system
-no tmp
-no secure boot
-bad track record
-boot volumes are not encrypted
-in standby the file vault is stored in efi
-no hidden volumes and containers

OSX pmset
OSX Filevualt2 uses entropy so don't encrypt on an unused mac....
OSX set firmware password set pmset to not hypernate


### Linux
Veracrypt cannot do whole disk encryption but is an option for container and partition encryption

It is recommended to encrypt at install state many distors offer that. => dmcrypt and LUKS

dm-crypt and LUKS is very configurable

#### dm-crpyt and LUKS

cryptsetup => cli tool => which cryptsetup

##### commands
cryptsetup benchmark

lsblk
=> show disks (sda5 is often encrpyted disk)

cryptsetup luksAddKey /dev/sda5
=> add new passphrase

##### Special for Arch Linux
https://wiki.archlinux.org/index.php/Disk_encryption
https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system

#### GUI
zulucrypt

#### Encrypt GRUB Bootlaoder

1. Copy files from root partition
```shell
# mount space
mount --bind / /mnt

#checck
lsblk

# copy boot partition
cp -a /boot/* /mnt/boot
cp -A /boot/vmlinux-* /mnt/boot/

# diff to make sure there is no differences
diff -ur /boot /mnt/boot/
# there should be none

#unmount 
umount /mnt
#check
lsbklk
```

2. Prevent /boot from mounting
```shell
#
sudo nano /etc/fstab

#remove /boot entry
```

3. Make nwe grub config
```shell
#BU grub.cfg
cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

#make new grub config
grub-mkconfig > /boot/grub/grub.cfg

# reinstall bootloader with encryption
echo  GRUB_ENABLE_CRYPTODISK=y >> /etc/default/grub

#check
cat /boot/grub/grub.cfg

#install
grub-install /dev/sda

#reboot
> set master password

```

##File Encryption
Peazip: Win, Linux 
Keka: Mac

AES Crypt (Win, Linux and Mac) <=> for decrypting both parties need AES Crypt
GPG => For Email (public private key encryption)¨

## Nesting Crypto System and Obfuscation
for more extreme cases
![](_images/cryptoobfuscation.png)
-Hard disc Whole Disk Enrcryption
-Different Passwords different levels of security

Encrypt Virutal Machines on the Hypervisor
