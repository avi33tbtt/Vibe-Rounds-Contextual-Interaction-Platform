
# Security, privacy, and clinical safety

## Security model

CIP handles potentially sensitive health information. It must be designed as a security-sensitive system from the beginning, even while using synthetic data during development.

### Identity

- Authenticate patients, clinicians, staff, agents, connectors, and system integrations.
- Resolve patient identity through a trusted EMR identity mapping.
- Never rely on a phone number or chat account alone as proof of patient identity.
- Support delegated caregiver access only when the connected clinical system authorizes it.

### Authorization

Use least privilege and enforce authorization on every server-side operation. Scope access by actor, patient, encounter, task, action, and integration. Connector credentials should be scoped to specific capabilities and environments.

### Consent and communication preferences

Before sending messages or collecting information, respect the clinical system's consent, communication preference, legal basis, and channel policy. Record the applicable policy reference and decision. Do not assume consent from the existence of a chat account.

### Webhooks and messaging

- Verify signatures.
- Enforce timestamp windows and replay protection.
- Rate-limit and validate payloads.
- Use idempotent event ingestion.
- Avoid logging message bodies or secrets.
- Store provider tokens in a secret manager or environment-specific secret store.

### Data minimization and retention

Retain only what is necessary for the interaction, audit, and applicable legal obligations. Define retention and deletion policies before production deployment. Do not assume that storing a full transcript is necessary to preserve a structured clinical response.

## Clinical safety

- Clearly identify whether information is patient-reported, caregiver-reported, clinician-entered, device-originated, or AI-proposed.
- Preserve the original answer and any normalization/transformation.
- Do not infer a missing clinical answer.
- Do not treat a chatbot summary as the original response.
- Route high-risk or urgent responses through a clinically approved escalation policy.
- Do not make diagnosis or treatment decisions within the collection engine.
- Do not send medication changes or treatment instructions without an authorized clinical workflow and appropriate approval.
- Provide a safe fallback when a user reports an emergency; exact content and routing must be approved for the deployment jurisdiction.
- Support correction, amendment, rejection, and supersession without erasing history.

## Threat modelling checklist

- Account takeover and wrong-patient association.
- Malicious or spoofed webhooks.
- Prompt injection through inbound messages or external content.
- AI agent privilege escalation.
- Cross-patient data leakage.
- Duplicate and out-of-order responses.
- Replay of old task links.
- Unauthorized channel delivery.
- Sensitive data leakage through logs, analytics, or crash reports.
- Denial of service and message flooding.
- Insecure secrets and connector configuration.
- Incorrect unit, time, or terminology mapping.

## Release gate

Do not use real patient data or deploy for clinical operations until security, privacy, clinical safety, regulatory, and operational reviews have been completed for the intended jurisdiction and use case.
