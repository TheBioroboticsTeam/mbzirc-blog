---
permalink: /pages/division/vehicledynamics
title: Vehicle dynamics division
last_modified_at: 2019-09-27
toc: true
---

The dynamics of the vheicle is currently managed by Arducopter.  In simulation, this means that
we have to specify a long list of parameters to determine the aerodynamics and the inertial charac-
teristics of the drone and its propellers.  Based on these parameters an Arducopter gazebo plugin
is able to simulate the physics within Gazebo physics simulator.  In the real world, what happens
is that before the first flight, we have to perform the calibration of the low level flight controller which is responsible both for the stabilization and the position/velocity control.  The PIXHAWK builds an internal dynamical model performing a basic identification, and then generates command with a classical cascade PD controller, an internal one for the attitude control and an external one for the higher level control.
	If we want to build an even higher level controller, (which in our case is the Intel NUC i7) to generate commands for the PIXHAWK, we are limited to this position and velocity control which
is a strong limitation if we want to do some long term planning over a trajectory.
	If we were able to perform the same identification.

## System Identification

## Simulation on MATLAB

## Control Implementation

## Results



 
