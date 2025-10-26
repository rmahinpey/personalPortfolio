---
title: "Pet Rescue Robot"
excerpt: "Fully autonomous robot built from scratch for a toy pet rescue competition. Body was laser cut, 3D printed, and machined from scratch. Pet recognition done with a neural network."
order: 1
tags: [Machining, ESP32, "Computer Vision", Sensors, Kicad, "Raspberry Pi", Solidworks, "Systems Design", Controls]
header:
  teaser: /assets/images/projects/robot-summer.jpg
  overlay_image: /assets/images/projects/robot-summer.jpg
  overlay_filter: 0.25
---
# Project overview

This was a robot that me and 3 other teammates designed for the annual eng phys robot competition at UBC. The competition was simple: pickup the most "pets" (which took the form of plush animals) in 2 minutes. Over 6 weeks, we designed, protoptyped, and manufactured a fully autonomous robot from scratch! No pre made kits, no hand holding, and no time to waste!

### High level design

The first stage of the robot, which involved contribution from the entire group, was to come up with a design to be able to pitch. After thorough consideration of problem constraints, ease of prototyping, and timeline, we came up with our high level design. We decided to detect the pets, we would use a camera with a trained neural net. This came with multiple benefits. As opposed to other sensor options, such as magnetometers (the pets had magnets inside) and LIDAR sensors, a camera had the broadest field of view and rage. We came to this conclusion after extensive testing, finding that magnetic sensors were prone to noise and needed to be close to detect the pets.

As for autonomous driving, there was a black line on the course, so PID controlled line following was the obvious answer. However, there was a break in the line, called "debris" which was a semi random cluster of wooden blocks which the robot needed to be able to traverse. To get by this, I designed a custom "skid wheel" by measuring the geometry of the obstacle and CADING a front wheel in solidworks to match.



