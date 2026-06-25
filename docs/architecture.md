# Architecture

Status: reference architecture

## System Context

```mermaid
flowchart TB
  Web["Frontend app"] --> API["Platform API"]
  API --> Auth["Auth and workspace service"]
  API --> AgentSvc["Agent service"]
  API --> WorkflowSvc["Workflow service"]
  API --> MemorySvc["Memory Hub service"]
  API --> RunSvc["Run service"]
  RunSvc --> Queue["Queue"]
  Queue --> Runtime["Agent runtime"]
  Runtime --> Router["Model router"]
  Router --> OpenAI["Provider A"]
  Router --> Anthropic["Provider B"]
  Router --> Local["Private / local model"]
  Runtime --> ToolGateway["Tool gateway"]
  ToolGateway --> Integrations["Approved integrations"]
  API --> Audit["Audit log"]
  API --> Analytics["Analytics store"]
```

## Service Boundaries

| Service | Responsibility |
| --- | --- |
| Platform API | Public API surface, auth checks, workspace context, orchestration |
| Agent service | Agent metadata, instructions, tools, status |
| Workflow service | Templates, parameters, schedules, lifecycle |
| Memory Hub | Durable context, knowledge references, access rules |
| Run service | Run state machine, logs, retries, approvals |
| Agent runtime | Provider calls, tool calls, context assembly |
| Tool gateway | Tool authorization, input validation, execution logging |
| Admin/back office | Policy, usage, billing, account controls |

## Run State Machine

```mermaid
stateDiagram-v2
  [*] --> queued
  queued --> running
  running --> awaiting_approval
  awaiting_approval --> running: approved
  awaiting_approval --> cancelled: rejected
  running --> succeeded
  running --> failed
  failed --> retrying
  retrying --> running
```

## Design Tradeoffs

- Async run execution improves resilience but requires richer UX states.
- Multi-provider routing improves resilience and cost control but requires normalized observability.
- Memory improves agent usefulness but requires tenant-scoped governance and auditability.
- Human approvals reduce risk but can slow automation.
