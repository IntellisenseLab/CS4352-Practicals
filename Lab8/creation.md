# Package Creation

Move to src folder and clone the repository

```sh
cd robotics/src
```
and run,

```sh
git clone https://github.com/hrnr/m-explore.git
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