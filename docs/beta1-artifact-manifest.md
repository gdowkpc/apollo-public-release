# Apollo Beta 1 frozen artifact manifest

Verify the complete SHA-256 before installing. Do not substitute a similarly
named build.

## Windows x64

- Release: `windows-v1.0.0-beta1-build96`
- Current owner-download asset: `ApolloPassiveReceive-1.0.0-build.96-windows-x64-setup.exe`
- Installer size: `12,551,244` bytes
- Installer SHA-256: `d4d882c0c560bf1d54a9f18ef91e08a179a6273e4e0925d38802393aeb30aad3`
- Portable ZIP: `ApolloPassiveReceive-1.0.0-build.96-windows-x64.zip`
- ZIP size: `14,971,509` bytes
- ZIP SHA-256: `640ae9934da4302cc92d432a5d0387a4b1e1d5099f61ae9bc340491124761935`
- Source: `20aab0b2dd92791ebad33ef36bc72aa3146c6a1a`
- Build timestamp: `2026-09-02T00:08:20.198Z`
- Release Build: `96`
- `ApolloPassiveReceive.exe` SHA-256: `8412f98ac08bc96a407a68c1f0c0b2d160663a5a560bf8dd008343d369c937ee`
- `rtl_fm.exe` SHA-256: `c4f13e02d230f0401300f640928a079f62c7637055b8b777aa23a47ff0e18fd9`
- Canonical inner inventory SHA-256: `d4a514f347908f67e6db08c6e35973d8a5b3b17ee48825c2ea3717e369a505b5`

Build 96 is the exact retained clean-install candidate. Its installer and ZIP
were constructed once, admitted through the durable pre-install retention gate,
and published without rebuilding. The installer contains the automatic
RepeaterBook provisioning flow and protected LocalService transition. It also
carries forward the Build 93 bounded sender repair.

Windows RC2 Build 90 remains available at
[`windows-v1.0.0-rc2-build90`](https://github.com/gdowkpc/apollo-public-release/releases/tag/windows-v1.0.0-rc2-build90)
as a historical prerelease. Build 93 remains available through its historical
prereleases. The original Build 93 container remains on the
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

- Release: `cj1-v1.0.12-beta1-build115`
- Asset: `Apollo-CJ1-1.0.12-beta1-build115.apk`
- Size: `147,674,811` bytes
- APK SHA-256: `6099e8212b92482fd505911c2627fa288a9940b52fd8296009b9918e9a4db59d`
- Source: `a746f796e22e1e722d92f0d890264463c5aa6f34`
- Android package: `org.gdowkpc.apollo_node_shell`
- Version name/code: `1.0.12-provider-evidence.2` / `115`
- App label: `Apollo Listening`
- Signer certificate SHA-256: `9824f91945459046d25cce94c83cef8a2b8baba246872377e6cb29fd707a69c0`
- Signature: APK Signature Scheme v2
- Native ABIs: `arm64-v8a`, `armeabi-v7a`, `x86_64`

The APK was pulled read-only from the qualified CJ-1 and matched byte-for-byte
to the retained artifact in the clean exact-source worktree. It is debug-signed
and debuggable. No production signing or trust-chain claim is made. Historical
Build 69 uses the same package ID and signer, so Android permits an in-place
`adb install -r` upgrade from that public build.
