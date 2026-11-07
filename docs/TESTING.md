# Test checklist and evidence

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **all physical and software acceptance tests pending**

Run the tests appropriate to the stage. Record observations and failures as well as successful results. A goal in this document is not a measured specification.

## Bench checks

- [ ] Record exact board/sensor revisions, wiring revision and firmware version.
- [ ] Inspect soldering, continuity and polarity before powering the circuit.
- [ ] Confirm firmware upload and recovery on controller and receiver.
- [ ] Confirm sensor/ADC values stay in the circuit's expected range.
- [ ] Log each module alone, then the combined circuit; identify noise or unstable supply behaviour.
- [ ] Check contact input idle, touch and release states.

## Index/thumb sensing gate

- [ ] Record straight/open, comfortable bend and neutral-return raw values for every active zone.
- [ ] Repeat at least 10 isolated bends of each intended joint.
- [ ] Hold neighbouring joints as still as practical; record cross-talk and movement limitations.
- [ ] Repeat thumb flexion and opposition trials; identify any motion inferred by the model.
- [ ] Check glove slipping, termination strain and movement through the full comfortable range.
- [ ] Refit the sample and recalibrate; note whether results remain repeatable.

Pass this gate only when the intended zones give distinguishable usable readings. A single sensor's response to whole-finger curl is not evidence of independent MCP/PIP/DIP measurement.

## Click, release and haptics

- [ ] Test 20 deliberate thumb/index left-click contacts and 20 thumb/middle right-click contacts.
- [ ] Record missed clicks, extra clicks, simultaneous-contact behaviour and accidental touches.
- [ ] Test click-hold, drag and release.
- [ ] Verify that link loss or stale data releases all held actions and displays a disconnected state.
- [ ] Verify no held action reappears unexpectedly on reconnect.
- [ ] If a motor is fitted, test through its driver and check for sensor noise or resets.

Investigate unintended input before normal use; keep the test view visible during calibration.

## Wireless and Hand Graph gate

- [ ] Compare the same real raw data over USB and the receiver path.
- [ ] Log sequence gaps, reconnect attempts and timeouts during a normal desk session.
- [ ] Test at the intended operating distance with normal laptop Wi-Fi active.
- [ ] Hide the fingers from the webcam and verify glove contact input still works.
- [ ] Confirm measured channels, hand orientation, calibration and capability flags reach the adapter.
- [ ] Confirm pointer/click/drag behaviour and Hand Graph practice scoring after integration exists.
- [ ] Verify USB transport in the chosen browser or desktop bridge.

Firmware timestamps and host timestamps may use different clocks. Define synchronization or an appropriate measurement method before claiming packet age or end-to-end latency.

## Finished-glove gate

- [ ] Test every baseline channel and the fitted thumb layout.
- [ ] Measure current and battery runtime under a recorded workload.
- [ ] Record weight, comfort, wire strain, glove slip and any unusual warmth.
- [ ] Check battery retention, charger compatibility and correct polarity.
- [ ] Test removable electronics and repeat the functional checks after refitting.
- [ ] Repeat relevant tests after changes to PCB, casing, sensor mounting or firmware.

## Visible-response measurement

Record physical movement/contact and the visible computer response together, for example in the same video. State frame rate, event definition, sample count and timing uncertainty. Report median, 95th percentile and worst observed delay where the data supports them.

The under-30-ms typical response aspiration has not been validated. Firmware loop speed or radio timing alone does not establish motion-to-screen response.

## Result template

| Field | Record |
| --- | --- |
| Date and stage | Pending |
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
