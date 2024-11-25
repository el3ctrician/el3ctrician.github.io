+++
draft = false
showReadingTime = false
showDate = false
showTableOfContents = true
title = 'Industrial Camera'
showSummary = true
summary = "Dual sensor industrial camera used in product inspection for quality control"
date = 2021-02-23
showAuthor = false
showPagination =  false
+++

# Industrial Camera for Product Inspection

## Overview
This project involved designing an industrial camera system for product inspection, utilizing a dual-sensor setup for enhanced optical zoom capabilities. The system was built around a Xilinx FPGA and featured advanced image processing, enabling high-performance frame acquisition and manipulation.

## Key Features and Achievements
- **Dual-Sensor Setup:** Integrated two identical Sony sensors with different lenses to achieve optical zoom functionality.
- **Advanced Image Processing Pipeline:**
  - Frame acquisition from the Sony sensor.
  - Debayering, white balance adjustment, and vignette removal.
  - Image zooming and cropping for customized output.
- **High-Speed Sensor Interface:**
  - Operated at the maximum bus speed of the device's speed grade.
  - Implemented dynamic phase alignment (DPA) to ensure reliable communication.
- **AXI-Based Architecture:**
  - Utilized an AXI bus for video data handling, ensuring compatibility and efficient integration of pre-existing Xilinx IPs.
- **Memory Management:** Processed images were stored in memory for efficient access by a Zynq processor.
- **High-Speed Transmission:** Images were further processed on Zynq and transmitted over Ethernet for real-time analysis.

## Technical Details
- **Hardware:** Xilinx FPGA, Sony sensors, Zynq processing unit.
- **Development:**
  - Designed and implemented the FPGA architecture in **VHDL**.
  - Verified using **SystemVerilog** testbenches.
  - Integrated pre-existing Xilinx IP cores into the design.
- **Technologies Used:**
  - Xilinx Vivado for synthesis and implementation.
  - Verilog/SystemVerilog for verification.
  - AXI bus for internal video data routing.
- **Image Pipeline:** Acquired and corrected images stored in memory before being accessed by Zynq for further processing.

## Challenges and Solutions
- **High-Speed Communication:** Overcame bus speed limitations by implementing dynamic phase alignment (DPA) to maintain reliable sensor communication at maximum speed.
- **AXI Integration:** Successfully adapted the design to incorporate pre-existing Xilinx IP cores, leveraging the AXI protocol for efficient video data handling.
- **Synchronization:** Managed synchronization between two sensors for seamless optical zoom integration.
- **Processing Efficiency:** Optimized FPGA resources to handle the entire image processing pipeline without bottlenecks.

## Outcome
The camera system delivered exceptional performance in industrial product inspection, leveraging dual-sensor optical zoom and real-time Ethernet transmission. Its robust image processing pipeline, AXI-based architecture, and high-speed communication met demanding industrial requirements.



