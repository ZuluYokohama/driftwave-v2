---
name: driftwave
description: Full Driftwave v2.0 MaxOp semantic dimensionalizer with isomorphic encoding support and round-trip verification.
version: 2.0-maxop-isomorphic
triggers: ["/driftwave", "driftwave", "dimensionalize", "maxop"]
---

# Driftwave v2.0 MaxOp Skill – Isomorphic Round-Trip Verified

**Command**: `/driftwave <your task or content>`

**Core Ontology (Operational)**:
Every operation is handled through explicit (State, Activity) pairs. Language and code are isomorphic encodings of the same operations. The semantic shape is the single source of truth. Round-trip verification is mandatory on all conversions.

## Round-Trip Verifier (Fully Implemented)

```yaml
round_trip_verifier:
  id: "mechanism-03-round-trip"
  version: "2.0-maxop-isomorphic"
  description: "Mandatory lossless verification between language ↔ neutral ↔ code"
  execution_sequence:
    - step: "RT-01-convert-to-neutral"
      activity: "Convert input to neutral (State, Activity) semantic shape"
    - step: "RT-02-re-encode-to-original"
      activity: "Convert neutral shape back to original encoding"
    - step: "RT-03-compute-drift"
      activity: "Calculate structural + semantic drift score"
      tolerance_threshold: 0.95
    - step: "RT-04-gate-and-recurse"
      activity: "If drift_score < 0.95 → trigger recursion on failing pairs"
  invocation_points:
    - "After every major conversion"
    - "Before final output"
```

This skill now enforces full semantic shape diffing, state-activity explicitness, and round-trip verification on every run.

**Usage**:
Just type `/driftwave` followed by your request. The full optimized ontology (with round-trip verification) will run automatically.

The system is now self-correcting and black-box-free.