+++
draft = false
title = 'Multi-Phase Inverter'
showReadingTime = false
date =  2019-12-23
showDate = false
showTableOfContents = true
showSummary = true
summary = "Multi-phase inverter distributed control system for metal foundries application"
showAuthor = false
showPagination =  false
+++

# Multi-Phase Inverter

## Overview
This project involved developing a distributed control system for a multi-phase inverter used in metal foundries. The system was designed using two main FPGAs (one master and one slave) utilizing Intel (Altera) technology. The master controlled multiple slaves simultaneously through point-to-point optical links and interfaced with a PC that manages high-level parameters and overall operation.

## Key Features and Achievements
- **Distributed Control:** The system consists of a master FPGA and multiple slave FPGAs working in parallel.
- **Point-to-Point Optical Links:** The master manages communication with the slaves using point-to-point optical links.
- **Communication Protocol:**
  - Developed a communication protocol between the master and slaves over optical links with embedded clock.
  - The protocol uses a periodic transmission scheme with an auto-recovery feature.
- **Real-Time Data Channel:** Created a special channel on the optical link for real-time data flowing from the slaves to the PC.
- **PWM Signal Control:** Developed the control for PWM signals, including algorithms for frequency and duty cycle management.
- **Sensor Monitoring:** Implemented continuous sensor monitoring to ensure safe operation and fault detection.
- **Comprehensive Documentation:**
  - Produced detailed study and architecture documents that provided in-depth insights into the system design, protocols, and hardware specifications.
  - Comprehensive technical documentation was created for the development and integration of VHDL code, communication protocols, and control logic.

## Technical Details
- **Hardware:** Intel (Altera) FPGA, current and temperature sensors, control PC.
- **Development:**
  - Designed and implemented the **communication protocol** between master and slaves in **VHDL**.
  - Developed the **PWM control logic** and **sensor reading systems** in **VHDL** to ensure accurate, real-time control of the inverter system.
  - Managed communication via point-to-point optical links to ensure low latency and high reliability.
  - Created a dedicated **real-time data channel** to transmit critical data between the slaves and the control PC.
- **Technologies Used:**
  - Intel (Altera) FPGA for control and communication management.
  - **VHDL** for the development of control logic, communication protocols, and sensor integration.
  - Sensor technologies for current and temperature monitoring.
- **PWM Control:** Advanced algorithms for controlling PWM frequencies, ensuring safe operation and fault detection.

## Challenges and Solutions
- **Communication Reliability:** Optimized the optical point-to-point transmission to ensure reliable communication in harsh industrial environments.
- **Synchronization:** Managed synchronization between the master and slaves to control multiple inverters simultaneously.
- **Error Recovery:** Implemented an auto-recovery mechanism for communication between the master and slaves in case of packet loss or link failure.

## Outcome
The system delivered precise and safe control of multi-phase inverters, ensuring optimal operation in metal foundries. With optical communication and an advanced protocol developed entirely in **VHDL**, the system maintained high operational reliability even in demanding conditions, with continuous monitoring and fault detection.
Additionally, all relevant **study architecture** and **detailed documentation** were produced, providing clear and comprehensive insights into the system design and operation.

---
