# India AI Governance Toolkit

A four-module tool for working with India's data protection and AI governance rules: learn the framework, assess a product against it, generate a draft privacy notice from the result, and check the sources behind every claim.

Built on the Digital Personal Data Protection Act 2023, the DPDP Rules 2025 (notified 13 November 2025), MeitY's India AI Governance Guidelines, and the IT Amendment Rules 2026.

**Live tool:** https://pauldipinadp2025.github.io/India-AI_Governance_Toolkit/

---

## Why this exists

Most DPDP explainers stop at the children's consent rule. That rule is real and strict, but it is one of nine obligation areas, and not the one carrying the largest penalty. The obligation that does — failure to implement reasonable security safeguards under Section 8(5), at up to ₹250 crore — applies to every data fiduciary regardless of who its users are.

This toolkit was built to close that gap: to move from "here is what the law says" to "here is what it means for the specific thing you are building."

## The four modules

**Learn.** The distinction between AI governance and AI safety, MeitY's seven guiding principles, the statutory timeline from the 2023 Act through to the May 2027 deadline, and the penalty schedule.

**Assess.** A structured questionnaire covering data categories collected, whether any users are minors, user scale, cross-border processing, automated decision-making, synthetic content generation, and which safeguards are already in place. Returns a scored report with a risk profile and severity-ranked findings, each citing its provision and giving one concrete next step.

**Draft.** Builds a first-pass privacy notice under Rule 3 from the same answers: itemised data categories with per-category purpose and retention, rights, consent withdrawal, and grievance escalation. Where minors are involved it adds the Section 9 prohibition on tracking and behavioural advertising. Copies to clipboard as plain text.

**Sources.** Primary legal instruments, policy guidance, and secondary commentary, tiered by authority, with a method note setting out how the engine was built and where it stops.

## Design decisions

**No backend, no API, no dependencies.** The entire tool is one HTML file. Nothing a visitor enters leaves their browser. For a privacy compliance tool this is not incidental — a tool that asks about your data handling should not itself collect data.

**The rule engine is explicitly encoded, not delegated to a model.** Obligations map to statutory provisions in readable code. Every finding shows its score deduction, so the scoring can be examined and argued with rather than taken on trust. This was a deliberate choice over an LLM-backed version: for a governance tool, auditable reasoning matters more than fluent prose.

**Unknowns are surfaced, not guessed.** Where an answer is "not sure" — most importantly on whether any users are under 18 — the tool flags it as unresolved and explains why it matters, instead of assuming a position.

**Pending law is marked as pending.** Sensitive personal data categories and cross-border transfer restrictions have not been notified. The tool says so rather than implying settled rules.

**Knowledge base held as data.** `dpdp-knowledge-base.json` carries the obligation map, penalty schedule, institutional map, timeline, and full source citations as structured data, so the reference layer can be updated as rules phase in.

## Files

| File | Purpose |
|---|---|
| `index.html` | The complete tool. Open it directly in any browser. |
| `dpdp-knowledge-base.json` | Structured reference data: obligations, penalties, institutions, timeline, sources. |
| `README.md` | This file. |

## Running it

Open `index.html` in a browser. There is no build step, no install, and no configuration.

To host it, this repository is deployed with GitHub Pages from the main branch root.

## Scope and limits

This produces a preliminary signal for triage and internal discussion. It is not legal advice and does not substitute for review by a qualified practitioner.

Full DPDP obligations phase in to 14 May 2027. Sensitive personal data categories and cross-border transfer restrictions remain pending government notification, so any assessment reflects the framework as it stood at the last knowledge-base review, recorded in `meta.lastReviewed`.

## Sources

- Digital Personal Data Protection Act, 2023
- Digital Personal Data Protection Rules, 2025 (MeitY, notified 13 November 2025)
- India AI Governance Guidelines (MeitY, November 2025)
- IT Amendment Rules on synthetically generated content (MeitY, notified 10 February 2026)
- International AI Safety Report 2026, chaired by Yoshua Bengio

Full citations with publisher and date are held in `dpdp-knowledge-base.json` under `meta.sources`, and displayed in the Sources module of the tool itself.

## Note on classification

This is an **AI governance and policy** project: it concerns regulation, accountability, and compliance frameworks. It is not an AI safety project in the technical sense — it involves no model evaluation, alignment work, or red-teaming.
