# System Architecture

## Purpose

Describe how the sensor board connects to the rest of the avionics system.

## High-Level Blocks

```text
                  +----------------------+
                  |   Flight Computer    |
                  |      / STM32         |
                  +----------+-----------+
                             |
             +---------------+---------------+
             |                               |
          Power                         Data / I/O
             |                               |
     +-------v-------------------------------v-------+
     |              SENSOR BOARD                     |
     |                                               |
     |  +---------+   +---------+   +---------+      |
     |  |Sensor 1 |   |Sensor 2 |   |Sensor 3 |      |
     |  +---------+   +---------+   +---------+      |
     |                                               |
     |       Power + Shared Communication Buses      |
     +-----------------------------------------------+
```

Replace this diagram with the actual avionics architecture as interfaces are finalized.
