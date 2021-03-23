---
title: Jackal ROS Noetic Bringup 
subtitle: Network Configuration|Robot Setup|ROS|Debugging
layout: default
modal-id: 8
date: 2021-02-15
img: jackal.jpg
thumbnail: jackal.jpg
alt: image-alt
video: https://www.youtube.com/embed/kWFRQgxNj1g
project-date: Feburary 2021
Bringup: Source Code
category: Web Development
intro: Brief Description
description:  This is a setup instruction for how to bring Clearpath Jackal to ROS Noetic which is the latest version of ROS. Since many packages used for Jackal are not officially released for ROS noetic, this instruction will guide you how to build and set up jackal from scratch.
sub: Process Architecture
description2: 1. Installing Ubuntu 20.04 LTS<br>2. Setting up the wireless network<br>3. Installing ROS Noetic<br>4. Building packages and dependencies on Jackal<br>5. Building Jackal packages on remote pc<br>6. Setting up ROS between Jackal and remote PC<br>7. Final setup for Jackal specifics
sub2: 1. Installing Ubuntu 20.04 LTS
description3: The first step is to install Ubuntu 20.04 LTS on Jackal. I recommended to prepare a new SSD and a bootable USB then follow the official Ubuntu setup from the website.
sub3: 2. Setting up the wireless network
description4: The second step is to connect Jackal to Wifi. This step is not strictly necessary but it is very convient if the Jackal connect to the Wifi directly. A detailed instruction can be found in my githhub page bbelow. 
sub4: 3. Installing ROS Noetic
description5: Install ROS Noetic on both of your remoet pc and Jackal. Please follow the official ROS setup instruction.
sub6: 4. Building packages and dependencies on Jackal
description7: Since many packages for Jackal written by Clearpath aren't released for ROS noetic so they need to be built from source. Building those packages is a strightforward process and it can be done by cloning source code into your own workspace then run catkin_make. See my gthub page for all needed packages and detailed instruction.
sub8: 5. Building Jackal packages on remote pc
description9: Similar to the previous step, user need to build unpublished packages by building source code in workspace.
sub9: 6. Setting up ROS between Jackal and remote PC
description10: To let your Jackal and PC share a ROS master, you need to set up ROS_MASTER_URI and ROS_HOSTNAME environment on both Jackal and remote pc.
sub11: 7. Final setup for Jackal specifics
description12: Those are key steps to get Jackal up and running by setting up all undocumented intricates implemented by Clearpath on a Jacakl image. User need to add udev rules and install package for VLP-16. Please see my github page below for detailed instructions.
---
