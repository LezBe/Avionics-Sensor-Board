# Contributing

This repository is intended for collaborative avionics hardware development.

## Basic Workflow

1. Pull the newest version of `main`.
2. Create a branch for your work.
3. Edit only the files required for your sensor or subsystem whenever possible.
4. Commit meaningful checkpoints.
5. Push the branch.
6. Open a pull request.
7. Have another team member review the schematic or design.
8. Merge after review.

## Branch Naming

```text
feature/<sensor-name>
feature/power
feature/interfaces
feature/pcb-layout
fix/<description>
docs/<description>
```

## KiCad Collaboration Rules

- Use the same major KiCad version across the team.
- Pull before beginning work.
- Avoid having two people edit the same `.kicad_sch` or `.kicad_pcb` file simultaneously.
- Prefer separate hierarchical sheets for major sensor and subsystem blocks.
- Do not commit `.history/`, autosave, lock, or local preference files.
- Commit shared symbols and footprints if the design depends on them.
- Run ERC before requesting schematic review.
- Run DRC before requesting PCB review.

## Sensor Module Documentation

Every sensor folder should include a `README.md` based on `hardware/sensors/_template/README.md`.

Document the part number, function, supply voltage, interface, pull-ups/pull-downs, decoupling, interrupts, MCU signals, datasheet, owner, status, and important design decisions.
