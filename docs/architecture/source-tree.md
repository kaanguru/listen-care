# Source Tree

The project follows a modern, multi-module architecture to ensure separation of concerns and faster build times.

```plaintext
care-audio/
├── app/                  # Main application module (assembles all other modules)
│   └── src/main/java/com/careaudio/
├── core/
│   ├── audio/            # C++ AudioEngine source (NDK) and its Kotlin/JNI bridge
│   ├── data/             # SettingsRepository using Jetpack DataStore
│   ├── network/          # WebRTC, Discovery, and network models
│   └── ui/               # Shared Jetpack Compose components and the app theme
└── features/
    ├── monitoring/       # The main monitoring dashboard feature
    ├── pairing/          # The device discovery and pairing feature
    └── settings/         # The settings feature
```
