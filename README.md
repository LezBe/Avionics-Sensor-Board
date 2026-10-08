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
│   │   ├── lsm6dso32/           # LSM6DSO32 IMU design/documentation
│   │   └── _template/           # Template for future sensor modules
│   ├── power/
│   ├── communications/
│   └── sensor_board/
├── libraries/
│   └── footprints/
│       └── LSM6DSO32/
├── docs/
│   ├── architecture/
│   ├── requirements/
│   ├── datasheets/
│   │   └── LSM6DSO32.md
│   └── design_reviews/
├── manufacturing/
├── testing/
└── firmware/
```

## Current Sensor Design

### LSM6DSO32 6-Axis IMU

The LSM6DSO32 is planned as the board's inertial sensor, providing 3-axis acceleration and 3-axis angular-rate measurements.

This branch contains design documentation, official ST references, SPI integration requirements, and footprint-review guidance. A KiCad schematic has not yet been created or imported.

See [hardware/sensors/lsm6dso32/README.md](hardware/sensors/lsm6dso32/README.md).

## Communication Architecture

SPI is the board-standard sensor interface.

Shared bus lines are expected to include:

- `SPI_SCK`
- `SPI_MOSI`
- `SPI_MISO`

Each SPI peripheral should have its own dedicated chip-select signal. Interrupt lines should be routed separately where required.

## Sensor Status

| Sensor / Subsystem | Function | Interface | Owner | Schematic | Integrated | Footprint Verified | Tested |
|---|---|---|---|---|---|---|---|
| LSM6DSO32 | 6-Axis IMU | SPI | TBD | Pending | No | No | No |
| Additional Sensor | TBD | SPI | TBD | Not Started | No | N/A | No |
| Power | Power Distribution | Power | TBD | Not Started | No | N/A | No |

## LSM6DSO32 References

- Sensor documentation: [hardware/sensors/lsm6dso32/](hardware/sensors/lsm6dso32/)
- Datasheet notes: [docs/datasheets/LSM6DSO32.md](docs/datasheets/LSM6DSO32.md)
- Footprint review: [libraries/footprints/LSM6DSO32/README.md](libraries/footprints/LSM6DSO32/README.md)

## Branching

Keep sensor-specific work on feature branches until it is ready for review.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the team workflow.
