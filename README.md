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

   # Encoder Frequency and Speed Calculation

This guide explains how to calculate the frequency and speed of a system using encoders with a specified resolution.

## 1. Frequency Calculation from Encoder Counts

The encoder provides 12 counts per revolution (CPR) of the motor shaft when counting both edges of both channels. To compute the counts per revolution of the drive sprockets, you multiply the gearbox’s gear ratio by 12.

For example, if 75:1 motors are used (with a more accurate gear ratio of 75.81:1), the encoder provides approximately:

\[
\text{CPR} = 75.81 \times 12 \approx 909.7
\]

To calculate the frequency of encoder counts per second, use the following formula:

\[
f_{enc} = \frac{\text{RPM} \times \text{CPR}}{60}
\]

Where:
- `RPM` is the revolutions per minute of the motor.
- `CPR` is the counts per revolution of the drive sprockets (909.7 in this case).
- The division by 60 converts RPM to revolutions per second.

### Example

If the motor is running at 1000 RPM, the encoder count frequency would be:

\[
f_{enc} = \frac{1000 \times 909.7}{60} = 15161.67 \, \text{counts/s}
\]

## 2. Speed Calculation (Linear Speed)

To calculate the linear speed of a robot or vehicle, you need to convert the number of rotations of the drive sprockets into linear motion. This can be done if you know the radius of the wheels.

The formula to calculate the linear speed \( v \) is:

\[
v = 2 \pi r \times \frac{\text{RPM}}{60}
\]

Where:
- `r` is the radius of the wheel.
- `v` is the linear velocity of the robot in meters per second (m/s).

### Example

If the wheel has a radius of 0.05 meters and the motor is running at 1000 RPM, the linear velocity would be:

\[
v = 2 \pi (0.05) \times \frac{1000}{60} \approx 5.24 \, \text{m/s}
\]

## Conclusion

By calculating the encoder frequency and converting it to linear speed, you can determine the performance and movement of your system based on the encoder's counts.

   
## Developers
- **Mutasem Bader** 
- **Felix Fritz Biermann**
