---
title: KUKA youBot manipulation
subtitle: Feedback Control|Motion planning
subtext: KUKA youBot finishes a pick and place task in V-rep simulation scene
layout: default
modal-id: 2
date: 2020-12-03
img: best.gif
thumbnail: best.gif
alt: image-alt
video: https://www.youtube.com/embed/bPBQET7Chcs
project-date: December 2020
KUKA: Source Code
category: Web Development
intro: Brief Description
description: This is the final project for the cource ME 449 Robotic Manipulation at Northwestern University. It is also the capstone project for the course "Modern Robotics" on Cousera.The goal of the project is to wirte a program that enables KUKA youBot to finish a pick and place task in V-Rep simulation scene.
sub: Procedures for motion planning
description2: 1. Plan a trajectory as desired trajectory for the end-effector to follow <br>2. Use the previous desired trajectory in feedfoward+PI to calculate the kinematics of the youBot<br>3. Use the calculated kinematics to drive the youBot <br>4. Save the result as a .csv file and conduct simulation in V-rep scene 6.
sub2: Strategy for completing tasks
description3: There are three tasks and I need to choose a controller and find the best configuration setup.<br>For task 'Best', the main goal is to minimize the end effector error so I choose to use Feedfoward + PI controller. With KP = 20, KI = 0.5, this controller presents a very good result that the end effector error becomes very small as time goes by and the KUKA youBot finishes the task smoothly and accurately in the simulation.<br>For task 'Overshoot', I need to find an end effector error with large overshoot value. With KP = 2, KI = 0.001, there is a overshoot between 9 - 14s.<br>For task 'NewTask', I can customized a target location for the robot to go and I used the same strategy as the task 'Best'. With KP = 20, KI = 0.1, the end effector error is very small and the robot finishes the task very well in the simulation.<br>For more detailed information, please visit my github page below.  
---
