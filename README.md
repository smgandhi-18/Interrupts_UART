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

## Explanation

- Interrupt Service Routine (ISR):
The ISR handles both receive and transmit interrupts from UART1.
Upon receiving data (RX interrupt) or when data is ready to be transmitted (TX interrupt), the ISR is triggered.

- Receive Interrupt Handling:
When a receive interrupt occurs, the ISR processes the received data and stores it in a receive buffer.
It then checks if there's available space in the receive queue to store the received data.
If space is available, the received byte is added to the receive queue.

- Transmit Interrupt Handling:
Upon a transmit interrupt, the ISR checks if there's data in the transmit queue awaiting transmission.
If the transmit queue is not empty and the transmit FIFO is not full, the ISR retrieves bytes from the transmit queue and sends them via UART1.
This process continues until either the transmit queue is empty or the transmit FIFO is full.

- User-Defined Functions (MyReceiveFunction() and MySendFunction()):
These functions are invoked from the main application code (main_SDK.c) to manage UART communication.
MyReceiveFunction() retrieves received bytes from the receive queue.
MySendFunction() adds bytes to the transmit queue for transmission.

- Interrupt Counters:
Global counters (CountRxIrq and CountTxIrq) are updated by the ISR to track the number of receive and transmit interrupts processed.
These counters are initialized to zero at application startup and cleared after specific sequences (\r%\r) are received.

- Main Application Code (main_SDK.c):
This file comprises tasks that utilize the UART communication functions.
It calls MyReceiveFunction() to receive bytes and MySendFunction() to transmit bytes.
Additionally, it manages counters and handles specific sequences received from the SDK console.

## License

This exercise is provided under an open-source license. See the LICENSE file for details. Provide credits to the author(s).

