# Apollo CJ-1 1.1 Beta 2 — Build 118

Optional beta for supported ARM64 CJ-1 devices. Beta 2 retains the KA9Q-style
CTCSS detector from Build 117 and adds a five-minute authenticated status
check-in while Apollo is running. Stable 1.0 / Build 116 remains available.

## Check-in behavior

The check-in uses the CJ-1's existing node credential and a fixed RepeaterBook
HTTPS endpoint. The server derives the node identity from the existing
application-client binding; the device does not submit a node UUID. Failed
check-ins are logged locally and never block scanning, evidence capture, or
evidence delivery.

## Verification

- 45 focused Android tests passed, including three endpoint-allowlist tests.
- The APK has package `org.gdowkpc.apollo_node_shell`, Android version
  `1.1.0-dev.2`, and version code `118`.
- APK signature verification and the CJ-1 JNI boundary check passed.
- The production endpoint is deployed and rejects an unauthenticated POST with
  HTTP 401. A live authenticated check-in requires installation on a CJ-1.

## Artifact identity

- Source: `11e3c47788bff5c427f05f11094c4e8c0b92a386`
- APK size: `76,903,265` bytes
- SHA-256: `dfe37d801f089795bef880646b971e78641e5783b422af330c0f95b5ec21c12e`

Do not uninstall or clear app data to upgrade. This beta is an optional
download and does not change automatic update discovery.
