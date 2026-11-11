# Miele G 7765 display

External status display for a **Miele G 7765 SCVi XXL** dishwasher, built with **ESPHome + LVGL** on a **Waveshare ESP32-S3-Touch-LCD-5B (SKU 28151, 1024×600)** and integrated with Home Assistant.

The project is intended as a practical companion display for a fully integrated dishwasher where the machine's own front-panel information is not visible during normal use.

## Current status

The ESPHome configuration in `esphome/oppvaskmaskin-display.yaml` is the current verified baseline and is in daily use.

Main functions:

- remaining time and selected program
- current program phase
- elapsed-time/progress calculation
- PowerDisk and rinse-aid levels
- Home Assistant connection state
- door, warning and fault banner
- touch-controlled manual screen on/off
- automatic display policy that avoids waking the screen for warnings, faults or a Home Assistant reconnect
- controlled behaviour if Home Assistant becomes unavailable

## Hardware

- Miele G 7765 SCVi XXL
- Waveshare ESP32-S3-Touch-LCD-5B
- Waveshare SKU 28151
- 5-inch 1024×600 RGB display
- GT911 touch controller
- CH422G I/O expander
- 3D-printed enclosure: [HexCase Waveshare 5" ESP32 Case on MakerWorld](https://makerworld.com/en/models/3010625-hexcase-waveshare-5-esp32-case?from=search#profileId-3381269)

The current enclosure is used as a free-standing construction.

### Fasteners used/planned

- display: M2.5 machine screws, no nuts
- power connector: M1.6 machine screws with M1.6 nuts

## Repository layout

```text
.
├── esphome/
│   ├── oppvaskmaskin-display.yaml
│   └── secrets.example.yaml
├── docs/
│   ├── hardware.md
│   └── home-assistant.md
├── .gitignore
├── LICENSE
└── README.md
```

## Installation

1. Copy `esphome/secrets.example.yaml` to `secrets.yaml`.
2. Fill in Wi-Fi credentials.
3. Verify that the Home Assistant entities listed in [docs/home-assistant.md](docs/home-assistant.md) exist with matching entity IDs.
4. Compile and install `esphome/oppvaskmaskin-display.yaml` with ESPHome.
5. Add the ESPHome device to Home Assistant.

The configuration intentionally keeps credentials outside the tracked YAML file.

## Display policy

The display is intentionally conservative about waking the screen:

- real dishwasher activity may wake the display
- a completed program is shown temporarily
- OFF/READY is shown briefly after an actual status transition
- warnings and faults do **not** wake a dark display
- a Home Assistant restart/reconnect does **not** wake a dark display
- if Home Assistant disappears while the display is already lit, the screen may remain on for up to 15 minutes
- touching the glass toggles the display manually

See the ESPHome YAML for the authoritative implementation.

## Versioning and releases

ESP32/ESPHome software releases use date-based version tags:

```text
vYYYY.MM.DD
```

If more than one software release is needed on the same date, append a numeric revision:

```text
vYYYY.MM.DD-2
vYYYY.MM.DD-3
```

Release notes should state whether a release changes display behaviour, Home Assistant entity requirements, hardware assumptions or only documentation.

## License

MIT. See [LICENSE](LICENSE).
