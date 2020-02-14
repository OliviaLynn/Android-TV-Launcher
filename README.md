# Android TV Launcher (Installation)
<img src="https://img.shields.io/badge/android-9 (Pie)-blue"> <img src="https://img.shields.io/badge/unity-2017.4.34f1-blue"> <img src="https://img.shields.io/badge/maintained%3F-yes-green" /> <img src="https://img.shields.io/github/issues/OliviaLynn/Android-TV-Launcher-Installation" /> 

## Installation Instructions

This is a manual for installing a (private) launcher on an Android TV. To make your own launcher, check out this boilerplate [here](https://github.com/OliviaLynn/Android-TV-Launcher-Boilerplate).

### Prerequisites

- This was built in **Unity 2017.4.34f** (but I don't expect it to make much of a difference).
- This was built for a **Greatlizard Android TV**, while following instructions written for Shield TV (I also don't expect this to make much of a difference).
- Our Android TVs are running **Android 9 (Pie)**, so the following adb commands are for this version.

### On Your Android TV

- **Get device's IP.** This should be under Settings > Device Preferences > About > Status > IP address
- **Turn on developer mode.** Go to Settings > Device Preferences > About, find the item called "Build," and click it 7 times. You should see a pop-up telling you you are now in developer mode.
- **Turn on USB debugging.** Under Settings > Device Preferences, you should now see an item called "Developer options." Click that and make sure "USB debugging" is toggled on. (If you later on have trouble connecting to this device, you may have to come back to this and turn it off and on again.)
- **Install a backup launcher.** I personally use the free version of ATV Launcher, but anything should work.
- **Install the main launcher.** Plug in a USB stick that contains your launcher's .apk, and install the launcher. Once you're done, now is the most convenient time to unmount the USB and set it aside.
- **Also,** make sure you have some sort of way to launch the backup launcher from your main launcher. It could be a keyboard shortcut or a corner of the screen you click, but it will save you from some major headaches to have this while you're still developing and debugging your own launcher.

### On Your Computer

- **Make sure your computer is on the same wifi as your device.**
- **Make sure you've got adb installed on your computer.**
- **In your shell, run `adb connect [your Android TV's IP]`**
- **Make sure you really did install the backup launcher.**
- **In your shell, run `adb shell pm list packages`**
- **Find which of those packages is your device's default launcher.** For example, mine was 'com.oranth.tvlauncher'
- **In your shell, run `adb shell pm uninstall -k --user 0 [your device's default launcher]`.** This should remove the default launcher, letting you set your own launcher as the new default. Sometimes it won't work the first time, and you need to run this again. You can check that the package has been removed by re-running the `list packages` command.
- **Turn your device off and on again.**
- **You should see a popup asking what default home screen you want,** either a blank app or the "settings" app. Click the blank app and choose "always"
- **You should see another popup with the same question,** this time between your (new) main launcher and your backup launcher. Click your main launcher and choose "always."
- **Restart your device and make sure these preferences have been set properly.** If they have, the device should go straight to your main launcher right after it boots.
