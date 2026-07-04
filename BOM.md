# BOM — electronics prototype (ESP32 → Tarang simulator)

Sourced on robu.in, 2026-07-04. Everything panel-mounts into the printed
parts with no rework; total ≈ **₹470** plus the ESP32 you already have.

| # | Part | Qty | Price (incl. GST) | Source |
|---|---|---|---|---|
| 1 | **LCD2004 20×4 LCD with I2C backpack** (SKU 26300, 98×60×14, addr 0x27, 5 V) | 1 | ₹274 | https://robu.in/product/lcd-2004-i2c/ |
| 2 | **Hongyan EC11H 7CE15P1ZD15F7** rotary encoder w/ push switch, 15 mm D-shaft (SKU R185172) — *buy the 15 mm shaft variant, not ZD20* | 3 | ₹55 ea | https://robu.in/?s=EC11H |
| 3 | **MTS-102-A2T** miniature toggle ON-ON, M6 bushing (SKU R132370) — R.Tx/R.Rx position | 1 | ₹26 | https://robu.in/?s=MTS-102 |
| 4 | 3.5 mm panel-mount audio jack (H/S position — PTT/headset) | 1 | ~₹20 | https://robu.in/?s=3.5mm+jack+panel+mount |
| 5 | ESP32 DevKit (any 30/38-pin) | 1 | on hand | — |
| 6 | Jumper wires / heat-shrink / 2 small zip ties | — | ~₹50 | — |

Alternative for #2: "Green Rotary Encoder Module" (KY-040-style, ₹59) — same
EC11 core on a breakout PCB with header pins; mounts through the same Ø7.2
panel hole.

## How it goes together

- **LCD2004** drops behind the panel aperture; the printed `lcd_carrier`
  presses it flat (4 posts into the blind holes around the aperture). The
  I2C backpack pokes through the carrier window.
- **Encoders** mount in the three Ø7.2 knob holes, M7 nut on the front (it
  hides inside the knob's pocket). The printed wing knobs push straight onto
  the D-shafts. Anti-rotation lug drops into the blind pocket above or below
  the hole — if your batch's lug doesn't line up, just snip it.
- **Toggle / jack** use their own nuts in the Ø6.2 holes.
- **ESP32** zip-ties to the `esp32_tray`, which slides into the rails on the
  case floor; USB exits the Ø10 hole in the floor rear corner. The battery
  box backstops the tray when clicked on.
- No electronics? Click the three `boss_adapter` pieces into the encoder
  holes instead — knobs press on and stay turnable (the adapter's barb ring
  spins in the round hole).

## Suggested ESP32 pin map (prototype)

| Signal | Pin |
|---|---|
| LCD SDA / SCL (I2C 0x27) | GPIO 21 / 22 |
| FUNCTION encoder A/B/SW | GPIO 32 / 33 / 25 |
| CHANNEL encoder A/B/SW | GPIO 26 / 27 / 14 |
| VOLUME encoder A/B/SW | GPIO 12 / 13 / 15 |
| R.Tx/R.Rx toggle | GPIO 4 |
| PTT (3.5 mm jack sleeve switch) | GPIO 5 |

Talk to the simulator over Wi-Fi (ESP32 → backend REST/WS on the LAN) or USB
serial — the radio's WS verbs (`radio.freq`, `radio.mode`, PTT audio start)
map 1:1 onto encoder turns and the PTT line.
