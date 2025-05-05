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
- **R**epudiation: Data hashed before transmission
- **I**nformation Disclosure: Bluetooth encryption
- **D**enial of Service: Packet validation logic
- **E**levation of Privilege: No remote admin capability

### Secure Data Transmission
- **Bluetooth-based encryption & authentication**
- **No internet exposure** (local data only)
- Option for cloud backup via iCloud or Google (user-controlled)

### Data Integrity & Anomaly Detection
- Detected outliers using **moving median** and **percentile filtering**
- Simulated 10% packet drops and 30s noise every 5 mins
- Firmware logic to validate and discard data outside range

---

## 📊 Data Visualization & Results

- **ThingSpeak** charts visualized X, Y, Z axis movements
- Outliers with values like `187`, `420`, `423` flagged as abnormal
- Recommended:
  - High/Low thresholds for sensor validation
  - Firmware-level input sanitization
- Detected sensor anomalies led to proposal of **hardware validation flags**

---

## 📱 User Interaction

- Dumbbells pair with smartphone via **QR Code + Bluetooth**
- Accelerometer triggers motion tracking
- LED indicates battery level
- Application dashboard shows:
  - Reps/Sets
  - Calories burned
  - Weight lifted
  - Real-time session logs

---

## 📦 Future Enhancements

- Add **gyroscope** for better angle tracking
- Integrate **biometric sensors** (e.g. pulse)
- Introduce **gesture recognition**
- Improve Bluetooth range and security
- Develop full mobile app with cloud sync option

---

## 🛡️ Final Conclusion

This project proved that secure, reliable IoT-based fitness tracking is feasible even in hardware-constrained environments. By applying encryption, STRIDE, and anomaly detection, we addressed key security and reliability concerns. The Smart Weight System merges usability and cybersecurity, showcasing best practices in embedded IoT design.

---

## 📚 References
- OWASP IoT Top 10
- STRIDE Threat Modeling by Microsoft
- Future Market Insights: Smart Fitness Forecast
- CDC & Medline: Exercise Statistics
- TinkerCAD, MATLAB, ThingSpeak Documentation
