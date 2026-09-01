# Raspberry Pi Beta 1 owner guide

## Exact payload

Download `ApolloPassiveReceive-1.0.0-build.92-linux-arm64.zip` from the
[Build 92 prerelease](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build92)
and verify:

```sh
sha256sum ApolloPassiveReceive-1.0.0-build.92-linux-arm64.zip
```

The result must be
`ee3819e971aa49b856da8045f2447baff3fc4d871d573cffe7e3ff5dc02dc071`.

## Installation boundary

Build 92 is the exact package qualified on the Pi as a managed update. It
contains the receiver, matched ARM64 RTL-SDR runtime, node-agent Build 50, and
release identity. It does **not** contain a clean-Pi installer or a generic
bootstrap for the protected service, node identity, credential, reporting
policy, audio policy, release custody, rollback, and managed-update authority.

On an already managed Apollo Pi, use only the existing managed release path.
Do not unpack the ZIP over the active release, manually create allowlist or
custody state, copy a credential, or replace a service file.

On a clean Pi, stop here. The current public materials do not provide the first
supported product bootstrap step. The existing internal bootstrap is tied to a
specific qualification hostname and legacy baseline and is not a clean-install
mechanism.

## UI access after a supported installation exists

The owner UI is loopback-only at `http://127.0.0.1:17882/`. Open it in a browser
on the Pi, or use an SSH tunnel from another computer:

```sh
ssh -L 17882:127.0.0.1:17882 pi@PI_HOSTNAME_OR_IP
```

Then open `http://127.0.0.1:17882/` on that computer. Do not expose port 17882
to the LAN.

In the UI, verify Build 92, set the intended scan ranges, leave gain blank for
automatic selection unless the test plan specifies a fixed gain, and leave
**Reference calibration** at **Automatic** unless **Not applicable** is
explicitly required. Save the scan plan, run **Validate and start receiver**,
and confirm receiver/scanning continuity, reporting mode, and empty or actively
draining observation/audio queues.

Identity, credential, location, `production_review`, and audio authorization
must come from the supported protected bootstrap. They must not be recreated
from this document.
