# Wiring and GPIO Map (Raspberry Pi Pico W)

## Overview
This project uses a **4x4 matrix keypad** as input and **12 discrete LEDs** as output indicators.

- Keys `1`-`8` control blue LEDs individually.
- Key `9` turns ON LEDs 1-8; key `0` turns OFF LEDs 1-8.
- Keys `A`-`D` control red LEDs individually.
- Key `*` turns ON LEDs A-D; key `#` turns OFF LEDs A-D.

## Components (derived from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220Ω current-limiting resistors (series with each LED)
- 4x 1kΩ resistors (pull-up network for keypad rows)
- Jumper wires

## GPIO Pin Mapping

### Keypad Matrix
| Keypad Signal | Pico W GPIO | Role |
|---|---:|---|
| C1 | GP19 | Column input/output scan |
| C2 | GP18 | Column input/output scan |
| C3 | GP17 | Column input/output scan |
| C4 | GP16 | Column input/output scan |
| R1 | GP26 | Row input/output scan |
| R2 | GP22 | Row input/output scan |
| R3 | GP21 | Row input/output scan |
| R4 | GP20 | Row input/output scan |

> The wiring includes 1kΩ pull-ups from R1-R4 to 3V3.

### LEDs
| Logical LED | GPIO |
|---|---:|
| LED1 (key `1`) | GP11 |
| LED2 (key `2`) | GP10 |
| LED3 (key `3`) | GP9 |
| LED4 (key `4`) | GP8 |
| LED5 (key `5`) | GP7 |
| LED6 (key `6`) | GP6 |
| LED7 (key `7`) | GP5 |
| LED8 (key `8`) | GP4 |
| LED9 (key `A`) | GP3 |
| LED10 (key `B`) | GP2 |
| LED11 (key `C`) | GP28 |
| LED12 (key `D`) | GP27 |

All LED cathodes are tied to GND and each anode goes through a 220Ω resistor to a GPIO pin.

## Wokwi notes
- Serial monitor is connected to GP0/GP1 in the provided diagram.
- Use the included keypad + LED mapping exactly to preserve behavior.
