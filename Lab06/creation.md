# Package Creation

Move inside the ROS workspace and Create a ros package that depends on rospy, roscpp, std_msgs, sensor_msgs, open_manipulator_msgs.

Assuming workspace name is 'robotics'

```sh
cd robotics/src
```

```sh
catkin_create_pkg lab_6_jointTrajectoryPlanner rospy roscpp std_msgs sensor_msgs open_manipulator_msgs
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
cd robotics/src/lab_6_jointTrajectoryPlanner
```

```sh
mkdir scripts
```

This folder will hold all the python scripts required by the nodes.

[<< Back to Main menu](../README.md)