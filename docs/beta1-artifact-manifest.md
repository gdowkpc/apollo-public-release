# Apollo Beta 1 frozen artifact manifest

Verify the complete SHA-256 before installing. Do not substitute a similarly
named build.

## Windows x64

- Release: `windows-v1.0.0-rc2-build90`
- Asset: `ApolloPassiveReceive-1.0.0-rc2-build90-windows-x64-portable.zip`
- Size: `15,011,878` bytes
- ZIP SHA-256: `5cd9d16fe84d2d04d53716ad9a2d2c5e4ce12b53d27581c5f663704e73b6f40b`
- Source: `ebb1e1c83911a2a8e545abce28fc561f691624af`
- Release Build: `90`
- `ApolloPassiveReceive.exe` SHA-256: `82c1cb990553353aa184843df41d8768bb5da00c267c396a984f0bec762ab122`
- `rtl_fm.exe` SHA-256: `c4f13e02d230f0401300f640928a079f62c7637055b8b777aa23a47ff0e18fd9`
- Boot-service installer SHA-256: `7f028a36116e4b468d2b2637db16701c4d8462ce0daab6fb64ec66c05dbcc9c4`
- Canonical inner inventory SHA-256: `0011739b2427084c9aad51b5c5b22f4b1988cb9da489d93fde08f1a26e44a14e`

The qualified Windows node reports the same Build 90 source identity and
packaged RTL runtime hashes while running as the automatic
`ApolloPassiveReceiveBoot` service under `NT AUTHORITY\LocalService`.

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

- Bootstrap release: `pi-bootstrap-v1.0.0-beta1`
- Script: `apollo-pi-bootstrap-beta1.sh`
- Script size: `19,158` bytes
- Script SHA-256: `02bbe13df5bb9015a24b510d7ab324d4ef590c3c2ea19869234c4e362c85ef65`
- Payload: `apollo-pi-bootstrap-beta1-payload.tar.gz`
- Payload size: `33,522` bytes
- Payload SHA-256: `077f88e37373354d3712a530c3eb5cc9ad5a4bd97eaa50707f59357a43b895a6`

The bootstrap is installation tooling, not another receiver build. It admits
only the exact Build 92 identity above and does not replace its release asset.

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
