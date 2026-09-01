# Apollo Beta 1 clean-install checklist

Garrett should perform this checklist using only this public repository and its
linked release assets. Record the exact output for every hash and stop at the
first mismatch. Do not use a development checkout, retained credential, manual
allowlist entry, or hidden deployment command.

## Common preflight

- [ ] Start with the intended clean test machine/device and supported receiver.
- [ ] Download only the asset linked from this repository.
- [ ] Verify filename, byte size, and SHA-256 against the frozen manifest.
- [ ] Record OS/device version and whether this is a clean install or supported
      in-place upgrade.
- [ ] Treat no organic RF traffic and ordinary matcher ambiguity as non-failures.

## Windows x64 — Build 90

- [ ] Follow the [Windows owner guide](windows-beta1.md).
- [ ] Extract the entire ZIP and launch only `Start Apollo Passive Receive.cmd`.
- [ ] Open `http://127.0.0.1:17882/`; record Build 90 and source `ebb1e1c8…`.
- [ ] Complete the first-run scan plan. Confirm **Reference calibration** is
      **Automatic**, or record why the test plan requires **Not applicable**.
- [ ] Run **Validate and start receiver** and require ready/scanning state.
- [ ] Copy the non-secret Device authorization request; do not expose a token.
- [ ] Confirm the coordinator has authorized this exact Device ID and installed
      the approved credential-free production Review policy.
- [ ] Only then install the boot service and verify LocalService, automatic
      start, Build 90, intended reporting mode, queue health, and UI access.
- [ ] Observe one organic qualified event if RF traffic occurs; verify its audio
      association and no duplicate. Absence of traffic is not a failure.

Stop and report `WINDOWS OWNER INSTALL BLOCKED` if the coordinator prerequisite
cannot be completed through the public owner workflow.

## Raspberry Pi / Linux ARM64 — Build 92

- [ ] Verify the Build 92 ZIP and its SHA-256.
- [ ] Confirm whether the Pi already has the supported Apollo managed-release
      bootstrap and device identity.

For a clean Pi, stop before extraction or system changes and report:

`PI OWNER INSTALL BLOCKED — PUBLIC CLEAN-PI BOOTSTRAP IS MISSING`

Do not manually create credentials, policies, allowlists, custody directories,
service units, rollback state, or a managed-release baseline. Build 92 cannot
pass this clean-install checklist until a generic supported bootstrap is
published and separately qualified.

For an already managed Pi only, the coordinator may run the existing managed
release procedure. Afterward:

- [ ] Verify Build 92/source `a7a8447f…` and node-agent Build 50.
- [ ] Access the loopback UI locally or through the documented SSH tunnel.
- [ ] Confirm the intended ranges and **Automatic**/**Not applicable** reference
      choice, then validate/start the receiver.
- [ ] Verify `production_review`, queue health, scanning continuity, and one
      organic audio-backed delivery if RF traffic occurs.

## CJ-1 — Build 115

- [ ] Follow the [CJ-1 owner guide](cj1-beta1.md).
- [ ] Verify APK size/hash, then use `adb install -r`.
- [ ] Confirm package `org.gdowkpc.apollo_node_shell`, version code 115, and app
      label **Apollo Listening**.
- [ ] Grant the requested Android permissions.
- [ ] Sign in through **RepeaterBook node sign-in**; confirm a local node ID and
      assigned scan plan.
- [ ] Select **Start** and verify the foreground service and changing scan state.
- [ ] Confirm reporting state, outbox/audio queue health, and correct evidence
      association for an organic qualified event if RF traffic occurs.
- [ ] Verify no duplicate report and continued scanning.

## Result

Record PASS/FAIL/BLOCKED separately for Windows, Pi, and CJ-1. The current
frozen packages support a complete CJ-1 install/upgrade path and a bounded
Windows owner setup with coordinator authorization. The public clean-Pi path is
blocked at its first product bootstrap step; do not call the three-platform
owner-install gate complete until that is resolved.
