# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W project that reads a 4x4 matrix keypad and controls 12 LEDs using direct key-to-output mappings.

## Features
- 4x4 keypad input scanning via `Keypad` library.
- 12 GPIO-controlled LEDs with grouped actions.
- Deterministic behavior with no network/Wi-Fi dependency.
- Wokwi-compatible wiring and pin map documentation.

## Repository Structure (C/C++ variant)

```text
.
├── CMakeLists.txt
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Firmware Behavior
- `1..8`: turn on corresponding blue LED.
- `9`: turn on LEDs 1..8.
- `0`: turn off LEDs 1..8.
- `A..D`: turn on corresponding red LED.
- `*`: turn on LEDs A..D.
- `#`: turn off LEDs A..D.

## Hardware Bill of Materials
- Raspberry Pi Pico W (RP2040)
- 4x4 membrane keypad
- 12x LEDs
- 12x 220Ω resistors
- 4x 1kΩ resistors (row pull-ups)
- Jumper wires / breadboard

See full pin mapping in [`docs/wiring.md`](docs/wiring.md).

## Run in Wokwi
1. Create/open a Raspberry Pi Pico project in Wokwi.
2. Paste the provided `diagram.json` into Wokwi's diagram editor.
3. Use `src/main.cpp` as your sketch logic in an Arduino-compatible RP2040 environment.
4. Start simulation and use the keypad to trigger LEDs.

## Run on Real Hardware (Pico W)

### Option A: Arduino IDE (recommended for this exact code)
This code uses Arduino APIs (`Keypad`, `pinMode`, `digitalWrite`, `delay`), so Arduino IDE with an RP2040 core is the most direct path.

1. Install Arduino IDE and add an RP2040 board package.
2. Install `Keypad` library from Library Manager.
3. Select **Raspberry Pi Pico W** as board.
4. Connect hardware exactly as in `docs/wiring.md`.
5. Build/upload and test each keypad key.

### Option B: Pico SDK project scaffold
`CMakeLists.txt` is included to provide a Pico SDK-aligned repository layout.

> Note: `src/main.cpp` is still Arduino-style and requires adaptation/wrappers to compile directly with raw Pico SDK.

## Wi-Fi/Credentials
- No Wi-Fi is used in this firmware.
- No credentials are required or stored.

## Documentation
- Wiring details: [`docs/wiring.md`](docs/wiring.md)
- Architecture details: [`docs/architecture.md`](docs/architecture.md)
