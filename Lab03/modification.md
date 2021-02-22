# Modification

Open the manipulator/open_manipulator/open_manipulator_control_gui and open launch/open_manipulator_control_gui.launch

Replace 

```sh
<arg name="robot_name"   default="open_manipulaotr"/>
```
with

```sh
<arg name="robot_name"   default=""/>
```

save and move to workspace root and re build the workspace

```sh
cd robotics
```

```sh
catkin build
```

or 

```sh
catkin_make
```

Install following package if you get following error,

Error:

```sh
Could not load controller 'gripper_sub_position' because controller type 'effort_controllers/JointPositionController' does not exist.
```

Package to be installed:

```sh
sudo apt-get install ros-melodic-effort-controllers
```

[<< Back to Main menu](../README.md)