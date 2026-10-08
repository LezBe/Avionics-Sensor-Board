# Interface Control

This document is the shared reference for electrical interfaces between the sensor board and the rest of the avionics system.

## Power

| Net | Nominal Voltage | Source | Loads | Notes |
|---|---:|---|---|---|
| 3V3 | 3.3 V | Flight Computer / STM32 system | BMP581 and other sensors | Confirm available current and final connector source |
| GND | 0 V | System Ground | All | Shared board ground |

## Digital Interfaces

| Signal | Voltage | Protocol | Source | Destination | Notes |
|---|---:|---|---|---|---|
| SDA | 3.3 V | I2C | MCU / I2C devices | BMP581 and other I2C sensors | Shared-bus pull-up implementation to be finalized |
| SCL | 3.3 V | I2C | MCU | BMP581 and other I2C sensors | Shared-bus pull-up implementation to be finalized |
| BMP581_INT | 3.3 V | GPIO | BMP581 | MCU | Usage to be finalized; current design should be reviewed before integration |

## Sensor Addresses

| Device | Bus | Address / CS | Interrupt | Status / Notes |
|---|---|---|---|---|
| BMP581 | I2C | To be confirmed from final SDO configuration | Available | Confirm configuration during integration |
| TBD | TBD | TBD | TBD | Future sensor |

## Connector Pinout

The final flight-computer-to-sensor-board connector has not yet been finalized.

| Pin | Signal | Direction | Voltage | Notes |
|---:|---|---|---:|---|
| 1 | 3V3 | Input | 3.3 V | Proposed sensor-board supply |
| 2 | GND | Power | 0 V | |
| 3 | SDA | Bidirectional | 3.3 V | Proposed I2C |
| 4 | SCL | Input | 3.3 V | Proposed I2C |
| 5 | TBD | TBD | TBD | Final pinout pending |

## BMP581 Integration Gate

The BMP581 footprint must be committed and verified against the Bosch datasheet before the design is released for PCB fabrication.
