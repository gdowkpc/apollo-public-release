# Apollo Windows Beta 1 — Build 98

Build 98 is the retained clean Windows owner-install candidate for end-to-end
controlled qualification.

- Replaces the incomplete Build 97 browser account-link flow with direct
  RepeaterBook owner authentication from Apollo's localhost-only setup page.
- Creates one canonical Windows Apollo node after successful owner
  authentication and continues through the existing protected LocalService
  credential transition.
- Does not retain the owner's RepeaterBook password.
- Preserves the qualified launch-to-browser flow, Location before Scan Plan,
  Build 93 sender deadline repair, and existing receiver, gain, reporting,
  audio, and guarded RTL recovery behavior.

Exact identity:

- Version: `1.0.0`
- Build: `98`
- Source: `7e87866ff1b1310b489c62987ab0a71f0845c477`
- Build timestamp: `2026-09-02T17:08:29.356Z`
- Installer size: `12,552,133` bytes
- Installer SHA-256: `bf44963db7cee7ae89f473fb346efe824df18650f9f26fbd7f0bd33a99c68ce3`
- Portable ZIP size: `14,972,687` bytes
- Portable ZIP SHA-256: `583ab1ec73944c0189661c3d101cb287122d50ed8aa52630f3fd5c0358bb6891`
- Canonical inner inventory SHA-256: `00106f3a185331213a57de8b0dafd59b1a32fd942d096ca4e247e6ec6edf4e16`

Build 97 remains available as a historical prerelease and should not be used
for the current clean-owner end-to-end test.
