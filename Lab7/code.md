# Client Planner Python Implementation

<br>

## Setting up configuration

Move to rosbot_navigation inside rosbot_decription/src and create folder name config

```sh
cd src/rosbot_description/src/rosbot_navigation

mkdir config

cd config
```

## Robot Dimensions

![](ROSbot-dim-bold.jpg)

## costmap_common_params

Create a new file inside config folder called costmap_common_params.yaml

```sh
code costmap_common_params.yaml
```

copy following content to it

```sh

footprint: [[0.12, 0.14], [0.12, -0.14], [-0.12, -0.14], [-0.12, 0.14]]

map_type: voxel

obstacle_layer:
  enabled:              true
  obstacle_range:       2.0
  raytrace_range:       2.0
  min_obstacle_height:  0.0
  max_obstacle_height:  0.5
  inflation_radius:     0.2
  origin_z:             0.0
  z_resolution:         0.05
  z_voxels:             20
  unknown_threshold:    5
  mark_threshold:       5
  combination_method:   1
  map_topic:            map
  subscribe_to_updates: false
  track_unknown_space:  true    #true needed for disabling global path planning through unknown space
  publish_voxel_map:    true
  observation_sources:  pointCloud
  
  pointCloud:
    sensor_frame:       camera_rgb_frame
    data_type:          PointCloud2
    topic:              camera/depth/points
    marking:            true
    clearing:           true
    max_obstacle_height: 0.5
    min_obstacle_height: 0.0

inflation_layer:
  enabled:              true
  cost_scaling_factor:  3.0  # exponential rate at which the obstacle cost drops off (default: 10)
  inflation_radius:     0.25  # max. distance from an obstacle at which costs are incurred for planning paths.

static_layer:
  enabled:              true
  track_unknown_space:  true
```

## global_costmap_params

Create a new file inside config folder called global_costmap_params.yaml

```sh
code global_costmap_params.yaml
```

copy following content to it

```sh
global_costmap:
   global_frame:            map
   robot_base_frame:        base_link
   update_frequency:        0.5
   publish_frequency:       2.0
   static_map:              true
   plugins:
     - {name: static_layer,            type: "costmap_2d::StaticLayer"}
```

## local_costmap_params

Create a new file inside config folder called local_costmap_params.yaml

```sh
code local_costmap_params.yaml
```

copy following content to it

```sh
local_costmap:
   global_frame:              map
   robot_base_frame:          base_link
   update_frequency:          2.5
   publish_frequency:         2.5
   rolling_window:            true
   width:                     3.0
   height:                    3.0
   resolution:                0.05
   transform_tolerance:       1.0
   always_send_full_costmap:  true

   plugins:
     - {name: obstacle_layer,  type: "costmap_2d::VoxelLayer"}
     - {name: inflation_layer, type: "costmap_2d::InflationLayer"}
```

## global_planner

Create a new file inside config folder called global_planner_params.yaml

```sh
code global_planner_params.yaml
```

copy following content to it

```sh
GlobalPlanner:                                  # Also see: http://wiki.ros.org/global_planner
  old_navfn_behavior: false                     # Exactly mirror behavior of navfn, use defaults for other boolean parameters, default false
  use_quadratic: true                           # Use the quadratic approximation of the potential. Otherwise, use a simpler calculation, default true
  use_dijkstra: false                           # Use dijkstra's algorithm. Otherwise, A*, default true
  use_grid_path: true                           # Create a path that follows the grid boundaries. Otherwise, use a gradient descent method, default false
  
  allow_unknown: true                           # Allow planner to plan through unknown space, default true
                                                #Needs to have track_unknown_space: true in the obstacle / voxel layer (in costmap_commons_param) to work
  planner_window_x: 0.0                         # default 0.0
  planner_window_y: 0.0                         # default 0.0
  default_tolerance: 0.1                        # If goal in obstacle, plan to the closest point in radius default_tolerance, default 0.0
  
  publish_scale: 100                            # Scale by which the published potential gets multiplied, default 100
  planner_costmap_publish_frequency: 0.0        # default 0.0
  
  lethal_cost: 253                              # default 253
  neutral_cost: 66                              # default 50
  cost_factor: 0.56                             # Factor to multiply each cost from costmap by, default 3.0
  publish_potential: true                       # Publish Potential Costmap (this is not like the navfn pointcloud2 potential), default true
```

## teb_local_planner

Create a new file inside config folder called teb_local_planner.yaml

```sh
code teb_local_planner.yaml
```

copy following content to it

```sh
TebLocalPlannerROS:

  odom_topic:                         odom
  map_frame:                          map
      
  # Trajectory
    
  teb_autosize:                       true
  dt_ref:                             0.3
  dt_hysteresis:                      0.05
  global_plan_overwrite_orientation:  true
  max_global_plan_lookahead_dist:     3.0
  feasibility_check_no_poses:         3
      
  # Robot
          
  max_vel_x:                          0.1
  min_vel_x:                          0.05
  max_vel_x_backwards:                0.1
  max_vel_theta:                      2.5
  min_vel_theta:                      -2.5
  acc_lim_x:                          1.5
  acc_lim_theta:                      1.0
  min_turning_radius:                 0.0
  footprint_model:                                # types: "point", "circular", "two_circles", "line", "polygon"
    type:                             "polygon"
    #radius:                           0.2         # for type "circular"
    #line_start: [-0.3, 0.0]                      # for type "line"
    #line_end: [0.3, 0.0]                         # for type "line"
    #front_offset: 0.2                            # for type "two_circles"
    #front_radius: 0.2                            # for type "two_circles"
    #rear_offset: 0.2                             # for type "two_circles"
    #rear_radius: 0.2                             # for type "two_circles"
    vertices: [[0.12, 0.14], [0.12, -0.14], [-0.12, -0.14], [-0.12, 0.14]] # for type "polygon"

  # GoalTolerance
      
  xy_goal_tolerance:                  0.1
  yaw_goal_tolerance:                 0.1
  free_goal_vel:                      false
      
  # Obstacles
      
  min_obstacle_dist:                  0.25
  include_costmap_obstacles:          true
  costmap_obstacles_behind_robot_dist: 1.0
  obstacle_poses_affected:            30
  costmap_converter_plugin:           ""
  costmap_converter_spin_thread:      true
  costmap_converter_rate:             5

  # Optimization
      
  no_inner_iterations:                5
  no_outer_iterations:                4
  optimization_activate:              true
  optimization_verbose:               false
  penalty_epsilon:                    0.09
  weight_max_vel_x:                   2
  weight_max_vel_theta:               1
  weight_acc_lim_x:                   1
  weight_acc_lim_theta:               1
  weight_kinematics_nh:               1000
  weight_kinematics_forward_drive:    1
  weight_kinematics_turning_radius:   1
  weight_optimaltime:                 1
  weight_obstacle:                    10
  weight_dynamic_obstacle:            10          # not in use yet
  selection_alternative_time_cost:    false       # not in use yet

  # Homotopy Class Planner

  enable_homotopy_class_planning:     false #True
  enable_multithreading:              true
  simple_exploration:                 false
  max_number_classes:                 4
  roadmap_graph_no_samples:           15
  roadmap_graph_area_width:           5
  h_signature_prescaler:              0.5
  h_signature_threshold:              0.1
  obstacle_keypoint_offset:           0.1
  obstacle_heading_threshold:         0.45
  visualize_hc_graph:                 false
```

## move_base_params

Create a new file inside config folder called move_base_params.yaml

```sh
code move_base_params.yaml
```

copy following content to it

```sh
shutdown_costmaps:          false

controller_frequency:       0.5
controller_patience:        15.0

planner_frequency:          0.0
planner_patience:           5.0

oscillation_timeout:        5.0
oscillation_distance:       0.2

base_local_planner:         "teb_local_planner/TebLocalPlannerROS"

base_global_planner:        "global_planner/GlobalPlanner"

clearing_rotation_allowed:  true
max_planning_retries:       5
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

  <arg name="odom_frame_id"   default="odom"/>
  <arg name="base_frame_id"   default="base_link"/>
  <arg name="global_frame_id" default="map"/>
  <arg name="odom_topic" default="odom" />
  <arg name="laser_topic" default="scan" />

  <node pkg="tf" type="static_transform_publisher" name="odom_to_map" args="0 0 0 0 0 0 /map /odom 100"/>

  <!-- Map server -->
    <node pkg="octomap_server" type="octomap_server_node" name="octomap_server" output="screen">
        <param name="resolution" value="0.01" />
        <param name="frame_id" type="string" value="/odom" />
        <param name="sensor_model/max_range" value="2.0" />
        <param name="latch" value="true" />

        <remap from="cloud_in" to="/camera/depth/points" />
        <remap from="projected_map" to="map" />
    </node>

  <!-- Move base -->
  <node pkg="move_base" type="move_base" respawn="false" name="move_base" output="screen">
    <rosparam file="$(find rosbot_navigation)/config/costmap_common_params.yaml" command="load" ns="global_costmap" />
    <rosparam file="$(find rosbot_navigation)/config/costmap_common_params.yaml" command="load" ns="local_costmap" />
    <rosparam file="$(find rosbot_navigation)/config/local_costmap_params.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/global_costmap_params.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/teb_local_planner.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/global_planner_params.yaml" command="load" />
    <rosparam file="$(find rosbot_navigation)/config/move_base_params.yaml" command="load" />

    <remap from="cmd_vel" to="cmd_vel"/>
    <remap from="odom" to="odom"/>
    <remap from="scan" to="/scan"/>
    <param name="move_base/DWAPlannerROS/yaw_goal_tolerance" value="1.0"/>
    <param name="move_base/DWAPlannerROS/xy_goal_tolerance" value="1.0"/>

  </node>
</launch>
```
[<< Back to Main menu](../README.md)
