---
Specification: RFC-0002 CEK Object Model
Version: 0.2
Status: Revised Draft
Authority: Institutional Constitution v0.1
Supersedes: RFC-0002 v0.1
Superseded-By: none
Depends-On: RFC-0001, Institutional Constitution v0.1
Last-Ratified: none
Normative: false
---

# RFC-0002: CEK Object Model

**Status**: Revised Draft  
**Type**: Design  
**Date**: 2026-07-23

## 1. Summary

This RFC proposes the canonical epistemic object types, shared attributes, and identity model for the Computational Constitution (CEK). It is deliberately narrow: it does not define operations, events, metrics, or routing.

## 2. Motivation

CEK requires a stable ontology before operations, invariants, or event vocabulary can be specified. Prior architectural discussion converged on a small set of first-class entities. This RFC formalises that convergence for acceptance.

## 3. Proposal

### 3.1 Canonical Object Types

The following seven types are the complete set of first-class epistemic objects:

| Object         | Epistemic Role |
|----------------|----------------|
| **Question**   | An unresolved inquiry that drives investigation. |
| **Evidence**   | Observed information. MUST NOT contain speculation. |
| **Claim**      | A statement asserted to be true. MAY reference Evidence. Does not explain. |
| **Hypothesis** | A proposed explanation or prediction. MUST be falsifiable. |
| **Experiment** | A procedure designed to test one or more Hypotheses. |
| **Theory**     | The current best explanatory model. Continuously subject to revision. |
| **Decision**   | A recorded choice that affects the research process or knowledge state. |

Derived constructs (Contradiction, Open Question, Rejected Idea, Research Gap, etc.) SHALL be expressed as relationships or specialised states of the seven entities, not as additional first-class types.

**Canonical Definitions** are a specialization of Claim whose purpose is to establish normative terminology for an Institution. They inherit all Claim semantics and introduce no new constitutional object type.

### 3.2 Shared Attributes

Every epistemic object SHALL carry at least the following attributes:

- **Provenance** — Origin and supporting references.
- **Confidence** — Graded assessment of reliability.
- **Status** — Object-specific (defined per type; not a global enum).
- **Timestamp** — Creation and last material modification times.
- **Relationships** — Links to other epistemic objects.

Confidence is a cross-cutting attribute, not a first-class entity.

### 3.3 Identity Model

**Identity Invariant**  
Every constitutional object possesses a stable identifier that remains unchanged for the lifetime of the object. Revisions create immutable versions of the same object rather than new object identities. Previous versions SHALL remain permanently available for replay, audit, and provenance.

Constitutional identity is distinct from implementation identity. The CEK governs only the constitutional identifier. Implementations are free to map that identifier to database rows, Git blobs, notebook cells, graph nodes, UUIDs, filesystem paths, or any other storage mechanism.

The constitutional identity MUST be preserved across Constitutional State transitions (Provisional → Institutional → Historical).

### 3.4 Evidence Content Constraint

Evidence content SHALL NOT be modified after Institutional publication. Corrections are represented through superseding Evidence objects or versioned revisions that preserve prior content. This is a concrete instance of the broader principle that Institutional objects are append-only with respect to their substantive content.

### 3.5 Explicit Non-Goals

This RFC does **not** define:

- Operations or their pre/postconditions
- Constitutional event vocabulary
- Legal transformation rules
- Invariants (except the Identity Invariant stated above)
- Metrics
- Routing, scheduling, or human-gate procedures
- Storage, serialisation, or UI representations

Those concerns belong to subsequent RFCs or subordinate specifications.

## 4. Open Questions

None remaining for this RFC. Prior open questions regarding Canonical Definition and Experiment have been resolved in this revision.

## 5. Acceptance Criteria

This RFC may be marked Accepted when:

- The seven object types and their epistemic roles are agreed.
- Canonical Definition is accepted as a Claim specialization.
- The Identity Invariant (stable identity, versioned revisions, permanent history) is agreed.
- The distinction between constitutional identity and implementation identity is agreed.
- The Evidence content constraint is agreed.
- Non-goals are confirmed.

## 6. Status

**Revised Draft**. Ready for final review pass and promotion to Accepted.
