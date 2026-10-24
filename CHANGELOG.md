# Changelog

## Own repository + new case (October 2026)

- The LCD version moved out of
  [Pico-Latency-Tester](https://github.com/Casio-Byte/Pico-Latency-Tester) into
  this repository, with everything it needs (USB library included).
- New case: `case/Pico_Latency_Tester_LCD.stl` - front screen window, button
  cap, sensor hole in the back, strap loops. Also split into `case_only.stl` and
  `button_cap_only.stl`. The earlier OpenSCAD case is kept in `case/parametric/`.

## v3.1 (October 2026)

Hardware: Waveshare RP2040-LCD-0.96 + Adafruit ALS-PT19 + one 6x6 mm button.

| From | To |
|---|---|
| ALS-PT19 `+` / `-` / `OUT` | 3V3 (pin 36) / AGND (pin 33) / GP26 (pin 31) |
| Button | GP16 (pin 21) and GND (pin 23) - soldered straight onto the board |

- **Button moved** from GP15 (pin 20) to GP16 (pin 21), with GND on pin 23.
  Maintenance mode (hold the button while plugging in) follows it.
- **Manual test removed.**
- **Flicker test fixed:** it ran the board out of memory analysing the 16,000
  samples and crashed, most visibly when no flicker was found. It now uses a
  fixed buffer made at start-up and a small histogram instead of a sorted
  copy. It also has a countdown, holds the mouse button so the target turns
  white, and reports "TOO DARK" when the sensor sees no light.
- **Countdown before every test** (run, response scope, flicker), and a click
  wherever the test needs the screen to change.
- **Sensor view** redraws continuously; a press sends a click so you can watch
  the reading jump; hold goes back.
- **History:** browse every run, open one for median / average / spread / 95th
  / fails, and *Clear history* (hold again to confirm).
- **Trigger defaults to Small** (the most sensitive fixed trigger). Boards
  with older settings switch once; later choices are kept.
- An out-of-memory error in any menu item now shows a message instead of
  crashing.
- **3D-printed case** (now `case/parametric/`): screen window and button hole in
  the lid, sensor pocket under the board looking out of the back, board on a
  ledge with gaps for solder joints, push-fit lid, USB-C slot.
- Simulator covers 84 steps, including the flicker test on flickering, steady
  and dark screens, sensor-view clicks and clearing history.

## v3.0

First version without a PC app: one-button menus, automatic runs with
calibration, results pages (median, histogram, every click, detail), response
scope, flicker test, sensor view, history, settings saved on the board.

---

Tested and confirmed working on real hardware.
