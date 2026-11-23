
# Contracts

The JSON Schemas in this directory are draft contracts for the initial scaffold.

Rules:
- Add a schema version and compatibility policy before public release.
- Prefer stable identifiers from the source EMR for clinical elements.
- Do not encode a particular chat vendor's message format in core contracts.
- Keep channel-specific identifiers in adapter metadata.
- Preserve source, respondent, effective time, and verification/review status.
- Add positive and negative examples and automated schema tests for every contract change.

These schemas are not a FHIR implementation guide or a finalized clinical interoperability standard.
