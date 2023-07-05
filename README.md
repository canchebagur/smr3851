# SMR3851 Arduino Demo

This repository contains the material used in the Arduino demo made on SMR385. This material lets you connect an [Arduino® Nano 33 BLE Sense Rev2](https://docs.arduino.cc/hardware/nano-33-ble-sense-rev2) to [Edge Impulse®](https://edgeimpulse.com/) using its [Data Forwarder](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-data-forwarder) tool. 

## Contents

1. The boards: Nano 33 BLE Sense Rev2 and Nicla Vision
2. Arduino ecosystem installation
3. Edge Impulse CLI installation
4. Creating datasets with Edge Impulse® (Nano 33 BLE Sense Rev2 board)
5. Creating datasets with OpenMV (Nicla Vision)

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

- **Microcontroller**: Dual 32-bit Arm® Cortex®-M7 running at 480 MHz and Cortex®-M4 running at 240 MHz microcontroller (STM32H747AII6), 2 MB of Flash, and 1 MB of RAM (same as the Portenta H7!)
- **Connectivity**: Wi-Fi® and Bluetooth® Low Energy connectivity
- **Onboard sensors**: 6-axis IMU, digital microphone, and distance sensor
- **Onboard camera**: 2MP color camera
- **Security**: Onboard crypto chip 

## Arduino Ecosystem Installation

To use the Nano BLE Sense 33 Rev2 board with the Arduino ecosystem tools, you need to install the following:

- **IDE**: [Arduino IDE 2.0+](https://www.arduino.cc/en/software)
- **Core**: Arduino Mbed OS Nano Boards (installation via the Boards Manager of the Arduino IDE) 
- **Libraries**: [Arduino_BMI270_BMM150](https://github.com/arduino-libraries/Arduino_BMI270_BMM150) (installation via the Library Manager of the Arduino IDE)

To use the Nicla Vision board with the Arduino ecosystem tools, you need to install the following:

- **IDE**: [Arduino IDE 2.0+](https://www.arduino.cc/en/software) and [OpenMV v3.0+](https://openmv.io/pages/download)
- **Core**: Arduino Mbed OS Nicla Boards (installation via the Boards Manager of the Arduino IDE) 

Install the Arduino and OpenMV IDE first, and then use the **Boards Manager** and **Library Manager** to install the board core and libraries. 

***Note for the Nicla Vision: Before using your board, ensure its bootloader is updated to the latest release. This can be done by running the `STM32H747_manageBootloader` example. The example can be found by navigating into **File > Examples > STM32H747_System > STM32H747_manageBootloader**.***

## Creating Datasets with OpenMV (Nicla Vision)

With OpenMV running, connect your Nicla Vision board to your computer. Select the **Connect** icon in the bottom left side of the OpenMV IDE; you should see your Nicla Vision onboard green LED start flashing; this indicates that your board is on bootloader mode.

![OpenMV IDE](/assets/OpenMV_IDE_01.png)

The following connection dialogue will open; select the "**Install the latest release firmware**" option. 

![OpenMV IDE](/assets/OpenMV_IDE_02.png)

***Note: **DO NOT ERASE THE INTERNAL FILE SYSTEM of your Nicla Vision board.*****

Now, navigate to select **File > New File** and add the following code into the OpenMV code editor window and save it as `nicla_vision_test.py`. The following code will start the Nicla Vision camera and display the feed in the OpenMV IDE's frame buffer. You will also use this code to capture frames for the ML model:

```python
import sensor, image, time

sensor.reset()
sensor.set_pixformat(sensor.RGB565)
sensor.set_framesize(sensor.QVGA)
sensor.skip_frames(time = 2000)

clock = time.clock()

while(True):
    clock.tick()
    img = sensor.snapshot()
    print(clock.fps())
```

Select the **Start** icon (green triangle) in the bottom left of the OpenMV IDE; the camera feed will display in the OpenMV IDE's frame buffer (notice that the dynamic color balance is also shown). 

![OpenMV IDE](/assets/OpenMV_IDE_03.png)

Now your Nicla Vision is all set up and working!