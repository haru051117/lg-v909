
# Building the Kernel #

---


## Prerequisites ##

---

  * toolchain for arm
    * you can use the prebuilt toolchain from android sources
    * you need to know where the toolchain is located and its "name prefix", for the android toolchain:
      * location: your-android-sources/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin/
      * the prefix of the tools is "arm-eabi-" (the thing that comes before eg. gcc and ld in the names of the tools)
  * kernel source - get it from git://github.com/ChiefzReloaded/lge-kernel-startablet-new for Honeycomb or git://github.com/gslate-cm9/android\_kernel\_lge\_v909.git for CM9

## Building ##

---

  * clone the kernel Honeycomb repo:
```
git clone https://github.com/ChiefzReloaded/lge-kernel-startablet-new
```
  * or clone the kernel Ice Cream Sandwich repo:
```
git clone git://github.com/gslate-cm9/android_kernel_lge_v909.git
```
  * go to the kernel directory:
```
cd lge-kernel-startablet-new
or
cd android_kernel_lge_v909
```
  * the recommended configuration is already present in .config, so if you only want to build that, you don't have to configure the kernel
  * set up cross-compilation, e.g.:
```
export ARCH=arm
export CROSS_COMPILE=arm-linux-androideabi-
PATH=your-android-sources/prebuilt/linux-x86/toolchain/arm-eabi-4.4.3/bin/:$PATH
```
(CROSS\_COMPILE needs to be set to the "name prefix" - see above; this is example for the android toolchain)
  * run the build:
```
make zImage
```
  * if all is successful, this should produce a zImage in arch/arm/boot/. To actually you this image, you need to make a fastboot image out of this (for that you need an initramfs and the mkbootimg android utility). If you want to use this with android build (e.g. for recovery) use the produced zImage to overwrite arch/arm/boot/kernel and rebuild the relevant android image (recovery). -- See Building\_Recovery.

## Configuring the Kernel ##

---

Just do:
```
ARCH=arm make menuconfig
```

# New kernel repo #

While the git repo mentioned above workd well (so use that if you just want a working kernel), ideally the LGE changes could be put on top of the nvidia Tegra kernel repo and then we could - if we're extra lucky - rebase it on top of something newer.

An attempt was started at http://repo.or.cz/w/nv-tegra-linux-2.6/startablet-kernel.git.

There are two interesting branches:
  * LGV909DW - based on the older LGE tarball. Produces non-working kernel.
  * LGV909DWV10O - based on the newer LGE tarball. Produces a working kernel.

(The defconfings/.config were not updated - use the one from CR's repo mentioned above.)

There's some work ongoing on cleaning this up. Talk to us in [IRC](irc.md) if you are interested in this.