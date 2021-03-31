---
title: EKF SLAM On Turtlebot3 from Scratch
subtitle: EKF SLAM|Robotics Sensing & Navigation|Machine Learning|Differential Drive Control
subtext: Implemented an Extended Kalman Filter on Turtlebot3 in both known and unknown data association and used machine learning to detect landmarks from laserscan  
layout: default
modal-id: 9
date: 2021-03-20
img: unknownEKF.gif
thumbnail: unknownEKF.gif
alt: image-alt
video: https://www.youtube.com/embed/qTvNrYvYrNc
project-date: March 2021
EKF: Source Code
category: Web Development
intro: Brief Description
description: This is my implementation of Extended Kalman Filter SLAM on Turtlebot3. The blue path is the real(ground truth) path, the red one is the EKF slam path and the green one is the odometery path. The blue circles are tubes from simulator, green circles are landmarks sensed by customized laserscan and the yellow circles are estimated locations of landmark from EKF SLAM. 
sub: Turtle Simulator
image6: https://user-images.githubusercontent.com/70287453/113029334-e973f000-9151-11eb-9d7a-b25c36e05183.gif
description2: This is a customized simultor for turtlebot3. In this simulator, the turtlebot is represented by a green sphere. Tubes are shown in blue color at given location. When the robot moves close enough to the tubes, the fake laserscan can detect them and publish the red tubes with some noises. The fake laserscan uses circle-line intersection algorithm to detect the tubes.
sub2: EKF SLAM
description3: EKF SLAM is a class of algorithms which utilizes the extended Kalman filter (EKF) for simultaneous localization and mapping (SLAM). Typically, EKF SLAM algorithms are feature based, and use the maximum likelihood algorithm for data association.<br> This algorithm can be divided into two parts:State update and measurement update. The state estimate is the same for both.<br>The robot state used a probabilistic motion model. Xi bar is the state estimate at time t, g is the motion model, u is the body twist at time t and epsilion is the motion noise:<br>\begin{equation} \hat{\xi_t^-} = g(\hat{\xi}_{t-1}, u_t, \epsilon) \end{equation}<br>Next, propagate the uncertainty using linearized transition model:<br>\begin{equation} \hat{\Sigma_t^-} = g'(\hat{\xi}_{t-1}, u_t, \epsilon) \ \hat{\Sigma}_{t-1} \ g'(\hat{\xi}_{t-1}, u_t,\epsilon)^T + \bar{Q} \end{equation}<br>The process noise is a diagonal matrix corresponding to the gaussian noise for the robot pose(x,y,theta)<br>\begin{equation}\bar{Q} =\begin{bmatrix} Q & 0_{3*2n} \\ 0_{2n*3} & 0_{2n*2n} \end{bmatrix}\end{equation}<br>The algorithm can be found below.
link1: EKF SLAM
sub3: Feature Detection
description4: The laserscan is clustered by many points using a distance threshold. To find circles in cluster, I implemented the circle fitting algorithm. The algorithm can be found below.
link2: Circle Fitting
sub4: Known Data Association
image7: https://user-images.githubusercontent.com/70287453/111915711-a1641780-8a45-11eb-8195-0a614c478679.gif
description5: Known Data Association assumes we known the relative positions of landmarks in the robot frame.<br> For each measurement, i is assocaited with landmark j, then compute the Kalman gain K.<br>\begin{equation} K_i = \Sigma_t^- h_j' \ (\xi_t)^T (h_j' \ (\xi_t) \Sigma_t^- \ h_j'(\xi_t)^T + R)^{-1} \end{equation}<br> Next, use the measurement model to predict the state given current belief and updated posterior state<br>\begin{equation}\hat{z_t}^i = h_j(\hat{\xi_t^-}) \end{equation}<br>\begin{equation} \hat{\xi_t} = \hat{\xi_t^-} + K_i(z_t^- - \hat{z_t^i}) \end{equation}<br> Lastly, compose the posterior covariance.<br>	\begin{equation} \Sigma_t = (I - K_i h_j'(\xi_t)) \Sigma_t^- \end{equation}<br>
sub6: Unknown Data Association
image8: https://user-images.githubusercontent.com/70287453/111963676-c8602f00-8ac1-11eb-87e3-ce65009a0f91.gif
description7: This data association is achieved by using the mahalanobis distance.<br> Iterates over the number of the observed landmarks N where k is the landmark number.<br>\begin{equation} \psi_k = h_k’(\hat{\xi_t}^-) \Sigma_t^- \ h_k’(\hat{\xi_t}^-)^T + R \end{equation}<br> Then, calculate the predicted measurement above<br> Next, compute the Mahalanobis distance and append to a vector of measurements<br> \begin{equation} d_k = (z_i - \hat{z_k}) \psi_k (z_i - \hat{z_k})^T \end{equation}<br>Let d_star be the minimum mahalonbis distance and  be the landmark index corresponding to the minimimum distance. If d_star is smaller than the lower-bound Mahalanobis threshold, then j is the index used in the measurement update. If it is greater than the upper-bound Mahalanobis threshold, then j = N and increase N by 1.<br> The algorithm can be found below.
link3: Unknown Data Association
sub8: Differential Drive Control
description9: The diff_drive class performs the calculation for turtlebot's odometery. The purpose of this class is to convert wheel velocities to a body twist Vb and then integrate twist to get pose.<br> The full explaination can be found below.
link4: Differential Drive Calculation
---
