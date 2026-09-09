# DEEPSEEK V4 FLASH — 100 GENERATED HTML DONOR CATALOG

**Status:** full static pass over all 100 numbered HTML files. No title-only sampling.

The supplied archive contains **100 numbered HTML studies** and **100 matching prompt/text files**, plus authoring briefs/requirements and a small smoke-test artifact folder. No license file was present, so the safe default is **reference / algorithm / equation / test inspiration**, not direct code copying.

Each page is treated as a **candidate micro-donor**. Titles/prompts are metadata, never evidence. Physical, chemical, biological or mathematical correctness is not inferred from visual plausibility.

## Grades

- **A+** — unusually strong, directly reusable computational primitive / solver / algorithm.
- **A** — clear reusable computational primitive or strong heuristic with explicit limits.
- **A-** — useful compact algorithm/approximation with caveats.
- **B** — useful rendering, interaction, procedural or heuristic donor; not a strong solver.
- **C** — mainly UI/presentation or no meaningful SHADED computational donor.

**Counts:** A+ 7 · A 21 · A- 30 · B 35 · C 7

## Strongest new primitives vs. Fable + Astra + DeepSeek SINGULARITY + Qwen + Muse + Ox/GLM

| ID | Page | Grade | Primitive | Why it matters |
|---:|---|:---:|---|---|
| 066 | `marble-ink` | **A+** | Differential comb-shear marbling transform + curl-advection | Distinct surface/material transformation: snapshot read semantics, strip-wise differential shear, animated comb rake. |
| 075 | `ant-colony` | **A+** | Agent ↔ pheromone-field feedback | Agents sense a scalar field, deposit into it, field diffuses/evaporates, food changes behavior. Strong reusable coupled system. |
| 089 | `slime-mold` | **A+** | Physarum-style sensor/deposit/diffuse loop | Tri-sensor trail following with deposition, Laplacian-like diffusion/decay and food interaction; strong emergent morphology primitive. |
| 036 | `topo-terrain` | **A+** | Mutable heightfield authoring → contours → hillshade | Seeded terrain, sculpt/flatten brushes, Marching Squares, loop walking, hillshade and peak extraction in one compact pipeline. |
| 080 | `dune-wind` | **A** | Aeolian heightfield transport heuristic | Wind-driven grains alter a mutable dune field via slope-sensitive erosion/deposition. Very relevant to SHADED, but not mass-conserving. |
| 039 | `voronoi-bloom` | **A** | Voronoi field + Lloyd-style centroidal relaxation | Extends the earlier Voronoi donor into self-relaxing centroidal cells. |
| 092 | `letter-physics` | **A** | Dynamic bodies coupled to a deformable 1D net | Collision bodies inject impulses into a damped propagating trampoline/string field. |
| 069 | `moon-phases` | **A** | Per-pixel spherical Lambert illumination | A compact sphere-illumination/material reference independent of astronomical ephemeris. |
| 077 | `coral-growth` | **A** | Occupancy-constrained branching growth | Growth candidates are scored against free space and directional bias; useful procedural structure concept, though one neighbor-scoring helper is buggy. |

## Strong overlaps worth keeping

- **050 `cursor-ripple` — A+**: discrete ripple/wave heightfield with ping-pong buffers; overlaps Fable 099 but is independently useful.
- **062 `waving-flag` — A+**: Verlet cloth with structural + shear constraints, wind/gravity and facet shading; overlaps Qwen cloth but provides a different compact reference.
- **090 `gray-scott` — A+**: real Gray-Scott reaction-diffusion; overlaps Fable 086 and is valuable as an independent implementation.
- **074 `boids-flock` — A**: spatially binned flocking + predator response; overlaps Fable 080.
- **082 `orbit-lab` — A**: mutual softened inverse-square acceleration loop; overlaps Muse's stronger N-body donor.
- **084 `chladni-plate` — A**: modal field + gradient-biased grains; overlaps Fable 076.

## Important failures / false friends

### 023 `jelly-physics` — visually convincing, numerically flawed

The soft-body page has the right vocabulary — ring points, spring constraints, pressure restoration and Verlet-style position history — but its implementation is not a trustworthy solver:

- neighbor spring accelerations are **assigned/overwritten** rather than accumulated;
- the named `GRAV` term is applied in the **x** update, while y receives a tiny separate constant;
- blob-blob interaction is centroid repulsion rather than surface collision.

Keep it as a **soft-body design sketch**, not a physics oracle.

### 032 `maze-gen` — maze topology is broken

The code defines wall bitmasks and then “carves” by clearing bits, but reset initializes every wall cell to **0**. Clearing bits from zero does nothing. The solver checks those bits and therefore sees an effectively **wall-free grid**.

The DFS visitation order and shortest-path code are individually useful, but the combined “maze generator + solver” is not correct as written.

### 080 `dune-wind` — useful transport idea, not conservative sediment physics

The heightfield genuinely mutates in response to wind and slope. However, multiple branches add more height than they remove, so the algorithm can create sand mass. Treat it as an **aeolian visual/authoring heuristic** until rewritten around explicit mass conservation.

### 039 `voronoi-bloom` — second relaxation pass is not a true Lloyd iteration

The code computes centroids once, then may apply two movements toward those same centroids without recomputing the Voronoi partition. It is still a useful centroidal relaxation heuristic, just not two proper Lloyd iterations.

### 077 `coral-growth` — neighbor score helper misuse

The main occupancy test is meaningful, but one `occAt(...).get(...)` call passes coordinate-like values to a getter that accepts a single linear index. The growth concept survives; the neighborhood scoring should be rewritten before reuse.

### Other title traps

- `013-fluid-wave`: layered prescribed wave curves, **not** fluid dynamics.
- `054-aurora-borealis`: procedural ribbons/noise, **not** plasma/magnetosphere physics.
- `056-black-hole`: lensing-style visual, **not** GR/geodesic integration.
- `057-supernova`: particle burst, **not** stellar physics.
- `060-stained-glass`: stylized light beam, **not** validated refraction.
- `063-smoke-study`: buoyant curl-noise particles, **not** a fluid solver.
- `072-comet-catch`: Bezier path, **not** orbital mechanics.
- `093-zen-sand`: rake/surface drawing, **not** granular transport.

## Primitive families

- **Fields / PDE / cellular:** 033, 036, 038, 039, 050, 059, 075, 080, 089, 090
- **Constraints / deformables / mechanics:** 018, 023, 041, 042, 062, 073, 081, 082, 092
- **Agents / emergent systems:** 004, 068, 074, 075, 077, 089
- **Procedural geometry / projection:** 012, 015, 021, 031, 035, 036, 037, 039, 069, 070, 076, 077
- **Surface / material transforms:** 007, 020, 045, 051, 052, 061, 065, 066
- **Audio / signal:** 030, 034, 100
- **Environment / particles:** 026, 028, 054, 055, 057, 063, 067, 068, 071, 078, 079, 087, 088, 100
- **Discrete topology / search:** 032, 033, 038, 039

## Most SHADED-relevant takeaways

1. **066 is unusually valuable** because it is not “ink that looks marbled”; it implements a distinct *material-space transformation* with separated read/write buffers. That maps well to surface-bound material editing.
2. **075 and 089 are the big systems finds.** Both couple mobile agents to a persistent field they themselves modify. This is exactly the kind of world-state feedback SHADED can generalize.
3. **080 fills a missing conceptual layer between falling-sand cells and full sediment simulation.** Its current math is non-conservative, but the architecture — explicit grains + mutable heightfield + wind — is highly relevant.
4. **036 is a strong authoring pipeline**, even though Fable's Marching Squares handles ambiguity more carefully. DeepSeek adds direct sculpt/flatten tools and hillshade/peak extraction.
5. **The failures are useful evidence for the workflow:** titles and even comments are insufficient. The wall-bit bug in 032 and force-assembly bug in 023 are only visible when the actual state update is inspected.

## Verification policy

1. Generated page title/prompt is metadata, never evidence.
2. Extract the computational kernel and state its actual contract.
3. Check state initialization, buffer swaps, force accumulation, conservation/invariants and boundary conditions — not just formula names.
4. Mark visual approximations, dead paths and synthetic data explicitly.
5. Deduplicate by primitive family, not by page theme.
6. Validate equations/units/invariants independently before promotion into SHADED.
7. For ports/regressions, use independent black-box scenes/metrics; never use the generated implementation as its own golden oracle.

## Full inventory

See [`DEEPSEEK_V4_FLASH_100_INVENTORY.md`](DEEPSEEK_V4_FLASH_100_INVENTORY.md) for the complete 100/100 page classification.
