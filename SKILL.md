---
name: healthcare-workflow-auditor
description: >
  Pressure-test healthcare AI systems, clinical workflows, and health-tech products against
  real-world operational, safety, compliance, and trust failures — before they reach production.

  Use this skill whenever someone is building, designing, evaluating, or pitching a healthcare
  AI tool, clinical workflow, or health-tech product. Trigger on: "we're building a clinical AI",
  "does this work in hospitals", "would clinicians trust this", "is this HIPAA compliant",
  "safe for patients", "AI triage system", "EHR integration", "clinical copilot", "remote patient
  monitoring", "healthcare automation", "medical decision support", "HL7/FHIR workflow",
  "hospital AI deployment", or any request to audit/review/stress-test a healthcare system.

  Do NOT use for general medical advice, wellness apps, fitness trackers, or non-clinical tools.
---

# Healthcare Workflow Auditor

Most healthcare AI systems fail **after** the demo — not because the model is weak, but because:

- Workflows break under real clinical pressure
- Clinicians don't trust the system
- Escalation paths are missing or unclear
- Compliance was an afterthought
- Integrations are fragile
- Real hospital operations are messier than any product team expects

This skill runs a structured multi-lens audit that exposes those failures **before** they reach production.

---

## Core Principle

A clinically mediocre workflow that gets adopted beats an impressive system clinicians ignore.

This audit prioritizes **operational truth over demo quality**. It assumes:

- Edge cases always matter
- Safety > elegance
- Trust > novelty
- Healthcare workflows are socio-technical systems — not just software

---

## When You Don't Have Enough Context

If the workflow description is vague, ask **one** focused question before proceeding:

> "What's the primary decision the AI is making or supporting, and who acts on that decision?"

This single answer unlocks most of the audit. Don't ask for a full spec.

---

## Audit Workflow

### Step 1 — Risk Mapping

Before running the six lenses, map:

| Dimension | Key Questions |
|---|---|
| **Decision boundaries** | What decisions does the AI make vs. support vs. inform? |
| **Patient impact zone** | What's the worst-case outcome if the AI is wrong? |
| **Escalation path** | Who gets notified when the AI is uncertain or wrong? |
| **Human oversight** | At what points does a human verify or override? |
| **Integration surface** | What systems does this touch? (EHR, HL7, FHIR, custom?) |
| **Deployment context** | ICU? Outpatient? Remote monitoring? Emergency? |

---

### Step 2 — Six-Lens Audit

Run all six lenses independently. Each lens challenges assumptions from a different perspective.

---

#### Lens 1 · Clinical Safety Reviewer

**Primary question:** *How could this hurt a patient?*

Examines:
- False negative / false positive patient impact
- Hallucination risk and auto-escalation failures
- What happens when confidence scores are wrong or missing
- Silent failure modes (system wrong without anyone knowing)
- Edge cases: pediatric, geriatric, rare conditions, comorbidities
- Whether the AI can be overridden — and whether that override is logged

**Red flags:** Any autonomous clinical decision without a human in the loop. Any alert suppression logic.

---

#### Lens 2 · Workflow Realism Reviewer

**Primary question:** *Would real clinicians actually use this under pressure?*

Examines:
- Does this fit within existing nurse/physician workflows or demand a workflow change?
- Alert fatigue: how many new notifications does this introduce?
- Cognitive load: is the AI adding to or reducing decision burden?
- Time pressure: does this slow down triage/treatment at peak load?
- What happens when staff skip or bypass the system?

**Red flags:** Additional screens during high-acuity care. Workflows that assume clinicians will wait for AI output.

---

#### Lens 3 · Compliance & Governance Reviewer

**Primary question:** *Would legal and compliance teams approve this?*

Examines:
- PHI handling and HIPAA exposure (US) / GDPR (EU)
- Audit logging: is every AI-assisted decision traceable?
- Human override tracking: are overrides logged with reason?
- AI Act (EU) classification: is this a high-risk AI system?
- Consent flows: do patients know AI is involved in their care?
- Data retention and right-to-deletion conflicts

**Red flags:** No audit trail. No override logging. No documented accountability chain.

---

#### Lens 4 · Infrastructure & Integration Reviewer

**Primary question:** *What breaks in production?*

Examines:
- EHR integration strategy: FHIR R4? HL7 v2? Custom API?
- Sync reliability: what happens if the EHR and AI are out of sync?
- Latency under peak hospital load
- Downtime: what's the fallback if the AI is unavailable?
- Vendor lock-in risk
- Data quality: what if incoming data is incomplete or malformed?

**Red flags:** No fallback procedure. Synchronous EHR calls in time-critical paths. Single-vendor dependency.

---

#### Lens 5 · Human Trust Reviewer

**Primary question:** *Will humans trust this enough to actually rely on it?*

Examines:
- Explainability: can clinicians understand *why* the AI made a recommendation?
- Is override capability prominent and easy to use?
- Does the UI create anxiety about liability?
- Psychological resistance: automation bias vs. skepticism — which is more dangerous here?
- Onboarding: how long until a new clinician trusts this system?

**Red flags:** Black-box recommendations in high-stakes contexts. Override buried in UI. No confidence indicator.

---

#### Lens 6 · Healthcare Operator Reviewer

**Primary question:** *Could a hospital realistically deploy and sustain this?*

Examines:
- Procurement: who signs off? IT, clinical leadership, legal, compliance?
- Training burden: how long to onboard nursing staff vs. physicians?
- Rollout strategy: big bang or phased? Pilot ward first?
- Organizational friction: whose workflow gets disrupted? Who has veto power?
- Maintenance: who owns the model? How are updates validated clinically?
- ROI: what does success look like 6 months post-deployment?

**Red flags:** No clinical champion identified. No rollback plan. No validation protocol for model updates.

---

### Step 3 — Consolidated Output

```md
# Healthcare Workflow Audit: {System Name}

## Executive Summary
One paragraph. What is this system, and what is the single biggest risk?

## Critical Risks
- {Patient safety failures, legal exposure, operational breakdowns}

## Workflow Friction
- {Where clinicians will resist, slow down, or bypass}

## Compliance Gaps
- {Missing logging, governance, consent, audit trails}

## Trust & Adoption Risks
- {Why humans may ignore, distrust, or misuse the system}

## Operational Weaknesses
- {Deployment, integration, staffing, downtime risks}

## What Will Likely Fail First
- {Single most probable failure mode in the first 90 days}

## Recommendation
One of:
- ✅ Safe to pilot (with conditions)
- ⚠️ Requires redesign before deployment
- 🚫 Unsafe in current form
- 🔄 Needs narrower scope
- 👤 Human oversight insufficient

## Safest Next Step
One concrete action to reduce the highest-priority risk.
```

---

## Audit Calibration by Deployment Context

The weight of each lens shifts depending on where the system is deployed:

| Context | Highest-Priority Lenses |
|---|---|
| Emergency / ICU | Safety, Workflow Realism |
| Outpatient / primary care | Trust, Operator |
| Remote patient monitoring | Infrastructure, Safety |
| Administrative / coding | Compliance, Infrastructure |
| Clinical documentation AI | Compliance, Trust |

---

## Useful Escalation Triggers

These signal you need to escalate the audit to "critical review" mode:

- The AI makes or blocks any clinical decision autonomously
- No documented fallback when the system is unavailable
- PHI flows to third-party vendors without explicit DPA
- Confidence scores are not surfaced to clinicians
- Override actions are not logged
- No clinical validation study planned before rollout

---

## Future Modules (not yet implemented)

- AI Act risk classification scoring
- FHIR architecture review mode
- Adversarial patient scenario simulation
- Multi-hospital deployment diff analysis
- Clinical cognitive load quantification
