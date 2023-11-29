+++
title="Walli"
description="Walli is a Mars-Rover style robot I participated in building and programming as a software team member. Walli is designed to finish versatile tasks with its differential drive base and the Robotics arm equipped on it."
date="2023-09-15"

[taxonomies]
categories=["Project", "Robot"]
skills=["C++", "Python", "ROS"]

[extra]
byline = "Versatile Mars Rover for University Rover Challenge."
timeframe = "August 2023 - Now"
organization = "RoboNav - RoboJackets"
role = "Software Team Member"
code_link="https://github.com/RoboJackets/urc-software"
title_image = "images/walli-square.png"
+++

## Innovations

### ROS2 Control Stack

The base drive of the whole robot is based on [ROS2 Control](https://github.com/ros-controls/ros2_control) - a generic, simple, and universal driver system for ROS. This system divides up hardware and software via two concepts - hardware interface and controllers, so the development of hardware drivers can be decoupled from the development of control algorithms.

{{ image(name="images/control-stack.png", alt="Control Stack") }}
{{ caption(caption="The ROS2 Control Stack for Walli.") }}

I lead the refactoring and integration using ROS2 Control with other team members. Most of the changes are visible in [Pull Request #149](https://github.com/RoboJackets/urc-software/pull/149) and [Pull Request #155](https://github.com/RoboJackets/urc-software/pull/155).


### MoveIt!2 Robotics Arm Control

Using [MoveIt!2](https://moveit.picknik.ai/main/index.html) and the move group tools provided, I'm able to plan the move of Walli's robotics arm in 3d space. At the same time, with the support of real-time servoing programs, the arm is able to be tele-operated.

{{ image(name="images/walli_moveit.png", alt="Walli Moveit") }}
{{ caption(caption="Walli's 5-DOF Arm in Rviz, Controlled by MoveIt!2") }}
