# Table Tennis Motion Classifier (TinyML)

This project was developed for the **IESTI01 - TINYML (Machine Learning Applied for Embedded IoT Devices)** course at the **Universidade Federal de Itajubá (UNIFEI)**, taught by Professor Marcelo José Rovai.

The objective is to classify common table tennis movements using an **Arduino Nano 33 BLE Sense** integrated into a racket, processed through the **Edge Impulse** platform.

## Authors
- Daniel Ferreira Lara
- Enzo Yukio Chinen
- Matheus Siston Galdino

## Overview
The system identifies four basic table tennis strokes plus an "Idle" state using the 6-axis IMU (Accelerometer and Gyroscope) integrated into the Arduino Nano 33 BLE Sense. The device provides real-time feedback through a buzzer and an LED to indicate the detected movement.

### Movement Classes & Feedback
| Class | Action | Buzzer Feedback | LED Feedback |
| :--- | :--- | :--- | :--- |
| **Idle** | Waiting or static racket | No sound | LED R OFF |
| **Backhand** | Backhand stroke | 1 beep | LED R ON |
| **Cozinhada** | Chop stroke | 2 beeps | LED R ON |
| **Forehand** | Forehand stroke | 3 beeps | LED R ON |
| **Serve** | Serving motion | 4 beeps | LED R ON |

## Hardware Requirements
- **Arduino Nano 33 BLE Sense**
- **Buzzer** (connected to Pin 3)
- Table Tennis Racket
- Battery (for portable operation)

## Software & Libraries
The implementation uses the following libraries:
- `Arduino_LSM9DS1` (IMU)
- `TableTennisMotion_inferencing` (Exported Edge Impulse library)
- `Arduino_LPS22HB`, `Arduino_HTS221`, `Arduino_APDS9960` (Standard sensors for the board)

## Methodology
- **Data Collection:** Approximately 15 minutes of motion data recorded at 100 Hz.
- **Preprocessing:** Spectral analysis with a 2000 ms window and 200 ms sliding increment.
- **Model:** Deep Neural Network (DNN) trained on Edge Impulse.
- **Performance:** Achieved over **95% accuracy** in testing for classification of movements.

## Project Resources
- **PDF Report:** Detailed technical documentation is available in this repository as `TableTennisMotionClassifier.pdf`.
- **Demo Video:** [Watch on YouTube](https://youtu.be/QTeRWiVCu_U)
- **Edge Impulse Project:** The project is available on Edge Impulse for further details. (Check the PDF report for embedded links).

## Usage
1. Mount the Arduino Nano 33 BLE Sense on the racket as shown in the documentation.
2. Upload the `Final.ino` sketch using the Arduino IDE.
3. Ensure the `TableTennisMotion_inferencing` library is installed (provided as `.zip` in the repository).
4. Monitor the serial output or use the buzzer/LED for real-time inference.

---
*Developed as a final project for TinyML at UNIFEI, 2023.*
