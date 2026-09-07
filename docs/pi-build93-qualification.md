# Apollo Pi Build 93 / Bootstrap R3 — Qualification Candidate

Build 93 / Bootstrap R3 is undergoing final clean-Pi qualification before the Apollo Beta is opened to testers. It is not promoted to the current/stable Beta. The existing Build 92 / Bootstrap R2 stable path remains unchanged.

Start at [Apollo Downloads](https://www.repeaterbook.com/apollo/downloads/). Choose **Apollo for Raspberry Pi**, **Version 1.0.0 / Build 93**, **Qualification Candidate**, **Node Agent 51 · Bootstrap R3**.

## Supported clean installation

Use a genuinely clean Raspberry Pi 5 Model B, Raspberry Pi OS 64-bit Debian 13 (trixie), and RTL2832U USB ID `0bda:2838`. Create the owner account named `pi`, enable SSH during OS setup for headless access, and allow at least 2 GiB free storage. Existing Apollo installations or state cause the installer to stop; do not erase a configured node to satisfy this guide.

The clean-install action is **Bootstrap R3**. The Build 93 managed-update ZIP and separate node-agent payload are supporting artifacts, not standalone clean installers.

In the Pi's terminal or SSH session, download and verify the exact installer before running it:

```bash
curl --fail --location --proto '=https' --tlsv1.2 'https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r3/apollo-pi-bootstrap-beta1-r3.sh' --output apollo-pi-bootstrap-beta1-r3.sh
echo 'ad57330df225a4b93dc82489ccc51b5fd84039a4472611954738671e3afdf598  apollo-pi-bootstrap-beta1-r3.sh' | sha256sum --check --strict
sudo bash ./apollo-pi-bootstrap-beta1-r3.sh
```

The installer downloads and verifies the exact bound Build 93 package and R3 payload, installs dependencies and protected services, then prints the hostname and owner-UI access instructions. No RepeaterBook password or receiver coordinates are entered in the terminal.

## Open and configure Apollo

On the Pi, browse to `http://127.0.0.1:17882/`. For a headless Pi, run the installer-provided command on your computer, substituting its printed hostname:

```text
ssh -N -T -L 17882:127.0.0.1:17882 pi@PRINTED-HOSTNAME.local
```

Keep that tunnel open and browse to `http://127.0.0.1:17882/` on the computer. If that local port is already occupied, close the conflicting local application or use the Pi's local browser. The Apollo HTTP service remains loopback-only. No router forwarding or LAN listener is needed.

1. **Connect to RepeaterBook**: enter Username and Password and choose **Sign in and connect this node**. The protected node-agent receives one permanent device credential. The password is not saved and the browser does not receive the durable bearer.
2. **Receiver Location**: use the OpenStreetMap map, draggable marker, or manual latitude/longitude, then **Confirm Location**. **Use My Location** describes the computer running the browser; verify the actual Pi receiver location when using a tunnel.
3. **SDR Scan Plan**: select supported bands/ranges, gain policy, and reference policy. No RepeaterBook target list is required. Matching remains server-side.
4. Save the plan, then **Start Receiver** to open **Dashboard/Live**. A receiver fault remains in the configured dashboard.

Scanning can continue after the SSH tunnel closes. UUID, permanent credential, protected location, scan plan, and gain/reference settings are intended to persist through reboot. Physical confirmation for this release is pending.

## Qualification boundary

Source/package checks and ARM64 compiled-owner UI checks have passed. A genuinely clean physical Pi must still prove receiver readiness, finite samples, applicable NOAA/reference qualification, advancing SDR sweeps, genuine production RF observation HTTP 202, required audio HTTP 201 and correct association, Evidence Review receipt without duplicates, queue zero, and normal reboot with unattended scanning/reporting and unchanged identity/configuration. This guide makes no physical qualification claim.

## Exact immutable artifacts

Source: `93f1f63360927b43fda2c2278c9275016363a385`. Qualified parent: `873555c1de4e46004196f54d989fb82431589a7c`. Runtime version/build: **1.0.0 / 93**, **Linux ARM64**. Node-agent **1.0.0 / 51**. Bootstrap **R3**.

- [ApolloPassiveReceive-1.0.0-build.93-linux-arm64.zip](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-v1.0.0-beta1-build93/ApolloPassiveReceive-1.0.0-build.93-linux-arm64.zip) — 17890630 bytes; SHA-256 `344b847406634c7723591108d1308e730d38537f06a28e7979a8e2712e2de6fc`.
- [ApolloNodeAgent-1.0.0-build.51-linux-arm64.tar.gz](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-v1.0.0-beta1-build93/ApolloNodeAgent-1.0.0-build.51-linux-arm64.tar.gz) — 10312 bytes; SHA-256 `3c122064461631e5a2064e4b732e75cb2086496f9679105a55428353d2d1a205`.
- [apollo-pi-bootstrap-beta1-r3.sh](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r3/apollo-pi-bootstrap-beta1-r3.sh) — 14871 bytes; SHA-256 `ad57330df225a4b93dc82489ccc51b5fd84039a4472611954738671e3afdf598`.
- [apollo-pi-bootstrap-beta1-payload.tar.gz](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r3/apollo-pi-bootstrap-beta1-payload.tar.gz) — 165921 bytes; SHA-256 `b4b3ee98406f82c3be172134079bac45ecf0a439dffebd47e406b69bf719f732`.

Principal executable SHA-256: `50536cdfa342a5cb2308eb3b19bf217680ce2baa59e5527367a2413733211a8f`. Inner inventory SHA-256: `8aad9f1459e715f8fda2a9eb2fc89a0753d2f0b7a9d02b426fc03189679d842c`.
