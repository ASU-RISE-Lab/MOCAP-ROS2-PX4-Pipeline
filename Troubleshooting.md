# Troubleshooting

## Error from `sudo apt get update for ROS`

This is generally due to the old key. Do the following:

Delete the keys:
```
sudo apt-key del 421C365BD9FF1F717815A3895523BAEEB01FA116
```

Add the keys:
```
sudo -E apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
Now do
```
$sudo apt clean && sudo apt update
$sudo apt install
```

## Colcon build doesn’t show anything while building PX4-Autopilot

This is because git submodules need to be updated and it is waiting for your input. To fix this always try verbose while building so you can see the prompts: 
```
colcon build --packages-select px4_msgs px4_ros_com px4 --event-handlers console_direct+ 
```
This will let you see the prompts and respond to it. Generally, I do “u + enter”, feel free to do whatever you think is suitable.

## ROS1 – ROS2 Conflict

Source the ROS2 Workspace every time you open a terminal if you had not added the source to .bashrc file. Also, please note that either ROS1 or ROS2 can be used. So, source your ROS directory as required. 

`source /opt/ros/foxy/setup.bash`

## If PX4-Autopilot build fails or pops random Errors

```
make distclean
make clean 
make px4_fmu-v5_rtps
make px4_fmu-v5_rtps upload
```

## SSH Server Setup 
```
sudo apt install openssh-server
sudo systemctl status ssh
sudo ufw allow ssh
```

## Raspberry Pi High CPU Usage

If you had installed the GUI for the Raspberry Pi, it would conusme a lot of CPU. So, it is recommended to use the headless mode.

In that case refer to this website to disable it : [GDM](https://wiki.debian.org/GDM)


