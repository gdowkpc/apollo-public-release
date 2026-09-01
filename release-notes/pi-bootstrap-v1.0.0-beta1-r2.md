# Apollo Pi Beta 1 clean-install bootstrap R2

This prerelease contains owner-facing installation tooling for a supported,
fresh Raspberry Pi 5. It downloads and installs the unchanged public Build 92
receiver package; it is not a new receiver build.

R2 makes the exact Build 92 package identified by clean-install policy the
node's first known-good rollback baseline. It no longer assumes or fabricates
custody of a historical release. Existing upgraded nodes keep their actual
historical rollback state.

The bootstrap remains initial-install-only and fails closed for unsupported or
pre-existing Apollo installations, missing baseline policy, or any package,
inventory, executable, or source-identity mismatch.

Exact assets:

- `apollo-pi-bootstrap-beta1.sh` — 15,749 bytes — SHA-256
  `d36b3b876b93aea02c2bbbba48f2d57ce3e3d9e7657be65b8723774cbb82a7d9`
- `apollo-pi-bootstrap-beta1-payload.tar.gz` — 34,937 bytes — SHA-256
  `2e3724d5ca8f7121bf26902fa9adeba5318faa84164d218a91faeb4e2a5c24d9`

Bootstrap source: `879bf6c6e469e955248fb9896b0d67e0de772240`

Consumed receiver release:

- Build 92 source: `a7a8447f88c1159effb762dcf1f6c7b6764707d7`
- Build 92 ZIP SHA-256:
  `ee3819e971aa49b856da8045f2447baff3fc4d871d573cffe7e3ff5dc02dc071`
