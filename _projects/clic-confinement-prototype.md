---
title: "Microfluidics pressure Control system. – ScopeSys Inc."
excerpt: "Co-op project at Scopesys. Developed pressure control system for microfluidic chip. Plenty of design interation through CAD. Wrote firmware for sensor, designed circuits for setup."
order: 3
tags: [Microcontrollers, Electronics, Sensors, Solidworks, "3D printing", Prototyping, Python, C++, Instrumentation]
header:
  teaser: /assets/images/projects/testRig.jpg
  overlay_image: /assets/images/projects/testRig.jpg
  overlay_filter: 0.25
---

# Project overview
During my coop at scopesys, I worked on developing a prototype pressure control system for a microfluidic cell. The objective was to test different hardware and to test functionality of their technology. Throughout the project I gained invaluable experience in controls, instrumentation, fluid mechanics, and more.

## firmware and electronics
To gain a sense for funtionality, I first had to write drivers to read to be able to read data from a pressure transducer. I wrote drivers for a HSCDRRN160MD2A5 pressure transducer using an I2C bus. I then integrated this with a NE - 1000 syringe pump using UART communication. After integrating this with some low pass filters, and LEDs as visual indicators, I had a working autonomous pressure control system.

## fluidics
In order to be able to pressurize the cell properly, I had to perform calculations to determine total tubing volume. I also had to find appropriate connectors, and way to be able to test and validate the setup. To do this, I connected another syringe to the system, so I could manually control the pressure myself and observe the system's response. I mathematically determined pressure as a function of syringe position given some assumptions about the system, and used that to test data. 

## performance characterisation
In order to make the setup easier to use, I integrated the setup with a python script that collected serial data from the micro controller. Using the pyserial library and matplotlib, I could effectively collect data from the setup and characterize it's performance, namely speed of ocnvergence.

## mechanical integration
To be able to interface this technology with the microscope, I designed alignment and manufacturing jigs in solidworks, and 3d printed them to make manufacturing simple.