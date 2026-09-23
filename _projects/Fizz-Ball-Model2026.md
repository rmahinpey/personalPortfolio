---
title: "Fizz Ball Model"
excerpt: "Schrodingers cat inspired drink dispensing system for Eweek 2026."
order: 7
tags: ["Power Electronics", Solidworks, "Circuit Design", Machine Learning]
header:
  teaser: /assets/images/projects/cat.jpg
  overlay_image: /assets/images/projects/cat.jpg
  overlay_filter: 0.25
---

# Project Overview
The Ball Model Competition is a yearly contest between engineering faculties where you build something related to your faculty. Being passionate about physics (and of course being an eng phys student) I decided to build a robot that demonstrated the concept of Schrodingers cat. The project also needs to dispense beverages to the judges.

# High Level Design
![Cat hi]({{ '/assets/images/projects/Cat_hi.jpg' | relative_url }})
![Cat CAD]({{ '/assets/images/projects/CatCAD.png' | relative_url }})

To replicate the famous thought experiment, we needed a way to know that the box that the Cat was inside was being observed. I decided to use computer vision for this task, as the camera could easily replace the eye of the cat and have a robotic / techy look. The benefit of using a camera is that the cat can track the face of the user and follow it. Integrating a laptop as well as a circuit board with an ESP32, we could now compute high level computer vision and control the low level hardware. The system was powered by a bench top power supply.

From a mechancical design perspective, no significant load needed to be moved, so standard hobby servo motors were more than enough for the task. The cat lies on a thrust bearing and has it's yaw controlled by a servo motor, as well as it's arm controlled by a servo so that it can "wave" at users.