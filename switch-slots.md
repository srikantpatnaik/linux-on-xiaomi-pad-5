# Switch Slots

## Android(slot A) to Linux(slot B)

Install the APK from [here](https://github.com/gibcheesepuffs/Switch-My-Slot-Android/releases/tag/v0.7.1) and install the Magisk 
module from [here](https://github.com/roihershberg/bootctl-binary/releases/tag/v2.2). Use the app to switch the slot.

## Linux(slot B) to Android(slot A)

1. `sudo apk add qbootctl`

2. `sudo qbootctl -s a && sudo reboot`


