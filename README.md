# Lab 4: Power-Efficient Acoustic Monitoring 

> This manual is subject to change.

## Overview
This lab builds upon the Keyword Spotting system from Lab 3, shifting focus toward **energy efficiency** and **wireless communication**. Students will optimize their models through pruning, implement aggressive power-management strategies, and profile the physical energy consumption of the ESP32-S3.

---

## Task Setup

### 1. Model Compression: Structured Pruning
Students will apply **structured pruning** to their existing Lab 3 models. This process removes redundant parameters or entire channels within the Neural Network, providing a quantifiable reduction in memory footprint and computational overhead beyond standard quantization.

### 2. Interrupt-Driven Deep Sleep
To minimize idle power draw, students will implement a duty-cycled power scheme:
* **Sleep Cycle:** The ESP32 enters **Deep Sleep**, powered down except for the Real-Time Clock (RTC).
* **Wake Trigger:** The RTC Timer wakes the device at set intervals (e.g., every 30 seconds).
* **Task:** The system performs a single, minimal-latency audio inference and immediately returns to sleep.

### 3. BLE 5.0 Integration
Upon detecting the target keyword, the ESP32-S3 will use **BLE 5.0 advertising** to transmit the classification result. Students will verify the transmission using a mobile application (such as nRF Connect or a custom dashboard).

### 4. Physical Power Profiling
Students will perform hands-on measurements to calculate the total **Energy ($Joules$)** consumed per cycle:
* **Idle Current:** Measure current draw in Deep Sleep vs. Active Idle.
* **Active Cycle:** Measure the "Wake → Sense → Classify" power profile.
* **Transmission:** Measure the specific power spike during the BLE Transmission Phase.
* **Analysis:** Use a multimeter or power profiler to capture raw data and compare the efficiency of different software configurations.

---

## Learning Objectives
* **NN Optimization:** Master Neural Network Pruning techniques to reduce model complexity.
* **Ultra-Low Power Design:** Implement and manage Deep Sleep states and RTC wake-up timers.
* **Power Profiling:** Develop critical skills for measuring and calculating physical energy consumption in embedded systems.
* **Wireless Protocols:** Understand the fundamentals of BLE 5.0 advertising and data transmission.
