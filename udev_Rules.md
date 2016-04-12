
# Configuring udev rules #

---

This document will outline how to configure [udev](http://en.wikipedia.org/wiki/Udev) to work with [fastboot](http://goo.gl/CCUAK), adb and nvflash. This will allow a "normal" user to have full access to the device using [fastboot](http://goo.gl/CCUAK), adb and nvflash without root access.

## Prerequisites ##

---

  1. Ubuntu Linux 10.04+ -- If using another distro, adjust the rules syntax accordingly
  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access

## Instructions ##

---

  * Create a new rule for udev to use:
```
sudo gedit /etc/udev/rules.d/99-android.rules
```
> (Use whatever editor you'd like. I prefer `vi`, but for the fairness of being noob friendly, I'll do `gedit`.)

  * Insert the following code:
```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="1004:61f9"
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0955:7820"
TEST=="/var/run/ConsoleKit/database", \
RUN+="udev-acl --action=$env{action} --device=$env{DEVNAME}"
```
  * Save the file.
  * Reboot the computer.

## Conclusion ##

---

After reboot, you should now be able to access your G Slate without root or sudo access needed.