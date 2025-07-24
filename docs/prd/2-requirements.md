# 2. Requirements

## Functional

1.  **FR1**: The system shall automatically scan the local WiFi network to discover other devices running the Listen Care application, allowing a user to select a device to initiate a pairing session.
2.  **FR2**: After pairing, one device shall operate in "patient mode," continuously capturing audio via the microphone.
3.  **FR3**: The "patient mode" device shall transmit a short audio snippet over the local WiFi network only when a significant sound is detected.
4.  **FR4**: The "guardian mode" device shall receive and automatically play the audio snippet from the patient device.
5.  **FR5**: The "guardian mode" device must trigger a vibration alert when an audio snippet is received.
6.  **FR6**: The "guardian mode" device must trigger a critical, continuous, and loud alarm if the connection to the patient device is lost.
7.  **FR7**: The application running in "patient mode" must operate reliably in the background as a persistent service.
8.  **FR8**: Both the "patient mode" and "guardian mode" devices shall display controls to 'Pause' (temporarily suspend the audio stream) and 'Stop' (end the monitoring session).
9.  **FR9**: Listen Override: The 'guardian mode' device must include a 'Listen Override' button. When this button is pressed and held, it will open a live audio stream from the 'patient' device, regardless of the noise level. Releasing the button will stop the live stream and return the system to event-based monitoring.

## Non-Functional

1.  **NFR1**: The application must be highly optimized for low battery and CPU consumption, especially when running in "patient mode".
2.  **NFR2**: The application must be compatible with devices running **Android 10** and higher.
3.  **NFR3**: The build process must be streamlined for fast development releases on older hardware.
4.  **NFR4**: The audio stream between devices must have low latency to be considered near real-time.
5.  **NFR5**: The MVP of the application will only function over a WiFi connection; mobile data and internet connectivity are not supported.
6.  **NFR6**: **Audio Encoding**: The audio stream must be configured for a low bitrate of approximately 32 kbps. High fidelity is not a goal; low resource usage is the priority.
