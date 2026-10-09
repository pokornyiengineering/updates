## v3.3.0 — 2026-10-09

### New features

* **MCP ButtonBox16: first release.**
* **Supply voltage readable from the PC.**

### Fixes

* **Inputs no longer stop on long USB cables while the LEDs keep working.**
* **MCP MultiBox, HYP-R and TGR-H LED current limited.**



## v3.2.7 — 2026-10-06

*MCP MultiBox only.*

### Fixes

* **MCP MultiBox brightness limited.**



## v3.2.6 — 2026-10-01

### New features

* **MCP SideRotaryBox: first release.**

### Fixes

* **Rotary switches read the position printed on the faceplate, and count in the direction they turn.**



## v3.2.4 — 2026-09-28

*Stable, for every device. The 3.2.x line the wheels have been running as 3.2.3-beta is now a
stable release, and the PDU5, the PDU7 and the LED Brows join it. For a wheel already on
3.2.3-beta nothing changes but the version number.*

### New features

* **The PDU5, the PDU7 and the LED Brows run 3.x.** Their first release on this line, with the
whole 3.2.x feature set. A PDU keeps the Display ID it was given on 2.5.x.
* **MCP MultiBox: a factory multi-link.** On a fresh settings page instance 0 comes set up —
encoder push switches the layer, the rotary steps it up and down. It is never written over a
configuration you have made yourself.

### Fixes

* **MCP MultiBox: the startup animation plays on the flag matrix only.** It was lighting the eight
encoder-ring LEDs as well.



## v3.2.3-beta — 2026-09-16

*Pre-release, every wheel except RALLY (already on 3.2.3). Not hardware-tested per device.*

Brings these wheels onto the 3.2.x line. The 3.2.3 fix itself was RALLY-only; what is new
here is everything released since 3.1.2.



## v3.2.3 — 2026-09-15

*RALLY only.*

### Fixes

* Mouse mode moved the cursor left when you pushed right, and right when you pushed left.



## v3.2.2 — 2026-09-15

*PGT only.*

### Fixes

* Rotaries 7 and 8 reported their absolute position half a turn off. The 3.1.10 mounting
relabel is now set per rotary instead of device-wide.



## v3.2.1 — 2026-09-14

*PGT only. Other wheels remain on 3.1.2.*

### New features

* Multi-link raised from 1 to 4 instances, each supporting up to 20 layers.

### Fixes

* Restores the mouse-mode scroll wheel and the 4th pedal axis (Slider = bite point), both of
which were present in 3.1.10 but missing from the unreleased 3.2.0 build.

Everything from 3.1.8 and 3.1.10 is retained unchanged: launch control, brake magic \& hold,
split-pedal clutch axes, bite-point adjust, advanced buttons, mouse emulation, and the RS16A
position relabel. Coming from 3.1.10, the only behavioural change is multi-link.



## v3.1.10 — 2026-08-15

*PGT only.*

### Fixes

* RS16A absolute rotaries relabelled by +6 (mod 12): physical detent 1 now reports position 7,
7 reports 1, and so on. Applied at the decode source, so the plugin position number, the game
position one-hot and the multi-link slot all agree.



## v3.1.8 — 2026-08-14

*PGT only.*

### New features

* Full feature parity for PGT: launch control, brake magic \& hold, split-pedal clutch axes,
bite-point adjust, advanced buttons, mouse emulation, and a 4th analog axis.
* Improved encoder detent decoder (1:1 side \& funky rotaries).

### Fixes

* USB input-endpoint stall recovery.

## v3.1.7-beta — 2026-08-22

*Pre-release, all wheels.*

### New features

* Plugin-exclusive LED RGB commands.

### Fixes

* USB HID input-endpoint stall auto-recovery: the wheel detects a wedged input endpoint and
re-enumerates itself instead of going silent until a replug.
* Improved encoder detent decoder — fixes skipped detents on side and funky rotaries.

## v3.1.2 — 2026-07-20

### Fixes

* Multi-link one-hot position report fix



## v3.1.1 — 2026-07-20

### New features

* Force-set of an input (used by Advanced target setting).
* Active layer report option for multi-link (one-hot input).
* Instance-based advanced input feature.
* Adjustable double-shift protection.
* Added full 480-bit RAW and DERIVED streams.
* Multi-link now supports up to 20 layers (previously 12).

### Fixes

* ADC clock source.
* Fixed bite point lost in button mode.

## v3.0.36 — 2026-07-11

### Fixes

* Fixed flash save scheduling.
* Fixed analog calibration (reverted to standard method).

## v3.0.34-beta — 2026-07-10

### Fixes

* Fixed analog calibration (smart calibration reverted to standard method).

## v3.0.33 — 2026-07-11

### Fixes

* Fixes phantom button presses when position rotaries and multi-links together exceed the
128-button report.

## v3.0.31 — 2026-07-10

* Initial SimEngine 3 release.

