# RC Controller

![Ubuntu](https://img.shields.io/badge/OS-Ubuntu_22.04_LTS-E95420.svg)
![STM32CubeMX](https://img.shields.io/badge/STM32CubeMX-v6.15.0-C80000.svg)
![MCU](https://img.shields.io/badge/MCU-STM32F4-006699.svg)
![CLion Version](https://img.shields.io/badge/CLion-2025.2.4-007ACC.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)


This repository contains the configurations for STM32CubeMX, schematics and firmware source code for a custom 
RC controller built around the **STM32F4VE** development board (MCU STM32F407VET6, Cortex-M4). <br>
The controller is designed to communicate via radio-frequency with systems such as the 
[Teensy Flight Controller](https://github.com/jmend3s/flight-controller), providing a reliable, extensible and open
platform for remote control and telemetry exchange.

---
### Project Objectives

This project aims to develop a full-featured modular radio controller with the following goals:

- **Expandable and modular design** — Support new modules through a unified API.
- **Full STM32 ecosystem integration** — Generate initialization code with STM32CubeMX and extend it through a C++ HAL wrapper.
- **Standardized wireless communication** — Implement flexible protocols for broad compatibility.
- **User interface system** — Build a menu/UI framework for the display and input controls.
- **Cross-platform firmware base** — Keep architecture portable for other MCU's.

---
### Firmware Architecture

```
+-----------------------------+
| Application Layer           |
| - Menu / UI System          |
| - Control                   |
| - Telemetry                 |
+-----------------------------+
| Middleware Layer            |
| - Communication             |
| - Input System              |
| - Display Interface         |
+-----------------------------+
| Hardware Abstraction Layer  |
| - GPIO, SPI, I²C, ADC       |
+-----------------------------+
| STM32 HAL                   |
+-----------------------------+
```

---
### Project Structure

```
cad/                # Files for cad model design
printables/         # Printable parts
docs/               # Diagrams and documentation
rc_controller/      # Source code and drivers
├── cmake/          # Cmake files for tools/features integration
├── Core/
│   ├── Inc/        # STM32CubeMX generated includes
│   └── Src/        # STM32CubeMX generated source files and main.c
├── drivers/        # STM32CubeMX generated drivers
└── CMakeLists.txt
```
---
### Current Status

**Software**
- [x] STM32 environment setup  
- [x] Clock configuration  
- [x] First program flashed successfully  
- [ ] C++ HAL wrapper  
- [ ] Button driver  
- [ ] Display interface (I²C LCD)  
- [ ] Menu/UI system  
- [ ] Wireless communication layer (NRF24L01)  

**Hardware**
- [ ] Electrical schematics  
- [ ] First physical prototype

**CAD Design**
- [ ] V 1.0.0  

---
### Hardware <br>

- **Microcontroller:** STM32F407VET6 (Cortex-M4, 168 MHz) 
- **Transceiver:** NRF24L01-PA + LNA (SPI)
- **Screen:** GM12864-59N LCD (I2C)
- **Inputs:**
  - Rotary encoder with push button
  - Mechanical keyboard high profile buttons × 2  
  - SPST switches × 2
- **Power:** LiPo 2S 1500 mAh  
- **Enclosure:** Custom 3D-printed shell
