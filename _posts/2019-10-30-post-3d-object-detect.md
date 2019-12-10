---
title: "3D Object Detection from LiDAR Point Cloud"
author_profile: false
excerpt_separator: "<!--more-->"
last_modified_at: 2019-10-30
# classes: wide
header:
  image: /assets/images/2019-10-30-3d-object-detect/model_6000_img_64_top.png
categories:
  - Blog
tags:
  - Object Detection
---

## 1. Introduction

## 2. Model Implementation

## 3. Initial Results
### 3.1 Single Class Detection
### Simple Scenes
Currently the model is trained on a single class: `car`. For the following result, green indicates the ground truth labels, and light blue indicates the predicted results. 

In a simple scene, the model seems to recognize all the car objects:

![model_6000_img_64](/assets/images/2019-10-30-3d-object-detect/model_6000_img_64.png)

![model_6000_img_83](/assets/images/2019-10-30-3d-object-detect/model_6000_img_83.png)

### Harder
Since the model is trained using only the top view LIDAR data, it is reasonable that the model can miss the cases where thr LIDAR point cloud of the object is sparse:

![model_6000_img_95_3dbox](/assets/images/2019-10-30-3d-object-detect/img_95_3dbox_gt.png)

![model_6000_img_95](/assets/images/2019-10-30-3d-object-detect/model_6000_img_95.png)

![model_6000_img_95_top](/assets/images/2019-10-30-3d-object-detect/model_6000_img_95_top.png)

![model_6000_img_95_sparse_top](/assets/images/2019-10-30-3d-object-detect/model_6000_img_95_sparse_top.png)

### Easy Mistake!
However, the model still misses some obvious detection, such as in the following scene. Here, the front car in the very middle doesn't get detected.

![model_6000_img_49_3dbox](/assets/images/2019-10-30-3d-object-detect/img_49_3dbox_gt.png)

![model_6000_img_49](/assets/images/2019-10-30-3d-object-detect/model_6000_img_49.png)

### Why Top View?

What I think the top view (or bird's eye view) detection approach can do well is that: It can detect the objects which are occluded in the front camera view. If we look at the following image, the car on the very right of the image is largely occluded:

![img_99_zoom](/assets/images/2019-10-30-3d-object-detect/zoom.png)

![model_6000_img_99_occlusion_top](/assets/images/2019-10-30-3d-object-detect/model_6000_img_99_front.png)

However, viewing the point cloud from the top, these 2 cars are clearly separated in the space, and therefore the model can easily detect the targeted objects:

![model_6000_img_99_occlusion_top](/assets/images/2019-10-30-3d-object-detect/model_6000_img_99_occlusion_top.png)

### 3.2 Multi-Class Detection

(In progress)

## 4. Final Results

(In progress)

## 5. My Thoughts

## 6. References
- H. Su, S. Maji, E. Kalogerakis, and E. G. Learned-Miller. [Multi-view convolutional neural networks for 3d shaperecognition]() ICCV, 2015
- Bin Yang, Wenjie Luo, and Raquel Urtasun. [PIXOR: Real-time 3d object detection from point clouds]() CVPR, 2018

