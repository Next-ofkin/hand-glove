# Decisions and build log

Dates use **Africa/Lagos**. Statuses describe recorded evidence.

## Current status: 7 November 2026

| Workstream | Status | Evidence / next action |
| --- | --- | --- |
| DIY ownership and staged plan | Documented | Owner assembles and tests; local help for specified soldering jobs |
| Candidate architecture and parts | Documented, unvalidated | Confirm board choice and obtain sensor geometry/sample quotes |
| Supplier contact / purchasing | No confirmed order recorded | Record quotes and actual orders below |
| Simulator and packet model | Pending | Define and implement |
| Firmware and receiver code | Pending | Establish toolchain and upload/recovery procedure |
| Board-specific wiring and pin table | Pending | Produce for actual selected hardware before soldering |
| Soldering and bench electronics | Pending | Start with agreed headers/connectors and isolated module checks |
| Fitted index/thumb sample | Pending | First physical validation milestone |
| Wireless Hand Graph integration | Pending | Prove sample over the proposed receiver path |
| Full hand, battery and haptics | Pending | Expand after the sample gate |
| Compact USB-C pod and final textile | Pending | Design after the working prototype |

## Decision record

| Date | Decision | Reason / consequence |
| --- | --- | --- |
| 2026-11-07 | Use a DIY build led by the owner in Nigeria | Owner sources, assembles, loads software, calibrates and tests |
| 2026-11-07 | Use local electronics help for defined soldering tasks | Keep a small task sheet, joint checks and functional acceptance for each visit |
| 2026-11-07 | Buy standard parts locally where suitable and import specialist items as needed | Exact local stock for all selected parts remains unconfirmed |
| 2026-11-07 | Test index/thumb samples before a full sensor order | Sensor-zone geometry and mounting still need validation |
| 2026-11-07 | Carry forward the latest nRF52840 dedicated-receiver proposal | The earlier ESP32/BLE outline is archived; firmware and radio development remain open |
| 2026-11-07 | Target 16 baseline sensing channels; defer spread sensing | Independent joint readings require suitable zones and calibration |
| 2026-11-07 | Use USB bench power before wearable battery tests | Isolate circuit and software behaviour before adding the battery |
| 2026-11-07 | Defer compact PCB and USB-C packaging | Learn from a working development-board prototype first |
| 2026-11-07 | Treat the earlier roughly ₦40,000 figure as historical | It covered the simpler concept and is not the full-design budget |

## Spending and orders

No completed purchase is recorded by this update.

| Date | Item / exact model | Supplier | Qty | Currency / unit quote | Delivery / import charges | Actual landed cost | Order status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pending | Pending | Pending | Pending | Pending | Pending | Pending | Not ordered |

Record soldering labour, tools and fabrication as separate entries. Keep original currencies and date any conversion rate used.

## Session log

| Date | Stage | Work performed | Evidence | Result / blocker | Next action |
| --- | --- | --- | --- | --- | --- |
| 2026-11-07 | M0 | Documented current design and owner-led DIY route | README, plan, BOM, build sequence, soldering brief and test checklist | Documentation updated; no hardware or software acceptance claimed | Confirm exact boards, toolchain and sample sensor geometry |

## New session template

Copy this section for each work session.

### YYYY-MM-DD: short session title

- Stage:
- Exact parts and wiring revision:
- Firmware/app commit:
- Changes made:
- Tests and measurements:
- Evidence location:
- Pass / fail / blocked:
- Cost incurred:
- Open issues:
- Next small action:

Keep quotes, received-part photos, as-built wiring evidence and raw test logs tied to the corresponding session. Document substitutions and failed experiments so later changes remain understandable.
