# Communications

The avionics sensor board uses SPI as the standard sensor communication interface.

## Shared SPI Bus

The common SPI bus should use:

- `SPI_SCK` — serial clock from the STM32 / flight computer
- `SPI_MOSI` — controller-to-sensor data
- `SPI_MISO` — sensor-to-controller data

Each SPI peripheral should have its own chip-select signal, for example:

- `BMP581_CS`
- `IMU_CS`
- `SENSOR3_CS`

Interrupt outputs should use dedicated GPIO signals where needed.

## Design Guidance

When adding a sensor:

1. Confirm that it supports SPI.
2. Verify its required SPI mode and maximum clock frequency.
3. Connect it to the shared SCK, MOSI, and MISO nets.
4. Assign a unique chip-select net.
5. Route any required interrupt output separately.
6. Document the MCU pin assignment in the interface-control document.

Store any shared SPI buffering, level shifting, protection, or connector circuitry in this directory.
