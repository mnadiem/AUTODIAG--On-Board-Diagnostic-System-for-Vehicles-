# AUTODIAG — On-Board Diagnostic System for Vehicles

**AUTODIAG** is an academic embedded-systems and IoT project exploring remote vehicle monitoring and diagnostics. It combines an STM32 microcontroller, an ESP8266 Wi-Fi gateway, and MQTT-based communication to transmit vehicle sensor data and Diagnostic Trouble Codes (DTCs) for remote monitoring.

> **Project context:** This repository documents a prototype and its design. It is not a certified automotive diagnostic or safety system.

## Project Goals

The system was designed around four service areas:

- **Real-time monitoring** of incoming vehicle subsystem data
- **On-board diagnostics** through Diagnostic Trouble Code (DTC) processing
- **Remaining Useful Life (RUL) estimation** for selected subsystems
- **Roadside assistance** supported by diagnostic information

## System Architecture

The prototype uses a layered embedded architecture. In the documented data path, a Python script streams sample sensor data through a PL2303 USB-to-UART bridge to the STM32F103C8T6. The STM32 processes the data and communicates with an ESP8266 gateway over SPI. The ESP8266 publishes information over Wi-Fi using MQTT.

```mermaid
flowchart LR
    A[Python sensor-data stream] -->|USB / UART via PL2303| B[STM32F103C8T6]
    B -->|SPI| C[ESP8266 NodeMCU]
    C -->|Wi-Fi / MQTT| D[MQTT Broker]
    D --> E[Backend and database]
    E --> F[Remote monitoring interface]
```

## Hardware

| Component | Purpose |
|---|---|
| **STM32F103C8T6** | Main embedded controller for data handling and diagnostic processing |
| **ESP8266 NodeMCU** | Wi-Fi connectivity and MQTT gateway |
| **PL2303 USB-to-UART bridge** | Serial connection for feeding sample data to the STM32 |
| **ST-LINK** | Programming and debugging the STM32 |

## Embedded Software and Communication

- **C / STM32 firmware:** peripheral configuration and embedded data handling
- **RTOS:** task-based execution for system functions
- **UART:** serial input from the PL2303 bridge
- **SPI:** communication between the STM32 and ESP8266
- **MQTT:** lightweight publish/subscribe messaging between the ESP8266 and broker

## Technology Stack

- **Microcontroller:** STM32F103C8T6 (ARM Cortex-M3)
- **Wireless module:** ESP8266 NodeMCU
- **Protocols:** UART, SPI, MQTT
- **Development tools:** STM32CubeIDE, Arduino IDE, ST-LINK Utility
- **Connectivity:** Wi-Fi and HiveMQ MQTT broker

## Project Materials

- [Project presentation](https://drive.google.com/file/d/12X-7KyyK5NAQu-tFUbDE7he6bxcZAbdy/view?usp=sharing)
- [Published research paper — Springer AISI 2025](https://doi.org/10.1007/978-3-031-81308-5_19)

## Notes

AUTODIAG was developed as a university graduation project. The architecture and capabilities described here represent the project prototype and its intended services; implementation details and results should be interpreted in that academic-project context.
