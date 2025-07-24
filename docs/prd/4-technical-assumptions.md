# 4. Technical Assumptions

## Repository Structure

- **Monorepo**: A single repository will be used to keep the Android project (Kotlin/Java) and any native C++ code (NDK) together.

## Service Architecture

- **Peer-to-Peer**: The application follows a P2P architecture. Communication is direct between devices on the local network. There is no backend server.

## Testing Requirements

- **Unit & Integration Tests**: The strategy will include Unit Tests and Integration Tests to verify the end-to-end local connection and audio processing.

## Additional Technical Assumptions

- **User Interface**: Built with Jetpack Compose.
- **Real-time Streaming**: Implemented using WebRTC, configured for local network communication only.
- **Network Traversal**: As the application is for local WiFi only, no external STUN/TURN services are required for the MVP.
- **Background Operation**: A standard Android Foreground Service will be used.
- **Performance**: Performance-critical code will be written in C++ and integrated using JNI/NDK.