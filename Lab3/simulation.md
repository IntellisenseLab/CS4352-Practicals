# Simulation

First open a terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo simulation

```sh
cd robotics
```

```sh
source devel/setup.bash
```

```sh
roslaunch open_manipulator_gazebo open_manipulator_gazebo.launch
```

Start the simulation by pressing the "play" button in the lower part of the screen.

Then open another terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo controller

```sh
cd robotics
```

```sh
source devel/setup.bash
```

```sh
roslaunch open_manipulator_controller open_manipulator_controller.launch use_platform:=false
```

Then open a third terminal window, move to robotics folder, source the devel/setup.bash and start the gazebo controller

```sh
cd robotics
```

```sh
source devel/setup.bash
```

```sh
roslaunch open_manipulator_control_gui open_manipulator_control_gui.launch
```

### Press "Timer Start"

### Press "Actuator Enable"

### Press "Home Position"