# Apollo Pi Bootstrap R4 — Pi 4 qualification candidate

Bootstrap R4 adds Raspberry Pi 4 Model B to the clean installer and retains
Raspberry Pi 5 Model B. Use Raspberry Pi OS 64-bit Debian 13 (Trixie), an owner
account named `pi`, and an RTL2832U USB receiver (`0bda:2838`).

[Step-by-step owner guide](https://github.com/gdowkpc/apollo-public-release/blob/pi-bootstrap-v1.0.0-beta1-r4/docs/pi-build93-qualification.md)
· [Apollo Downloads](https://www.repeaterbook.com/apollo/downloads/)

R4 changes only the board-model check in the exact published R3 installer.
It installs the same Build 93 runtime and Node Agent 51 and downloads the unchanged
R3 payload from its existing immutable URL. It retains the architecture, OS,
existing-installation, integrity, owner-authentication and service boundaries.
The R3 release and stable Build 92 / Bootstrap R2 update record remain available.

**Qualification candidate:** 26 focused source tests and exact artifact/inventory
verification passed. Physical clean-install, RF, reporting/audio association,
Review and reboot verification on Pi 4 and Pi 5 remain pending. This release does
not promote the candidate to stable or update existing devices automatically.

## Installer

Download [apollo-pi-bootstrap-beta1-r4.sh](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r4/apollo-pi-bootstrap-beta1-r4.sh).
SHA-256: `773ed9cd87472f90386ab1ed8500977f77aa1ef69d341bf8f6517ed5ba91e3a1`.

Verify the downloaded file before running it:

```bash
printf '%s  %s\n' 773ed9cd87472f90386ab1ed8500977f77aa1ef69d341bf8f6517ed5ba91e3a1 apollo-pi-bootstrap-beta1-r4.sh | sha256sum --check --strict &&
sudo bash ./apollo-pi-bootstrap-beta1-r4.sh
```

## Provenance

Installer source: `50b7db24c3463220b115b2d18d19417ce79729a3`.
Runtime source: `93f1f63360927b43fda2c2278c9275016363a385`.

| Retained dependency | SHA-256 |
| --- | --- |
| Build 93 Linux ARM64 ZIP | `344b847406634c7723591108d1308e730d38537f06a28e7979a8e2712e2de6fc` |
| Node Agent 51 archive | `3c122064461631e5a2064e4b732e75cb2086496f9679105a55428353d2d1a205` |
| R3 payload | `b4b3ee98406f82c3be172134079bac45ecf0a439dffebd47e406b69bf719f732` |
| R3 installer preimage | `ad57330df225a4b93dc82489ccc51b5fd84039a4472611954738671e3afdf598` |

The release's `pi-bootstrap-r4-artifact-manifest.json` records the exact installer,
dependency URLs, sizes, hashes and pending physical qualification.
