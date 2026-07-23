# NUDGE

6 keys. 1 lever. 1 knob. Fully open-source.

Board 1 of a planned 10-board open-source hardware library.

## What it is

- Compact HID macropad
- 6 keys (2x3 grid, MX-compatible)
- 1 rotary encoder (EC11) with push
- 1 lever acting as a 3-position mode switch
- Per-key RGB (WS2812B)
- USB-C wired HID + BLE HID

## Hardware summary

| | |
|---|---|
| MCU | ESP32-C3-MINI-1 (integrated antenna) |
| Connectivity | USB-C, BLE (NimBLE) |
| LEDs | 6x WS2812B, single-wire chain |
| PCB | 2-layer, JLCPCB free tier |
| Target BOM cost | €5.60–7.50 |

## Repo structure

```
NUDGE_PCB_V1R0/       Altium project (schematic, PCB, libraries)
  docs/               Design rules and reference docs
eda-agent/            Altium MCP agent tooling used to build this board
```

## Design rules

See [`NUDGE_PCB_V1R0/docs/DESIGN_RULES.md`](NUDGE_PCB_V1R0/docs/DESIGN_RULES.md) for the full cheat sheet — naming, branding, PCB rules, sourcing policy, git workflow.

## Naming convention

Files use `<name>_V<version>R<revision>`, e.g. `NUDGE_PCB_V1R0`.

- Version bump → new hardware iteration
- Revision bump → fix on the same version

## Status

- Project structure set up, design rules locked
- Schematic and PCB layout not yet populated

## Credits

Designed by Irshath Ali Syed (IAS) — [@designwithirshath](https://www.linkedin.com/in/irshath-ali-syed/)

## License

Open-source hardware — license to be added.
