# Sensor Designs

Each sensor should have its own directory.

```text
sensors/
├── bmp390/
│   ├── README.md
│   └── bmp390.kicad_sch
├── imu/
│   ├── README.md
│   └── imu.kicad_sch
└── _template/
    └── README.md
```

Copy `_template/README.md` when adding a new device. Approved circuits should ultimately be integrated into the final project under `hardware/sensor_board/`.
