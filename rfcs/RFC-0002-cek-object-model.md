---
Specification: RFC-0002 CEK Object Model
Version: 0.1
Status: Draft
Authority: Institutional Constitution v0.1
Supersedes: none
Superseded-By: none
Depends-On: RFC-0001, Institutional Constitution v0.1
Last-Ratified: none
Normative: false
---

# RFC-0002: CEK Object Model

**Status**: Draft  
**Type**: Design  
**Date**: 2026-07-23

## 1. Summary

This RFC proposes the canonical epistemic object types, shared attributes, and identity model for the Computational Constitution (CEK). It is deliberately narrow: it does not define operations, events, metrics, or routing.

## 2. Motivation

CEK requires a stable ontology before operations, invariants, or event vocabulary can be specified. Prior architectural discussion converged on a small set of first-class entities. This RFC formalises that convergence for acceptance.

## 3. Proposal

### 3.1 Canonical Object Types

The following seven types are proposed as the complete set of first-class epistemic objects:

| Object       | Epistemic Role |
|--------------|----------------|
| **Question** | An unresolved inquiry that drives investigation. |
| **Evidence** | Observed information. MUST NOT contain speculation. |
| **Claim**    | A statement asserted to be true. MAY reference Evidence. Does not explain. |
| **Hypothesis** | A proposed explanation or prediction. MUST be falsifiable. |
| **Experiment** | A procedure designed to test one or more Hypotheses. |
| **Theory**   | The current best explanatory model. Continuously subject to revision. |
| **Decision** | A recorded choice that affects the research process or knowledge state. |

Derived constructs (Contradiction, Invariant, Canonical Definition, Open Question, Rejected Idea, Research Gap, etc.) SHALL be expressed as relationships or specialised states of the seven entities, not as additional first-class types.

### 3.2 Shared Attributes

Every epistemic object SHALL carry at least the following attributes:

- **Provenance** — Origin and supporting references.
- **Confidence** — Graded assessment of reliability.
- **Status** — Object-specific (defined per type; not a global enum).
- **Timestamp** — Creation and last material modification times.
- **Relationships** — Links to other epistemic objects.

Confidence is a cross-cutting attribute, not a first-class entity.

### 3.3 Identity Model

Each epistemic object SHALL have a stable, unique identifier within the adopting Institution. Identifiers are opaque to the CEK; generation and storage are implementation concerns. The identity MUST be preserved across Constitutional State transitions (Provisional → Institutional → Historical).

### 3.4 Explicit Non-Goals

This RFC does **not** define:

- Operations or their pre/postconditions
- Constitutional event vocabulary
- Legal transformation rules
- Invariants
- Metrics
- Routing, scheduling, or human-gate procedures
- Storage, serialisation, or UI representations

Those concerns belong to subsequent RFCs or subordinate specifications.

## 4. Open Questions

1. Should “Canonical Definition” remain a specialised Claim, or does it warrant distinct treatment in a later revision?
2. Is the seven-type set minimal and sufficient, or should Experiment be derived rather than first-class?

## 5. Acceptance Criteria

This RFC may be marked Accepted when:

- The seven object types and their epistemic roles are agreed.
- Shared attributes and the identity model are agreed.
- Non-goals are confirmed.

## 6. Status

**Draft**. Discussion and refinement are open.
