# DEEPSEEK V4 FLASH 0731 — SINGULARITY DONOR CATALOG

**Status:** complete static pass over the supplied archive. The archive contains one substantive file: `index.html` (3,124,821 bytes / 1,037 lines), plus an empty `.gitignore`. No title-only sampling.

The page is treated as a **compound micro-donor** and decomposed into reusable computational primitives rather than counted as a single feature. Roughly 3.08M of the 3.12M characters are an embedded Base64 audio track; the actual HTML/CSS/JS implementation is ~49.4k characters.

## Overall assessment

**Page:** `SINGULARITY — 3D AUDIO VISUALIZER`  
**Overall grade:** **A** as a compact GPU/signal-processing compound donor; **C** for physics/chemistry (none present).

The strongest value is not physical simulation. It is the integration path:

`WebAudio FFT → band aggregation → adaptive beat detection → audio-reactive state → raw WebGL2 geometry/shaders → multi-pass post FX → temporal feedback`

## Strong new primitives vs. Fable 5.1 + GPT-6 Astra

| Primitive | Grade | Novelty | What is actually implemented | SHADED relevance |
|---|:---:|---|---|---|
| Adaptive audio beat detector | **A+** | **NEW / stronger than prior audio donors** | `AnalyserNode` FFT, bass/mid/high aggregation, weighted energy, adaptive decaying threshold, cooldown, kick pulse | Audio/event-driven world impulses, music-reactive material/light/particle systems |
| Temporal feedback post-processing | **A+** | **NEW** | Scene + bloom + previous-frame FBO ping-pong with adjustable trail persistence | Motion persistence, energy trails, ghosting, temporal stylization |
| Compact bloom pipeline | **A** | **NEW as a complete pipeline** | Bright-pass threshold → separable horizontal/vertical Gaussian-like blur → additive composite | Lightweight browser bloom / emissive-material pass |
| GPU point-cloud morphology | **A** | **NEW** | 9,000 particles carry two 3D source positions (sphere/disc); vertex shader interpolates topology with `mix()` and applies audio-driven deformation | Morphing material distributions, portal assembly, phase/state transitions |
| Procedural icosphere subdivision | **A** | **NEW** | Icosahedron seed, cached edge midpoints, repeated triangle subdivision, projection to unit sphere | Compact procedural sphere/planet/collision proxy/field sampling geometry |
| Audio-reactive dynamic spectrum mesh | **A-** | partial overlap | 64 FFT buckets mapped to dynamic radial bar geometry rebuilt each frame | Field/debug visualizers, radial energy displays |
| Manual matrix/camera stack | **A-** | overlap | Perspective matrix, look-at matrix, VP multiplication, smoothed orbital camera | Small dependency-free WebGL reference |
| Camera-facing shockwave billboard concept | **B** | partial/new | Ring geometry oriented using camera `right/up`; radius/alpha evolve over lifetime | Impact/shockwave rendering concept; implementation has a geometry caveat below |
| Section-driven visual state machine | **B** | new orchestration pattern | Track bar ranges drive DROP/BREAKDOWN behavior, shape blend, spin and camera response | High-level scene choreography / authored event layers |

## Computational decomposition

### 1. WebAudio analysis — **A+**

- `AudioContext` + decoded embedded track
- `AnalyserNode` with FFT size 2048
- FFT split into bass / mid / high bands
- weighted energy: approximately `0.55*bass + 0.30*mid + 0.15*high`
- 64 max-pooled spectrum buckets with temporal smoothing
- adaptive beat threshold that decays toward a floor
- beat cooldown to avoid immediate retriggering
- beat event emits a visual impulse (`kickPulse`) and ring spawn

**Donor claim:** useful as an event extraction primitive, not as a musically rigorous onset detector. The fixed bin ranges are index-based rather than frequency-Hz calibrated, so reuse should map bins through sample rate / FFT size first.

### 2. Multi-pass post-processing — **A+**

Pipeline:

1. render scene into offscreen FBO
2. bright-pass threshold extraction
3. horizontal blur
4. vertical blur
5. composite scene + bloom + previous-frame feedback
6. chromatic aberration
7. vignette
8. scanline modulation
9. noise/grain
10. write into ping-pong feedback target and copy to screen

**Donor claim:** strong compact reference for browser-native bloom + temporal persistence without external libraries.

### 3. GPU point-set morphing — **A**

Each particle stores:

- spherical position
- disc position
- random seed
- point size

The vertex shader uses `mix(aSph, aDisc, uShape)` and then applies independent orbital rotation, global spin, tilt, bass-driven radial push and high-frequency wobble.

**SHADED translation:** the important primitive is not “audio particles”; it is **one material population carrying multiple target configurations and transitioning entirely on GPU**.

### 4. Procedural icosphere — **A**

- normalized icosahedron seed vertices
- triangular face list
- midpoint cache per edge
- four subdivision rounds
- midpoint normalization back to unit sphere
- direct vertex normals from normalized positions

This is a clean dependency-free geometry primitive.

### 5. Dynamic radial spectrum mesh — **A-**

64 spectrum values become vertical quads placed around a ring. Height follows a nonlinear spectrum mapping (`spect^1.6`), while colour interpolates across the theme. Geometry is rewritten into a dynamic buffer each frame.

### 6. Camera / matrices — **A-**

The file implements its own:

- perspective projection
- look-at view matrix
- view-projection multiply
- orbital camera controls
- eased target yaw/pitch/distance
- section/energy-driven automatic camera behavior

Useful as a compact raw-WebGL reference, but not novel relative to existing projection donors.

## False-friend / correctness warnings

### “Procedural full-length track” is false

A header comment calls the audio a procedural full-length EDM/dubstep track, but the actual audio block identifies an embedded pre-existing track: **“Vlog Beat Background” by Tunetank**, with a Pixabay Content License reference. Treat the audio as an embedded asset, not generated DSP output.

### WebGL1 fallback is not real

Initialization asks for `webgl2` and then falls back to `webgl`, but the shaders use GLSL ES 3.00 syntax (`#version 300 es`, `layout`, fragment `out`, `texture`) and the implementation calls WebGL2 VAO APIs such as `createVertexArray()`. Therefore the apparent WebGL1 fallback is not a functional backend.

**Donor rule:** classify this as **WebGL2-only** unless independently ported.

### Shockwave ring geometry likely degenerates

The ring buffer stores paired vertices with identical XY positions and only varies an “edge” scalar. The vertex shader does not offset inner vs. outer radius, so the triangle strip can collapse to zero-area triangles. Preserve the billboard/orientation idea, but rebuild the annulus geometry before reuse.

### Beat detection is heuristic

The adaptive bass threshold is useful and compact, but it is not a robust spectral-flux/onset detector. It should be tested against independent audio fixtures before becoming a general SHADED event detector.

### No physics / chemistry solver

Despite the “Singularity”, “shockwave”, particle and deformation presentation, the page contains no gravity solver, fluid solver, wave PDE, field physics, relativity, or black-hole simulation. Those names are visual metaphors only.

## Overlap with existing generated-site donor catalog

### Already substantially covered by Fable/Astra

- WebAudio fundamentals / analysers / filters: Fable 032, 042, 089
- procedural particle rendering: many Fable/Astra pages
- perspective/view transforms: Fable 072, 097; Astra 064
- additive visual effects / pulses: partial overlap

### Worth adding as distinct primitives

- **adaptive beat threshold + cooldown event extractor**
- **previous-frame FBO temporal feedback**
- **bright-pass + separable blur + bloom composite as one compact raw-WebGL pipeline**
- **dual-position GPU particle morphing**
- **dependency-free icosphere subdivision**

## Licensing / provenance

The supplied ZIP contains no repository `LICENSE` file. Therefore the HTML/JS/GLSL should remain **reference / algorithm / equation / test inspiration** until provenance and code licensing are independently established.

The embedded audio is separately identified in source as a Tunetank track under the Pixabay Content License. Its presence does **not** establish a license for the surrounding source code.

## SHADED promotion recommendation

**PROMOTE AS CANDIDATE PRIMITIVES:**

1. `AUDIO_EVENT_ADAPTIVE_BEAT`
2. `POSTFX_TEMPORAL_FEEDBACK`
3. `POSTFX_BLOOM_SEPARABLE`
4. `PARTICLE_DUAL_TARGET_GPU_MORPH`
5. `GEOMETRY_ICOSPHERE_SUBDIVISION`

**KEEP AS REFERENCE ONLY:** radial FFT bars, camera choreography, shockwave billboard.

**REJECT AS CLAIMS:** procedural music, WebGL1 fallback, any physical “singularity” or shockwave simulation claim.

## Verification gates before SHADED use

- Beat detector: evaluate precision/recall against independent onset-labelled audio samples; do not derive fixtures from this implementation.
- Bloom/feedback: compare against independent golden frames and test energy blow-up / persistence decay.
- GPU morph: verify bounded positions and deterministic endpoint equivalence at `uShape=0` and `1`.
- Icosphere: verify expected face/vertex counts, unit-radius error, winding and manifold edge incidence.
- WebGL backend: explicitly require WebGL2 or port shaders/API calls before claiming fallback support.
