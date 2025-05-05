# Smart Weights – An IoT Security Project Report
**Date:** May 05, 2025  
**Authors:** William Turner, Veera Sumanth Uppala, Bertrand Bonny Byera  
**Course:** IoT Security, Spring 2024  
**University:** University of New Haven

---

## 📘 Abstract

MuscleMind Metrics is a smart gym equipment solution designed to enhance physical training by tracking repetitions, sets, rest intervals, and performance metrics using embedded sensors and Bluetooth-enabled communication. It incorporates key principles of IoT security to ensure the reliability, integrity, and privacy of fitness data.

---

## 🧠 Problem Statement

Most gym-goers lose track of repetitions and sets. According to studies, over 30% overestimate their physical activity. Traditional tracking is cumbersome and error-prone. Our goal was to build an **IoT-enabled dumbbell** that:
- Tracks reps and movement using accelerometers.
- Connects to smartphones using Bluetooth.
- Charges wirelessly.
- Implements robust security practices for safe use.

---

## 🏗️ Design & Implementation

### Core Functionalities
- **Motion Tracking:** Using accelerometer sensors.
- **Wireless Charging:** Dumbbells recharge via induction pads in the rack.
- **Bluetooth Communication:** Pairs with smartphones for real-time data transfer.
- **Mobile Integration:** App interface for viewing metrics.

### Sensors & Actuators
- **Sensors:** Accelerometer, Battery Level Sensor, Bluetooth Tx/Rx
- **Actuators:** LED power indicator, Power/Pairing Button

### Circuit Design Tools
- **TinkerCAD** – for digital prototyping and sensor simulation
- **ESP8266** – simulated Wi-Fi/Bluetooth module for communication
- **ThingSpeak** – for real-time data visualization
- **MATLAB** – for data analytics and anomaly detection

---

## 🔐 IoT Security Implementation

### Threat Modeling
Used **STRIDE** methodology:
- **S**poofing: QR-code-based pairing and authentication
- **T**ampering: Encased sensors; local processing only
