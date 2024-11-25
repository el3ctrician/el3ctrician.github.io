+++
draft = false
title = 'Particle accelerator'
showReadingTime = false
date =  2019-03-15
showDate = false
showTableOfContents = true
showSummary = true
summary = "Control System for Particle Accelerator Used in Cancer Treatment"
showAuthor = false
showPagination =  false
+++


# Control System for Particle Accelerator Used in Cancer Treatment

## Overview
This project focused on upgrading the control system of an existing particle accelerator used in cancer treatment. The core development involved creating a new communication protocol to efficiently distribute data over optical links connected to a master. The system also allowed a National Instruments (NI) device on a backplane to retrieve data collected from the slaves via the master using PCI.

## Key Features and Achievements
- **Advanced Communication Protocol:**
  - Designed and implemented a new protocol for distributing data between the master and multiple slaves via optical links.
  - Enabled data retrieval by a National Instruments device connected through PCI on the backplane.
- **Protocol Features:**
  - Added special fields for specific event handling.
  - Integrated a priority-based system for handling critical data transmission.
  - Embedded clock signal within the data stream to simplify synchronization.
  - Utilized **8b/10b encoding** for reliable data transmission and **error correction codes** for enhanced fault tolerance.
- **Synchronization:**
  - Developed a synchronization mechanism between the master and slaves using a **digital controlled oscillator (DCO)** and a **second-order phase-locked loop (PLL)** on the master FPGA.
- **System Design Enhancements:**
  - Supported the distribution and collection of real-time data required for the precise control of the particle accelerator.
  - Optimized performance and reliability for use in a medical application, where accuracy and safety are paramount.

## Technical Details
- **Hardware:**
  - Xilinx FPGAs for the master and slave devices.
  - Optical links for communication between the master and slave devices.
  - National Instruments device on the backplane for data retrieval via PCI.
- **Protocol Development:**
  - Embedded clocking mechanism to ensure synchronization over the optical links.
  - Implemented **8b/10b encoding** to improve signal integrity.
  - Incorporated error correction code (ECC) to detect and correct transmission errors.
  - Developed custom fields for handling special events and a priority system for critical data.
- **Synchronization Mechanism:**
  - Control of a **digital controlled oscillator (DCO)** on the master FPGA board for synchronization.
  - Achieved precise clock alignment using a **second-order PLL**, ensuring smooth operation and communication reliability.
- **Technologies Used:**
  - VHDL for designing the protocol logic and data handling systems.
  - PCI bus for interfacing the master with the National Instruments device.

## Challenges and Solutions
- **Data Synchronization:** Used a **digital controlled oscillator** with a **second-order PLL** on the master FPGA board to maintain precise timing with the slaves.
- **Error Resilience:** Used **8b/10b encoding** and ECC to enhance data reliability and clock recovery.
- **Priority Handling:** Designed a priority-based system to manage the transmission of critical data efficiently without delays.
- **Real-Time Data Retrieval:** Integrated PCI communication for fast and reliable data access by the National Instruments device.

## Outcome
The new communication protocol enhanced the control system of the particle accelerator, enabling precise and reliable operation crucial for cancer treatment applications. By incorporating advanced features like embedded clocking, error correction, and priority handling, as well as synchronization via a **digital controlled oscillator** and **second-order PLL**, the system achieved high reliability and performance, meeting stringent medical standards.

---

