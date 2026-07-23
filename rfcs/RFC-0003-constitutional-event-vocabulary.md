---
Specification: RFC-0003 Constitutional Event Vocabulary
Version: 0.2
Status: Revised Draft
Authority: Institutional Constitution v0.1
Supersedes: RFC-0003 v0.1
Superseded-By: none
Depends-On: RFC-0001, RFC-0002, Institutional Constitution v0.1
Last-Ratified: none
Normative: false
---

# RFC-0003: Constitutional Event Vocabulary

**Status**: Revised Draft  
**Type**: Design  
**Date**: 2026-07-23

## 1. Summary

This RFC proposes the closed set of constitutional events that may appear in the institutional event log. It defines only the event vocabulary, minimal ordering requirements, and the extension mechanism. It does not define object semantics (owned by RFC-0002), legal transformation rules (RFC-0004), or invariants (RFC-0005).

## 2. Motivation

Law III (Replayable Evolution) requires that every material change be attributable, reproducible, replayable, and permanently linked to provenance. A closed constitutional event vocabulary is the minimal mechanism that makes institutional history machine-checkable and portable across implementations.

## 3. Proposal

### 3.1 Design Principles

1. The core vocabulary is closed. New core events require a superseding RFC.
2. Vendor- or implementation-specific events MAY exist but MUST be namespaced and MUST NOT alter constitutional semantics.
3. Every constitutional event MUST reference the constitutional identity of the affected object(s) and carry provenance sufficient for replay.
4. Events record that something occurred; they do not themselves perform reasoning or governance.
5. The ordered sequence of Constitutional Events SHALL be sufficient to deterministically reconstruct Constitutional State. Any event that changes Constitutional State MUST therefore include the information necessary to compute that resulting state.

### 3.2 Constitutional vs Operational Events

**Constitutional events** record changes to institutional knowledge state.  
**Operational events** record implementation or infrastructure activity (HTTP requests, webhooks, database commits, notebook synchronisations, etc.).

The CEK and the institutional event log govern only constitutional events. Operational events MAY be recorded for convenience but have no constitutional standing and MUST NOT alter the meaning or validity of core events.

### 3.3 Core Events (Closed Set)

| Event                  | Description |
|------------------------|-------------|
| `ObservationRecorded`  | Raw external information has been detected (Constitutional State: Observed). |
| `ObjectPublished`      | An epistemic object has been published into the institution (typically Provisional). |
| `ObjectPromoted`       | An object has transitioned to a higher Constitutional State (e.g., Provisional → Institutional). |
| `ObjectRevised`        | A new immutable version of an existing object has been created. |
| `ObjectArchived`       | An object has entered the Historical state. |
| `DecisionRecorded`     | A Decision object has been created or ratified. |
| `ArtifactReleased`     | A formal publication or external release has occurred under governed process. |
| `RatificationGranted`  | A recognized authority has ratified a gated transition. |
| `RatificationDenied`   | A recognized authority has denied a gated transition. |

The vocabulary is deliberately type-agnostic. Object-specific behaviour (including changes to a Theory) is expressed through ordinary `ObjectRevised` events, optionally linked to a `DecisionRecorded` event. No core event is reserved for a particular object type.

### 3.4 Extension Mechanism

Implementations and Research Programs MAY define namespaced events of the form:

```
<namespace>.<EventName>
```

Examples: `github.PullRequestMerged`, `gemini.NotebookImported`, `openclaw.SkillExecuted`.

**Non-interference rule**  
Extension events MUST NOT alter the semantics of core constitutional events. The presence or absence of any namespaced event SHALL NOT change the meaning or validity of a core event. Namespaced events carry no constitutional force unless elevated by a later RFC.

### 3.5 Ordering and Required Fields

Events that affect the same constitutional identity MUST form a total order.

Every constitutional event SHALL carry at least:

- Event type (from the closed core or a namespace)
- Timestamp (or equivalent ordering key)
- Constitutional identity of primary affected object(s)
- Provenance (actor / system / source)

In addition:

- Any event that changes Constitutional State MUST include the resulting Constitutional State.
- Any revision event (`ObjectRevised`) MUST include the prior version identity.
- Causal links that are required for legality (e.g., a ratification that authorises a promotion) SHOULD be recorded explicitly or be deterministically recoverable from the log.

Exact serialisation and choice of logical clock are implementation concerns.

### 3.6 Explicit Non-Goals

- Object type definitions (RFC-0002)
- Legal transformation rules and preconditions (RFC-0004)
- Global invariants (RFC-0005)
- Event validation rules or cryptographic signatures
- Routing, scheduling, or human-gate procedures (Research Controller)
- Storage format or transport protocol

## 4. Open Questions

1. Should `RatificationGranted` / `RatificationDenied` remain core events, or move under a governance namespace while retaining constitutional force?
2. Is a dedicated `ContradictionDetected` event warranted, or is contradiction adequately expressed as relationships among Claims/Hypotheses?
3. Should `ArtifactReleased` remain distinct, or is it adequately covered by `ObjectPromoted` + `DecisionRecorded`?

## 5. Acceptance Criteria

This RFC may be marked Accepted when:

- The closed core event set is agreed as minimal and sufficient.
- The constitutional-versus-operational distinction is agreed.
- The non-interference rule for extension events is agreed.
- Ordering requirements and mandatory fields for state-changing and revision events are agreed.
- Non-goals are confirmed.

## 6. Status

**Revised Draft**. Ready for final review pass targeting only remaining ambiguity or inconsistency.
