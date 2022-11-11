# RASPBERRY PI 4 Setup
Instrucions to Setup Raspberry Pi 4

## UBUNTU 20.04 LTS Installation 
The Raspberry Pi has only the Ubuntu 20.04 Server version available for install. This is a minimal version of Ubuntu with no GUI. This is fine for our purposes. But still you can install the GUI with a single line command. 



- Download the Ubuntu 20.04.5 LTS (Focal Fossa) server image from [here](https://cdimage.ubuntu.com/releases/20.04/release/ubuntu-20.04.5-preinstalled-server-arm64+raspi.img.xz).
- User [Etcher](https://www.balena.io/etcher/) or [Raspberry Pi Imager](https://downloads.raspberrypi.org/imager/imager_latest.exe) to flash the image to the SD card.
- Insert the SD card into the Raspberry Pi and power it on.
- Connect a Display, Keyborad and Mouse to Raspberry Pi. The default username is `ubuntu` and the default password is `ubuntu`.
- The process will ask you to change the password. Change the password to something you can remember.
- Connect the Raspberry Pi to the internet using an ethernet cable.
- Run `sudo apt update` and `sudo apt upgrade` to update the packages.

