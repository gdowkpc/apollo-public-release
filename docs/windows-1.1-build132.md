# Apollo Windows 1.1 Build 132

Build 132 is a controlled beta for Windows x64 with a compatible RTL-SDR
receiver. It shortens the idle broad-sweep interval to two seconds when the
receiver has classified a band with no energy candidates. Energy candidates
keep the configured active dwell.

Download the installer or portable ZIP from the linked Build 132 release and
verify the published SHA-256 first. The installer is owner-initiated. Do not
overwrite a protected installation, copy credentials between nodes, or use an
unapproved upgrade path. Existing nodes must preserve their identity, settings,
and retained observations.

This package includes the RTL-SDR runtime only. Install the required WinUSB
driver for the receiver interface. SDRplay components are not included in this
Windows package.

Package and installer checks passed. Physical installation, RF reception,
organic reporting, matching, and Review qualification remain pending.
