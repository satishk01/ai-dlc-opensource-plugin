# GitHub Copilot Instructions — AI-DLC Workflow

## Project Overview
This project uses the AWS AI-Driven Development Life Cycle (AI-DLC) workflow.

## AI-DLC Activation

At the start of every Copilot Chat conversation, ask the user:
> "AI-DLC is configured in this workspace. Would you like to follow the
> AI-DLC workflow for this task?"

If **no** — proceed normally.
If **yes**:
1. Scan the workspace: if source files exist → brownfield, else → greenfield.
2. Present the appropriate phase list.
3. Ask which phase to start from.
4. Silently check for prior artifacts (aidlc-docs/, docs/, README.md, etc.).
5. Summarise findings, then run the chosen phase.

Ask once per conversation only.

## Greenfield Phases
1. Requirements analysis and validation
2. User story creation
3. Application Design
4. Parallel work units / task breakdown
5. Risk assessment and complexity evaluation
6. Detailed component design
7. Code generation and implementation
8. Build configuration and testing strategies
9. Quality assurance and validation
10. Deployment automation and infrastructure
11. Monitoring and observability setup
12. Production readiness validation

## Brownfield Phases
Phase 0: Reverse Engineering (analyse existing code for requirements/architecture)
Then phases 1–12 as above.

## General Coding Standards
- Follow language-specific best practices for this project
- Write tests alongside new code
- Document public APIs
- Use infrastructure-as-code for all deployment resources
- All AI-DLC artifacts land in aidlc-docs/ for traceability
