 # Battery Monitoring System

This project is a real-time Battery Monitoring System using ESP32, Arduino UNO, INA219 sensor, and MCP2515 CAN transceivers. It features Firebase integration for remote monitoring and data logging. The system is designed to monitor voltage, current, and power of a battery pack and is suitable for applications such as EVs, industrial battery banks, and IoT-based energy systems.

## Features

- Measures voltage, current, and power using the INA219 sensor
- Data communication between Arduino UNO and ESP32 via CAN protocol (MCP2515)
- ESP32 uploads real-time sensor data to Firebase
- Wi-Fi connectivity for remote data access and monitoring
- Scalable for large battery packs and multi-node monitoring

## Hardware Components

| Component           | Description                            |
|--------------------|----------------------------------------|
| ESP32              | Wi-Fi-enabled microcontroller          |
| Arduino UNO        | Controls sensor and sends CAN messages |
| INA219 Sensor      | Measures voltage, current, and power   |
| MCP2515 CAN Module | Enables CAN communication              |
| Battery            | Power source for testing               |
| Jumper Wires       | For connections                        |

## System Architecture

INA219/temperature/  --> Arduino UNO --> MCP2515 CAN --> ESP32 --> Wi-Fi --> Firebase

## Working Overview

- Arduino reads values from the INA219 sensor and sends the data over CAN using MCP2515.
- ESP32 receives the CAN messages and pushes the data to Firebase Realtime Database over Wi-Fi.
- The Firebase backend stores the data, which can be visualized or analyzed externally.

## Software Stack

- Arduino IDE for firmware development
- Firebase Realtime Database for cloud data logging
- MCP_CAN library for CAN communication
- Firebase ESP Client library for cloud integration

## Project Structure


## Setup Instructions

1. Connect INA219 to Arduino UNO via I2C.
2. Set up MCP2515 modules on both Arduino and ESP32 for CAN communication.
3. Upload `sensor_transmit.ino` to the Arduino UNO.
4. Upload `receiver_firebase_upload.ino` to the ESP32.
5. Add your Wi-Fi and Firebase credentials in `firebase_credentials.h`.
6. Open the Firebase Realtime Database to view live data.

## Firebase Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new Firebase project
3. Enable the Realtime Database
4. Obtain the database URL and Web API key
5. Add them to the ESP32 code

## Example Output (Firebase)

```json
{
  "Battery_Data": {
    "Voltage": "12.3",
    "Current": "1.5",
    "Power": "18.45",
    "Timestamp": "2025-08-01 10:42:00"
  }
}
