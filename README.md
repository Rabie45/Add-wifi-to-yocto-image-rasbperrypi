# Add-wifi-to-yocto-image-rasbperrypi

## Steps 
  - Go to your ```bblayers.conf``` in your build folder
  - Add this lines \
```
PATH/poky/meta-openembedded/meta-oe \
PATH/poky/meta-openembedded/meta-python \
PATH/poky/meta-openembedded/meta-networking \
``` 
  - Then go to ```local.conf```  add
```
DISTRO_FEATURES:append = " bluez5 bluetooth wifi"
IMAGE_INSTALL:append = " linux-firmware-rpidistro-bcm43430 bluez5 wpa-supplicant"
```
  - If u got error like this ```Correct Layer Versions: Ensure the layers are compatible with your Yocto release version. If there are compatibility issues, check out the correct branch of the meta-openembedded repository that matches your Yocto version (e.g., kirkstone). ``` make sure to go to ```meta-openembedded``` layer ```cd PATH/poky/meta-openembedded/``` and wtite this command ```git checkout kirkstone``` if u r using  kirkstone (or write ur branch name zeus or kgrouth...)

## Core-image-base
 - I tryed to add wifi with core-image-minimal it didnt work and it wanst smart enough so i tried base and it worked
 - After installing the image in the SDcard go to this path ```/etc/wpa_supplicant.conf``` and add ur user_name of wifi and password
 -
  ```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1

network={
    ssid="YourNetworkSSID"
    psk="YourNetworkPassword"
}
   ```
- And save but ur card in raspberry pi
- After powering up and booting write this three commands
```
/usr/sbin/wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf
ifconfig wlan0 up
udhcpc -i wlan0
```

  ![Screenshot from 2024-07-14 16-07-19](https://github.com/user-attachments/assets/cc4fd21a-b546-4a3b-ba65-46927306fe8b)
- Now u can access with ssh with the ip given 

