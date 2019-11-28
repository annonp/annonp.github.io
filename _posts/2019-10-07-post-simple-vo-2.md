---
title: "A Simple Monocular Visual Odometry: Part 2"
author_profile: false
excerpt_separator: "<!--more-->"
# classes: wide
header:
  image: /assets/images/vo_header.png
categories:
  - Blog
tags:
  - MATLAB
  - VO
---

## Notes
This is a second post that continues the implementation from the last part. I will try to complete a write-up as much as possible.

***Disclaimer:***

## Problems from Previous Implementation
Coming soon ...

## Estimate World Camera Pose
Coming soon ...

~~~matlab
~~~

## Bundle Adjustment
Bundle adjustment is a very cool concept. Coming soon ...

~~~matlab
~~~

## Results

Putting it all together, the `vo_initialize.m` function initializes the VO pipeline, creating initial 3D point landmarks, extracting initial keypoints, and estimating the initial pose of the camera. The `vo_process.m` sequentially extracting and tracking image features from an image frame, across frames, and simultaneously estimating the pose of the camera. Bundle adjustment is also implemented to refine the estimated pose at each step. Lastly, new 3D points are regularly created as the number of currently tracked keypoints is shrinking over time. The following is the final result.

<iframe width="560" height="315" src="https://www.youtube.com/embed/A5HnnSiZ_LM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/><br/>

From the video, it is obvious that this is not a state-of-the-art implementation. There are various components that are not implemented. As we can see, the estimated trajectory starts to deviate from the ground truth after some time, due to the scale drift--a common problem in monocular VO. The estimated trajetory also wiggles slightly, probaly due to the fact that the full bundle adjustment is not implemented. And the most importantly, I did not try to implement a loop closure ().

## Reflections

Although this implementation is not perfect, it serves my purpose of learning, research, and self-satisfaction. Academic papers are full of theories, but there usualy are missing steps. Here I tried to connect those steps, and it stands as a self-assesment of my understanding of visual odometry. (It took me about 3 weeks during my free time to build this VO.) 