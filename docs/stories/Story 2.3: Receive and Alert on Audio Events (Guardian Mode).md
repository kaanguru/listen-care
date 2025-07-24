# Story 2.3: Receive and Play Audio (Guardian Mode)

## Status
- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story
**As a** Caregiver in "Guardian Mode",
**I want** to be alerted and hear the audio snippet when a noise is detected,
**so that** I can immediately understand the situation.

## Acceptance Criteria
1. The app on the guardian device listens for incoming audio event streams.
2. When an audio snippet is received, it is played automatically through the speaker.
3. Simultaneously, the device triggers a vibration alert.
4. The UI updates to show an "Audio Event Received" status while the snippet is playing.

## Tasks / Subtasks
- [ ] **Task 1: Handle Incoming Audio Track** (AC: 1)
    - [ ] In the `WebRTCManager`, implement the callback for when a remote audio track is added to the peer connection.
- [ ] **Task 2: Implement Audio Playback** (AC: 2)
    - [ ] In the `AudioEngine` (`:core:audio`), implement the logic to take the received audio data from the `WebRTCManager`.
    - [ ] Use a low-latency API like `AudioTrack` to play the audio stream through the device's speaker.
- [ ] **Task 3: Implement UI Feedback** (AC: 3)
    - [ ] In `MonitoringViewModel`, create a `StateFlow<Boolean>` to represent if audio is actively being received.
    - [ ] The `AudioEngine` or `WebRTCManager` should update this state.
    - [ ] In `MonitoringScreen.kt`, create a simple visual indicator (like a pulsing dot or a small waveform) that appears and animates when the audio state is true.
- [ ] **Task 4: Write Tests**
    - [ ] Write unit tests for the audio activity state logic in the `MonitoringViewModel`.
    - [ ] Write a Maestro UI test to verify that when a session is active, the audio indicator on the `Guardian Dashboard` is visible and animating.

## Dev Notes
This story implements the receiving and playback part of the `Audio Engine`. It's the counterpart to Story 2.2.

### Audio Playback
* To meet the low-latency requirement (NFR4), the implementation should use Android's `AudioTrack` API. The native C++ portion of the `AudioEngine` can be used for efficient audio buffer management before passing the data to the `AudioTrack` player via JNI.

### UI Feedback
* The visual indicator (AC #3) is critical for user confidence. The caregiver must have a clear, persistent visual confirmation that the audio stream is live, so they don't have to guess if silence means the room is quiet or the stream is dead.

## Testing
- A Maestro UI test is required. The test should establish a connection between two devices. On the Guardian device, it must verify that the audio activity indicator becomes active. The test steps will include a manual check to confirm that audio is audible.

## Change Log
| Date | Version | Description | Author |
| :--- | :--- | :--- | :--- |
| 2025-07-23 | 1.0 | Initial story draft created from PRD. | Bob (SM) |