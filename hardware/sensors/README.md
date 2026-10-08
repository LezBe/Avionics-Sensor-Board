# Sensor Designs

Each sensor should have its own directory so team members can develop, review, and document sensor circuits independently before they are integrated into the final board.

## Current Sensors

```text
sensors/
├── bmp581/
│   ├── BMP_unit.kicad_sch
│   ├── BMP_unit.kicad_pro
│   ├── BMP_unit.kicad_pcb
│   ├── README.md
│   └── SOURCE.md
└── _template/
    └── README.md
```

## BMP581

The BMP581 folder contains the current barometric pressure sensor design copied from the original `LezBe/BMPunit` repository.

The schematic is available and the BMP581 symbol is embedded in the schematic. However, the referenced `QFN10_BMP581_BOS` footprint file was not present in the source repository, so footprint verification remains an open task before PCB fabrication.

See [bmp581/README.md](bmp581/README.md) for design details.

## Adding Another Sensor

1. Copy `_template/README.md` into a new sensor directory.
2. Add the sensor's KiCad schematic and supporting project files.
3. Document supply voltage, communication interface, decoupling, address/configuration, interrupts, and MCU connections.
4. Add or reference the manufacturer datasheet.
5. Commit any custom symbols or footprints required by the design.
6. Have another team member review the circuit before integration.

Approved circuits should ultimately be incorporated into the final design under `hardware/sensor_board/`.
