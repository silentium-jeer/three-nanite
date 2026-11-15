# 06 — Reference Limitations and Provenance

**Status:** REFERENCE LIMITATIONS RECORDED · NO PRODUCTION ADOPTION

## Technical limits recorded upstream
The upstream README/report describe an experiment rather than a production engine feature. Recorded limits include CPU-side hierarchy selection; standard hardware rasterization/forward shading without Nanite visibility buffer or compute software rasterizer; relatively large uncompressed hierarchy data; coarse level-granular streaming with no eviction; partial instance-level occlusion using earlier-frame depth; static opaque rigid meshes; no skinning/morph targets/transparency sorting; one-material/UV-set limitations; no geomorphing; and reliance on Three.js private BatchedMesh fields/browser extension behavior.

Re-check exact source revision before reusing any technical detail.

## MIST interpretation
Useful for cluster DAG/projected-error concepts, offline preprocessing/validation test design, explicit benchmark/failure reporting and progressive coarse/fine residency hypotheses.

Not useful as PC/Unreal performance evidence, replacement for Unreal Native Nanite, production geometry/streaming dependency or universal triangle/pixel-error policy.

## Provenance
- Upstream: https://github.com/apekshik/three-nanite
- MIST fork: https://github.com/silentium-jeer/three-nanite
- Upstream reference revision at review: `b730aac13ab0ea67b75214613eea56c14151f6e5`
- Fork observed at same HEAD when reviewed; this package contains documentation only.
- Upstream declares MIT. Preserve license notices and attribution before copying source code. This package maps concepts and does not copy implementation code.

## Evidence limitation
Upstream benchmark report is author-produced; its test meshes are not included in the repo. MIST has not independently reproduced those measurements. External figures remain reference data only.
