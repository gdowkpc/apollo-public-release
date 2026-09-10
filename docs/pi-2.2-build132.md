# Apollo Pi 2.2 Build 132

Build 132 is a controlled ARM64 runtime beta for Raspberry Pi OS / Linux. It
shortens the idle broad-sweep interval to two seconds when the receiver has
classified a band with no energy candidates. Energy candidates keep the
configured active dwell.

The ZIP is a runtime package, not a clean installer. Verify its SHA-256 before
use. Existing nodes must use their approved owner-initiated upgrade procedure
and preserve node identity, credentials, settings, and retained observations.

The package supports bundled RTL-SDR utilities and the Apollo SDRplay RSP1B
capture helper. An SDRplay RSP1B also requires the SDRplay API/service 3.15.2
to be installed separately on the Pi. The proprietary vendor API is not
bundled, and Build 132 does not include a one-click vendor-dependency installer.

Archive, inventory, and ARM64 executable checks passed. SDRplay vendor-service
readiness, physical Pi installation, RF reception, organic reporting, matching,
and Review qualification remain pending.
