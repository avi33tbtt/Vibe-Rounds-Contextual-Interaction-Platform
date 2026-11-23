
# Demonstration scenarios

All examples and demonstrations must use synthetic data.

## Scenario A — Pathway-triggered patient collection

1. A mock EMR pathway indicates that home blood pressure and medication adherence are required.
2. CIP receives the requirement and an authorization-scoped context summary.
3. The planner finds that the latest home blood pressure is stale and adherence is missing.
4. CIP creates a collection task for the patient.
5. The patient receives a web form or chat interaction.
6. The patient reports readings and adherence.
7. CIP validates structure, units, effective time, and required fields.
8. CIP submits proposed observations to the mock EMR.
9. The mock EMR accepts one value and routes another for clinician review.
10. CIP records the result and updates task status.

## Scenario B — Clinician-initiated collection

1. A clinician opens a synthetic patient encounter.
2. The clinician selects contextual elements to collect.
3. CIP creates a task and records the initiating clinician.
4. The patient responds through an available channel.
5. The clinician reviews the response in the EMR workflow.

## Scenario C — Patient-initiated update

1. An authenticated patient opens the patient interface.
2. The patient selects an authorized information category.
3. CIP checks which updates are permitted and whether a task is needed.
4. The patient submits information.
5. CIP records provenance and sends a proposal to the EMR.

## Scenario D — AI-assisted collection

1. An authorized AI agent requests the outstanding collection requirements for a patient.
2. CIP returns only the requirements the agent is authorized to see.
3. The agent proposes a task using an approved collection specification.
4. CIP checks permissions and creates or rejects the task.
5. The agent asks the approved questions.
6. Responses are submitted as patient-reported data.
7. CIP validates and submits them to the EMR.

## Scenario E — Chat connector failure

1. CIP attempts delivery through a connector.
2. The provider times out.
3. CIP records the delivery failure and schedules a bounded retry.
4. Duplicate provider callbacks are safely deduplicated.
5. After the retry policy is exhausted, the task remains visible for an alternative channel or staff follow-up.
