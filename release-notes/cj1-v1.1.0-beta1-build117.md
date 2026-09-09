# Apollo CJ-1 1.1 Beta 1 — Build 117

Optional beta for supported ARM64 CJ-1 devices. Adds KA9Q-style CTCSS analysis
and tighter rejection of off-frequency and harmonic false confirmations.
Stable 1.0 / Build 116 remains available.

## Download and install

Download **Apollo-CJ1-1.1-beta1-build117.apk** from this release or choose **CJ-1 → Test releases**
on [RepeaterBook Live Downloads](https://www.repeaterbooklive.com/apollo/downloads/).
See the [Beta 1 installation guide](https://github.com/gdowkpc/apollo-public-release/blob/cj1-v1.1.0-beta1-build117/docs/cj1-1.1-beta1.md).

This publishes the exact APK already installed and checked on the CJ-1.
Android reports **1.1.0-dev.1**, version code **117**; the public beta designation
does not change the APK. Package: `org.gdowkpc.apollo_node_shell`.
The APK remains a debug build for direct installation.

## Verification

- 42 focused Android tests passed; final APK JNI checks passed.
- Corrected 1,246-case retained corpus: zero wrong-tone confirmations, 857
  correct confirmations, 330 rejections and 59 prior misses. Of the previous
  57 wrong-tone cases, 56 now reject; one AM-carrier expectation was corrected
  to agree with the signal and existing native test. This is offline evidence.
- 215 short-transmission/gap cases were rechecked against the Build 117 source.
- In-place upgrade from Build 116 preserved all 14 captured app-state files.
  Receiver startup and 49 scan acknowledgements across 19 frequencies passed.

## Known beta limitations

Tested continuous tones first confirm after about 1.2 seconds of delivered PCM;
this is not a guarantee for every noisy signal. Some approximately one-second
tones can confirm during a following silence tail. Short gaps depend on phase
and block alignment. Brief close/reopen edges can be missed by the receiver's
roughly 250 ms state polling. Controlled over-the-air tone/gap qualification
and new end-to-end reporting qualification remain pending.

## Artifact identity

- Source: `a0d3868349834d2df7f2f896b2afc0a963a2b9d9`
- APK size: `76,903,265` bytes
- SHA-256: `ade7099d2e411eaff16fb08fb11638781c134e4b256af23031223752647c47eb`

Do not uninstall or clear app data to upgrade. Android normally blocks a
downgrade to Build 116; do not erase node identity or retained state to force it.
This beta is an optional download and does not change automatic update discovery.
