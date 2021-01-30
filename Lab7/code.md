# Client Planner Python Implementation

<br>

## Setting up configuration

Move to rosbot_navigation inside rosbot_decription/src and create folder name config

```sh
cd src/rosbot_description/src/rosbot_navigation

mkdir config

cd config
```

<br>

## Robot Dimensions

![](ROSbot-dim-bold.jpg)

## costmap_common_params

Create a new file inside config folder called costmap_common_params.yaml

```sh
code costmap_common_params.yaml
```

copy following content to it

```sh
obstacle_range: 6.0
raytrace_range: 8.5
footprint: [[0.12, 0.14], [0.12, -0.14], [-0.12, -0.14], [-0.12, 0.14]]
map_topic: /map
subscribe_to_updates: true
observation_sources: laser_scan_sensor
laser_scan_sensor: {sensor_frame: laser, data_type: LaserScan, topic: scan, marking: true, clearing: true}
global_frame: map
robot_base_frame: base_link
always_send_full_costmap: true
```

<br>

## global_costmap_params

Create a new file inside config folder called global_costmap_params.yaml

```sh
code global_costmap_params.yaml
```

copy following content to it

```sh
global_costmap:
  update_frequency: 0.5
  publish_frequency: 1.5
  transform_tolerance: 0.5
  width: 15
  height: 15
  origin_x: -7.5
  origin_y: -7.5
  static_map: false
  rolling_window: true
  inflation_radius: 2.5
  resolution: 0.01
```

<br>

## local_costmap_params

Create a new file inside config folder called local_costmap_params.yaml

```sh
code local_costmap_params.yaml
```

copy following content to it

```sh
local_costmap:
  update_frequency: 2.5
  publish_frequency: 2.5
  transform_tolerance: 0.25
  static_map: false
  rolling_window: true
  width: 3
  height: 3
  origin_x: -1.5
  origin_y: -1.5
  resolution: 0.01
  inflation_radius: 1.0
```

<br>

## trajectory_planner

Create a new file inside config folder called trajectory_planner.yaml

```sh
code trajectory_planner.yaml
```

copy following content to it

```sh
TrajectoryPlannerROS:
 max_vel_x: 0.1
 min_vel_x: 0.05
 max_vel_theta: 2.5
 min_vel_theta: -2.5
 min_in_place_vel_theta: 0.5
 acc_lim_theta: 1.0
 acc_lim_x: 1.5
 acc_lim_Y: 1.5
 holonomic_robot: false
 meter_scoring: true 
 xy_goal_tolerance: 0.1
 yaw_goal_tolerance: 0.1
 meter_scoring: true
 occdist_scale:  0.01
 pdist_scale: 0.4
 gdist_scale: 0.2
```

## single_rosbot

Create a new file inside config folder called single_rosbot.rviz

```sh
code single_rosbot.rviz
```

copy following content to it

```sh
Panels:
  - Class: rviz/Displays
    Help Height: 78
    Name: Displays
    Property Tree Widget:
      Expanded:
        - /Global Options1
        - /Status1
      Splitter Ratio: 0.5
    Tree Height: 747
  - Class: rviz/Selection
    Name: Selection
  - Class: rviz/Tool Properties
    Expanded:
      - /2D Pose Estimate1
      - /2D Nav Goal1
      - /Publish Point1
    Name: Tool Properties
    Splitter Ratio: 0.588679016
  - Class: rviz/Views
    Expanded:
      - /Current View1
    Name: Views
    Splitter Ratio: 0.5
  - Class: rviz/Time
    Experimental: false
    Name: Time
    SyncMode: 0
    SyncSource: ""
Visualization Manager:
  Class: ""
  Displays:
    - Alpha: 0.5
      Cell Size: 1
      Class: rviz/Grid
      Color: 160; 160; 164
      Enabled: true
      Line Style:
        Line Width: 0.0299999993
        Value: Lines
      Name: Grid
      Normal Cell Count: 0
      Offset:
        X: 0
        Y: 0
        Z: 0
      Plane: XY
      Plane Cell Count: 10
      Reference Frame: <Fixed Frame>
      Value: true
  Enabled: true
  Global Options:
    Background Color: 48; 48; 48
    Default Light: true
    Fixed Frame: map
    Frame Rate: 30
  Name: root
  Tools:
    - Class: rviz/Interact
      Hide Inactive Objects: true
    - Class: rviz/MoveCamera
    - Class: rviz/Select
    - Class: rviz/FocusCamera
    - Class: rviz/Measure
    - Class: rviz/SetInitialPose
      Topic: /initialpose
    - Class: rviz/SetGoal
      Topic: /move_base_simple/goal
    - Class: rviz/PublishPoint
      Single click: true
      Topic: /clicked_point
  Value: true
  Views:
    Current:
      Class: rviz/Orbit
      Distance: 10
      Enable Stereo Rendering:
        Stereo Eye Separation: 0.0599999987
        Stereo Focal Distance: 1
        Swap Stereo Eyes: false
        Value: false
      Focal Point:
        X: 0
        Y: 0
        Z: 0
      Focal Shape Fixed Size: true
      Focal Shape Size: 0.0500000007
      Invert Z Axis: false
      Name: Current View
      Near Clip Distance: 0.00999999978
      Pitch: 0.785398006
      Target Frame: <Fixed Frame>
      Value: Orbit (rviz)
      Yaw: 0.785398006
    Saved: ~
Window Geometry:
  Displays:
    collapsed: false
  Height: 1028
  Hide Left Dock: false
  Hide Right Dock: true
  QMainWindow State: 000000ff00000000fd00000004000000000000016a0000037afc0200000008fb0000001200530065006c0065006300740069006f006e00000001e10000009b0000006100fffffffb0000001e0054006f006f006c002000500072006f007000650072007400690065007302000001ed000001df00000185000000a3fb000000120056006900650077007300200054006f006f02000001df000002110000018500000122fb000000200054006f006f006c002000500072006f0070006500720074006900650073003203000002880000011d000002210000017afb000000100044006900730070006c00610079007301000000280000037a000000d700fffffffb0000002000730065006c0065006300740069006f006e00200062007500660066006500720200000138000000aa0000023a00000294fb00000014005700690064006500530074006500720065006f02000000e6000000d2000003ee0000030bfb0000000c004b0069006e0065006300740200000186000001060000030c00000261000000010000010f0000037afc0200000003fb0000001e0054006f006f006c002000500072006f00700065007200740069006500730100000041000000780000000000000000fb0000000a0056006900650077007300000000280000037a000000ad00fffffffb0000001200530065006c0065006300740069006f006e010000025a000000b200000000000000000000000200000490000000a9fc0100000001fb0000000a00560069006500770073030000004e00000080000002e10000019700000003000003a00000003efc0100000002fb0000000800540069006d00650100000000000003a00000030000fffffffb0000000800540069006d00650100000000000004500000000000000000000002300000037a00000004000000040000000800000008fc0000000100000002000000010000000a0054006f006f006c00730100000000ffffffff0000000000000000
  Selection:
    collapsed: false
  Time:
    collapsed: false
  Tool Properties:
    collapsed: false
  Views:
    collapsed: true
  Width: 928
  X: 65
  Y: 1224
```

## launch file

Create a new file inside launch folder called navigation_demo.launch

```sh
cd ..
cd launch
```

```sh
code navigation_demo.launch
```

copy following content to it

```sh
<?xml version="1.0"?>
<launch>
  <master auto="start"/>

  <!-- Map server -->
  <arg name="map_file" default="$(find rosbot_navigation)/maps/test_map.yaml"/>
  <node name="map_server" pkg="map_server" type="map_server" args="$(arg map_file)" />

  <!-- Move base -->
  <node pkg="move_base" type="move_base" respawn="false" name="move_base" output="screen">
    <rosparam file="$(find rosbot_navigation)/config/costmap_common_params.yaml" command="load" ns="global_costmap" />
    <rosparam file="$(find rosbot_navigation)/config/costmap_common_params.yaml" command="load" ns="local_costmap" />
    <rosparam file="$(find rosbot_navigation)/config/local_costmap_params.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/global_costmap_params.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/trajectory_planner.yaml" command="load" />

    <remap from="cmd_vel" to="cmd_vel"/>
    <remap from="odom" to="odom"/>
    <remap from="scan" to="/scan"/>
    <param name="move_base/DWAPlannerROS/yaw_goal_tolerance" value="1.0"/>
    <param name="move_base/DWAPlannerROS/xy_goal_tolerance" value="1.0"/>

  </node>
</launch>
```
[<< Back to Main menu](../README.md)
