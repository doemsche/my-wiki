# Cleanly format USB stick
```powershell
#Open Terminal as Administrator
diskpart.exe
#list disks
list disk
#select disk
select disk n
#clean
clean
create partition primary
format fs=fat32 quick
```


# Disable Automatic Repair on Startup
http://winaero.com/blog/how-to-disable-automatic-repair-at-windows-10-boot/
```powershell
#Open Terminal as Administrator
#Disable
bcdedit /set recoveryenabled NO
#Enable
bcdedit /set recoveryenabled YES
```

