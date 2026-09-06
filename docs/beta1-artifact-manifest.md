# Apollo Beta 1 frozen artifact manifest

Verify the complete SHA-256 before installing. Do not substitute a similarly
named build.

## Windows x64 — no current owner download

The Windows download is temporarily unavailable while the next Beta build is
being qualified. Build 98 is retained below as historical failure evidence; it
is not a current, recommended, or installable Beta release.

### Historical non-publishable Build 98

- Historical release identity: `windows-v1.0.0-beta1-build98`
- Historical installer: `ApolloPassiveReceive-1.0.0-build.98-windows-x64-setup.exe`
- Installer size: `12,552,133` bytes
- Installer SHA-256: `bf44963db7cee7ae89f473fb346efe824df18650f9f26fbd7f0bd33a99c68ce3`
- Portable ZIP: `ApolloPassiveReceive-1.0.0-build.98-windows-x64.zip`
- ZIP size: `14,972,687` bytes
- ZIP SHA-256: `583ab1ec73944c0189661c3d101cb287122d50ed8aa52630f3fd5c0358bb6891`
- Source: `7e87866ff1b1310b489c62987ab0a71f0845c477`
- Build timestamp: `2026-09-02T17:08:29.356Z`
- Release Build: `98`
- `ApolloPassiveReceive.exe` SHA-256: `e8b7586b708a3b56edff54a8cea35d6369ba9a21e97126f139fd5bcbfbed01bc`
- `rtl_fm.exe` SHA-256: `c4f13e02d230f0401300f640928a079f62c7637055b8b777aa23a47ff0e18fd9`
- Canonical inner inventory SHA-256: `00106f3a185331213a57de8b0dafd59b1a32fd942d096ca4e247e6ec6edf4e16`

Build 98 was constructed once and admitted through the durable pre-install
retention gate, but it failed clean-install qualification because the packaged
owner application did not expose the authentication-first setup UI. It is
permanently non-publishable. The exact bytes, hashes, and provenance above are
preserved only as historical failure evidence.

Windows RC2 Build 90 remains available at
[`windows-v1.0.0-rc2-build90`](https://github.com/gdowkpc/apollo-public-release/releases/tag/windows-v1.0.0-rc2-build90)
as a historical prerelease. Builds 93, 96, and 97 remain available through their
historical prereleases. The original Build 93 container remains on the
Build 93 release as
`ApolloPassiveReceive-1.0.0-build.93-windows-x64-original-historical.zip` for
historical custody: `15,009,016` bytes, ZIP SHA-256
`eb9346f994196bc865a45e20fd20fb879c53f9e7bc49606c923d0652610eea6c`.
The later Build 93 packages remain unchanged for historical custody.

Qualification also recorded two inherited source-test failures: the Pi
bootstrap hash/line-ending fixture and the same-event audio-recapture timing
test. Both were present on parent `ebb1e1c83911a2a8e545abce28fc561f691624af`
and were not introduced or altered by the Build 93 repair. Exact-device
unattended Windows RTL recovery remains installed with organic fault
qualification pending; no hardware fault was induced for publication.

## Raspberry Pi / Linux ARM64

- Release: `pi-v1.0.0-beta1-build92`
- Asset: `ApolloPassiveReceive-1.0.0-build.92-linux-arm64.zip`
- Size: `17,878,898` bytes
- ZIP SHA-256: `ee3819e971aa49b856da8045f2447baff3fc4d871d573cffe7e3ff5dc02dc071`
- Source: `a7a8447f88c1159effb762dcf1f6c7b6764707d7`
- Release Build: `92`
- Node-agent internal Build: `50`
- Inner inventory SHA-256: `01f7dba98293afedf3c4fa341111018bb611241745d0a9aa1936f746b69a6944`
- `ApolloPassiveReceive` SHA-256: `7335def91c8036d09cbfa2ada333f0444ff24f3c68908124c72a961c5c32ec8a`
- Node-agent SHA-256: `916769e2c34b4ab63ebd9635e300653b9176d367da895cecb3c6bf3f54b2b148`
- `rtl_power` SHA-256: `e6bdf3a1ba496be04b4afa53e04cd5a67d2c0c535250db5150e8426fa758d568`

This exact package remains the qualified, unchanged managed-update payload. The
separate initial-install tooling is:

- Bootstrap release: `pi-bootstrap-v1.0.0-beta1-r2`
- Script: `apollo-pi-bootstrap-beta1.sh`
- Script size: `15,749` bytes
- Script SHA-256: `d36b3b876b93aea02c2bbbba48f2d57ce3e3d9e7657be65b8723774cbb82a7d9`
- Payload: `apollo-pi-bootstrap-beta1-payload.tar.gz`
- Payload size: `34,937` bytes
- Payload SHA-256: `2e3724d5ca8f7121bf26902fa9adeba5318faa84164d218a91faeb4e2a5c24d9`
- Bootstrap source: `879bf6c6e469e955248fb9896b0d67e0de772240`

The bootstrap is installation tooling, not another receiver build. It admits
only the exact Build 92 identity above and does not replace its release asset.
The exact validated clean-install policy makes Build 92 the first known-good
rollback baseline; no historical Build 55 custody is fabricated.

## CJ-1

- Release: `cj1-v1.0.12-beta1-build116`
- Asset: `Apollo-CJ1-1.0.12-beta1-build116.apk`
- Size: `76,887,137` bytes
- APK SHA-256: `05ec5d417e52d17b1dd6f0c458ca2ebacc58cba26c82e7257f27de6a00f72e6c`
- Source: `069cb24773c30cd75f4aa7071f2de72391299b2a`
- Android package: `org.gdowkpc.apollo_node_shell`
- Version name/code: `1.0.12-provider-evidence.3` / `116`
- App label: `Apollo Listening`
- Signer certificate SHA-256: `9824f91945459046d25cce94c83cef8a2b8baba246872377e6cb29fd707a69c0`
- Signature: APK Signature Scheme v2
- Native ABI: `arm64-v8a`

This exact APK was built from the source above and installed in-place on a CJ-1.
The installed APK hash matches the published artifact. The upgrade preserved
node identity, credentials, settings, and retained delivery state. Receiver
scanning resumed and the preloaded notification reported ready; 26 focused
Android tests passed. A fresh over-the-air listening check was not completed
before publication. This notification change does not claim to fix missing
receive audio on short or silent hits.

It remains debug-signed and debuggable for controlled Beta testing. No production
signing or trust-chain claim is made. Public Builds 115 and 69 use the same
package ID and signer, permitting an in-place `adb install -r` upgrade.
