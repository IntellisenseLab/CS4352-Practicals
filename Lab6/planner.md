# Client Planner Python Implementation

<br>

## Planner creation

Open a terminal inside scripts folder and create a file name planner.py.
Copy the content from planner.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x planner.py
```

to enable execute permission.

<br>

## CMakeLists.txt file modifications

Open lab_6_jointTrajectoryPlanner/CMakeLists.txt and add following lines to the bottom of the file.

```sh
catkin_install_python(PROGRAMS scripts/planner.py
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

## Run the Planner

Go to root of the workspace and run

```sh
roscore
```

Go to root of the workspace and on a new terminal

```sh
cd ~/robotics/
```
```sh
source devel/setup.bash
```
```sh
rosrun lab_6_jointTrajectoryPlanner planner.py
```


[<< Back to Main menu](../README.md)