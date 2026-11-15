# 07 — Upstream Report Assessment

**Audit date:** 2026-11-15  
**Status:** SOURCE REVIEWED · REFERENCE VALUE CONFIRMED · PRODUCTION ADOPTION NOT ACCEPTED

## 1. What the project actually is

The upstream project describes a Nanite-style virtual-geometry experiment for Three.js. It contains an offline GLB preprocessor and a browser runtime. The preprocessor uses the WASM build of meshoptimizer; runtime hierarchy selection runs on the CPU and uses Three.js drawing facilities. The upstream README explicitly says this is an experiment, not a production engine feature, and states that it is not affiliated with or derived from Unreal Engine code.

Sources:
- https://github.com/apekshik/three-nanite
- https://github.com/apekshik/three-nanite/blob/main/docs/REPORT.md
- https://github.com/apekshik/three-nanite/blob/main/docs/RESEARCH.md

## 2. Relevant algorithmic ideas

The upstream report/research describes the following pipeline:
1. Split source geometry into meshlets of up to 128 triangles.
2. Group adjacent meshlets and simplify grouped geometry.
3. Lock shared group-boundary vertices during simplification to preserve a crack-free replacement boundary.
4. Build higher hierarchy levels, retaining group/cluster provenance.
5. Enforce monotonic parent error and bounds so a local threshold test can select a consistent cut.
6. Select the cut using projected error; frustum-cull groups/clusters.
7. Run an offline verifier that evaluates selected cuts at sampled camera positions and thresholds and reports open edges.

These are useful references for offline asset QA and LOD/HLOD validation. The verifier's sampled camera positions and thresholds are a finite test corpus, not a proof of crack freedom for all possible camera paths, transformations or content.

## 3. Limits that matter to MIST

Upstream explicitly documents these limitations:
- Runtime selection is CPU-side.
- Drawing uses standard hardware rasterization and forward shading; it does not implement Nanite's visibility buffer or compute software rasterizer.
- Hierarchy data is relatively large and uncompressed.
- Streaming is level-granular and has no eviction.
- Occlusion is partial, instance-level and based on older depth.
- The content path is static, opaque and rigid; no skinning, morph targets or transparency sorting.
- One material and one UV set per asset.
- No geomorphing.
- The runtime depends on Three.js private BatchedMesh fields and browser multi-draw behavior.

These limitations prevent its use as a production renderer, Unreal Nanite substitute, runtime geometry dependency or evidence of PC/Unreal performance.

## 4. Upstream benchmark provenance

The upstream measurement report is dated 2026-11-11. It describes six AI-generated props with approximately 1.85–1.97 million source triangles each, measured in Chrome using Three.js 0.186.1 and meshoptimizer 1.3.0 on one integrated AMD GPU and an RTX 5090.

The report notes that the test meshes are not included in the repository and warns that some integrated-GPU runs varied by approximately 20–30%. Consequently:
- Do not import upstream FPS/frame-time numbers into a MIST acceptance threshold.
- Do not compare its browser draw path to Unreal Nanite or UE renderer timings.
- Treat every upstream benchmark as author-produced external reference evidence.
- Re-run equivalent questions in a pinned Unreal scene before making any production decision.

## 5. MIST research use

Retain this repository as a methodology and offline-algorithm reference for:
- projected geometric-error definitions and monotonicity checks;
- source/output provenance for offline simplification;
- crack checks on selected mesh cuts;
- fixed-camera and multi-threshold LOD/HLOD regression fixtures;
- comparing geometric metrics with silhouette/normal/attribute quality.

A future MIST evaluation may compare source assets with generated LODs and HLOD proxies using a labeled asset-class corpus and fixed cameras. It must remain offline QA: no runtime cut selection, renderer integration or production dependency is implied.

## 6. Decision

**ACCEPT AS RESEARCH REFERENCE ONLY.**  
**NOT ACCEPTED** as a production runtime, renderer, geometry streaming system, Unreal Nanite replacement or performance evidence source.

The MIST lab should preserve upstream source and licence notices. This document maps concepts and findings; it does not copy upstream implementation code.
