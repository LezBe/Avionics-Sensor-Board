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
             Power                       Data / I/O
                |                             |
       +--------v-----------------------------v--------+
       |                SENSOR BOARD                   |
       |                                               |
       |   +----------------+     +----------------+   |
       |   |     BMP581     |     | Future Sensor  |   |
       |   | Pressure/Temp  |     |     Module     |   |
       |   +-------+--------+     +-------+--------+   |
       |           |                      |            |
       |           +------ Shared Bus ----+            |
       |                                               |
       |       Power + Shared Communication Buses      |
       +-----------------------------------------------+
```

## BMP581 Module

The BMP581 is currently the first populated sensor module in the repository. Its design is located at:

`hardware/sensors/bmp581/`

The current schematic uses a 3.3 V board supply and is intended to communicate over I2C.

Before the BMP581 is integrated into the final PCB, the team still needs to:

- verify the BMP581 footprint against the Bosch landing pattern;
- complete peer schematic review;
- confirm final I2C bus integration and address configuration;
- integrate the approved circuit into the top-level sensor-board schematic;
- complete PCB layout and DRC;
- bench-test the assembled sensor.

## Future Integration

Additional sensor modules should follow the same modular structure and connect through the shared power, communication, and flight-computer interfaces defined by the project requirements.
