## Epic 2: Core Audio Streaming & Monitoring

**Expanded Goal**: To implement the event-driven audio functionality. By the end of this epic, the 'patient' device will intelligently detect sounds and transmit short audio snippets, and the 'guardian' device will receive, play these snippets, and alert the caregiver.


---

### Story 2.1: Implement Device Roles and UI

- **As a** User,
- **I want** to select a role (Guardian or Patient) for my device after pairing,
- **so that** the app displays the correct interface for monitoring or being monitored.

**Acceptance Criteria:**

1. Immediately after a successful pairing, the app on each device prompts the user to select its role: "Guardian Mode" or "Patient Mode".
2. Selecting "Patient Mode" displays the `Patient Status Screen`, which has a clear "Monitoring Active" status indicator.
3. Selecting "Guardian Mode" displays the `Guardian Dashboard`, showing a "Connected" status and a placeholder for audio activity.
4. The role selection is communicated to the paired device, which automatically assumes the opposite role.

---

### Story 2.2: Capture and Stream Audio (Patient Mode)

- **As a** User with a device in "Patient Mode",
- **I want** the app to capture audio from the microphone and stream it,
- **so that** the guardian can monitor the room.

**Acceptance Criteria:**

1. Upon entering "Patient Mode", the app correctly requests and receives microphone permissions.
2. The app captures a low-latency audio stream from the device's microphone.
3. The captured audio is attached to the active WebRTC connection and streamed to the connected guardian device.
4. The app continues to stream reliably while running as a background (Foreground) service.

---

### Story 2.3: Receive and Play Audio (Guardian Mode)

- **As a** Caregiver with a device in "Guardian Mode",
- **I want** to hear the live audio from the patient's device,
- **so that** I can monitor them effectively.

**Acceptance Criteria:**

1. When in "Guardian Mode", the app successfully receives the incoming audio stream via the WebRTC connection.
2. The received audio is played clearly through the device's speaker.
3. A simple visual indicator (e.g., a pulsing icon) is displayed on the `Guardian Dashboard` to confirm that audio is being received.
