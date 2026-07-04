# DFM report — STARS-V Mk II replica on Creality K2 Plus Combo

Target machine: **Creality K2 Plus Combo** — 350 × 350 × 350 mm bed, stock
**0.4 mm** nozzle, 0.2 mm layers, CFS multi-colour unit. All numbers below are
checked against that setup.

## Plate fit (350 × 350 bed, 3 plates)

| Plate | Footprint | Max height | Status |
|---|---|---|---|
| PLATE1_GREEN | 273 × 267 mm | 144 mm | ✅ fits, 77/83 mm margin |
| PLATE2_BLACK | 299 × 152 mm | 26 mm | ✅ fits |
| PLATE3_PANEL_2COLOUR | 260 × 150 mm | 3.6 mm | ✅ fits, 2 filament swaps (Z 3.0 / 3.6) |

Because the K2 Plus **Combo** has the CFS, you can also skip the 3-plate
workflow entirely and print `STARSV-MK2_PRINT_multicolour.3mf` in one go —
the 3-plate split just avoids purge waste.

## 0.4 mm nozzle feature audit

| Feature | Size | Rule of thumb | Verdict |
|---|---|---|---|
| Case / battery walls | 3.5–4.0 | ≥ 0.8 | ✅ |
| Panel plate | 3.0 | ≥ 1.2 structural | ✅ |
| Raised markings | 0.6 tall = 3 layers | ≥ 2 layers | ✅ |
| Smallest text (ring labels) | 2.3 mm cap height | stroke ≥ 0.45 | ✅ *(bumped from 2.0 this revision)* |
| Keymat base | 0.45 | ≥ 2 layers | ✅ |
| Keymat retaining ridge | 0.25 | ≥ 1 layer | ✅ *(fixed — was 0.12, sub-layer)* |
| Snap-finger walls (connectors) | 1.8 | ≥ 1.2 | ✅ |
| Knob crush rib | Ø0.5 | ≥ 0.4 | ✅ (ream lightly if too tight) |
| LCD carrier posts | Ø4.5 × 13.5 | slender | ⚠ print slowly, handle gently |
| Audio connector pins | Ø1.8 × 1.8 | ≥ 1.0 | ✅ enable "slow down for small features" |
| Volume-arc band | Ø2.5 discs overlapped | ≥ 1.0 | ✅ |

**Overhangs / bridges** — no supports needed anywhere:
- Old mushroom-boss flat overhang is **gone** (knobs are D-bore now).
- Cap bump rings: 0.65 mm internal protrusion — fine.
- Knob nut-pocket ceiling: 3.2 mm annular bridge — fine.
- Tray rail lips: horizontal ledge, self-similar every layer — fine.
- USB exit hole (Ø10, horizontal axis): slight top-arc sag, cosmetic only.
- Case-opening groove lip: chamfer-free 0.8 mm step — acceptable at 0.2 layers.

**Brim needed** (small bed contact): all 5 cosmetic connectors, both latches,
the 3 boss adapters, toggle, H/S jack — they stand on their snap posts.

**Material**: PLA everywhere is fine for a display unit. Use PETG for the
knobs + boss adapters if they'll be turned a lot (snap/crush features last
longer).

## Click-to-lock audit (every joint)

| # | Joint | Type | Interference / engagement | Verdict |
|---|---|---|---|---|
| 1 | Panel → case opening | edge ridge in groove | 0.25 mm/side, 0.8 groove | ✅ firm click |
| 2 | Battery box → case | 2 cantilever clips in windows | 1.7 mm barb, 8×5 face | ✅ strong |
| 3 | Latch dummies → battery box | 2 split pins each | 0.35 mm catch | ✅ |
| 4 | Guard bars → front rim | 4 split pins | 0.45 mm catch | ✅ |
| 5 | Caps → connector barrels | bump ring in groove | 0.65 into 0.8 groove | ✅ re-snappable |
| 6 | Connectors → panel | barbed keyed posts | 0.45 past panel back | ✅ anti-rotation keys |
| 7 | Keymat → panel pocket | bow-under ridges | 0.7 mm under-lap | ✅ *(pocket deepened to 0.8)* |
| 8 | LCD tile → aperture | stepped edge barbs | 0.25 mm catch | ✅ *(new clip design)* |
| 9 | Knob → EC11 shaft | D-bore + crush rib | 0.1–0.25 crush | ✅ real encoder drive |
| 10 | Knob → boss adapter stub | same bore, fatter stub | 0.1–0.15 crush | ✅ prop mode |
| 11 | Boss adapter → panel hole | barbed split post in Ø7.2 | 0.45 catch, round hole | ✅ **spins freely → prop knobs stay turnable** |
| 12 | LCD carrier → panel back | 4 press posts in blind holes | 0.15 crush | ✅ |
| 13 | ESP32 tray → case rails | slide channel | 0.2 clearance, battery box backstops | ✅ |

## Electronics fit check (no rescale needed)

The full-size model absorbs the real parts at 1:1 — the 20×4 LCD's viewing
area (76 × 25.5) is within half a millimetre of the real radio's window:

| Component | Mount | Clearance check |
|---|---|---|
| LCD2004 module | aperture 77 × 26.5 + carrier | frame clears keymat pocket & FUNCTION encoder by 6 mm |
| EC11 encoders ×3 | Ø7.2 holes + M7 nut | nut hides inside knob pocket (Ø12.6 × 3.6); blind lug pockets both sides |
| Encoder shaft | ZD15 (15 mm): 12 mm proud | knob bore depth 12.3–14.1 → seats fully. **ZD20 sits 3 mm proud — buy the 15 mm shaft variant** |
| MTS-102 toggle | Ø6.2 hole @ R.Tx/R.Rx | nut clamps 3 mm panel ✅ |
| 3.5 mm jack | Ø6.2 hole @ H/S | PTT / headset input ✅ |
| ESP32 DevKit | slide-in tray on case floor | 1.2 mm clear under VOLUME encoder body; USB exits Ø10 floor hole |

## Changes made in this revision

1. Ring/label text 2.0 → 2.3 mm (0.4-nozzle stroke width).
2. Keymat ridge 0.12 → 0.25 mm + pocket 0.6 → 0.8 mm.
3. LCD pocket → through-aperture + clip-in tile + press-in carrier.
4. Knob snap-boss system → 6 mm D-bore (EC11) + prop-mode boss adapters.
5. Toggle + H/S holes → Ø6.2 for real MTS-102 / 3.5 mm jack.
6. ESP32 tray + case rails + USB exit hole.
