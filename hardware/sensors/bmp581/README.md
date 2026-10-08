# BMP581 Barometric Pressure Sensor

## Device

**Manufacturer:** Bosch Sensortec  
**Part Number:** BMP581  
**Function:** High-resolution barometric pressure and temperature sensing for the avionics sensor board.

## Owner

**Designer:** Leziga Beage  
**Reviewer:** TBD

## Electrical Interface

**Board supply used by this design:** 3.3 V  
**Interface:** I2C design intent  
**Logic level:** 3.3 V

The BMP581 itself supports separate VDD and VDDIO rails. The current sensor-board schematic uses the board's 3.3 V supply.

## Design Files

- `BMP_unit.kicad_sch` — BMP581 sensor schematic
- `BMP_unit.kicad_pro` — KiCad project configuration
- `BMP_unit.kicad_pcb` — PCB file created with the original project; currently contains no completed layout

These files were copied from the `LezBe/BMPunit` repository without altering the source repository.

## Schematic Notes

The design includes the BMP581 sensor, local bypass/decoupling components, I2C support circuitry, and the 3.3 V/GND connections required for the sensor module.

The BMP581 symbol is embedded in the KiCad schematic, so a separate symbol library file is not required to open the schematic.

## Footprint Dependency

The BMP581 symbol in the original schematic references:

`QFN10_BMP581_BOS`

That footprint file was **not committed to the BMPunit repository**, including its current recursive Git tree. Do not manufacture from the design until a footprint has been added and checked against the Bosch landing-pattern drawing.

See:

`../../../libraries/footprints/BMP581/README.md`

## Datasheet

See:

`../../../docs/datasheets/BMP581.md`

## Status

- [x] Part selected
- [x] Datasheet identified
- [x] Schematic present
- [ ] ERC status documented
- [ ] Peer reviewed
- [ ] Integrated into top-level sensor board
- [ ] Footprint committed and verified
- [ ] PCB routed
- [ ] DRC passed
- [ ] Bench tested
