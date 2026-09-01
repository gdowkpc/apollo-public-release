# Raspberry Pi Beta 1 owner guide

## Supported clean baseline

Beta 1 clean installation deliberately supports one narrow baseline:

- Raspberry Pi 5 Model B
- Raspberry Pi OS (64-bit), Debian 13 `trixie`
- ARM64 (`aarch64`) with `systemd` as PID 1
- at least 2 GiB free on `/`
- working HTTPS access to GitHub and RepeaterBook
- an RTL2832U-compatible USB receiver; the unattended recovery authority is
  restricted to the qualified `0bda:2838` device identity
- the standard Raspberry Pi OS owner account named `pi`

The bootstrap installs these runtime prerequisites from Raspberry Pi OS:
`ca-certificates`, `curl`, `unzip`, `python3`, `nodejs`, `rtl-sdr`,
`librtlsdr0`, `libusb-1.0-0`, `usbutils`, `avahi-daemon`, and `sudo`.
Other Pi models, operating systems, architectures, and pre-existing Apollo
installations are outside this Beta 1 clean-install contract.

## Clean installation

Start with the supported fresh OS. Connect the RTL-SDR and network, sign in as
`pi`, and run:

```sh
curl -fL https://github.com/gdowkpc/apollo-public-release/releases/download/pi-bootstrap-v1.0.0-beta1-r2/apollo-pi-bootstrap-beta1.sh -o apollo-pi-bootstrap-beta1.sh
sudo bash apollo-pi-bootstrap-beta1.sh
```

The script accepts no arguments and fails closed if it detects an unsupported or
existing Apollo installation.

The bootstrap visibly checks the system, installs prerequisites, downloads its
exact public payload, then downloads the unchanged
`ApolloPassiveReceive-1.0.0-build.92-linux-arm64.zip`. It validates the exact
Build 92 release identity, receiver, node-agent, and RTL runtime before
activation. It installs the established
non-root receiver and node-agent services, narrow RTL recovery authority,
production Review/audio policies, initial managed-release policy, and Build 92
as the clean node's protected rollback baseline. It does not clone a development
repository or authorize any future build.

The controller obtains that initial baseline from the clean-install policy and
makes Build 92 the first known-good baseline. It does not create fake Build 55
custody or history. Existing upgraded nodes use their real historical baseline
and are not part of this clean-install flow.

During installation, enter the receiver latitude and longitude in decimal
degrees. RepeaterBook sign-in is interactive; the password is not echoed or
placed in shell arguments. Apollo creates a unique node ID, uses the canonical
node-agent enrollment exchange, and stores only the issued device credential in
the protected node-agent state. If approval is pending, rerun:

```sh
apollo-onboard check-approval
```

Never copy another node's identity or credential.

## UI and initial configuration

The owner UI is intentionally loopback-only at `http://127.0.0.1:17882/`. Open
it in a browser on the Pi. From another computer, keep this tunnel running:

```sh
ssh -N -T -L 17882:127.0.0.1:17882 pi@PI_HOSTNAME.local
```

Then open `http://127.0.0.1:17882/` on that computer. Do not expose port 17882
to the LAN.

In the UI:

1. Confirm the Version/Build page reports Build 92 and source
   `a7a8447f88c1159effb762dcf1f6c7b6764707d7`.
2. Open Settings and select the intended scan bands/ranges.
3. Leave gain blank for automatic selection unless the test plan specifies an
   exact manual gain.
4. Choose **Reference calibration: Automatic** for the normal reference path.
   Choose **Not applicable** where no reference service is available; healthy
   finite samples use the established 14.4 dB fallback. A zero-sample/device
   fault is still a receiver failure.
5. Save the scan plan and run **Validate and start receiver**.
6. Require receiver ready/scanning status. Review health, version, reporting
   mode, and observation/audio queue status in the UI.

The installed reporting mode is `production_review`, with required audio
enabled. No organic RF traffic is not a failure, and an ordinary ambiguous or
`no_candidate` matcher result is not a receiver failure.

## Release references

- Bootstrap release: [`pi-bootstrap-v1.0.0-beta1-r2`](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-bootstrap-v1.0.0-beta1-r2)
- Receiver release: [`pi-v1.0.0-beta1-build92`](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build92)
- Node-agent internal Build: `50`

Build 92 remains the previously qualified, unchanged managed-update payload.
The bootstrap is separate installation tooling. After initial installation,
future upgrades use Apollo's normal owner-managed update path.

## Failure behavior

If setup or receiver validation fails, Apollo services are stopped and disabled;
the installed files, unique identity, and diagnostic state are retained. Record
the displayed stage and error rather than deleting state or rerunning with
manual policy changes.
