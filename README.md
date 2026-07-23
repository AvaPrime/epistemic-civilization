# Epistemic Civilization

**Knowledge is governed; tools are replaceable.**

This repository holds the constitutional framework for an Epistemic Civilization — a set of independent institutions that share the same epistemic laws while remaining organizationally autonomous.

## Constitutional Core

| Layer | Document | Status |
|-------|----------|--------|
| Institutional legitimacy & governance | [Institutional Constitution v0.1](constitution/institutional/Institutional_Constitution_v0.1.md) | **Ratified (v0.x exploratory)** |
| Epistemic semantics | Computational Constitution (CEK) | Planned |
| Intake of external information | Epistemic Intake Specification (EIS) | Planned |
| Event processing & coordination | Research Controller (RC) | Planned |
| Long-lived research units | Research Program Specification (RPS) | Planned |

## Current Baseline

**Tag target**: `v0.1-constitutional-baseline`  
See [RELEASE_MANIFEST_v0.1.md](RELEASE_MANIFEST_v0.1.md) and [ARCHITECTURE_STATUS.md](ARCHITECTURE_STATUS.md).

## Principles

- Uncertainty is preserved until evidence justifies reduction.
- The institution exists to reduce uncertainty, not to maximize agreement.
- Observation is open; commitment is gated.
- Every material change shall be attributable, reproducible, replayable, and permanently linked to its provenance.

## Repository Layout

```
constitution/
├── institutional/     # Institutional Constitution
├── computational/     # CEK
├── intake/            # EIS
├── controller/        # RC
└── programs/          # RPS
conformance/
reference-implementations/
research-programs/
rfcs/
adrs/
docs/
```

## License & Contribution

See [REPOSITORY_GOVERNANCE.md](REPOSITORY_GOVERNANCE.md) for branch strategy, specification workflow, and review requirements.
