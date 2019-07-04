SkyDragon OS Manifest
======================

This source is pre-set to build OP3/3T,5/5T,6/6T, if you're wanting to build for other devices there are a couple commits you need to change, please see below..


To initialize your local repository using the SkyDragon trees, use a command like this:

    repo init -u https://github.com/skydragonos/android_skydragon -b ndp

Then to sync up:

    repo sync -c -j# --force-sync --no-clone-bundle --no-tags

Build commands are:

    . build/envsetup.sh

    lunch skydragon_oneplus6t-userdebug

    time mka dragon


Things To Do
======================
If building for a device with an SOC other than SD820/SD821(MSM8996)
In vendor/skydragon/sdclang/vendorsetup.sh 
you need to change the cpu target from cortex-a57 to your correct big core cpu
so if building for op6/6t for instance, you should change to cortex-a75
then re-run '. build/envsetup.sh' before lunching and building for your device


For other devices
======================

In build/make revert this commit that hardcodes using a prebuilt kernel image in root of kernel source: 
https://gitlab.com/HolyDragonProject/android_build_make/commit/92e109ef61a7e7ba874738195f03b925734c8e0f

In your device tree, you will need to make your own commit like this one below, in order for the cpuinfo qs tile to read your soc temperature. 
Not doing so will stop the rom from building. Note that thermalzone is specific to your soc:
https://gitlab.com/HolyDragonProject/android_device_oneplus_oneplus3/commit/de6c8b2637dcd360e654616bc2663c52d91a8306

