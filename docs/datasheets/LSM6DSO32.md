# LSM6DSO32 Datasheet and Package References

## Official Device

**Manufacturer:** STMicroelectronics  
**Part:** LSM6DSO32 / LSM6DSO32TR  
**Function:** 6-axis IMU with a 3-axis accelerometer and 3-axis gyroscope

## Official References

Product page:

https://www.st.com/en/mems-and-sensors/lsm6dso32.html

Official datasheet:

https://www.st.com/resource/en/datasheet/lsm6dso32.pdf

## Key Design Information

ST lists the device as an LGA-14 package with a body size of approximately 2.5 mm × 3.0 mm × 0.86 mm.

Relevant board-level features include:

- SPI support on the primary host interface;
- accelerometer ranges up to ±32 g;
- gyroscope ranges up to ±2000 dps;
- analog supply range of 1.71 V to 3.6 V;
- independent I/O supply capability;
- INT1 and INT2 programmable interrupt pins.

## Pin / SPI Mapping

For the primary SPI interface, use the datasheet pin table and connection diagrams as the source of truth.

Typical signal mapping:

| Device Signal | SPI Role |
|---|---|
| SCL | SCK |
| SDA | MOSI / SDI |
| SDO/SA0 | MISO / SDO |
| CS | Chip Select |
| INT1 | Optional interrupt |
| INT2 | Optional interrupt |

## CAD Resources

The official ST product page includes EDA symbol, footprint, and 3D-model resources through supported CAD providers.

Any downloaded footprint must be checked against the ST package drawing and land pattern before use in manufacturing.

## Orientation Requirement

Because this is an inertial sensor, package orientation is a functional design parameter. The PCB design must explicitly document how the device X/Y/Z axes map to the avionics board and airframe coordinate system.
