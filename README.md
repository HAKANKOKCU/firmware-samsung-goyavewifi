# Samsung-goyavewifi firmware
Firmware for postmarketOS. 
I added these mostly to the wiki too.

# WiFi
Do these as root
* Make /system/etc folder
  ```shell
  mkdir /system
  mkdir /system/etc
  ```
* Copy /wifi to /system/etc
* OPTIONAL:
  * You can make it mount /efs and mkdir /data if you wanna make dmesg logs "happy":
    ```shell
    # /etc/local.d/wifi.start +x
    mkdir /efs
    mkdir /data
    mount /dev/disk/by-partlabel/efs /efs
    echo 2 > /data/.psm.info # I don't know what this number means
    ```
# Audio
* These are packaged in postmarketOS repos
* Install package `soc-sprd-audio-sc8830` package
* Edit `/etc/asound.conf`, add these lines:
  ```config
  defaults.ctl.card 1
  defaults.pcm.card 1
  defaults.pcm.device 1
  ```
* Edit `/etc/pulse/default.pa`, change `load-module module-udev-detect` to `load-module module-udev-detect tsched=0`
# Bluetooth (!)
IDK, dmesg doesn't show something useful(?)
