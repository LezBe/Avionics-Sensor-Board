# Sensor Module Template

## Device

**Manufacturer:**  
**Part Number:**  
**Function:**  

## Owner

**Designer:**  
**Reviewer:**  

## Electrical Interface

**Supply Voltage:**  
**Typical Current:**  
**Interface:** SPI (board standard) / Other  
**Logic Level:**  

## SPI Signals

If the device uses the board-standard SPI interface, document:

| Signal | Device Pin | Shared / Dedicated | Notes |
|---|---|---|---|
| SCK | | Shared | |
| MOSI | | Shared | |
| MISO | | Shared | |
| CS | | Dedicated | |
| INT | | Dedicated if used | |

## Signals

Document any additional power, reset, enable, interrupt, analog, or auxiliary signals.

## Supporting Circuitry

Document decoupling, pull resistors, filtering, level shifting, protection, and external timing components.

## MCU / Flight-Computer Interface

Document intended controller pins, SPI bus assignment, chip-select assignment, connector pins, and net names.

## Datasheet

Store the datasheet under `docs/datasheets/`.

## Design Decisions

Record important reasoning such as decoupling selection, SPI mode/timing, chip-select behavior, interrupt usage, and power-up requirements.

## Status

- [ ] Part selected
- [ ] Datasheet reviewed
- [ ] Schematic complete
- [ ] ERC passed
- [ ] Peer reviewed
- [ ] Integrated into top-level schematic
- [ ] Footprint verified
- [ ] PCB routed
- [ ] DRC passed
- [ ] Bench tested
