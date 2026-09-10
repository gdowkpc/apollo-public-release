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

## `de-darc`

The [DARC 2m plan, August 2017](https://www.darc.de/fileadmin/filemounts/referate/vus/bandplaene/VHF_Bandplan_2_m_August_2017.pdf) gives 145.575–145.7875 MHz FM/DV repeater outputs. The current-linked document retains its 2017 date; it was reviewed in September 2026.

Page 2 of the [DARC 70cm plan, May 2025](https://www.darc.de/fileadmin/filemounts/referate/vus/bandplaene/UHF_Bandplan_70_cm_Mai_2025.pdf) separates NBFM outputs (438.550–439.4375 MHz), digital-voice outputs (439.450–439.5875 MHz), and digital/packet duplex outputs. For the latter, footnotes 4 and 6 specify 25 kHz channel centres: the profile uses 438.300–438.525 MHz after excluding the explicitly marked legacy simplex span through 438.275 MHz, and 439.825–439.975 MHz. It preserves the gaps and excludes simplex gateways, repeater inputs, paging and broadband experiments. DARC permits regional FM/DV sharing in some blocks. Including digital RF coverage does not add digital decoding to Apollo.

## `fr-ref`

The REF Commission THF [144 MHz](https://thf.r-e-f.org/plans_des_bandes/144.htm) and [430–440 MHz](https://thf.r-e-f.org/plans_des_bandes/432.htm) tables give 145.575–145.7935 MHz repeater-output allocation and 430.025–430.375 MHz French NBFM output coverage. Their published update date is November 28, 2017; no superseding national output-direction table was found during the September 2026 review. The 430.400–430.575 MHz digital-link/French repeater-input block is excluded, as are output blocks labelled for other countries.

## `at-oevsv`

The official ÖVSV [2m](https://www.oevsv.at/funkbetrieb/ukw-referat/plan/Bandplan-2m/) and [70cm](https://www.oevsv.at/funkbetrieb/ukw-referat/plan/Bandplan-70cm/) pages, retrieved September 2026, explicitly list outputs at 145.575–145.7875 and 437.975–439.0875 MHz. The latter published envelope overlaps the separately listed 438.025 MHz OE Dapnet/POCSAG channel. The profile retains the national output envelope and documents that coexistence; it does not claim every signal within it is a repeater.

## `it-mimit`

The [Italian ministry circular of May 16, 2022](https://www.mimit.gov.it/images/stories/normativa/Circolare_16_05_2022_ripetitori_radioamatoriali.pdf), pages 10–11, explicitly labels output/downlink and input/uplink columns. The profile uses the first-to-last output channel centres: 145.575–145.7875 MHz, 430.025–430.3875 MHz, and 431.225–431.600 MHz. It adds no padding beyond those channels and preserves the UHF gap.

The [ARI bandplan webpage](https://www.ari.it/bandplan.html) reverses the direction labels for the second UHF pair. The ministry's explicit channel table controls this profile: 431.225–431.600 MHz is output; 432.825–433.200 MHz is input. The source was reviewed in September 2026.

All four added profiles are operator-selectable and intentionally omit rectangular recommendation bounds, which would overlap neighbouring countries. They cover the sourced 2m and 70cm output ranges; unsupported bands are omitted. Existing UK and SERA profile definitions are unchanged.

## Downloading and updates

Apollo Build 122 and later checks `manifest.json` for availability. Profile data downloads only after the operator explicitly chooses Download. Selecting bands and applying a profile fills the normal editable custom scan configuration; saving remains a separate operator action. The packages contain no geographic profile dataset.

For maintainers: prepare reviewed source data with Apollo's `tools/prepare_band_plan_data.js`, using a newer UTC publication timestamp. Publish the resulting immutable timestamped JSON file first and verify its public SHA-256. Publish `manifest.json` last, retaining its matching filename, timestamp, and hash. Keep existing timestamped files available for clients that already fetched an earlier manifest. Data updates require no application rebuild.
