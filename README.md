# RASPBERRY PI 4 - PX4 - MOCAP SETUP
A Repo to guide you through setup of Raspberry Pi to be used in MOCAP Space

## Table of Contents

1. [Components List](##components_list)
2. [Raspberry Pi Setup](Raspbery_Pi_Setup.md)
3. [Fast DDS and Fast-DDS-Gen Installation](Fast_DDS.md)
4. [ROS 2 Foxy Installation](ROS_2.md)
5. [Workspace Structure Overview](##workspace_structure_overview)
6. [Workspace Setup](Workspace_Setup.md)
7. [Firmware Flashing and Pixhawk Setup](Firmware_Flash.md)
8. [Launching the MicroRTPS Agent and VRPN Nodes](Launching.md)
9. [Troubleshooting](Troubleshooting.md)

## Components List
1. [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)
2. [EDUP AC600M USB Wi-fi Dongle](https://www.amazon.com/Adapter-Wireless-Network-External-OS10-6-10-13/dp/B019SRBUNG/ref=sr_1_8?dchild=1&keywords=edup+wifi+module&qid=1622580522&sr=8-8)
3. [TTL-232 USB Serial Adapter - 5V](https://www.digikey.com/en/products/detail/ftdi,-future-technology-devices-international-ltd/TTL-232R-5V-PCB/1836395?utm_adgroup=Adapters%2C%20Converters&utm_source=google&utm_medium=cpc&utm_campaign=Shopping_Product_Computer%20Equipment_NEW&utm_term=&utm_content=Adapters%2C%20Converters&gclid=Cj0KCQiAgribBhDkARIsAASA5bteGEQyTV42-7hkcruJWAl1t5A19p2Kl3ol-miOGzfpyiQN3Hh26wgaArcIEALw_wcB) or [TTL-232 USB Serial Adapter - 3V3](https://www.digikey.com/en/products/detail/ftdi-future-technology-devices-international-ltd/TTL-232R-3V3-PCB/1836396)
4. [Pixhawk Cable Set](https://www.getfpv.com/holybro-pixhawk-5x-cable-set.html?gclid=Cj0KCQiAgribBhDkARIsAASA5buqjVeZrVoAVQoCIZTKD5rzX0lMi5KUl-bz913E4Abji5LsPsZgydoaAvchEALw_wcB)
5. Power Adapter
6. [Telemetry Module](https://shop.holybro.com/sik-telemetry-radio-v3_p1103.html?)

## Raspberry Pi Setup

Follow the instructions in the [Raspbery_Pi_Setup.md](Raspbery_Pi_Setup.md) file to setup the Raspberry Pi.

## Fast DDS and Fast-DDS-Gen Installation

Follow the instructions in the [Fast DDS](Fast_DDS.md) page to install Fast DDS and Fast-DDS-Gen.

## ROS 2 Foxy Installation

Follow the instructions in the [Ros2 Foxy](ROS_2.md) page to install ROS 2 Foxy and setup the workspace.

## Workspace Structure Overview

The workspace structure is as follows and should almost similar to this.

    home
    ├───Fast-DDS
        ├───foonathan_memory_vendor
        ├───FAST-CDR
        ├───FAST-DDS
    ├───Fast-DDS-Gen
    ├───Colcon_ws
        ├───build
        ├───install
        ├───log
        ├───src
            ├───custom_packages
            ├───px4_msgs
            ├───px4_ros_com
            ├───PX4-Autopilot
            ├───vrpn
            ├───vrpn_client_ros

## Workspace Setup

Follow the instructions in the [Workspace Setup](Workspace_Setup.md) to create the required packages and setup the environment. 

## Firmware Flashing and Pixhawk Setup

Follow the instructions in the [Firmware Flashing and Pixhawk Setup](Firmware_Flash.md) to flash the firmware and setup the Pixhawk.

## Launching the MicroRTPS Agent and VRPN Nodes

Follow the instructions in the [Launching the MicroRTPS Agent and VRPN Nodes](Launching.md) to launch the MicroRTPS Agent and VRPN Nodes.

## Troubleshooting

Check this [Troubleshooting](Troubleshooting.md) page for common issues and their solutions.