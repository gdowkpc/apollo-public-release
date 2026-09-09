# Apollo public releases

This repository is the public download and owner-documentation home for Apollo
software. Large binaries are attached to GitHub Releases rather
than committed to Git.

## CJ-1 1.0 stable

Apollo CJ-1 1.0 is the stable release of **Build 116**. Download
`Apollo-CJ1-1.0-build116.apk` from the
[1.0 release](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.0-build116)
and follow the [CJ-1 owner guide](docs/cj1.md) to verify and install it.

The APK bytes are unchanged from the published Build 116. Its Android version
remains `1.0.12-provider-evidence.3`, version code `116`; **1.0** is the public
release designation. Further KA9Q-style CTCSS work is reserved for 1.1 and is
not included in this promotion. See the [release notes](release-notes/cj1-v1.0.0-build116.md)
for exact provenance and verification limits.

## Beta 1 candidates

| Platform | Frozen candidate | Owner guide | Release |
| --- | --- | --- | --- |
| Windows x64 | Temporarily unavailable while the next Beta build is qualified | [Windows owner guide](docs/windows-beta1.md) | No current download |
| Raspberry Pi 5 / Linux ARM64 | Apollo Passive Receive 1.0.0, Build 92 | [Clean-install Pi owner guide](docs/pi-beta1.md) | [Bootstrap R2](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-bootstrap-v1.0.0-beta1-r2) / [Build 92](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build92) |

For these Beta candidates, use the [frozen artifact manifest](docs/beta1-artifact-manifest.md).
Garrett's end-to-end procedure is the
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
prereleases. Build 98 failed clean-install qualification because its actual
owner application did not expose the authentication-first setup UI. Build 98
is preserved as historical evidence and must not be installed or published as
the current Windows Beta.

Apollo CJ-1 1.0.2 Build 69 remains available at its
[historical release](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.2).
It is not the current CJ-1 release. The
[Build 116 Beta publication](https://github.com/gdowkpc/apollo-public-release/releases/tag/cj1-v1.0.12-beta1-build116)
and its [owner guide](docs/cj1-beta1.md) remain available for history.

The original Pi clean-bootstrap prerelease remains available for history. New
Pi installations must use Bootstrap R2 linked above.

## Publication policy

Artifacts are published only after exact-identity authorization. A release does
not authorize a different build, changed bytes, automatic installation,
production signing, or a relaxation of device/reporting policy.
