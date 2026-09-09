# SHADED OCEAN HANDOFF

**Purpose:** compact build handoff for Astra/other coding agents. This file exists so the next agent does **not** repeat broad donor discovery. Use the verified findings below as the starting point, then inspect only the SHADED files actually needed for implementation.

## Build target

Create the smallest integrated SHADED ocean slice proving:

**A rock. A shore. Water. Throw the rock. The world reacts.**

The point is not a pretty water demo. The point is a world-state contract:

`world object -> water impact -> simulated state change -> propagated response -> persistent consequences`

## Recommended architecture

Use a hybrid surface:

- **Far ocean:** cheap analytic multi-wave/Gerstner-style representation.
- **Near interaction zone:** local interactive heightfield / wave field with ping-pong state.
- **World coupling:** explicit world->water coordinate mapping and impulse injection.
- **Surface state:** foam / floating material should be derived from or coupled to simulation state, not independent decoration.
- **Underwater:** same water boundary viewed from the opposite side; no separate fake scene.

This is an architectural recommendation from the donor audit, not a demand to overwrite an existing better SHADED subsystem.

## Water / field donors already audited

### Fable 5.1
Catalog: `generated-site-donors/FABLE_5_1_100.md`

- **016 `fluid-smoke-touch` — A+**
  - Jos Stam-style Stable Fluids.
  - Diffusion, Gauss-Seidel, pressure projection, semi-Lagrangian advection.
  - Best used as a compact independent CPU/reference solver family, not necessarily as the production ocean surface.

- **052 `rain-on-window` — A+**
  - Surface-bound droplet transport.
  - Gravity/terminal velocity/accretion/coalescence/trails/lens rendering.
  - Relevant to binding material to a surface and to persistent wetness-like state.

- **082 `prism-light-dispersion` — A+**
  - Vector Snell refraction/reflection/TIR + wavelength-dependent refractive index.
  - Use as an optics reference for water-interface refraction ideas; do not substitute authored fake prism demos from other sets.

- **099 `water-ripple-reflection` — A+**
  - Discrete ripple/wave heightfield.
  - Ping-pong state + damping + reflection sampling.
  - Strong simple reference for near-field interactive water.

- **090 `bioluminescent-deep-sea` — A+**
  - Verlet + iterative distance constraints + root pinning.
  - Useful for underwater ropes, algae, kelp-like strands, cables or soft appendages; not a water solver.

### DeepSeek v4 x100
Catalog: `generated-site-donors/DEEPSEEK_V4_FLASH_100.md`

- **050 `cursor-ripple` — A+**
  - Independent discrete ripple/wave heightfield overlap with Fable 099.

- **066 `marble-ink` — A+**
  - Differential comb-shear material transform + curl advection.
  - Useful as a material-space / surface-bound transport reference.

- **075 `ant-colony` — A+** and **089 `slime-mold` — A+**
  - Strong agent<->field feedback examples.
  - Not ocean algorithms, but useful examples of entities reading and modifying persistent fields.

- **080 `dune-wind` — A**
  - Explicit particles + mutable heightfield + erosion/deposition architecture.
  - Important caveat: the audited version is **not mass-conserving** and can create material. Do not copy its conservation logic.

### Qwen 3.8 27B
Catalog: `generated-site-donors/QWEN_3_8_27B_100.md`

- **005 `tideglass-water` — A+**
  - Classic discrete ripple heightfield with ping-pong buffers and damping.
  - Good independent reference against Fable 099 / DeepSeek 050.

- **024 `rain-glass` — A**
  - Droplet growth/sliding/trails + per-drop lens distortion.
  - Weaker physically than Fable 052, but useful independent render/surface reference.

- **069 `leaf-storm` — A**
  - Particle -> persistent surface-height accumulation.
  - Conceptually important for SHADED: particles do not merely disappear; landed material modifies a persistent world field.

- **092 `wave-tank`** and **081 `paper-boat`**
  - **Do not treat as water PDE solvers.** They use prescribed analytic waves / Gaussian impulses.

### Qwen 3.8 Max
Catalog: `generated-site-donors/QWEN_3_8_MAX_100.md`

- **059 `waves-interference` — A+**
  - Real radial wave-source superposition field sampled over cells.
  - Useful for field composition and testing, not necessarily a production ocean solver.

- **085 `sandbox-particles` — A+**
  - Real cellular falling-sand solver.
  - Relevant to beach/sediment/discrete material interaction, not water itself.

### GLM 5.3 / Ox special water benchmark
Source was separately audited from `Water-Ripple-Prompt-GLM-5.3-DS4F-Qwen3.8-27b-main.zip`.

- **GLM 5.3 water implementation**
  - 512x512 GPU heightfield.
  - Three ping-pong render targets.
  - Fixed 120 Hz simulation step.
  - This is the most directly relevant generated-site backend/architecture reference for a GPU near-water heightfield.
  - Treat it as algorithmic/reference inspiration, not as a golden oracle.

- **Qwen 27B water implementation from the same shootout**
  - 513x513 CPU grid + Three.js/PBR.
  - Algorithmically overlaps the same classic discrete ripple/wave family as Qwen 005 / DeepSeek 050.

- **DeepSeek v4 water implementation from the same shootout**
  - Analytic sine waves + Gaussian ripple rings in the vertex shader.
  - Useful rendering comparison, **not** a real field solver.

### Fable high-effort `Synesthesia`
Source was separately audited from the high-effort Fable collection.

- GPU/WebGL2 Stable-Fluids-style pipeline.
- Advection -> divergence -> pressure Jacobi -> gradient subtraction -> vorticity confinement -> dye + bloom.
- Strong production-style GPU fluid pipeline reference.
- MIT licensed in the audited source.
- Use for GPU field architecture and backend comparison; do not assume it is the right direct ocean surface model.

## Useful optics / representation references

- Fable 082 is the strongest audited physical refraction donor.
- Ox/GLM AETHER catalog: `generated-site-donors/OX_ALPHA_GLM_5_3_AETHER.md`
  - Useful GPU distance-field / procedural rendering reference, not water physics.
- Qwen Max 089 gives a CPU SDF sphere-tracing reference, useful for CPU-vs-GPU black-box comparison patterns.

## Known false friends to avoid

Do **not** spend time rediscovering or promoting these as real water/optics solvers:

- Qwen Max 081 `fluid-simulation`: trigonometric angle field + particle advection, no pressure projection / Navier-Stokes.
- Qwen 27B 041 `prism-spectrum`: authored band fan, no Snell/IOR.
- Qwen 27B 066 `caustic-garden`: animated gradients/rings, no ray focusing.
- Qwen 27B 073 `interference`: additive circles, not sampled wave superposition.
- GLM 5.2 070 `glass-prism`: authored angle offset, no physical refraction.
- GLM 5.2 082 `caustic`: straight colored rays, no caustic computation.
- Grok 4.5 064 `water-ripple`: independent expanding rings, no spatial wave state.
- Grok 4.5 072 `crystal-prism`: CSS transforms, no optics.
- GLM/Ox `quantum-garden-cfd`: curl-noise particle advection, not CFD.

## Suggested first implementation contract

A minimal useful near-water state should expose approximately:

- `height`
- `previousHeight` or velocity-equivalent state
- `impulse(x,z,strength,radius)`
- fixed-step update
- damping
- world<->field coordinate mapping
- sample height / normal
- optional derived `energy` channel for foam

Then prove:

1. zero state stays approximately zero;
2. a centered impulse propagates outward;
3. centered symmetric input stays symmetric within tolerance;
4. damping reduces total disturbance;
5. no NaN/Infinity over long runs;
6. world->water coordinate mapping is deterministic;
7. a real rock impact changes the actual field;
8. no rock impact means no impact wave;
9. the rock persists after entry;
10. shoreline and water share the same world coordinates.

## Scope guidance

For the first slice, **do not** build tides, global currents, boats, weather, full erosion, marine ecology or infinite streaming.

The correct first proof is:

**rock + shore + far ocean + local interactive water + one persistent surface consequence.**

## Validation rule

Generated donors are references, not oracles. For ports/regressions, use independent black-box invariants and compare coarse measurable behavior across CPU/WebGL/WebGPU implementations where possible.

Never build a test from the current implementation and then claim the implementation is correct because it passes its own assumptions.
