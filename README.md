# PSOC
Smart Lamp System
A real-time embedded system that wirelessly controls a smart lamp based on ambient light and motion detection. This project utilizes FreeRTOS for multitasking and Cypress PSoC5LP microcontrollers for hardware implementation.

🔧 Project Overview
The system comprises two PSoC5LP microcontroller-based modules:

Transmitter Module

Receiver Module

The transmitter continuously monitors light intensity and motion. Based on these environmental inputs, it sends control signals to the receiver, which adjusts the lamp brightness accordingly using PWM.

🧠 Features
Real-time Multitasking with FreeRTOS

UART communication between transmitter and receiver

Motion detection via PIR sensor

Ambient light monitoring via LDR

PWM control of LED lamp for brightness modulation

Interrupt-driven design for responsiveness and energy efficiency

Scalable architecture for integration with other IoT devices

🛠️ Hardware Used

Module	Component	Description
Microcontroller	Cypress PSoC5LP (CY8C5588AXI-060)	32-bit MCU with integrated analog/digital features
Sensor	PIR Motion Sensor (HC-SR501)	Detects motion to trigger lamp activation
Sensor	LDR (Light Dependent Resistor)	Measures ambient light intensity
Actuator	12V LED Lamp	Controlled via PWM on receiver module
Communication	UART (RS-232 level on PSoC5)	Data exchange between transmitter and receiver
Others	Breadboard, jump wires, power supply	Circuit assembly and testing

🧵 Software Architecture
Transmitter (FreeRTOS tasks):
Task 1: Read LDR values periodically

Task 2: Poll PIR sensor and detect motion

Task 3: Send status to receiver over UART

ISR: Debounced PIR interrupt for motion detection

Receiver (FreeRTOS tasks):
Task 1: Receive UART data

Task 2: Control PWM output to LED based on input

Task 3: Heartbeat task (for testing/system alive indicator)

Timer: Auto-shutoff timer after inactivity

🧪 Results
System latency: Reduced by ~40% using FreeRTOS multitasking compared to sequential design

Response time: ~200ms for motion-to-light activation

Power efficiency: Idle task enabled deep-sleep mode on transmitter when inactive

🚀 Future Enhancements
Integrate BLE/Wi-Fi module for remote app control

Add temperature sensor for smart cooling lamps

Enable cloud logging and ML-based usage prediction

Refactor to support multi-lamp control grid

🧑‍💻 Author
Tejashwini Rajashankar
Embedded Systems & AI
California State University, Los Angeles

