# Interface Control

This document is the shared reference for electrical interfaces between the sensor board and the rest of the avionics system.

## Power

| Net | Nominal Voltage | Source | Loads | Notes |
|---|---:|---|---|---|
| 3V3 | 3.3 V | TBD | Sensors | Confirm source/current capability |
| GND | 0 V | System Ground | All | |

## Digital Interfaces

| Signal | Voltage | Protocol | Source | Destination | Notes |
|---|---:|---|---|---|---|
| SDA | 3.3 V | I2C | MCU / Devices | I2C devices | Pull-up value TBD |
| SCL | 3.3 V | I2C | MCU | I2C devices | Pull-up value TBD |

## Sensor Addresses

| Device | Bus | Address / CS | Interrupt | Notes |
|---|---|---|---|---|
| TBD | I2C | TBD | TBD | |

## Connector Pinout

| Pin | Signal | Direction | Voltage | Notes |
|---:|---|---|---:|---|
| 1 | TBD | TBD | TBD | |
