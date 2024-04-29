# PSOC
Smart Lamp System
The project described in the provided code outlines a smart lamp system implemented using PSoC (Programmable System-on-Chip) microcontrollers and the FreeRTOS real-time operating system. The system consists of two main components: a transmitter and a receiver, each equipped with specific functions and tasks. Here's a brief of how the smart lamp system operates:
Transmitter:
Hardware Initialization: The transmitter sets up global interrupts and initializes UART (Universal Asynchronous Receiver/Transmitter) for communication and other necessary hardware components.
Interrupt Service Routine (ISR): An ISR for receiving UART data is implemented. Data received through UART is stored in a circular buffer (rx_buf).
String Handling: The system continuously checks the received buffer for new data and processes strings delimited by characters like spaces, tabs, carriage returns, or line feeds.
Command Execution: Upon receiving and validating a string, the system checks environmental sensor values, specifically:
Light Sensor (LDR): Measures ambient light intensity.
PIR Sensor: Detects motion.
Based on the sensor readings, if the light level is below a threshold (e.g., 300) and motion is detected, the lamp is turned "ON." Otherwise, it is turned "OFF." This action is followed by a response message through UART, and the system prompts for new input.
Receiver:
Hardware Initialization: Similar to the transmitter, the receiver sets up global interrupts and UART for communication.
Command Parsing and Execution: The receiver waits for commands from the UART. These commands include turning an LED on or off and displaying help instructions. The commands are processed, converted to uppercase, and executed accordingly.
User Interaction: The system provides a user-friendly command interface over UART, displaying a splash screen, command usage help, and a command prompt.
LED Control: Based on the parsed command, the receiver controls an LED to turn it on or off, providing feedback through UART about the action performed.
General Operation:
The system operates continuously, checking for new strings in the buffer and processing them accordingly.
Both the transmitter and receiver are designed to run tasks indefinitely with the capability to reset if the scheduler ever returns (though it should not).
Conclusion:
The smart lamp system effectively uses sensors and real-time data processing to automate lighting based on environmental conditions and detected motion, providing a practical example of how embedded systems can be used to create responsive and interactive devices. This system can be expanded or modified for broader applications in smart home or office environments.
