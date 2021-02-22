# Dependency installation

Run the following command to setup dependencies required for the open manipulator

```sh
sudo apt-get install ros-melodic-ros-controllers ros-melodic-gazebo* ros-melodic-moveit* ros-melodic-industrial-core
```

# Package Creation

Move inside the ROS workspace and clone open manipulator package

Assuming workspace name is 'robotics'

```sh
cd robotics/src
```

```sh
mkdir manipulator
```

```sh
cd manipulator
```

```sh
git clone https://github.com/ROBOTIS-GIT/DynamixelSDK.git
git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench.git
git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench-msgs.git
git clone https://github.com/ROBOTIS-GIT/open_manipulator.git
git clone https://github.com/ROBOTIS-GIT/open_manipulator_msgs.git
git clone https://github.com/ROBOTIS-GIT/open_manipulator_simulations.git
git clone https://github.com/ROBOTIS-GIT/robotis_manipulator.git
```

Move to workspace root and build the package

```sh
cd ..
```

```sh
catkin build
```

or 

```sh
catkin_make
```


[<< Back to Main menu](../README.md)