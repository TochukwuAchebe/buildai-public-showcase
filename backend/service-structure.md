# Example Backend Service Structure

```text
src/
  app.ts
  modules/
    auth/
      auth.middleware.ts
      roles.ts
    workspaces/
      workspace.controller.ts
      workspace.service.ts
    agents/
      agent.controller.ts
      agent.service.ts
      agent.repository.ts
    workflows/
      workflow.controller.ts
      workflow.service.ts
    runs/
      run.controller.ts
      run.service.ts
      run-state-machine.ts
    approvals/
      approval.controller.ts
      approval.service.ts
    memory/
      memory.controller.ts
      memory.service.ts
    providers/
      provider-router.ts
      provider-policy.ts
    audit/
      audit.service.ts
    analytics/
      analytics.service.ts
  shared/
    errors.ts
    idempotency.ts
    redaction.ts
    request-context.ts
```

## Notes

- Controllers expose API resources.
- Services own product behavior.
- Repositories isolate persistence.
- Provider router normalizes model/provider calls.
- Redaction runs before logs and provider calls.
- Audit service records security-relevant events.
