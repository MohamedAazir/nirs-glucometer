# Aprick by Meditrones
<p align="center">
<img src="https://github.com/user-attachments/assets/82aeb303-5646-4cde-ac7d-a9fd6fe43cf6" alt="Aprick" width="400"/>
</p>
In our 2nd semester, for the module BM 1190 Engineering Design Project we came up  with an idea for building a Non - Invasive Bloodglucometer using NIR. So, this repository contains the whole work related to our project. The content includes, 

- [Problem Statement](#problem-statement)
- [Our Solution](#our-solution)
- [Technical Architecture](#technical-architecture)
- [PCB Design](#pcb-design)
- [Enclosure Design](#enclosure-design)
- [Problems Encountered and Solutions](#problems-encountered-and-solutions)

## Problem Statement
Diabetes is a chronic metabolic disorder that occurs when the body either does not produce enough insulin or cannot effectively use the insulin it produces. Without proper insulin function, glucose builds up in the bloodstream, leading to high blood sugar levels (hyperglycemia), which can cause serious health complications.
Diabetes management requires frequent blood glucose monitoring, typically done using **finger-prick glucometers**. However, this traditional method presents several challenges:  
- **Pain & Discomfort**: Repeated pricking can be painful, discouraging frequent monitoring.  
- **Risk of Infection**: Regular use of lancets increases the chance of **skin infections** and irritation.  
- **Disease Transmission**: Sharing glucometers without proper sanitization can spread **bloodborne diseases** such as Hepatitis and STDs.  
- **Needle Phobia**: Individuals with a fear of needles often avoid testing, leading to **poor glucose regulation**.  

These challenges highlight the **need for a non-invasive, pain-free, and user-friendly alternative** that ensures continuous glucose monitoring without compromising accuracy.  

## Our Solution  
As a solution for this issue We proposed a solution of developing a **NIR Based Non-Invasive Glucometer** that allows diabetes patients to check their glucose levels **without drawing blood**.  

### Key Features of the Device
- **Non Invasive**: No need of pricking again. The device functionality is totally non invasive and painless.
- **Real-time monitoring**: The device provides real-time values of the blood glucose levels.
- **User friendly**: Simple finger placement mechanism for hassle-free use. OLED display for clear and easy-to-read results.
- **Portable**: Compact, lightweight design for easy carrying.

## Technical Architecture
The technical perspective of our device comprises of **four main parts**:

### 1. Signal Transmission & Reception  
<p align="center">
  <img src="https://github.com/user-attachments/assets/a7818d9c-d757-463e-8829-5899ceedd731" alt="Description" width="300">

</p>
The process begins when an near-infrared (NIR) beam is emitted by an IR LED with a wavelength of 940 nm. As the infrared light passes through the skin and tissue, it interacts with the biological components in the finger, primarily the blood. Specifically, the near-infrared light is absorbed by glucose molecules present in the blood. The absorption of light by these molecules causes a reduction in the intensity of the transmitted light. The remaining light is then detected by a photodetector, which is the CJ-MCU OPTO 101 module, which is sensitive to the intensity of the incoming light. This photodetector generates a corresponding voltage signal based on the amount of light it receives, which varies depending on the concentration of glucose in the blood. This voltage signal is then sent to the processing unit for further analysis. 

### 2️. Signal Processing & Analysis  

<p align="center">
  <img src="https://github.com/user-attachments/assets/5549b346-5b50-432a-abe3-797fd9725d6b" alt="Description" width="700">

</p>
The received signal first passes through a passive high-pass filter. The purpose of this filter is to eliminate any DC offset present in the signal, ensuring that only the variations in the signal, such as the fluctuations caused by glucose absorption, remain. This step is crucial because DC offsets can distort the signal, leading to inaccurate measurements.

Next, the signal is passed through a first-order active low-pass filter. This filter is designed to remove unwanted high-frequency noise that may be present in the signal. High-frequency noise, which can originate from various sources such as electrical interference or environmental factors, can obscure the desired signal and affect the accuracy of the measurement. The active filter helps to preserve the low-frequency components of the signal, which are more relevant for detecting glucose levels, while attenuating the higher-frequency noise.

After the signal has been filtered, it is then sent to an amplifier. The amplifier increases the amplitude of the signal, making it more suitable for further processing or analysis. This amplification ensures that the signal is strong enough to be accurately interpreted by subsequent stages of the system.

### 3️. Glucose Level Calculation & Display  
Finally, after the signal has been amplified and processed, it is sent to a pre-trained Linear Regression model. This model has been trained on a dataset that correlates voltage signals with known blood glucose levels, enabling it to make predictions based on the processed signal. The model applies the learned relationship between the voltage variations and glucose concentrations, using the input voltage signal to calculate the blood glucose level in real-time. Once the model processes the signal, the estimated blood glucose level is displayed on an OLED screen in milligrams per deciliter (mg/dL), which is the standard unit for measuring blood sugar levels.

### 4️. Power Supply System  
The device is powered by a 3.7V 500mAh LiPo battery, chosen for its lightweight and high energy density, ideal for portable use. A booster module increases the battery voltage to 12V. This 12V is then regulated down to 5V using a voltage regulator, which powers the microcontroller, amplifier, filters, and OLED display. The voltage regulation ensures stable operation and protects sensitive components from voltage fluctuations, allowing the device to run efficiently while optimizing battery life.  

## Firmware

The firmware for the microcontroller is written in C++ using the Arduino IDE. It handles the calculation of blood glucose values by applying the pre-trained Linear Regression model to the processed voltage signal. The firmware also manages displaying the glucose levels on the OLED screen in real-time and updates the display with the current value in mg/dL. Additionally, it indicates the status of the device, at which stage the process currently lies on.

<p align="center">
 ![PlatformIO IDE](https://platformio.gallerycdn.vsassets.io/extensions/platformio/platformio-ide/3.3.4/1736607344047/Microsoft.VisualStudio.Services.Icons.Default)


</p>

## PCB Design

To accomplish the tasks in our project, we designed two PCBs: the emitter LED PCB and the main PCB. The emitter PCB is a single-layer design, optimized for simplicity and functionality. The main PCB, on the other hand, is a more complex two-layer design, allowing for better routing and integration of components. Both PCBs were designed using Altium, a professional PCB design software, to ensure precision and reliability in the layout. Once the design was complete, the PCBs were printed and manufactured by JLCPCB, a trusted provider of high-quality PCB fabrication services.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7c9484c6-b1c7-4147-905e-7d98b535c79a" alt="Description" width="800">

</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5d01a63e-879a-4db5-9c9b-a6fd21126861" alt="Description" width="800">

</p>

## Enclosure Design
The enclosure of our device is inspired by the general structure of a pulse oximeter, ensuring a compact, ergonomic, and user-friendly design for comfortable handheld use. It consists of four main parts: the top lid, top compartment, bottom compartment, and bottom lid. These sections are carefully designed to securely house the internal components while providing ease of access for assembly and maintenance.

For increased accuracy, enhanced comfort and stability, we have used black TPU (Thermoplastic Polyurethane) material for the padding where the user inserts their finger. TPU is chosen for its flexibility, durability, and soft texture, ensuring a snug fit while minimizing discomfort during measurements. The rest of the enclosure is 3D-printed using PLA.
<p align="center">
  <img src="https://github.com/user-attachments/assets/40842173-0160-4b70-96f6-9f55cc9e9f99" alt="Description" width="800">

</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/73dc1e88-d429-4478-a23c-d63622027ed5" alt="Description" width="800">

</p>


## Problems Encountered and Solutions

- **Noise in Circuit**: Resolved by utilizing active filters.
- **IR Receiver Issues**: Switched to the CJ-MCU OPTO 101 module hoping for better performance. But didn't provide accurate results as expected
- **Ethical Issues**: encountered an ethical issue of getting a large enough dataset to train the linear regression model.

## Our Team

- **Aazir M.A.M.**
- **Boralugoda M.S.**
- **Liyanage D.L.B.B.**
- **Madusanka S.P.S.**

</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/843a2f54-bb96-4a4e-b7a6-72ebf269a8da" alt="Description" width="400">

</p>
