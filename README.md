# CS4352-Practicals

## Introduction

This repository contains practicals designed for the CS4352 - Robotics and Automation module offered by Department of Computer Science and Engineering of University of Moratuwa. This branch contains lab activities related to Batch 2016. This series of practicals are designed to support the theroy components taught in the CS4352 lectures and will have complementing activities each week. This work assumes that the students have a basic understanding of Robot Operating System (ROS) including its internal structure, Publisher-Subscriber architecture and Client-Server architecture which can be covered by following the [ROS Introduction](https://github.com/IntellisenseLab/ROS-Introduction) webinar series.

## Lab 1

This lab focuses on learning about TF broadcasters & TF listeners. The practical focuses on creating a TF broadcaster that recives input from keybaord and bradocasting them as a tf transform and a listener that listens to the broadcasted transform and controls the velocity of the turrtlesim accodingly. The static frame transform braodcasts a fixed transformatin which a second tutrle follows. The dynamic frame transformation broadcasts a dnamic frame that a second turtle follow.

This practical is based ion [ROS TF tutorial](http://wiki.ros.org/tf/Tutorials) available in ros.wiki.org.

Package Creation - [here](/Lab01/creation.md) \
TF broadcaster creation - [here](/Lab01/broadcaster.md) \
TF listener creation - [here](Lab01/listener.md) \
Additional static frame - [here](Lab01/static_frame.md) \
Additional dynamic frame - [here](Lab01/dynamic_frame.md) \
Compiling and Running - [here](/Lab01/running.md)

## Lab 2

This lab focuses on learning about the relationship between 3 Angle representation, Quaternions and ROS. The server implements a converter that converts the 3 angle representation to quarternions. The client can send the 3 angle representation and receive the converted quaternion value back. This lab exercise will also give an understating of ROS Server client. architecture.

Package Creation - [here](/Lab02/creation.md) \
Srv creation - [here](Lab02/srv.md) \
Server and Client creation - [here](/Lab02/server_and_client.md) \
Exercise - [here](/Lab02/activity.md)

## Lab 3

This lab focuses on setting up and getting an basic understanding of openmanipulator including its Joint space control and Task space control. 

Package Creation - [here](/Lab03/creation.md) \
Modification - [here](/Lab03/modification.md) \
Simulation - [here](Lab03/simulation.md) \
Exercise - [here](/Lab03/activity.md)

## Lab 4

This lab focuses on creating a service client for Joint space control. The server used is the open_manipulator_controller.

Package Creation - [here](/Lab04/creation.md) \
Client Creation - [here](Lab04/jont_client.md) \
Exercise - [here](/Lab04/activity.md)

## Lab 5

This lab focuses on creating a service client for Task space control. The server used is the open_manipulator_controller.

Package Creation - [here](/Lab05/creation.md) \
Client Creation - [here](Lab05/task_client.md) \
Exercise - [here](/Lab05/activity.md)

## Lab 6

This lab focuses on creating a server that implements a Joint space control which can be used to replace the open_manipulator_controller.

Package Creation - [here](/Lab06/creation.md) \
Impelmentation - [here](Lab06/code.md) \
Exercise - [here](/Lab06/activity.md)

## Lab 7

This lab focuses on Setting up navigation stack of ROS.

Package Creation - [here](/Lab07/creation.md) \
Navigation Stack Configuration - [here](Lab07/code.md) \
Exercise - [here](/Lab07/activity.md)

## Lab 8

This lab focuses on setting up and using Explore-Lite along with navigation stack.

Package Creation - [here](/Lab08/creation.md) \
Explore-Lite Configuration - [here](Lab08/code.md) \
Exercise - [here](Lab08/activity.md)

## Lab 9

This lab focuses on localization and combines Gmapping with navigation stack.

Gmapping Configuration - [here](Lab09/configuration.md) \
Mapping and Navigation - [here](Lab09/code.md) \
Exercise - [here](Lab09/activity.md)

## Lab 10

This lab focuses on creating a ROS based Offboard Control system for a Drone.

Package Configuration - [here](Lab10/configuration.md) \
Controller creation - [here](Lab10/code.md) \
Exercise - [here](Lab10/activity.md)
