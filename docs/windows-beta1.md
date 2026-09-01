# Windows Beta 1 owner guide

## Download

Download the [Build 93 Windows ZIP](https://github.com/gdowkpc/apollo-public-release/releases/download/windows-v1.0.0-beta1-build93-r3/ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip).

After the download finishes, open the ZIP file and select **Extract All**. Choose
a new folder, such as `C:\ApolloPassiveReceive`, and select **Extract**. Run
Apollo from that extracted folder; do not run it from inside the ZIP file, and do
not move or delete individual files from the folder.

If Windows does not recognize the RTL-SDR, use Zadig to install WinUSB for
**RTL-SDR interface 0** only. Do not change drivers for other USB devices.

## First launch and local UI

Double-click `Start Apollo Passive Receive.cmd`. A command window will stay open
while Apollo is running; this is expected. Do not type into it or close it while
you are using Apollo.

After the command window appears, double-click `Open Apollo Local UI.url` in the
same extracted folder. It opens the Apollo setup page in your web browser. If the
shortcut does not open, manually enter the address below.

Open a separate browser window on the same Windows computer and go to
`http://127.0.0.1:17882/`. This local web page is where you complete setup and
control Apollo. Do not open this address in a remote or in-app browser:
`127.0.0.1` always means the computer where Apollo is running.

On the first-run page:

1. Confirm the bundled RTL-SDR runtime is ready and device index `0` is the
   intended receiver.
2. Select a scan plan and ranges appropriate for the test location.
3. Leave RTL-SDR gain blank for automatic selection unless the test plan gives
   an exact fixed gain.
4. Leave **Reference calibration** set to **Automatic**.
5. Leave **Start automatically next launch** selected when unattended operation
   is intended.
6. Select **Start Passive Observation**. After later edits, use **Save Scan Plan
   and Restart**.
7. In **Receiver self-test**, select **Validate and start receiver** and require
   a ready/running receiver before continuing.

The UI is intentionally localhost-only. Do not create a firewall exception.

## Identity, location, and reporting

Apollo creates the Device ID automatically the first time it starts. You do not
need to enter a Device ID, username, password, or provisioning command on
Windows.

Scroll down to **Device authorization** and check its status:

1. If the status says **Ready for RepeaterBook**, continue. No action is needed.
2. Otherwise, select **Copy authorization request** and send the copied text to
   the Beta coordinator. It contains no password or device credential.
3. After the coordinator confirms this Device ID, return to this panel and select
   **Revalidate authorization**.

Enter the receiver's actual latitude and longitude under **Receiver location**,
then select **Save Authorized Location**. These coordinates let RepeaterBook
authorize and support the node's configured receiver location. The exact
coordinates are stored in protected policy and are not published as the public
node location or listing. The save succeeds only after the existing Device ID is
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

### Build 93 R3

The refreshed Windows package adds `Open Apollo Local UI.url` beside the launcher
so the owner can open the local setup page without typing the address. It also
shows the release Build in the page header and provides a visible **Back to
dashboard** control while editing settings.
