# Windows Beta 1 owner guide

## Download and verify

Download the ZIP from the [Build 90 release](https://github.com/gdowkpc/apollo-public-release/releases/tag/windows-v1.0.0-rc2-build90).
In Command Prompt, verify it before extraction:

```bat
certutil -hashfile ApolloPassiveReceive-1.0.0-rc2-build90-windows-x64-portable.zip SHA256
```

The result must be
`5cd9d16fe84d2d04d53716ad9a2d2c5e4ce12b53d27581c5f663704e73b6f40b`.

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
release is Build 90, reporting is the intended mode, the receiver is scanning,
and observation/audio queue depths are not stuck.

## Everyday controls and support

- **Edit Receiver Settings** changes the scan plan and restarts through the
  validated settings path.
- **Test receiver** reruns the bounded receiver check.
- **Export Diagnostics** creates a sanitized local support report.
- The optional USB stability action is not part of normal installation. Use it
  only for a confirmed long-run USB suspend/recovery problem.
- Removing the application data destroys this Device ID and credential. Do not
  do that during an upgrade or ordinary troubleshooting.
