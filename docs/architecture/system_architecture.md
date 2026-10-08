# System Architecture

## Purpose

This document describes how individual sensor modules fit into the shared avionics sensor board and interface with the flight computer / STM32.

## Current High-Level Architecture

```text
                    +----------------------+
                    |   Flight Computer    |
                    |      / STM32         |
                    +----------+-----------+
                               |
                +--------------+--------------+
                |                             |
             Power                          SPI
                |                             |
       +--------v-----------------------------v--------+
       |                SENSOR BOARD                   |
       |                                               |
       |   +----------------+     +----------------+   |
       |   |     BMP581     |     | Future Sensor  |   |
       |   | Pressure/Temp  |     |     Module     |   |
       |   +-------+--------+     +-------+--------+   |
       |           |                      |            |
       |           +----- Shared SPI -----+            |
       |                                               |
       |     SCK / MOSI / MISO + Per-Device CS        |
       +-----------------------------------------------+
```

## SPI Architecture

SPI is the communication standard for the sensor board.

The expected topology is:

- shared SCK between compatible SPI peripherals;
- shared MOSI;
- shared MISO;
- a dedicated chip-select signal for each sensor;
- optional dedicated interrupt lines where required.

This structure allows multiple sensors to share one SPI peripheral on the STM32 while remaining individually addressable through their chip-select signals.

## BMP581 Module

The BMP581 is currently the first populated sensor module in the repository. Its design is located at:

`hardware/sensors/bmp581/`

The current schematic uses a 3.3 V board supply and is intended to communicate over SPI.

The BMP581 signals map as follows:

| Sensor Pin | SPI Role |
|---|---|
| SCK | SCK |
| SDI | MOSI |
| SDO | MISO |
| CSB | Chip Select |
| INT | Optional interrupt |

Before the BMP581 is integrated into the final PCB, the team still needs to:

- verify the BMP581 footprint against the Bosch landing pattern;
- complete peer schematic review;
- confirm final shared SPI net names;
- assign the BMP581 chip-select signal;
- decide whether the INT signal will be routed to the MCU;
- integrate the approved circuit into the top-level sensor-board schematic;
- complete PCB layout and DRC;
- bench-test the assembled sensor.

## Future Integration

Additional sensor modules should follow the same modular structure and use SPI where supported so they can share the common SPI bus defined by the project requirements.
