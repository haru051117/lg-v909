
# Restore to stock WIP #

---

This article will describe how to return your G-Slate to the factory specs for service or a return.

## Downloads ##

---

| Downloads | Mirror |
|:----------|:-------|
| Linux nvflash | http://tinyw.in/QcGo |
| Windows nvflash | http://tinyw.in/vbbk |
| v900 Restore Files | Coming soon! |

## Prerequisites ##

---

  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access or [udev rules configured](http://code.google.com/p/lg-v909/wiki/udev_Rules)
  1. nvflash binary (See [Downloads](http://code.google.com/p/lg-v909/wiki/Restore_to_Stock#Downloads))
  1. Windows nvflash will need drivers installed, included with nvflash binary for Windows

## Instructions ##

---

### LG G-Slate v900 Stock Restore ###

---

  * Download the v900\_restore.zip archive. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Restore_to_Stock#Downloads))
  * Unzip the v900\_restore.zip, use an app like [7zip](http://www.7-zip.org/) or [WinRar](http://www.win-rar.com/download.html) or tar or...
  * Boot into APX mode. (See [fastboot\_apx\_modes](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes))
  * Unpack the appropriate nvflash. (See [Downloads](http://code.google.com/p/lg-v909/wiki/Restore_to_Stock#Downloads))
  * Run the following to restore /system to the stock image:
```
   ./nvflash --bct v900.bct --setbct --configfile flash.cfg --create --bl bootloader.bin --odmdata 0x3b048000 --sbk 0xe3baffc6 0xa9585c23 0xe21b497b 0x793d1932 --go
```
  * When that is done, reset the device with the reset button under the battery cover.
  * You should now be booting into Honeycomb 3.0.

## Known Issues ##

---

  * You will need to run the restorer as 'root'.
  * This will wipe your slate, including /sdcard. Back up your data.