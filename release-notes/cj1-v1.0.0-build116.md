# Apollo CJ-1 1.0 — Build 116

Apollo CJ-1 1.0 promotes the existing Build 116 APK to stable and removes its
Beta designation. This is a release promotion with unchanged APK bytes;
receiver behavior, CTCSS detection, reporting, and evidence policy remain as
published in Build 116. Further KA9Q-style CTCSS improvements are reserved for
1.1 and are not included here.

## Download and install

Download `Apollo-CJ1-1.0-build116.apk` from this release and follow the
[CJ-1 owner guide](https://github.com/gdowkpc/apollo-public-release/blob/cj1-v1.0.0-build116/docs/cj1.md).
Use `adb install -r` for an in-place upgrade that preserves app data. If Build
116 is already installed, no reinstallation is needed for this promotion.

- Hardware: supported ARM64 CJ-1 devices (`arm64-v8a`).
- Public release: Apollo CJ-1 **1.0 stable**.
- Package: `org.gdowkpc.apollo_node_shell`.
- Unchanged Android version: `1.0.12-provider-evidence.3`, version code `116`.
- Size: `76,887,137` bytes.
- SHA-256: `05ec5d417e52d17b1dd6f0c458ca2ebacc58cba26c82e7257f27de6a00f72e6c`.
- Apollo source commit: `069cb24773c30cd75f4aa7071f2de72391299b2a`.

The APK remains debuggable and is distributed for direct installation. Stop if
Android reports a signature mismatch; uninstalling erases app data and node
identity.

## Recorded verification

Before the original Build 116 publication, 26 focused Android tests passed.
These covered notification, monitor, preferences, and audio-evidence behavior;
they were not a CTCSS accuracy qualification. The exact APK was installed on a
CJ-1, preserving identity, credentials, settings, and retained delivery state.
The notification loaded, and GPS, provider plan, and receiver scanning resumed.

This promotion does not add a new physical-device acceptance run or sustained
scanning soak. The recorded Build 116 checks do not establish comprehensive
CTCSS accuracy or fresh end-to-end over-the-air delivery and Review proof.

The [original Build 116 Beta publication](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build116)
remains available as immutable release history. Its APK has the same SHA-256.
