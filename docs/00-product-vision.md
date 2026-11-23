
# Product vision

## Problem

Clinical information is often fragmented across EMR forms, patient portals, messaging applications, phone calls, clinician interviews, and third-party chatbots. When each channel implements its own clinical questions, validation, and data mapping, the result is duplicated logic, inconsistent data, and fragile integrations.

## Vision

Vibe Rounds Contextual Interaction Platform (CIP) provides a reusable interaction and data-acquisition layer between people or AI agents and clinical information systems.

A pathway or authorized user can identify information that is needed. CIP can turn that requirement into a collection task, deliver it through an appropriate interface, capture the response, preserve its provenance, and submit a structured proposal to the authoritative clinical system.

## Product promise

**Define clinical collection once; deliver it through many channels.**

A collection workflow should be reusable across:
- Patient-facing web forms.
- Clinician-facing interfaces.
- Messaging applications.
- Conversational AI agents.
- Other authorized healthcare applications.

## Users and actors

- Patient or caregiver: provides information within an authorized scope.
- Clinician: initiates collection, enters information, reviews submissions, and takes clinical responsibility.
- Care team member: may collect information within assigned permissions.
- AI agent: may discover gaps, explain questions, and propose task creation within bounded permissions.
- Channel adapter: transports messages and translates platform payloads.
- EMR or clinical system: supplies clinical definitions and remains authoritative for the clinical record.
- CIP operator: configures connectors, policies, and platform operations.

## Non-goals

CIP is not:
- An EMR or patient-record system.
- A replacement for a clinical pathway engine.
- A general-purpose autonomous medical agent.
- A diagnostic or treatment recommendation engine.
- A messaging provider.
- A terminology server.
- A system that treats every chat message as a verified clinical observation.

## Success measures

Early measures should include:
- Percentage of collection tasks completed successfully.
- Time from task creation to response.
- Response validation failure rate.
- Duplicate submission rate.
- Percentage of submissions accepted, rejected, or routed for review by the EMR.
- Connector delivery and webhook reliability.
- User comprehension and accessibility.
- Audit completeness and authorization failure tests.
