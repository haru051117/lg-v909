
# Rooting #

---

## `*** It is highly recommended to make backups of all your applications and data before proceeding. ***` ##

This will give you a how-to on rooting. Right now there are a two main options. The Clockwork method is recommended.

## Prerequisites ##

---

  1. Windows or Linux based system with the ADB and fastboot binaries installed.
  1. USB Cable
  1. LGE G-Slate v9xx

## Downloads ##

---

| Downloads | Mirror |
|:----------|:-------|
| Clockwork Recovery 5.5.0.4 | http://goo.gl/c8NZS |
| Fastboot Linux | http://tinyw.in/i6zP |
| Fastboot Windows | http://tinyw.in/VnhB |
| Linux nvflash | http://tinyw.in/QcGo |
| Windows nvflash | http://tinyw.in/vbbk |
| Root.zip  | http://tinyw.in/xYRG |

## Instructions ##

---

### CWM root.zip (3.0 and 3.1) -- RECOMMENDED METHOD (Thanks ChiefzReloaded): ###

---

  * Make sure to have the latest LG Drivers installed. (See [Installing Windows Drivers](http://code.google.com/p/lg-v909/wiki/Install_Windows_Drivers))
  * Download the root.zip (See [Downloads](http://code.google.com/p/lg-v909/wiki/Rooting#Downloads))
  * Download the Clockwork Recovery. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Rooting#Downloads))
  * Download the correct fastboot for your OS (See [Downloads](http://code.google.com/p/lg-v909/wiki/Rooting#Downloads))
  * Untar the recovery.tgz, use an app like [7zip](http://www.7-zip.org/) or [WinRar](http://www.win-rar.com/download.html) or tar or...
  * Boot the recovery:
```
  fastboot oem unlock
```
> > Then:
```
  fastboot boot recovery.img
```
  * Install the root.zip:
```
   Install ZIP from sdcard
   Choose ZIP from sdcard
   root.zip
   Yes - Install root.zip
```
  * Let it flash, then:
```
   Go Back
   Go Back
   Reboot System Now
```
  * Congratulations, you are now rooted.


### Original Root method `[LINUX ONLY]` (Thanks Chandon) -- v909 ONLY!!! : ###

---

  * Download Linux nvflash package. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Rooting#Downloads))
  * Extract the needed files into a directory and cd to that directory.
  * Shut down your G-Slate and plug it into your computer via USB.
  * Hold down both volume buttons and press the power button. The G-Slate will not appear to turn on, but it'll go into APX mode.
  * Verify Linux recognizes APX mode:
```
  lsusb
  0955:7820 NVidia Corp.
```
  * Linux needs root if you have not setup the [udev rules](http://code.google.com/p/lg-v909/wiki/udev_Rules):
```
  sudo su
```
  * Run the following commands:
```
  ./nvflash --bl bootloader.bin --getpartitiontable ptable.txt
  ./nvflash -r --read 8 system-orig.img
```
  * Wait while 400 meg of data copies.
```
  cp system-orig.img system.img
  mkdir system
  mount -o loop system.img system
  cp su system/bin
  chmod 4755 system/bin/su
  cp Superuser.apk system/app
  umount system
  ./nvflash -r --download 8 system.img
```
  * Wait while it copies back.
  * Sync the flash memory:
```
  ./nvflash -r --sync
```
  * Press the reset button under the sim cover to reboot.

## Known Issues: ##

---

  * fastboot mode requires 25% or more battery life, otherwise it will not accept input.