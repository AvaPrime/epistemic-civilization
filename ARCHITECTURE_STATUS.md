# Architecture Status

**Last updated**: 2026-07-23  
**Baseline tag**: `v0.1-constitutional-baseline` (pending)

This file is the single source of truth for the current constitutional and specification state of the Epistemic Civilization framework.

---

## Constitutional Core

| Specification                        | Version | Status                          | Notes |
|--------------------------------------|---------|---------------------------------|-------|
| Institutional Constitution           | v0.1    | **Ratified (v0.x exploratory)** | Frozen. Amendments require concrete ambiguity, inconsistency, or governance failure. |
| Computational Constitution (CEK)     | —       | Planned                         | Awaits Accepted RFCs (0002–0005). |
| Epistemic Intake Specification (EIS) | —       | Planned                         | Depends on CEK. |
| Research Controller (RC)             | —       | Planned                         | Depends on CEK + EIS. |
| Research Program Specification (RPS) | —       | Planned                         | Depends on Constitution. |

---

## Active RFCs

| RFC      | Title                                      | Status              |
|----------|--------------------------------------------|---------------------|
| RFC-0001 | Institutional Constitution Ratification    | **Accepted**        |
| RFC-0002 | CEK Object Model                           | **Accepted**        |
| RFC-0003 | Constitutional Event Vocabulary            | **Draft**           |
| RFC-0004 | Legal Transformation Rules                 | Planned             |
| RFC-0005 | Invariant Catalogue                        | Planned             |

---

## Maturity Ladder (Institutional Constitution)

| Stage              | Meaning                                                                 | Status |
|--------------------|-------------------------------------------------------------------------|--------|
| Frozen Draft       | Text complete; amendments controlled                                    | Passed |
| **Ratified v0.1**  | Approved for implementation and conformance testing                       | **Current** |
| Validated v0.9     | Successfully exercised through CEK + EIS + RC + ≥1 Research Program     | Pending |
| Ratified v1.0      | Proven stable through operational use                                   | Future |

---

## Active Research Programs

| Program                      | Status   | Charter |
|------------------------------|----------|--------|
| Computational Epistemology   | Planned  | Will own production of CEK, EIS, RC, RPS, conformance suite, and related artifacts. |

---

## Governance Rules in Force

- Changes to the Institutional Constitution require identification of a concrete ambiguity, inconsistency, or governance failure. New ideas alone are not sufficient grounds for amendment.
- Subordinate specifications MAY evolve under their own versioning rules provided they remain consistent with the Institutional Constitution.
- Knowledge is governed; tools are replaceable.
- Architectural exploration occurs in RFCs; normative specifications incorporate only Accepted decisions.
- **Accepted RFCs are append-only.** Substantive changes require a superseding RFC.

---

## Next Actions

1. Review and accept (or refine) RFC-0003 Constitutional Event Vocabulary.
2. Draft RFC-0004 (Legal Transformation Rules) and RFC-0005 (Invariant Catalogue).
3. Once RFCs 0002–0005 are Accepted, generate CEK v0.1 skeleton and populate from Accepted RFCs only.
4. Proceed to EIS → RC → RPS.
