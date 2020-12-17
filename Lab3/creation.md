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
git clone https://github.com/ROBOTIS-GIT/open_manipulator.git
git clone https://github.com/ROBOTIS-GIT/DynamixelSDK.git
git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench.git
git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench-msgs.git
git clone https://github.com/ROBOTIS-GIT/open_manipulator_msgs.git
git clone https://github.com/ROBOTIS-GIT/open_manipulator_simulations.git
git clone https://github.com/ROBOTIS-GIT/robotis_manipulator.git
```


While inside the robotics/src folderCreate a ros package that depends on roscpp, rospy. (will have to add other dependencies later)

```sh
catkin_create_pkg lab_3_trajectories roscpp rospy
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

move inside the package and create a folder called scripts

```sh
cd robotics/src/lab_3_trajectories
```

```sh
mkdir scripts
```

This folder will hold all the python scripts required by the nodes.