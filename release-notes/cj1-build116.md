# CJ-1 Beta 1 — Build 116

Build 116 replaces the old hit beep with a subtle, warm two-note notification.
The 220 ms descending tone is preloaded and remains controlled by **Hit beep**.
The hit interval, receive-audio path, RF behavior, and evidence/reporting policy
are unchanged. This is a notification refinement, not a fix for missing receive
audio on short or silent hits.

## Install

Download `Apollo-CJ1-1.0.12-beta1-build116.apk` below and follow the
[CJ-1 owner guide](https://github.com/gdowkpc/apollo-public-release/blob/cj1-v1.0.12-beta1-build116/docs/cj1-beta1.md).
Use `adb install -r` for an in-place upgrade that preserves app data.

- Hardware: supported ARM64 CJ-1 devices (`arm64-v8a`).
- Package: `org.gdowkpc.apollo_node_shell`.
- Version: `1.0.12-provider-evidence.3`, version code `116`.
- Size: `76,887,137` bytes.
- SHA-256: `05ec5d417e52d17b1dd6f0c458ca2ebacc58cba26c82e7257f27de6a00f72e6c`.
- Source commit: `069cb24773c30cd75f4aa7071f2de72391299b2a`.
- Signer certificate SHA-256: `9824f91945459046d25cce94c83cef8a2b8baba246872377e6cb29fd707a69c0`.

This uses the same debug signer as Build 115 and remains a debuggable controlled
Beta APK, not a production-signed Play Store artifact. Stop if Android reports
a signature mismatch; uninstalling erases app data and node identity.

## Validation

All 26 focused Android tests passed. The exact APK was installed on a CJ-1;
identity, credentials, settings, and retained delivery state were preserved.
The notification loaded successfully, and GPS, provider plan, and receiver
scanning resumed. A fresh over-the-air listening check was not completed before
publication; no new end-to-end receive-audio claim is made.

[Build 115](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build115)
remains available for release history. Android downgrade restrictions apply;
do not uninstall to force a downgrade.
