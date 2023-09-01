# Partition and Install PostmarketOS (Alpine Linux)

* Wait for 15 days to unlock your tablet (unlock will remove all user data!)

* Get the recovery image (not be FLASHED) `wget https://github.com/serdeliuk/xiaomi-nabu-orangefox/releases/download/2/xiaomi-nabu-orangefox.0.0.2.zip`

* `unzip xiaomi-nabu-orangefox.0.0.2.zip`

* `adb reboot bootloader`

* Now when `FASTBOOT` appear on screen then run `fastboot boot xiaomi-nabu-orangefox.img` from your host

* Check the userdata partition number `parted /dev/block/sda`

* Inside parted `print` to view partitions and then remove userdata partition `rm 31`

* Inside parted the 30th partition ends at 10.9GB and for 256GB version of tablet one can use 
`mkpart userdata   10.9GB 100GB`. This shall create ~90GB userdata partition and rest will be kept for `pmos`.

* Inside parted now create `pmos` partition `mkpart pmos ext4 100GB 250GB`

* Inside parted check the free space `print free` if it shows a few GBs then you might go back and adjust your partitions, if not, do `quit` and reboot.

* The reboot should land you to recovery screen, select WIPE USERDATA and reboot to Android with new userdata partition

* Connect `adb` and do `adb reboot bootloader` again

* Now when `FASTBOOT` appears on screen run `fastboot getvar current-slot`. This usually should print `a`, this means the Android uses `slot a`, this also means that `slot b` could be used for `pmos`

* There are 3 partitions involved to boot pmos? boot, vbmeta, dtbo? (need more info)

* `fastboot set_active b`

* Download the pmos preview image from [here](https://github.com/serdeliuk/xiaomi-nabu-postmarketos/releases/download/6.1.10/xiaomi-nabu-pmos-preview.6.1.10.tar.gz)

* Extract the above tar file and `cd` 

* Flash the modified vbmeta to disable the boot verification process `fastboot flash vbmeta_b vbmeta_disabled.img`

* Erase `dtbo_b` to prevent interfering with pmos `fastboot erase dtbo_b`

* Flash Linux Kernel to `slot b` boot region `fastboot flash boot_b boot.img`
    (You may use alternate kernel from [here](https://forum.xda-developers.com/attachments/boot-img.5834319/) which contains 
    `CONFIG_SCSI_UFS_BSG` for switching slots using `qbootctl`)

* Now flash prebuilt Alpine image (pmos) `fastboot flash pmos xiaomi-nabu.img` 

* Once done `fastboot reboot` to get into `KDE Desktop`.

* Default user is `user` and password is `147147` [details](https://forum.xda-developers.com/t/rom-postmarketos-linux-boot-on-xiaomi-pad-5-nabu.4454143/)

