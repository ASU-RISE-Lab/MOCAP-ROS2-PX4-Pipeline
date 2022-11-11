# RASPBERRY PI 4 Setup
Instrucions to Setup Raspberry Pi 4

## Table of Contents
1. [UBUNTU 20.04 LTS Installation](##ubuntu_20.04_lts_installation)
2. [WiFi Setup](##wifi_setup)



## UBUNTU 20.04 LTS Installation 
The Raspberry Pi supports only the Ubuntu 20.04 Server version. This is a minimal version of Ubuntu with no GUI. This is fine for our purposes. But still you can install the GUI with a single line command. 

- Download the Ubuntu 20.04.5 LTS (Focal Fossa) server image from [here](https://cdimage.ubuntu.com/releases/20.04/release/ubuntu-20.04.5-preinstalled-server-arm64+raspi.img.xz).
- User [Etcher](https://www.balena.io/etcher/) or [Raspberry Pi Imager](https://downloads.raspberrypi.org/imager/imager_latest.exe) to flash the image to the SD card.
- Insert the SD card into the Raspberry Pi and power it on.
- Connect a Display, Keyborad and Mouse to Raspberry Pi. The default username is `ubuntu` and the default password is `ubuntu`.
- The process will ask you to change the password. Change the password to something you can remember.
- Connect the Raspberry Pi to the internet using an ethernet cable.
- Run `sudo apt update` and `sudo apt upgrade` to update the packages.
- Run `sudo apt install ubuntu-desktop` to install the GUI.
- Reboot the Raspberry Pi with `sudo reboot`.
- Now you should have a GUI and you can login with the username and password you set earlier.

## WiFi Driver Setup
The Raspberry Pi 4 has an inbuilt WiFi module. But it has occasional spikes of latency and not relaible for our purposes. So we will use an external USB WiFi dongle. We use the EDUP AC600M USB Wi-fi Dongle over the 5GHz band.

We use the [rtl8812au](https://github.com/Aravind-Adhith/rtl8812au) driver for the WiFi dongle.

- In the [Makefile](https://github.com/Aravind-Adhith/rtl8812au/blob/master/Makefile) we have changed the `CONFIG_PLATFORM_I386_PC = y` to `CONFIG_PLATFORM_ARM_RPI = y`. This is to build the driver for the Raspberry Pi.

Continue with instrucion in the [Repo](https://github.com/Aravind-Adhith/rtl8812au) to install the driver.
