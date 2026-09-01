# Apollo Windows Beta 1 Build 93 package revision 2

This prerelease republishes the unchanged, physically qualified Build 93
runtime in a Windows Explorer-compatible ZIP container. The original package
used `./` prefixes for every archive member; command-line and PowerShell ZIP
tools accepted it, but Windows Explorer could report the compressed folder as
invalid or show no files.

No receiver, sender, RF, CTCSS, audio, recovery, configuration, or executable
content changed. All 31 inner files are byte-identical to the qualified Build
93 package.

Exact package:

- Asset: `ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip`
- Size: `15,592,220` bytes
- ZIP SHA-256:
  `d8a395b0a73a1c4d9ae90c56928b128154175fe18706077eca4e49dbd5a85950`
- Canonical inner inventory SHA-256:
  `605390a952c59f0345ba4c0cd23304d29d63656874f8db9aca890b9d78b8690a`
- `ApolloPassiveReceive.exe` SHA-256:
  `a0696b7de55b57bfffa3ea7679c350639087bc89841dbb8567e7d1f4ee53017e`
- `rtl_fm.exe` SHA-256:
  `c4f13e02d230f0401300f640928a079f62c7637055b8b777aa23a47ff0e18fd9`
- Source: `56e6a9079dcbe8eb9952dcd1ab5c7900b6bd9234`

The original Build 93 release remains available for historical identity and
custody. New Windows Beta installations should use this package revision.
