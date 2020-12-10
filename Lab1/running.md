# Running the package

## Creating launch file for Broadcaster

Create a launch file inside the package if one does not exist already.

```sh
cd robotics/src/lab_1_tf
```

```sh
mkdir launch
```

create a launch file inside it called 'broadcaster_demo.launch'

```sh
code broadcaster_demo.launch
```

copy the following lines into it

```sh
<launch>
    <!-- Turtlesim Node-->
    <node pkg="turtlesim" type="turtlesim_node" name="sim"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="teleop" output="screen"/>
    
    <node name="turtle1_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle1" />
    </node>
    
    <node name="turtle2_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle2" /> 
    </node>
</launch>
```

<br>

## Building the broadcaster

Modify CMakeLists.txt

```sh
catkin_install_python(PROGRAMS scripts/broadcaster.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Build the code

Go to root of the workspace

```
cd robotics/
```

and run either of
```sh
catkin build
```

or

```sh
catkin_make
```
<br>

## Running the broadcasters
Move to the root of the ROS workspace and launch the program


```sh
source devel/setup.bash
```

```sh
roslaunch lab_1_tf broadcaster_demo.launch
```

On a seperate terminal, run 

```sh
rosrun tf tf_echo /world /turtle1
```

to check the tf broadcast.

<br>
<br>

## Creating launch file for Listener

Create a launch file inside the package if one does not exist already.

```sh
cd robotics/src/lab_1_tf
```

```sh
mkdir launch
```

create a launch file inside it called 'broadcaster_listener_demo.launch'

```sh
code broadcaster_listener_demo.launch
```

copy the following lines into it

```sh
<launch>
    <!-- Turtlesim Node-->
    <node pkg="turtlesim" type="turtlesim_node" name="sim"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="teleop" output="screen"/>
    
    <node name="turtle1_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle1" />
    </node>
    
    <node name="turtle2_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle2" /> 
    </node>

    <node pkg="lab_1_tf" type="listener.py" name="listener" />
</launch>
```

<br>

## Building the listener

Modify CMakeLists.txt

```sh
catkin_install_python(PROGRAMS scripts/broadcaster.py scripts/listener.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Build the code

Go to root of the workspace

```
cd robotics/
```

and run either of
```sh
catkin build
```

or

```sh
catkin_make
```
<br>

## Running the listener

```sh
source devel/setup.bash
```

Move to the root of the ROS workspace and launch the program

```sh
roslaunch lab_1_tf broadcaster_listener_demo.launch
```



<br>
<br>

## Creating launch file for Static Frame

Create a launch file inside the package if one does not exist already.

```sh
cd robotics/src/lab_1_tf
```

```sh
mkdir launch
```

create a launch file inside it called 'broadcaster_listener_static_demo.launch'

```sh
code broadcaster_listener_static_demo.launch
```

copy the following lines into it

```sh
<launch>
    <!-- Turtlesim Node-->
    <node pkg="turtlesim" type="turtlesim_node" name="sim"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="teleop" output="screen"/>
    
    <node name="turtle1_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle1" />
    </node>
    
    <node name="turtle2_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle2" /> 
    </node>

    <node pkg="lab_1_tf" type="listener.py" name="listener" />

    <node pkg="lab_1_tf" type="static_frame.py"
          name="broadcaster_fixed" />
</launch>
```

<br>

## Building the static frame

Modify CMakeLists.txt

```sh
catkin_install_python(PROGRAMS scripts/broadcaster.py scripts/listener.py scripts/static_frame.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Build the code

Go to root of the workspace

```
cd robotics/
```

and run either of
```sh
catkin build
```

or

```sh
catkin_make
```
<br>

## Running the static frame
Move to the root of the ROS workspace and launch the program

```sh
source devel/setup.bash
```

```sh
roslaunch lab_1_tf broadcaster_listener_static_demo.launch
```



<br>
<br>

## Creating launch file for dynamic frame

Create a launch file inside the package if one does not exist already.

```sh
cd robotics/src/lab_1_tf
```

```sh
mkdir launch
```

create a launch file inside it called 'broadcaster_listener_dynamic_demo.launch'

```sh
code broadcaster_listener_dynamic_demo.launch
```

copy the following lines into it

```sh
<launch>
    <!-- Turtlesim Node-->
    <node pkg="turtlesim" type="turtlesim_node" name="sim"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="teleop" output="screen"/>
    
    <node name="turtle1_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle1" />
    </node>
    
    <node name="turtle2_tf_broadcaster" pkg="lab_1_tf" type="broadcaster.py" respawn="false" output="screen" >
        <param name="turtle" type="string" value="turtle2" /> 
    </node>

    <node pkg="lab_1_tf" type="listener.py" name="listener" />

    <node pkg="lab_1_tf" type="dynamic_frame.py" name="broadcaster_dynamic" />
</launch>
```

<br>

## Building the dynamic frame

Modify CMakeLists.txt

```sh
catkin_install_python(PROGRAMS scripts/broadcaster.py scripts/listener.py scripts/dynamic_frame.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Build the code

Go to root of the workspace

```
cd robotics/
```

and run either of
```sh
catkin build
```

or

```sh
catkin_make
```
<br>

## Running the dynamic frame

Move to the root of the ROS workspace and launch the program

```sh
source devel/setup.bash
```

```sh
roslaunch lab_1_tf broadcaster_listener_dynamic_demo.launch
```

