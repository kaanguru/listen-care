# Story 2.1: Implement Device Roles and UI

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** User,
**I want** to select a role (Guardian or Patient) for my device after pairing,
**so that** the app displays the correct interface for monitoring or being monitored.

## Acceptance Criteria

1.  Immediately after a successful pairing, the app on each device prompts the user to select its role: "Guardian Mode" or "Patient Mode".
2.  Selecting "Patient Mode" displays the Patient Status Screen with a clear "Listening..." status indicator.
3.  Selecting "Guardian Mode" displays the Guardian Dashboard, showing a "Connected and waiting for sound..." status.
4.  The role selection is communicated to the paired device, which automatically assumes the opposite role.

## Tasks / Subtasks

- [ ] **Task 1: Create Role Selection UI** (AC: 1)
  - [ ] Design and implement a simple UI prompt (e.g., a dialog with two buttons) that appears after the connection is established.
- [ ] **Task 2: Implement Role Selection Logic** (AC: 2, 3)
  - [ ] Create `MonitoringScreen.kt` (Guardian) and `PatientStatusScreen.kt` (Patient) in the `:features:monitoring` module.
  - [ ] Create `MonitoringViewModel.kt` to handle the business logic for role selection and state management.
  - [ ] On user selection, the ViewModel will update the `MonitoringSession` state and navigate to the appropriate screen.
- [ ] **Task 3: Implement Role Communication** (AC: 4)
  - [ ] Update the `WebRTCManager` to establish a simple "Data Channel" alongside the audio stream.
  - [ ] When a user selects a role, send a message over the Data Channel to the other device.
  - [ ] The receiving device must listen for this message and automatically configure itself to the opposite role and navigate to the correct screen.
- [ ] **Task 4: Write Tests**
  - [ ] Write unit tests for the role selection logic in the `MonitoringViewModel`.
  - [ ] Write a Maestro UI test to verify that after a connection, the role prompt appears, a selection is made, and both devices navigate to the correct corresponding screens.
- [ ] **Task 5: Create Core UI Components**
  - [ ] In the `:core:ui` module, create a reusable `@Composable` function for `LargeButton`.
  - [ ] Ensure the button is easily customizable for different text and colors.

## Dev Notes

This story builds directly on the successful connection from Epic 1. It establishes the specific roles each device will play in the monitoring session.

### Component Interaction

- The UI will communicate the user's role choice to the `MonitoringViewModel`. The ViewModel will then update the `MonitoringSession` state and use the `WebRTCManager` to inform the other device of its role.

### WebRTC Data Channel

- A WebRTC Data Channel is the standard way to send non-media data (like control messages) between connected peers. The `WebRTCManager` should be updated to open a reliable data channel upon connection to handle this communication.

## Testing

- A Maestro UI test is required to verify the entire role selection flow. This test should run on two devices/emulators and confirm that when one selects "Guardian," the other automatically becomes "Patient."
