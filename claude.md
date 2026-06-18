# CLAUDE.md — Project Instructions for Claude Code

## AI-DLC Workflow

AI-DLC (AI-Driven Development Life Cycle) is active in this workspace.

At the start of every task, ask:

> "I see AI-DLC is set up in this workspace. Would you like to use the AI-DLC workflow for this task? (yes / no)"

If the user says **no** — proceed normally.

If the user says **yes**:

1. Silently scan the workspace to determine if it is **greenfield** (no source/build files yet) or **brownfield** (existing code found).
2. Present the appropriate phase list (see below).
3. Ask the user which phase to start from.
4. Before running the chosen phase, silently scan for prior artifacts in:
   `aidlc-docs/`, `README.md`, `ARCHITECTURE.md`, `docs/`, `.github/workflows/`,
   `terraform/`, `k8s/`, `src/`, `tests/`, `runbooks/`
5. Briefly summarise what artifacts were found, then execute the phase.

Ask **once per conversation**. Remember the user's choice for the rest of the session.

---

### Greenfield Phases (no existing code)

1. Requirements analysis and validation
2. User story creation
3. Application Design
4. Creating units of work for parallel development
5. Risk assessment and complexity evaluation
6. Detailed component design
7. Code generation and implementation
8. Build configuration and testing strategies
9. Quality assurance and validation
10. Deployment automation and infrastructure
11. Monitoring and observability setup
12. Production readiness validation

---

### Brownfield Phases (existing code found — add Reverse Engineering first)

0. Reverse Engineering — analyse existing codebase to reconstruct requirements, architecture, and design decisions
1. Requirements analysis and validation
2. User story creation
3. Application Design
4. Creating units of work for parallel development
5. Risk assessment and complexity evaluation
6. Detailed component design
7. Code generation and implementation
8. Build configuration and testing strategies
9. Quality assurance and validation
10. Deployment automation and infrastructure
11. Monitoring and observability setup
12. Production readiness validation

---

## Detailed Rule References

@.claude/aidlc/core-workflow.md
@.claude/aidlc/inception/workspace-detection.md
@.claude/aidlc/inception/reverse-engineering.md

<!-- Tip: Add construction and operations imports selectively once you reach those phases
     to avoid overloading context early in inception.

     Example — add these when entering construction phases:
     @.claude/aidlc/construction/
     @.claude/aidlc/common/

     Example — add these when entering operations phases:
     @.claude/aidlc/operations/
-->

---

## General Coding Standards

- Follow language-specific best practices for this project
- Write tests alongside new code
- Document public APIs
- Use infrastructure-as-code for all deployment resources
- Reference `aidlc-docs/` for design decisions and architectural context
- Update `aidlc-docs/` with any deviations from the original design

---

## Artifact Locations

| Phase | Output Directory |
|---|---|
| Inception (requirements, stories, architecture) | `aidlc-docs/inception/` |
| Construction (component design, decisions) | `aidlc-docs/construction/` |
| Operations (runbooks, readiness checklists) | `aidlc-docs/operations/` |
| Source code | `src/` |
| Tests | `tests/` |
| Infrastructure | `terraform/` or `k8s/` |

---

## Directory Structure Expected

```
<project-root>/
├── CLAUDE.md                        ← this file
└── .claude/
    └── aidlc/
        ├── core-workflow.md         ← copied from .kiro/steering/aws-aidlc-rules/
        ├── common/                  ← copied from .kiro/aws-aidlc-rule-details/common/
        ├── inception/               ← copied from .kiro/aws-aidlc-rule-details/inception/
        │   ├── workspace-detection.md
        │   └── reverse-engineering.md
        ├── construction/            ← copied from .kiro/aws-aidlc-rule-details/construction/
        ├── extensions/              ← copied from .kiro/aws-aidlc-rule-details/extensions/
        └── operations/              ← copied from .kiro/aws-aidlc-rule-details/operations/
```

### Setup Commands (run once after cloning aws-samples/sample-power-aidlc-all)

```bash
# 1. Run the upstream setup script to pull down all rule files
bash ../sample-power-aidlc-all/aidlc_power/scripts/setup-aidlc.sh "$(pwd)"

# 2. Create the Claude-specific directory
mkdir -p .claude/aidlc

# 3. Copy rule files into place
cp .kiro/steering/aws-aidlc-rules/core-workflow.md .claude/aidlc/
cp -R .kiro/aws-aidlc-rule-details/common       .claude/aidlc/
cp -R .kiro/aws-aidlc-rule-details/inception    .claude/aidlc/
cp -R .kiro/aws-aidlc-rule-details/construction .claude/aidlc/
cp -R .kiro/aws-aidlc-rule-details/extensions   .claude/aidlc/
cp -R .kiro/aws-aidlc-rule-details/operations   .claude/aidlc/
```

---

## Version Control

Commit these files — they are the AI-DLC instructions for Claude Code:

```gitignore
# .gitignore — always keep these tracked
CLAUDE.md
.claude/aidlc/
aidlc-docs/
```
