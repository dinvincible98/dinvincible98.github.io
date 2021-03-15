---
title: Autonomous Jackal Explorer
subtitle: SLAM|Froniter Exploration|Computer Vision|Pointcloud
subtext: Developed an autonomous Jackal robot equipped with perception, localization, mapping and navigation abilities 
layout: default
modal-id: 7
date: 2021-03-14
img: real.gif
thumbnail: real.gif
alt: image-alt
video: https://www.youtube.com/embed/shDFnn4GH-g
project-date: March 2021
Jackal: Source Code
category: Web Development
intro: Brief Description
description:  This is my individual winter project at Northwestern University. The goal of the project is to build a mobile robotic system equipped with perception, localization, mapping and navigation abilities in both simulation and real world. The robot is capable of exploring an unknown environment autonomously and mapping the world. It can also detect pedestrians and classify different objects with lidar and camera. Based on the changing the environment, the robot should give responses accordingly.  
sub: Hardware Dependencies
description2: Clearpath Jackal Robot, Velodyne-16 Lidar, Intel Realsense Camera D435i   
sub2: Software Dependencies
description3: Gazebo, Slam Toolbox, Costmap2D, hdl people tracking, NumPy, OpenCV(4.5.1), YOLOv4-tiny
sub3: 	Project Breakdown
description4: 1.SLAM(Simultaneous Localization and Mapping)<br>2.Frontier Exploration<br>3. People Tracking<br>4.Real-time Object Detecion 
sub4: Part 1. SLAM
description5: SLAM(Simultaneous Localization and Mapping) technology allows the robot to map an unknown environment while keeps tracking its own location. I used slam toolbox package to accomplish the task.Below is a SLAM flowchart for Jackal.
image1: https://user-images.githubusercontent.com/70287453/111082277-67d75d80-84d5-11eb-9138-d69e5b4e340e.png
sub5:
description6: Demo
image2: https://user-images.githubusercontent.com/70287453/111059530-f3140d00-845b-11eb-8aa3-7b2310e49384.gif
sub6: Part 2. Frontier Exploration
description7: Frontier exploration is a fast and advanced algorithm for robot to explore in an unknown environment and map the world. This algorithm finds every existed frontiers and robot will move to the closest frontier based on its distance to the centroid of frontier. A detailed explaination for my implementation of the algorithm can be found at my github page below. 
sub7:
description8: Demo
image3: https://user-images.githubusercontent.com/70287453/111059806-e8f30e00-845d-11eb-8db0-c0366c25a32b.gif
sub8: 
description9: As shown in the demo, robot will move to the centroid of the closest frontier and constantly updating the map. All found frontiers are represented in blue; If the robot dose not move to the target point in a time limit, then the frontier will turn red and robot will move to the next frontier point.
sub9: Part 3. People Tracking
description10: For people tracking feature, I used hdl_people tracking package which can detect walking pedestrains by extracting information from the pointcloud data then displayed as markerarray in Rviz.
sub10: 
description11: Demo
image4: https://user-images.githubusercontent.com/70287453/111059814-eee8ef00-845d-11eb-96fa-cdfd59554b52.gif
sub11: Part 4. Real-time Object Detection 
description12: This part of the project is also my final project for COMP_ENG 395:Connected and Autonomous Vehicles:Challenges and Design which I thorougly explained how I implemented YOLO using OpenCV and evaluated the performance of YOLOv3, YOLOv4 and YOLOv4-tiny models then tested on the Jackal. Based on my test result, I found YOLOv4-tiny can reach approximately 30FPS in ROS whereas the other two models only have 3FPS. Even though YOLOv4-tiny has less accuracy compared with the other two models, it is still good enough to classify most objects. Besides, FPS is extreamly important in real time detection for autonomous vehicle so I decided to use YOLOv4-tiny on Jackal. My full analysis paper can be found at my github page below.
sub12:
description13: Demo
image5: https://user-images.githubusercontent.com/70287453/111059811-eb556800-845d-11eb-906a-2048baa3e898.gif
sub13: Future Work
description14: 1. Add a boundary feature to the automapping so I can specify an area for the robot to explore instead of trying to map the whole environment(Not realistic if given a very large environment).<br>2. Implement lidar - camera fusion so the detected objects can be shown in the map and use GPU for handling object detection task.<br>3. Estimate the distance between the camera and objects using the depth information from the realsense camera.
---
