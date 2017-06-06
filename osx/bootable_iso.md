Making a Bootable USB from ISO on Mac OSX
Posted on 2015/06/13
Been doing tons of writing images to USB recently and have found these few commands very useful.

To do this we first need a ISO image we want to write to USB. In our case this would be the latest Ubuntu release I grabbed.

First we need to convert that .iso to .dmg which dd can understand and write to the USB. Do this by running the following command:

```bash
hdiutil convert -format UDRW -o ~/path/to/ubuntu.img ~/path/to/ubuntu.iso
```
Once this complete there will now be a .img file at ~/path/to/ubuntu.img which we will write to the USB.

Before we write to the USB we first need to identify which /dev/{device-name} we are referring to. To do this run:
```bash
diskutil list
```

The easiest is to run the command, then remove your device and run it again. The missing device is your USB device. THIS IS VERY IMPORTANT IF YOU PICK THE WRONG DEVICE THAT DEVICE WILL BE WIPED!!

Next make sure to unmount the disk so dd can do some magic on it:

```
diskutil unmountDisk /dev/{device-name}
```

Once that is done run the following command, pointing dd both to ~/path/to/ubuntu.img which we created the device we found from diskutil list.
```
sudo dd if=~/path/to/ubuntu.img of=/dev/{device-name} bs=1m
```

If the command fails look at perhaps using "1m" instead of "1M", users have noted differences on platforms in the comments.

For more speed on the dd command consider using /dev/r{device-name} which will rather use raw and give a slight boost in performance.

That will take a while and do the actual write and wiping of the device. Once done your device should be ready for action.

Just to be thorough let's eject the device before removing it to save our precious data !

```
diskutil eject /dev/diskN
```

And that's that, you'll now have a bootable device. Problems / other ways ? Let me know in the comments !