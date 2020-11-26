# Creating a Dynamic Frame BroadCaster

Create a python script inside scripts folder and name it dynamic_frame.py

```sh
cd robotics/src/lab_1_tf/scripts
```

```sh
code dynamic_frame.py
```

Copy the content from the Lab1/dynamic_frame.txt into the dynamic_frame.py

Enable permission to run the script as an executable.

```sh
chmod +x dynamic_frame.py
```

Open the listener.py and modify following line

```sh
(trans,rot) = listener.lookupTransform('/turtle2', '/turtle1', rospy.Time(0))
```
as

```sh
(trans,rot) = listener.lookupTransform("/turtle2", "/carrot1", rospy.Time(0))
```
