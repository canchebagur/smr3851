# SMR3851 Arduino Demo

This repository contains the material used in the Arduino demo made on SMR385. This material lets you connect an [Arduino® Nano 33 BLE Sense Rev2](https://docs.arduino.cc/hardware/nano-33-ble-sense-rev2) to [Edge Impulse®](https://edgeimpulse.com/) using its [Data Forwarder](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-data-forwarder) tool. 

## Contents

1. The boards: Nano 33 BLE Sense Rev2 and Nicla Vision
2. Arduino ecosystem installation
3. Edge Impulse CLI installation
4. Sending data from the onboard accelerometer to Edge Impulse

## The Boards: Nano 33 BLE Sense Rev2 and Nicla Vision

The [Arduino Nano 33 BLE Sense Rev2](https://docs.arduino.cc/hardware/nano-33-ble-sense-rev2) is a compact and versatile development board based on the nRF52840 microcontroller from Nordic Semiconductor®. The board was designed for low-power applications and features wireless connectivity via Bluetooth® Low Energy (BLE). 

![The Arduino Nicla Vision](/assets/nano_ble_sense_33_01.png)

Some key features of the Nano 33 BLE Sense Rev2 board are the following:

- **Microcontroller**: 32-bit ARM Cortex-M4 processor running at 64 MHz (nRF52840), 1 MB of Flash, and 256 kB of SRAM
- **Connectivity**: Bluetooth® Low Energy connectivity
- **11 onboard sensors**: 9-axis Inertial Measurement Unit (IMU), temperature, humidity, barometric pressure, digital microphone, gesture, proximity, ambient light, and color sensor

***There are currently two versions of the Nano 33 BLE Sense board, Rev1, and Rev2. The IMU, temperature sensor, humidity sensor, and microphone of the boards differ, so the libraries used with each of the boards.***

The Nicla Vision is a powerful development board with a 2MP color camera in a tiny form factor (just 23x23 mm). With Wi-Fi® and Bluetooth® Low Energy connectivity, the Nicla Vision maximizes compatibility with professional and consumer equipment. 

![The Arduino Nicla Vision](/assets/nicla_vision_01.png)

Some key features of the Nicla Vision board are the following:

- **Microcontroller**: Dual 32-bit Arm® Cortex®-M7 running at 480 MHz and Cortex®-M4 running at 240 MHz microcontroller (STM32H747AII6), 2 MB of Flash, and 1 MB of RAM
- **Connectivity**: Wi-Fi® and Bluetooth® Low Energy connectivity
- **Onboard sensors**: 6-axis IMU, digital microphone, and distance sensor
- **Onboard camera**: 2MP color camera
- **Security**: Onboard crypto chip 

## Arduino Ecosystem Installation

For using the Nano BLE Sense 33 Rev2 board with the Arduino ecosystem tools, you need to install the following:

- **IDE**: [Arduino IDE 2.0+](https://www.arduino.cc/en/software)
- **Core**: Arduino Mbed OS Nano Boards (installation via the Boards Manager of the Arduino IDE) 
- **Libraries**: [Arduino_BMI270_BMM150](https://github.com/arduino-libraries/Arduino_BMI270_BMM150) (installation via the Library Manager of the Arduino IDE)

For using the Nicla Vision board with the Arduino ecosystem tools, you need to install the following:

- **IDE**: [Arduino IDE 2.0+](https://www.arduino.cc/en/software) and [OpenMV v3.0+](https://openmv.io/pages/download)
- **Core**: Arduino Mbed OS Nicla Boards (installation via the Boards Manager of the Arduino IDE) 

Install first the Arduino and OpenMV IDE and then use the **Boards Manager** and **Library Manager** to install the board core and libraries.