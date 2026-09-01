# Apollo Beta 1 clean-install checklist

Garrett should perform this checklist using only this public repository and its
linked release assets. Record exact hash output and stop at the first mismatch.
Do not use a development checkout, retained credential, manual allowlist entry,
or hidden deployment command.

## Common preflight

- [ ] Start with the intended clean test machine/device and supported receiver.
- [ ] Download only the asset linked from this repository.
- [ ] Verify filename, byte size, and SHA-256 against the frozen manifest.
- [ ] Record OS/device version and whether this is a clean install or supported
      in-place upgrade.
- [ ] Treat no organic RF traffic and ordinary matcher ambiguity as non-failures.

## Windows x64 — Build 93

- [ ] Follow the [Windows owner guide](windows-beta1.md).
- [ ] Extract the entire ZIP and launch only `Start Apollo Passive Receive.cmd`.
- [ ] Open `http://127.0.0.1:17882/`; record Build 93 and source `56e6a907…`.
- [ ] Complete the first-run scan plan. Confirm **Reference calibration** is
      **Automatic**, or record why the test plan requires **Not applicable**.
- [ ] Run **Validate and start receiver** and require ready/scanning state.
- [ ] Copy the non-secret Device authorization request; do not expose a token.
- [ ] Confirm the coordinator has authorized this exact Device ID and installed
      the approved credential-free production Review policy.
- [ ] Only then install the boot service and verify LocalService, automatic
      start, Build 93, intended reporting mode, queue health, and UI access.
- [ ] In the support view, confirm the sender is not stuck in-flight, the
      observation/audio queues are not stuck, and any transient delivery retry
      retains the current queue head.
- [ ] Observe one organic qualified event if RF traffic occurs; verify its audio
      association and no duplicate. Absence of traffic is not a failure.
- [ ] Record exact-device unattended RTL recovery as **installed — organic fault
      qualification pending**. Do not induce a hardware fault.

Stop and report `WINDOWS OWNER INSTALL BLOCKED` if the coordinator prerequisite
cannot be completed through the public owner workflow.

## Raspberry Pi 5 / Raspberry Pi OS 64-bit — Build 92

- [ ] Confirm a fresh Raspberry Pi 5 Model B running Raspberry Pi OS (64-bit),
      Debian 13 `trixie`, with account `pi`, network access, a supported
      RTL-SDR, and at least 2 GiB free.
- [ ] Follow only the [Pi owner guide](pi-beta1.md).
- [ ] Download `apollo-pi-bootstrap-beta1.sh` from release
      `pi-bootstrap-v1.0.0-beta1-r2`.
- [ ] Verify its SHA-256 is
      `d36b3b876b93aea02c2bbbba48f2d57ce3e3d9e7657be65b8723774cbb82a7d9`.
- [ ] Run the single documented `sudo bash apollo-pi-bootstrap-beta1.sh`
      command. Do not supply arguments.
- [ ] Confirm all bounded stages complete and the script independently verifies
      the public Build 92 ZIP as
      `ee3819e971aa49b856da8045f2447baff3fc4d871d573cffe7e3ff5dc02dc071`.
- [ ] Confirm Build 92 is the initial protected rollback baseline and that no
      historical Build 55 release or custody record was created.
- [ ] Enter this receiver's decimal location and sign in interactively to
      RepeaterBook; verify no password appears in shell history.
- [ ] Record the new Device ID. Confirm it is unique and do not reuse any desk
      Pi identity or credential.
- [ ] If approval is pending, run `apollo-onboard check-approval` until the
      established flow reports registration complete.
- [ ] Access `http://127.0.0.1:17882/` locally or through the documented SSH
      tunnel; do not expose the port to the LAN.
- [ ] Confirm Build 92, source `a7a8447f…`, node-agent Build 50,
      `production_review`, and required audio.
- [ ] Save intended scan bands/ranges and choose **Automatic** or explicitly
      justified **Not applicable** reference calibration.
- [ ] Run **Validate and start receiver**; require receiver open, ready, and
      changing scan state.
- [ ] Record the Device ID, reboot the Pi, and confirm both services return,
      the same Device ID remains, the UI returns, and scanning resumes.
- [ ] Confirm observation and audio queues are empty or actively draining.
- [ ] If organic RF occurs, verify one qualified observation/audio association,
      no duplicate report, and continued scanning. Absence of traffic is not a
      failure.
- [ ] Confirm no private source checkout, copied credential, manual JSON edit,
      or internal deployment command was needed.

Stop and preserve state at the first bootstrap error. Do not manually repair
service, policy, allowlist, identity, custody, or rollback files.

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

Record PASS/FAIL/BLOCKED separately for Windows, Pi, and CJ-1. The clean Pi
result is complete only after the new physical Pi proves receiver readiness,
reboot persistence, stable identity, and resumed scanning; userspace/package
qualification alone does not substitute for those checks.
