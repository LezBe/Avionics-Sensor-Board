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
       |   +------------------+   +----------------+   |
       |   |   LSM6DSO32     |   | Future Sensor  |   |
       |   |  6-Axis IMU     |   |     Module     |   |
       |   +--------+---------+   +-------+--------+   |
       |            |                     |            |
       |            +----- Shared SPI ----+            |
       |                                               |
       |      SCK / MOSI / MISO + Per-Device CS       |
       +-----------------------------------------------+
```

## SPI Architecture

SPI is the communication standard for the sensor board.

Expected topology:

- shared SCK;
- shared MOSI;
- shared MISO;
- dedicated chip-select for each sensor;
- optional dedicated interrupt lines.

## LSM6DSO32 Module

The LSM6DSO32 is planned to provide 3-axis acceleration and 3-axis angular-rate measurements.

Its documentation is in:

`hardware/sensors/lsm6dso32/`

Before integration, the team must create/review the KiCad schematic, verify the LGA-14 footprint, assign the chip-select and interrupt lines, and define how the IMU X/Y/Z axes map to the airframe coordinate system.

## Future Integration

Additional sensor modules should follow the same modular structure and use the shared SPI architecture where supported.
