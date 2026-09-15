## v1.2.2 — 2026-09-15

### New features

- **Multi-link layer colours now show up on the elements they light.** Until now they could only be
  set up in the "Multi-link effects" section, and the rotary or the buttons a multi-link actually
  lights gave no sign of being part of one. The same row now appears in each of those elements'
  effect lists, and editing it in either place changes the one setting — there is no second copy to
  keep in step.
- **A multi-link can be ordered against an element's other effects.** It used to paint underneath
  everything, always, whatever the list said. Now it takes its place in that element's own layer
  order, so it can sit above the effects on the rotary that selects the layer and below them on a
  button it only tints — dragged by the same handle as any other row.
- **Taking a multi-link off an element is no longer a one-way door.** Switching a role off leaves
  the row where it is so you can switch it back on; deleting it removes it from that element alone,
  and you can bring it back from the top of any layer row's effect dropdown.

### Fixes

- **Firmware updates no longer hang part-way.** If a USB transfer stalled, the update simply sat
  there: the progress bar froze where it was, and the wheel could be left half-written — coming
  back reporting that it has no firmware. The flash is now bounded (two minutes of silence, ten
  minutes in total) and a stalled transfer is stopped instead of waited on forever. A stuck update
  also used to switch off LED control, device presence and every settings write for the rest of the
  SimHub session; that no longer happens.
- **A failed update now tells you what to do next.** It says whether the wheel is still in update
  mode (run it again) or has dropped off the bus (unplug it and start over), and it no longer
  retries the flash on a wheel that has already disappeared.
- **Several LED Control panels no longer go stale.** Dropdowns and switches could keep showing an
  old value after the panel refreshed underneath them.
- **Custom themes: the side and front encoders (S1, S2, F1, F2) can no longer be given a colour.**
  They own no LEDs of their own, so colouring one actually repainted the button LEDs — on the wheel
  it looked like the buttons changing colour by themselves. Buttons b1–b10 and all four RS16A
  rotaries are unaffected.

### Improvements

- **Much quieter logging.** With an advanced target mapped, the plugin wrote a trigger-poll line to
  SimHub's log every two seconds, forever; firmware updates wrote every line of the transfer even
  when they succeeded. Neither happens during normal use any more.
- **A failed firmware update writes a single report file** to your own AppData folder — wheel,
  USB id, previous and target firmware, the image it was fetching and the full transcript with
  timestamps — and the dialog tells you where it is. Sending that one file is now enough to
  diagnose a failed flash.


## v1.2.1 — 2026-09-14

*LED Control needs firmware 3.2.0 or newer. On older firmware the tab warns you and stays limited.*

### New features

- **LED Control tab.** Configure the LEDs from a picture of the wheel itself: click a button, a
  rotary or the whole wheel and give it effect layers. The render shows what the wheel will do.
- **Effects.** Static colour (whole element or per LED), button press, rotary position, rotary
  rotation, value display, level bar and status indicators. Stack them as layers, drag them into
  the order you want, switch any of them off on its own.
- **Themes.** Base lighting from Vector, Endurance, Redline, Arctic, Miami or Slipstream, or build
  your own in the theme editor with gradient stops and per-element colours. Effects can follow the
  theme's colours instead of carrying their own.
- **Global effects.** One effect across a group of elements — flags, pit limiter, headlights,
  wipers — configured once and kept in step.
- **Animations.** Whole-wheel Idle, Engine start and Pit limiter sequences, each with its own
  preview button.
- **Brightness.** A master level per device, plus per-group levels.
- **Presets.** Save as many named LED configurations per wheel as you like and switch between them
  from a dropdown. Export and import them as `.peledpreset` files to share a setup. Your wheel now
  ships with a designed default rather than a bare skeleton.
- **Profile control.** Instead of driving the wheel over USB, the plugin can publish the colours it
  would have sent and let a SimHub LED profile light the wheel from them. Use *Configure → Export
  LED profile* to generate the profile, then load it in SimHub under the device's LEDs page with
  the individual-LED profile mode set to Combined. Direct control over USB stays the default.
- **Layout variants.** A wheel authored in more than one form (PGT Vector and PGT Limited) offers a
  Layout picker, and the render follows your choice.
- The whole tab works with the wheel unplugged — layouts, themes and presets can all be edited
  offline.
- The **PGT** now shows its own picture on the firmware update card instead of the generic image.


## v1.1.5 — 2026-08-24

### Fixes
- Fixed a clutch bite-point problem: if the wheel finished connecting a moment after SimHub started (or after a reconnect / power cycle), 
the plugin could briefly push a bite point of 0 to the wheel before it had read the real value. In master-slave clutch mode that left one clutch paddle inactive ("one clutch not working"),
and saving could make it stick. The plugin now waits until it has read the real value from the wheel before sending, and backs off after a failed send instead of retrying continuously.

### Diagnostics
- Added optional diagnostic logging (off by default) to help investigate clutch issues. It only writes to the SimHub log when explicitly enabled and does not change how the plugin or the clutch behaves.

## v1.1.3 (beta) — 2026-07-31

### Fixes
- Clutch bite point no longer resets to 0 after a power cycle in combined dual clutch. The plugin was reading and caching a mode-gated 0 from the device during (re)connect, and a later Save then persisted it; 
the bite value is now read from the per-preset data that is always valid.

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
