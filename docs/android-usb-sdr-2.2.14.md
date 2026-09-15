# RepeaterBook Live for Android 2.2.14 (Build 165)

Build 165 is the current stable, manual-download release of RepeaterBook Live for Android USB SDR monitoring.

## Download and verify

Download `app-controlledBeta.apk` from the [Build 165 release](https://github.com/gdowkpc/apollo-public-release/releases/tag/android-usb-sdr-v2.2.14-build165).

Before installing, verify its SHA-256 checksum:

```text
eaa2fd4fc23365ef740ee6842b5b9235a067cafb3fc8045c19766b8de6cfd9b5  app-controlledBeta.apk
```

## Install

1. Open the downloaded APK on the Android device and allow the browser or Files app to install unknown apps if Android asks.
2. Install the APK, then open **RepeaterBook Live**.
3. Connect a compatible USB SDR through a USB OTG adapter. Install **SDR Driver by Signalware Ltd.** if Android asks for the SDR driver.
4. Open **Settings**, complete Receiver Setup and Reporting Setup, then select **Start Monitoring** on the Receive page.

The app automatically stops, applies, and restarts monitoring when a saved receiver selection requires it.

## Existing installations

Build 165 is protected-signed. A legacy debug-signed installation cannot update in place: uninstall that legacy copy first, which removes its local app data, then install Build 165. Later updates from the protected-signed release lineage install in place and preserve app data.

This is a stable manual-download release; it does not enable automatic update discovery.
