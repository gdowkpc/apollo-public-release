# Apollo public releases

This repository is the public download and owner-documentation home for Apollo
controlled Beta software. Large binaries are attached to GitHub Releases rather
than committed to Git.

## Beta 1 candidates

| Platform | Frozen candidate | Owner guide | Release |
| --- | --- | --- | --- |
| Windows x64 | Apollo Passive Receive 1.0.0 Beta 1, Build 98 | [Windows owner guide](docs/windows-beta1.md) | [Download installer](https://github.com/gdowkpc/apollo-public-release/releases/download/windows-v1.0.0-beta1-build98/ApolloPassiveReceive-1.0.0-build.98-windows-x64-setup.exe) |
| Raspberry Pi 5 / Linux ARM64 | Apollo Passive Receive 1.0.0, Build 92 | [Clean-install Pi owner guide](docs/pi-beta1.md) | [Bootstrap R2](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-bootstrap-v1.0.0-beta1-r2) / [Build 92](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build92) |
| CJ-1 | Apollo Listening 1.0.12-provider-evidence.2, Build 115 | [CJ-1 owner guide](docs/cj1-beta1.md) | [Download](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build115) |

Use the [frozen artifact manifest](docs/beta1-artifact-manifest.md) to verify
every download. Garrett's end-to-end procedure is the
[clean-install checklist](docs/beta1-clean-install-checklist.md).

Pi Build 92 remains the unchanged qualified managed-update payload. The separate
public bootstrap establishes a supported fresh Raspberry Pi 5, verifies and
installs that exact package, performs canonical onboarding, and leaves future
upgrades to Apollo's normal managed-update path. Bootstrap R2 derives the clean
node's first known-good rollback baseline from exact validated installation
policy; it does not invent historical release custody.

## Historical releases

Apollo Windows RC2 Build 90 remains available at its
[historical release](https://github.com/gdowkpc/apollo-public-release/releases/tag/windows-v1.0.0-rc2-build90).
It is not the current Windows Beta candidate.

Windows Builds 93, 96, and 97 remain available through their historical
prereleases. They are superseded by Build 98 and are no longer the current
owner download.

Apollo CJ-1 1.0.2 Build 69 remains available at its
[historical release](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.2).
It is not the qualified CJ-1 Beta 1 artifact.

The original Pi clean-bootstrap prerelease remains available for history. New
Pi installations must use Bootstrap R2 linked above.

## Publication policy

Artifacts are published only after exact-identity authorization. A release does
not authorize a different build, changed bytes, automatic installation,
production signing, or a relaxation of device/reporting policy.
