# OX ALPHA / GLM 5.3 — SECOND 100 GENERATED HTML DONOR CATALOG

**Status:** full static pass over all 100 numbered HTML files. No title-only sampling.

The supplied archive is `Ox-Alpha-100-HTML-Files-main.zip`; its README labels the generator **Ox Alpha**. The user identifies Ox Alpha here as GLM 5.3, so this catalog keeps both names to distinguish it from the earlier `GLM-5.3-100-HTML-Files` collection.

The archive contains **100 self-contained HTML/CSS/JS studies**, 100 matching prompt files, thumbnails and a gallery. No standalone `LICENSE`, `COPYING`, or `NOTICE` file was found, so the safe default remains **reference / algorithm / equation / test inspiration**, not direct code copying.

All 100 embedded JavaScript payloads passed a `node --check` syntax parse. This is not proof of browser/runtime correctness; semantic/state-update defects were audited separately and several were found.

## Why this GLM 5.3 set feels different

This is genuinely a different 100-page benchmark set: there is **0/100 slug overlap** with the earlier GLM 5.3 collection.

| Metric | Earlier GLM 5.3 | Ox Alpha / second GLM 5.3 |
|---|---:|---:|
| Mean HTML chars | 16269 | 14932 |
| Mean JS chars | 8616 | 7042 |
| Mean named functions | 8.82 | 8.50 |
| Mean loops | 4.77 | 5.53 |
| Mean prompt chars | 2326 | 1814 |

Raw code and prompt length are **not larger** in the second set. The difference is architectural: more pages couple persistent state, procedural geometry, agents, controls and world consequences instead of spending most of their JS on presentation.

## Grades

- **A+** — unusually strong, directly reusable computational primitive / integrated system.
- **A** — clear reusable computational primitive or strong compact implementation.
- **A-** — useful algorithm/approximation with caveats.
- **B** — useful rendering, interaction or heuristic donor; not a strong computational primitive.
- **C** — mainly presentation/UI or a misleading title with little useful computation.

**Counts:** A+ 3 · A 26 · A- 35 · B 22 · C 14

Compared with the earlier GLM 5.3 pass (**A+ 2 · A 13 · A- 29 · B 41 · C 15**), the second set has **29 A-or-better pages vs. 15**, and **64 A-/or-better pages vs. 44**.

## Strongest new primitives / systems

| ID | Page | Grade | Primitive | SHADED relevance |
|---:|---|:---:|---|---|
| 042 | `bonsai-trainer` | **A+** | Mutable recursive branch tree with seasonal growth, soil moisture, pruning and wiring constraints | Excellent example of persistent structure + user edits + future growth responding to those edits. |
| 086 | `meridian-sundial` | **A+** | Solar declination approximation + horizontal sundial hour-angle + solar altitude + shadow length | Real compact solar/sundial geometry; substantially stronger than earlier decorative sundial pages. |
| 029 | `terminal-tales` | **A** | Command parser + rooms/items/inventory + world-state transitions | Tiny language-driven world-state engine; useful for action/interaction contracts. |
| 046 | `ceramic-studio` | **A** | Editable radial profile + spline reconstruction + nearest-control interaction | Strong authoring primitive for procedural vessel/lathe-like geometry. |
| 051 | `koi-pond` | **A** | Food-seeking agents + segmented body chain + interactive current/pellet state | Entity behavior and body representation respond to world inputs; good multi-layer coupling pattern. |
| 061 | `bauhaus-mobile` | **A** | Hierarchical damped pendulum/mobile with support coupling and gust impulses | Compact coupled-oscillator mechanics reference rather than independent decorative motion. |
| 071 | `planetarium-dome` | **A** | Uniform hemisphere sampling + fisheye-like projection + look transform | Useful dependency-free projection/sampling primitive. |
| 087 | `lace-maker` | **A** | Bobbin/pin lace grammar producing ordered over/under quadratic thread segments | New topology/material-structure family beyond prior plain/twill weave. |
| 014 | `hologram-scan` | **A** | Procedural 3D wireframe mesh + manual yaw/pitch/perspective projection | Small black-box 3D projection reference. |
| 019 | `mycelium-network` | **A** | Nutrient-seeking branching walkers with persistent trails and fruiting events | Agent-driven persistent world marking / procedural growth. |

## Strong overlaps worth keeping

- **055 `modular-synth` — A+**: polyphonic WebAudio synth with ADSR, low-pass filter, waveshaper drive and LFO routing. Strong independent audio implementation; overlaps earlier Fable/GLM audio donors.
- **030 `pendulum-harmonograph` — A**: damped analytic oscillator curves; independent overlap with Fable's harmonograph family.
- **073 `quantum-garden-cfd` — A**: finite-difference curl of a scalar noise field feeding particle advection. Useful flow-field reference, **not CFD**.
- **007 `herbarium` — A**: seeded recursive plant geometry; overlap with earlier L-system/growth donors but via a different direct branch grammar.
- **032 `bauhaus-playground` — A**: seeded rule-based composition plus inertia/snap/rotation/layers; useful editor/authoring overlap.
- **089 `opera-house-program` — A**: scheduled WebAudio plucks plus feedback delay and score/libretto timing.

## Semantic failures and hidden bugs found in the deeper audit

### 067 `tectonic-plates` — plate translation is broken

The page looks like a rich plate-tectonics system, but its transform subtracts the **current** plate center from fixed absolute base vertices and adds that same current center back after rotation. At zero rotation, `ox/oy` therefore cancel exactly and plate velocity produces **no translation at all**. With rotation, moving the pivot causes a different warped motion, not clean rigid drift. Boundary 'closing/opening' classification also uses original centers and authored velocities. Keep the coupling architecture as inspiration; do not treat it as a plate-motion solver.

### 034 `chess-endgame` — rule subset is real, reveal/search is not trustworthy

The K+Q vs K move/check/mate/stalemate logic is meaningful, but the reveal routine contains always-true/no-op conditions such as `... || true`. It is a specialized rule-engine sketch, not a reliable mate searcher.

### 073 `quantum-garden-cfd` — title overclaims CFD

The field is generated by finite-differencing value noise into a curl-style velocity field and advecting particles through it. There is no pressure projection, diffusion solve, continuity step or Navier–Stokes integration.

### 075 `mechanical-watch` — tooth counts do not drive the kinematics

The gear geometry uses tooth counts, but angular velocities are authored constants. The displayed claim that the train is ratio-scaled should not be treated as evidence of mechanical correctness.

### 091 `observatory-ephemeris` — only linear mean longitude

`Julian Date` is real, but each planet is reduced to `L = L0 + n·d`. Eccentricity, Kepler's equation, orbital planes and observer geometry are not solved. The 'night sky' visibility test is also a longitude heuristic, not true observability.

### 092 `paper-marbling` — boundary relaxation has a seam bug

Each drop stores perimeter points **plus a center point**. Rendering correctly excludes the center from the polygon, but `relax()` loops over the whole array and treats that center as a neighbor of the first/last perimeter points. That biases/collapses one contour seam. The local shear idea is still useful, but the relaxation ring should exclude the center.

### 094 `tide-clock` — phase label contradicts its own sine

The code comments `phase 0 = high water`, while height is `mean + amp·sin(phase)`. That puts high water at quarter-cycle, not phase zero. It is also a single semidiurnal harmonic, not constituent-based tide prediction.

### 096 `snow-globe-workshop` — settled snow creates mass every frame

Once a particle reaches the floor, the same particle keeps incrementing `floorMap[fi] += 0.05` on later frames while remaining in the simulation. The pile therefore grows without new snow mass. The particle→surface-field coupling is valuable; the accumulation rule is not conservative.

### 098 `balloon-regatta` — claimed wind interpolation does not interpolate

`windAt()` says it interpolates between altitude lanes, but the returned expression multiplies the neighboring lane by `0.0`. It simply selects a lane. The heat→vertical-velocity model is also an authored control heuristic, not thermodynamic buoyancy.

### 099 `antikythera-gears` — 'ratio-correct' is overstated

Awakened angular speed is scaled roughly as `48 / teeth`, but all gears rotate in the same direction and there are no pairwise mesh/phase/contact constraints. Useful assembly and gear-geometry donor; not a mechanically correct gear train.

## Primitive families

- **Persistent growth / living structure:** 007, 019, 027, 042, 066
- **Agents / entity behavior:** 019, 051, 076
- **Mechanics / oscillators / particles:** 011, 030, 037, 061, 096, 098, 099
- **World-state coupling / process systems:** 023, 042, 047, 067, 070, 076, 078, 095, 096, 098
- **Procedural geometry / authoring:** 007, 014, 028, 032, 046, 048, 059, 066, 068, 071, 077, 081, 084, 087, 092, 099, 100
- **Audio / signal:** 010, 025, 043, 055, 064, 080, 089
- **Astronomy / time / projection:** 004, 008, 014, 017, 049, 071, 086, 091, 094
- **Flow / environment visuals:** 005, 021, 027, 053, 063, 073, 076, 088
- **Rule / parser / discrete state:** 029, 034, 036, 043, 095

## Most SHADED-relevant takeaways

1. **Your irritation was justified:** this second GLM 5.3 set is materially richer in reusable systems even though it is not larger by raw JS or prompt length.
2. **042 is the architectural standout.** Pruning/wiring changes persistent branch state, and later growth uses that modified state. That is exactly the kind of consequence chain SHADED wants.
3. **086 is the clean mathematical standout.** It is one of the rare pages whose physical/astronomical title is substantially backed by actual equations.
4. **Several visually impressive systems are still wrong under the hood.** The tectonic transform, snow accumulation, marbling seam and balloon interpolation prove that longer/more polished pages still require state-update auditing.
5. **The collection adds more authoring primitives than solver primitives.** Ceramic profiles, lace topology, rule-based composition and botanical manipulation are stronger additions than its fluid/tectonic/thermodynamic claims.
6. **Independent overlaps remain useful for falsification, not as oracles.** Audio, harmonograph, flow field, plant branching and projection should be cross-checked against independent references before promotion.

## Verification policy

1. Page title/prompt is metadata, never evidence.
2. Extract the actual computational kernel and state its real contract.
3. Check coordinate frames, initialization, buffer/state updates, conservation, force accumulation, topology and comment-vs-code consistency.
4. Mark visual approximations, synthetic data and impossible/buggy state paths explicitly.
5. Deduplicate by primitive family, not page theme.
6. Validate equations/units/invariants independently before promotion into SHADED.
7. For ports/regressions, use independent black-box scenes/metrics; never use the generated demo as its own golden oracle.

## Full inventory

See [`GLM_5_3_OX_ALPHA_100_INVENTORY.md`](GLM_5_3_OX_ALPHA_100_INVENTORY.md) for the complete 100/100 classification.