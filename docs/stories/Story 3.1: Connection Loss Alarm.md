# Story 3.1: Connection Loss Alarm

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Caregiver,
**I want** to be alerted with a loud, continuous alarm if the connection is lost,
**so that** I never mistakenly believe I am monitoring when the system is down.

## Acceptance Criteria

1.  The 'Guardian Mode' app continuously monitors the health of the WebRTC connection.
2.  If the connection is lost for more than 5-10 seconds, a loud, repeating alarm sound is triggered.
3.  The alarm overrides the device's silent/vibrate settings to ensure it is heard.
4.  The alarm can only be dismissed by a direct user action on the screen.
5.  The app attempts to reconnect in the background while the alarm is sounding.

## Tasks / Subtasks

- [ ] **Task 1: Implement Connection Health Monitoring** (AC: 1)
  - [ ] In the `WebRTCManager`, implement a robust heartbeat or connection state monitoring mechanism to reliably detect a dropped connection.
- [ ] **Task 2: Create Alarm Service & UI** (AC: 2, 3, 4)
  - [ ] Implement an `AlarmManager` or similar service on the Guardian device that can play a loud, looping audio file.
  - [ ] Ensure the audio playback uses the correct Android audio stream (e.g., `STREAM_ALARM`) to bypass silent/vibrate modes.
  - [ ] Create a full-screen alert or a prominent dialog UI for the alarm, which includes a button to dismiss it.
- [ ] **Task 3: Implement Reconnection Logic** (AC: 5)
  - [ ] When a connection is lost, trigger a background process that periodically attempts to rediscover and reconnect to the Patient device.
- [ ] **Task 4: Write Tests**
  - [ ] Write unit tests for the connection loss detection logic.
  - [ ] Write a Maestro UI test that simulates a network drop and verifies that the alarm UI appears on the Guardian device.

## Dev Notes

This is a critical safety feature. The alarm must be reliable and loud enough to wake a sleeping caregiver. Bypassing the device's silent mode is a key requirement and should be tested thoroughly on different Android versions.

## Testing

A Maestro test is required. The test setup must include a step that simulates a network disconnection for the Patient device (e.g., turning off WiFi on that device) and then verifies that the alarm UI appears and sound is played on the Guardian device.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
