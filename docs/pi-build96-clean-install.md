# Apollo Pi Build 96 clean-install candidate

Bootstrap R5 Build 96 supports Raspberry Pi 3 Model B, Raspberry Pi 4 Model B, and Raspberry Pi 5 Model B only when running the 64-bit Raspberry Pi OS Debian 13 (Trixie) image. A Pi 3B+, Pi 400, Compute Module, 32-bit image, Bookworm image, or existing Apollo installation is not supported by this clean installer.

Requirements: ARM64 (`aarch64`), the standard `pi` account, systemd as PID 1, at least 2 GiB free storage, and a supported RTL2832U SDR receiver. Start from a genuinely clean Pi image. The installer refuses an existing Apollo state and verifies its payload and Build 96 runtime hashes before installation.

Download the R5 Build 96 installer from Apollo Downloads, verify its SHA-256, and run it with `sudo` from an interactive SSH terminal. It creates the loopback owner UI. Keep the installer-provided SSH tunnel open while completing setup.

In the owner UI: connect to RepeaterBook with username and password, confirm Receiver Location, save the SDR Scan Plan, then choose Start Receiver. If sign-in fails, the UI now says: â€œRepeaterBook did not accept the username or password. Check them and try again.â€ No password is stored by the installer or UI.

This is a clean-install candidate. Physical clean-Pi qualification remains pending. Existing R2/R3/R4 releases and their rollback paths are retained.