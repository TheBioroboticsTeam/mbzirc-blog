---
permalink: /pages/division/componentsdesign
title: Components design division
last_modified_at: 2019-09-28
toc: true
---

The whole purpose of the first challenge is to be ablemto correctly grasp the target ball and steal it from the Drone.  This highlight the critical role played by the grasping system during the challenge. The design process of the manipulation system determines how we approach, control, and stabilize he drone during the ”steal” phase.  The goal is to provide the control division with a basic but fully functional model which will be used in the first trials,but by the actual competition, there are other ideas with a lot of potential.  We will further discuss such solutions later.

## Requirements for the gripper

## 3D printed solution

Our gripper will be 3D printed based on the CAD design proposed in the following images.  It has
1 degree of freedom and it is easily actuated by an electric motor.
<br>
We’ve also designed a retractable mechanism to be able to reposition the center of gravity of
the drone in the same place as it was before the taking the soft baloon, achieved by replacing both
the gripper and the battery by opportune value as we can see in the following image.

<table>
<tr>
<td>
	<img src="{{ '/images/division/componentsdesign/gr1.png' | relative_url }}">
	<figcaption>
	The gripper in its closed configuration
	</figcaption>	
</td>
<td>
	<img src="{{ '/images/division/componentsdesign/grapA.png' | relative_url }}">
	<figcaption>
	The gripper in its open configuration
	</figcaption>	
</td>
<td>
	<img src="{{ '/images/division/componentsdesign/retrac.png' | relative_url }}">
	<figcaption>
	The retractable mechanism 
	<br>
	</figcaption>	
</td>
</tr>
</table>

In the 3d printed gripper we also would like to implement a bio-inspired passive ”fingertip” which grants more grip and allows for less precision during the approach phase.
<br>
In the following video we can see the complete 3d model of the drone realised with solidworks.

<video width="600" height="400" controls>
    <source src="{{ '/images/division/componentsdesign/model.mp4' | relative_url }}" type="video/mp4">
</video>

## Soft Gripper

We are evaluating the implementation of an innovative passive-soft gripper based on bistable mech-
anisms and highly friction materials. That’s what we would like to design in the long term but it’s really complicated and we cannot assure we’re going to be able to do it.


