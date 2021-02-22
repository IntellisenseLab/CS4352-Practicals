# Package Configuration

This practical depends on the resources that were downloaded in previous practicals. Modify amcl_demo.launch as follows
 
```sh
cd robotics/src/rosbot_description/src/rosbot_navigation/launch

code amcl_demo.launch
```

replace the section under <!---Movebase---> with the following section

```sh
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
```

[<< Back to Main menu](../README.md)
