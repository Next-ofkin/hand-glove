# DIY build sequence

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **planned sequence; no tested wiring diagram yet**

Work through one checkpoint at a time. The owner handles assembly, software and testing; use the [local soldering brief](LOCAL-SOLDERING.md) for individual soldering jobs.

This is a development sequence. It is not a pin-by-pin assembly manual. Exact pins, resistor values and connector assignments must be documented for the actual boards before connecting or soldering them.

## 1. Establish the first kit

1. Read the [current plan](PLAN.md) and [staged BOM](BOM.md).
2. Measure palm/wrist fit, finger lengths and joint spacing. Make a paper placement template.
3. Confirm controller, receiver and sensor models before ordering.
4. Check what the manufacturer supplies with each board: headers, cables and programming access.
5. Obtain the bench tools and small sensor sample kit.

**Checkpoint:** exact component identities, sensor dimensions and costs are recorded. No full-glove sensor order yet.

## 2. Prepare the software before the fitted build

1. Select a toolchain that supports the chosen controller and receiver; record versions.
2. Establish a working firmware upload and recovery procedure on each device.
3. Define the packet model, capabilities, contact states and disconnect/stale-data behaviour.
4. Build a simulator and diagnostic screen that can display raw channels, estimated poses and contact events.
5. Plan the Hand Graph adapter and check which browser or desktop bridge will handle receiver USB data.

**Checkpoint:** simulated input can drive the test view, including a link-loss case. These software components still need implementation.

## 3. Prepare the wiring and soldering job

1. Produce a schematic and board-specific pin table from the actual parts' documentation.
2. Record signal voltage limits, contact input conditioning, IMU interface and power route.
3. Keep initial connections removable and labelled.
4. Have a local technician solder headers/connectors and any agreed prototype joints.
5. Obtain continuity, polarity and joint-inspection results before power is applied.

**Checkpoint:** the returned wiring matches the drawing. Resolve any discrepancy before power-up.

## 4. Bring up modules separately over USB

1. Power the controller through its intended USB connector.
2. Confirm a simple firmware upload and diagnostic output.
3. Test one contact input, then the second; add debounce and release handling.
4. Connect the IMU only after its wiring is checked; log orientation and recenter behaviour.
5. Read one bend sensor through the agreed divider, then add the selector and buffer.
6. Record raw ranges, noise and settling before adding calibration.

Controller-facing signals must remain inside the chosen board's permitted logic and ADC ranges. A motor requires its own appropriate driver; never attach it as a direct GPIO load.

**Checkpoint:** each module works alone and then together. Keep the battery disconnected during initial USB bench checks.

## 5. Fit the index and thumb sample

1. Mark the intended sensing zones on fabric sleeves or a fitted donor glove.
2. Make channels that hold the sensor zones at their intended joints while allowing natural movement.
3. Follow the supplier's bend-radius and attachment guidance; protect terminations from strain.
4. Attach insulated wiring and separate conductive contact patches.
5. Mount the IMU firmly to the back of the hand.
6. Calibrate and test isolated movements using [TESTING.md](TESTING.md).

**Checkpoint:** repeated bends produce distinguishable readings and reliable contacts. Log cross-talk, slipping and neutral drift. Revise placement before adding the rest of the hand.

## 6. Make the sample wireless

1. Implement compatible glove and receiver firmware.
2. Pass the same diagnostic data through the wireless link and receiver USB channel.
3. Add pairing, reconnect handling and release of held inputs on disconnect/stale data.
4. Connect real sample data to the Hand Graph test adapter.
5. Test with the webcam unable to see the fingers and with normal laptop Wi-Fi active.

**Checkpoint:** real index/thumb movement and contacts drive the computer view reliably. The programmable dongle is not a plug-and-play paired glove receiver.

## 7. Expand and add wearable power

1. Freeze suitable sensor dimensions and order the remaining confirmed baseline parts.
2. Extend the harness and calibration to the full hand.
3. Select a protected battery and verify charger compatibility and connector polarity.
4. Secure rigid electronics and the battery in the cuff; add haptics through the driver circuit if ready.
5. Measure current, actual runtime and comfort.

Charge the removable pod off the glove. Avoid bending or compressing the battery, exposed conductive joints and charging a damaged cell.

**Checkpoint:** run the full acceptance checklist and save the measured results.

## 8. Refine the finished form

Once the prototype works, prepare the compact PCB, final USB-C power design, enclosure CAD and breathable textile pattern. The development board can remain bulkier during learning.

Retest after any PCB, battery, firmware or packaging change. Record the final schematic, pin table, firmware/source versions, calibration procedure and as-built photos needed to reproduce the project.

## Required implementation records

- Board-specific schematic and pin table.
- Sensor placement and connector/harness drawing.
- Firmware, receiver and simulator source with build instructions.
- Packet/transport specification and Hand Graph integration instructions.
- Calibration and measured test results.
- Final BOM, actual costs and known limitations.

These are future deliverables until committed and tested.
