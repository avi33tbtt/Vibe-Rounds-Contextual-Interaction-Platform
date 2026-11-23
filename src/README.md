
# Source implementation

The initial repository intentionally leaves runtime implementation open so the first engineering step can select a stack that fits the existing Vibe Rounds repositories.

Recommended first structure (keep it simple; do not split into microservices prematurely):

```text
src/
  domain/
    collection-task/
    collection-specification/
    interaction-session/
    audit-event/
  application/
    collection-planner/
    task-service/
    response-ingestion/
    submission-service/
  adapters/
    emr/
    channels/
    persistence/
  api/
  workers/
```

Keep source files at the repository root only if that is a deliberate project-wide convention; otherwise use these small, clear directories. Avoid creating abstractions before there is a real second implementation that needs them.
