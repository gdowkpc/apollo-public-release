# Apollo Pi Bootstrap R5 — Qualification Candidate

R5 fixes `published_at_invalid`, which stopped R3/R4 while activating Build 93.
The release timestamp now uses the canonical UTC form with milliseconds required
by the existing deployment validator. The timestamp value is unchanged.

The runtime remains **Version 1.0.0 / Build 93**, with **Node Agent 51** and
**Linux ARM64**. The Build 93 ZIP and node-agent archive were not rebuilt.
R4's Pi 4 Model B / Pi 5 Model B support is unchanged, as are the OS check,
clean-install guard, signing and release authorization, authentication,
credential storage, receiver behavior and loopback UI access.

[Installation guide](https://github.com/gdowkpc/apollo-public-release/blob/pi-bootstrap-v1.0.0-beta1-r5/docs/pi-build93-qualification.md)
· [Apollo Downloads](https://www.repeaterbook.com/apollo/downloads/)

## Failed R3/R4 installation

Preserve the failed card intact for diagnosis. Use a different card with a fresh
Raspberry Pi OS 64-bit Debian 13 (Trixie) image for clean-install qualification.
R5 will reject the partially installed card. No cleanup, guard bypass or repaired
installation is accepted as clean-install proof.

## Verification and status

Before construction, the generated manifest passed the actual retained deployment
validator on Windows and Linux. The old timestamp was rejected by the regression
check. The unchanged manual release authorization, initial baseline, package hash,
internal inventory and executable checks passed. R5 was constructed once, retained
and reread for verification. Public artifact hashes must match the retained files.

Physical clean-install, receiver/RF, production reporting/audio, Review and reboot
qualification remain pending. R3/R4 installer links are withdrawn from Downloads.
Stable Build 92 / R2 pointers and Windows/CJ-1 remain unchanged. No Beta promotion
or owner notifications are part of this release.

## Provenance

- Timestamp-fix source: `780eab4cab96bb9dd7cf2ba6edd46b1b470805d7`.
- Runtime source: `93f1f63360927b43fda2c2278c9275016363a385`.
- R4 installer baseline source: `50b7db24c3463220b115b2d18d19417ce79729a3`.
- Only the initial-release timestamp and its payload inventory record changed.
- The installer differs from R4 only in its payload URL and SHA-256 pin.

| Artifact | SHA-256 |
| --- | --- |
| [apollo-pi-bootstrap-beta1-payload.tar.gz](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r5/apollo-pi-bootstrap-beta1-payload.tar.gz) | `aa49f9f946a1b924bef701caad68e6b3a6530d5fac66d41a19d75807a6d53b34` |
| [apollo-pi-bootstrap-beta1-r5.sh](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r5/apollo-pi-bootstrap-beta1-r5.sh) | `6d0f474d1c570fe7a52113ad1431aac56b5e0ee1de53cb5d67bd573848c97503` |
| [ApolloPassiveReceive-1.0.0-build.93-linux-arm64.zip](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-v1.0.0-beta1-build93/ApolloPassiveReceive-1.0.0-build.93-linux-arm64.zip) | `344b847406634c7723591108d1308e730d38537f06a28e7979a8e2712e2de6fc` |
| [ApolloNodeAgent-1.0.0-build.51-linux-arm64.tar.gz](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-v1.0.0-beta1-build93/ApolloNodeAgent-1.0.0-build.51-linux-arm64.tar.gz) | `3c122064461631e5a2064e4b732e75cb2086496f9679105a55428353d2d1a205` |

[Machine-readable artifact manifest](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r5/pi-bootstrap-r5-artifact-manifest.json)
