# Avionics Sensor Board

Central hardware repository for the avionics team's multi-sensor PCB.

This repository is organized so team members can develop and review individual sensor circuits independently while maintaining one controlled design for the integrated sensor board.

## Goals

- Consolidate individual sensor designs in one repository
- Keep each sensor circuit modular and easy to review
- Standardize power, SPI communication, and MCU interfaces
- Maintain a controlled integrated KiCad project
- Preserve design decisions, datasheets, manufacturing files, and test results
- Make collaboration and revision history easier through Git and GitHub

## Repository Structure

```text
Avionics-Sensor-Board/
├── hardware/
│   ├── sensors/
│   │   ├── bmp581/              # BMP581 pressure sensor design
│   │   └── _template/           # Template for future sensor modules
│   ├── power/                   # Power regulation/distribution
│   ├── communications/          # Shared SPI bus and communication circuitry
│   └── sensor_board/            # Final integrated KiCad PCB project
├── libraries/
│   └── footprints/
│       └── BMP581/              # BMP581 footprint review/documentation
├── docs/
│   ├── architecture/
│   ├── requirements/
│   ├── datasheets/
│   │   └── BMP581.md
│   └── design_reviews/
├── manufacturing/
├── testing/
└── firmware/
```

## Current Sensor Designs

### BMP581 Barometric Pressure Sensor

The BMP581 module is the first sensor design added to this repository.

It currently includes:

- KiCad schematic
- KiCad project file
- Initial PCB file
- Sensor-specific documentation
- Bosch datasheet references
- Footprint verification notes
- Source traceability back to the original `BMPunit` repository

The BMP581 will communicate with the rest of the avionics system over SPI, consistent with the communication architecture planned for the sensor board.

The original BMP581 schematic references a footprint named `QFN10_BMP581_BOS`, but that footprint file was not committed to the original `BMPunit` repository. The sensor design should therefore **not be treated as fabrication-ready until the BMP581 footprint is added and verified against the Bosch landing pattern**.

See [hardware/sensors/bmp581/README.md](hardware/sensors/bmp581/README.md) for the module details.

## Recommended Design Flow

1. Develop each sensor circuit in its own folder under `hardware/sensors/`.
2. Document the sensor supply, SPI signals, supporting circuitry, and owner.
3. Run a peer schematic review.
4. Verify custom symbols and footprints against manufacturer documentation.
5. Integrate the approved design into `hardware/sensor_board/`.
6. Perform ERC and design-rule checks.
7. Assign and verify footprints.
8. Complete PCB layout.
9. Perform a PCB design review.
10. Generate manufacturing outputs.
11. Assemble and complete board bring-up.
12. Store test results under `testing/`.

## Sensor Status

| Sensor / Subsystem | Function | Interface | Owner | Schematic | Integrated | Footprint Verified | Tested |
|---|---|---|---|---|---|---|---|
| BMP581 | Barometric Pressure / Temperature | SPI | Leziga Beage | Present | No | No | No |
| Additional Sensor | TBD | SPI | TBD | Not Started | No | N/A | No |
| Power | Power Distribution | Power | TBD | Not Started | No | N/A | No |

## Communication Architecture

SPI is the board-standard sensor interface. Shared bus lines are expected to include SCK, MOSI, and MISO, with a separate chip-select line for each SPI peripheral. Interrupt signals may also be routed separately where required.

## BMP581 References

- Sensor design: [hardware/sensors/bmp581/](hardware/sensors/bmp581/)
- Datasheet notes: [docs/datasheets/BMP581.md](docs/datasheets/BMP581.md)
- Footprint review notes: [libraries/footprints/BMP581/README.md](libraries/footprints/BMP581/README.md)
- Original-source record: [hardware/sensors/bmp581/SOURCE.md](hardware/sensors/bmp581/SOURCE.md)

## Branching

Do not make major hardware changes directly on `main`.

Suggested branch names:

```text
feature/<sensor-name>
feature/power
feature/interfaces
feature/pcb-layout
fix/<short-description>
docs/<short-description>
```

Example:

```bash
git checkout -b feature/bmp581
```

Open a pull request when the circuit is ready for team review.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the team workflow.
