---
applyTo: "terraform/**,k8s/**,helm/**,.github/workflows/**,Dockerfile*,deploy/**"
---

# AI-DLC Operations Phase Instructions

When working on deployment, infrastructure, or monitoring:

- Follow the operations workflow in aidlc-docs/operations/
- Use infrastructure-as-code for all resources
- Include observability (metrics, logs, traces) in every deployment change
- Document runbooks in aidlc-docs/operations/runbooks/
- Validate production readiness against the AI-DLC checklist
