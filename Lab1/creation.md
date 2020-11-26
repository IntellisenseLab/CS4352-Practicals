# Package Creation

Move inside the ROS workspace and Create a ros package that depends on TF, roscpp, rospy, turtlesim.

Assuming workspace name is 'robotics'

```sh
cd robotics/src
```

```sh
catkin_create_pkg lab_1_tf tf roscpp rospy turtlesim
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
cd robotics/src/lab_1_tf
```

```sh
mkdir scripts
```

This folder will hold all the python scripts required by the nodes.