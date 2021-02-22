# Task Client Python Implementation

<br>

## Task Client creation

Open a terminal inside scripts folder and create a file name task_client.py.
Copy the content from task_client.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x task_client.py
```

to enable execute permission.

<br>

## CMakeLists.txt file modifications

Open lab_5_taskspacecontrol/CMakeLists.txt and add following lines to the bottom of the file.

```sh
catkin_install_python(PROGRAMS scripts/task_client.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

```

## Build the code 

Go to root of the workspace

```sh
cd ~/robotics/
```
```sh
catkin build
```
or
```sh
catkin_make
```

## Run the Task Client

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo simulation

```sh
cd robotics
```

```sh
source devel/setup.bash
```

```sh
roslaunch open_manipulator_gazebo open_manipulator_gazebo.launch
```

Start the simulation by pressing the "play" button in the lower part of the screen.

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo controller

```sh
cd robotics
```

```sh
source devel/setup.bash
```

```sh
roslaunch open_manipulator_controller open_manipulator_controller.launch use_platform:=false
```

Go to root of the workspace and on a new terminal

```sh
cd robotics
```
```sh
source devel/setup.bash
```
```sh
rosrun lab_5_taskspacecontrol task_client.py
```

[<< Back to Main menu](../README.md)
