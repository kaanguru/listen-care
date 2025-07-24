# Story 3.4: Release Finalization

## Status

- [ ] Draft
- [x] Approved
- [ ] InProgress
- [ ] Review
- [ ] Done

## Story

**As a** Developer,
**I want** to finalize all UI elements and prepare the application for release,
**so that** we can launch on the Google Play Store.

## Acceptance Criteria

1.  A 'Settings' screen is created that includes the 5-step noise sensitivity control and the beep/vibrate alert toggles.
2.  All UI elements on all screens are polished and consistent with the defined color palette and design goals.
3.  The application icon and a simple 'About' page are implemented.
4.  The application is successfully built into a release-signed App Bundle, ready for upload.

## Tasks / Subtasks

- [ ] **Task 1: Implement Settings Screen** (AC: 1)
  - [ ] In the `:features:settings` module, implement the `SettingsScreen` and `SettingsViewModel`.
  - [ ] The UI must contain the 5-step control for `noiseSensitivity` and the boolean toggles for `alertWithBeep` and `alertWithVibration`.
  - [ ] The ViewModel must use the `SettingsRepository` to load and save the settings.
- [ ] **Task 2: Final UI Polish** (AC: 2)
  - [ ] Review all existing screens (`Pairing`, `Guardian Dashboard`, `Patient Status`) for final UI polish.
  - [ ] Ensure all buttons, text, and colors are consistent with the architectural guidelines.
- [ ] **Task 3: Implement App Assets** (AC: 3)
  - [ ] Create a simple 'About' screen containing the app version and any other required information.
  - [ ] Integrate the final application icon assets for all required resolutions.
- [ ] **Task 4: Create Help Screen**
  - [ ] Create a simple "Help" screen that explains the meaning of the different UI states (e.g., "Scanning", "Connected", "Paused") and the function of each button.
- [ ] **Task 4: Prepare for Release** (AC: 4)
  - [ ] Configure the `build.gradle.kts` file for a release build, including versioning and signing configurations.
  - [ ] Generate a signed App Bundle artifact.
- [ ] **Task 5: Write Tests**
  - [ ] Write a Maestro test to verify that changing a setting on the Settings screen is correctly persisted and reflected in the app's behavior (e.g., disabling vibration).
  - [ ] Perform a full manual regression test on a release candidate build.

## Dev Notes

- This is the final story for the MVP. It is focused on tying up loose ends and preparing the final release artifact. Attention to detail on the UI polish is important for the app's first impression.
- The process for creating a signing key and configuring the release build in Gradle must be followed carefully according to the official Android developer documentation.

## Testing

- A full manual regression test of all features (Pairing, Streaming, Alerts, Controls) should be performed on the final release candidate build before it is uploaded to the Play Store.

## Change Log

| Date       | Version | Description                           | Author   |
| :--------- | :------ | :------------------------------------ | :------- |
| 2025-07-23 | 1.0     | Initial story draft created from PRD. | Bob (SM) |
