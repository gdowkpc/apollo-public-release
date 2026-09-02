# Windows Beta 1 owner guide

## Download

Download the [Build 97 Windows installer](https://github.com/gdowkpc/apollo-public-release/releases/download/windows-v1.0.0-beta1-build97/ApolloPassiveReceive-1.0.0-build.97-windows-x64-setup.exe).

After the download finishes, run the installer and accept the normal Windows
User Account Control prompt. The installer places the complete Apollo runtime
and protected Windows service support files together; no ZIP extraction or
manual service command is required.

If Windows does not recognize the RTL-SDR, use Zadig to install WinUSB for
**RTL-SDR interface 0** only. Do not change drivers for other USB devices.

## First launch and local UI

Open Apollo from the shortcut created by the installer. If the browser does not
open automatically, go to `http://127.0.0.1:17882/` on the same Windows
computer. This local web page is where you complete setup and control Apollo.
Do not open this address in a remote or in-app browser: `127.0.0.1` always means
the computer where Apollo is running.

On a clean installation, complete the pages in this order:

1. **Connect to RepeaterBook** and authenticate as the node owner.
2. Let Apollo create the canonical node and secure its credential for the
   protected Windows service. Accept the normal UAC prompt when Apollo displays
   **Securing Apollo service**. Do not copy or paste a node credential.
3. Set **Receiver Location** using the map, **Use My Location**, a draggable
   marker, or manual coordinates, then save it.
4. Select the intended **Scan Plan**. Leave **Reference calibration** set to
   **Automatic** unless the test plan says otherwise.
5. Leave RTL-SDR gain at its owner-configured value; for the current controlled
   test baseline this is 14.4 dB.
6. Select **Start Receiver** and require the receiver to reach ready/scanning
   state with advancing sweeps.

The UI is intentionally localhost-only. Do not create a firewall exception.

## Identity, location, and reporting

Apollo creates the Device ID automatically during authenticated onboarding. A
normal new-node installation does not require administrator approval, a manual
allowlist entry, or credential copy/paste. The exact receiver coordinates are
stored in protected policy and are not published as the public node location or
listing.

After onboarding, verify the service is `ApolloPassiveReceiveBoot`, starts
automatically as `NT AUTHORITY\LocalService`, and the local page reports Build
97. Reporting should show `production_review`; observation and audio queues
should be empty or draining normally.

## Everyday controls and support

- **Edit Receiver Settings** changes the scan plan and restarts through the
  validated settings path.
- **Test receiver** reruns the bounded receiver check.
- **Export Diagnostics** creates a sanitized local support report.
- The optional USB stability action is not part of normal installation. Use it
  only for a confirmed long-run USB suspend/recovery problem.
- Exact-device unattended Windows RTL recovery is installed, but organic fault
  qualification remains pending. Do not induce a hardware fault to test it.
- Removing the application data destroys this Device ID and credential. Do not
  do that during an upgrade or ordinary troubleshooting.

## Change log

### Build 97

Build 97 corrects the clean-install owner launch and first-run routing exposed
by Build 96 testing. The installed shortcut and post-install action start the
local Apollo UI host without presenting a command window, wait up to 30 seconds
for bounded localhost readiness, and open the owner UI in the default browser.
A clean node starts at **Connect to RepeaterBook**; receiver location, scan plan,
and receiver start remain unavailable until canonical provisioning and the
protected LocalService transition complete. No receiver, reporting, RF, CTCSS,
audio, gain, or recovery behavior was changed for this correction.

### Build 96

Build 96 adds the clean Windows owner-install flow: authenticated RepeaterBook
connection, automatic canonical node provisioning, protected LocalService
credential transition, map-based receiver location, scan-plan selection, and
receiver start in the required order. It also carries forward the Build 93
bounded sender repair and the qualified Windows receiver, gain, and unattended
recovery behavior. The downloadable installer contains the complete runtime and
the protected-service helpers required by onboarding.

### Build 93

Build 93 fixes a delivery condition where one stalled network operation could
indefinitely prevent later queued observations from being sent. Observation and
audio delivery operations are now bounded; an item that encounters a transient
timeout remains queued and retries through the normal sender. The local support
view shows the sender state, current observation, last attempt, and scheduled
retry without exposing credentials.

### Build 93 R3

The refreshed Windows package adds `Open Apollo Local UI.url` beside the launcher
so the owner can open the local setup page without typing the address. It also
shows the release Build in the page header and provides a visible **Back to
dashboard** control while editing settings.
