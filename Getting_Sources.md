
# Getting CM10 sources with LGE G-Slate v909 specific code #

---

  1. Install sun-java:
```
sudo add-apt-repository ppa:flexiondotorg/java; sudo apt-get update; sudo apt-get install sun-java-6-jdk
```
  1. Install necessary dependancies (ONLY 64-bit systems supported for compilation):
```
sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.6-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev sun-java6-jdk pngcrush schedtool g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline5-dev gcc-4.3-multilib g++-4.3-multilib
```
  1. Make needed directories:
```
mkdir -p ~/bin
mkdir -p ~/android/system
```
  1. Add needed paths to your bashrc (Make sure to edit the path\_to/ to match the location with your sdk installation):
```
echo "export CCOMPILER=${HOME}/android/system/prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin/arm-eabi-" >> ~/.bashrc
echo "export PATH=${PATH}:path_to/android-sdk/platforms:path_to/android-sdk/tools:path_to/android-sdk/platform-tools:~/bin:~/android/system/prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin" >> ~/.bashrc
```
  1. Install the repo:
```
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
  1. Initialize repo for JB sources:
```
cd ~/android/system/
repo init -u git://github.com/CyanogenMod/android.git -b jellybean
```
  1. create ~/android/system/.repo/local\_manifest.xml with the following contents:
```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="gslate-cm9/android_vendor_lge_v909" path="vendor/lge/v909" remote="github" revision="jellybean" />
  <remote fetch="git://github.com/CyanogenMod/" name="CyanogenMod" review="review.cyanogenmod.com" />
  <project name="CyanogenMod/android_device_lge_v909" path="device/lge/v909" remote="github" revision="jellybean" />
  <project name="CyanogenMod/android_kernel_lge_v909" path="kernel/lge/v909" remote="github" revision="jellybean" />
</manifest>
```
  1. Edit with your favorite editor, ~/android/system/vendor/cm/jenkins-build-targets and add our tablet:
```
cm_v909-userdebug
```
  1. checkout all the code (this can take a couple of hours or more):
```
repo sync
```

Later, when you want to update your sources, just do:
```
cd ~/android/system/
repo sync
```