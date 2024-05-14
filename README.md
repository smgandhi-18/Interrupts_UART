# UART Interrupt-Driven Driver Enhancement using FPGA

Implements interrupt-driven driver for UART1 in the Zynq-7000 SoC. The main objective is to design interrupt-driven methods for receiving and transmitting bytes through UART1.

## Overview

- **Objective:** Design interrupt-driven methods for receiving and transmitting bytes through UART1.
- **Files:**
  - `main_SDK.c`: Contains two FreeRTOS tasks calling the user-defined driver functions.
  - `uart_driver.h`: Driver software containing the ISR and definitions of new user-defined functions.
  - `initialization.c` and `initialization.h`: Initialization functions and definitions.

## Steps

1. **Download and Setup:**
   - Download the provided skeleton software design from the folder `Interrupt_driven_UART`.
   - Open the unchanged hardware design for the Zynq-7000 SoC in Vivado.
   - Export the design to Vivado SDK and create a new application project. Load all the SDK C files in the newly created project.

## Requirements

- Zynq-7000 SoC development environment.
- Vivado Design Suite.
- SDK (Software Development Kit).
- FreeRTOS.
- UART1 hardware configuration.

## Usage

- Follow the steps provided to download, setup, and modify the provided software design.
- Run the project to test the interrupt-driven UART driver enhancements.

## License

This exercise is provided under an open-source license. See the LICENSE file for details.

