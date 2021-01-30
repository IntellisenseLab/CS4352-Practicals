# Simulation

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo simulation

```sh
source devel/setup.bash
```
```sh
roslaunch rosbot_gazebo rosbot_world.launch
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the rosbot model
```sh
source devel/setup.bash
```

```sh
roslaunch rosbot_description rosbot_gazebo.launch
```

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the movebase (Navigation stack)

```sh
source devel/setup.bash
```

```sh
roslaunch rosbot_navigation navigation_demo.launch
```


Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the explore-lite system

```sh
source devel/setup.bash
```
```sh
roslaunch explore explore.launch
```

[<< Back to Main menu](../README.md)