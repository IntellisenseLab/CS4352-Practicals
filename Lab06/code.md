# Client Planner Python Implementation

<br>

## Planner creation

Open a terminal inside scripts folder and create a file name jplanner.py.
Copy the content from jplanner.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x jplanner.py
```

to enable execute permission.

<br>

## Client creation

Open a terminal inside scripts folder and create a file name jclient.py.
Copy the content from jclient.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x jclient.py
```

to enable execute permission.

<br>

## CMakeLists.txt file modifications

Open lab_6_jointTrajectoryPlanner/CMakeLists.txt and add following lines to the bottom of the file.

```sh
catkin_install_python(PROGRAMS scripts/jplanner.py scripts/jclient.py
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

## Simulate

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

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the JointSpaceControllerServer

```sh
cd ~/robotics/
```
```sh
source devel/setup.bash
```
```sh
rosrun lab_6_jointTrajectoryPlanner jplanner.py
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the JointSpaceControllerClient

```sh
cd ~/robotics/
```
```sh
source devel/setup.bash
```
```sh
rosrun lab_6_jointTrajectoryPlanner jclient.py
```

[<< Back to Main menu](../README.md)