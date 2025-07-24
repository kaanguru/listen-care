# Data Models

The application's data models represent the in-memory state and locally saved settings, not a traditional database.

- **PeerDevice**: Represents a discovered device on the network, holding its name, ID, and network address for pairing.
- **MonitoringSession**: Holds the state of an active session (e.g., `ACTIVE`, `PAUSED`) and the roles of the local and remote devices.
- **AppSettings**: Persists user-configurable settings locally on the device.
