# Story 2.2: Capture and Stream Audio (Patient Mode)

## Status
- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story
**As a** User in "Patient Mode",
**I want** the app to listen locally and only stream audio snippets when a sound exceeds a set threshold,
**so that** battery and network are conserved while the guardian can monitor the room.

## Acceptance Criteria
1. Upon entering "Patient Mode", the app correctly requests and receives the `RECORD_AUDIO` permission.
2. The app captures a low-latency audio stream from the device's microphone.
3. The app continuously analyzes audio from the microphone locally without streaming.
4. When a sound exceeds the noiseSensitivity threshold from the settings, the app initiates a stream.
5. A short snippet of audio (e.g., 5-10 seconds, including a pre-buffer of the triggering sound) is sent over the WebRTC connection.
6. This functionality continues to run reliably in a background (Foreground) service.


## Tasks / Subtasks
- [ ] **Task 1: Implement Permissions Handling** (AC: 1)
    - [ ] Add the `RECORD_AUDIO` permission to the `AndroidManifest.xml`.
    - [ ] Implement the logic in the `PatientStatusScreen` or its `ViewModel` to request the permission from the user if it has not already been granted.
- [ ] **Task 2: Develop Audio Capture Logic** (AC: 2)
    - [ ] In the `:core:audio` module, implement the native C++ part of the `AudioEngine` to capture a low-latency audio stream using low-level APIs like Oboe or AAudio via the NDK.
- [ ] **Task 3: Implement Background Service** (AC: 4)
    - [ ] Create and configure a `ForegroundService` for the monitoring session.
    - [ ] The service must be started when the device enters "Patient Mode".
    - [ ] The service must display a persistent notification to the user, as required by Android, indicating that the app is actively monitoring.
- [ ] **Task 4: Integrate Audio with WebRTC Stream** (AC: 3)
    - [ ] Update the `WebRTCManager` to create and manage a local audio track.
    - [ ] Connect the audio stream captured by the `AudioEngine` to the WebRTC audio track to be sent to the peer.
    - [ ] Configure the WebRTC audio codec and SDP to target a low bitrate of ~32 kbps (NFR6).
- [ ] **Task 5: Write Tests**
    - [ ] Write unit tests for any new logic in the `MonitoringViewModel` related to starting the service.
    - [ ] Write an integration test that verifies the `ForegroundService` starts correctly and that the `WebRTCManager` reports an active audio track is being sent.

## Dev Notes
This story focuses on the sending side of the audio pipeline. It is critical that this is implemented efficiently to meet our low-battery-usage requirement (NFR1).

### Background Execution
To meet AC #4, the audio capture and streaming **MUST** be managed by a Foreground Service. This is non-negotiable on modern Android to prevent the OS from killing the process. The service must be started as soon as "Patient Mode" is confirmed.

### Native Code (NDK)
The core audio capture should be done in C++ via the NDK, as specified in the architecture, to achieve the lowest possible latency and highest performance, which is crucial for both real-time monitoring and battery life.

## Testing
- An integration test is required to verify that activating "Patient Mode" correctly starts the Foreground Service and that the `WebRTCManager` begins transmitting an audio track. Testing the native audio code itself may require specific NDK testing strategies.

## Change Log
| Date | Version | Description | Author |
| :--- | :--- | :--- | :--- |
| 2025-07-23 | 1.0 | Initial story draft created from PRD. | Bob (SM) |