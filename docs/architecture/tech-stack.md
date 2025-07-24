# Tech Stack

## Cloud Infrastructure

For the MVP, **Listen Care** is a purely peer-to-peer application and does not require any cloud infrastructure.

## Technology Stack Table

| Category           | Technology            | Version                                     | Purpose                                | Rationale                                                                                          |
| :----------------- | :-------------------- | :------------------------------------------ | :------------------------------------- | :------------------------------------------------------------------------------------------------- |
| **Language**       | Kotlin                | `Latest Stable`                             | Primary language for Android.          | Ensures use of the most current, stable language features.                                         |
| **User Interface** | Jetpack Compose BOM   | `Latest Stable`                             | Declarative UI toolkit for Android.    | Aligns with modern Android best practices; BOM manages library versions.                           |
| **Runtime**        | Android OS            | Min: API 29 (10) \<br\> Target: API 34 (14) | The operating system the app runs on.  | Minimum version targets older devices; targeting the latest ensures modern features are supported. |
| **P2P Comms**      | Google WebRTC Library | `Latest Stable`                             | Handles real-time audio streaming.     | The official library for implementing WebRTC on Android.                                           |
| **Native Dev**     | Android NDK           | `Latest Stable`                             | Enables C++ integration.               | Required for high-performance code; latest version ensures best tooling.                           |
| **Build System**   | Android Gradle Plugin | `Latest Stable`                             | Manages the application build process. | Ensures the most up-to-date and efficient build tooling is used.                                   |
