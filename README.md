# Avionics Sensor Board

Central hardware repository for the avionics team's multi-sensor PCB.

This repository is organized so team members can develop and review individual sensor circuits independently while maintaining one controlled design for the integrated sensor board.

## Goals

- Consolidate individual sensor designs in one repository
- Keep each sensor circuit modular and easy to review
- Standardize power, communication, and MCU interfaces
- Maintain a controlled integrated KiCad project
- Preserve design decisions, datasheets, manufacturing files, and test results
- Make collaboration and revision history easier through Git and GitHub

## Repository Structure

```text
Avionics-Sensor-Board/
├── hardware/
│   ├── sensors/             # Individual sensor designs
│   ├── power/               # Power regulation/distribution
│   ├── communications/      # Shared buses and communication circuitry
│   └── sensor_board/        # Final integrated KiCad PCB project
├── libraries/               # Shared KiCad symbols, footprints, and 3D models
├── docs/                    # Architecture, requirements, datasheets, reviews
├── manufacturing/           # Gerbers, BOM, pick-and-place, assembly outputs
├── testing/                 # Bring-up procedures and test results
└── firmware/                # Hardware-test firmware and sensor drivers
```

## Recommended Design Flow

1. Develop each sensor circuit in its own folder under `hardware/sensors/`.
2. Document the sensor supply, interface, supporting circuitry, and owner.
3. Run a peer schematic review.
4. Integrate the approved design into `hardware/sensor_board/`.
5. Perform ERC and design-rule checks.
6. Assign and verify footprints.
7. Complete PCB layout.
8. Perform a PCB design review.
9. Generate manufacturing outputs.
10. Assemble and complete board bring-up.
11. Store test results under `testing/`.

## Sensor Status

| Sensor / Subsystem | Function | Interface | Owner | Schematic | Integrated | Tested |
|---|---|---|---|---|---|---|
| Sensor 1 | TBD | TBD | TBD | Not Started | No | No |
| Sensor 2 | TBD | TBD | TBD | Not Started | No | No |
| Power | Power Distribution | Power | TBD | Not Started | No | No |

Update this table as designs are added.

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
git checkout -b feature/bmp390
```

Open a pull request when the circuit is ready for team review.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the team workflow.
