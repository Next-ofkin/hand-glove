# DIY build sequence

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **planned sequence; no tested wiring diagram yet**

Required outcome: **one LEFT glove and one RIGHT glove operating together**. Bring up circuits individually when helpful, then validate both as a pair at the stated gates.

Work through one checkpoint at a time. The owner handles assembly, software and testing; use the [local soldering brief](LOCAL-SOLDERING.md) for individual soldering jobs.

This is a development sequence. It is not a pin-by-pin assembly manual. Exact pins, resistor values and connector assignments must be documented for the actual boards before connecting or soldering them.

## 1. Establish the first kit

1. Read the [current plan](PLAN.md) and [staged BOM](BOM.md).
2. Measure palm/wrist fit, finger lengths and joint spacing for each hand using [MEASUREMENTS.md](MEASUREMENTS.md). Make separate LEFT and RIGHT templates.
3. Confirm two controllers, two IMUs, the candidate shared receiver and both sensor layouts before ordering.
4. Check what the manufacturer supplies with each board: headers, cables and programming access.
5. Obtain shared bench tools and the first two-hand sample kit from the BOM.

**Checkpoint:** exact component identities, sensor dimensions and costs are recorded. No full-glove sensor order yet.

## 2. Prepare the software before the fitted build

1. Select tools supporting both glove controllers and the receiver; record versions.
2. Establish upload and recovery on all three devices; label each glove's device identity and hand assignment.
3. Define packets with LEFT/RIGHT identity, sequence, capabilities, contacts, battery state and explicit clock assumptions.
4. Build a simulator displaying two independent sets of raw channels, estimated poses, contacts and connection states.
5. Plan the Hand Graph two-hand adapter and receiver USB transport. Define pointer ownership, handover, per-hand timeout and receiver-loss behaviour.

**Checkpoint:** both simulated hands drive the view without identity swaps. Losing either simulated glove clears only its state; receiver loss clears both. Check pointer ownership and handover. Software still needs implementation.

## 3. Prepare the wiring and soldering job

1. Produce schematics and board-specific pin tables from the actual parts' documentation, identifying both LEFT and RIGHT circuits.
2. Record signal voltage limits, contact input conditioning, IMU interface and power route.
3. Keep connections removable and labelled by hand, connector and signal. Do not join the two independently powered gloves electrically.
4. Have a local technician solder headers/connectors and any agreed prototype joints.
5. Obtain continuity, polarity and joint-inspection results before power is applied.

**Checkpoint:** the returned wiring matches the drawing. Resolve any discrepancy before power-up.

## 4. Bring up modules separately over USB

Repeat these steps for LEFT and RIGHT. Keep a separate log and calibration record for each device.

1. Power the controller through its intended USB connector.
2. Confirm a simple firmware upload and diagnostic output.
3. Test one contact input, then the second; add debounce and release handling.
4. Connect the IMU only after its wiring is checked; log orientation and recenter behaviour.
5. Read one bend sensor through the agreed divider, then add the selector and buffer.
6. Record raw ranges, noise and settling before adding calibration.

Controller-facing signals must remain inside the chosen board's permitted logic and ADC ranges. A motor requires its own appropriate driver; never attach it as a direct GPIO load.

**Checkpoint:** each glove's modules work alone and then together. Check both bench circuits running at once and keep the batteries disconnected during initial USB checks.

## 5. Fit index and thumb samples on both hands

Repeat the fitting and measurements on each hand. Keep both physical samples available for the next gate.

1. Mark the intended sensing zones on fabric sleeves or a fitted donor glove.
2. Make channels that hold the sensor zones at their intended joints while allowing natural movement.
3. Follow the supplier's bend-radius and attachment guidance; protect terminations from strain.
4. Attach insulated wiring and separate conductive contact patches.
5. Mount the IMU firmly to the back of the hand.
6. Calibrate and test isolated movements using [TESTING.md](TESTING.md).

**Checkpoint:** both samples give distinguishable readings and reliable hand-tagged contacts. Log cross-talk, slip and neutral drift separately. Confirm the left hand's axes and joint directions rather than copying right-hand calibration.

## 6. Make both samples wireless together

1. Implement firmware on the LEFT controller, RIGHT controller and shared receiver. Record explicit device-to-hand pairing.
2. Pass both real data streams through the receiver USB channel into distinct hand states.
3. Define fair radio access/retries and record update rate, gaps and visible response for each hand while both transmit.
4. Add independent reconnect/timeouts and held-input release. Test loss of each glove and loss of the receiver.
5. Integrate two virtual hands, hand-specific calibration/contact events and selected-pointer ownership into the test adapter.
6. Move and click both hands together, hide either/both from the webcam and repeat with normal laptop Wi-Fi active.

**Checkpoint:** both real samples work simultaneously. Neither starves, changes identity or takes over the other hand's input unexpectedly. Removing one preserves the healthy hand. The programmable dongle still needs custom two-glove receiver firmware; revise the transport if this gate fails before expanding.

## 7. Expand both gloves and add wearable power

1. Freeze each hand's sensor dimensions and order the remaining confirmed baseline parts for the pair.
2. Extend both harnesses and calibrations to the full hands: 16 proposed analog channels each, 32 total.
3. Select one protected battery and compatible charging path per glove; check both connector polarities independently.
4. Secure electronics and batteries in their respective cuffs; add separately addressable haptics through driver circuits if ready.
5. Measure each glove's current, actual runtime and comfort while using both together.

Charge the removable pod off the glove. Avoid bending or compressing the battery, exposed conductive joints and charging a damaged cell.

**Checkpoint:** run the full acceptance checklist and save the measured results.

## 8. Refine the finished form

Once both full prototypes work together, prepare compact PCBs, final USB-C power designs, enclosure CAD and breathable textile patterns for the pair. A shared circuit design may be reusable, but validate mounting and cable routing on each hand. Development boards can remain bulkier during learning.

Retest after any PCB, battery, firmware or packaging change. Record the final schematic, pin table, firmware/source versions, calibration procedure and as-built photos needed to reproduce the project.

## Required implementation records

- Schematics, pin tables, device identities and LEFT/RIGHT assignment records.
- Separate sensor placement, orientation mounting and connector/harness drawings for each hand.
- Firmware, receiver and simulator source with build instructions.
- Packet/transport specification and Hand Graph integration instructions.
- Per-device calibration plus separate and simultaneous-use test results.
- Pair BOM, actual costs, shared items and known limitations.

These are future deliverables until committed and tested.
