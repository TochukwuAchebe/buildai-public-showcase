# Product Requirements Document: BuildAI Showcase

Status: public sanitized showcase

## Summary

BuildAI is a governed AI agent platform that helps users create, run, monitor, and govern AI agents and workflows across workspaces.

## Target Users

| User | Need |
| --- | --- |
| Individual operator | Automate repeatable knowledge work |
| Team lead | Coordinate AI workflows with approvals and auditability |
| Agency | Manage client workspaces and reusable templates |
| Enterprise admin | Enforce roles, usage controls, and security policies |
| Partner developer | Connect agents to approved APIs and tools |

## Goals

- Make AI workflows repeatable, observable, and governable.
- Support multiple user types without collapsing into a generic chatbot.
- Provide model provider routing without exposing provider secrets.
- Add human approval for high-risk actions.
- Create product metrics for adoption, cost, quality, and reliability.

## Non-Goals

- Expose production source code.
- Store real provider credentials in frontend code.
- Claim this public repo is a live production system.

## Core Requirements

- Workspace-based tenancy.
- Agent templates and agent configuration.
- Workflow templates and run execution.
- Memory Hub references and context management.
- Run logs, audit trails, and status transitions.
- Approval queue for high-risk tools.
- Provider routing policy.
- Admin/back-office policy controls.
- Analytics dashboard.

## Success Metrics

- Time to first configured agent.
- Time to first successful workflow run.
- Workflow completion rate.
- Human approval response time.
- Cost per run.
- Provider error rate.
- Workspace retention.
