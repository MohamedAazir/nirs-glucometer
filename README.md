# Aprick by Meditrones

This repository contains the source code and documentation for a NIR-based non-invasive glucometer, developed as part of the BM 1190 Engineering Design Project at the University of Moratuwa.

<img src="https://github.com/user-attachments/assets/0ce704d8-9f37-4909-bde7-e2de586f7ca9" alt="Aprick" width="400"/>

## Project Overview

The non-invasive glucometer provides a novel approach for diabetes patients by offering painless and continuous monitoring of blood glucose levels. The device uses a near-infrared LED and photodetector to measure blood glucose concentration based on the scattering and absorption of infrared light through the blood.

## Features

- **Non-Invasive**: No needle pricks required, reducing pain and discomfort.
- **Continuous Indicating**: Allows for regular glucose level checks without the need for invasive procedures.
- **User-Friendly**: Designed for ease of use with a simple interface and clear display.
- **Portable**: Compact and lightweight design, suitable for home use.

## Hardware Components

- **Microcontroller**: Atmega 328P-AU
- **Display**: OLED screen
- **IR LED**: 940nm wavelength
- **Photodetector**: CJ-MCU OPTO 101 module
- **Battery**: 3.7V 500mAh Lipo
- **Voltage Regulator**: 5V
- **Other Components**: SMD resistors, capacitors, JST connectors, and step-up booster.

## Software

The software for the microcontroller is written in C++, and it includes algorithms for processing sensor data, calibrating readings, and estimating blood glucose levels. The software focuses on accurate data processing, user-friendly interface, and reliable integration with the non-invasive sensor.

## PCB Design

The project includes custom-designed PCBs for both the main circuit and the transmitter. The PCBs were designed using [software used, if applicable] and fabricated using 3D printing technology with PLA+ material.

## Enclosure Design

The enclosure was designed using SolidWorks and printed using PLA+ and Black TPU for padding. It ensures a secure fit for the device components and provides a comfortable user experience.

## Problems Encountered and Solutions

- **Noise in Circuit**: Resolved by utilizing active filters.
- **IR Receiver Issues**: Switched to the CJ-MCU OPTO 101 module for better performance.
- **Programming Challenges**: Overcame issues with programming the Atmega 328P-AU using a TQFP-32 clamp shell.

## Contributors

- **Aazir M.M.M.**: Research, Circuit Development, Enclosure Design, Coding
- **Boralugoda M.S.**: Research, Documentation
- **Liyanage D.L.B.B.**: Circuit Development, Implementation, Documentation
- **Madusanka S.P.S.**: PCB Design, Circuit Implementation

