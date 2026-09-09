# HydraSDR RFOne on Raspberry Pi — Build 95 test release

This release provides a clean installer, Apollo Build 95, Node Agent 51, and the
native ARM64 Hydra driver and capture helper. It is a test release for a directly
connected HydraSDR RFOne. Physical reception and reporting on your Pi are the next
qualification step; this is not a stable-release promotion.

## Prepare the Pi

Use a **fresh SD card** with Raspberry Pi OS **64-bit, Debian 13 (Trixie)** on a
**Raspberry Pi 4 Model B or Pi 5 Model B**. Create the owner account named `pi`,
enable SSH, and connect the Pi to the Internet. The installer requires at least
2 GiB free. Attach the Hydra by USB and connect an appropriate receive antenna.

The installer rejects existing Apollo files or services. Preserve an existing or
failed installation on its original card; use another card for this test.

## Install

On the Pi, download Bootstrap R6 and its checksums:

```sh
mkdir -p ~/apollo-hydra-install
cd ~/apollo-hydra-install
curl --fail --location --remote-name https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r6/apollo-pi-bootstrap-beta1-r6.sh
curl --fail --location --remote-name https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r6/SHA256SUMS.txt
sha256sum --check --ignore-missing SHA256SUMS.txt
sudo bash apollo-pi-bootstrap-beta1-r6.sh
```

Proceed only if the installer checksum reports `OK`. The installer separately
verifies the bootstrap payload and Build 95 package before activation. It installs
the bundled Hydra libraries and restricted USB permissions; no SDK build is needed
on the Pi. It uses the existing protected enrollment and reporting services.

## Connect and select Hydra

Keep the hostname printed by the installer. From your computer, open an SSH tunnel:

```sh
ssh -N -T -L 17882:127.0.0.1:17882 pi@YOUR-PI-HOSTNAME.local
```

Open **http://127.0.0.1:17882/** in that computer's browser, leaving the tunnel open.

1. Connect the node to your RepeaterBook account.
2. Confirm the receiver's actual location. Browser geolocation identifies the
   browser's location, which may differ from the Pi's.
3. Select **HydraSDR RFOne**, then **Find connected receivers**. A single connected
   Hydra fills its USB serial automatically. With multiple devices, enter the
   serial shown for the receiver you intend to use.
4. Start with **linearity gain step 10**. Steps 0–21 are native device settings,
   not dB. The clean setup uses **2.5 MS/s**, which supports both CTCSS and bounded
   audio evidence. Keep this rate for the test.
5. Select the frequency bands/ranges, save the scan plan, and start the receiver.

Apollo broadly sweeps the selected ranges. RepeaterBook performs repeater matching
on the server; you do not need to assign individual repeater targets. Hydra does
not use the RTL-SDR NOAA gain-calibration routine.

## Verify the test

Confirm the dashboard shows **Build 95**, the Hydra receiver, and advancing sweeps.
Let normal RF activity produce observations. Confirm the node is authorized for
reporting and that the observation queue drains with a successful delivery time.
If authorization is pending or denied, complete the normal RepeaterBook approval
path; a running receiver alone does not establish reporting readiness.

Detected CTCSS observations do not require audio merely because audio is available.
When the evidence policy requires audio, Apollo attaches a qualified two-second
NFM clip and uploads it after the observation is acknowledged. Missing or rejected
required audio keeps the observation from being reported. No continuous recording
or retained IQ is introduced.

For end-to-end qualification, verify an organic observation in RepeaterBook's
protected Apollo Review with the correct node ID, frequency, time and tone/audio.
An HTTP acknowledgment alone does not establish matching or Review visibility.
Then reboot the Pi and confirm receiver settings, identity and reporting persist.

If capture fails, retain the error and node ID. Check the USB cable, power, selected
serial and permissions. Do not erase retained observations or re-enroll the node as
a troubleshooting shortcut.

## Build contents and validation

The release manifest records exact source, file sizes and SHA-256 hashes. The
package includes `apollo_hydrasdr_capture`, libhydrasdr 1.1.2 and libusb 1.0.29,
their license notices, and the existing RTL runtime. Hydra uses RX0 with bias power
and hardware AGC disabled. Relative RF power is shown in dBFS; it is not reported
as calibrated dBm.

Prepublication checks cover software tests, real ARM64 SDK compilation and loader
startup, package inventory/permissions, installer binding, and local Pi reporting
through the actual DSP and node-agent handlers. Generated IQ and emulation do not
prove physical USB reception, receiver timing/performance, or organic server
matching. Record those outcomes on the test Pi.

Airspy and SDRplay source integrations are present, but their native runtimes are
not included in this Hydra test package. Existing stable Pi pointers and installed
nodes are not updated automatically by this release.
