# Windows Beta 1 owner guide

## Download and verify

Download the [Build 93 package R2 ZIP](https://github.com/gdowkpc/apollo-public-release/releases/download/windows-v1.0.0-beta1-build93-r2/ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip).
Package R2 contains the unchanged qualified Build 93 files in a ZIP that opens
normally in Windows Explorer.
In Command Prompt, verify it before extraction:

```bat
certutil -hashfile ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip SHA256
```

The result must be
`d8a395b0a73a1c4d9ae90c56928b128154175fe18706077eca4e49dbd5a85950`.

Extract the complete ZIP into a new folder. Keep every extracted file together.
Use Zadig to bind WinUSB only to RTL-SDR interface 0 if Windows has not already
done so. Do not change unrelated USB drivers.

## First launch and local UI

Run `Start Apollo Passive Receive.cmd` without administrator elevation. Open
`http://127.0.0.1:17882/` on that Windows computer.

On the first-run page:

1. Confirm the bundled RTL-SDR runtime is ready and device index `0` is the
   intended receiver.
2. Select a scan plan and ranges appropriate for the test location.
3. Leave RTL-SDR gain blank for automatic selection unless the test plan gives
   an exact fixed gain.
4. Leave **Reference calibration** at **Automatic**. Use **Not applicable** only
   when the test plan explicitly says reference calibration does not apply.
5. Leave **Start automatically next launch** selected when unattended operation
   is intended.
6. Select **Start Passive Observation**. After later edits, use **Save Scan Plan
   and Restart**.
7. In **Receiver self-test**, select **Validate and start receiver** and require
   a ready/running receiver before continuing.

The UI is intentionally localhost-only. Do not create a firewall exception.

Build 93 fixes a delivery condition where one stalled network operation could
indefinitely prevent later queued observations from being sent. Observation and
audio delivery operations are now bounded; an item that encounters a transient
timeout remains queued and retries through the normal sender. The local support
view shows the sender state, current observation, last attempt, and scheduled
retry without exposing credentials.

## Identity, location, and reporting

Under **Device authorization**, copy the non-secret authorization request and
send it to the Beta coordinator. The download contains no reusable credential
or reporting authorization. After the coordinator confirms that this exact
device is authorized, select **Revalidate authorization**.

Enter latitude and longitude under **Receiver location**, then select **Save
Authorized Location**. The save succeeds only after the existing Device ID is
positively authorized by RepeaterBook.

Production Review is not enabled merely by downloading or launching the ZIP.
The persistent boot-service installer also requires the coordinator-installed,
credential-free production Review policy. Do not construct that policy or copy
another device's credential. Once the coordinator confirms those prerequisites,
open an elevated PowerShell window in the extracted package directory and run:

```powershell
& ".\windows-support\Install Apollo Boot Service.ps1" -PackageRoot $PWD
```

The installer must finish with service `ApolloPassiveReceiveBoot` running as
`NT AUTHORITY\LocalService`. Reopen `http://127.0.0.1:17882/` and verify the
release is Build 93, reporting is the intended mode, the receiver is scanning,
and observation/audio queue depths are not stuck.

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
