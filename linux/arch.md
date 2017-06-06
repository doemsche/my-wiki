## Installing

### Partition Table GPT vs MBR
1) MBR => Master Boot Record
The first 512 bytes of storage. MBR is not located in a partition. It contains the bootloader and the partition table. There are 3 types of partitions in the MBR:
-primary, -extended, --logical 
Primary Partitions can be bootable (limited to 4 partitions per disk or raid) (if needed more then primary must be replaced by extended containing logical partitions)

2) GPT GUID (Globally Unified Identifier == UUID) usage of UUID's to define partitions and partition types (it is designed to succeed MBR)
Is part of UEFI


### Partition Schemas

### Single Root Partition
This scheme is the simplest and should be enough for most use cases. A swapfile can be created and easily resized as needed. It usually makes sense to start by considering a single / partition and then separate out others based on specific use cases like RAID, encryption, a shared media partition, etc.

/ => contains the /usr dir
/boot => contains kernel, ramdisk images and bootloader-config and bootloader-stages
/home => contains user specific config
/var => contains variable data logging , pacman 

### Commands
fdisk -l
mount -t ext /dev/sdX /mnt
fdisk /dev/sdX => enter m for help 
mkfs.ext4 -L root /dev/sda1 => creates logical file system with formatting
genfstab -U /mnt

