# Database Schema

The application does not use a traditional database. The only persisted data is the `AppSettings`, stored locally using Android's Jetpack DataStore.

| Key                  | Data Type       | Description                                                                                               | Default Value        |
| :------------------- | :-------------- | :-------------------------------------------------------------------------------------------------------- | :------------------- |
| `deviceName`         | `String`        | The user-friendly name the device shows on the network.                                                   | "Listen Care Device" |
| `noiseSensitivity`   | `Enum (String)` | : The threshold for triggering a noise alert. Can be 'Quietest', 'Quiet', 'Normal', 'Loud', or 'Loudest'. | "Normal"             |
| `alertWithBeep`      | `Boolean`       | If true, the guardian device will play a sound on a noise alert.                                          | `true`               |
| `alertWithVibration` | `Boolean`       | If true, the guardian device will vibrate on a noise alert.                                               | `true`               |
