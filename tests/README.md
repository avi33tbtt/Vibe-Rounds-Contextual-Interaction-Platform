
# Test strategy

Start with contract and domain tests before UI or provider integrations.

Required test categories:
- JSON Schema positive and negative examples.
- Valid and invalid task state transitions.
- Patient/encounter authorization boundaries.
- Idempotent response and webhook ingestion.
- Out-of-order event handling.
- Provenance preservation through normalization.
- EMR accepted/rejected/review-required outcomes.
- Connector retry and delivery failure.
- AI agent scope and privilege escalation.
- Cross-patient data isolation.

All fixtures must be synthetic. Tests must assert that an AI proposal or patient-reported value is never automatically marked clinician-verified.
