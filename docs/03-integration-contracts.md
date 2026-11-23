
# Integration contracts

## Integration pattern

Use versioned HTTP APIs and webhooks initially. Use an outbox or equivalent reliable event-delivery mechanism for outbound events. All write operations should support idempotency keys and correlation IDs.

## EMR to CIP

The EMR may provide:
- Patient/encounter references and authorization-scoped identity mappings.
- Contextual element metadata and versions.
- Pathway requirements or a pathway-step event indicating required elements.
- A limited context summary sufficient to determine whether collection is needed.
- Collection policy, permitted recipient, and review requirements.

CIP should request only the minimum context needed. Avoid broad patient-record replication.

## CIP to EMR

CIP may submit:
- Collection task status events.
- Structured response packages.
- Proposed observations with source and provenance metadata.
- References to the collection specification and pathway requirement.
- Review disposition and integration correlation identifiers.

The EMR decides whether to accept, reject, or route a submission for review. The EMR should return a durable acknowledgement and a reason or validation result where possible.

## Connector to CIP

A connector translates:
- CIP outbound interaction requests into platform-specific messages or forms.
- Platform inbound messages into normalized response envelopes.
- Provider delivery/read/error callbacks into connector delivery events.

Connectors must not decide clinical meaning, bypass task authorization, or write directly to the EMR.

## AI agent to CIP

An AI agent may, within explicit authorization:
- Discover which information is missing or due.
- Explain a collection specification in user-friendly language.
- Propose a collection task.
- Ask questions using approved specification content.
- Normalize a response into a proposed response envelope.

An AI agent must not:
- Expand its patient access beyond the authorized scope.
- invent clinical values or fill missing answers by inference.
- mark patient information as clinician-verified.
- independently change treatment or issue unapproved clinical instructions.
- bypass human review rules or EMR acceptance.

## Initial endpoint sketch

These are proposed endpoints, not implemented APIs:

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/v1/context/requirements` | Retrieve authorized collection requirements |
| POST | `/api/v1/collection-tasks` | Create a task |
| GET | `/api/v1/collection-tasks/{taskId}` | Retrieve task state |
| POST | `/api/v1/collection-tasks/{taskId}/assign` | Assign recipient/channel |
| POST | `/api/v1/collection-tasks/{taskId}/responses` | Submit normalized response |
| POST | `/api/v1/collection-tasks/{taskId}/cancel` | Cancel task |
| POST | `/api/v1/webhooks/{connector}` | Receive signed connector webhook |
| POST | `/api/v1/emr/submissions` | Submit proposed data package |

## Contract rules

- Prefix APIs with `/api/v1`.
- Include `source_system`, `schema_version`, and stable external identifiers where applicable.
- Use UTC timestamps in ISO 8601 format.
- Use idempotency keys for response and webhook ingestion.
- Use correlation IDs across task, interaction, connector, and EMR submission.
- Define retryable versus permanent errors.
- Never trust a patient ID supplied by a client without authorization and identity resolution.
- Version contracts deliberately and document breaking changes.
