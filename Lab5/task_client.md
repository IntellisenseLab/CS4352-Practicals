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
rosrun lab_5_taskspacecontrol task_client.py
```