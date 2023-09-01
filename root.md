# Root and Magisk

1. Get the original factory firmware(android OS) for your region, in our case download 
   the fastboot version from [here](https://xiaomifirmwareupdater.com/miui/nabu/)

2. Extract the firmware and navigate to `images` directory. 

3. `adb push boot.img /sdcard`

4. Install `Magisk` from [here](https://github.com/topjohnwu/Magisk/releases)

5. In the Magisk app click on the first install from the top right then do `select and patch a file`

6. Do `adb pull /storage/emulated/0/Download/magisk_patched-xxxx_xxxx.img`

7. Restart device `adb reboot bootloader`

8. `fastboot flash boot magisk_patched-xxxx_xxxx.img`

9. `fastboot reboot` and done

Technically, this process could be repeated for other devices as well. 

