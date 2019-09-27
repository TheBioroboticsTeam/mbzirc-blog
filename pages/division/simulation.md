---
permalink: /pages/division/simulation
title: Simulation division
last_modified_at: 2019-09-26
toc: true
---

The  purpose of this division is creating a framework to safely test control and
computer vision algorithms, with obvious advantages with respect to real world testing. In order to achieve this goal, we need to create interfaces between software, simulated hardware, and real hardware, to grant the smoothest transition from the simulation to the real world.

## The Simulation workflow
We have chosen to work in ROS, using Gazebo as a full physics simulator for its native interface with ROS and Ardupilot. All the algorithms are implemented as ROS packages. This highly modular approach allowed us to work on different tasks and to integrate new functionalities effortlessly.

## The low level flight Controller: Ardupilot
Ardupilot possesses the most used DIY flight controller and was thus an obvious choice. Messages between the high level controller and the low level controller are exchanged with MAVlink, which is a very lightweight messaging protocol for communicating with drones (and between onboard drone components).

<figure align="center">
	<img src="{{ '/images/division/simulation/Simulationworkflow.png' | relative_url }}">
	<figcaption>
	The attachment system of the target 
	</figcaption>
</figure>

## The high level flight Controller: Intel NUC i7
We chose to have this on-board computer to perform all the required autonomous tasks:  video acquisition, video processing, computer vision algorithm, control algorithm, navigation and planning. It will interface with the low level controller through MAVROS and MAVlink.

## Setup the Simulation
We have written a tutorial in order to correctly setup everything we needed for the  simulation, which is in order: Setup ROS melodic on Ubuntu 18.04, install gazebo, install Ardupilot, download our custom drone into the Ardupilot/Gazebo simulator, run the simulator, run the cv and control algorithm within the state machine.

## Gazebo Simulator
Gazebo has been a choice of preference because of his excellent physical engine and simple interfaces: less than 2k lines of XML code are necessary to specify every parameter needed in the simulation. Once acknowledged the software is able to provide a very high quality simulation with little effort, we then proceeded to build the simulation environment. Starting from the already existing IRIS model, available on Gazebo’s official model database, we changed the SDF code of the model in order to add two rotors (the IRIS drone is a quadcopter) and to insert our own right inertias and
motor  characteristics. After that, a visual rework has been done, in order to set  the drone to have the right appearances, making visual debugging much easier. Thanks  to a built-in gazebo plugin which communicates to ardupilot, we were able to control the simulated drone via MAVlink messages, thus creating the above-mentioned interface, since also the real model will be controlled in this way.  It must be noted that putting excessive focus into building a photorealistic scenario is not useful: given the wide availability of real videos, the purpose of simulation is not to train
computer-vision  algorithms,  but  rather  to  use  them  (even  in  a  simplified  version), and once the position of the ball has been acquired, to proceed with the chasing and grasping.




