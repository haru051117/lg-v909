
# Manually Install 3.1 v10o Update (Thanks chiefzreloaded) #

---

**`*** Backup your data. If not, it's your own fault if you lose anything. ***`**

This article will describe how to install the latest patch from LG and T-Mobile, version 3.1 manually.

## Downloads ##

---

| Downloads | Mirror |
|:----------|:-------|
| Clockwork Recovery 5.5.0.4 | http://goo.gl/c8NZS |
| Fastboot Linux | http://tinyw.in/i6zP |
| Fastboot Windows | http://tinyw.in/VnhB |
| Linux nvflash | http://tinyw.in/QcGo |
| Windows nvflash | http://tinyw.in/vbbk |
| Stock Image Files | http://tinyw.in/oS3q |
| 3.1 v10o  | http://tinyw.in/4eI6 |

## Prerequisites ##

---

  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access on workstation being used or [udev rules configured](http://code.google.com/p/lg-v909/wiki/udev_Rules)
  1. fastboot binaries (See [Downloads](http://code.google.com/p/lg-v909/wiki/Upgrade31#Downloads))
  1. Understanding of fastboot and accessing the G Slate diag modes. (See [Accessing Diag and Recover Modes](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes))
  1. Understanding partition layouts (See [Partitions](http://code.google.com/p/lg-v909/wiki/Partitions#Fastboot_Partition_Layout))

## Instructions ##

---

  * Download the 3.1 v10o OTA. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Upgrade31#Downloads))

### Update from rooted system ###

---

  * Rename it to:
```
   update.zip
```
  * Copy it to /sdcard/
  * Download Clockwork Recovery (See [Downloads](http://code.google.com/p/lg-v909/wiki/Upgrade31#Downloads))
  * Unzip the v909\_restore.zip, use an app like [7zip](http://www.7-zip.org/) or [WinRar](http://www.win-rar.com/download.html) or tar or...
  * Download your version of nvflash. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Upgrade31#Downloads))
  * Reboot to APX mode. (See [Accessing Diag and Recover Modes](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes))
  * Make sure you are in the newly unpacked folder: v909\_restore.zip
  * Restore your /system partition to stock: (See [Restore G-Slate for more information](http://code.google.com/p/lg-v909/wiki/Restore_to_Stock))
```
   nvflash --bl bootloader.bin --getpartitiontable ptable.txt
   nvflash -r --format_partition 8
   nvflash -r --download 8 system.img
   nvflash -r --sync
```
  * Continue install [here](http://code.google.com/p/lg-v909/wiki/Upgrade31?ts=1313433860&updated=Upgrade31#Update_from_stock_system)

### Update from stock system ###

---

  * Reset to Fastboot mode and boot Hacky Clockwork Recovery. (See [Accessing Diag and Recover Modes](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes))
```
   fastboot oem unlock
```
> > Then:
```
   fastboot boot recovery.img
```
  * Install the update.zip:
```
   Install ZIP from sdcard
   Choose ZIP from sdcard
   Update.zip
   Yes - Install update.zip
```
  * Let it flash, it will take about 15 minutes, then:
```
   Go Back
   Go Back
   Reboot System Now
```
  * The system will reboot to a _"Downloading Now"_ screen. Let it finish, and it will reboot.
  * The initial boot can take up to 15 minutes, once it boots successfully, it will reboot one more time.
  * Congratulations, you have upgraded to 3.1.
  * If you would like to root, please see [rooting](http://code.google.com/p/lg-v909/wiki/Rooting) for multiple options.

## Known Issues: ##

---

  * The OTA requires 70% or more battery life.
  * fastboot mode requires 25% or more battery life, otherwise it will not accept input.