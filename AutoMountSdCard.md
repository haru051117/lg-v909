
# Configuring MTP Support #

---

This document will outline how to configure [MTP](http://en.wikipedia.org/wiki/Media_Transfer_Protocol) to mount the SDCARD of the G Slate automatically when plugged in to the computer.

## Prerequisites ##

---

  1. Ubuntu Linux 10.04+ -- Check your distros documentation on how to configure MTP to work with it.
  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access
  1. udev Rules configured (See [Configuring udev Rules](http://code.google.com/p/lg-v909/wiki/udev_Rules))

## Instructions ##

---

  * Do the following in a terminal or terminal emulator.
```
   sudo apt-get install mtpfs
   sudo mkdir /media/gslate
   sudo chown $USER:$GROUP /media/gslate -- (YOUR USER AND USER GROUP, so: sudo chown myuser:myuser /media/gslate
   sudo gedit /etc/fstab
```
  * Insert the following into the `fstab` file:
```
   # mount point for LG G Slate
   mtpfs        /media/gslate       fuse      user,noauto,allow_other         0       0
```
  * Edit the `fuse.conf` to allow other users:
```
   sudo gedit /etc/fuse.conf
```
  * Uncomment the following line by removing the `#`:
```
   #user_allow_other
```
  * Add your user to the `fuse` group in the `group` file:
```
   sudo gedit /etc/group
```
  * Edit this line, add your user name after the last `:` (Colon):
```
   fuse:x:104:
```
  * Reboot your Computer.

## Conclusion ##

---

Now when you're done booting, you should now notice a new mount labelled `gslate` in the Places Menu. Anytime you plug in your G Slate, it will automatically mount and launch a new window that will be mounted to `/media/gslate`.

## Known Issues: ##

---

  * MTP is broken in using Gnome 2 in Ubuntu 11.04+, install gnome-shell (Gnome 3) to correct the MTP issues.
  * Ubuntu 12.04 works correctly with MTP devices.