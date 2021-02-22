# Explore-Lite Configuration

Move to m-explore/explore/launch folder and create a new launch file named activity.launch

```sh
code activity.launch
```

copy the following snippet into the launch file

```sh
<launch>
  <node pkg="explore_lite" type="explore" respawn="false" name="explore" output="screen">
    <param name="robot_base_frame" value="base_link"/>
    <param name="costmap_topic" value="move_base/global_costmap/costmap"/>
    <param name="visualize" value="true"/>
    <param name="planner_frequency" value="0.5"/>
    <param name="progress_timeout" value="30.0"/>
    <param name="potential_scale" value="0.001"/>
    <param name="orientation_scale" value="0.0"/>
    <param name="gain_scale" value="2.0"/>
    <param name="transform_tolerance" value="0.5"/>
    <param name="min_frontier_size" value="0.5"/>
  </node>
</launch>
```

# Simulation

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo world

```sh
source devel/setup.bash

roslaunch rosbot_gazebo rosbot_world.launch
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the rosbot model
```sh
source devel/setup.bash

roslaunch rosbot_description rosbot_gazebo.launch
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the movebase (Navigation stack) and octomap_server

```sh
source devel/setup.bash

roslaunch rosbot_navigation navigation_demo.launch
```


Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the explore-lite system

```sh
source devel/setup.bash
```
```sh
roslaunch explore_lite activity.launch
```

[<< Back to Main menu](../README.md)
