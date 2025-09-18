# UART Communication Between MCUs

## Overview
This project establishes UART communication between two TM4C123 LaunchPads (MCU1 and MCU2) and two PC serial terminals. The system operates in three modes showcasing various communication techniques including LED control, synchronized color selection, and a chat room.

## Features

### Mode 1: LED Control (PC to MCU1)
- User controls LED color and brightness on MCU1 via PC serial terminal.
- Colors include red, green, blue, purple, white, and dark.
- Brightness adjusted via PWM duty cycle (0–100).
- Simple UART communication between PC and MCU1 at 57600 bps.

### Mode 2: Color Wheel (MCU1 & MCU2)
- Both MCUs cycle through predefined LED colors.
- Users cycle colors using switch SW2 and send selection with SW1.
- MCU1 and MCU2 synchronize LED colors via UART communication.
- Baud rates: 57600 bps (PC to MCU1 and MCU2 to PC), 38400 bps (MCU1 to MCU2 and vice versa).

### Mode 3: Chat Room (PC to PC via MCUs)
- Bi-directional chat between two PCs through MCU1 and MCU2.
- Messages limited to < 20 characters.
- Users send messages via their PC serial terminals.
- MCU1 and MCU2 forward messages appropriately.
- Interrupt-driven UART reception ensures reliable communication.
- Exiting chat via SW1 on either MCU.

## Hardware Setup
- Two TM4C123 LaunchPads (MCU1, MCU2)
- Two PC serial terminals
- Switches and RGB LEDs on MCU boards
- Connections:
  - UART0 for PC-MCU communication at 57600 bps
  - UART2 (MCU1) and UART3 (MCU2) for inter-MCU communication at 38400 bps

## Software Design
- Interrupt-driven UART RX for incoming data handling.
- PWM for LED brightness control.
- State machine managing operating modes and transitions.
- GPIO inputs for switches to cycle colors/send data/exit modes.
- UART transmit and receive buffers with synchronization.

## Usage Instructions
1. Connect MCUs and PCs as described.
2. Use PC serial terminal 1 to control MCU1 LEDs in Mode 1.
3. Switch to Mode 2 for multi-MCU synchronized color control using onboard buttons.
4. Switch to Mode 3 to start bi-directional PC chat through MCUs.
5. Exit modes using designated switches.
6. Observe UART responses and LED indicators for feedback.

## Challenges and Lessons Learned
- Managing different baud rates for PC-MCU and MCU-MCU communication.
- Implementing interrupt-driven reliable UART transfers.
- Synchronizing LED color states across multiple MCUs.
- Designing multi-mode interaction with clear state management.
- Understanding and applying microcontroller peripherals (UART, GPIO, PWM, interrupts).

## Contributors
- Jonathan Cerniaz
- Joseph Guzman
- Afzal Hakim
- Robby Rimal

## Additional Resources
- Video Demo: [All modes](https://youtu.be/k_YQ9rOFpMw?feature=shared)
