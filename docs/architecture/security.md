# Security

- **Data in Transit**: As per the PRD, the audio stream over local WiFi is **not encrypted** for the MVP.
- **Data at Rest**: Settings are stored in the app's private, sandboxed directory using Jetpack DataStore.
- **PII**: The application must not store any Personally Identifiable Information.
