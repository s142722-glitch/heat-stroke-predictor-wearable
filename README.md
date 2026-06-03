# Heat Stroke Predictor - Wearable Device

A wearable health monitoring system designed to predict and prevent heat stroke through real-time physiological and environmental sensing. Built with **ESP32-C3 Super Mini** and multiple I2C sensors, featuring a two-part architecture with a lightweight wearable unit and a BLE base station.

![Wearable Device](images/wearable-device.jpeg)

## Features

- **Body Temperature Monitoring** - MAX30205 high-accuracy clinical-grade body temperature sensor
- **Heart Rate & SpO2** - MAX30102 pulse oximeter and heart rate sensor
- **Environmental Sensing** - BME280 sensor for ambient temperature, humidity, and barometric pressure
- **BLE Wireless Communication** - Bluetooth Low Energy link between wearable and base station
- **Two-Part Architecture** - Lightweight wearable unit + BLE base station for data processing and display
- **Real-Time Data Acquisition** - Continuous multi-sensor sampling with I2C bus
- **Heat Stroke Risk Assessment** - Algorithm combining body temp, heart rate, SpO2, and environmental data

## System Architecture

```
 WEARABLE UNIT                         BASE STATION
+------------------+        BLE        +------------------+
| ESP32-C3 Super   | ~~~~~~~~~~~~~~~>  | ESP32-C3 Super   |
| Mini             |                   | Mini             |
|                  |                   |                  |
| Sensors (I2C):   |                   | - Data display   |
| - BME280         |                   | - Risk analysis  |
| - MAX30205       |                   | - Alert system   |
| - MAX30102       |                   |                  |
+------------------+                   +------------------+
```

## Hardware Components

### Wearable Unit
| Component | Function |
|-----------|----------|
| ESP32-C3 Super Mini | Main microcontroller with BLE |
| BME280 | Ambient temperature, humidity, pressure (I2C) |
| MAX30205 | Clinical-grade body temperature sensor (I2C) |
| MAX30102 | Heart rate and SpO2 pulse oximeter (I2C) |

### Base Station
| Component | Function |
|-----------|----------|
| ESP32-C3 Super Mini | BLE receiver and data processor |
| Display / Interface | Real-time readings and alerts |

## Prototype (Proteus Simulation)

The initial prototype was developed and validated in Proteus using an ATmega8 microcontroller with basic temperature, humidity, and gas sensors before moving to the final ESP32-based wearable design.

![Proteus Simulation](images/simulation.png)

### Prototype Components
| Component | Description |
|-----------|-------------|
| U1 - ATmega8 | Prototype microcontroller |
| LCD1 - LM016L | 16x2 character LCD display |
| U2 | Temperature/Humidity sensor |
| U3 - LM358N | Op-amp for signal conditioning |
| D1, D2, D3 | LED status indicators (Red/Green) |

### Prototype Output
```
======================================
    Heat Stress Monitor v2.0
======================================

------ Readings ------
Temp: 29.29 C
Hum:  48.04 %
Gas:  330.07 ppm
Status: SAFE
```

## Tech Stack

- **ESP32-C3 Super Mini** - Main microcontroller (final design)
- **ATmega8** - Prototype microcontroller
- **Arduino IDE** - Firmware development
- **Proteus 8** - Circuit simulation (prototype stage)
- **I2C Protocol** - Sensor communication bus
- **BLE** - Wireless data transmission

## Development Stages

1. **Prototype** - Proteus simulation with ATmega8, basic sensors, LCD display, and LED alerts
2. **Hardware Migration** - Moved to ESP32-C3 Super Mini for BLE capability and I2C sensor support
3. **Sensor Integration** - Integrated BME280, MAX30205, and MAX30102 via I2C bus
4. **Wireless Architecture** - Implemented BLE communication between wearable and base station
5. **Final Assembly** - Compact wearable form factor with wrist strap
