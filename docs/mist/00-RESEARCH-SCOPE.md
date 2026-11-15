# 00 — Research Scope

**Status:** ACCEPTED AS RESEARCH REFERENCE  
**Production use:** NOT ACCEPTED  
**Specification:** NOT FROZEN

## Objective
Extract reusable engineering concepts from three-nanite while preserving MIST's PC/Unreal target. Unreal Native Nanite remains the production virtualized-geometry system. This repository is not an alternative renderer.

## In scope
- Cluster DAG construction and crack-free simplification concepts.
- Projected geometric error and monotonicity requirements.
- Offline mesh preprocessing and per-asset quality metadata.
- Deterministic topology/edge validation methods.
- Coarse-first geometry layout as a data-locality/streaming hypothesis.
- Reproducible benchmark methodology and failure documentation.

## Out of scope
Shipping Three.js/WEBGL runtime; replacing Unreal Native Nanite; porting ClodBatch, WebGL multi-draw or Three.js private internals into MIST; replacing UE Static Mesh LOD/HLOD/World Partition/IO; treating browser timings as PC/Unreal evidence; adopting upstream pixel thresholds, triangle budgets or file format as MIST policy.

## Research questions
1. Which geometric-error definitions predict visible silhouette/normal-map degradation by asset class?
2. Which LOD/cut topology properties can be validated deterministically offline?
3. Which simplification defects need automated rejection versus human review?
4. Does coarse-first/chunked layout improve any actual UE asset/IO workload?
5. Which upstream benchmark practices can be reproduced in a pinned UE project?

## Validation boundary
Geometry preprocessing may be studied here. Engine import, Nanite fallback, LOD/HLOD, materials, shadows, collision, streaming and target-hardware performance must be tested in Unreal. A passing reference-lab test cannot substitute for UE integration validation.
