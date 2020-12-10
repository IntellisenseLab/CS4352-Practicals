# Custom Message Creation and Publisher and Subsciber

## Messages

Create a srv folder inside robotics/src/lab_2_3dPose folder

```sh
mkdir -p robotics/src/lab_2_3dPose/srv
```

Open the folder 
```sh
cd robotics/src/lab_2_3dPose/srv
```

Create a .srv file with desired name. (we will select angles.srv as an example)

```sh
code angles.srv
```
Inside the file add following lines, then save and close.
```sh
float64 a
float64 b
float64 c
string format
---
float64 qx
float64 qy
float64 qz
float64 qw
```

Open package.xml and add the following lines in the respective sections

```sh
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```

Open the CMakeLists.txt and add following lines to respective section,

message_generation to find_package()

```sh
find_package(catkin REQUIRED COMPONENTS
   roscpp
   rospy
   std_msgs
   message_generation
)
```

message_runtime to catkin_package

```sh
catkin_package(
  ...
  CATKIN_DEPENDS message_runtime ...
  ...)
```

uncomment add_service_files section and add angles.srv file

```sh
add_service_files(DIRECTORY 
  srv
  FILES
  angles.srv
)
```

uncomment generate_messgae() section. It shoul look like this,

```sh
generate_messages(
  DEPENDENCIES
  std_msgs
)
```

Move to the workspace root and rebuild

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