# System architecture (proposed)

```text
Unity XR UI / accessible input
        |
Session Controller ---- Safety Policy (hard limits, stop/pause)
        |                         |
EMG / Hand / Gaze adapters         |
        |                         |
Signal validation -> Features -> A.U.R.A. bounded adaptation
        |                         |
Encrypted local session store <- Audit events
        |
Consent-controlled sync gateway -> Segregated research/clinical backend
```

## Boundaries
1. **Unity client:** XR rendering, interactions, local exercise execution; must function without network.
2. **Sensor abstraction:** calibrated timestamps, quality scores, disconnection states, no unvalidated hardware assumptions.
3. **A.U.R.A.:** start with interpretable deterministic adaptation; ML-Agents training only after dataset and safety validation. The safety policy can veto every output.
4. **Data:** purpose-limited, encrypted, versioned records; no identifiable clinical telemetry to generic analytics without documented legal basis and vendor review.
5. **Clinical supervision:** authorized clinician configures constraints and reviews changes; emergency stop always available.
6. **Evaluation:** synthetic fixtures, unit/integration tests, device benchmarks, clinical and regulatory evidence.

## Key hazards
Motion sickness, photosensitivity, fatigue, pain aggravation, unsafe adaptation, misleading predictions, sensor dropout, privacy breach and model bias. Mitigate through validated limits, reduced-motion modes, clinician oversight, explicit consent, fallback modes and systematic hazard tracking.

The concept's 90 FPS target is a performance requirement to verify on selected headsets, not proof of safety. Predictive recovery reports and conversational assistants remain experimental until clinically validated.
