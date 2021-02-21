# Package Configuration

This practical depends on PX4 as Flightstack and Mavlink as communication stack. This implements a controller that works alogside MAVROS to guide the drone.

Create a new folder called PX4 inside home directory

## Install PX$ FlightStack/Autopilot system

```sh
cd PX4
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

Then to install dependencies

```sh
cd PX4-Autopilot

bash ./Tools/setup/ubuntu.sh --no-nuttx --no-sim-tools
```

## Install FAST DDS

```sh
cd PX4

#For melodic
git clone --recursive https://github.com/eProsima/Fast-DDS.git -b v1.8.2 FastDDS-1.8.2
cd FastDDS-1.8.2
mkdir build && cd build

#For noetic
git clone --recursive https://github.com/eProsima/Fast-DDS.git -b v2.0.0 FastDDS-2.0.0
cd FastDDS-2.0.0
mkdir build && cd build
```

Then run 

```sh
cmake -DTHIRDPARTY=ON -DSECURITY=ON ..
make -j$(nproc --all)
sudo make install
```

Finally,

```sh
cd PX4

git clone --recursive https://github.com/eProsima/Fast-DDS-Gen.git -b v1.0.4 Fast-RTPS-Gen \
    && cd Fast-RTPS-Gen \
    && ./gradlew assemble \
    && sudo ./gradlew install
```
## Ros related setup

Create and Move to a new subfolder folder run the following commands,
 
```sh
mkdir -p px4_ros/src
cd px4_ros

catkin init

wstool init src
```

wstools is used to retrieve source files and catkin and rosinstall are used to build them

```sh
sudo apt-get install python-catkin-tools python-rosinstall-generator -y
```

## Install mavlink 

Kinect reference is used because its the most updated and since mavlink is not distro specific.

```sh
rosinstall_generator --rosdistro kinetic mavlink | tee /tmp/mavros.rosinstall
```

## Install MAVROS

```sh
rosinstall_generator --upstream mavros | tee -a /tmp/mavros.rosinstall
```

## Setup dependencies

```sh
wstool merge -t src /tmp/mavros.rosinstall
wstool update -t src -j4
rosdep install --from-paths src --ignore-src -y
```

```sh
sudo ./src/mavros/mavros/scripts/install_geographiclib_datasets.sh
```

## Additional Dependencies for Gazebo simulation

```sh
sudo apt-get install libprotobuf-dev libprotoc-dev protobuf-compiler libeigen3-dev libxml2-utils python-rospkg python-jinja2
```

```sh
sudo apt-get install libgstreamer-plugins-base1.0-dev gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly -y
```

## Build

```sh
catkin build
```

## Setting variables

```sh
source devel/setup.bash
```

## Testing the setup in JMAVSim

Move into PX4-Autopilot folder and run,

```sh
make px4_sitl jmavsim
```

Then run following command to operate the drone.

```sh
commander takeoff   #To takeoff
```

## Testing the setup in Gazebo

Move into PX4-Autopilot folder and run,

```sh
DONT_RUN=1 make px4_sitl_default gazebo
source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo
roslaunch px4 posix_sitl.launch
```

Then run following command to operate the drone.

```sh
commander takeoff   #To takeoff
```

This is based on the [PX4 guide](https://docs.px4.io/master/en/ros/mavros_installation.html)

[<< Back to Main menu](../README.md)
