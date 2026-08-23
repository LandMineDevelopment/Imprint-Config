# Imprint Configuration

Custom ZMK firmware for a wireless Cyboard Imprint with a function row and
full bottom row.

## Studio-enabled branch

The `studio-migration` branch preserves `config/imprint.keymap` as the firmware
default while enabling live edits through [Cyboard
Studio](https://studio.cyboard.digital) on the left half. Studio changes are
stored separately in the keyboard's flash, survive later firmware flashes,
and override the source defaults until the keyboard settings are reset.

The firmware stack is deliberately pinned to ZMK `v0.3.0` and Cyboard's
`zmk-keyboards` `v2026.07` release. Do not switch either dependency back to a
moving `main` branch without also migrating and testing the physical layout.

## Build and test

1. Push the branch and wait for the GitHub Actions `build` job to pass.
2. Download and unzip the firmware artifact from that workflow run.
3. Connect the left half by USB, double-tap its reset button, and copy
   `imprint_left-assimilator-bt-zmk.uf2` to the `ASSIMILATOR` drive.
4. Confirm the existing layout, combos, layers, and trackball behavior before
   flashing the right half.
5. Flash `imprint_right-assimilator-bt-zmk.uf2` to the right half using the
   same reset procedure.
6. Connect the left half over USB in Chrome or Edge, open Cyboard Studio, and
   hold the physical A and F key positions for three seconds to unlock it.

Keep a known-good artifact from `main` available for rollback. If the halves
stop pairing, follow Cyboard's [firmware update and settings-reset
guidance](https://docs.cyboard.digital/studio-firmware-update).

## Workflow boundary

Use firmware built from this repository, not Cyboard's generic Studio firmware
release, when preserving this source keymap. The generic release starts from
Cyboard's standard layout. Studio cannot currently import changes from or
export changes to `config/imprint.keymap`.
