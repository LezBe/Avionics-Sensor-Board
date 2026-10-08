# System Architecture

## Purpose

This document describes how individual sensor modules fit into the shared avionics sensor board and interface with the flight computer / STM32.

## High-Level Architecture

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
       |   |    Sensor 1    |     |    Sensor 2    |   |
       |   +-------+--------+     +-------+--------+   |
       |           |                      |            |
       |           +------ Shared SPI ----+            |
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

This allows multiple sensors to share one SPI peripheral on the STM32 while remaining individually selectable.

## Future Integration

Each sensor should be developed on its own feature branch, reviewed, and then merged into the integrated board design when ready.
