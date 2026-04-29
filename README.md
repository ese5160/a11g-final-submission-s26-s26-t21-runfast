[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Y5lYn2wb)

# a11g-final-submission

**Team Number:21**

**Team Name:RunFast**

| Team Member Name | Email Address           | GitHub Username |
| ---------------- | ----------------------- | --------------- |
| Muhammad Noman   | [Email 1]               | [Username 1]    |
| Deepa Lokesha    | deepasr1@seas.upenn.edu | DeepaLokesha    |

**GitHub Repository URL: https://github.com/ese5160/a11g-final-submission-s26-s26-t21-runfast.git**

## 1. Video Presentation

## 2. Project Summary

**Device Description:**
RunFast is an ankle-mounted IoT wearable that captures real-time biomechanical data — foot pressure via Force Sensitive Resistors (FSRs) and leg motion via a 6-axis IMU — to help runners monitor and correct their running form during a session. A buzzer provides immediate on-device audio feedback to mark key session events: it plays when a running session starts and again when it ends, keeping the runner informed without requiring them to glance at a screen. Performance metrics are transmitted over WiFi to a cloud-hosted Node-RED dashboard for remote visualization and logging.

Most runners have no way to know in real time when their running form is breaking down under fatigue. Standard fitness trackers record pace and distance but cannot tell you the moment your ground contact time spikes or your stride becomes asymmetric — the early warning signs of injury. RunFast solves this by placing pressure and motion sensing directly on the ankle, computing stride metrics at the edge, and alerting the runner with a buzzer the instant a session starts and ends — no phone, no screen, no coach required. The device transmits the full session data to a Node-RED dashboard so runners can review their biomechanical performance after the run.

The SiWG917 WiFi SoC connects to a Node-RED instance hosted on Microsoft Azure. Sensor readings (FSR pressure, IMU motion metrics, computed cadence, ground contact time) are published via MQTT and visualized on a live dashboard accessible from any browser. The internet connection also enables over-the-air firmware updates (OTAFU), so new features and bug fixes can be deployed to the wearable without physical access.

**Device Functionality:**
RunFast is built around the Silicon Labs SiWG917 wireless microcontroller, which integrates a WiFi radio and ARM Cortex-M4 core in a single module. Two Force Sensitive Resistors (FSRs) are connected to the MCU's ADC channels through an AD8606 dual op-amp signal conditioning circuit, providing conditioned analog readings of foot pressure. An LSM6DSVETR 6-axis IMU communicates via I2C and captures leg acceleration and angular velocity to segment each stride into stance and swing phases and detect motion smoothness. A buzzer serves as the primary user-facing actuator, signaling session start and end events so the runner stays informed without looking at a screen. Sensor data is transmitted over WiFi to a  Node-RED instance hosted on Microsoft Azure , where it is stored and visualized on a live dashboard. Power is provided by a single-cell LiPo battery, managed by a BQ24075 battery charger IC with a TPS62082 buck converter supplying 3.3V to the system, and charged via  USB-C .

![1777497584634](image/README/1777497584634.png)


## 3. Hardware & Software Requirements


## Hardware Requirements Specification (HRS)

| ID    | Requirement                                                                                                                            |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------- |
| HRS01 | The system shall consist of an ankle-mounted wearable module, worn on the leg.                                                         |
| HRS02 | The module shall be based on the SIWG917Y121MGABA MCU.                                                                                 |
| HRS03 | The module shall include at least one IMU to measure leg motion during running.                                                        |
| HRS04 | The module shall include pressure sensors positioned to detect foot-ground contact events and loading characteristics.                 |
| HRS05 | The pressure sensors shall be capable of detecting foot contact onset and release to enable measurement of stance and swing phases.    |
| HRS06 | The module shall include a buzzer to indicate system status, including session start and end.                                          |
| HRS07 | The system shall include a single-cell Li-ion battery (3.7V nominal) as the primary power source.                                      |
| HRS08 | The system shall include appropriate voltage regulation circuitry to supply stable operating voltages to the MCU, sensors, and buzzer. |

## Software Requirements Specification (SRS)

| ID    | Requirement                                                                                                                                             |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SRS01 | The system shall sample pressure sensor data at a sufficient rate to reliably detect foot contact start and end events.                                 |
| SRS02 | The system shall segment each stride into stance and swing phases using pressure sensor data.                                                           |
| SRS03 | The system shall compute ground contact time (GCT) for each stride with a timing resolution of at least 10 ms.                                          |
| SRS04 | The system shall compute cadence in real time based on consecutive foot contact events.                                                                 |
| SRS05 | The system shall use IMU data to estimate leg swing timing, peak motion intensity, and motion smoothness during the swing phase.                        |
| SRS06 | The system shall activate the buzzer to signal session start and session end events.                                                                    |
| SRS07 | The system shall enter a low-power sleep state when no motion is detected for more than 5 minutes.                                                      |
| SRS08 | All real-time sensing, stride analysis, and feedback generation shall execute locally on the device without requiring continuous internet connectivity. |
| SRS09 | The system shall transmit summary performance metrics to a remote dashboard via Wi-Fi for visualization and logging.                                    |

## 4. Project Photos & Screenshots

![1777499236202](image/README/1777499236202.png)

![1777499357557](image/README/1777499357557.png)

![1777499327848](image/README/1777499327848.png)

![1777499338920](image/README/1777499338920.png)

![1777499775634](image/README/1777499775634.png)

![1777499183955](image/README/1777499183955.png)

![1777499714460](image/README/1777499714460.png)

![1777499891860](image/README/1777499891860.png)

![1777499938742](image/README/1777499938742.png)


## 5. Codebase

Do *not* commit any of your source code to this repository. Rather, provide links to the other GitHub repository you've already been using with your firmware.

- A link to your final embedded C firmware codebases
- A link to your Node-RED dashboard code
- Links to any other software required for the functionality of your device
