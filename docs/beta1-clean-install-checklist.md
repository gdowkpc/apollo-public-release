# Apollo Beta 1 clean-install checklist

Garrett should perform this checklist using only this public repository and its
linked release assets.
Do not use a development checkout, retained credential, manual allowlist entry,
or hidden deployment command.

## Common preflight

- [ ] Start with the intended clean test machine/device and supported receiver.
- [ ] Download only the asset linked from this repository.
- [ ] Record OS/device version and whether this is a clean install or supported
      in-place upgrade.
- [ ] Treat no organic RF traffic and ordinary matcher ambiguity as non-failures.

## Windows x64 — Build 93

- [ ] Follow the [Windows owner guide](windows-beta1.md).
- [ ] Download `ApolloPassiveReceive-1.0.0-build.93-windows-x64.zip`.
- [ ] Open or extract the ZIP with Windows Explorer and confirm the application,
      launcher, `Open Apollo Local UI.url`, `sdr`, and `windows-support` contents
      are visible.
- [ ] Extract the entire ZIP and launch only `Start Apollo Passive Receive.cmd`.
- [ ] Double-click `Open Apollo Local UI.url` in the extracted folder. If needed,
      open `http://127.0.0.1:17882/` manually on the same Windows computer.
- [ ] Confirm the page reports Build 93 and source `c8129afa…`.
- [ ] Complete the first-run scan plan. Leave **Reference calibration** set to
      **Automatic**.
- [ ] Run **Validate and start receiver** and require ready/scanning state.
- [ ] Copy the non-secret Device authorization request; do not expose a token.
- [ ] Confirm the coordinator has authorized this exact Device ID and installed
      the approved credential-free production Review policy.
- [ ] Enter the receiver's actual latitude and longitude and save the authorized
      location. These coordinates are protected and are not published as the
      public node location or listing.
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
- [ ] Run the single documented `sudo bash apollo-pi-bootstrap-beta1.sh`
      command. Do not supply arguments.
- [ ] Confirm all bounded stages complete and Build 92 is installed.
- [ ] Confirm Build 92 is the initial protected rollback baseline and that no
      historical Build 55 release or custody record was created.
- [ ] When the bootstrap asks for **Latitude** and **Longitude**, enter this
      receiver's actual decimal location. Confirm the guide's privacy note:
      exact coordinates are protected and are not published as a public node
      location or listing.
- [ ] When `apollo-onboard` prompts for **RepeaterBook username or email** and
      **RepeaterBook password**, enter the owner's account credentials at those
      prompts. Confirm the password is not echoed or placed in shell history,
      and that only the issued per-device node credential is retained.
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
