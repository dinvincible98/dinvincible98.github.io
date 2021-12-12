---
title: 3D optical flow
subtitle: Computer Vision|Pointcloud Processing|Deep Learning
subtext: A deep learning model that can perdict sub-pixel movement from 3d optical flow 
layout: default
modal-id: 9
date: 2021-12-10
img: flow.gif
thumbnail: flow.gif
alt: image-alt
video: 
project-date: Dec 2021
Flow: Source Code
category: Web Development
intro: Brief Description
description: This is my final project at Northwestern University. The project is focused on using a rgbd camera(Intel Realsense D435i) to capture an object with random motion. By capturing the pointcloud at consecutive timestamps and giving a groundtruth motion, the deep learning model is able to learn the sub-piexl motion(less than 5mm). The whole project is simulation based using ROS and Gazebo.
sub: Software Dependencies
description2: Gazebo, PCL, Open3D, NumPy, OpenCV(4.5.1), Pyrealsense
sub2: Project Breakdown
description3: 1.Setup simulation environment<br>2.Post-processing raw pointcloud data<br>3.Given random gaussian motion<br>4.Capture pointcloud data and corresponding groundtruth motion<br>5.Training Deep learning model<br>6.Evaluation of the model<br>
sub3: Part 1. Setup simulation environment
description4: The simulation is all done in Gazebo. The realsense camera is pointing at the small cube which is the moving object. The giant cube behind acts like a static wall. The idea here is when the small cube is moving which means its pointcloud is also shifting, whereas the wall will not move and act like a ground reference. It is important for the deep learning model to learn the motion.
image1: https://user-images.githubusercontent.com/70287453/145697005-a5e690b8-242a-4917-a2f1-5a3d55eea54f.png
sub6: Part 2. Post-processing raw pointcloud data
description7: In this step, I used PCL library for post-processing raw pointcloud data. I used passfilters, voxelgrid filter to filter out unnecessary point clouds and only focuses on ROI(region of interest).
image3: https://user-images.githubusercontent.com/70287453/145697021-d77cfa97-345e-4165-8d99-3fe8d5179086.png
sub9: Part 3. Given random gaussian motion
description10: I wrote a ROS simulation node which subscribe the states of the cube from gazebo world then publish a motion with gaussian noise added to it. The motion is very small(<5mm) since I want to achieve sub-pixel movement prediction.
sub11: Part 4. Capture pointcloud data and corresponding groundtruth motion
description12: In this step, I firstly saved pointcloud data and corresponding motion data into rosbag and then convert it to pcd files and motion.txt file. Aligining the timestamp is key here, I used python for extracting files names and timestamps then did a matching for pcd files and corresponding motion in the same timestamp  
sub12: Part 5. Training Deep learning model
description13: The deep learning model adopted the thinking of scene flownet3d. It consist of set conv2d layers, flow-embedding layers and set upconv2d layers. set conv2d layers is used for grouping pointclouds based on a specific radius. flow-embedding layers learns to aggregrate both feature similarites and spatial relationship to produce embeddings that encode point motions. the set upconv2d layers are used to propapage and refine the embedding in a informed way. In the original flownet3d, it uses rgb color as a learning feature and it calculates the geometric differences between two pointcloud. However, my proposed approch does not rely on the rgb color and geometric difference. Insted, I give a groundturth motion for a pair of pointcloud and see if the model can learn such motion.
sub13: 6.Evaluation of the model
description14: I generate around 15000 pointcloud from simulations and I use 13000 files for training and rest for testing. During evaluation, I use two accuarcy metrics. 1.Error within 10mm. 2. Error within 5mm. The final accuracy reaches 78% for errors within 10mm but only 52% for errors within 5mm. Even though the result is not very ideal, it can be improved by creating a larger dataset and tunning some hyperparameters. 
---
