# 02 — Crack-Free Validation

**Priority:** P2 advanced LOD validation; basic mesh health remains P1 in the parent program.  
**Status:** DESIGN INPUT · EXPERIMENT NOT RUN

## Upstream reference
three-nanite includes an offline verifier that selects hierarchy cuts from multiple camera positions and error thresholds, then checks open edges and error monotonicity. This is a useful starting pattern, not a complete asset correctness proof.

## MIST validation goals
- no unexpected open boundaries introduced by simplification;
- parent/group error monotonicity where the hierarchy requires it;
- shared boundaries remain positionally consistent within declared tolerance;
- normals/winding and UV charts remain valid for the asset class;
- degenerate/non-manifold topology regressions are detected;
- thin features and disconnected components are not silently removed where the class contract requires retention.

## Important distinction
An open edge in the source mesh is not automatically a defect. Hard-surface shells, single-sided foliage and intentionally open surfaces may be valid. Compare source defects with introduced defects and apply class-specific rules. A naive watertightness requirement would incorrectly reject many valid real-time assets.

An LOD cut edge test does not prove continuity across separate UE components, landscape tiles, HLOD cells or streaming boundaries. Those require in-engine adjacency/transition tests.

## Test layers
1. Static source audit: topology, degenerates, bounds, normals, UV/material metadata.
2. Generated LOD audit: introduced edge defects, error monotonicity, component/feature loss.
3. Boundary compatibility: adjacent modular pieces/tiles/cells under known transforms and tolerance.
4. Unreal visual transition: camera motion, LOD switches, HLOD/cell handoff and packaged build.
5. Collision continuity: separate collision representation and ownership tests; never infer from visual geometry.

## Outcomes
PASS / FAIL / INDETERMINATE / NOT_APPLICABLE per rule. Store source/output hashes, tool versions, numerical tolerances, defect counts, screenshots and reviewer notes.
