# Zumo328PEncoders Library

**Zumo328PEncoders** is a library designed for reading and managing encoder counts on the Zumo robot using an ATmega328P microcontroller (such as an Arduino Uno). This library provides an efficient and reliable way to monitor the rotation of motors, enabling accurate tracking of movement and direction.

## Background

This library is based on the encoder implementation from the Zumo 32U4 library and is adapted specifically for the Zumo Shield for Arduino, v1.2. It is designed to work with external encoders such as the [Magnetic Encoder Pair Kit for Micro Metal Gearmotors, 12 CPR, 2.7–18V](https://www.pololu.com/product/3081) from Pololu.

## Features

- **Ported for ATmega328P**: Adapted specifically for use with the Arduino Uno and compatible boards.
- **Encoder Count Monitoring**: Tracks both left and right encoders using interrupts for high accuracy.
- **Error Detection**: Detects and reports any potential encoder errors to help ensure data reliability.
- **Seamless Integration**: Uses `attachInterrupt()` for ease of compatibility with other code.

## Installation

1. Clone or download this repository.
2. Place the `Zumo328PEncoders` folder in your Arduino `libraries` directory.
3. Restart the Arduino IDE and include the library in your sketch.
