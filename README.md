# Hand Glove

A DIY wireless right-hand sensing glove for [Hand Graph](https://github.com/Next-ofkin/hand-graph).

**Current plan: 7 November 2026, Africa/Lagos.** The owner will source parts, assemble the glove, load software, calibrate it and run the tests. A local electronics engineer or technician will help with soldering and checking those connections when needed.

**Status:** design and documentation stage. This repository does not yet contain working glove firmware, a receiver application, a simulator, a tested wiring diagram or a completed hardware build. Features below are targets until demonstrated.

## Intended result

- A fitted, breathable glove with a removable rechargeable wrist pod.
- Finger-joint sensing, hand rotation and physical thumb-to-index / thumb-to-middle click contacts.
- A dedicated wireless USB receiver connected to the computer.
- A live virtual hand and pointer/click input in Hand Graph.
- USB-C charging in the finished pod; development-board packaging comes first.

The current proposal uses nRF52840 hardware and joint-specific sensor samples. The earlier ESP32/BLE and five whole-finger sensor outline is retained in the [original plan](docs/archive/2026-11-07-original-plan.md) as history.

## Start here

| Document | Purpose |
| --- | --- |
| [Current plan](docs/PLAN.md) | Decisions, responsibilities, milestones and open engineering work |
| [Parts and sourcing](docs/BOM.md) | Small first purchases, Nigerian suppliers and import candidates |
| [DIY build sequence](docs/BUILD.md) | What to do and verify at each stage |
| [Local soldering brief](docs/LOCAL-SOLDERING.md) | A limited task sheet to take to a local technician |
| [Test checklist](docs/TESTING.md) | Fit, sensing, clicks, radio and app acceptance checks |
| [Build log](docs/BUILD-LOG.md) | Decisions, spending, evidence and progress over time |

## Next milestone

Prove an index-finger and thumb sample that gives separate repeatable readings, detects contact clicks and sends real data through the proposed wireless receiver into a Hand Graph test view. Prove each connection over USB on the bench before adding wireless.

Buy the remaining full-glove sensors and commission compact packaging after this sample passes. A single IMU supplies rotation; reliable absolute hand position in a room requires separate tracking.
