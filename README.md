# Zumo328PControl Library

**Zumo328PControl** is a library designed for reading and managing encoder counts and controlling the speed of the Zumo robot using the ATmega328P microcontroller (such as the Arduino Uno). This library provides an efficient and reliable way to monitor motor rotation, enabling accurate tracking of movement and direction.

## Background

This encoder-based implementation is derived from the Zumo 32U4 library and specifically adapted for the Zumo Shield for Arduino v1.2. It is designed to work with external encoders such as the Magnetic Encoder Pair Kit for Micro Metal Gearmotors, 12 CPR, 2.7–18V from (https://www.pololu.com/product/3081) Pololu. The PID algorithm has been created to control motor direction and speed, improving line-following capabilities.

### Pin Configuration Changes

- **Left Encoder XORed Input**: Mapped to **Pin 2**.
- **Right Encoder XORed Input**: Mapped to **Pin 3**.
- **Left Encoder Input**: Mapped to **Pin 6**.
- **Right Encoder Input**: Mapped to **Pin 12**.
- **Note**:
  - **Pin 2 and 3**: The use of I2C is no longer possible due to the use of external interrupts for reading encoder signals.
  - **Pin 12**: Used for a user push button, so it can no longer be used for that purpose.
  - **Pin 6**: Connected to the buzzer via a jumper; the jumper must be removed to enable encoder functionality.

### Implementation Details

On the Zumo 32U4 board, an XOR chip was used to reduce the required number of interrupt pins for encoders. This has been addressed in this library through software-based solutions, allowing the same functionality using fewer hardware resources. We use `attachInterrupt()` instead of directly defining `ISR(INTx_vect)` to ensure compatibility with other code that also utilizes `attachInterrupt()`.

## Features

- **Ported for ATmega328P**: Adapted specifically for use with the Arduino Uno and compatible boards.
- **Encoder Count Monitoring**: Tracks both left and right encoders using interrupts for high accuracy.
- **Error Detection**: Detects and reports any potential encoder errors to help ensure data reliability.
- **Seamless Integration**: Uses `attachInterrupt()` for ease of compatibility with other code.

## Installation

1. Clone or download this repository.
2. Place the `Zumo328PControl` folder in your Arduino `libraries` directory.
3. Restart the Arduino IDE and include the library in your sketch.
   
## Developers
- **Mutasem Bader** 
- **Felix Fritz Biermann**
