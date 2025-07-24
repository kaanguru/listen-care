# Listen Care Product Requirements Document (PRD)

| Date       | Version | Description                                                                                                   | Author    |
| :--------- | :------ | :------------------------------------------------------------------------------------------------------------ | :-------- |
| 2025-07-23 | 1.1     | Revised timeline to 60 days, updated target to Android 10, and removed internet dependency (local WiFi only). | John (PM) |
| 2025-07-23 | 1.0     | Initial PRD draft.                                                                                            | John (PM) |

## 1. Goals and Background Context

### Goals

- Successfully launch V1 of Listen Care on the Google Play Store by **October 10, 2025**.
- Achieve 100 active installations within the first three months post-launch.
- Establish a strong brand reputation for reliability and simplicity within the tech-enabled elder care market.
- Provide caregivers with a tangible increase in their peace of mind.
- Ensure the setup process from download to active monitoring is under five minutes.

### Background Context

**Listen Care** is an Android application designed to serve caregivers of elderly or at-risk individuals, particularly those with conditions that may prevent them from actively calling for help. The MVP is a lightweight, event-driven audio monitoring tool that operates exclusively over a local WiFi network to ensure reliability and low battery consumption. Instead of a constant stream, the 'patient' device will listen locally and only transmit audio when a sound exceeds a user-defined threshold.

## 2. Requirements

### Functional

1.  **FR1**: The system shall automatically scan the local WiFi network to discover other devices running the Listen Care application, allowing a user to select a device to initiate a pairing session.
2.  **FR2**: After pairing, one device shall operate in "patient mode," continuously capturing audio via the microphone.
3.  **FR3**: The "patient mode" device shall transmit a short audio snippet over the local WiFi network only when a significant sound is detected.
4.  **FR4**: The "guardian mode" device shall receive and automatically play the audio snippet from the patient device.
5.  **FR5**: The "guardian mode" device must trigger a vibration alert when an audio snippet is received.
6.  **FR6**: The "guardian mode" device must trigger a critical, continuous, and loud alarm if the connection to the patient device is lost.
7.  **FR7**: The application running in "patient mode" must operate reliably in the background as a persistent service.
8.  **FR8**: Both the "patient mode" and "guardian mode" devices shall display controls to 'Pause' (temporarily suspend the audio stream) and 'Stop' (end the monitoring session).
9.  **FR9**: Listen Override: The 'guardian mode' device must include a 'Listen Override' button. When this button is pressed and held, it will open a live audio stream from the 'patient' device, regardless of the noise level. Releasing the button will stop the live stream and return the system to event-based monitoring.

### Non-Functional

1.  **NFR1**: The application must be highly optimized for low battery and CPU consumption, especially when running in "patient mode".
2.  **NFR2**: The application must be compatible with devices running **Android 10** and higher.
3.  **NFR3**: The build process must be streamlined for fast development releases on older hardware.
4.  **NFR4**: The audio stream between devices must have low latency to be considered near real-time.
5.  **NFR5**: The MVP of the application will only function over a WiFi connection; mobile data and internet connectivity are not supported.
6.  **NFR6**: **Audio Encoding**: The audio stream must be configured for a low bitrate of approximately 32 kbps. High fidelity is not a goal; low resource usage is the priority.

## 3. User Interface Design Goals

### Overall UX Vision

The user experience for **Listen Care** will be exceptionally simple, clear, and functional. The primary goal is to provide peace of mind to the caregiver through an interface that is immediately understandable and completely reliable. Every element will be designed to reduce cognitive load, build trust, and ensure critical information (like connection status) is always evident.

### Key Interaction Paradigms

- **Controls**: All interactions will be based on simple taps on large, clearly-labeled buttons. No complex gestures like swiping or drag-and-drop will be used.

### Core Screens and Views

1.  **Pairing Screen**: For device discovery and selection.
2.  **Guardian Dashboard**: Main screen for the caregiver showing connection status and controls.
3.  **Patient Status Screen**: Minimal screen for the monitored device showing active status and controls.
4.  **Settings Screen**: For basic configurations like noise sensitivity.

### Accessibility

Given the user base, accessibility is a priority. The design should aim for high-contrast text, very large touch targets for all buttons, and simple, clear language to ensure ease of use for everyone.

### Branding

The UI will use the following defined color palette:

- `#ffa69e` (Light Coral)
- `#faf3dd` (Ivory)
- `#b8f2e6` (Light Teal)
- `#aed9e0` (Powder Blue)
- `#5e6472` (Slate Gray)

### Target Device and Platforms

The application will target Android smartphones running Android 10 and up. For the V1, the application will be optimized for portrait mode on standard phone screen sizes. Full responsive support for tablets and landscape mode is a post-MVP consideration.

## 4. Technical Assumptions

### Repository Structure

- **Monorepo**: A single repository will be used to keep the Android project (Kotlin/Java) and any native C++ code (NDK) together.

### Service Architecture

- **Peer-to-Peer**: The application follows a P2P architecture. Communication is direct between devices on the local network. There is no backend server.

### Testing Requirements

- **Unit & Integration Tests**: The strategy will include Unit Tests and Integration Tests to verify the end-to-end local connection and audio processing.

### Additional Technical Assumptions

- **User Interface**: Built with Jetpack Compose.
- **Real-time Streaming**: Implemented using WebRTC, configured for local network communication only.
- **Network Traversal**: As the application is for local WiFi only, no external STUN/TURN services are required for the MVP.
- **Background Operation**: A standard Android Foreground Service will be used.
- **Performance**: Performance-critical code will be written in C++ and integrated using JNI/NDK.