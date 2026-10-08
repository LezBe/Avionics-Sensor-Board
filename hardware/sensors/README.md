# Sensor Designs

Each sensor should have its own directory so team members can develop, review, and document sensor circuits independently before they are integrated into the final board.

## Current Sensor on This Branch

```text
sensors/
├── lsm6dso32/
│   └── README.md
└── _template/
    └── README.md
```

## LSM6DSO32

The LSM6DSO32 folder contains design and integration documentation for the planned 6-axis IMU.

No KiCad schematic has been committed yet. The next hardware step is to create or import a reviewed SPI schematic and then add the verified LGA-14 footprint.

## Adding Another Sensor

1. Copy `_template/README.md` into a new sensor directory.
2. Add the sensor's KiCad schematic and supporting project files.
3. Document supply voltage, SPI interface, decoupling, chip select, interrupts, and MCU connections.
4. Add or reference the manufacturer datasheet.
5. Commit any custom symbols or footprints required by the design.
6. Have another team member review the circuit before integration.

Approved circuits should ultimately be incorporated into the final design under `hardware/sensor_board/`.
