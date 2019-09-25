---
permalink: /pages/aboutus/
title: ""
last_modified_at: 2017-10-20T12:42:38-04:00
toc: true
---

The MBZIRC SSSUP team is a group of 35 engineering students from Sant’Anna university, which, led by Stefano Roccella, researcher of the Livorno Laboratory of the Biorobotics Sant’Anna institute, will compete in Abu Dhabi in 2020.

## Our Setup
We are competing with 3 drones. Two of them will carry out the obstacle avoidance tasks. They are exacopters built at the Autonomous drone laboratory in Livorno. In this section we present the design choices and the selection of the components to build the custom drone. Based on the rules and specification section the requirements for the platform would be:

• An autonomy which is roughly between 10 and 25 minutes, strongly dependent on the strategy.

• Constraints on dynamic performances, the more performances we have the easier it is to match the target speed and intercept it.

• The eventual capability to navigate in an unstructured, indoor environment in the case we want to use the same platform for the third challenge.


### • The Exacopters

### • The Quadcopters

<div align="center">
<figure align="center">
	<img src="{{ '/images/setup.png' | relative_url }}">
	<figcaption align="center"> The quadcopter
	</figcaption>
</figure>
<table>
<tr><td> Frame </td><td> Tarot 650 Sport </td></tr>
<tr><td> Motors </td><td> Less than 10m/s </td></tr>
<tr><td> Electronic Controller </td><td> Boh </td></tr>
<tr><td> Low level Control </td><td> PixHawk  </td></tr>
<tr><td> High level Control </td><td> Intel NUC i7 </td></tr>
<tr><td> Unloaded weight </td><td> 2.6 kg </td></tr>
<tr><td> Fully loaded weight </td><td> 3 kg </td></tr>
</table>
</div>

## Our Organization
A  strong  organizational  effort  is  needed  to  make  such  a  group  of  engineers  with  different
backgrounds and seniority work together efficiently.  We decided to tackle the Challenges by
identifying 6 macro problems and dividing in groups.  The Divisions are:

• Computer Vision Division

• Components Design Division

• Indoor Testing Division

• Dynamics and Simulation Division

• Control Division

• AI Division

<figure align="center">
	<img src="{{ '/images/organization.jpg' | relative_url }}">
	<figcaption align="center"> Organization chart
	</figcaption>
</figure>
<br>
We will further discuss the role of each division.


