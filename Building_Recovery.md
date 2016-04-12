
# Building CWM Recovery #

---


## Prerequisites ##

---

  * [Gettting sources](Getting_Sources.md)

## Building the image ##

---

  1. . build/envsetup.sh
  1. lunch cm\_v909-eng
  1. make -j4 recoveryimage

## Running the image ##

---

  1. boot into fastboot
  1. then do:
```
fastboot boot ~/android/system/out/target/product/v909/recovery.img
```