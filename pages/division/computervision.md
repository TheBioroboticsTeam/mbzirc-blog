---
permalink: /pages/division/computervision
title: Computer vision division
last_modified_at: 2019-09-27
toc: true
---

The purpose of the computer vision section is to create the algorithms needed for the perception system on the drone to be able to correctly identify the target in an unstructured outdoor environment. There are several challenges associated with the task, and several state of the art solutions have been proposed to tackle these difficulties. We will now proceed with a careful review of these aspects.

## The Arena

It is extremely important to understand as many characteristics of the arena not to have unforeseen problems during the challenge.  The first challenge will take place in an outdoor open space, a field of approximately 80 x 50 x 40 meters, similar to a football field in size. The arena would probably consist in a parking spot.

## The target
We know that the target is a drone which will bring a 10-15cm (diameter) ball in mid air, performing a 3D trajectory in space. We do not know any information about the material or the colour of the ball.

## Current Setup

Under the current setup, the drone equips a Mobius ActionCam as front camera, which enables the system to acquire frames with a 150 FOV at 1080p 30 fps.  Any captured image is either processed by a detector or a tracker, depending on the current state of the drone.
The  detection  algorithm  keeps  running  on  newly  acquired  frames,  until  the  target  is  eventually found. When a successful detection occurs, the drone locks onto the target and switches to tracking mode. Taking into account the previous positions in the images, the tracker attempts to follow the object movements; if by chance the objective is lost, or the max number of consecutive frames (20 in our case) is reached, the drone switches back to detection mode.  All the experiments have been run on a red ball.  Red infact proved to be the most difficult color to detect as the sensitivity is lower and there is a lot of noise in the red frequency on the ground test where we run our tests.

## The Detection Algorithm

In order to detect the presence and position of the target in a given frame, we adopt a custom multi-stage algorithm, which exploits both classic and modern computer vision techniques.

### •HSV Representation and filtering

Firstly, the image is converted to HSV color representation, which makes it easier to subsequently extract areas having approximatively the same color of the ball.  The color thresholds are carefully tuned before the experiment,  since they strongly depend on the actual lighting conditions. It is advisable  to  calibrate  this  filter  to  be  quite  selective  to  exclude  false  positives,  even  if  this  may
result  in  portions  of  the  target  body  being  filtered  out;  in  this  stage,  the  aim  is  just  to  locate some regions that may contain balls,  instead a more precise detection is locally performed later. Among the found regions, those whose area is below a certain threshold (few pixels) are classified as environmental noise, thus discarded; this might potentially exclude the target when it is really far, anyway it wouldn’t be reliable to detect any object from very few pixels. Out of the eligible portions, in order to limit the computational cost,  only the five largest ones are kept, under the assumption that the actual target,  if present,  is most likely contained in one of these. For each of them, the algorithm determines a region of interest (ROI) where to perform a new, thorough local search. Such ROI is a rectagular box, three times larger than the corresponding region and centered on it:  the purpose is to ensure that false negatives are included back, that is ”good” pixels
that were accidentally discarded when filtering.

### •Background and foreground extraction:  The Grabcut algorithm

Within this box, on the basic of color values, we mark few points that belong for sure to  the background, as well as we tag some pixels that would be probably part of the body if the target is actually present. This information is exploited to segment the subfigure with the grabcut algorithm, which turns out to be fairly accurate in determining the exact pixels that make up the identified object.

### •Background and foreground extraction:  Hu Moments

Then, by comparing the Hu moments of this object with the true target ones (precomputed before the experiment), it is possible to tell whether the entity is actually the target ball or something else. If more than one pseudo-circular object is found, we lock onto the most similar (in terms of shape) to the actual target. The distance between the drone and the target is estimated by the means of a simple proportion between the ball diameter (which is known) and its apparent size (in
pixel).

### •Target pose estimation

Similarly, the position is estimated as well.  Finally, the tracker is enabled and initialized with the
position.

## The Tracker

The tracker is CSRT, a discriminative correlation filter tracker with channel and spatial reliability. Our experiments show that, when properly initialized, it is very robust to sudden movements and temporary  occlusions. Alone, the tracker is generally able to follow the target for a very long sequence of frames (more than a thousand).  This property is a double-edged sword: if for any reason a misdetection occured in the previous stage, the drone is likely to remain locked on a spurious  object,  which  is  a  very  bad  scenario. Therefore, we choose to periodically perform a detection in between of the trackings, even if this results in slightly worse performances.

## Detector Tracker Balance

## The Validation

In classical computer vision there are hundreds of different slightly different algorithms which perform better depending on the situation. Let’s just think to all the possibilities for the detection and tracking algorithm:
	Given  the  space  of  possibilities, we had to make some reasonable  assumptions based on the type of the problem to identify a set of possibly optimal algorithms and then, discriminate the best performing one. Usually, performances among the best working algorithms are similar, and there are lots of hyper parameters to tune which makes the task of choosing the best one exponentially hard. In order to  evaluate performances objectively we would like to implement an evaluation algorithm which based on a dataset is able to evaluate the algorithm based on some metric.



