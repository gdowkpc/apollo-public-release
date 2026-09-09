# Apollo CJ-1 1.0 owner guide

## Download and verify

Download `Apollo-CJ1-1.0-build116.apk` from the
[Apollo CJ-1 1.0 release](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.0-build116).

On Windows:

```bat
certutil -hashfile Apollo-CJ1-1.0-build116.apk SHA256
```

On Linux:

```sh
sha256sum Apollo-CJ1-1.0-build116.apk
```

On macOS:

```sh
shasum -a 256 Apollo-CJ1-1.0-build116.apk
```

The result must be
`05ec5d417e52d17b1dd6f0c458ca2ebacc58cba26c82e7257f27de6a00f72e6c`.
The APK is `76,887,137` bytes.

This is the stable **Apollo CJ-1 1.0** release for supported ARM64 CJ-1 devices.
The existing Build 116 APK is promoted without changing its bytes. Its package
is `org.gdowkpc.apollo_node_shell`, Android version
`1.0.12-provider-evidence.3`, version code `116`. It remains a debuggable APK
distributed for direct installation. If Build 116 is already installed, no
reinstallation is needed for this release designation.

Build 116 uses a subtle, 220 ms warm two-note hit notification controlled by
**Hit beep**. This promotion retains the existing receiver, CTCSS, and evidence
behavior. Further KA9Q-style CTCSS work is reserved for 1.1.

## Install or upgrade

Enable Android developer options and USB debugging, connect the CJ-1, and
confirm the intended device:

```sh
adb devices
adb install -r Apollo-CJ1-1.0-build116.apk
```

Use `-r` to preserve app data. The in-place upgrade from Build 115 to this exact
Build 116 APK was previously verified to preserve node identity, credentials,
settings, and retained delivery state. If Android reports a signature mismatch,
stop; uninstalling would erase the node's app data and identity.

Open **Apollo Listening**. Grant the requested location, microphone/receive-
audio, notification, and foreground-service permissions. These support GPS-
based target selection, the CJ-1 receive path, visible background operation,
and bounded evidence audio; they do not authorize transmission.

## First use

1. In **RepeaterBook node sign-in**, enter the owner RepeaterBook username or
   email and password, then select **Sign in and connect this node**. Apollo
   stores the returned node credential, not the password.
2. Confirm the app obtains location and a scan plan. **Node details** should
   show the target source, target count, local node ID, and reporting state.
3. Select **Start**. Require **Receiver running**, an active foreground-service
   notification, and changing **NOW SCANNING** frequencies.
4. Open the Settings drawer to choose **Hit audio**, **Hit beep**, and
   **Temporary audio evidence**. Temporary evidence also requires RepeaterBook
   permission for this device.
5. In **Node details**, watch **Outbox pending**, **Audio clips queued**, latest
   delivery, and audio association. A quiet RF period is not a failure.

CJ-1 uses RepeaterBook app provider targets when available. Offline operation
continues with available local targets or the approved cached plan, and queued
reportable observations can drain when connectivity returns.

Use **Stop** for an intentional stop. Do not use **Diagnostic Fixed Tune** for
normal operation; it suspends normal scanning and deliberately creates no
observation or evidence upload.

See the [release notes](../release-notes/cj1-v1.0.0-build116.md) for source
provenance and the scope of recorded verification.
