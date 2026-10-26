<!-- AUTODIAG project README -->

<div align="center">

# AUTODIAG
### Remote Vehicle Diagnostics · Embedded Systems · IoT

**An embedded prototype for vehicle data monitoring and diagnostic information over Wi-Fi and MQTT.**

<p>
  <a href="https://doi.org/10.1007/978-3-031-81308-5_19"><img src="https://img.shields.io/badge/Research-Springer%20AISI%202025-1769aa?style=for-the-badge&logo=springer" alt="Springer AISI 2025 paper"></a>
  <img src="https://img.shields.io/badge/MCU-STM32F103C8T6-03234B?style=for-the-badge" alt="STM32F103C8T6">
  <img src="https://img.shields.io/badge/Wireless-ESP8266-E7352C?style=for-the-badge" alt="ESP8266">
  <img src="https://img.shields.io/badge/Protocol-MQTT-660066?style=for-the-badge" alt="MQTT">
</p>

[Project Presentation](https://drive.google.com/file/d/12X-7KyyK5NAQu-tFUbDE7he6bxcZAbdy/view?usp=sharing) · [Published Research Paper](https://doi.org/10.1007/978-3-031-81308-5_19)

</div>

---

## 👀 Project at a Glance

AUTODIAG is an academic embedded-systems and IoT project exploring remote vehicle monitoring and diagnostics. It combines an **STM32 microcontroller**, an **ESP8266 Wi-Fi gateway**, and **MQTT messaging** to transfer sensor data and Diagnostic Trouble Codes (DTCs) for remote monitoring.

<div align="center">
  <img src="STM.png" alt="STM32 controller used in the AUTODIAG project" width="42%">
  &nbsp;&nbsp;
  <img src="esp.png" alt="ESP8266 module used as the wireless gateway" width="42%">
</div>

> **Project status:** Academic prototype. It is not a certified automotive diagnostic or safety system.

## ✨ Core Goals

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>📊 Real-Time Monitoring</h3>
      Process incoming vehicle subsystem data for remote observation.
    </td>
    <td width="50%" valign="top">
      <h3>🔎 On-Board Diagnostics</h3>
      Process diagnostic information and Diagnostic Trouble Codes (DTCs).
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>🤖 Remaining Useful Life</h3>
      Explore RUL estimation for selected vehicle subsystems.
    </td>
    <td width="50%" valign="top">
      <h3>🛠️ Roadside Assistance</h3>
      Use diagnostic information to support assistance workflows.
    </td>
  </tr>
</table>

## 🧩 System Architecture

The documented data path starts with a Python script streaming sample sensor data through a **PL2303 USB-to-UART bridge** to the **STM32F103C8T6**. The STM32 processes the data and communicates with the **ESP8266** over SPI. The ESP8266 then publishes information over Wi-Fi using MQTT.

<div align="center">
  <img src="https://mermaid.ink/img/pako:eNqNkE1PwzAMhv9KlBMn7Q8Q4k1cOHAwMZg0m7Rpa1q7pE1t1k5q1b_vJpA0m0t2vOe9fJxwQqk0gJx0qk7J2kYQ1o6b7s9qQ6V8w2q0d1aQ8m5q8Q5o3m0v2sQ0p4xk7b2m8Q1j2h7YQ6n9j7JQ4v4G2b1jQ6s4cQ" alt="AUTODIAG data flow from Python sensor stream to remote monitoring" width="100%">
</div>

```mermaid
flowchart LR
    A["Python sensor-data stream"] -->|"USB / UART · PL2303"| B["STM32F103C8T6"]
    B -->|"SPI"| C["ESP8266 NodeMCU"]
    C -->|"Wi-Fi / MQTT"| D["MQTT Broker"]
    D --> E["Backend & Database"]
    E --> F["Remote Monitoring Interface"]

    classDef mcu fill:#123B5D,color:#fff,stroke:#4EA5D9,stroke-width:2px
    classDef network fill:#4C276A,color:#fff,stroke:#B794F4,stroke-width:2px
    class B mcu
    class C,D,E,F network
```

## 🔌 Hardware

| Component | Role in the prototype |
|---|---|
| **STM32F103C8T6** | Main controller for data handling and diagnostic processing |
| **ESP8266 NodeMCU** | Wi-Fi connectivity and MQTT gateway |
| **PL2303 USB-to-UART bridge** | Serial input for sample data |
| **ST-LINK** | STM32 programming and debugging |

### Hardware Reference

<div align="center">
  <img src="PL2303%20USB%20to%20Serial_page9_image.png" alt="PL2303 USB-to-serial adapter reference" width="34%">
</div>

## 🖥️ Project Screenshots

<div align="center">
  <img src="Screenshot%202024-05-15%20141221.png" alt="AUTODIAG project screenshot 1" width="48%">
  <img src="Screenshot%202024-05-15%20141234.png" alt="AUTODIAG project screenshot 2" width="48%">
  <img src="Screenshot%202024-05-15%20141319.png" alt="AUTODIAG project screenshot 3" width="48%">
  <img src="Screenshot%202024-05-15%20141613.png" alt="AUTODIAG project screenshot 4" width="48%">
</div>

## ⚙️ Embedded Software & Communication

- **C / STM32 firmware** — peripheral configuration and embedded data handling
- **RTOS** — task-based execution for system functions
- **UART** — serial input from the PL2303 bridge
- **SPI** — communication between the STM32 and ESP8266
- **MQTT** — publish/subscribe messaging between the ESP8266 and broker

## 🧰 Technology Stack

<p>
  <img src="https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white" alt="C">
  <img src="https://img.shields.io/badge/STM32-03234B?style=flat-square" alt="STM32">
  <img src="https://img.shields.io/badge/FreeRTOS-6DB33F?style=flat-square" alt="RTOS">
  <img src="https://img.shields.io/badge/ESP8266-E7352C?style=flat-square" alt="ESP8266">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/MQTT-660066?style=flat-square" alt="MQTT">
  <img src="https://img.shields.io/badge/UART%20%7C%20SPI-555555?style=flat-square" alt="UART and SPI">
</p>

- **MCU:** STM32F103C8T6 (ARM Cortex-M3)
- **Wireless module:** ESP8266 NodeMCU
- **Development tools:** STM32CubeIDE, Arduino IDE, ST-LINK Utility
- **Connectivity:** Wi-Fi and an MQTT broker

## 📚 Project Materials

- 🎥 [Project presentation](https://drive.google.com/file/d/12X-7KyyK5NAQu-tFUbDE7he6bxcZAbdy/view?usp=sharing)
- 📄 [Published research paper — Springer AISI 2025](https://doi.org/10.1007/978-3-031-81308-5_19)

---

<div align="center">

**AUTODIAG** · University Graduation Project

<sub>The architecture and capabilities described here reflect the academic prototype and its intended services.</sub>

</div>
