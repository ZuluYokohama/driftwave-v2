---
name: driftwave
description: Full Driftwave v2.1 MaxOp semantic dimensionalizer with explicit (State, Activity) ontology, semantic shape diffing, isomorphic encoding (language ↔ code), and mandatory round-trip verification.
version: 2.1-maxop-isomorphic
triggers: ["/driftwave", "driftwave", "dimensionalize", "maxop", "verify-roundtrip"]
---

# Driftwave v2.1 MaxOp – Isomorphic & Self-Verifying

**Core Ontology Principle**
Every operation consists of explicit, labeled (State, Activity) pairs. Language and code are isomorphic encodings of the same underlying operations. The Target Semantic Shape is the single source of truth. All conversions are subject to mandatory round-trip verification to eliminate black-box behavior.

## Execution Flow (Operational)

1. **Qualify** – Lock in exact value and success criteria
2. **Capture State** – Full snapshot of current system
3. **Dimensionalize** – Build Target Semantic Shape
4. **Compute Diff** – Semantic shape diff between current and target
5. **Generate Work Order** – Ordered (State → Activity → New State) transitions
6. **Execute + Verify** – Run with sub-agents, round-trip verification, and recursion on failure
7. **Final Alignment** – Only return output when diff is within tolerance

## Round-Trip Verifier (Mandatory)

```yaml
round_trip_verifier:
  version: 2.1
  tolerance: 0.95
  execution:
    - RT-01: Convert input → Neutral Semantic Shape
    - RT-02: Neutral → Original encoding
    - RT-03: Compute structural + semantic drift score
    - RT-04: If drift_score < 0.95 → recurse on failing (State, Activity) pairs
  invocation: "Automatic after every conversion and before final deliverables"
```

**Usage**: `/driftwave <your request>`
The skill automatically runs the full ontology with round-trip verification and self-correction.

This implementation enforces discrete, auditable state-activity transitions across all encodings.