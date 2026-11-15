# MIST Reference Lab — three-nanite

**Role:** Virtual Geometry & Asset Validation Research Lab  
**Status:** RESEARCH REFERENCE ONLY  
**Production dependency:** NOT ACCEPTED  
**Upstream:** apekshik/three-nanite

## Purpose
Preserve selected algorithm, preprocessing, validation and benchmarking insights for MIST without turning the Three.js runtime into an Unreal production dependency.

This lab covers cluster hierarchy, projected geometric error, crack-free cut checks, offline preprocessing, geometry layout hypotheses and evidence methodology. Unreal-only World Partition/HLOD, collision handoff, VSM and foliage scenes belong in Unreal test projects and silentium-jeer/Unreal-mist.

## Documents
- [00 — Research Scope](00-RESEARCH-SCOPE.md)
- [01 — Geometric Error Model](01-GEOMETRIC-ERROR-MODEL.md)
- [02 — Crack-Free Validation](02-CRACK-FREE-VALIDATION.md)
- [03 — Asset Preprocessing Mapping](03-ASSET-PREPROCESSING-MAPPING.md)
- [04 — Geometry Data Layout](04-GEOMETRY-DATA-LAYOUT.md)
- [05 — Residency and Streaming Mapping](05-RESIDENCY-STREAMING-MAPPING.md)
- [06 — Reference Limitations](06-REFERENCE-LIMITATIONS.md)
- [07 — Upstream Report Assessment](07-UPSTREAM-REPORT-ASSESSMENT.md)

## Upstream preservation
Keep upstream src/, examples/, test/, docs/REPORT.md, docs/RESEARCH.md and docs/bench/ as reference material. Do not make unreviewed runtime changes as part of MIST documentation work.

## Evidence discipline
Upstream results are external reference measurements, not MIST pass evidence. Unreal comparisons require a pinned project/build, target hardware, equivalent asset/camera conditions, raw Unreal captures and repeatable runs.
