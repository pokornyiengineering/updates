# SimEngine Plugin — Changelog

## v1.1.0-beta — 2026-07-17

### New features
- Advanced target setting (auto-adjusts e.g. brake bias to a selected target): with latch, and press-to-override.
- Active layer report option for multi-link (one-hot input).
- Instance-based advanced input feature.
- Adjustable clutch dead zone.
- Per-channel analog dead zone with sliders in the plugin.
- Versioned updates: selectable versions and a beta option.
- Raw and derived input streams are now accessible through SimHub properties (for third-party implementations).
- Derived inputs (e.g. multi-link output) can now also be used as an input for other features.
- Adjustable double-shift protection.

### Improvements
- Editable numeric entry boxes on every slider — type an exact value instead of dragging.
- UI polish throughout: sectioned layout, per-tab scrolling, tidier fonts and spacing.
- Wide input support: inputs exceeding the 128-input report limit can now be used within the plugin.
- Smaller, faster firmware (link-time optimization) and O(1) input suppression, so heavy configurations no longer bog down the USB stream
- Changelog viewer added

### Fixes
- DFU driver issue fix (Guillemot driver conflict - WinUSB driver force-bind wit PEDfuRepair.exe)
- Game changes no longer stall the plugin and dash.
- Fixed device presence getting stuck in the plugin.
- Fixed multi-link reassignments not reaching the device, and stale multi-link counts on reconnect.
- Analog axis readers now self-heal if setup failed at connect time.

## v1.0.8-beta — 2026-07-11

### New features
- Advanced target setting (preview).

## v1.0.5 — 2026-07-10

### Fixes
- Fixed analog calibration (reverted to standard method).

## v1.0.1 — 2026-07-10

### Fixes
- Fixed smart calibration algorithm for short-throw clutches.

## v1.0.0
- Initial SimEngine 3 release.
