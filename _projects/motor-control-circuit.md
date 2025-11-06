---
title: "Motor Control Circuit"
excerpt: "Fully electrical motor PWM feedback circuit. Using DAC, PI control, 8-bit counters, flip-flops, D-latches."
order: 4
tags: [Oscilloscope, "Waveform Generator", "Digital Circuits", "Circuit Debugging and Analysis"]
header:
  teaser: /assets/images/projects/feedback.jpg
  overlay_image: /assets/images/projects/feedback.jpg
  overlay_filter: 0.25
---
# Project overview
The goal of this project was to create an electrical motor control feedback system. This was done with a motor that spins a circular array of slits over an LED, controlling the LED on / off cycle. This LED then shined on a photodiode, which created an analog signal. The circuit's jump was to be able to create a stable motor output using this analog signal. This project integrated digital and analog electronics to create an analog PI controller.
