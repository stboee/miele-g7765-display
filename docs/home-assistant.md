# Home Assistant dependencies

The current ESPHome baseline expects these Home Assistant entities.

| Purpose | Entity ID | Type |
|---|---|---|
| Dishwasher status | `sensor.oppvaskmaskin` | text sensor |
| Selected program | `sensor.oppvaskmaskin_program` | text sensor |
| Program phase | `sensor.oppvaskmaskin_programfase` | text sensor |
| Remaining time | `sensor.oppvaskmaskin_gjenvaerende_tid` | numeric sensor |
| Elapsed time | `sensor.oppvaskmaskin_forlopt_tid` | numeric sensor |
| PowerDisk level | `sensor.oppvaskmaskin_powerdisk_niva` | numeric sensor |
| Rinse-aid level | `sensor.oppvaskmaskin_skyllemiddelniva` | numeric sensor |
| Door | `binary_sensor.oppvaskmaskin_dor` | binary sensor |
| Problem | `binary_sensor.oppvaskmaskin_problem` | binary sensor |
| Warning active | `binary_sensor.oppvaskmaskin_varsel_aktivt` | binary sensor |

## Status values used by the display

The current logic explicitly handles these dishwasher states:

- `in_use`
- `pause`
- `programmed`
- `waiting_to_start`
- `program_ended`
- `off`
- `idle`
- `on`
- `failure`

## Program phases used by the display

The current logic maps these program-phase values:

- `pre_dishwash`
- `main_dishwash`
- `interim_rinse`
- `final_rinse`
- `drying`
- `finished`
- `reactivating`
- `rinse`

## Important

The ESPHome YAML is the authoritative source for entity IDs, status handling and display behaviour. This document is a human-readable dependency summary and must be updated if those contracts change.
