---
permalink: /pages/division/navigationandcontrol
title: Navigation and control
last_modified_at: 2019-09-27
toc: true
---

This division deals with the design and implementation of the control system and the navigation system of the quadcopter. The control system has a front seat-backseat architecture where the Pixhawk flight controller represents the front seat and the Intel Nuc the backseat.  The back seat takes the target relative position from  the  CV  algorithm,  it  computes  a  optimal  trajectory  and  outputs  linear  and  angular  speed references rapresented in the body frame. These references are sent to the Pixhawk via Mavlink and translated in references for each motor. The software implemented in the flight controller is Arducopter an advanced open-source autopilot
system for multicopters, helicopters, and other rotor vehicles which behaves like a PID. The high level controller was implemented in the back seat using ROS together with the Mavlink interface. For the navigation of the drone we are currently using the default Extended Kalman Filter implemented into the flight controller but we are planning to integrate it with the datas collected from both the camera and the other sensors.

## State Machine: SMACH

In order to be able to complete autonomous tasks, we have distinguished the different states of the autonomous drone during the challenge.

• Takeoff

• Target Search

• Target Distant Approach

• Target Close Approach

• Target intercept

• Steal Phase

• Stabilization

• Place and Land

This is implemented as a State Machine in ROS, with the use of SMACH. SMACH is a task-level architecture for rapidly creating complex robot behavior. At its core, SMACH is a ROS-independent Python library to build hierarchical state machines.
