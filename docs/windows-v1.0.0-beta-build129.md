# Apollo Windows Beta — Build 129

Build 129 is an optional Windows x64 portable beta for Apollo Passive Receive.
It adds the shared Flutter Live shell alongside the protected native receiver
service and extends selected-release health qualification to five minutes.
It is not a Windows setup EXE, does not install automatically, and does not
replace the stable Windows download.

## Release identity

- Version: `1.0.0`
- Build: `129`
- Source commit: `7723c3c4cb2a6feea392531373db1c68d5c0a238`
- Package: `ApolloPassiveReceive-1.0.0-build.129-windows-x64.zip`
- Size: `27,239,164` bytes
- SHA-256: `b694a26344f252bd02b606c7a1617063e13669e4918a899074b81ad35bd8597e`

## Before you start

Use Windows 10 or Windows 11 x64 and a compatible RTL-SDR. Install the RTL-SDR
interface 0 WinUSB driver with Zadig only for that receiver interface; do not
replace drivers for unrelated USB devices. Keep the complete extracted folder
together because it contains the native receiver, RTL-SDR runtime, and the
Flutter Live shell.

## Portable start

1. Download the ZIP and verify its SHA-256 against the value above.
2. Extract it to a writable local folder.
3. Run `Start Apollo Passive Receive.cmd`.
4. For the optional shared Live window, run `flutter-live\apollo_node_shell.exe`.
5. Confirm the receiver and reporting state shown by Apollo before collecting
   observations.

Existing managed Windows installations should use their approved operator
deployment path. Do not overwrite a protected service installation manually
with this portable ZIP.

## What Build 129 proves—and does not prove

The package identity, native service startup, protected reporting configuration,
and receiver readiness were checked on two authorized Windows installations.
That does not establish every hardware combination, continuous RF reception, or
an organic report flowing through intake, matching, and RepeaterBook Review.
The beta remains an owner-initiated test release.

## Safety and reporting boundary

The portable ZIP has no credential of its own. A device sends observations only
when it has separately been authorized and the application displays the intended
reporting state. Never copy credentials between devices. Preserve diagnostics
before troubleshooting or changing a receiver connection.
