# Hand Glove

A DIY pair of wireless sensing gloves, **one left and one right**, for [Hand Graph](https://github.com/Next-ofkin/hand-graph). Both hands working together are the required finished scope.

**Current plan: 7 November 2026, Africa/Lagos.** The owner will source parts, assemble the glove, load software, calibrate it and run the tests. A local electronics engineer or technician will help with soldering and checking those connections when needed.

**Status:** design and documentation stage. This repository does not yet contain working glove firmware, a receiver application, a simulator, a tested wiring diagram or a completed hardware build. Features below are targets until demonstrated.

## Intended result

- Two fitted, breathable gloves, each with its own removable rechargeable wrist pod.
- Finger-joint sensing, hand rotation and physical thumb-to-index / thumb-to-middle contacts on each hand.
- Two controllers and two orientation sensors, with a shared wireless USB receiver as the development target.
- Two separately calibrated virtual hands in Hand Graph, with hand-specific input and explicit pointer/click ownership.
- USB-C charging in each finished pod; development-board packaging comes first.

The current proposal uses nRF52840 hardware and joint-specific sensor samples. The earlier ESP32/BLE and five whole-finger sensor outline is retained in the [original plan](docs/archive/2026-11-07-original-plan.md) as history.

The previous right-hand-only documentation was a scope error. The project requires both hands. A shared receiver serving both gloves needs custom firmware and simultaneous-use testing; it is not an existing tested feature.

## Start here

| Document | Purpose |
| --- | --- |
| [Current plan](docs/PLAN.md) | Decisions, responsibilities, milestones and open engineering work |
| [Both-hand measurements](docs/MEASUREMENTS.md) | Separate left/right fit and sensor-zone measurements |
| [Parts and sourcing](docs/BOM.md) | Small first purchases, Nigerian suppliers and import candidates |
| [DIY build sequence](docs/BUILD.md) | What to do and verify at each stage |
| [Local soldering brief](docs/LOCAL-SOLDERING.md) | A limited task sheet to take to a local technician |
| [Test checklist](docs/TESTING.md) | Fit, sensing, clicks, radio and app acceptance checks |
| [Build log](docs/BUILD-LOG.md) | Decisions, spending, evidence and progress over time |

## Next milestone

Start by measuring **both hands separately**. Then prove an index-finger and thumb sample for each hand, with separate repeatable readings and contact events. Prove each circuit over USB on the bench, then prove both samples sending data together through the proposed shared receiver into a Hand Graph test view.

Buy the remaining sensors and commission compact packaging for the pair after both samples pass the simultaneous-use gate. One glove may be checked at a time on the bench; the completion milestone is two full gloves working together. Each IMU supplies its hand's rotation; reliable absolute position in a room requires separate tracking.
