# Story 1.2: Network Device Discovery

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Caregiver,
**I want** the app to automatically find other devices running Listen Care on my WiFi,
**so that** I can easily start the pairing process without typing codes.

## Acceptance Criteria

1.  When on the "Pairing Screen," the app automatically scans the local WiFi network for other Listen Care instances.
2.  Discovered devices are displayed in a simple, tappable list.
3.  The list updates if a new device joins or leaves the network.
4.  The scanning process is optimized for minimal battery usage.

## Tasks / Subtasks

- [ ] **Task 1: Implement NetworkDiscoveryManager** (AC: 1, 3, 4)
  - [ ] In the `:core:network` module, create the `NetworkDiscoveryManager` class.
  - [ ] Implement logic using Android's `NsdManager` to both register the local device's service and discover other services on the network.
  - [ ] Ensure the discovery lifecycle is tied to the app's lifecycle to conserve battery.
- [ ] **Task 2: Develop Pairing Feature UI** (AC: 2)
  - [ ] In the `:features:pairing` module, create the `PairingScreen.kt` composable.
  - [ ] Design a simple UI to show a "Scanning..." state and a list of discovered devices.
  - [ ] Design a clear UI for the error state (e.g., "Could not scan network").
- [ ] **Task 3: Implement Pairing ViewModel** (AC: 2, 3)
  - [ ] In the `:features:pairing` module, create the `PairingViewModel.kt`.
  - [ ] The ViewModel will hold the state for the `PairingScreen`.
  - [ ] Inject and use the `NetworkDiscoveryManager` to get and expose a `StateFlow` of discovered `PeerDevice` objects to the UI.
- [ ] **Task 4: Write Tests**
  - [ ] Write unit tests for the `PairingViewModel` using a mock `NetworkDiscoveryManager`.
  - [ ] Write a UI test using Maestro to verify that a discovered device is correctly displayed in the list on the `PairingScreen`.

## Dev Notes

This story implements the "Local Network Service Discovery" pattern defined in the Architecture Document.

### Component Interaction

- The `PairingViewModel` in the `:features:pairing` module should observe a flow of `List<PeerDevice>` from the `NetworkDiscoveryManager` in the `:core:network` module.

### Technology

- The implementation **MUST** use Android's native `NsdManager` API for mDNS-based service discovery, as specified in the architecture.

### Data Model

- The `PeerDevice` data class defined in the `:core:network` module should be used to represent the information of each discovered device.

## Testing

- Unit tests for the `PairingViewModel` are required to verify the logic of handling the list of discovered devices.
- A Maestro UI test is required to verify the `PairingScreen` correctly displays the devices found by the `NetworkDiscoveryManager`.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
