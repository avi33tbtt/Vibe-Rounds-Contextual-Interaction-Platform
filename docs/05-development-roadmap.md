
# Development roadmap

Build the platform in deliberate, testable increments. Start as a modular monolith with a mock EMR and synthetic data. Avoid prematurely implementing multiple messaging providers or microservices.

## Phase 0 — Repository and contract foundation

- [x] Product vision and responsibility boundaries.
- [x] Initial architecture and domain model.
- [x] Draft JSON Schemas and synthetic workflow example.
- [ ] Agree stable identifier and versioning conventions with EMR Enhancer.
- [ ] Agree context and pathway requirement payloads.
- [ ] Define threat model and data classification.

**Exit criterion:** the four-repository boundaries and initial contracts are reviewed and documented.

## Phase 1 — Core domain and task lifecycle

- [ ] Implement collection specification model and registry.
- [ ] Implement collection task model and validated state machine.
- [ ] Implement interaction session model.
- [ ] Implement audit event model.
- [ ] Add schema validation and contract tests.
- [ ] Add idempotency and correlation IDs.

**Exit criterion:** tasks can be created, assigned, progressed, cancelled, expired, and audited using synthetic data.

## Phase 2 — Context and pathway integration

- [ ] Build a mock EMR context adapter.
- [ ] Import element references and versions.
- [ ] Import pathway information requirements.
- [ ] Compare requirements with existing context and freshness rules.
- [ ] Propose missing or stale data collection.
- [ ] Keep clinical element semantics owned by the EMR.

**Exit criterion:** a synthetic pathway requirement can produce a justified collection plan.

## Phase 3 — Collection specifications and human interfaces

- [ ] Define question and response component types.
- [ ] Support required/optional questions and conditional branching.
- [ ] Build a basic patient-facing form.
- [ ] Build a clinician task-management view.
- [ ] Support accessibility and localization.
- [ ] Capture respondent and effective time.

**Exit criterion:** a patient can complete a task through a web interface and CIP produces a normalized response envelope.

## Phase 4 — Validation and EMR handoff

- [ ] Validate response shape and constraints.
- [ ] Validate units and terminology mappings against source-provided contracts.
- [ ] Preserve original answer and normalized value.
- [ ] Submit a proposed observation package to a mock EMR.
- [ ] Handle accepted, rejected, and review-required responses.
- [ ] Test retries and duplicate submissions.

**Exit criterion:** a complete synthetic collection flow reaches a mock EMR and displays its acknowledgement.

## Phase 5 — AI agent interface

- [ ] Define bounded agent capabilities and scopes.
- [ ] Add context-gap discovery endpoint.
- [ ] Allow an agent to propose task creation.
- [ ] Use approved collection specifications as the source for questions.
- [ ] Validate agent-produced response envelopes.
- [ ] Test prompt injection, hallucinated values, and privilege escalation.

**Exit criterion:** an agent can help conduct an authorized collection workflow without owning clinical truth or bypassing review.

## Phase 6 — Connector framework and first channel

- [ ] Define connector interface and capability declaration.
- [ ] Build a mock chat connector.
- [ ] Implement signed inbound webhook handling.
- [ ] Implement outbound delivery, retry, and failure states.
- [ ] Add one real messaging connector only after security and consent design.
- [ ] Document connector setup and local testing.

**Exit criterion:** the same task and response contracts work through the web interface and one chat channel.

## Phase 7 — Production readiness

- [ ] Authentication and authorization.
- [ ] Consent and communication preference enforcement.
- [ ] Encryption, secret management, and retention.
- [ ] Monitoring, audit, backup, and recovery.
- [ ] Load, reliability, and security testing.
- [ ] Clinical safety and jurisdictional review.
- [ ] Deployment and operations documentation.

**Exit criterion:** production readiness is assessed for a clearly bounded use case; no blanket claim of compliance.

## Phase 8 — Ecosystem and community integrations

- [ ] Stable public API and adapter SDK.
- [ ] Additional EMR adapters.
- [ ] Additional messaging connectors.
- [ ] FHIR mapping where appropriate and explicitly profiled.
- [ ] Community contribution templates and conformance suite.
- [ ] Compatibility matrix for supported contract versions.

**Exit criterion:** an external developer can build and test a connector without changing the core clinical domain model.
