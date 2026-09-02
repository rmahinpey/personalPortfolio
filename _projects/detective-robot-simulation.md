---
title: "Detective Robot Simulation"
excerpt: "Self-driving clue-detecting robot for competition. Designed CNN for image recognition, simulated using Gazebo."
order: 2
tags: [Python, Gazebo, "Machine Learning", Simulation, ROS, Controls, "Computer Vision"]
header:
  teaser: /assets/images/projects/logo-ros.jpg
  overlay_image: /assets/images/projects/logo-ros.jpg
  overlay_filter: 0.25
---

<span class="label label--info">In Progress</span>

## Autonomous Detective Robot

**ROS · Gazebo · Python · OpenCV · YOLOv5 · CNNs · Computer Vision · Machine Learning**

### System Overview

For UBC's ENPH 353 autonomous robotics competition, my teammate and I developed a simulated autonomous robot capable of navigating a complex urban environment while obeying traffic rules, avoiding dynamic obstacles, and visually identifying eight alphanumeric "clue boards" distributed throughout the course. The final system used a hybrid architecture combining learned driving, classical computer vision, object detection, and finite-state control. My primary ownership was the robot's **clue-recognition perception pipeline**: dataset generation, character-recognition training infrastructure, YOLO-based clue-board detection, image-processing tools, and failsafe recovery logic.

### Clue Detection and Character Recognition

A major challenge was building a perception system capable of reading small, low-resolution text from a moving robot. I developed a **YOLOv5 clue-board detector** that first reduced the full camera image to the region containing a clue. From there, I built an OpenCV pipeline to isolate and segment individual characters. The pipeline cropped the board, applied HSV-based colour filtering, used morphological erosion to separate characters that had merged together, identified connected regions using contours, and then dilated the isolated characters before classification. This separation between object detection, image processing, and character recognition made the system significantly easier to debug than attempting to solve the entire perception problem with a single model.

### Synthetic Data and Model Training

One of the largest problems was that clean synthetically generated characters looked very different from the noisy, pixelated images produced by Gazebo. I therefore built a **synthetic data-generation and augmentation pipeline** rather than relying on manually collected images. Training samples were heavily modified with Gaussian noise, blur, affine transformations, skew, and other distortions intended to reproduce the appearance of characters observed by the simulated camera. This allowed new datasets and models to be regenerated rapidly as weaknesses were discovered. I initially developed a custom CNN-based character classifier and iterated on both its training data and preprocessing pipeline before eventually moving to YOLOv5-based character recognition when it demonstrated better robustness at longer viewing distances.

### Perception Debugging Infrastructure

Debugging the perception stack became an engineering problem of its own. A bad prediction could originate from the detector, HSV thresholds, character segmentation, morphological processing, or the neural network itself. To isolate these failure modes, I developed both a **Jupyter-based test environment and a real-time graphical debugging node** that displayed intermediate images at each stage of the pipeline while the robot operated in Gazebo. This made it possible to distinguish model failures from preprocessing failures without repeatedly retraining the network. One particularly difficult issue was the "fat letter" problem, where HSV thresholding caused adjacent characters to merge into a single connected region; systematically visualizing the pipeline led to the erosion-and-dilation solution used in the final implementation.

### System Integration and Recovery Logic

I also implemented the robot's **failsafe recovery system**. A lightweight ROS node continuously compared camera frames over a short time window; if effectively identical frames persisted, the system inferred that the robot had become stuck and automatically respawned it at the beginning of the course. The complete perception subsystem operated alongside the team's learned driving controller, crosswalk detector, pedestrian detector, and finite-state machine. A dedicated high-resolution camera stream was used for clue recognition so that signs could be detected earlier and remain visible for more frames without sacrificing the lower-resolution stream used for real-time navigation.

### Results and Engineering Lessons

In pre-competition testing, the integrated robot achieved repeated autonomous runs of approximately **2 minutes 20 seconds at 0.8 m/s while successfully collecting clues from all eight signs**. The official competition run ultimately exposed a separate system-level weakness: additional computational load reduced Gazebo's real-time factor enough to alter the behaviour of the learned driving controller, resulting in a collision after three clues. While my perception pipeline was only one component of the overall robot, the project taught me how to build and debug an ML system as an engineering pipeline rather than treating the neural network as a black box — from generating representative data and designing preprocessing algorithms to creating diagnostic tooling and integrating perception into a larger autonomous system.