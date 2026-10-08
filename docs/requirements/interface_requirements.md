# Interface Control

This document is the shared reference for electrical interfaces between the sensor board and the rest of the avionics system.

## Power

| Net | Nominal Voltage | Source | Loads | Notes |
|---|---:|---|---|---|
| 3V3 | 3.3 V | Flight Computer / STM32 system | BMP581 and other sensors | Confirm available current and final connector source |
| GND | 0 V | System Ground | All | Shared board ground |

## Communication Standard

The sensor board uses **SPI** for communication between the STM32 / flight computer and the sensor peripherals.

Shared SPI signals:

- SCK
- MOSI
- MISO

Each SPI peripheral uses a dedicated chip-select signal.

## Digital Interfaces

| Signal | Voltage | Protocol | Source | Destination | Notes |
|---|---:|---|---|---|---|
| SPI_SCK | 3.3 V | SPI | MCU | BMP581 and other SPI sensors | Shared clock |
| SPI_MOSI | 3.3 V | SPI | MCU | BMP581 and other SPI sensors | Shared controller-to-peripheral data |
| SPI_MISO | 3.3 V | SPI | SPI sensors | MCU | Shared peripheral-to-controller data |
| BMP581_CS | 3.3 V | SPI CS | MCU | BMP581 | Dedicated chip-select |
| BMP581_INT | 3.3 V | GPIO | BMP581 | MCU | Optional interrupt; final usage TBD |

## SPI Peripheral Assignment

| Device | Bus | Chip Select | Interrupt | Status / Notes |
|---|---|---|---|---|
| BMP581 | SPI | BMP581_CS | Available | Confirm MCU pin assignment during integration |
| TBD | SPI | TBD_CS | TBD | Future sensor |

## Connector Pinout

The final flight-computer-to-sensor-board connector has not yet been finalized.

| Pin | Signal | Direction | Voltage | Notes |
|---:|---|---|---:|---|
| 1 | 3V3 | Input | 3.3 V | Proposed sensor-board supply |
| 2 | GND | Power | 0 V | |
| 3 | SPI_SCK | Input | 3.3 V | Shared SPI clock |
| 4 | SPI_MOSI | Input | 3.3 V | MCU to sensors |
| 5 | SPI_MISO | Output | 3.3 V | Sensors to MCU |
| 6 | BMP581_CS | Input | 3.3 V | Dedicated BMP581 chip select |
| 7 | BMP581_INT | Output | 3.3 V | Optional interrupt |
| 8 | TBD | TBD | TBD | Additional sensor CS or other signal |

## Integration Requirements

- Confirm the STM32 SPI peripheral and exact MCU pin assignment.
- Verify that all connected sensors support compatible SPI voltage levels and timing.
- Give each SPI sensor a unique chip-select signal.
- Keep shared SPI net naming consistent across hierarchical sheets.
- Confirm whether each sensor interrupt is required.
- Verify the BMP581 footprint against the Bosch datasheet before PCB fabrication.

## BMP581 Integration Gate

The BMP581 footprint must be committed and verified against the Bosch datasheet before the design is released for PCB fabrication.
