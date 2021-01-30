# Package Creation

First setup the robot model in the workspace. Move to src folder

```sh
cd robotics/src
```
and run,

```sh
git clone https://github.com/IntellisenseLab/CS4352-Practicals-Rosbot.git rosbot_description
```

to install dependencies, move to root of the workspace and run,

```sh
cd ..

rosdep install --from-paths src --ignore-src -r -y
```
then run 

```sh
catkin build
```
or
```sh
catkin_make
```

[<< Back to Main menu](../README.md)