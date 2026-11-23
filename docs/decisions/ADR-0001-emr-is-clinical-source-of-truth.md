
# ADR-0001: The EMR remains the clinical source of truth

- **Status:** Proposed
- **Date:** 2026-11-23

## Context

CIP must support multiple EMRs and interaction channels without duplicating clinical definitions, patient identity, pathway logic, or authoritative observations.

## Decision

The connected EMR or designated clinical system remains authoritative for patient identity, clinical element semantics, pathway requirements, and incorporation of observations into the clinical record.

CIP owns channel-neutral collection specifications, interaction sessions, collection tasks, response capture, connector orchestration, and acquisition provenance.

CIP submits structured proposals to the EMR. The EMR determines whether the proposal is accepted, rejected, or requires review.

## Consequences

Positive:
- CIP can integrate with multiple EMRs.
- Chat connectors remain replaceable.
- Clinical definitions are not duplicated.
- The EMR retains control of its clinical record and permissions.

Trade-offs:
- Integration contracts must be carefully versioned.
- CIP may need a limited cache of source metadata.
- End-to-end workflows depend on reliable EMR APIs and acknowledgement semantics.
