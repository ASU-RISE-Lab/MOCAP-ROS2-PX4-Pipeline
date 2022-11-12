# [ROS 2 Foxy](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html) Installation

A Barebone Installation should be fine. 

## Set Locale should be UTF-8

```
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings

sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl gnupg2 lsb-release

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update
sudo apt upgrade
```

## Install ROS 2 Foxy

Barebone Version : 
```
sudo apt install ros-foxy-ros-base`
```

Complete Install : 
```
sudo apt install ros-foxy-desktop
```

Source your Install : 
```
source /opt/ros/foxy/setup.bash
```

If you prefer add it to your .bashrc file (This is not mandatory you still can source it every time)

After installation, cross check by typing the following in a new terminal after sourcing: 
```
dpkg -s ros-foxy-fastrtps 2>/dev/null | grep -i version
```

It should returm something not empty and of the following sort: `2.1.1-1focal.20211014.171109`


## Workspace Creation

Create a workspace : 

```
cd
mkdir -p ~/colcon_ws/src
cd ~/colcon_ws/src
```
You can git clone packages into this directory prior to building it.

Build the packages using the following commands : 
```
cd ~/colcon_ws
colcon build --packages-select pkg_name --event-handlers console_direct+ 
```
or 
```
colcon build --event-handlers console_direct+
```

Build Sourcing your ROS2 Environment and Personal Workspace:

```
source /opt/ros/foxy/setup.bash
cd ~/colcon_ws
.install/local_setup.bash
```
**Note**: It is the same as sourcing colcon_ws’ setup.bash file (just that this sequential process gives you more flexibility instead of directly sourcing the overlay and underlay by the same command)
