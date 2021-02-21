# OFFBoard Control

## Package Creation

Create a package with depenedencies on mavros, mavros_msgs, geometry_msgs and roscpp

```sh
catkin_create_pkg lab10_offboardcontrol roscpp mavros mavros_msgs geometry_msgs
```
## Controller Creation

Move inside to the src folder and create a c++ file named offboardnode

```sh
cd lab10_offboardcontrol/src

code offboardnode.cpp
```

Copy and paste the following code inside it

```sh

#include <ros/ros.h>
#include <geometry_msgs/PoseStamped.h>
#include <mavros_msgs/CommandBool.h>
#include <mavros_msgs/SetMode.h>
#include <mavros_msgs/State.h>

mavros_msgs::State current_state;
void state_cb(const mavros_msgs::State::ConstPtr& msg){
    current_state = *msg;
}

int main(int argc, char **argv)
{
    ros::init(argc, argv, "offb_node");
    ros::NodeHandle nh;

    ros::Subscriber state_sub = nh.subscribe<mavros_msgs::State>
            ("mavros/state", 10, state_cb);
    ros::Publisher local_pos_pub = nh.advertise<geometry_msgs::PoseStamped>
            ("mavros/setpoint_position/local", 10);
    ros::ServiceClient arming_client = nh.serviceClient<mavros_msgs::CommandBool>
            ("mavros/cmd/arming");
    ros::ServiceClient set_mode_client = nh.serviceClient<mavros_msgs::SetMode>
            ("mavros/set_mode");

    //the setpoint publishing rate MUST be faster than 2Hz
    ros::Rate rate(20.0);

    // wait for FCU connection
    while(ros::ok() && !current_state.connected){
        ros::spinOnce();
        rate.sleep();
    }

    geometry_msgs::PoseStamped pose;
    pose.pose.position.x = 0;
    pose.pose.position.y = 0;
    pose.pose.position.z = 2;

    //send a few setpoints before starting
    for(int i = 100; ros::ok() && i > 0; --i){
        local_pos_pub.publish(pose);
        ros::spinOnce();
        rate.sleep();
    }

    mavros_msgs::SetMode offb_set_mode;
    offb_set_mode.request.custom_mode = "OFFBOARD";

    mavros_msgs::CommandBool arm_cmd;
    arm_cmd.request.value = true;

    ros::Time last_request = ros::Time::now();

    while(ros::ok()){
        if( current_state.mode != "OFFBOARD" &&
            (ros::Time::now() - last_request > ros::Duration(5.0))){
            if( set_mode_client.call(offb_set_mode) &&
                offb_set_mode.response.mode_sent){
                ROS_INFO("Offboard enabled");
            }
            last_request = ros::Time::now();
        } else {
            if( !current_state.armed &&
                (ros::Time::now() - last_request > ros::Duration(5.0))){
                if( arming_client.call(arm_cmd) &&
                    arm_cmd.response.success){
                    ROS_INFO("Vehicle armed");
                }
                last_request = ros::Time::now();
            }
        }

        local_pos_pub.publish(pose);

        ros::spinOnce();
        rate.sleep();
    }

    return 0;
}

```

Then open the CMakeLists.txt file and add the following line to the end of it to add the newly created c++ file.

```sh
add_executable(offboardnode src/offboardnode.cpp)
target_link_libraries(offboardnode ${catkin_LIBRARIES})
add_dependencies(offboardnode ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
```

Then move to workspace root and build it.

```sh
catkin build
```

## Starting the Simulation

To start MAVROS on a new terminal run,

```sh
source devel/setup.bash

roslaunch mavros px4.launch fcu_url:="udp://:14540@127.0.0.1:14557"
```

To Start gazebo on a new terminal move to PX4-Autopilot folder and run,

```sh
DONT_RUN=1 make px4_sitl_default gazebo
source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo
roslaunch px4 posix_sitl.launch
```

To run offboard controller created above, open a new terminal in the ros workspace and run,

```sh
source devel/setup.bash

rosrun lab10_offboardcontrol offboardnode
```

Based on [MAVROS offboard example](https://docs.px4.io/master/en/ros/mavros_offboard.html) and [ROS Gazebo Simulation](https://docs.px4.io/master/en/simulation/ros_interface.html)

[<< Back to Main menu](../README.md)
