# Firmware Architecture

## Design intent
The firmware is event-driven and intentionally simple:
1. Initialize all LED pins as outputs and force them LOW.
2. Poll keypad for a pressed key in each loop iteration.
3. Apply a `switch` action map from key value to LED state change.
4. Delay 10ms for basic debounce pacing.

## Source layout
- `src/main.cpp`: Entire application logic (unchanged behavior from provided source).
- `docs/wiring.md`: Electrical mapping and GPIO allocation.
- `README.md`: Build/run guidance for Wokwi and hardware.

## Module breakdown
- **Pin configuration data**
  - `ledPins[]`, `rowPins[]`, `colPins[]` define static hardware mapping.
- **Keypad interface**
  - `Keypad keypad = Keypad(makeKeymap(...))` manages matrix scanning.
- **Initialization (`setup`)**
  - Loop over all LED pins → `pinMode(..., OUTPUT)` and `LOW`.
- **Main loop (`loop`)**
  - `getKey()` fetches active key or `NO_KEY`.
  - `switch` maps commands to single-pin writes or grouped loops.

## Behavioral mapping summary
- `1..8` → turns on one of LED1..LED8.
- `9` / `0` → all ON / all OFF for LED1..LED8.
- `A..D` → turns on one of LED9..LED12.
- `*` / `#` → all ON / all OFF for LED9..LED12.

## Assumptions documented
- The provided code is Arduino-style C++ for RP2040 toolchains that support Arduino APIs.
- No Wi-Fi functionality is used even though hardware target is Pico W.
