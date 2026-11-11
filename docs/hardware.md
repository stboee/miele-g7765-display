# Hardware

## Display

The project uses a **Waveshare ESP32-S3-Touch-LCD-5B**, SKU **28151**, with a 1024×600 RGB panel.

The ESPHome configuration currently assumes:

- ESP32-S3
- ESP-IDF framework
- octal PSRAM at 80 MHz
- I²C SDA on GPIO8
- I²C SCL on GPIO9
- GT911 touch interrupt on GPIO4
- GT911 reset through CH422G EXIO1
- display backlight through CH422G EXIO2

These values are part of the verified configuration and should not be changed merely for cleanup or abstraction.

## Enclosure

A 3D-printed HexCase is used:

- https://makerworld.com/en/models/3010625-hexcase-waveshare-5-esp32-case?from=search#profileId-3381269

The first installation is a free-standing construction rather than an integrated dishwasher installation.

## Mechanical fasteners

Verified fasteners used for the current build:

| Component | Fastener |
|---|---|
| Display | Black M2.5 × 10 mm machine screw, no nut |
| Power connector | Black M1.6 × 10 mm machine screw + M1.6 nut |
