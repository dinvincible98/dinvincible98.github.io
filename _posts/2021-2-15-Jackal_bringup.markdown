---
title: Jackal ROS Noetic Bringup 
subtitle: Network Configuration|ROS|Debugging
layout: default
modal-id: 8
date: 2021-02-15
img: jackal.jpg
thumbnail: jackal.jpg
alt: image-alt
video: https://www.youtube.com/embed/BzSmWLWmOxg
project-date: Feburary 2021
Bringup: Source Code
category: Web Development
intro: Brief Description
description:  This is the final project for the course MAE106 mechanical system labratory at UC Irvine and the task is to design a wheel robot and participate a robot contest.
sub: Mechanical Design
description2: Our mechanical design goals were to build a robot that was stable, efficient and has a low fraction. To achieve stability, we wanted to make sure the error is small, so we employed the CNC router to cut pur wood plates. For wood selection, we chose plywood instead of the one given by school because it is lighter, smoother and has a better structure for CNC cutting. Besides, we cut two polycarbonate plates for the installation of power transmission. Moreover, we expected collision with other robots, so we tried to lower the center of mass of our robot by reducing the length of vertical plates.
sub2: Software design
description3: For software design, we first want an accurate heading reading. We had heard that the magnetometer would be interfered by many factors, since the magnetic field of the earth is quite weak compared to the magnets, solenoids, and other electronics, so we decided to also add a gyroscope to eliminate sudden, and incorrect directionschange. We bought a LSM9DS1 chip — a 9DOF IMU with a magnetometer, an accelerometer and a gyro. To code this chip, we modified the existing library for this Adafruit LSM9DS1, so the heading is calculated within the library functions. Calibrations were added into the sensor reading functions, along with a simple low pass filter. The magnetometer read just fine, but the gyro, after integration, always have a random shift, the accelerometer after two integrations only got worse. We then tried comparing heading readings both from the magnetometer and the gyro using a Madgwick filter, the shift is kind of eliminated. Initially, it still has a low frequency noise that puts a plus or minus 10 degrees, but after adjusting the low pass filter of the magnetometer and gyro readings, the noise is much smaller.<br>For more detailed information, please view my github page below.
---
