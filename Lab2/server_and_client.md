# Client Server Python Implementation

```sh
mkdir scripts
```

## Server creation

Open a terminal inside scripts folder and create a file name server.py.
Copy the content from server.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x server.py
```

to enable execute permission.

<br>

## Client creation

Open a terminal inside scripts folder and create a file name client.py.
Copy the content from client.txt and paste. Open a terminal in the same location and Run

```sh
chmod +x client.py
```

to enable execute permission.

<br>

## CMakeLists.txt file modifications

Open lab_2_3dPose/CMakeLists.txt and add following lines to the bottom of the file.

```sh
catkin_install_python(PROGRAMS scripts/client.py scripts/server.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

```

## Build the code 

Go to root of the workspace

```sh
cd ~/robotics/
```
```sh
catkin build
```
or
```sh
catkin_make
```