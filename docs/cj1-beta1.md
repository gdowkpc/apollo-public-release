# CJ-1 Beta 1 owner guide

## Download and verify

Download `Apollo-CJ1-1.0.12-beta1-build115.apk` from the
[Build 115 prerelease](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build115).

On Windows:

```bat
certutil -hashfile Apollo-CJ1-1.0.12-beta1-build115.apk SHA256
```

On Linux or macOS:

```sh
sha256sum Apollo-CJ1-1.0.12-beta1-build115.apk
```

The result must be
`6099e8212b92482fd505911c2627fa288a9940b52fd8296009b9918e9a4db59d`.

This is package `org.gdowkpc.apollo_node_shell`, version code `115`. It is
debug-signed and debuggable; it is a controlled Beta APK, not a production-
signed Play Store artifact.

## Install or upgrade

Enable Android developer options and USB debugging, connect the CJ-1, and
confirm the intended device:

```sh
adb devices
adb install -r Apollo-CJ1-1.0.12-beta1-build115.apk
```

The historical public Build 69 has the same package ID and signer, so `-r`
preserves app data during that upgrade. If Android reports a signature mismatch
from some other build, stop; uninstalling would erase the node's app data and
identity.

Open **Apollo Listening**. Grant the requested location, microphone/receive-
audio, notification, and foreground-service permissions. These support GPS-
based target selection, the CJ-1 receive path, visible background operation,
and bounded evidence audio; they do not authorize transmission.

## First use

1. In **RepeaterBook node sign-in**, enter the owner RepeaterBook username or
   email and password, then select **Sign in and connect this node**. Apollo
   stores the returned node credential, not the password.
2. Confirm the app obtains location and an assigned plan. **Node details** should
   show the target source, assigned target count, local node ID, and reporting
   state.
3. Select **Start**. Require **Receiver running**, an active foreground-service
   notification, and changing **NOW SCANNING** frequencies.
4. Open the Settings drawer to choose **Hit audio**, **Hit beep**, and
   **Temporary audio evidence**. Temporary evidence also requires RepeaterBook
   permission for this device.
5. In **Node details**, watch **Outbox pending**, **Audio clips queued**, latest
   delivery, and audio association. A quiet RF period is not a failure.

Use **Stop** for an intentional stop. Do not use **Diagnostic Fixed Tune** for
normal Beta operation; it suspends the signed plan and deliberately creates no
observation or evidence upload.
