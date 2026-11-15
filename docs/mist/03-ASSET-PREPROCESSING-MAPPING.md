# 03 — Asset Preprocessing Mapping

**Priority:** P1 for asset-pipeline design; no upstream binary/runtime format adoption.  
**Status:** RESEARCH REFERENCE

## Relevant upstream steps
GLB input validation and transform normalization; meshlet generation (up to 128 triangles in this implementation); cluster grouping; attribute-aware simplification with border locks; hierarchical cluster regeneration/error propagation; coarse-first output arrangement; optional discrete LODs; metadata and texture extraction.

The reusable idea is a deterministic preprocessing stage with declared input/output identity and repeatable metrics.

## Unreal mapping
Investigate native/editor workflows:
- source mesh ingest and DCC normalization;
- Static Mesh build settings and automated LOD generation;
- Nanite enablement and fallback settings where applicable;
- collision generation/complexity and intended-use metadata;
- material slot/texture policy and dependency validation;
- HLOD layer/build configuration for world aggregation;
- import/build/cook validation and target-platform review.

Prefer supported Unreal APIs, commandlets, Data Validation and build integration where they satisfy the need. Do not port the JavaScript GLB builder as the default production route.

## Proposed manifest
Asset ID/class, source path/URI and hash, DCC/tool version, transformation recipe/version, output hash, coordinate/unit normalization, material/texture references, UV metadata, geometry metrics, LOD/Nanite/fallback metadata, collision metadata, dependencies, validation results, reviewer/approval and UE import/build evidence.

## Experiments
Compare authored LODs with UE-generated LODs by asset class; measure preprocessing/build/cook time, output size and runtime memory; test silhouette/thin-feature/UV/normal degradation; verify deterministic output where possible; record repair rate and human review time.

No new MIST mesh format, custom runtime loader or renderer is proposed.
