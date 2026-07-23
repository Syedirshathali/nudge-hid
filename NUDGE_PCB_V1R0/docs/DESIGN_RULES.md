# NUDGE — Design Rules

Quick reference for anyone working on this board. Full detail lives in the JSON spec; this is the cheat sheet.

## Naming

- File format: `<name>_V<version>R<revision>` — e.g. `NUDGE_PCB_V1R0`
- Bump revision (R) for fixes on the same version
- Bump version (V) for a new hardware iteration
- Git tracks every rename so history stays visible

## Branding

- Base colors: black `#0D0D0D` / white `#FFFFFF`
- Accent colors (blue/green/red) — accents only, never full backgrounds
- Soldermask: black, silkscreen: white
- LED mode colors: mode 1 = blue, mode 2 = green, mode 3 = red

## Hardware

- MCU: ESP32-C3-MINI-1 (integrated antenna — not the -1U variant)
- 6 keys, 2x3 grid, MX-compatible, 19.05mm pitch
- 1 EC11 rotary encoder + push
- 1 SPDT lever as mode switch
- 6x WS2812B LEDs, one per key
- USB-C + BLE HID

## PCB Rules

- 2 layers, JLCPCB free tier, 1.6mm thickness, 1oz copper
- Min trace width / clearance: 0.2mm
- USB D+/D-: 90Ω diff pair, 0.2mm trace / 0.15mm gap, ≤30mm, no vias, no stubs
- Decoupling: 100nF within 2mm of every IC power pin — no exceptions
- Ground pour on both layers, stitching vias every 10mm
- Board edge clearance: 0.3mm
- ESP32 antenna: zero copper under datasheet keepout (as an Altium Keepout Region), ≥10mm clearance from metal switches

## Schematic Rules

- A4 landscape, 100mil grid
- One net per wire — no unlabeled implicit connections
- Power nets use power port symbols, never bare wires
- No floating pins (unless NoERC + comment explaining why)
- Every part needs: MPN, Manufacturer, Datasheet URL, JLCPCB Part Number, JLCPCB Tier

## Net Naming

- UPPER_SNAKE_CASE, functional not auto-generated
- Examples: `USB_DP`, `KEY1`–`KEY6`, `ENC_A`, `ENC_SW`, `LEVER_1`, `LED_DATA`, `I2C_SDA`

## Sourcing

- Active production parts only — no NRND / EOL / Last-Time-Buy
- JLCPCB Basic tier preferred, then Extended
- Stock minimum: 1000+ at LCSC or 5000+ across Mouser/Digi-Key
- In-stock only — no multi-week lead times
- Default passive package: 0603
- Always verify footprint against the datasheet — never trust the library blindly

## Git Workflow

- `main` = stable, fab-ready only
- `dev` = active work
- Commit prefixes: `[SCH]` `[PCB]` `[LIB]` `[DOC]` `[FAB]`
- Commit after every work session, before closing Altium

## Altium MCP / Agent Rules

- Datasheet before any device claim — never guess pin functions or ratings
- User libraries are read-only — agent may only edit libraries it created itself
- Connectivity checks use netlist tools, never visual renders
- Renders (SVG/screenshots) are for layout review only, not for judging connections

## Current Status (2026-07-23)

- Project renamed and moved into git: `NUDGE_PCB_V1R0/`
- PCB: board outline only, no components placed yet
- Schematic: not yet populated
- Screenshots will be added here once real content exists — a render of an empty board isn't useful documentation
