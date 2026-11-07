# Hand Glove: current DIY plan

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **planning; physical build and software implementation pending**

**Required scope: two gloves, one left and one right, used together.** The earlier right-hand-only description was a documentation error. Both hands are included in the build, parts, firmware, calibration and acceptance criteria from this revision onward.

## Build decision

The owner will build and test both gloves in Nigeria. Local help is limited to soldering, connector work and electrical checks associated with that work. The owner keeps responsibility for sourcing, assembly, firmware loading, calibration, integration and test records, with step-by-step development support as needed.

A specialist may print a casing or sew a glove sample from an agreed design. These are individual fabrication jobs. They do not change ownership of the build.

This plan replaces the earlier ESP32/basic-contact and five-sensor outline. The [original text](archive/2026-11-07-original-plan.md) remains available for the decision history.

## Design target

Two close-fitting gloves, one for each hand, with thin sensor channels, soft fingertip contacts, a hand-mounted orientation sensor and a removable rechargeable wrist pod on each glove. The target is one dedicated receiver plugged into the computer, serving both gloves. Each finished pod has USB-C charging; both gloves operate without a computer cable during use.

Measure each hand independently using [MEASUREMENTS.md](MEASUREMENTS.md). Do not assume identical finger lengths, sensor placement, glove fit or orientation transforms on the two hands.

The drawings and concept images describe the intended appearance. Sensor placement, circuit values, PCB dimensions, runtime and performance require physical testing.

| Function | Proposed implementation | What still needs proving |
| --- | --- | --- |
| Four ordinary fingers on each hand | Three bend zones per finger: MCP, PIP and DIP; 12 channels per hand, 24 across the pair | Individual joint response, fit, drift and cross-talk on each hand |
| Each thumb | MCP and IP flexion plus two thumb-base motion channels; 4 per hand, 8 across the pair | Hand-specific geometry and opposition mapping |
| Hand orientation | Two BNO085 breakouts, one fixed to each hand | Mounting, per-hand coordinate transforms and independent recentering |
| Contacts on each glove | Thumb common; separate index and middle inputs, each tagged with its source hand | Debounce, release and input ownership when both hands act |
| Sensor reader | One divider/selector/buffer/ADC chain per glove | Values, settling, voltage range, filtering and scan timing |
| Controllers and radio | Two Feather nRF52840 Express boards; one Nordic nRF52840 USB dongle as the shared receiver target | Firmware on all three devices; two-source scheduling, pairing and recovery |
| Feedback | One wrist vibration motor and driver per glove if fitted | Commands reach the intended hand without disturbing sensing |
| Power | USB for initial bench checks; one suitable protected single-cell LiPo and charging path per glove later | Charger compatibility, polarity, current and runtime separately |
| Computer input | Shared receiver USB data channel, demultiplexed into left/right hand state | Transport support, both-hand Hand Graph adapter and stale-state isolation |

The proposed baseline is **16 analog sensing channels per glove, 32 across both hands**. Four optional finger-spread channels per glove would make 20 per hand / 40 across the pair and require revised readers. Sideways spread is deferred until the baseline pair works.

One possible arrangement is five dual-zone strips plus six short single-zone sensors per glove: ten dual-zone plus twelve short sensors for the pair. It is a sourcing candidate, not a validated pattern: a standard 90 mm strip may not match a finger or thumb. Confirm active-zone positions for each hand and attachment requirements with the supplier.

A single whole-finger bend sensor gives a combined curl reading. It cannot independently establish all three finger-joint angles. Any joint pose inferred by the software must be identified as estimated.

## Two-glove connection and application behaviour

The target topology is two independently powered gloves communicating with one USB receiver. One controller, IMU and battery cannot serve two freely moving hands through the proposed cable-free design.

- Give each glove a stable device identity and a configured hand identity, LEFT or RIGHT. Pair both identities explicitly; never assign hands by arrival order.
- Include device identity, hand identity, sequence, capabilities and battery state in the versioned packet model. Reject conflicting hand assignments and incompatible packet versions visibly.
- Keep separate receiver/app state, calibration, orientation transforms, sequence tracking, reconnect state and stale-data timers for each hand.
- Schedule radio access and retransmissions so neither glove starves the other. Select the packet size and update rate using measured two-glove results; the one-receiver target is not yet validated.
- Define device and receiver clock relationships before comparing both hands' timing. Independent timestamps are not automatically synchronized.
- Display both hands and their connection/battery state. Both sets of pose and contact data remain available to practice tasks.
- A normal system pointer needs explicit ownership. The initial pointer mode will allow selection of either hand; only the selected hand drives that cursor and its click/drag actions. Keep hand identity on all raw contact events, and define separate rules for any bimanual task.
- Changing pointer ownership releases held pointer actions before the new owner takes control.
- If one glove disconnects or goes stale, release its held actions and mark only that hand unavailable; the other glove continues. A receiver disconnect clears both hands. Reconnect must not replay an old held click.
- Route any haptic command to the named device/hand only.

Prove this behaviour with two simulated streams and then two real index/thumb samples before ordering the remaining full-hand sensors. One successful glove does not complete the pair milestone.

## Responsibilities

| Task | Owner / route |
| --- | --- |
| Select exact board revisions, learn the tools and maintain this repository | Owner, with development support |
| Compare Nigerian stock and import quotations; buy in stages | Owner |
| Measure both hands separately, position samples and make two removable harnesses | Owner; textile help if needed |
| Agree a schematic and exact pin table before soldering | Owner, with technical review where needed |
| Solder headers, leads, connectors and an agreed prototype circuit | Local electronics technician as needed |
| Inspect solder joints and check continuity / polarity | Technician; owner records the results |
| Write and load firmware, simulator and application integration | Owner, with development support |
| Calibrate and perform every functional test | Owner |
| Enclosure printing or textile fabrication | Optional local service to an agreed drawing |

The technician is not being commissioned to invent the circuit or deliver the whole product. If they identify a design problem, document and resolve it before the next soldering task.

## Milestones and purchase gates

| Stage | Work | Evidence required before proceeding |
| --- | --- | --- |
| M0: document both-hand DIY scope | Correct plan, pair quantities, measurements, soldering brief and logs | Completed by this documentation update |
| M1: establish software tools | Pick supported tools; define hand/device IDs and protocol; simulate two independent hands | Both virtual hands, ownership and isolated/combined disconnects work; upload/recovery procedure documented |
| M2: prove both bench circuits | Two USB-powered controllers, their contacts and IMUs; one sensing zone on each | Independent raw readings and contact transitions logged; left/right identity verified |
| M3: fit both index/thumb samples | Trial sensor geometry separately on each hand | Both samples give distinguishable repeatable readings without excessive slip or strain |
| M4: prove simultaneous wireless use | Program two glove radios plus receiver; integrate both streams into Hand Graph test adapter | Both samples work together; no identity swaps, starvation or incorrect click ownership; isolated failure passes |
| M5: expand both full hands | Confirm both geometries; buy remaining baseline sensors; add two harnesses, batteries and optional motors | All 32 proposed channels validated or limitations stated; simultaneous use, per-hand current/runtime and failure checks pass |
| M6: compact the finished pair | Two fitted pods, USB-C power designs, enclosures and textiles | Full pair retested after packaging; reproducible build files and source recorded |

A temporary USB cable is useful on each bench circuit. Bring up modules one at a time if that makes debugging easier; the scope remains both hands and the wearable milestone requires simultaneous wireless operation.

Only documentation is complete today. Simulator, firmware, wiring, purchases, soldering, measurements and hardware acceptance are pending.

## Software work to implement

- Glove firmware with explicit LEFT/RIGHT configuration, raw/calibrated sensor values, hand orientation and contact states.
- Versioned packets with stable device/hand identity, capabilities, sequence, battery state and timing fields with defined units and clock assumptions.
- Receiver firmware serving both paired gloves with fair access, per-hand reconnect handling and a USB data interface.
- A two-hand simulator using the same model, including malformed/stale packets, conflicting identities and isolated/combined link loss.
- A Hand Graph adapter alongside the webcam path with two virtual hands, per-hand calibration and practice events, and explicit pointer/click/drag ownership.
- Diagnostics that distinguish measured channels from model estimates and report both connection/battery states separately.
- Per-hand stale-data timeouts and correct held-action release on a glove loss, receiver loss or pointer-owner change.

The dedicated Nordic radio link is the current target. BLE/Web Bluetooth can be evaluated separately if it helps development. Neither transport has been implemented or tested in this repository. The dongle is programmable hardware and does not arrive paired to either glove. If the single-receiver approach fails the simultaneous-use gate, revise the transport and its BOM before expanding the sensors.

## Budget and sourcing

The old roughly ₦40,000 figure described a simpler prototype. It is not a quotation or budget promise for this pair. Budget per-glove electronics, sensors, batteries and fabrication twice, while the laptop, test tools and target shared receiver are common items. Confirm actual quantities rather than doubling an incomplete old total. Add shipping/import charges, soldering labour and spares.

Use the [BOM](BOM.md) to request samples first. Record actual costs in the [build log](BUILD-LOG.md). Exact local availability for the controller, receiver, BNO085 and specialist sensors is not confirmed.

## Acceptance and limitations

Use the [test checklist](TESTING.md) at each milestone.

- Both physical gloves must provide repeatable hand-tagged contacts even when the webcam cannot see the fingers. Verify pointer ownership separately from raw contact capture.
- Record sensor repeatability, cross-talk, click errors and neutral drift for each hand.
- Measure each hand's visible response, gaps, reconnects, weight, current, runtime and comfort while both operate together.
- Confirm disconnecting, reconnecting or recalibrating either glove does not corrupt the healthy hand's state or calibration.
- Under 30 ms typical motion-to-visible response is a design aspiration, not a measured result or guarantee. Record the measurement method and distribution.
- The IMU supports orientation and an air-mouse pointer. Sustained absolute room position needs a camera or another position tracker.
- Hand Graph integration is planned; this documentation commit does not change the companion application's code.

## Immediate next steps

- [ ] Record LEFT and RIGHT measurements independently using MEASUREMENTS.md.
- [ ] Confirm two controllers, two IMUs and one candidate shared receiver, their programming access and stock.
- [ ] Obtain small-quantity dual-zone and short-sensor quotations for both hand geometries.
- [ ] Define the firmware tools, hand identities and packet model; create the two-hand simulator.
- [ ] Produce reviewed schematics, pin tables and labelled harness drawings for both gloves.
- [ ] Buy the first pair of bench/sample circuits, reusing shared test tools.
- [ ] Take only the agreed soldering tasks to a local technician.
- [ ] Run both index/thumb tests and simultaneous wireless tests before expanding either glove to the full set.
