# Apollo Windows Beta 1 — Build 97

Build 97 is the corrected clean Windows owner-install candidate for end-to-end
controlled Beta testing.

- Opens the owner UI automatically from the installed shortcut and post-install
  action after a bounded localhost readiness check.
- Starts a clean installation at **Connect to RepeaterBook** before exposing
  receiver setup.
- Preserves automatic canonical node provisioning and the protected Windows
  LocalService credential transition.
- Guides the owner through receiver location, scan-plan selection, and receiver
  start only after identity and protected service setup are complete.
- Carries forward the Build 93 bounded sender repair and the qualified Windows
  receiver, gain, audio, reporting, and unattended recovery behavior.

Exact identity:

- Version: `1.0.0`
- Build: `97`
- Source: `154656cd1eaa8bf3e3203e8b37ad93cd1de1855a`
- Installer SHA-256: `29fe00aba708f1b3b53e6a6ca5b1437233fe9e9d359bf9c3c496481c48b0b1fc`
- Portable ZIP SHA-256: `3221557fad55fb99c27c6ee30336d5dd05edcbaf4615ccfe7c076365c6189f8a`

Build 96 remains available as a historical prerelease and should not be used
for the clean-owner end-to-end test.
