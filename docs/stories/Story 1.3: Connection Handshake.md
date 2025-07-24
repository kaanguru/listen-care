# Story 1.3: Connection Handshake

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Caregiver,
**I want** to tap on a discovered device to establish a connection,
**so that** I can pair the two devices for monitoring.

## Acceptance Criteria

1.  Tapping a device in the discovery list initiates a connection request.
2.  The receiving device shows a simple prompt to "Accept" or "Decline" the connection.
3.  When "Accept" is tapped, a stable peer-to-peer WebRTC connection is established.
4.  Both devices leave the "Pairing Screen" and display a new screen with a clear "Connected" status, ready for role selection in the next Epic.

## Tasks / Subtasks

- [ ] **Task 1: Implement Connection Initiation** (AC: 1)
  - [ ] In `PairingViewModel`, handle the user tap on a discovered `PeerDevice`.
  - [ ] Call a new method in the `WebRTCManager` to begin the connection process with the selected device.
- [ ] **Task 2: Implement Connection Prompt UI & Logic** (AC: 2)
  - [ ] Create a simple, clear `@Composable` dialog for the "Accept/Decline" prompt.
  - [ ] The `WebRTCManager` on the receiving device must be able to trigger this prompt on the UI.
  - [ ] Handle the user's "Accept" or "Decline" selection.
  - [ ] Design UI states for "Connecting..." and "Connection Failed".
- [ ] **Task 3: Establish WebRTC Connection** (AC: 3)
  - [ ] Implement the local network signaling mechanism for the WebRTC offer/answer/ICE candidate exchange (e.g., using temporary local sockets).
  - [ ] Successfully establish the direct P2P media channel.
  - [ ] Create and manage the state of the `MonitoringSession` data model.
- [ ] **Task 4: Implement Navigation on Connection** (AC: 4)
  - [ ] Upon a successful connection, navigate both devices away from the `PairingScreen`.
  - [ ] For this story, navigate to a simple placeholder screen that displays a "Connected" status.
- [ ] **Task 5: Write Tests**
  - [ ] Write unit tests for the connection state logic in the `PairingViewModel`.
  - [ ] Write a Maestro UI test for the full handshake flow: tap device -> see prompt -> accept -> verify navigation to "Connected" screen.

## Dev Notes

This story completes the pairing workflow by implementing the connection logic within the `WebRTCManager` component.

### Local Signaling

Since no internet STUN/TURN servers are used, the initial WebRTC "offer" and "answer" payloads must be exchanged directly over the local WiFi. The `WebRTCManager` will need to implement a temporary signaling channel (e.g., using a simple TCP socket on a known port) for this initial handshake.

### State Management

Upon a successful connection, the application's global state should transition to "Connected," and a `MonitoringSession` object should be created to hold the details of the active session. This state will be used in the next epic to manage device roles and audio streaming.

## Testing

- A Maestro UI test is required to simulate the entire handshake flow across two devices (or emulators): tapping a device, seeing the prompt on the second device, accepting, and verifying that both devices navigate to the correct "Connected" screen.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
