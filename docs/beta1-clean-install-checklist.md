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

## Windows x64 — Build 98

- [ ] Follow the [Windows owner guide](windows-beta1.md).
- [ ] Download `ApolloPassiveReceive-1.0.0-build.98-windows-x64-setup.exe`.
- [ ] Verify installer SHA-256
      `bf44963db7cee7ae89f473fb346efe824df18650f9f26fbd7f0bd33a99c68ce3`.
- [ ] Run the installer and accept the normal Windows UAC prompt.
- [ ] Open Apollo from the installed shortcut. If needed, open
      `http://127.0.0.1:17882/` manually on the same Windows computer.
- [ ] Confirm the page reports Build 98 and source `7e87866f…`.
- [ ] Select **Connect to RepeaterBook**, enter the owner's RepeaterBook
      username/password locally, and select **Sign in and connect this node**.
      Confirm the password is not retained.
- [ ] Confirm a new canonical Apollo node is created automatically; record its
      Device ID and public label without exposing its credential.
- [ ] Confirm **Securing Apollo service** invokes normal UAC and completes the
      protected LocalService transition without credential copy/paste or a
      separate service-setup step.
- [ ] Set and save **Receiver Location** before the Scan Plan. Coordinates are
      protected and are not published as the public node location or listing.
- [ ] Select the Scan Plan, leave **Reference calibration** set to **Automatic**,
      and confirm the configured gain is 14.4 dB for this test baseline.
- [ ] Select **Start Receiver** and require ready/scanning state with advancing
      sweeps.
- [ ] Verify LocalService, automatic start, Build 98, `production_review`, queue
      health, and UI access.
- [ ] In the support view, confirm the sender is not stuck in-flight, the
      observation/audio queues are not stuck, and any transient delivery retry
      retains the current queue head.
- [ ] Observe one organic qualified event if RF traffic occurs; verify its audio
      association and no duplicate. Absence of traffic is not a failure.
- [ ] Record exact-device unattended RTL recovery as **installed — organic fault
      qualification pending**. Do not induce a hardware fault.

Stop and report `WINDOWS OWNER INSTALL BLOCKED` at the first owner-flow
divergence. Do not substitute a manual credential, allowlist, service command,
or development checkout.

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
