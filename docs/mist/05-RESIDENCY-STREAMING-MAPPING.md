# 05 — Residency and Streaming Mapping

**Priority:** P1 program reference; Unreal validation belongs in UE test environments.  
**Status:** RESEARCH REFERENCE · NOT UE VALIDATION

## Upstream pattern
three-nanite keeps coarse hierarchy information resident and fetches finer geometry levels on demand using HTTP Range requests. It loads whole levels per asset and has no eviction. This is a coarse-grained progressive-refinement demonstration, not a production residency system.

## Useful concepts
A low-detail valid representation may be available before fine data; hierarchy/metadata for refinement is distinct from detailed geometry payload; fine-data demand can be derived from current selection; residency is measurable independently of source asset size; coarse-first layout can simplify progressive acquisition.

## MIST/Unreal mapping
Compare only against supported UE-native pathways:
- World Partition cells/HLOD layers and runtime streaming sources;
- async asset loading and package/chunk organization;
- Nanite native virtualized-geometry residency where observable;
- texture streaming and other resource residency;
- collision/navigation/animation dependencies required for readiness.

A visual representation's residency does not imply gameplay or collision dependencies are ready.

## Test requirements
Request/load/initialize/ready/in-use/releasing/evicting/failed timing; cold/warm traversal; memory high-water/resource retention; request coalescing/cancellation/churn; visual and collision handoff independently; reacquisition cost and active-consumer safety; persistent identity/state preservation.

The Unreal test project, not this Three.js repo, must produce acceptance evidence.
