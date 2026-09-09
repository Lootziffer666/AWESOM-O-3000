# OX ALPHA / GLM 5.3 — AETHER COMPOUND DONOR CATALOG

**Status:** complete static pass over the supplied archive. The archive contains one substantive generated page, `index.html`, plus `README.md`. No title-only sampling.

The page is treated as a **compound micro-donor** and decomposed into reusable computational primitives rather than counted as one feature. `index.html` is 6,527,542 characters; about 6,495,644 characters are an embedded Base64 MP3, leaving roughly 31.9k characters of HTML/CSS/JS implementation.

No license file is present in the supplied archive, so the safe default is **reference / algorithm / equation / test inspiration**, not direct code copying.

## Overall assessment

**Page:** `AETHER — a cathedral of pure mathematics`  
**Overall grade:** **A+** as a compact GPU fractal / distance-field rendering compound donor.  
**Physics/chemistry:** not applicable; this is a mathematical/rendering donor.

The core path is:

`fullscreen triangle → camera ray → fractal distance estimator → sphere tracing → finite-difference normal → AO + soft shadow + orbit-trap material → sky/dust → tone map`

Five authored forms are exposed:

1. Mandelbulb
2. Menger Cathedral
3. Sierpinski Flame
4. Trinity Bulb
5. Urchin

Only the first three are distinct canonical-ish fractal/decomposition families. `Trinity Bulb` is a Mandelbulb distance modified by a sinusoidal y-dependent multiplier, and `Urchin` is a twisted power-12 Mandelbulb variant.

## Strong new primitives vs. Fable 5.1 + GPT-6 Astra + DeepSeek v4 Flash + Qwen 3.8 Max + Muse Spark 1.3

| Primitive | Grade | Novelty | What is actually implemented | SHADED relevance |
|---|:---:|---|---|---|
| GPU fractal distance-estimator raymarcher | **A+** | **NEW / stronger than prior CPU SDF donor** | Raw WebGL fragment-shader sphere tracing over Mandelbulb, Menger and Sierpinski distance estimators | Browser-native implicit/fractal geometry, procedural world detail, GPU reference against CPU/WASM/WebGPU ports |
| Mandelbulb distance estimator + orbit trap | **A+** | **NEW** | Polar power iteration, derivative accumulation, logarithmic distance estimate and orbit-trap minimum | Fractal volumetrics/surfaces, procedural micro/macro geometry, material coordinates |
| Menger-sponge distance estimator | **A** | **NEW** | Iterated scale-3 box-space construction with repeated coordinate folding | Architectural/cathedral-like procedural void/solid structures |
| Sierpinski tetrahedral fold estimator | **A** | **NEW** | Repeated symmetric plane folds + scale-2 transform + bounded distance estimate | Recursive structural geometry / procedural fracture-like motifs |
| Cross-DE transmutation | **A** | **NEW, with caveat** | Evaluates two live geometry fields and blends their distances/traps during a seven-second morph | State-to-state world/material morphing and transitions between implicit representations |
| DE-based soft shadow + ambient occlusion | **A** | **PARTIAL NEW** | Secondary distance-estimator marching toward a key light plus normal-offset AO probes | Lightweight implicit-scene lighting reference |
| Orbit-trap-driven material mapping | **A** | **NEW** | Fractal orbit-trap value drives indigo→violet→gold material interpolation | Geometry-derived material classification without UVs |
| Distance-adaptive hit epsilon / normal epsilon | **A-** | **NEW compact reference** | Hit threshold and finite-difference normal epsilon increase with march distance | Stabilizes raymarched detail across depth |
| Hard render-pixel budget + software-rasterizer detection | **A-** | **NEW infrastructure pattern** | DPR/scale capped by MAXPX; renderer string checks SwiftShader/software/llvmpipe and lowers resolution | “AAA on toaster” browser safety / graceful quality budgeting |
| Fullscreen-triangle WebGL path | **A-** | overlap | One oversized triangle drives the entire fragment shader | Minimal dependency-free GPU pass |
| Procedural sky + in-ray atmospheric motes | **B** | visual | Hash/noise star layers plus 26 procedural dust samples along the camera ray | Cheap atmosphere / environmental storytelling |
| Inertial orbit camera + idle attractor | **B** | overlap | Pointer velocity, exponential damping, zoom, scripted opening and idle rotation | Presentation/camera donor |

## Computational decomposition

### 1. Mandelbulb DE — **A+**

The shader iterates a 3D power map and tracks both radius and derivative:

- spherical conversion from the current `z`
- angular multiplication by power `pw`
- radial power `r^pw`
- derivative accumulation `dr = r^(pw-1) * pw * dr + 1`
- bailout around `r > 2.6`
- logarithmic distance estimate approximately `0.25 * log(r) * r / dr`
- orbit trap stores the minimum radius encountered

The primary form uses power 8. `Urchin` uses a twisted coordinate field and power 12.

**Donor claim:** strong compact Mandelbulb distance-estimator reference. Constants and safety factors are authored and should be independently validated before using them as a numerical oracle.

### 2. Menger construction — **A**

A box SDF is repeatedly transformed into scale-3 local cells. The code derives three cross-removal distances and keeps the maximum with the existing field, producing a Menger-sponge-like cathedral.

**SHADED translation:** a tiny procedural solid/void grammar that can generate repeated architectural negative space without storing explicit geometry.

### 3. Sierpinski construction — **A**

The position undergoes repeated symmetric coordinate folds, then `p = p*2 - 1`. After ten iterations, the code converts the transformed position back into a bounded distance estimate.

**SHADED translation:** recursive fold-space geometry; useful as an implicit procedural structure rather than as a mesh asset.

### 4. Cross-form transmutation — **A, heuristic**

Both source and destination fields are evaluated simultaneously and blended with eased `mix()`. Around the middle of the transition, the distance is scaled down by an envelope factor to reduce unsafe marching.

The comment claims this keeps the gradient below roughly one. That is **not proven by the implementation**. Linear blending of distance estimators generally does not preserve an exact signed-distance property.

**Donor claim:** excellent visual/architectural morphing pattern, but it is a stability heuristic rather than a mathematically guaranteed SDF blend.

### 5. Raymarch + shading — **A+ as a compact integrated reference**

- up to 110 primary steps
- conservative step scale (`distance * 0.85`)
- distance-adaptive hit threshold
- finite-difference normals
- three AO probes along the surface normal
- up to 24 soft-shadow DE samples toward the warm key light
- two directional lights
- Blinn-like specular
- Fresnel-like rim term
- distance fog
- glow accumulated from proximity to the field
- ACES-like tone mapping and gamma

This is materially richer than Qwen's earlier CPU SDF sphere tracer because the entire implicit/fractal scene is rendered directly in the fragment shader.

## Important caveats / false friends

### Broken GPU-stall watchdog

The frame delta is clamped before the watchdog sees it:

`dt = min(0.05, realFrameDelta)`

The smoothed `dts` is then tested against:

`dts > 0.5`

That condition is unreachable because `dts` cannot rise anywhere near 0.5 seconds. The comment says the watchdog will shed resolution after GPU stalls, but that mechanism as written **cannot trigger**.

The separate hard pixel ceiling and software-renderer scaling are real and useful.

### “Trinity Bulb” is not a separate fractal solver

It calls the Mandelbulb estimator and multiplies its returned distance by:

`1 + 0.35 * sin(p.y * 3.1)`

That is a stylized deformation of the DE, not a distinct mathematically established fractal family.

### “Urchin” is also a Mandelbulb variant

The input coordinates are twisted as a function of radius, then a power-12 Mandelbulb DE is evaluated and rescaled. Useful visual donor, not a separate solver family.

### Morph safety is heuristic

The comment says the blend rescaling keeps gradients safe, but no bound is derived or checked. Treat the morph as a visual technique that needs independent step-safety testing.

### Fixed iteration reporting

The HUD reports 11 iterations and the uniform is always set to 11. This is not a dynamically adapted quality parameter despite the broader adaptive-resolution machinery.

## Most SHADED-relevant takeaways

- **This is the strongest generated-site donor so far for browser-native implicit/fractal rendering.**
- It complements Qwen 089 perfectly: Qwen gives a **CPU SDF black-box reference**, while AETHER gives a **GPU fractal-DE reference**.
- Orbit traps are especially valuable because they provide **material coordinates derived from procedural geometry itself**, without UV unwraps.
- The cross-DE morph pattern is directly relevant to SHADED's stored-form/material-reassembly ideas, but it should be treated as a visual morphing primitive until independently tested for conservative marching.
- The Menger and Sierpinski fields are useful not merely as “fractals”, but as compact **recursive structure generators**.
- The software-renderer detection + hard pixel budget is good browser survivability infrastructure even though the explicit stall watchdog is dead code.

## Verification policy

1. Generated page title/prompt is metadata, never evidence.
2. Extract the computational kernel and state its actual contract.
3. Mark authored approximations and impossible/dead control paths explicitly.
4. Deduplicate by primitive family, not by page theme.
5. Validate distance bounds, gradients, iteration constants and invariants independently before promotion into SHADED.
6. For ports/regressions, use independent black-box scenes/metrics; never use the generated implementation as its own golden oracle.
