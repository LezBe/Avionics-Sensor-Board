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
**Interface:** I2C / SPI / UART / Analog / Other  
**Logic Level:**  

## Signals

| Signal | Direction | Destination | Notes |
|---|---|---|---|
| VCC | Input | Power rail | |
| GND | Power | Ground | |
| | | | |

## Supporting Circuitry

Document decoupling, pull resistors, filtering, level shifting, protection, and external timing components.

## MCU / Flight-Computer Interface

Document intended controller pins, connector pins, bus assignment, or net names.

## Datasheet

Store the datasheet under `docs/datasheets/`.

## Design Decisions

Record important reasoning such as decoupling selection, bus choice, interrupt usage, address configuration, and power-up requirements.

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
