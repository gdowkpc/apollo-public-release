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

## Windows and Raspberry Pi downloads

The authoritative current downloads and retained recovery installers are on
[RepeaterBook Live Downloads](https://www.repeaterbooklive.com/apollo/downloads/).

| Platform | Current release | Owner guide | Release |
| --- | --- | --- | --- |
| Windows x64 | Apollo 1.0.0, Build 123 stable | [Windows owner guide](https://www.repeaterbooklive.com/apollo/downloads/windows.php) | [Build 123](https://github.com/gdowkpc/apollo-releases/releases/tag/apollo-passive-v1.0.0-build.123) |
| Raspberry Pi 3B, 4B, 5B / Linux ARM64 | Apollo 1.0.0, Build 124 beta | [Clean-install Pi owner guide](docs/pi-build124-clean-install.md) | [Bootstrap R7](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-bootstrap-v1.0.0-beta1-r7-build124) / [Build 124](https://github.com/gdowkpc/apollo-public-release/releases/tag/pi-v1.0.0-beta1-build124) |

These builds add owner-confirmed installation of newer stable releases. Run the
Windows installer once to enable its protected update helper. Pi Bootstrap R7
includes the matching helper and requires a fresh supported SD image. Equal or
older builds are not installed, and update checks never install on their own.

[Build 125 receiver tests](https://github.com/gdowkpc/apollo-public-release/releases/tag/receiver-parity-v1.0.0-build125)
are optional and are not selected by stable update discovery. Their Pi ZIP is
not a clean installer. Physical Pi installation and receiver/reporting
qualification remain pending; local package checks and ARM64 emulation do not
establish physical qualification. Windows update-installation testing is also
separate from the retained Build 116 receiver evidence.

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

Previous Pi clean-bootstrap releases, the original
[Beta 1 artifact manifest](docs/beta1-artifact-manifest.md), and its
[clean-install checklist](docs/beta1-clean-install-checklist.md) remain available
for history. New Pi installations should use the current installer and guide
linked above. Retain existing SD cards and node data when using recovery builds.

## Publication policy

Artifacts are published only after exact-identity authorization. A release does
not authorize a different build, changed bytes, automatic installation,
production signing, or a relaxation of device/reporting policy.
