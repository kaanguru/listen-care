## Epic 1: Project Foundation & Device Pairing

**Expanded Goal**: The goal of this epic is to create the fundamental scaffolding for the **Listen Care** application and deliver the core pairing functionality. By the end of this epic, we will have a testable app that proves two devices can successfully discover and connect to each other on a local network, validating our core technical choices before we add the complexity of audio streaming.

---

### Story 1.1: Initial Project Setup

- **As a** Developer,
- **I want** a new, correctly configured Android project for Listen Care,
- **so that** I have a stable foundation to start building features.

**Acceptance Criteria:**

1. A new Android project is created and hosted in a Git repository.
2. The project is configured to use Jetpack Compose for the UI.
3. Dependencies for WebRTC and JNI/NDK are successfully added and compile.
4. The project's minimum target is set to Android 9 (API level 28).
5. A basic "Hello World" screen can be successfully built and run on a device.

---

### Story 1.2: Network Device Discovery

- **As a** Caregiver,
- **I want** the app to automatically find other devices running Listen Care on my WiFi,
- **so that** I can easily start the pairing process without typing codes.

**Acceptance Criteria:**

1. When on the "Pairing Screen," the app automatically scans the local WiFi network for other Listen Care instances.
2. Discovered devices are displayed in a simple, tappable list.
3. The list updates if a new device joins or leaves the network.
4. The scanning process is optimized for minimal battery usage.

---

### Story 1.3: Connection Handshake

- **As a** Caregiver,
- **I want** to tap on a discovered device to establish a connection,
- **so that** I can pair the two devices for monitoring.

**Acceptance Criteria:**

1. Tapping a device in the discovery list initiates a connection request.
2. The receiving device shows a simple prompt to "Accept" or "Decline" the connection.
3. When "Accept" is tapped, a stable peer-to-peer WebRTC connection is established.
4. Both devices leave the "Pairing Screen" and display a new screen with a clear "Connected" status.
