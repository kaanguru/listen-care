# Error Handling Strategy

- **Error Propagation**: Functions that can fail will return Kotlin's built-in `Result` type, an approach similar to the `neverthrow` library, to ensure all errors are handled explicitly.
- **Logging**: **Timber** will be used for logging. Errors and warnings in the release build will be sent to **Sentry**.
