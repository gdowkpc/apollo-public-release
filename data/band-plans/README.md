# Downloadable repeater-output scan-band profiles

The timestamped JSON file is downloadable profile data for broad receiver sweeps. It contains no receiver binary, individual repeater targets, directory IDs, callsigns, coordinates, tones, credentials, or deployment manifest.

Segments are inclusive integer-Hz RF coverage ranges for the named band-plan allocation. They preserve gaps between allocations and are not a claim that every frequency is occupied. A profile remains an operator-selected scan choice; it does not identify a signal as a particular repeater or grant operating authority.

## `gb-rsgb`

The [RSGB Band Plan January 2026](https://rsgb.services/public/bandplans/docs/260125_rsgb_band_plan_2026.pdf) provides the two included bands. Its 2m table gives the 145.5935–145.7935 MHz RV48–RV63 repeater-output allocation. Its 70cm table gives 430.8125–430.9750 MHz RU65–RU78 repeater outputs and the 432.9940–433.3810 MHz output allocation, including 433.0000–433.3750 MHz UK repeater-output channels. The JSON preserves those exact table allocation boundaries; it does not truncate them to channel centres.

The source also lists isolated output assignments narrower than the default 25 kHz scan bin. They are omitted without widening them. The optional `recommendation_bounds` is a coarse UK envelope for a suggestion only; it never auto-applies the profile.

## `us-sera`

The [SERA Coordination Policy and Guidelines, revision June 9 2024](https://sera.org/wp-content/uploads/2024/07/SERA-CPG-Rev-06-09-2024.pdf) defines NBD as including D-Star, NXDN, P25, DMR, 2.5 kHz analogue, and 2.5 kHz analogue mixed-mode use. Its 2m table lists outputs 144.920–144.980, 145.020–145.080, 145.110–145.450, and 145.120–145.460 MHz. The JSON takes the union of the overlapping latter two ranges: 145.110–145.460 MHz. The [SERA 144 MHz FUP](https://sera.org/wp-content/uploads/2016/11/sera-fup-144.pdf) confirms the standard 146.610–147.390 MHz repeater-output span.

The SERA 440 MHz table lists outputs 440.5125–440.7250, 441.8000–444.9750, and 441.8125–444.9875 MHz. The JSON preserves the first gap-separated range and takes the coverage union of the latter overlap: 441.8000–444.9875 MHz. This produces non-overlapping continuous sweep coverage without inventing a channel raster.

SERA coordination territory cannot be accurately expressed as a simple rectangle, so this profile intentionally has no geographic recommendation bounds.

## Downloading and updates

Apollo Build 122 and later checks `manifest.json` for availability. Profile data downloads only after the operator explicitly chooses Download. Selecting bands and applying a profile fills the normal editable custom scan configuration; saving remains a separate operator action. The packages contain no geographic profile dataset.

For maintainers: prepare reviewed source data with Apollo's `tools/prepare_band_plan_data.js`, using a newer UTC publication timestamp. Publish the resulting immutable timestamped JSON file first and verify its public SHA-256. Publish `manifest.json` last, retaining its matching filename, timestamp, and hash. Keep existing timestamped files available for clients that already fetched an earlier manifest. Data updates require no application rebuild.
