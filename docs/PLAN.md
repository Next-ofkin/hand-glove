# Hand Glove: current DIY plan

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **planning; physical build and software implementation pending**

## Build decision

The owner will build and test this project in Nigeria. Local help is limited to soldering, connector work and electrical checks associated with that work. The owner keeps responsibility for sourcing, assembly, firmware loading, calibration, integration and test records, with step-by-step development support as needed.

A specialist may print a casing or sew a glove sample from an agreed design. These are individual fabrication jobs. They do not change ownership of the build.

This plan replaces the earlier ESP32/basic-contact and five-sensor outline. The [original text](archive/2026-11-07-original-plan.md) remains available for the decision history.

## Design target

One close-fitting right-hand glove, thin sensor channels, soft fingertip contacts, a hand-mounted orientation sensor and a removable rechargeable wrist pod. A dedicated receiver plugs into the computer. The finished target has USB-C charging and no glove-to-computer cable during use.

The drawings and concept images describe the intended appearance. Sensor placement, circuit values, PCB dimensions, runtime and performance require physical testing.

| Function | Proposed implementation | What still needs proving |
| --- | --- | --- |
| Four ordinary fingers | Three bend zones per finger: MCP, PIP and DIP; 12 channels total | Individual joint response, fit, drift and cross-talk |
| Thumb | MCP and IP flexion plus two thumb-base motion channels; 4 channels total | Sensor geometry and opposition mapping |
| Hand orientation | BNO085 breakout fixed to the back of the hand | Mounting, calibration, interface and stable readings |
| Left and right clicks | Thumb common contact; separate index and middle contacts | Debounce, release and unintended-contact behaviour |
| Sensor reader | Divider circuits, CD74HC4067 selector, proposed MCP6002 buffer and controller ADC | Values, settling, voltage range, filtering and scan timing |
| Controller and radio | Feather nRF52840 Express for development; Nordic nRF52840 USB dongle for receiver | Toolchain, firmware on both devices, pairing and recovery |
| Feedback | Wrist vibration motor with an appropriate driver circuit | Driver selection, current demand and supply noise |
| Power | USB for initial bench tests; a suitable protected single-cell LiPo later | Charger compatibility, polarity, current and runtime |
| Computer input | Receiver USB data channel to a supported browser or desktop bridge | Transport support, protocol and Hand Graph adapter |

The proposed baseline is **16 analog sensing channels**. Four optional finger-spread channels would bring this to 20 and require a revised reader. Sideways spread is deferred until the baseline works.

One possible full-glove sensor arrangement is five dual-zone strips plus six short single-zone sensors. It is a sourcing candidate, not a validated pattern: a standard 90 mm strip may not match a finger or thumb. Confirm active-zone positions and attachment requirements with the supplier.

A single whole-finger bend sensor gives a combined curl reading. It cannot independently establish all three finger-joint angles. Any joint pose inferred by the software must be identified as estimated.

## Responsibilities

| Task | Owner / route |
| --- | --- |
| Select exact board revisions, learn the tools and maintain this repository | Owner, with development support |
| Compare Nigerian stock and import quotations; buy in stages | Owner |
| Measure the hand, position samples and make a removable harness | Owner; textile help if needed |
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
| M0: document the DIY route | Update plan, shopping stages, soldering brief and logs | Completed by this documentation update |
| M1: establish software tools | Pick supported board/toolchain versions; define protocol; create a simulated input path | Simulator shows bends, contacts and disconnects; firmware upload/recovery procedure documented |
| M2: prove the bench electronics | USB-powered controller, contact inputs and IMU; then one sensing zone | Real raw values and contact transitions logged; each module checked separately |
| M3: fit index and thumb | Trial dual-zone and short sensor samples; identify each active zone | Isolated movement gives distinguishable repeatable readings; no routing damage or excessive slip |
| M4: prove the wireless sample | Program both radios; pass sensor/contact data to the computer and Hand Graph test adapter | Real fitted sample drives the view and clicks; disconnect releases held actions |
| M5: expand to the full hand | Confirm geometry; order remaining baseline sensors; add harness, battery and optional haptic motor | All fitted channels and buttons pass tests; power and actual runtime recorded |
| M6: compact the finished build | Final PCB/pod, USB-C power design, enclosure and textile finish | Full retest after packaging; reproducible build files and source recorded |

A temporary USB cable is useful during bench development. The wearable-use milestone still requires wireless operation.

Only documentation is complete today. Simulator, firmware, wiring, purchases, soldering, measurements and hardware acceptance are pending.

## Software work to implement

- Firmware that reads raw sensor values, calibrated values, IMU orientation and physical contact states.
- Versioned packets containing capability information, sequence information, battery status and timing fields with defined units and clock assumptions.
- Receiver firmware with pairing/reconnect handling and a USB data interface.
- A simulator using the same data model, including malformed/stale packets and link loss.
- A Hand Graph glove adapter alongside the webcam input path; calibration, pointer/click/drag behaviour and practice scoring.
- Diagnostics that distinguish measured channels from model estimates.
- A defined stale-data timeout that releases held inputs and displays a disconnected state.

The dedicated Nordic radio link is the current target. BLE/Web Bluetooth can be evaluated separately if it helps development. Neither transport has been implemented or tested in this repository. The dongle is programmable hardware and does not arrive paired to this glove.

## Budget and sourcing

The old roughly ₦40,000 figure described the simpler prototype. It is not a quotation or budget promise for this detailed glove. A finished cost needs sensor quotations, electronics, delivery/import charges, tools, soldering labour, fabrication and spares.

Use the [BOM](BOM.md) to request samples first. Record actual costs in the [build log](BUILD-LOG.md). Exact local availability for the controller, receiver, BNO085 and specialist sensors is not confirmed.

## Acceptance and limitations

Use the [test checklist](TESTING.md) at each milestone.

- Physical contacts should provide repeatable left/right clicks even when the webcam cannot see the fingers.
- Record sensor repeatability, cross-talk, click errors and neutral drift.
- Measure visible response, wireless gaps, reconnect behaviour, weight, current, runtime and comfort.
- Under 30 ms typical motion-to-visible response is a design aspiration, not a measured result or guarantee. Record the measurement method and distribution.
- The IMU supports orientation and an air-mouse pointer. Sustained absolute room position needs a camera or another position tracker.
- Hand Graph integration is planned; this documentation commit does not change the companion application's code.

## Immediate next steps

- [ ] Record hand and joint spacing measurements for the sensor layout.
- [ ] Confirm the exact controller/receiver models, programming access and available stock.
- [ ] Obtain small-quantity dual-zone and short-sensor quotations with geometry details.
- [ ] Define the firmware toolchain and packet model; create the simulator.
- [ ] Produce a board-specific reviewed schematic and pin table.
- [ ] Buy the first bench/sample kit.
- [ ] Take only the agreed soldering tasks to a local technician.
- [ ] Run and log the bench and index/thumb tests before expanding.
