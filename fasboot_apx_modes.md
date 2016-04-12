
# Accessing Diag and Recovery modes #

---

This document will briefly outline how to access the various diagnostic modes of the LG G Slate. You should familiarize yourself with this section before continuing onto [rooting](http://code.google.com/p/lg-v909/wiki/Rooting) or any other modification that you'd like to do.

## Prerequisites ##

---

  1. G Slate
  1. Paper clip (Pen will work also, but I don't like to give myself away. ;))

## Instructions ##

---

### Fastboot ###

---

  * Power off the device.
  * Press and hold Volume +.
  * Press the Power button.
  * Do not let go of the Volume + button until you see Yellow letters along the top talking about fastboot mode.

### APX Mode (nvflash) ###

---

Note: to use APX without any further hacking the battery has to be charged (>= 25%?)

If the battery is sufficiently charged:
  * Power off the device.
  * Press and hold Volume +/-.
  * Press the Power button.
  * The screen will look like it's off and the device is off, plug it into your computer and it should see the device as `0955:7820 NVidia Corp.`

In case the battery is dead and you cannot charge it (i.e. the tablet is utterly bricked) you will need to do some more work:
  * Open the device.
  * Disconnect the battery, power supply, USB.
  * Press and hold Volume+, Volume- and Power buttons. While holding them, connect USB.
  * Now you should see the APX device: `0955:7820 NVidia Corp.`
  * Connect power supply - without this nvflash works, but flashing always fails.

### MDP/Recovery/Download Mode ###

---

  * Power off the device.
  * Press and hold Volume -.
  * Press the Power button.
  * It will boot and a screen will pop up saying not to power the device off as it's in Download mode.

## Known Issues: ##

---

  * fastboot mode requires 25% or more battery life, otherwise it will not accept input.