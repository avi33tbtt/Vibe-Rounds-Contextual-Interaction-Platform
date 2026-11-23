
# Contributing

Thanks for considering a contribution to Vibe Rounds CIP.

## Before contributing

- Read the README and architecture documents.
- Preserve the separation between channel adapters and clinical collection logic.
- Do not introduce real patient data into examples, tests, screenshots, issues, or pull requests.
- Do not bypass the connected EMR's identity, authorization, validation, audit, or review controls.
- Discuss changes to public contracts before implementing breaking changes.

## Contribution workflow

1. Open an issue describing the problem and proposed change.
2. Identify whether the change affects a public contract.
3. Add or update synthetic examples and tests.
4. Document security, privacy, and provenance implications.
5. Submit a focused pull request.

## Areas for early contributions

- Contract review and schema validation.
- Mock EMR adapter.
- Collection task state machine.
- Structured form renderer.
- Audit event model.
- Connector interface and mock chat adapter.
- Accessibility and localization.
- Threat modelling and security testing.

## Definition of done

A contribution should include relevant tests, documentation, synthetic examples, error handling, and migration notes where contracts change.
