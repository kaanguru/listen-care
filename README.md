# Listen Care

Listen Care is an Android application designed to serve caregivers of elderly or at-risk individuals, particularly those with conditions that may prevent them from actively calling for help. The MVP is a lightweight, event-driven audio monitoring tool that operates exclusively over a local WiFi network to ensure reliability and low battery consumption. Instead of a constant stream, the 'patient' device will listen locally and only transmit audio when a sound exceeds a user-defined threshold.

## Features

*   **Local Network Discovery:** Automatically discover other devices running Listen Care on the same WiFi network.
*   **Event-Driven Audio Monitoring:** The "patient" device only transmits audio when a significant sound is detected, saving battery life.
*   **Real-Time Audio Streaming:** The "guardian" device receives and plays audio snippets in near real-time.
*   **Vibration Alerts:** The "guardian" device vibrates when an audio snippet is received.
*   **Connection Loss Alarm:** A loud, continuous alarm sounds if the connection to the patient device is lost.
*   **Session Control:** Pause and stop monitoring sessions from either device.
*   **Listen Override:** Manually listen in on the "patient" device at any time.

## Tech Stack

*   **Language:** Kotlin
*   **UI:** Jetpack Compose
*   **P2P Comms:** WebRTC
*   **Native Dev:** Android NDK (C++)
*   **Build System:** Gradle
