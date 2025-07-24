# Story 3.3: Implement Listen Override

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Caregiver,
**I want** a 'press-and-hold' button to listen in on the patient's room at any time,
**so that** I can proactively check on them without changing the permanent settings.

## Acceptance Criteria

1.  The `Guardian Dashboard` UI contains a "Listen" button.
2.  Pressing and holding the "Listen" button sends a 'start manual stream' signal to the patient device.
3.  The patient device receives the signal and starts streaming audio immediately, bypassing the local noise detection logic.
4.  Releasing the "Listen" button sends a 'stop manual stream' signal to the patient device.
5.  The patient device receives the signal, stops streaming audio, and returns to its normal state of listening locally for noise events.

## Tasks / Subtasks

- [ ] **Task 1: Implement UI Control** (AC: 1)
  - [ ] Add a "Listen" button to the `MonitoringScreen` composable.
  - [ ] The button must correctly detect both press-and-hold and release gestures.
- [ ] **Task 2: Implement Control Messaging** (AC: 2, 4)
  - [ ] In the `MonitoringViewModel`, implement functions to send 'start_override' and 'stop_override' messages via the WebRTC Data Channel.
- [ ] **Task 3: Implement Patient Device Logic** (AC: 3, 5)
  - [ ] The `AudioEngine` and `WebRTCManager` on the Patient device must be updated to handle the incoming override messages.
  - [ ] The 'start_override' message must force the `AudioEngine` to begin capturing and streaming audio immediately.
  - [ ] The 'stop_override' message must cause the `AudioEngine` to stop streaming and return to its passive listening state.
- [ ] **Task 4: Write Tests**
  - [ ] Write a unit test for the override logic in the `MonitoringViewModel`.
  - [ ] Write a Maestro UI test to verify the press-and-hold functionality and the resulting audio stream (via a manual check).

## Dev Notes

- **State Management**: This feature requires a momentary state change. The communication over the Data Channel must be fast and reliable. The Patient device must be able to seamlessly switch between its passive listening state and the active override streaming state without dropping the main WebRTC connection.

## Testing

A Maestro test is required. The test will perform a 'long press' action on the 'Listen' button, hold for a few seconds, then release the button. It should verify that the UI correctly reflects the 'Listening' state during the hold and returns to the normal monitoring state upon release.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
