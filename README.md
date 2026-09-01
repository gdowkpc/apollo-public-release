# Apollo public releases

This repository is the public download and owner-documentation home for Apollo
controlled Beta software. Large binaries are attached to GitHub Releases rather
than committed to Git.

## Beta 1 candidates

| Platform | Frozen candidate | Owner guide | Release |
| --- | --- | --- | --- |
| Windows x64 | Apollo Passive Receive 1.0.0 RC2, Build 90 | [Windows owner guide](docs/windows-beta1.md) | [Download](https://github.com/gdowkpc/apollo-public-release/releases/tag/windows-v1.0.0-rc2-build90) |
| Raspberry Pi / Linux ARM64 | Apollo Passive Receive 1.0.0, Build 92 | [Pi owner guide](docs/pi-beta1.md) | [Download](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build92) |
| CJ-1 | Apollo Listening 1.0.12-provider-evidence.2, Build 115 | [CJ-1 owner guide](docs/cj1-beta1.md) | [Download](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build115) |

Use the [frozen artifact manifest](docs/beta1-artifact-manifest.md) to verify
every download. Garrett's end-to-end procedure is the
[clean-install checklist](docs/beta1-clean-install-checklist.md).

Pi Build 92 is currently a qualified managed-update payload, not a clean-Pi
bootstrap installer. That limitation is called out in the Pi guide and causes
the clean-install checklist to stop before modifying a clean Pi. It must not be
bypassed by manually constructing credentials, allowlists, custody directories,
or service state.

## Historical releases

Apollo CJ-1 1.0.2 Build 69 remains available at its
[historical release](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.2).
It is not the qualified CJ-1 Beta 1 artifact.

## Publication policy

Artifacts are published only after exact-identity authorization. A release does
not authorize a different build, changed bytes, automatic installation,
production signing, or a relaxation of device/reporting policy.
