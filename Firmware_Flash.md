# Firmware Flashing and Pixhawk Setup
The PIXHAWK 4 should also contain the same firmware the Raspi contains. In order to do that we need to manually build and upload the firmware.

Download the same firmware to your computer. Before you build the firmware, navigate to below file and change the following parameter : 

```
git clone -b v1.13.0 https://github.com/PX4/PX4-Autopilot.git
nano or gedit PX4-Autopilot/boards/px4/fmu-v5/rtps.px4board
```

Update `CONFIG_MODULES_MICRODDS_CLIENT=n`

```
make px4_fmu-v5_rtps
make px4_fmu-v5_rtps upload
```

This should flash the firmware onto the PIXHAWK. We need to configure some parameters on the PIXHAWK to enable the RTPS and to inject Mocap data into it. Please update the following parameters using the QGroundControl(QGC) Software. 

| Parameter Name | Parameter Value |
| --- | --- |
|MNT_MODE_IN|RC|
|COM_PRE_ARM_MODE|Disable|
|CBRK_IO_SAFETY|22027|
|RTPS_CONFIG|TELEM 2|
|SER_TEL2_BAUD|1500000 8N1|
|EKF2_AID_MASK|24 (Vision Position Fusion & Vision Yaw Fusion)|
|EKF2_RNG_AID|Disabled|
|EKF2_HGT_MODE|Vision|
|COM_POSCTL_NAVL|1| 
|COM_OBL_ACT|Land Mode|
|COM_OF_LOSS_T|0|
|COM_OBC_LOSS_T|0|
|COM_OBL_RC_ACT|Land Mode|
|COM_RC_ACT_T|1|
|EKF2_MULTI_IMU|1|
|EKF2_MULTI_MAG|1|

Once the above parameters are set, reboot the PIXHAWK.


