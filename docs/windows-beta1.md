# Windows Beta 1 owner guide

## Download

Download the [Build 93 Windows ZIP](https://github.com/gdowkpc/apollo-public-release/releases/download/windows-v1.0.0-beta1-build93/ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip).

After the download finishes, open the ZIP file and select **Extract All**. Choose
a new folder, such as `C:\ApolloPassiveReceive`, and select **Extract**. Run
Apollo from that extracted folder; do not run it from inside the ZIP file, and do
not move or delete individual files from the folder.

If Windows does not recognize the RTL-SDR, use Zadig to install WinUSB for
**RTL-SDR interface 0** only. Do not change drivers for other USB devices.

## First launch and local UI

Run `Start Apollo Passive Receive.cmd`. Open
`http://127.0.0.1:17882/` on that Windows computer.

On the first-run page:

1. Confirm the bundled RTL-SDR runtime is ready and device index `0` is the
   intended receiver.
2. Select a scan plan and ranges appropriate for the test location.
3. Leave RTL-SDR gain blank for automatic selection unless the test plan gives
   an exact fixed gain.
4. Leave **Reference calibration** set to **Automatic**. This is the normal
   choice. Select **Not applicable** only if your test instructions specifically
   tell you to.
5. Leave **Start automatically next launch** selected when unattended operation
   is intended.
6. Select **Start Passive Observation**. After later edits, use **Save Scan Plan
   and Restart**.
7. In **Receiver self-test**, select **Validate and start receiver** and require
   a ready/running receiver before continuing.

The UI is intentionally localhost-only. Do not create a firewall exception.

## Identity, location, and reporting

Check **Device authorization**:

1. If the status says **Ready for RepeaterBook**, continue. No action is needed.
2. Otherwise, select **Copy authorization request** and send the copied text to
   the Beta coordinator. It contains no password or device credential.
3. After the coordinator confirms this Device ID, return to this panel and select
   **Revalidate authorization**.

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

## Change log

### Build 93

Build 93 fixes a delivery condition where one stalled network operation could
indefinitely prevent later queued observations from being sent. Observation and
audio delivery operations are now bounded; an item that encounters a transient
timeout remains queued and retries through the normal sender. The local support
view shows the sender state, current observation, last attempt, and scheduled
retry without exposing credentials.
