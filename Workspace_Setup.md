# Workspace Setup

## Table of Contents
1. [PX4 - ROS2 Packages](#px4---ros2-packages)
2. [VRPN - ROS2 Packages](#vrpn---ros2-packages)
3. [MoCAP Setup and Configuration](#mocap-setup-and-configuration)

## **PX4 - ROS2 Packages**

- Clone the following repositories into the `src` folder of the `Colcon_ws` workspace.

```
git clone -b PX4-Autopilot-v1.13.0 git@github.com:ASU-RISE-Lab/px4_msgs.git
git clone -b PX4-Autopilot-v1.13.0 git@github.com:ASU-RISE-Lab/px4_ros_com.git
git clone -b v1.13.0 https://github.com/PX4/PX4-Autopilot.git --recursive
```

- Verify that the repos are corrent by verifying the below SHA1 hashes.

```
cd package_name
git rev-parse HEAD
```
- PX4-Autopilot - `6823cbc4140e29568f00e1211ae60e057adb1a1f`

<!-- - PX4_MSGS - `7f89976091235579633935b7ccaab68b2debbe19`

- PX4_ROS_COM - `1562ff30d56b7ba26e4d2436724490f900cc2375` -->

## The following is described only for understanding and not required for the setup.

------------------------------------------------------------------------------------------

The PX4_MSGS repo will have the corresponsing messages for the PX4-Autopilot v.1.13.0. 

This was done using the follwing command:

```
cd ~/colcon_ws/src/PX4-Autopilot/msg/tools
mkdir px4_msgs
python3 uorb_to_ros_msgs.py ~/colcon_ws/src/PX4-Autopilot/msg/ px4_msgs/
```
This should have generate the messages in the px4_msgs folder. Copy those files and paste in the following directory `~/colcon_ws/src/px4_msgs/msg`, please delete the previous messages before copying the new ones.  

Similarly, the PX4_ROS_COM repo will have the corresponsing .yaml file for the PX4-Autopilot v.1.13.0.

This was done using the follwing command:
    
```
cd ~/colcon_ws/src/PX4-Autopilot/msg/tools
python3 uorb_to_ros_urtps_topics.py -i urtps_bridge_topics.yaml -o new_rtps_ids.yaml
```
The above command would have generated a file name new_rtps_ids.yaml which is to be copied and pasted in the `~/colcon_ws/src/px4_ros_com/templates` folder. There will a file named urtps_bridge_topics.yaml in that directory, please replace the newly generated file with that and renaming it to the same. 

------------------------------------------------------------------------------------------

## Building the PX4 - ROS2 Packages

```
cd ~/colcon_ws/
source install/setup.bash
source /opt/ros/foxy/setup.bash
colcon build --packages-select px4_msgs px4_ros_com px4 --event-handlers console_direct+
```

## **VRPN - ROS2 Packages**

- Clone the following repositories into the `src` folder of the `Colcon_ws` workspace.

```
git clone git@github.com:ASU-RISE-Lab/vrpn.git
git clone git@github.com:ASU-RISE-Lab/vrpn_client_ros.git
git clone git@github.com:ASU-RISE-Lab/px4_vrpn.git
```
## Building the VRPN - ROS2 Packages

```
cd ~/colcon_ws/
colcon build --packages-select vrpn --event-handlers console_direct+
source install/setup.bash
colcon build --packages-select vrpn_client_ros --event-handlers console_direct+
source install/setup.bash
colcon build --packages-select px4_vrpn_pubsub --event-handlers console_direct+
```

## **MoCAP Setup and Configuration**

Create the Rigid Body of your drone in the Optitrack software named “RigidBody1”

`nano or gedit ~/colcon_ws/src/vrpn_client_ros/config/sample.params.yaml`

Update the “server:10.203.53.82” to the IP address of your MoCAP system.

