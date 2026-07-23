# Repository Governance

This document defines how the `epistemic-civilization` repository itself is governed. It is subordinate to the Institutional Constitution.

## Branch Strategy

- `main` is the protected, always-releasable branch.
- Feature and specification work occurs on short-lived branches (`spec/cek-v0.1`, `docs/...`, etc.).
- Direct commits to `main` are reserved for constitutional baseline releases and urgent governance fixes.

## Specification Workflow

1. Ideas begin as GitHub Issues or RFCs (`/rfcs`).
2. Normative specifications are drafted on feature branches.
3. Specifications are reviewed against the Institutional Constitution for consistency.
4. Upon acceptance they are merged to `main` and the `specification_index.md` and `ARCHITECTURE_STATUS.md` are updated in the same commit series.
5. Releases that change constitutional or core specification status receive annotated tags.

## RFC Lifecycle and Append-Only Rule

RFC stages: Draft → Review → Accepted | Rejected | Deferred | Superseded.

**Accepted RFCs are append-only.**  
If an Accepted RFC requires a substantive change, do not edit it in place. Instead:

- publish a new RFC that amends or supersedes it, or
- apply only clearly identified editorial (non-semantic) corrections.

This preserves auditability and replayability of architectural decisions.

## ADR Requirement

Significant architectural or governance decisions MUST be recorded as Architecture Decision Records in `/adrs`.

## Issue Taxonomy (recommended labels)

- `constitution`
- `cek`
- `intake` / `eis`
- `controller` / `rc`
- `program` / `rps`
- `conformance`
- `implementation`
- `governance`
- `adr`
- `rfc`
- `blocked`
- `discussion`

## Review Requirements

- Changes to the Institutional Constitution require explicit recognition of a concrete ambiguity, inconsistency, or governance failure (per Constitution §6).
- Changes to subordinate specifications SHOULD be reviewed for consistency with higher layers before merge.

## Release Policy

Constitutional baselines and major specification freezes are tagged. The tag `v0.1-constitutional-baseline` marks the first such release.
