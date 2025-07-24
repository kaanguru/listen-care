## Epic 3: Alerts, Controls & Finalization

**Expanded Goal**: This final epic transforms the core audio streamer into a complete, reliable monitoring tool. We will add the critical alert systems for noise and connection loss, implement user controls to manage the session, and perform the final polish needed for a confident V1 release on the Google Play Store.

---

### Story 3.1: Noise Detection & Alert

- **As a** Caregiver,
    
- **I want** to receive a vibration alert on my device when a significant noise is detected,
    
- **so that** I am notified of potential distress even if I'm not actively listening.
    

**Acceptance Criteria:**

1. The 'Guardian Mode' app analyzes the incoming audio stream for sudden spikes in volume.
    
2. When a noise event that exceeds a set threshold is detected, the guardian device vibrates distinctly.
    
3. The alert does not trigger on low-level, continuous background noise.
    
4. A simple setting is available to adjust noise sensitivity (e.g., Low, Medium, High).
    

---

### Story 3.2: Connection Loss Alarm

- **As a** Caregiver,
    
- **I want** to be alerted with a loud, continuous alarm if the connection is lost,
    
- **so that** I never mistakenly believe I am monitoring when the system is down.
    

**Acceptance Criteria:**

1. The 'Guardian Mode' app continuously monitors the health of the WebRTC connection.
    
2. If the connection is lost for more than 5-10 seconds, a loud, repeating alarm sound is triggered.
    
3. The alarm overrides the device's silent/vibrate settings to ensure it is heard.
    
4. The alarm can only be dismissed by a direct user action on the screen.
    
5. The app attempts to reconnect in the background while the alarm is sounding.
    

---

### Story 3.3: Session Pause & Stop Controls

- **As a** User,
    
- **I want** to be able to pause and stop the monitoring session from either device,
    
- **so that** I have full control over the system.
    

**Acceptance Criteria:**

1. Both the 'Guardian' and 'Patient' screens contain functional 'Pause' and 'Stop' buttons.
    
2. Tapping 'Pause' temporarily suspends the audio stream without ending the connection; tapping 'Resume' restarts the stream.
    
3. The status on both devices clearly indicates when the session is paused.
    
4. Tapping 'Stop' terminates the connection and returns both devices to the 'Pairing Screen'.
    

---

### Story 3.4: Release Finalization

- **As a** Developer,
    
- **I want** to finalize all UI elements and prepare the application for release,
    
- **so that** we can launch on the Google Play Store.
    

**Acceptance Criteria:**

1. A 'Settings' screen is created that includes the noise sensitivity control.
    
2. All UI elements are polished according to the defined color palette and design goals.
    
3. The application icon and a simple 'About' page are implemented.
    
4. The application is successfully built into a release-signed App Bundle.
    

---
