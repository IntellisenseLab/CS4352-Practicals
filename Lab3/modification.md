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