---
Specification: RFC-0003 Constitutional Event Vocabulary
Version: 0.1
Status: Draft
Authority: Institutional Constitution v0.1
Supersedes: none
Superseded-By: none
Depends-On: RFC-0001, RFC-0002, Institutional Constitution v0.1
Last-Ratified: none
Normative: false
---

# RFC-0003: Constitutional Event Vocabulary

**Status**: Draft  
**Type**: Design  
**Date**: 2026-07-23

## 1. Summary

This RFC proposes the closed set of constitutional events that may appear in the institutional event log. It defines only the event vocabulary and its extension mechanism. It does not define object semantics (owned by RFC-0002), operations (RFC-0004), or invariants (RFC-0005).

## 2. Motivation

Law III (Replayable Evolution) requires that every material change be attributable, reproducible, replayable, and permanently linked to provenance. A closed constitutional event vocabulary is the minimal mechanism that makes institutional history machine-checkable and portable across implementations.

## 3. Proposal

### 3.1 Design Principles

1. The core vocabulary is closed. New core events require a superseding RFC.
2. Vendor- or implementation-specific events MAY exist but MUST be namespaced and MUST NOT alter constitutional semantics.
3. Every constitutional event MUST reference the constitutional identity of the affected object(s) and carry provenance sufficient for replay.
4. Events record that something occurred; they do not themselves perform reasoning or governance.

### 3.2 Proposed Core Events (Closed Set)

| Event                      | Description |
|----------------------------|-------------|
| `ObservationRecorded`      | Raw external information has been detected (Constitutional State: Observed). |
| `ObjectPublished`          | An epistemic object has been published into the institution (typically Provisional). |
| `ObjectPromoted`           | An object has transitioned to a higher Constitutional State (e.g., Provisional → Institutional). |
| `ObjectRevised`            | A new immutable version of an existing object has been created. |
| `ObjectArchived`           | An object has entered the Historical state. |
| `DecisionRecorded`         | A Decision object has been created or ratified. |
| `TheoryUpdated`            | A Theory has been revised or replaced under governed process. |
| `ArtifactReleased`         | A formal publication or external release has occurred. |
| `RatificationGranted`      | A recognized authority has ratified a gated transition. |
| `RatificationDenied`       | A recognized authority has denied a gated transition. |

This list is intentionally minimal. Additional granularity belongs either in object-specific attributes or in namespaced extension events.

### 3.3 Extension Mechanism

Implementations and Research Programs MAY define namespaced events of the form:

```
<namespace>.<EventName>
```

Examples:

- `github.PullRequestMerged`
- `gemini.NotebookImported`
- `openclaw.SkillExecuted`

Namespaced events MUST NOT be treated as constitutional core events. They MAY be recorded in the same event log for operational convenience but carry no constitutional force unless a later RFC elevates them.

### 3.4 Required Event Fields

Every constitutional event SHALL carry at least:

- Event type (from the closed core or a namespace)
- Timestamp
- Constitutional identity of primary affected object(s)
- Provenance (actor / system / source)
- Optional: prior version identity, resulting Constitutional State, linked Decision

Exact serialisation is an implementation concern.

### 3.5 Explicit Non-Goals

- Object type definitions (RFC-0002)
- Operation pre/postconditions (RFC-0004)
- Global invariants (RFC-0005)
- Routing, scheduling, or human-gate procedures (Research Controller)
- Storage format or transport protocol

## 4. Open Questions

1. Is `TheoryUpdated` distinct enough from `ObjectRevised`, or should Theory changes be ordinary revisions plus a Decision?
2. Should `RatificationGranted` / `RatificationDenied` be core events or namespaced under a governance namespace?
3. Is a dedicated `ContradictionDetected` event warranted, or is contradiction adequately expressed as relationships among Claims/Hypotheses?

## 5. Acceptance Criteria

This RFC may be marked Accepted when:

- The closed core event set is agreed as minimal and sufficient.
- The extension (namespacing) mechanism is agreed.
- Required event fields are agreed.
- Non-goals are confirmed.

## 6. Status

**Draft**. Discussion and refinement are open.
