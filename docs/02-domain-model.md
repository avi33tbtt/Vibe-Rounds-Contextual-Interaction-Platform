
# Domain model

This document defines the initial conceptual model. The accompanying JSON Schemas are draft implementation aids and will evolve.

## Core entities

### Context reference

A reference to a clinical element defined by the connected EMR. CIP stores the source system, stable identifier, display metadata needed for collection, and definition version. It does not become the canonical clinical definition.

### Collection specification

A reusable description of how to ask for one or more contextual elements. It can include:
- Target element references.
- Prompt and help text.
- Response type and constraints.
- Options and conditional follow-up questions.
- Supported interaction modes.
- Language variants.
- Review requirements and safety notes.
- Version and lifecycle metadata.

A collection specification is not a clinical pathway and does not itself request data from a patient.

### Collection task

A concrete request to obtain information from a recipient for a patient and optionally an encounter. It records:
- Who or what initiated the request.
- Why it was created and the pathway/workflow reference.
- Which elements are requested.
- Intended recipient and permitted channels.
- Due date, status, and lifecycle history.
- Consent/communication policy references.
- Whether clinician review is required.

A task is a request, not an observation.

### Interaction session

A channel-neutral interaction associated with a task. A session may span multiple messages or form submissions. Channel-specific message identifiers belong in adapter metadata, not in clinical element definitions.

### Response envelope

A normalized representation of submitted answers. It records the respondent, collection method, timestamps, specification version, answers, and references to the interaction/task.

### Submission package

A structured proposal sent to the EMR. The EMR validates, accepts, rejects, or routes it for review. CIP records the outcome and correlation identifiers.

### Audit event

An append-only record of significant actions and state transitions, including actor, action, target, timestamp, correlation ID, and relevant metadata.

## Task lifecycle

Suggested states:

- `draft`
- `requested`
- `assigned`
- `in_progress`
- `responded`
- `validating`
- `submitted_for_review`
- `accepted`
- `rejected`
- `completed`
- `declined`
- `unable_to_answer`
- `expired`
- `cancelled`
- `failed`

Not every integration must use every state. State transitions must be explicit and validated; clients must not set arbitrary states.

## Provenance distinctions

At minimum, distinguish:
- Patient-reported.
- Caregiver-reported.
- Clinician-entered.
- Other staff-entered.
- Device-originated.
- AI-extracted or AI-proposed.
- Imported from another system.

Also distinguish `unreviewed`, `review_required`, `reviewed`, `accepted`, and `rejected` as appropriate. Do not conflate source type with verification status.

## Important temporal fields

Keep separate:
- `effective_at`: when the information was true or measured.
- `recorded_at`: when CIP received it.
- `submitted_at`: when it was sent to the EMR.
- `reviewed_at`: when a reviewer acted.

Never assume the message timestamp is the clinical effective time.
