## v1.1.5 — 2026-08-24

### Fixes
- Fixed a clutch bite-point problem: if the wheel finished connecting a moment after SimHub started (or after a reconnect / power cycle), the plugin could briefly push a bite point of 0 to the wheel before it had read the real value. In master-slave clutch mode that left one clutch paddle inactive ("one clutch not working"), and saving could make it stick. The plugin now waits until it has read the real value from the wheel before sending, and backs off after a failed send instead of retrying continuously.

### Diagnostics
- Added optional diagnostic logging (off by default) to help investigate clutch issues. It only writes to the SimHub log when explicitly enabled and does not change how the plugin or the clutch behaves.

## v1.1.3 (beta) — 2026-07-31

### Fixes
- Clutch bite point no longer resets to 0 after a power cycle in combined dual clutch. The plugin was reading and caching a mode-gated 0 from the device during (re)connect, and a later Save then persisted it; the bite value is now read from the per-preset data that is always valid.

### Improvements
- Update checks now run once at startup instead of repeatedly. Each section (firmware / plugin / dash) has a "refresh" link on the Update tab to re-check on demand. This also stops the version-check log spam.

## v1.1.2 — 2026-07-20

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
- Multi-link layer limit raised to 20.

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
