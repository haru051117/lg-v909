
# Backup Data #

---

This article will describe how to backup and restore your data, with multiple methods, on the G Slate.

## Prerequisites ##

---

  1. USB Cable
  1. Terminal or Terminal Emulator
  1. [Root](http://en.wikipedia.org/wiki/Su_(Unix)) or [Sudo](http://en.wikipedia.org/wiki/Sudo) access or [udev rules configured](http://code.google.com/p/lg-v909/wiki/udev_Rules)
  1. Understanding of the GNU utility `dd` and parition layouts (See [Partitions](http://code.google.com/p/lg-v909/wiki/Partitions#Fastboot_Partition_Layout))
  1. `BusyBox` Installed (See [busybox](https://market.android.com/details?id=stericson.busybox&feature=search_result))
  1. Clockwork Recovery (CWM Method's)
  1. [Fastboot](http://goo.gl/CCUAK) (CWM Manual Method)

## Downloads ##

---

| Downloads | Mirror |
|:----------|:-------|
| Clockwork Recovery 5.5.0.4 | http://goo.gl/c8NZS |
| Fastboot Linux | http://tinyw.in/i6zP |
| Fastboot Windows | http://tinyw.in/VnhB |

## Instructions ##

---

### CWM Method -- ROM Manager (Recommended Method) - CM9 only ###

---

  * Download and flash CWM Recovery (See [downloads](http://code.google.com/p/lg-v909/wiki/Backups#Downloads), [accessing diag and recovery](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes), [partitions](http://code.google.com/p/lg-v909/wiki/Partitions#Fastboot_Partition_Layout))
```
  fastboot flash recovery recovery.img
```
> or
```
  dd if=/sdcard/recovery.img of=/dev/block/mmcblk0p5
```
  * Download and install [Rom Manager](https://market.android.com/details?id=com.koushikdutta.rommanager&feature=search_result) from the market.
  * Open Rom Manger, tap `Backup Current ROM`
  * Name your backup set
  * Tap `OK`
  * Allow root permissions if needed
  * Let [Rom Manager](https://market.android.com/details?id=com.koushikdutta.rommanager&feature=search_result) handle the rest
  * All backups are stored in:
```
  /sdcard/clockworkmod/backups/<backup_name>/
```
  * To restore, open [Rom Manager](https://market.android.com/details?id=com.koushikdutta.rommanager&feature=search_result):
```
  Manage and Restore Backups
  <backup_name>
  Restore
```

### CWM Method (Manual) ###

---

Since the bootloader of the G Slate doesn't have direct access to the recovery partition from any key combo or reboot in Honeycomb, this method requires fastboot.

  * Download the fastboot binary (See [downloads](http://code.google.com/p/lg-v909/wiki/Backups#Downloads))
  * Recommend configuring udev rules. (See [Configuring udev Rules](http://code.google.com/p/lg-v909/wiki/udev_Rules))
  * Reboot to the bootloader (fastboot) (See [accessing diag and recovery](http://code.google.com/p/lg-v909/wiki/fasboot_apx_modes))
  * Boot the recovery image:
```
  fastboot boot recovery.img
```
  * Use the `Volume +/-` buttons to navigate the menu and the `Power` button to select a menu item.
  * Go to the following menu options:
```
  Backup and Restore...
  Backup
```
  * Let CWM backup the system
  * Reboot
  * To restore, follow the same steps as above to access recovery, then:
```
  Backup and Restore...
  Restore
  <backup_name>
```

### dd Method (Data+APK's only) ###

---

  * Make sure you are rooted. (See [Rooting](http://code.google.com/p/lg-v909/wiki/Rooting))
  * Make sure to have [busybox](https://market.android.com/details?id=stericson.busybox&feature=search_result) installed from the Market.
  * Start a shell over adb and switch to root:
```
   adb shell
   su
```
  * Use `dd` to backup your data partition:
```
   dd if=/dev/block/mmcblk0p4 of=/sdcard/data.img
```
  * Store the newly created data.img in a safe place.
  * To restore your data:
```
   dd if=/sdcard/data.img of=/dev/block/mmcblk0p4
```
  * Reboot

### `MyBackup` Root Method (Data+APK's Only) ###

---

  * Download [mybackup root](https://market.android.com/details?id=com.rerware.android.MyBackupRoot&feature=search_result)
  * Make sure to have [busybox](https://market.android.com/details?id=stericson.busybox&feature=search_result) installed from the Market.
  * Change the following settings -- Open Menu -> Options:
```
   Backup Location: /sdcard
   Use root features: On
   Use BusyBox: On
   Use PM Binaries: On
   Restore Market Link: On
```
  * You set to backup /system apps too, if you do, do a separate backup with that and only backup the data and not the apk's.
  * Back out to the menu and select backup, tell it to backup the applications that you want. Then tell it, APK's+DATA to complete the backup.
  * Reboot
  * To restore your data, simply re-install mybackup root once you've re-installed your ROM and click restore. Make sure the app is pointing back to the same location you backed up to. It looks for the reware folder.

## Known Issues: ##

---

  * fastboot mode requires 25% or more battery life, otherwise it will not accept input.