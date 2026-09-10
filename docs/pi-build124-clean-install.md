# Apollo Pi Build 124 clean-install beta

Build 124 brings owner-initiated stable updates into the existing Build 96 analog RTL-SDR release line. Bootstrap R7 installs the matching Build 124 runtime and protected update helper. It remains a beta release.

## Supported Pi and operating system

Use a Raspberry Pi 3 Model B, Raspberry Pi 4 Model B, or Raspberry Pi 5 Model B with the 64-bit Raspberry Pi OS Debian 13 (Trixie) image. Pi 3B+, Pi 400, Compute Module, 32-bit images and Bookworm are outside this clean installer's supported hardware/OS gate.

The installer requires ARM64 (`aarch64`), the standard `pi` account, systemd as PID 1, at least 2 GiB free storage, and a supported RTL2832U SDR receiver.

## Clean installation

Start with a clean SD card. Keep any existing Apollo SD card and its node data intact. This bootstrap refuses an existing Apollo installation; it is not an in-place migration or recovery command for an existing node.

Download [Bootstrap R7 Build 124](https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r7-build124/apollo-pi-bootstrap-beta1-r7.sh) from [Apollo Downloads](https://www.repeaterbooklive.com/apollo/downloads/).

Verify the script's SHA-256 before running it:

`694271e599a4b6a92a25473e4e84d7e8c074df58a59b389eecce6886b60e1e71`

Run the verified script with `sudo bash ./apollo-pi-bootstrap-beta1-r7.sh` from an interactive SSH terminal. It verifies the protected payload and exact Build 124 runtime before installation. Keep the installer-provided SSH tunnel open to use the loopback owner interface.

In the owner interface, connect to RepeaterBook, confirm Receiver Location, save the SDR Scan Plan, then choose Start Receiver.

## Updates after installation

When a newer approved stable release is available, choose Update and confirm installation. Apollo checks the latest stable record again, verifies the download and installs it only when its version/build is newer. Identity, settings and pending reports remain under the existing managed installation and recovery paths. Reception pauses while the runtime is replaced and restarted.

Checks do not install software by themselves. Equal or older builds are not installed. A failed check or download does not start installation. Optional beta/test downloads are not selected by stable update discovery. Build 124 can therefore report no newer stable update while a different test release is available on Downloads.

The separate receiver-test ARM64 ZIP is not a clean installer and does not include this bootstrap.

## Release identity and qualification

- Runtime: `ApolloPassiveReceive-1.0.0-build.124-linux-arm64.zip`
- Runtime SHA-256: `a49827b6eb02dc60ea98da3b168baac65438c57004984738a665e162afdfc2f1`
- Source commit: `22e6587a2f70a9471c8d6b7306c87e614cc90c01`
- Physical clean-Pi installation, receiver and reporting qualification remain pending. Local package and emulated ARM64 checks do not establish physical qualification.

Previous immutable installers remain available for recovery on a separate clean SD card. Retain the original card and node data; do not run a clean bootstrap over an existing installation.
