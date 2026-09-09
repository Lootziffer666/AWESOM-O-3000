# MUSE SPARK 1.3 — 100 GENERATED HTML DONOR CATALOG

**Status:** full static pass over all 100 numbered HTML files. No title-only sampling. The supplied archive contains 100 self-contained HTML/CSS/JS studies, 100 prompt files, thumbnails, an offline gallery, and a Playwright screenshot helper.

Each page is treated as a **candidate micro-donor**. Titles/prompts are metadata, never evidence. Grades below are based on implementation present in the HTML/CSS/JS. Physical, chemical, biological, financial, astronomical or quantum correctness is not inferred from visual plausibility. No license file was present in the supplied archive, so the safe default is **reference / algorithm / equation / test inspiration**, not direct code copying.

## Grades

- **A+** — unusually strong, directly reusable computational primitive / solver / algorithm.
- **A** — clear reusable computational primitive.
- **A-** — useful compact algorithm/approximation with caveats.
- **B** — useful rendering, interaction, procedural or heuristic donor; not a strong solver.
- **C** — mainly UI/presentation or a false friend for the named phenomenon.

**Counts:** A+ 1 · A 6 · A- 18 · B 45 · C 30

## Strong new primitives vs. Fable 5.1 + GPT-6 Astra + DeepSeek v4 Flash + Qwen 3.8 Max

| ID | Page | Grade | New primitive | Why it matters |
|---:|---|:---:|---|---|
| 023 | `physics-orbits` | **A+** | Softened mutual N-body gravity + inelastic momentum-conserving mergers | First collection here to go beyond fixed gravity wells into mutual body-body gravity. |
| 019 | `generative-terrain` | **A** | Mutable seeded heightfield with local brush/rain lowering | Useful surface-field mutation pattern; explicitly a heuristic, not hydraulic erosion. |
| 050 | `meadow-pollinators` | **A** | Scent-biased nearest-target foraging agents | Distinct lightweight goal-selection/retargeting primitive for insects/agents. |
| 034 | `pixel-garden` | **A-** | Resource-coupled discrete crop growth | Water and season alter staged maturation; useful systems-game primitive, not botany. |
| 039 | `copper-steampunk` | **A-** | Coupled pressure/heat/control state with valves and auto-vent | Interesting compact control-loop heuristic; equations are authored, not thermodynamic truth. |
| 072 | `dna-helix-viz` | **A-** | DNA complement/RNA/triplet/GC transforms + mutation | New sequence-transformation utility; biological tables are intentionally incomplete. |

These are **candidate primitives**, not automatically validated production physics. Promotion into SHADED still requires independent equations/units/invariant checks and a black-box/acceptance test that does not use the generated demo as its own oracle.

## Primitive families

- **Dynamics / mechanics:** 011, 021, 023, 044, 046, 052, 085, 088
- **Terrain / scalar fields:** 014, 019, 040, 056, 100
- **Agents / behavior:** 021, 050
- **Growth / living-system heuristics:** 034, 050, 072
- **Audio / signal:** 027, 033, 039, 061, 065, 066, 069, 076, 077
- **Procedural rendering / fields:** 013, 014, 019, 031, 038, 040, 042, 043, 056, 100
- **Path / network motion:** 012, 074
- **Color / raster / authoring:** 054, 057, 068, 092, 093, 095
- **Control/state systems:** 034, 039, 045, 047, 061, 069

## Full inventory

See [`MUSE_SPARK_1_3_100_INVENTORY.md`](MUSE_SPARK_1_3_100_INVENTORY.md) for the complete 100/100 page classification.

## Explicit false-friend warnings

- **006 `quantum-dashboard`:** Quantum terminology is visual/stateful only; no amplitudes, unitary gates, measurement model, or Bloch-state math.
- **013 `liquid-chrome`:** Good procedural material shading; no liquid solver.
- **022 `svg-tides`:** Stylized wave/tide visualization; no tidal physics.
- **025 `infographic-climate`:** No climate data/model.
- **042 `desert-mirage`:** No atmospheric refraction or sediment physics.
- **043 `arctic-aurora-lab`:** No plasma/magnetosphere physics.
- **049 `canyon-echoes`:** No acoustic propagation/ranging.
- **064 `stargazer-planner`:** No astronomy/ephemeris.
- **067 `labyrinth-canvas`:** No maze solver/pathfinding; solution ignores walls.
- **070 `plant-care-panel`:** No plant/soil model.
- **071 `stock-market-poetry`:** No real market model/data.
- **073 `weather-cathedral`:** No atmospheric model.
- **080 `chess-tactics-board`:** Not chess move generation/search/engine despite engine claims.
- **090 `tooltip-planetarium`:** No celestial mechanics/projection.
- **096 `bonsai-circuit`:** No circuit/electrical simulation.
- **097 `sahara-astronomy`:** No astronomy/orbital model.

## Most SHADED-relevant takeaways

- **023 is the standout:** it computes softened mutual gravity between all bodies and supports inelastic mergers that preserve linear momentum. This is materially different from Qwen's fixed gravity wells.
- **019 is useful because the field is mutable:** a seeded height grid can be locally lowered by pointer/rain stamps and immediately changes terrain classification and route height. Do not call it erosion; it is a local subtraction heuristic.
- **050 provides a compact behavior primitive:** agents periodically choose a flower target using distance minus scent bias, move toward it, register visits, and retarget.
- **056 is a good field-authoring donor, not a fluid donor:** 900 particles are steered by a trigonometric vector field, while interactive vortices inject directional impulses.
- **034 is useful for systems gameplay:** water and season modulate staged crop growth. Treat it as a tunable game-system primitive rather than botanical simulation.
- **039 is an authored control-system toy:** coal increases pressure/heat, valves bleed pressure, and an overpressure threshold auto-vents. The architecture is useful; the numerical model is not validated thermodynamics.
- **072 has real sequence transforms but incomplete biology:** complement, RNA conversion, GC composition and mutation are usable utilities; the amino-acid/codon mapping is only partial.
- **006 must stay downgraded:** the 'quantum dashboard' toggles classical bits and animates a decorative Bloch-style view; it does not simulate qubit amplitudes or gates.
- **067 must stay downgraded:** its 'solution' is a sinusoidal line between endpoints and ignores user-drawn walls; there is no pathfinding/maze solver.
- **080 must stay downgraded:** pieces can move without legal move validation and the claimed engine evaluation is synthetic.

## Verification policy

1. Generated page title/prompt is metadata, never evidence.
2. Extract the computational kernel and state its actual contract.
3. Mark visual approximations and synthetic/fake data explicitly.
4. Deduplicate by primitive family, not by page theme.
5. Validate equations/units/invariants independently before promotion into a SHADED donor.
6. For regressions or ports, build a reproducible black-box/acceptance test that fails before the fix and passes after it; the generated implementation must not be its own golden oracle.
