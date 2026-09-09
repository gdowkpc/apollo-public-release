# Apollo Pi Hydra test release: Build 95 / Bootstrap R6

Fresh-card installation for HydraSDR RFOne connected directly by USB to a Pi 4 or Pi 5 running Raspberry Pi OS 64-bit Debian 13 (Trixie). Includes Apollo Build 95, Node Agent 51, the ARM64 Hydra helper, libhydrasdr 1.1.2, libusb 1.0.29, license notices, and USB permission rules.

The owner setup selects Hydra, enumerates its serial, configures native linearity gain and 2.5 MS/s capture, and starts broad sweeps. Analog CTCSS observations use the existing authenticated node reporting path. Qualified two-second audio is attached only through the existing evidence policy. Repeater matching remains server-owned.

Use the [fresh SD card installation and end-to-end test guide](../docs/pi-hydra-build95.md). The managed-update ZIP alone is not a clean installer. Check SHA256SUMS.txt before running Bootstrap R6; the installer verifies the separately pinned payload and Build 95 ZIP.

Validation: 779 source tests passed, 11 skipped, no failures in the permitted release suite. The final sealed application started under Debian 13 ARM64 emulation and passed version, setup and Hydra UI checks. Exact package inventory, executable identity, payload permissions, initial installation policy and bootstrap syntax passed. Local generated-IQ tests passed through the actual DSP, observation queues, Node Agent handlers and test intake.

Physical USB reception, clean-card installation and an organic report appearing in RepeaterBook Review remain for the test Pi. This is a test prerelease, with no stable-update promotion or automatic installation. Airspy and SDRplay source support is present, but this package does not bundle their native runtimes.

Source: `c5e57cfd14aeffa920f08641d826ef64d7ad23cc` on `codex/pi-hydra-release`. Exact sizes and hashes are in `hydra-pi-build95-manifest.json` and `SHA256SUMS.txt` attached to this release.
