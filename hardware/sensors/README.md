# Sensor Designs

Each sensor should have its own directory so team members can develop, review, and document sensor circuits independently before they are integrated into the final board.

## Recommended Structure

```text
sensors/
├── <sensor-name>/
│   ├── README.md
│   ├── <sensor>.kicad_sch
│   └── supporting project files
└── _template/
    └── README.md
```

## Adding a Sensor

1. Copy `_template/README.md` into a new sensor directory.
2. Add the sensor's KiCad schematic and supporting project files.
3. Document supply voltage, SPI interface, decoupling, chip select, interrupts, and MCU connections.
4. Add or reference the manufacturer datasheet.
5. Commit any custom symbols or footprints required by the design.
6. Have another team member review the circuit before integration.

Approved circuits should ultimately be incorporated into the final design under `hardware/sensor_board/`.
