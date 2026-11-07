# Test checklist and evidence

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **all physical and software acceptance tests pending**

Completion requires **both LEFT and RIGHT gloves working at the same time**. Run per-glove checks on each hand, then the simultaneous-use gate below. Track hardware identity, hand assignment and results separately.

Run the tests appropriate to the stage. Record observations and failures as well as successful results. A goal in this document is not a measured specification.

## Bench checks

- [ ] Record exact board/sensor revisions, wiring revision and firmware version.
- [ ] Inspect soldering, continuity and polarity before powering the circuit.
- [ ] Confirm upload and recovery on both controllers and the receiver, and verify each device's hand assignment.
- [ ] Confirm sensor/ADC values stay in the circuit's expected range.
- [ ] Log each module alone, then the combined circuit; identify noise or unstable supply behaviour.
- [ ] Check contact input idle, touch and release states.

## Index/thumb sensing gate

Repeat this gate independently for LEFT and RIGHT, preserving distinct calibration and orientation transforms.

- [ ] Record straight/open, comfortable bend and neutral-return raw values for every active zone.
- [ ] Repeat at least 10 isolated bends of each intended joint.
- [ ] Hold neighbouring joints as still as practical; record cross-talk and movement limitations.
- [ ] Repeat thumb flexion and opposition trials; identify any motion inferred by the model.
- [ ] Check glove slipping, termination strain and movement through the full comfortable range.
- [ ] Refit the sample and recalibrate; note whether results remain repeatable.

Pass this gate only when the intended zones give distinguishable usable readings. A single sensor's response to whole-finger curl is not evidence of independent MCP/PIP/DIP measurement.

## Click, release and haptics

- [ ] On each hand, test 20 deliberate thumb/index and 20 thumb/middle contacts; confirm source-hand tags and the selected mapping to left/right mouse buttons.
- [ ] Record missed clicks, extra clicks, simultaneous-contact behaviour and accidental touches.
- [ ] Test click-hold, drag and release.
- [ ] Verify glove loss/stale data releases only that hand's held actions; receiver loss releases both. Display the corresponding disconnected state.
- [ ] Verify no held action reappears unexpectedly on reconnect.
- [ ] If a motor is fitted, test through its driver and check for sensor noise or resets.

Investigate unintended input before normal use; keep the test view visible during calibration.

## Wireless and Hand Graph gate

Run with both real gloves transmitting. Record per-hand rates, losses and response; a successful single-transmitter test is insufficient.

- [ ] Compare the same real raw data over USB and the receiver path.
- [ ] Log sequence gaps, reconnect attempts and timeouts during a normal desk session.
- [ ] Test at the intended operating distance with normal laptop Wi-Fi active.
- [ ] Hide the fingers from the webcam and verify glove contact input still works.
- [ ] Confirm both sets of measured channels, orientation, device/hand identity, calibration, capabilities and battery state reach the correct adapter state.
- [ ] Confirm pointer/click/drag behaviour and Hand Graph practice scoring after integration exists.
- [ ] Verify USB transport in the chosen browser or desktop bridge.

Firmware timestamps and host timestamps may use different clocks. Define synchronization or an appropriate measurement method before claiming packet age or end-to-end latency.

## Simultaneous-use and isolation gate

- [ ] Simulate two independent streams, conflicting hand assignments, malformed packets and separate stale timers before real hardware tests.
- [ ] Move each hand alone, then both in opposite directions; verify the two virtual hands and coordinate transforms.
- [ ] Bend matching fingers differently and confirm no channels or calibration values cross between hands.
- [ ] Generate contacts simultaneously on both hands; preserve raw event identity and enforce the selected pointer owner.
- [ ] Switch pointer ownership while an input is held; verify release before handover and no phantom click.
- [ ] Turn off LEFT while RIGHT moves/clicks, then reverse; the remaining hand continues with its own calibration and input state.
- [ ] Reconnect in both orders and confirm identities are stable, with no replayed held contacts.
- [ ] Recenter or recalibrate one hand without changing the other.
- [ ] Stress both streams together at the intended desk distance; record per-hand update rate, gaps and visible response, including starvation/retry behaviour.
- [ ] Remove the receiver and verify both states clear; reconnect and pair both predictably.
- [ ] If fitted, address each haptic motor separately and verify only the intended hand responds.
- [ ] Run both gloves wirelessly on their own batteries and record battery status/runtime separately.

Do not release the full-glove sensor purchase gate until both fitted index/thumb samples pass simultaneous operation, identity, ownership and isolated-disconnect checks. All these tests are pending.

## Finished-glove gate

Repeat per hand and together; record coverage for all 32 proposed analog channels, clearly marking unvalidated or model-estimated motion.

- [ ] Test every baseline channel and the fitted thumb layout.
- [ ] Measure current and battery runtime under a recorded workload.
- [ ] Record weight, comfort, wire strain, glove slip and any unusual warmth.
- [ ] Check battery retention, charger compatibility and correct polarity.
- [ ] Test removable electronics and repeat the functional checks after refitting.
- [ ] Repeat relevant tests after changes to PCB, casing, sensor mounting or firmware.

## Visible-response measurement

Record physical movement/contact and the visible computer response together, for example in the same video. State frame rate, event definition, sample count and timing uncertainty. Report median, 95th percentile and worst observed delay where the data supports them.

Measure each hand while both transmit; record synchronization assumptions and relative timing uncertainty for any coordinated gesture claims. The under-30-ms typical response aspiration is unvalidated. Firmware loop speed or radio timing alone does not establish motion-to-screen response.

## Result template

| Field | Record |
| --- | --- |
| Date and stage | Pending |
| Device / LEFT or RIGHT / simultaneous pair | Pending |
| Hardware / wiring revision | Pending |
| Firmware and app commit | Pending |
| Test setup and calibration | Pending |
| Test performed / repetitions | Pending |
| Raw data or evidence reference | Pending |
| Expected behaviour | Pending |
| Observed behaviour / measured values | Pending |
| Pass / fail / blocked and reason | Pending |
| Next change and retest | Pending |

Store actual results in [BUILD-LOG.md](BUILD-LOG.md); mark tests that could not be run as blocked or pending.
