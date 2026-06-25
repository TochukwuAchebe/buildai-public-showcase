# Security Considerations

Status: reference security model

## Principles

- Tenant isolation is enforced on every object access.
- Provider secrets remain server-side.
- Tool execution is scoped, audited, and policy-controlled.
- High-risk actions require human approval.
- Logs redact secrets and sensitive payloads.
- Public showcases must not contain real production data.

## Controls

| Area | Control |
| --- | --- |
| Auth | OAuth/JWT with workspace roles |
| Secrets | Managed secret store, never frontend bundled |
| Tools | Allowlist, input schema validation, risk levels |
| Approvals | Approval queue for risky external side effects |
| Audit | Append-only audit events for admin/security actions |
| Model calls | Redaction before provider calls |
| Public API | Rate limits, idempotency, request IDs |

## Audit Events

- Agent created/updated/deleted
- Workflow published
- Run started/completed/failed
- Approval requested/approved/rejected
- Integration connected/disconnected
- Provider routing policy changed
- Admin policy changed
