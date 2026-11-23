
# Security policy

CIP is an early-stage scaffold. Do not deploy it with real patient information.

## Reporting vulnerabilities

Please do not publish exploitable details in public issues. Until a dedicated security contact is configured, use the repository host's private vulnerability reporting feature if available.

## Security requirements for implementation

- Authenticate every system, user, and connector.
- Authorize every patient, task, and action at the server boundary.
- Use verified patient and practitioner identity mappings supplied by the connected clinical system.
- Encrypt data in transit and apply appropriate encryption at rest.
- Store secrets outside source control.
- Validate webhook signatures and enforce replay protection.
- Make ingestion idempotent and protect against duplicate/out-of-order events.
- Minimize retained message content; avoid retaining full chat transcripts unless explicitly justified and governed.
- Record provenance and auditable state transitions.
- Apply rate limits, abuse controls, retention policies, and secure logging.
- Separate development, test, and production environments.
- Perform threat modelling, penetration testing, and privacy review before production use.

## Clinical safety

CIP is not a diagnostic or treatment system. It must not independently make clinical decisions or issue unreviewed treatment changes. Urgent or high-risk responses require a separately designed escalation pathway and clinically approved safety process.
