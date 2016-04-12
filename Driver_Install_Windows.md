
# G-Slate/Optimus Pad Driver Install Guide #

---

## Disclaimer ##

This is a crude method that works to get your Slate recognized by your Windows 7/XP machine. The
driver that is installed is not intended for the G-Slate, but it will work as it is another LG USB driver. Also,
after the driver is installed DO NOT use the LG Software Updater to "Upgrade" your device. This is
intended for another product (LGV999). Keep in mind that this guide is a rough version of the process as I
may have missed or mixed up a step along the way. You will, however, have a general idea of what to do
if my guide isn't completely on point. ;)

---


## Prerequisites ##

---

  1. USB Cable
  1. LG Mobile Updater (See [Downloads](http://code.google.com/p/lg-v909/wiki/Driver_Install_Windows#Downloads))

## Downloads ##

---

|  LG Mobile Updater | http://goo.gl/zuM5N |
|:-------------------|:--------------------|

## Instructions ##

---

  * Download the software BC2AppSetup.exe from our Downloads section.

  * Install the Software Package ([LG Mobile Updater](http://goo.gl/zuM5N))

  * After installation you will see a button "Install USB Drivers". It will        then bring you to a drop down menu where you will select your carrier (T-Mobile).

  * After selecting your carrier you will see another drop down menu where you     will choose which driver to install. I'm sure that most of them would work but for   this guide you are going to choose "LGV999".

  * Next you will see a pop up asking to install the drivers. Keep your LG G-Slate disconnected via USB until the driver install is complete. After the install you may now plug in your   device.

  * Now you want to test that your driver install was successful. Open up your    Command   Prompt and CD to your folder containing ADB. Type "_adb devices_" and      look at the output. It will contain a bunch of numbers with the word "device" next  to it if you were successful.

  * If it was unsuccessful please uninstall the software/drivers and try again.