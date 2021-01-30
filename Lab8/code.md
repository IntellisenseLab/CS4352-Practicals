# Simulation

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the simulation

```sh
source devel/setup.bash
```
```sh
roslaunch rosbot_description rosbot_rviz.launch
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
