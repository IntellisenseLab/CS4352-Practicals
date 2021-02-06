# Mapping

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo world

```sh
source devel/setup.bash

roslaunch rosbot_description rosbot_rviz_gmapping.launch
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the teleop node for robot movement

```sh
source devel/setup.bash

roslaunch rosbot_navigation rosbot_teleop.launch
```

After completing the mapping, open another terminal window, move to robotics folder, source the devel/setup.bash and save the map. (modify the path to the maps folder according to your folder structure)

```sh
source devel/setup.bash

rosrun map_server map_saver -f ~/robotics/src/rosbot_description/src/rosbot_navigation/maps/test_map
```

Close all three terminals.

# Navigation

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo world

```sh
source devel/setup.bash

roslaunch rosbot_description rosbot_rviz_amcl.launch
```

Then use rviz to set 2D Nav Goal and the robot will autonomously reach the indicated position. Reconfigure the Path representations in the RVIZ plugins to accomodate Global Planner and Teb Local Planner.

[<< Back to Main menu](../README.md)
