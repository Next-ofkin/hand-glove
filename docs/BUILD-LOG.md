# Decisions and build log

Dates use **Africa/Lagos**. Statuses describe recorded evidence.

**Confirmed scope: one LEFT glove and one RIGHT glove working together.** The previous right-hand-only wording was an assistant documentation error, corrected after the user clarified the requirement. No hardware purchase or build is recorded.

## Current status: 7 November 2026

| Workstream | Status | Evidence / next action |
| --- | --- | --- |
| Two-hand DIY ownership and staged plan | Documented | Owner builds/tests both; local help for specified soldering jobs |
| Measurements | Pending on both hands | Use MEASUREMENTS.md; separate LEFT and RIGHT templates |
| Candidate architecture and pair quantities | Documented, unvalidated | Two controllers/readers/IMUs; one target shared receiver; quote both sensor layouts |
| Supplier contact / purchasing | No confirmed order recorded | Record quotes and actual orders below |
| Two-hand simulator and packet model | Pending | Define identities, independent state, ownership and per-hand timeout behaviour |
| Two glove firmware builds and shared receiver code | Pending | Establish toolchain and upload/recovery on all three devices |
| Board-specific wiring and pin tables | Pending | Label and verify both actual circuits before soldering |
| Soldering and bench electronics | Pending | Start with agreed headers/connectors and isolated module checks |
| LEFT and RIGHT index/thumb samples | Pending | Fit, sense and calibrate each independently |
| Simultaneous wireless Hand Graph integration | Pending | Prove both samples together; test identity, ownership and isolated failures |
| Two full hands, batteries and haptics | Pending | Expand after both samples pass together; target 32 analog channels total |
| Two compact USB-C pods and final textiles | Pending | Design after the full pair works |

## Decision record

| Date | Decision | Reason / consequence |
| --- | --- | --- |
| 2026-11-07 | Correct scope to both hands | User requires LEFT and RIGHT; earlier right-only wording was an assistant error |
| 2026-11-07 | Use a DIY build led by the owner in Nigeria | Owner sources, assembles, loads software, calibrates and tests |
| 2026-11-07 | Use local electronics help for defined soldering tasks | Keep a small task sheet, joint checks and functional acceptance for each visit |
| 2026-11-07 | Buy standard parts locally where suitable and import specialist items as needed | Exact local stock for all selected parts remains unconfirmed |
| 2026-11-07 | Test index/thumb samples for both hands before a full sensor order | Both geometries and simultaneous wireless operation need validation |
| 2026-11-07 | Carry forward the latest nRF52840 dedicated-receiver proposal | The earlier ESP32/BLE outline is archived; firmware and radio development remain open |
| 2026-11-07 | Target 16 baseline channels per glove, 32 for the pair; defer spread sensing | Validate each hand's geometry and calibration independently |
| 2026-11-07 | Target one receiver for two independently powered controllers | Needs explicit IDs, radio scheduling and two-stream validation before expansion |
| 2026-11-07 | Keep contact events hand-specific and configure normal pointer ownership | Both hands update pose; avoid conflicting cursor/click/drag control |
| 2026-11-07 | Isolate glove failures and calibration | Lost hand releases its actions; healthy hand continues; receiver loss clears both |
| 2026-11-07 | Use USB bench power before wearable battery tests | Isolate circuit and software behaviour before adding the battery |
| 2026-11-07 | Defer compact PCB and USB-C packaging | Learn from a working development-board prototype first |
| 2026-11-07 | Treat the earlier roughly ₦40,000 figure as historical | It covered the simpler concept and is not the full-design budget |

## Spending and orders

No completed purchase is recorded by this update.

| Date | Item / exact model | Hand / shared | Supplier | Qty | Currency / unit quote | Delivery / import charges | Actual landed cost | Order status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Pending | Pending | LEFT / RIGHT / shared | Pending | Pending | Pending | Pending | Pending | Not ordered |

Record soldering labour, tools and fabrication as separate entries. Keep original currencies and date any conversion rate used.

## Session log

| Date | Stage | Work performed | Evidence | Result / blocker | Next action |
| --- | --- | --- | --- | --- | --- |
| 2026-11-07 | M0, initial revision | Documented owner-led DIY route | Commit 3a5cfa967c57f3ff6f7486a6043a709da8ef5ccd | Right-only scope error subsequently identified; no hardware acceptance claimed | Correct documentation for both hands |
| 2026-11-07 | M0, scope correction | Replanned both gloves, pair quantities, radio/app state, calibration, tests and measurement sheet | Current README and linked documents; prior right-only plan archived | Documentation corrected; implementation and physical tests remain pending | Measure both hands and confirm the two-hand sample kit |

## New session template

Copy this section for each work session.

### YYYY-MM-DD: short session title

- Stage:
- Device identity / LEFT, RIGHT or pair:
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
