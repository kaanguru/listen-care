# Story 3.2: Session Pause & Stop Controls

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** User,
**I want** to be able to pause and stop the monitoring session from either device,
**so that** I have full control over the system.

## Acceptance Criteria

1.  Both the 'Guardian' and 'Patient' screens contain functional 'Pause' and 'Stop' buttons.
2.  Tapping 'Pause' temporarily suspends the audio analysis/streaming without ending the connection; tapping 'Resume' restarts it.
3.  The status on both devices clearly indicates when the session is paused.
4.  Tapping 'Stop' terminates the connection and returns both devices to the 'Pairing Screen'.

## Tasks / Subtasks

- [ ] **Task 1: Implement UI Controls** (AC: 1)
  - [ ] Add 'Pause/Resume' and 'Stop' buttons to the `MonitoringScreen` (Guardian) and `PatientStatusScreen` (Patient) composables.
- [ ] **Task 2: Implement ViewModel Logic** (AC: 2, 3, 4)
  - [ ] In the `MonitoringViewModel`, implement the state logic and functions to handle the pause, resume, and stop actions.
- [ ] **Task 3: Implement State Communication** (AC: 2, 3, 4)
  - [ ] Use the WebRTC Data Channel to send control messages (Pause, Resume, Stop) between the two devices to keep their states synchronized.
  - [ ] Update the `WebRTCManager` to mute/unmute the audio track for pausing/resuming.
  - [ ] The 'Stop' action should gracefully close the peer connection.
- [ ] **Task 4: Write Tests**
  - [ ] Write unit tests for the pause/stop state logic in the `MonitoringViewModel`.
  - [ ] Write a Maestro UI test to verify the functionality of both buttons, checking that the UI on both devices updates correctly.

## Dev Notes

- **Pausing vs. Stopping**: Pausing should be a "soft" action. Muting the WebRTC audio track (`audioTrack.setEnabled(false)`) is more efficient than renegotiating the connection. Stopping is a "hard" action that should tear down the entire peer connection.
- **State Synchronization**: The state change (e.g., 'Paused') must be communicated reliably between devices so that both UIs always reflect the correct state.

## Testing

A Maestro test is required to verify the end-to-end flow. The test should:

1. Start a session.
2. Tap 'Pause' on the Guardian device and verify the Patient device UI also shows 'Paused'.
3. Tap 'Resume' and verify both UIs update.
4. Tap 'Stop' and verify both devices return to the Pairing screen.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
