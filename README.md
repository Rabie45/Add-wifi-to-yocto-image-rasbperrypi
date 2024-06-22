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
  
