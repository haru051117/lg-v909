
# Unlock bootloader (Thanks chiefzreloaded and dasunsrule32) #

---

**`*** Backup your data. If not, it's your own fault if you lose anything. ***`**

This article will describe how to unlock the bootloader after the 3.1 update.

## Downloads ##

---

| Downloads | Mirror |
|:----------|:-------|
| Clockwork Recovery 5.5.0.4 | http://tinyw.in/L6Jn |
| Fastboot Linux | http://tinyw.in/i6zP |
| Fastboot Windows | http://tinyw.in/VnhB |
| bootloader\_unlock\_L-06c\_v10r.zip | http://tinyw.in/zuFW |

## Prerequisites ##

---

  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access on workstation being used or [udev rules configured](udev_Rules.md)
  1. fastboot binaries (See [Downloads](Upgrade31#Downloads.md))
  1. Understanding of fastboot and accessing the G Slate diag modes. (See [Accessing Diag and Recover Modes](fasboot_apx_modes.md))

## Instructions ##

---

  * Download the bootloader\_unlock\_L-06c\_v10r.zip. (See [Downloads](#Downloads.md))

### Unlocking the bootloader ###

---

  * Copy bootloader.zip to /sdcard/
  * Download Clockwork Recovery (See [Downloads](Upgrade31#Downloads.md))
  * Do an OEM unlock:
```
   fastboot oem unlock
```
  * Reset to Fastboot mode and boot Clockwork Recovery. (See [Accessing Diag and Recover Modes](fasboot_apx_modes.md))
```
   fastboot boot recovery.img
```
  * Install the bootloader.zip:
```
   Install ZIP from sdcard
   Choose ZIP from sdcard
   bootloader.zip
   Yes - Install update.zip
```
  * Let it flash, it will take about 60 seconds, then:
```
   Go Back
   Go Back
   Reboot System Now
```
  * The system will reboot to a _"Downloading Now"_ screen. Let it finish, and it will reboot.
  * All done!