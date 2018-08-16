SkyDragon OS Manifest
======================

To initialize your local repository using the SkyDragon trees, use a command like this:

    repo init -u https://github.com/holydragonproject/android_manifest.git -b ndp

Then to sync up:

    repo sync -c -j# --force-sync --no-clone-bundle --no-tags

Build commands are:

    . build/envsetup.sh

    lunch skydragon_oneplus3-userdebug

    time mka otapackage

