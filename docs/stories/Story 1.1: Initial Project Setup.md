# Story 1.1: Initial Project Setup

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Developer,
**I want** a new, correctly configured Android project for Listen Care,
**so that** I have a stable foundation to start building features.

## Acceptance Criteria

1.  A new Android project is created in a Git repository.
2.  The project is configured to use Jetpack Compose.
3.  Dependencies for WebRTC, JNI/NDK are added and compile successfully.
4.  The project's minimum target is Android 10 (API level 29).
5.  A basic "Hello World" screen can be successfully built and run on a device.

## Tasks / Subtasks

- [ ] **Task 1: Create Project Structure** (AC: 1)
  - [x] Create a new Android Studio project with an empty Activity.
  - [x] Initialize a Git repository and make the initial commit.
  - [ ] Create the modular structure as defined in the Architecture Document (`:app`, `:core:audio`, `:core:data`, `:core:network`, `:core:ui`, `:features:monitoring`, `:features:pairing`, `:features:settings`).
- [ ] **Task 2: Configure Gradle and Dependencies** (AC: 2, 3, 4)
  - [ ] Configure the root `settings.gradle.kts` to include all the new modules.
  - [ ] Update the `build.gradle.kts` files for the app and core modules.
  - [ ] Set `minSdk` to 29 and `compileSdk` to 34.
  - [ ] Add the "Latest Stable" dependencies for Jetpack Compose (BOM), Kotlin, and the Google WebRTC library.
  - [ ] Configure the NDK for the `:core:audio` module.
- [ ] **Task 3: Implement Verification Screen** (AC: 5)
  - [ ] Create a simple "Hello World" `@Composable` function in the `:app` module.
  - [ ] Set this composable as the content for `MainActivity.kt`.
  - [ ] Build and run the application on an emulator or physical device to confirm the project setup is valid.
- [ ] **Task 4: Setup Static Analysis and Testing**
  - [ ] Configure Detekt and Android Lint according to the Coding Standards.
  - [ ] Create a basic JUnit5 unit test to ensure the test runner is configured correctly.
- [ ] **Task 5: Implement Core Data Layer**
  - [ ] Create the `SettingsRepository.kt` in the `:core:data` module.
  - [ ] Implement the basic structure using Jetpack DataStore to handle the `AppSettings` model.
- [ ] **Task 6: Setup CI/CD**
  - [ ] Create a basic GitHub Actions workflow file (`.github/workflows/android-ci.yml`).
  - [ ] The workflow should trigger on push and pull requests to the `main` branch.
  - [ ] It must include steps to build the project and run all unit tests.

## Dev Notes

This story is foundational. Its purpose is to create the skeleton of the project according to the finalized Architecture Document. All subsequent stories will build upon this structure.

### Source Tree

The developer agent **MUST** create the full, multi-module source tree as defined in `architecture.md#Source Tree (Full Detail)`. This modular structure is critical for the project.

### Tech Stack to Configure

- **Language**: Kotlin (`Latest Stable`)
- **UI**: Jetpack Compose (`Latest Stable`)
- **Runtime**: Android 10+ (minSdk 29, targetSdk 34)
- **P2P Comms**: Google WebRTC Library (`Latest Stable`)
- **Native Dev**: Android NDK (`Latest Stable`)
- **Build System**: Android Gradle Plugin (`Latest Stable`)

### Coding Standards

The developer agent **MUST** set up Detekt and Android Lint. Key standards to remember for future stories are the use of the `Result` type for error handling, `val` over `var`, and immutable collections.

## Testing

- A basic unit test must be created in `app/src/test/` to verify the JUnit5 configuration.
- A basic UI test for the "Hello World" screen should be created in `app/src/androidTest/` to verify the Compose test runner configuration.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
