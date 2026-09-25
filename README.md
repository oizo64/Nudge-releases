# Nudge releases

Firmware packages for **Nudge**, an ESP32 or ESP32-C3 board that acts as a Bluetooth mouse and gently nudges the cursor so connected computers stay awake.

The source code is kept in a private repository. This repository only holds the released firmware.

## Installing an update

Open the board's web panel and go to **Settings**. Your browser checks this repository and shows **Install X.Y.Z** when a newer version exists. It downloads the package and sends it to the board, which verifies and installs it.

Manual install: download the package for your board - `<board>/vX.Y.Z/nudge.mmu`, for example the newest folder under `esp32/` - and upload it in **Settings → Firmware update**. The board reads the chip id from the image header, so a package built for a different board is refused instead of bricking it.

## Layout

One folder per board, each with its own versions and its own `latest.txt`:

| Path | Purpose |
|---|---|
| `<board>/latest.txt` | Latest version number and package size for that board |
| `<board>/vX.Y.Z/nudge.mmu` | Signed and encrypted package for that board and version |

Boards published so far: `esp32` and `esp32c3`. A board only ever reads its own folder, so the same
version number can mean different firmware on different boards, and a package can never be installed
on the wrong one. Releases are tagged `<board>-vX.Y.Z`.

## Security

Every package is signed with a private RSA key that never leaves the author's computer. A board verifies the signature before it switches to the new firmware and rejects anything else, so a modified or foreign package cannot be installed. The firmware image is also encrypted.
