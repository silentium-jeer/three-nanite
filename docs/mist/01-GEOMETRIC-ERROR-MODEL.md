# 01 — Geometric Error Model

**Priority:** P2  
**Status:** HYPOTHESIS / DESIGN INPUT · NOT A MIST STANDARD

## Reference concept
three-nanite projects cluster/group geometric error into screen space using a bounding sphere, camera projection and viewport parameters. Its hierarchy enforces non-decreasing error upward so a selected cut can be evaluated without neighbor communication.

This is a useful reference algorithm, not a claim that Unreal Nanite exposes or uses an identical external contract.

## MIST relevance
Potential offline uses:
- compare source mesh and generated LOD/fallback silhouette;
- predict asset-class-specific screen-space deviation;
- find thin-feature loss and coarse-level collapse;
- build camera/route test cases for LOD/HLOD transitions;
- store quality metadata alongside an asset validation manifest.

Potential Unreal validation uses:
- compare project-authored LODs and HLOD outputs under fixed camera paths;
- inspect Nanite fallback quality for paths that require it;
- correlate geometric metrics with human review and target-build evidence.

## Required inputs
Source/output identities and hashes; coordinate space/unit scale; source/output bounds; camera FOV/viewport/transform; view/visibility assumptions; error metric definition, units and algorithm version; asset class and feature-protection policy; reference camera set and acceptance profile.

## Risks and limitations
Bounding-sphere projected error is conservative and may mispredict silhouette defects. Normal/UV attribute error is not identical to perceptual error. Thin surfaces, foliage cards, hard-surface edges, alpha masks, high-frequency normal maps and glancing angles require separate treatment.

Do not copy upstream pixel thresholds into MIST. The upstream report documents coarse-quality degradation and a browser forward-rendering pipeline with different bottlenecks from Unreal Nanite.

## Proposed evaluation
1. Build a labeled asset corpus by class: hard-surface prop, modular architecture, organic prop, foliage, vehicle and static character proxy.
2. Generate controlled LOD/fallback variants with source/output hashes.
3. Render fixed views across distance, FOV and resolution.
4. Measure silhouette displacement, projected symmetric distance, normal deviation and thin-feature survival.
5. Run blinded human review.
6. Correlate metrics with per-class acceptance; report false acceptance/rejection.

## Decision boundary
Offline QA/research only. It does not select runtime Nanite clusters or override Unreal's native view-dependent representation.
