# 04 — Geometry Data Layout

**Priority:** P2  
**Status:** HYPOTHESIS · NOT TESTED IN UNREAL

## Reference observation
three-nanite stores coarse hierarchy levels first and numbers vertices to form compact prefixes. Its report describes improved vertex locality on one integrated GPU. This is implementation-specific browser evidence, not proof that Unreal Static Mesh or Nanite layout should change.

## MIST questions
- Does source mesh ordering or asset/package organization affect UE import/build/cook cost?
- Are there measurable IO read-amplification differences for current asset/chunk packaging?
- Do HLOD/World Partition cells exhibit locality problems or dependency fan-out?
- Which data is loaded/resident at each transition stage?
- Can asset grouping reduce redundant IO/decompression without worsening memory or hitches?

## Constraints
Do not infer Nanite's internal page layout from this repo. Do not introduce a custom package/cluster format without a measured native-system gap and separate approval. Keep identity, resource requests and representation state independent from physical layout. Smaller disk size is not automatically faster at runtime; include decompression and initialization.

## Proposed experiment
Use a fixed asset/cell manifest and compare supported UE package/chunk/asset organization variants. Capture cook output, IO traces, async-load duration, dependency counts, memory residency and traversal hitch distributions on target hardware. Preserve warm/cold cases and raw artifacts.

Retain only findings reproduced on the pinned Unreal build and representative PC profile; otherwise mark NOT ESTABLISHED.
