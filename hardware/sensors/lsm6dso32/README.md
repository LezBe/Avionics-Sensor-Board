# LSM6DSO32 6-Axis IMU

## Device

**Manufacturer:** STMicroelectronics  
**Part Number:** LSM6DSO32 / LSM6DSO32TR  
**Function:** 6-axis inertial measurement unit with a 3-axis accelerometer and 3-axis gyroscope.

## Owner

**Designer:** TBD  
**Reviewer:** TBD

## Electrical Interface

**Planned board supply:** 3.3 V  
**Interface:** SPI  
**Logic level:** 3.3 V design intent

ST specifies an analog supply range of 1.71 V to 3.6 V and supports an independent I/O supply. For this board, the intended implementation is to use the avionics board's 3.3 V logic/power domain unless the final power architecture requires otherwise.

## SPI Signals

| LSM6DSO32 Signal | SPI Function | Notes |
|---|---|---|
| SCL | SCK / SPI clock | Shared SPI clock |
| SDA | MOSI / SDI | Data from MCU to IMU |
| SDO/SA0 | MISO / SDO | Data from IMU to MCU |
| CS | Chip select | Dedicated LSM6DSO32 chip-select line |
| INT1 | Interrupt 1 | Optional dedicated GPIO to MCU |
| INT2 | Interrupt 2 | Optional dedicated GPIO to MCU |

The sensor board uses SPI as the standard sensor interface. SCK, MOSI, and MISO may be shared with other SPI sensors; the LSM6DSO32 must have its own chip-select signal.

## Device Capabilities

- 3-axis accelerometer: ±4 / ±8 / ±16 / ±32 g
- 3-axis gyroscope: ±125 / ±250 / ±500 / ±1000 / ±2000 dps
- Embedded temperature sensor
- FIFO up to 9 kB
- Programmable interrupt/event functions

## Design Files

No KiCad schematic has been committed for this sensor yet.

When the design is created, place its files in this directory, for example:

```text
hardware/sensors/lsm6dso32/
├── LSM6DSO32.kicad_sch
├── LSM6DSO32.kicad_pro
├── README.md
└── SOURCE.md        # only if imported from another design source
```

Do not add a placeholder schematic that has not been reviewed.

## Recommended Supporting Circuitry

Confirm all final values against the ST datasheet before schematic review.

At minimum, review:

- local VDD decoupling;
- local VDDIO decoupling;
- CS default state during MCU reset/startup;
- SPI signal integrity and routing;
- use of INT1 and/or INT2;
- unused/NC pin handling;
- sensor orientation on the PCB.

## Footprint Dependency

The LSM6DSO32 uses an LGA-14 package approximately 2.5 mm × 3.0 mm × 0.86 mm.

See:

`../../../libraries/footprints/LSM6DSO32/README.md`

The footprint must be verified against ST's package and recommended land-pattern documentation before fabrication.

## Datasheet

See:

`../../../docs/datasheets/LSM6DSO32.md`

## Integration Notes

Before top-level integration:

- assign a dedicated `LSM6DSO32_CS` signal;
- confirm which STM32 SPI peripheral will be used;
- confirm SPI mode and maximum clock rate from the datasheet/firmware design;
- decide whether INT1, INT2, or both are required;
- establish the physical sensor orientation relative to the vehicle/airframe coordinate system;
- verify the footprint and package orientation;
- complete ERC and peer review.

## Status

- [x] Part selected
- [x] Datasheet identified
- [x] Communication interface selected: SPI
- [ ] Schematic created
- [ ] ERC passed
- [ ] Peer reviewed
- [ ] Integrated into top-level sensor board
- [ ] Footprint committed and verified
- [ ] PCB routed
- [ ] DRC passed
- [ ] Bench tested
