# Autonomous Drone for Intelligent Navigation

## Objective
The goal of this project is to design and implement a **fully autonomous drone** capable of flying from an origin to a destination **without human control**, while intelligently **avoiding obstacles**, adapting to **environmental conditions** (such as wind, GPS drift, or limited visibility), and making **AI-based flight decisions** in real time.

This project integrates **sensor fusion**, **computer vision**, and **PWM-based control** through a companion computer to achieve safe, efficient, and intelligent flight performance.

---

## System Overview

### Core Concept  
To create a drone that can **perceive**, **plan**, and **act** on its own — continuously interpreting its surroundings, predicting potential collisions, and dynamically adjusting its flight path to maintain stability and safety.

| **Subsystem** | **Description** |
|----------------|-----------------|
| **Flight Controller** | Cube Orange+ / Pixhawk 6X running ArduPilot or PX4 firmware for low-level stabilization and motor control |
| **Companion Computer** | NVIDIA Jetson Orin NX handling perception, SLAM, object detection, and path planning |
| **Sensors** | GPS, IMU, TF Luna LiDAR, barometer, ultrasonic sensors, and camera modules for navigation and obstacle avoidance |
| **Communication** | MAVLink telemetry over UART connecting the Jetson to the flight controller |
| **Power System** | 4S LiPo battery with LM2596 step-down converter supplying stable power to all onboard components |

---

## Control Logic

- All analog input signals (e.g., sensor readings or trigger inputs) are represented using **PWM (Pulse Width Modulation)** for unified processing.  
- PWM is used for:  
  - **Motor control** through ESCs  
  - **Sensor signal emulation** for analog interfacing  
- **Failsafe Logic:**  
  - Automatic *Return-to-Home (RTH)* or hover behavior on signal loss or low-battery detection  

---

## Development Phases

| **Phase** | **Goal / Deliverable** |
|------------|------------------------|
| **1. Research & Design** | Finalize system architecture, select flight controller, companion computer, and sensors |
| **2. Hardware Assembly** | Mount frame, motors, ESCs, Pixhawk, and Jetson; integrate power distribution and verify PWM output |
| **3. Firmware & Software Setup** | Flash ArduPilot/PX4, configure Mission Planner or QGroundControl, and establish Jetson–Pixhawk MAVROS communication |
| **4. Sensor Calibration & Testing** | Calibrate IMU, GPS, LiDAR, barometer, and camera modules; validate indoor stability |
| **5. AI Navigation Algorithm** | Implement SLAM, object detection, and path-planning logic on Jetson for autonomous navigation |
| **6. Field Testing & Evaluation** | Perform outdoor test flights, record telemetry, analyze obstacle-avoidance accuracy and failsafe response |
| **7. Documentation & Presentation** | Deliver final report, architecture diagram, and live flight demonstration |

---

## System Design Summary

```text
[ LiDAR / Camera / GPS / IMU ]
             ↓
     Sensor Fusion + AI (Jetson)
             ↓ MAVLink UART
     Flight Controller (Pixhawk)
             ↓ PWM Output
        ESCs → Motors → Thrust


---

##** Expected Outcomes**

- Fully autonomous drone capable of stable, intelligent, and obstacle-aware flight
- Effective sensor fusion integrating LiDAR, GPS, IMU, and visual inputs
- Real-time AI navigation adaptable to varying environmental conditions
- A reproducible open-source framework for future academic and research expansion

---

##** Folder OverView**

src/                → Core source code (AI, flight, sensors, utilities)
config/             → YAML configuration files (ports, PID, AI, calibration)
simulation/         → SITL or Gazebo scripts for software-in-the-loop testing
backend/            → Flask/FastAPI dashboard for telemetry visualization
notebooks/          → Model training, data analysis, and visualization notebooks
docs/               → Architecture diagrams and detailed documentation
data/               → Image datasets, flight logs, and telemetry data


---
<table>
  <tr><th>Category</th><th>Functionality</th></tr>
  <tr><td><b>Control</b></td><td>Stabilization (PID), takeoff, hover, landing</td></tr>
  <tr><td><b>Perception</b></td><td>IMU, GPS, LiDAR, camera</td></tr>
  <tr><td><b>Decision</b></td><td>AI logic for movement and avoidance</td></tr>
  <tr><td><b>Navigation</b></td><td>Path planning, mapping, auto return</td></tr>
  <tr><td><b>Safety</b></td><td>Emergency landing, low battery handling</td></tr>
  <tr><td><b>Communication</b></td><td>Optional telemetry/logging to laptop</td></tr>
  <tr><td><b>Autonomy</b></td><td>Fully self-driven, no manual RC control</td></tr>
</table>
-----

##** Future Vision**

- Integration of reinforcement learning for adaptive decision-making
- Advanced multi-sensor fusion (stereo vision + LiDAR + ultrasonic)
- Research on AI-based path optimization and flight efficiency
- Publish an open-source research framework for educational and academic collaboration Contributors

---

##** Contributors**

Name	                        Affiliation / Role

**Bavani Karthikeyan Janaki **  Long Island University, Brooklyn — Hardware & System Design
**Saicharan Boda**	            Long Island University, Brooklyn — Flight Control & Testing
**Sunil Ganta	**                Long Island University, Brooklyn — AI & Systems Integration (Recent Graduate)

Supervising Professor:      **Dr. Kewei Li**, Associate Professor of Computer Science — Project Advisor
