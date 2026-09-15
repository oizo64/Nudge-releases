# Nudge releases

Firmware packages for **Nudge**, an ESP32 board that acts as a Bluetooth mouse and gently nudges the cursor so connected computers stay awake.

The source code is kept in a private repository. This repository only holds the released firmware.

## Installing an update

Open the board's web panel and go to **Settings**. Your browser checks this repository and shows **Install X.Y.Z** when a newer version exists. It downloads the package and sends it to the board, which verifies and installs it.

Manual install: download `vX.Y.Z/nudge.mmu` and upload it in **Settings → Firmware update**.

## Layout

| Path | Purpose |
|---|---|
| `latest.txt` | Latest version number and package size, read by the panel |
| `vX.Y.Z/nudge.mmu` | Signed and encrypted firmware package for that version |

Every version is also tagged `vX.Y.Z`.

## Security

Every package is signed with a private RSA key that never leaves the author's computer. A board verifies the signature before it switches to the new firmware and rejects anything else, so a modified or foreign package cannot be installed. The firmware image is also encrypted.
