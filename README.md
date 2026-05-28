# healthcare-workflow-auditor

> Pressure-test healthcare AI systems and clinical workflows against real-world operational, safety, compliance, and trust failures — before they reach production.

Most healthcare AI systems fail **after** the demo. Not because the model is weak. But because workflows break under pressure, clinicians don't trust the system, escalation paths are missing, and real hospital operations are far messier than any product team expects.

This skill runs a structured multi-lens audit that exposes those failures early.

---

## What it does

Given a description of a healthcare AI system or clinical workflow, the auditor stress-tests it across six independent review lenses:

| Lens | Primary Question |
|---|---|
| 🏥 Clinical Safety | How could this hurt a patient? |
| 🔄 Workflow Realism | Would real clinicians actually use this under pressure? |
| ⚖️ Compliance & Governance | Would legal and compliance teams approve this? |
| 🔧 Infrastructure & Integration | What breaks in production? |
| 🤝 Human Trust | Will humans trust this enough to actually rely on it? |
| 🏗️ Healthcare Operator | Could a hospital realistically deploy and sustain this? |

---

## Output format

```md
# Healthcare Workflow Audit: {System Name}

## Executive Summary
## Critical Risks
## Workflow Friction
## Compliance Gaps
## Trust & Adoption Risks
## Operational Weaknesses
## What Will Likely Fail First
## Recommendation
## Safest Next Step
```

Recommendation is always one of:
- ✅ Safe to pilot (with conditions)
- ⚠️ Requires redesign before deployment
- 🚫 Unsafe in current form
- 🔄 Needs narrower scope
- 👤 Human oversight insufficient

---

## Ideal use cases

Works well for:
- AI triage systems
- Clinical copilots and documentation assistants
- EHR assistants and FHIR-based integrations
- Remote patient monitoring workflows
- Healthcare automation pipelines
- Diagnostic decision support tools
- Hospital operations tooling

Not intended for general medical advice, wellness apps, or non-clinical tools.

---

## Example trigger phrases

- `audit this healthcare workflow`
- `we're building a clinical AI — stress test it`
- `would clinicians trust this?`
- `is this HIPAA compliant?`
- `run a healthcare AI audit`

---

## Design principles

**Safety before automation** — defaults toward human oversight and conservative deployment.

**Operational truth over demo quality** — a mediocre workflow that gets adopted beats an impressive system clinicians avoid.

**Explainability matters** — healthcare users must be able to understand, verify, and override AI decisions.

**Operational resilience is mandatory** — the system must survive outages, staffing shortages, incomplete data, and workflow chaos.

---

## Deployment context calibration

The audit automatically shifts lens weight based on deployment context:

| Context | Highest-priority lenses |
|---|---|
| Emergency / ICU | Safety, Workflow Realism |
| Outpatient / primary care | Trust, Operator |
| Remote patient monitoring | Infrastructure, Safety |
| Administrative / coding | Compliance, Infrastructure |
| Clinical documentation AI | Compliance, Trust |

---

## Files

| File | Description |
|---|---|
| `SKILL.md` | Full skill definition with audit workflow, six lenses, output format, and calibration tables |
| `README.md` | This file |

---

## License

MIT
