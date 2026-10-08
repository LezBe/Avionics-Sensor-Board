# Interface Control

This document is the shared reference for electrical interfaces between the sensor board and the rest of the avionics system.

## Power

| Net | Nominal Voltage | Source | Loads | Notes |
|---|---:|---|---|---|
| 3V3 | 3.3 V | Flight Computer / STM32 system | LSM6DSO32 and other sensors | Confirm available current and final connector source |
| GND | 0 V | System Ground | All | Shared board ground |

## Communication Standard

The sensor board uses **SPI** for communication between the STM32 / flight computer and sensor peripherals.

Shared SPI signals:

- `SPI_SCK`
- `SPI_MOSI`
- `SPI_MISO`

Each peripheral uses a dedicated chip-select signal.

## Digital Interfaces

| Signal | Voltage | Protocol | Source | Destination | Notes |
|---|---:|---|---|---|---|
| SPI_SCK | 3.3 V | SPI | MCU | LSM6DSO32 and other sensors | Shared clock |
| SPI_MOSI | 3.3 V | SPI | MCU | LSM6DSO32 and other sensors | Shared controller-to-peripheral data |
| SPI_MISO | 3.3 V | SPI | Sensors | MCU | Shared peripheral-to-controller data |
| LSM6DSO32_CS | 3.3 V | SPI CS | MCU | LSM6DSO32 | Dedicated chip select |
| LSM6DSO32_INT1 | 3.3 V | GPIO | LSM6DSO32 | MCU | Optional interrupt |
| LSM6DSO32_INT2 | 3.3 V | GPIO | LSM6DSO32 | MCU | Optional interrupt |

## SPI Peripheral Assignment

| Device | Bus | Chip Select | Interrupt | Status / Notes |
|---|---|---|---|---|
| LSM6DSO32 | SPI | LSM6DSO32_CS | INT1 / INT2 available | Schematic and MCU pin assignment TBD |
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
| 6 | LSM6DSO32_CS | Input | 3.3 V | Dedicated IMU chip select |
| 7 | TBD | TBD | TBD | Interrupt/additional CS signals pending |

## Integration Requirements

- Confirm the STM32 SPI peripheral and exact MCU pin assignments.
- Verify that all connected sensors support compatible SPI voltage levels and timing.
- Give each SPI sensor a unique chip-select signal.
- Keep shared SPI net naming consistent across hierarchical sheets.
- Confirm which sensor interrupt lines are required.
- Define and document the LSM6DSO32 physical axis orientation.
- Verify all sensor footprints before PCB fabrication.
