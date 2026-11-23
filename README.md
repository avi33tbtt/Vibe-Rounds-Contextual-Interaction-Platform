
# Vibe Rounds — Contextual Interaction Platform (CIP)

**An open-source, channel-independent platform for collecting and exchanging clinical context through humans, AI agents, and messaging applications.**

CIP is the interaction and acquisition layer of the Vibe Rounds ecosystem. It connects patient and clinician interfaces, conversational AI, and external messaging channels to clinical context owned by an EMR or other authorized clinical system.

> **Architectural boundary:** CIP owns how information is requested, collected, orchestrated, and transported. The connected EMR owns clinical definitions, patient identity, the authoritative clinical record, and the decision to accept submitted information into that record.

This repository is an initial architecture and implementation scaffold. It is **not yet a production clinical system** and does not include a production-ready chatbot, messaging connector, EMR integration, authentication system, or clinical validation engine.

## Position in the Vibe Rounds ecosystem

| Repository / product | Primary responsibility |
|---|---|
| Vibe Rounds | Clinical knowledge creation and learning |
| Vibe Rounds EMR Enhancer | Contextual elements, patient records, observations, pathways, clinical workflows |
| Vibe Rounds CCIS | Contextual clinical intelligence execution and analytics |
| **Vibe Rounds CIP (this repository)** | Human/AI interaction, contextual data acquisition, collection tasks, and channel connectors |

CIP should remain independently deployable and should be able to integrate with other EMRs through documented, versioned contracts.

## Core capabilities

1. **Context integration** — receive contextual element definitions, pathway requirements, and patient-context summaries from an authorized clinical system.
2. **Collection specifications** — define reusable questions, forms, response types, branching rules, and mappings to external clinical element identifiers.
3. **Collection orchestration** — create, assign, track, expire, and complete requests for information.
4. **Interaction runtime** — manage channel-neutral interaction sessions and structured response capture.
5. **AI agent interface** — allow an authorized agent to discover collection requirements and propose or initiate permitted collection tasks.
6. **Channel adapters** — translate between CIP contracts and platform-specific messaging APIs.
7. **Submission and review handoff** — submit structured responses to the EMR for validation, review, and record incorporation.
8. **Audit and provenance** — preserve who or what initiated, collected, transformed, and submitted information.

## Design principles

- **EMR remains the clinical source of truth.** CIP does not redefine the meaning of clinical elements or silently write directly to an EMR database.
- **Channel independence.** Clinical collection workflows must not depend on WhatsApp, Telegram, web chat, or a particular chatbot vendor.
- **Human and AI parity with safeguards.** Both may initiate permitted collection workflows, but identity, authorization, provenance, and review requirements remain explicit.
- **No silent clinical promotion.** Patient-reported information and AI-extracted proposals are not automatically clinician-verified observations.
- **API-first and contract-first.** Use versioned schemas and documented integration boundaries.
- **Synthetic data by default.** Development and demos must not require real patient data.
- **Auditable lifecycle.** Requests, responses, corrections, retries, and state transitions must be traceable.
- **Minimal coupling.** Integrate with the EMR and CCIS through contracts, not shared database tables.

## Repository map

```text
.
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── CHANGELOG.md
├── .gitignore
├── docs/
│   ├── 00-product-vision.md
│   ├── 01-system-architecture.md
│   ├── 02-domain-model.md
│   ├── 03-integration-contracts.md
│   ├── 04-security-and-safety.md
│   ├── 05-development-roadmap.md
│   ├── 06-demo-scenarios.md
│   └── decisions/
│       └── ADR-0001-emr-is-clinical-source-of-truth.md
├── contracts/
│   ├── README.md
│   ├── collection-task.schema.json
│   ├── collection-specification.schema.json
│   └── response-envelope.schema.json
├── examples/
│   └── hypertension-follow-up/
│       ├── README.md
│       ├── pathway-requirements.example.json
│       ├── collection-specification.example.json
│       └── collection-task.example.json
├── src/
│   └── README.md
└── tests/
    └── README.md
```

## Suggested first implementation slice

Build one end-to-end, synthetic-data workflow before integrating a real messaging provider:

1. Import a pathway requirement from a mock EMR adapter.
2. Check whether required contextual information is missing or stale.
3. Create a collection task for the patient.
4. Render the task in a basic patient-facing web form.
5. Submit a structured response to CIP.
6. Validate the response against the collection specification.
7. Preserve patient-reported provenance and task history.
8. Send a proposed observation to a mock EMR endpoint.
9. Have the mock EMR acknowledge, reject, or request review.
10. Display the updated task state and audit trail.

Only after this vertical slice works should a platform-specific chat connector be added.

## Development status

**Stage:** Architecture and contract scaffold.

The JSON Schemas and examples in this repository are starting contracts for discussion and iteration. They are not final FHIR profiles, terminology bindings, or a production interoperability specification.

See [the roadmap](docs/05-development-roadmap.md) for staged implementation.
