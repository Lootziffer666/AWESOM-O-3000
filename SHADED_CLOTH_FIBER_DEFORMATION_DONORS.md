# SHADED Cloth / Fiber / Deformation Donors — Functional Classification

> **Rule:** classify repositories by the transformation they actually provide, not by words such as *cloth*, *fur*, *hair* or *shader* in the repository name.
>
> This batch spans deformable-surface simulation, collision, woven-material scattering, hair/fiber scattering, deep shadowing, real-time fur approximations, analytical deformation, secondary motion, shader primitives, interaction effects, and research/mining sources.

## Executive map

| Repository | Actual function | SHADED role / operator class | Value |
|---|---|---|---|
| [nakjun/Cloth-Simulation-WebGPU](https://github.com/nakjun/Cloth-Simulation-WebGPU) | WebGPU mass-spring simulation + BVH broad phase + triangle/triangle collision + response | **Deformable Surface Solver / Collision** | **S+** |
| [ThunderLoom/ThunderLoom](https://github.com/ThunderLoom/ThunderLoom) | Physically based woven-cloth shading using weave structure / WIF patterns | **Woven Material / Fiber Microstructure BSDF** | **S+** |
| [dsforza96/yocto-hair](https://github.com/dsforza96/yocto-hair) | PBRT-style physically based hair scattering with absorption, roughness, IOR and melanin pigments | **Fiber Scattering / Hair BSDF** | **S+** |
| [ecidevilin/DeepShadowMap](https://github.com/ecidevilin/DeepShadowMap) | Real-time Deep Shadow Maps implementation | **Fiber / Hair / Semi-transparent Shadowing** | **S** |
| [redcool/PowerFur](https://github.com/redcool/PowerFur) | Shell/fin fur with GPU-instanced and multipass paths, wind, flow, AO and lighting | **Realtime Fur Approximation / Runtime LOD** | **S** |
| [gam0022/unity-shader-experiments](https://github.com/gam0022/unity-shader-experiments) | Cheap procedural cloth sway with analytically derived normals; also other shader experiments | **Analytical Deformation / Cheap Surface Motion** | **A+** |
| [dmitrykurash/holocloth](https://github.com/dmitrykurash/holocloth) | Browser cloth physics via Verlet + structural/shear/bend constraints, interaction and material stack | **Browser Cloth Integration Donor** | **A+** |
| [Jedzia/alShaders](https://github.com/Jedzia/alShaders) | Arnold shader-node library including hair/scattering, Fresnel, flakes, curvature, layering etc. | **Shader / Scattering Donor Cluster** | **A+ / S−** |
| [kseniya7991/fur-shader](https://github.com/kseniya7991/fur-shader) | Fur-like surface built from procedural grass/blade geometry with height variation, waves and mouse blow | **Cheap Geometric Fur / Fiber LOD** | **A** |
| [cullenwebber/three-clothing](https://github.com/cullenwebber/three-clothing) | Spring-damped bone-chain secondary motion driven by movement velocity | **Secondary Motion Chain** | **A−** |
| [steaklive/CgFX-Shader-Compilation](https://github.com/steaklive/CgFX-Shader-Compilation) | Collection of material/shader techniques: Oren-Nayar, SSS, shell fur, snow, tessellation deformation etc. | **Shader Primitive Cookbook** | **A−** |
| [chengkehan/chengkehan.github.io](https://github.com/chengkehan/chengkehan.github.io) | Large technical notebook / demo archive for rendering and shaders, including anisotropic hair lighting | **Research Router / Shader Mining Source** | **A as miner** |
| [beto-group/TornCloth](https://github.com/beto-group/TornCloth) | Interactive Three.js/WebGL cloth presentation with wind, media mapping and torn-edge visual controls | **Cloth Presentation / Tear Visual FX** | **B+ / A−** |
| [Manishbhai9350/Chipsa---Stone-Animation](https://github.com/Manishbhai9350/Chipsa---Stone-Animation) | Pointer/raycast-driven mesh-part displacement, lerped recovery and stone↔cloth presentation transition | **Interactive Mesh Decomposition / Proximity Deform** | **B+** |

**Duplicate in source batch:** `steaklive/CgFX-Shader-Compilation` was supplied twice; it is recorded once here.

---

# 1. Cloth-Simulation-WebGPU — GPU deformable-surface solver

Repository: https://github.com/nakjun/Cloth-Simulation-WebGPU

The repository describes a **real-time mass-spring simulation system using WebGPU**.

### Verified functional pieces

- spring-centric mass-spring simulation;
- WebGPU rendering / browser execution;
- collision detection with **AABB-based BVH broad phase**;
- **triangle-triangle intersection** narrow phase;
- triangle-based collision response;
- test meshes ranging from small sphere geometry to tens of thousands of vertices / up to roughly 100K triangle faces;
- self-collision is explicitly *not* included in the stated mass-spring feature set.

### SHADED interpretation

**Operator class:** `DEFORMABLE_SURFACE_SOLVER / CLOTH_GPU`

```text
MESH
  ↓
SPRING CONSTRAINTS
  ↓
GPU INTEGRATION
  ↓
BVH BROAD PHASE
  ↓
TRIANGLE / TRIANGLE NARROW PHASE
  ↓
COLLISION RESPONSE
  ↓
DEFORMED MESH
```

The collision pipeline is not inherently cloth-specific. It is potentially reusable for other deformable meshes, membranes and dynamic surfaces.

### High-value extraction targets

- GPU data layout for spring systems;
- constraint/integration scheduling;
- BVH construction / traversal strategy;
- tri/tri intersection path;
- collision response;
- performance behavior at increasing mesh density.

---

# 2. ThunderLoom — cloth appearance from actual weave structure

Repository: https://github.com/ThunderLoom/ThunderLoom

ThunderLoom is not a cloth-motion simulator. It addresses the other half of cloth: **how woven structure reflects light**.

### Verified architecture

- implementation of the **Irawan** woven-cloth shading model;
- core shading implementation wrapped in a reusable library/API;
- weave patterns described using standard **WIF weaving drafts**;
- frontends/plugins historically provided for renderers such as V-Ray and Mitsuba;
- separate pattern-editing workflow;
- MIT license stated in the repository README.

### SHADED interpretation

**Operator class:** `WOVEN MATERIAL / STRUCTURED FIBER BSDF`

```text
WARP YARN
+
WEFT YARN
+
WEAVE PATTERN
+
FIBER / MATERIAL PARAMETERS
+
LIGHT
       ↓
WOVEN-CLOTH SCATTERING
       ↓
APPEARANCE
```

The important abstraction is that **cloth is not merely a texture**. Its microstructure is structured data that drives appearance.

### Pairing with Cloth-Simulation-WebGPU

```text
Cloth-Simulation-WebGPU
GEOMETRY → MOTION

ThunderLoom
MICROSTRUCTURE → LIGHT
```

Together these represent two orthogonal parts of a physically meaningful cloth system.

---

# 3. yocto-hair — physically based fiber scattering

Repository: https://github.com/dsforza96/yocto-hair

Yocto/Hair extends Yocto/GL with a realistic hair shading model following the PBRT hair implementation.

### Verified material parameters

- `sigma_a` — absorption coefficient;
- `beta_m` — longitudinal roughness;
- `beta_n` — azimuthal roughness;
- `alpha` — hair scale angle;
- `eta` — internal index of refraction;
- `eumelanin` concentration;
- `pheomelanin` concentration.

Hair color can be specified by direct color, absorption, or pigment concentrations. The implementation includes evaluation, sampling and PDF routines for the hair scattering distribution, and the repository states energy-conservation / sampling tests derived from the PBRT treatment.

### SHADED interpretation

Do not store this merely as `HAIR_SHADER`.

**Operator class:** `FIBER_SCATTERING / BSDF`

```text
FIBER TANGENT
+ WIDTH / RADIUS
+ ABSORPTION / MELANIN
+ LONGITUDINAL ROUGHNESS
+ AZIMUTHAL ROUGHNESS
+ SCALE ANGLE
+ IOR
       ↓
FIBER SCATTERING
       ↓
REFLECTED / TRANSMITTED LIGHT
```

The abstraction is useful beyond human hair: oriented thin fibers are also relevant to fur, some textiles and other filament-like materials.

### High-quality reference role

This is a **quality/reference path**, not necessarily the runtime implementation for every browser target.

---

# 4. DeepShadowMap — attenuation through many thin layers

Repository: https://github.com/ecidevilin/DeepShadowMap

The project explicitly references **Real-Time Deep Shadow Maps** from GPU Pro 4.

### SHADED interpretation

**Operator class:** `DEPTH-DEPENDENT TRANSMITTANCE / FIBER SHADOWING`

Ordinary binary depth shadows are a poor fit for dense populations of thin or partially covering elements. The useful abstraction is cumulative attenuation along the light direction:

```text
LIGHT
  ↓ fiber layer
TRANSMITTANCE_1
  ↓ fiber layer
TRANSMITTANCE_2
  ↓ ...
DEPTH-DEPENDENT ATTENUATION
```

### Natural pairing

```text
yocto-hair
  → how an individual fiber scatters light

DeepShadowMap
  → how a population of fibers attenuates light through depth
```

This is valuable for hair/fur but the underlying transmittance concept is broader than either material.

---

# 5. PowerFur — pragmatic real-time fur path

Repository: https://github.com/redcool/PowerFur

PowerFur is a layered **shell/fin-based fur renderer** with practical runtime implementation paths.

### Verified features

- GPU-instanced single-pass fur path;
- multi-pass path for skinned meshes;
- multiple shell offsets from the base surface;
- fur mask channels for alpha noise, vertex-offset attenuation and AO;
- normal-direction fur length / offset;
- gravity droop / rigidity controls;
- wind;
- flow-map UV offset;
- alpha edge handling;
- lighting with metallic/roughness controls and specular model;
- vertex/fragment AO;
- rim and fog;
- ShadowCaster path;
- shared HLSL helpers / BSDF distributions.

### SHADED interpretation

**Operator class:** `REALTIME FUR APPROXIMATION / RUNTIME LOD`

```text
BASE MESH
  × N SHELLS
  ↓ offset along normal
ALPHA / DENSITY MASK
  ↓
APPROXIMATE FUR VOLUME
```

This should be treated as a practical middle quality tier rather than a replacement for physically based individual-fiber rendering.

---

# 6. unity-shader-experiments — analytical deformation normals

Repository: https://github.com/gam0022/unity-shader-experiments

The cloth experiment is explicitly designed as a lightweight wind-swaying cloth shader and derives its normals analytically so it can remain cheap enough for mobile-class execution.

### General pattern

```text
KNOWN DEFORMATION f(x,y,t)
          ↓ differentiate
ANALYTICAL SURFACE NORMAL
```

### SHADED interpretation

**Operator class:** `ANALYTICAL DEFORMATION / CHEAP SURFACE MOTION`

The important idea is not the specific flag/cloth effect:

> If the deformation function is known analytically, derive the corresponding normal instead of paying for a more generic reconstruction/simulation path.

Potential applications:

- flags;
- foliage;
- grass;
- paper;
- curtains;
- simple hair/fur motion;
- procedural surface waves.

This is an excellent **cheap-path donor**.

The same repo also contains other shader experiments such as parallax-corrected box-projection cubemaps + lightmaps; mine independently rather than treating the repository as one feature.

---

# 7. holocloth — browser cloth integration donor

Repository: https://github.com/dmitrykurash/holocloth

Holocloth is a browser application that combines cloth physics, user interaction, media mapping and material/postprocessing into one compact system.

### Verified pieces

- custom cloth simulation written from scratch;
- **Verlet integration**;
- structural constraints;
- shear constraints;
- bend constraints;
- grab / pull / throw interaction;
- user image or SVG mapped onto deforming cloth;
- holographic foil shader with diffraction/sparkle/bump treatment;
- chrome / black-cloth presets;
- depth of field;
- ambient occlusion in folds;
- film grain / bloom;
- Three.js + WebGL2 + custom GLSL.

### SHADED interpretation

**Role:** `BROWSER CLOTH INTEGRATION / INTERACTION DONOR`

Its main value is not necessarily being the strongest solver. It demonstrates a compact end-to-end combination:

```text
CLOTH PHYSICS
+
POINTER INTERACTION
+
CONTENT MAPPING
+
MATERIAL SHADING
+
POST FX
       ↓
INTERACTIVE BROWSER MATERIAL EXPERIENCE
```

---

# 8. alShaders — shader/scattering donor cluster

Repository: https://github.com/Jedzia/alShaders

This is not one shader. It is an Arnold shader library (Anders Langlands' alShaders codebase / interpretation) containing many specialized nodes.

### Visible donor nodes include

- `alBlackbody`;
- `alCache`;
- `alCel`;
- `alColorSpace`;
- `alCombine`;
- `alCurvature`;
- `alFlake`;
- `alFresnel`;
- `alHair`;
- `alImage`;
- `alInputVector`;
- `alJitterColor`;
- `alLayer`;
- and more.

`alHair` alone contains substantial dedicated hair implementation plus a separate scattering header.

### SHADED interpretation

**Role:** `SHADER NODE DONOR CLUSTER / RECURSIVE MINING TARGET`

Do not record this as a single `HAIR` feature. Mine it node-by-node and map each meaningful operation into SHADED's operator vocabulary.

### License

The repository README states MIT licensing for alShaders.

---

# 9. fur-shader — very cheap geometric fur / grass path

Repository: https://github.com/kseniya7991/fur-shader

The README explicitly calls it a **Fur (grass shader)** based on a grass shader, with additional geometry/detail controls.

### Verified features

- more vertices for smoother blades;
- adjustable blade height;
- blade-height variation;
- wave size;
- mouse-driven "blow" effect;
- Three.js / GLSL implementation.

### SHADED interpretation

**Operator class:** `PROCEDURAL BLADE GEOMETRY / CHEAP FIBER APPROXIMATION`

This suggests a useful quality ladder:

```text
HIGH
  individual fibers + physical fiber BSDF

MID
  shell / fin fur (PowerFur)

LOW
  procedural blade / grass-like geometry
```

The lower tier can be especially useful at distance, on weak hardware, or for dense surfaces where individual physical fibers are unjustified.

---

# 10. three-clothing — secondary motion, not cloth simulation

Repository: https://github.com/cullenwebber/three-clothing

The repository contains a `WiggleChain` built around a skeleton and spring-damped `WiggleBone`s. External velocity influences the root and the chained bones update with stiffness/damping.

### Functional signature

```text
CHARACTER / ROOT MOTION
        ↓
SPRING-DAMPED BONE CHAIN
        ↓
SECONDARY MOTION
```

### SHADED interpretation

**Operator class:** `SECONDARY_MOTION_CHAIN`

Potential uses:

- coat tails;
- straps;
- belts;
- jewelry;
- braids;
- tails;
- tentacles;
- loose equipment;
- hanging decorative elements.

This should **not** be classified as a general cloth solver.

---

# 11. CgFX-Shader-Compilation — shader primitive cookbook

Repository: https://github.com/steaklive/CgFX-Shader-Compilation

The README lists several independent Unity/CgFX experiments:

- interference shader;
- Oren-Nayar shader;
- simple snow shader;
- fast subsurface scattering;
- intersection outline;
- see-through + rim;
- shell-rendered fur;
- deformable-surface tessellation shader.

### SHADED interpretation

**Role:** `SHADER PRIMITIVE COOKBOOK`

Do not ingest the repository as one feature. Split it into independent candidate operators/material paths and verify licensing before direct source reuse.

Potentially relevant beyond cloth/fur because Oren-Nayar, SSS, interference, snow and deformation belong to different material/operator families.

---

# 12. chengkehan.github.io — shader research archive / mining source

Repository: https://github.com/chengkehan/chengkehan.github.io

Despite the GitHub Pages-style name, this is a large technical rendering notebook containing articles, code and examples across many graphics topics.

### Verified example: anisotropic hair lighting

The `Anisotropic.md` material discusses:

- anisotropic lighting using the tangent direction;
- tangent/highlight relationships instead of a normal-only Blinn/Phong-style treatment;
- random tangent shifting (`normalize(T + shift * N)` pattern);
- a second highlight layer;
- AO considerations;
- storing movement-related parameters in vertex color channels.

### SHADED interpretation

**Role:** `RESEARCH ROUTER / SHADER MINING SOURCE`

Treat like a treasure map, not like a single runtime donor.

Mine recursively for:

- anisotropy;
- PBR theory;
- texture-array techniques;
- hair rendering;
- material tricks;
- geometry / coordinate handling;
- other reusable shader/operator fragments.

---

# 13. TornCloth — presentation / visual tear treatment, not yet a tear solver

Repository: https://github.com/beto-group/TornCloth

The README describes an interactive WebGL / Three.js torn-cloth presentation with:

- fabric blowing in wind;
- custom photo/video content on the cloth;
- physical / wind controls;
- grunge FX;
- vignette;
- shadow opacity;
- torn-edge parameters;
- real-time GUI controls.

### Important classification caution

The material inspected so far does **not** establish a true topological tear/fracture solver.

Do not promote it to `TEAR_SOLVER` without code-level evidence that connectivity actually changes.

### SHADED interpretation

Current role:

**`CLOTH PRESENTATION / TORN-EDGE VISUAL FX`**

Potentially useful for cheap tearing appearance, presentation and content-on-cloth workflows even if topology remains static.

---

# 14. Chipsa — interactive mesh decomposition / proximity deformation

Repository: https://github.com/Manishbhai9350/Chipsa---Stone-Animation

This is not fundamentally a stone-material shader.

The main implementation loads a GLTF stone model and a cloth model, uses raycasting to determine pointer proximity, and displaces individual stone mesh parts based on distance/falloff before smoothly lerping them back. GLTF animation and GSAP are used for transitions between states.

### Functional pattern

```text
POINTER
  ↓ RAYCAST
MESH-PART DISTANCE
  ↓ FALLOFF
RADIAL DISPLACEMENT
  ↓ LERP / RECOVERY
INTERACTIVE DECOMPOSITION
```

### SHADED interpretation

**Operator class:** `INTERACTIVE_MESH_EXPLODE / PROXIMITY_DEFORM`

Potential uses:

- environmental UI transitions;
- object inspection;
- reveal/hide states;
- proximity-driven geometry reactions;
- interactive destruction approximations;
- editor feedback.

The repository's tiny standalone GLSL files are not the interesting part; the interaction/state choreography in the Three.js application is.

---

# Cross-repository architecture

## A. Cloth is two systems: motion + optical structure

```text
                   CLOTH
                     │
       ┌─────────────┴─────────────┐
       │                           │
    GEOMETRY                    APPEARANCE
       │                           │
WebGPU mass-spring             ThunderLoom
Verlet constraints            weave / yarn BSDF
Analytical sway
Secondary chains
```

A SHADED cloth material should therefore avoid collapsing everything into a single `cloth shader` concept.

---

## B. Hair / fur is also multiple independent layers

```text
FIBER GEOMETRY
    │
    ├─ explicit individual fibers
    ├─ shells / fins
    └─ blade geometry

FIBER MATERIAL
    │
    └─ physical scattering / absorption / pigments

FIBER POPULATION LIGHTING
    │
    └─ deep / cumulative shadow transmission

FIBER MOTION
    │
    ├─ physical dynamics
    ├─ spring chains
    └─ cheap analytical / wind deformation
```

This prevents a single expensive implementation from being forced into every runtime situation.

---

## C. Proposed SHADED quality ladder for fur / fibers

```text
QUALITY / REFERENCE
  explicit fibers
  + yocto-hair style physical scattering
  + depth-dependent / deep shadowing

REALTIME MID
  PowerFur shell / fin approximation
  + simplified anisotropic material
  + appropriate shadow approximation

CHEAP / DISTANT / TOASTER
  procedural blade geometry
  or even cheaper surface anisotropy / normal treatment
```

The representation can change with LOD while preserving higher-level material intent.

---

## D. Deformation ladder

```text
FULL DEFORMABLE SURFACE
  WebGPU mass-spring + collision

LIGHTWEIGHT PHYSICS
  Verlet + structural/shear/bend constraints

SECONDARY OBJECT MOTION
  spring-damped bone chain

ANALYTICAL CHEAP PATH
  known deformation + analytically derived normals

PRESENTATION-ONLY
  shader / transform / mesh-part proximity deformation
```

Again, the correct solver depends on what actually needs to be conserved or interacted with.

---

# Strongest extraction priorities

## Tier S — deep extraction

1. **nakjun/Cloth-Simulation-WebGPU**
   - WebGPU mass-spring architecture
   - BVH broad phase
   - tri/tri narrow phase
   - collision response

2. **ThunderLoom/ThunderLoom**
   - weave representation
   - WIF-driven pattern structure
   - Irawan cloth scattering
   - renderer-independent material API idea

3. **dsforza96/yocto-hair**
   - PBRT fiber scattering
   - longitudinal / azimuthal lobes
   - absorption
   - melanin-derived color
   - sampling/PDF correctness patterns

4. **ecidevilin/DeepShadowMap**
   - depth-dependent transmittance representation
   - real-time fiber/hair shadow logic

5. **redcool/PowerFur**
   - shell/fin runtime approximation
   - instancing strategy
   - skinned multipass path
   - wind/flow/AO/shadow integration

## Tier A — extraction / integration references

6. **gam0022/unity-shader-experiments** — analytical-normal cheap path.
7. **dmitrykurash/holocloth** — browser integration and Verlet interaction.
8. **Jedzia/alShaders** — mine node-by-node, especially `alHair` and scattering utilities.
9. **kseniya7991/fur-shader** — lowest-cost geometric fiber tier.
10. **cullenwebber/three-clothing** — generic secondary-motion chain.
11. **chengkehan/chengkehan.github.io** — recursively mine techniques/articles.
12. **steaklive/CgFX-Shader-Compilation** — split into independent shader primitives.

## Conditional / presentation donors

13. **beto-group/TornCloth** — retain for visual tear/presentation; do not call it a topology solver without further evidence.
14. **Manishbhai9350/Chipsa---Stone-Animation** — retain as proximity-driven mesh reaction / UI-environment interaction donor.

---

# System-level conclusion

The useful abstraction is not four unrelated buckets named **cloth**, **grass**, **hair** and **fur**.

A more reusable SHADED model is:

```text
ORIENTED FLEXIBLE ELEMENTS
          +
COLLECTIVE STRUCTURE
          +
MOTION / CONSTRAINTS
          +
LIGHT SCATTERING
          +
POPULATION SHADOWING
          +
LOD REPRESENTATION
```

At different scales this can express:

- woven fabric;
- loose cloth;
- hair;
- fur;
- grass;
- fiber mats;
- tassels / straps / braids;
- other filamentary or flexible structured materials.

That is the architectural connection worth preserving: **the same physical/material problem can be represented at different resolutions and solved by different operators without changing its high-level intent.**

---

# Verification / source-use cautions

- The classifications above distinguish observed repo behavior from proposed SHADED abstractions.
- `TornCloth` is deliberately *not* classified as a true topology-changing tear solver based on the material inspected so far.
- `three-clothing` is deliberately *not* classified as a cloth solver; its useful mechanism is secondary spring-bone motion.
- `Chipsa---Stone-Animation` is deliberately *not* classified as a stone material shader; its stronger donor mechanism is proximity-driven component displacement / state choreography.
- `alShaders` states MIT licensing in its README; `ThunderLoom` and `yocto-hair` also state MIT licensing. Verify license at exact commit before source ingestion for every donor regardless.
- Repositories without a verified permissive license should be treated as algorithm/reference donors until licensing is resolved.
