# Project Overview

## 📌 Project Title:
**Dual-Barreled Fire Fighting Robot Using Arduino**

## 🧠 Project Idea:
This project addresses the risk faced by human firefighters by developing a **low-cost, autonomous firefighting robot prototype**. The robot is capable of **detecting and extinguishing fires automatically**, making it useful in hazardous environments where human intervention is unsafe or delayed.

The system combines **infrared flame sensors, motor control, and water pump actuation** to identify fire sources and respond swiftly. It is a multidisciplinary project incorporating elements of **mechanical design, electronics, embedded systems, and automation**.

---

## ⚙️ System Design and Architecture:

### 🔄 Mode of Operation:
- **Automatic Mode**: Robot detects fire using IR sensors and moves toward it to extinguish.
- **Manual Mode** (Optional/Scalable): Can be extended using RF or remote control for direct human operation.

### 🧱 Modules:

1. **Fire Detection (IR Sensors):**
   - Three infrared flame sensors placed at 180° for wide-angle detection.
   - Detect IR radiation emitted by fire and trigger response.

2. **Motion & Navigation:**
   - **L293D Motor Driver Module** to control DC motors and robot movement.
   - **Chassis with wheels** for mobility toward the fire source.

3. **Fire Suppression Mechanism:**
   - **Dual-barrel water pump system** increases water flow rate for faster extinguishing.
   - **Servo motor (SG90)** used to rotate the barrel toward fire direction.

4. **Microcontroller:**
   - **Arduino Uno** – central processing unit that reads sensor input, controls motors and actuators.

---

## 🔧 Technologies and Tools Used:

| Component            | Description                               |
|---------------------|-------------------------------------------|
| **Arduino Uno**     | Microcontroller for logic and control     |
| **IR Flame Sensors**| Fire detection via infrared radiation     |
| **L293D Motor Driver**| Controls motor direction and speed      |
| **SG90 Servo Motor**| Aims water barrel toward flame            |
| **Water Pump Motor**| Sprays water when fire is detected        |
| **Chassis & Wheels**| For robot mobility                        |
| **Power Supply**    | Battery/USB powered circuitry             |
| **Arduino IDE**     | Code written in C and uploaded to board   |

---

## 🔬 Deeper Understanding and Learning Outcome:
- **Sensor Calibration**: Learned to fine-tune IR sensor sensitivity for accurate fire detection.
- **Embedded Logic Design**: Implemented real-time condition-based triggers in Arduino C.
- **Motor Control and Actuation**: Integrated multiple motors using motor drivers and PWM.
- **Multi-sensor Fusion**: Combined data from multiple sensors to determine optimal direction.
- **Future Scope**: Integrate wireless communication (e.g., Zigbee or Bluetooth) for remote monitoring, use flameproof materials for hardware casing, and add thermal imaging for industrial use.

---

##  Conclusion:
This prototype demonstrates how **autonomous robotic systems** can assist in hazardous environments and form the basis for future scalable firefighting solutions using **IoT and AI**. It promotes safety, efficiency, and real-world problem solving with embedded systems.

