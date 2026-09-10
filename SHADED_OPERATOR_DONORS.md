# SHADED Operator Donors — Functional Classification

> **Rule:** classify repositories by the transformation they actually provide, not by the search context, name, or visual theme that surfaced them.
>
> This document captures a batch of repositories that initially looked like a "painting / brush / watercolor" cluster but in reality spans topology, depth inference, differentiable computation, inverse reconstruction, 3D representation transforms, compositing, authoring assets, and research discovery.

## Executive map

| Repository | Actual function | SHADED role / operator class | Value |
|---|---|---|---|
| [kanguyen451/One-brushstroke](https://github.com/kanguyen451/One-brushstroke) | Graph → determine whether / how it can be traversed as one continuous stroke | **Topology / Path Solver** | **A−** |
| [CompVis/depth-fm](https://github.com/CompVis/depth-fm) | RGB → depth; also depth inpainting / depth-conditioned synthesis | **Perception / Domain Transform** | **S** |
| [reiinakano/neural-painters-pytorch](https://github.com/reiinakano/neural-painters-pytorch) | Learn a differentiable surrogate for a non-differentiable painter | **Differentiable Surrogate / Constraint** | **S** |
| [nv-tlabs/brushstroke_engine](https://github.com/nv-tlabs/brushstroke_engine) | Stroke geometry + learned medium/style + color → rendered stroke appearance | **Learned Stroke Materializer** | **S** |
| [Spyduck/pyautopainter](https://github.com/Spyduck/pyautopainter) | Reference image → iterative brush marks, with error-driven skipping and optional height accumulation | **Image → Marks Reconstruction** | **A** |
| [Xzzit/BrushGaussian](https://github.com/Xzzit/BrushGaussian) | 3D Gaussian representation → textured / deformed / compacted Gaussian representation | **3D Representation Transformer** | **S** |
| [Draneria/Toolkit-by-Draneria_Krita-Brushes](https://github.com/Draneria/Toolkit-by-Draneria_Krita-Brushes) | Brush presets / material-like stroke authoring controls | **Stroke Material Modifier / Authoring Assets** | **B+ / A−** |
| [CompVis/brushstroke-parameterized-style-transfer](https://github.com/CompVis/brushstroke-parameterized-style-transfer) | Target appearance → optimized explicit brushstroke parameters | **Inverse Stroke Solver** | **S** |
| [lmgonzalves/brushstroke](https://github.com/lmgonzalves/brushstroke) | Path / points → temporal draw / erase / fill composite | **Path-driven Compositor** | **A−** |
| [Ramotion/aquarelle](https://github.com/Ramotion/aquarelle) | Texture + mask + noise evolution → animated reveal / deformation | **Procedural Mask Transition** | **B+ / A−** |
| [erdavids/WatercolorClouds](https://github.com/erdavids/WatercolorClouds) | Shape → repeated translucent deformed shapes → accumulated organic result | **Procedural Shape Layering** | **B+** |
| [mattdesl/graphics-resources](https://github.com/mattdesl/graphics-resources) | Curated graphics research / techniques → further technical sources | **Research Router / Donor Index** | **S as miner** |

---

## 1. One-brushstroke — topology, not painting

Repository: https://github.com/kanguyen451/One-brushstroke

The name is misleading if it is discovered in a brush / painting search. Its useful abstraction is purely logical/topological.

```text
GRAPH
  ↓
SINGLE_STROKE_SOLVE
  ↓
ordered edge/node path | impossible
```

### What it does

- Works on a graph of connected points / edges.
- Determines whether the graph can be traversed as one continuous stroke.
- Produces a traversal / Euler-style path when possible.

### SHADED interpretation

**Operator class:** `TOPOLOGY / PATH SOLVER`

Possible operator shape:

```text
GRAPH → EULERIZE / SINGLE_STROKE_SOLVE → ORDERED_PATH
```

Potential uses are broader than drawing style:

- convert unordered connected line segments into an executable continuous path;
- ornament / vine path ordering;
- SVG / curve-network traversal;
- cable / road / conduit ordering;
- engraving / plotter paths;
- brush execution with minimal pen-up events;
- generic graph traversal nodes inside a visual operator graph.

### Extension idea

If the graph is not Eulerian, a SHADED-level wrapper could choose among:

- reject as impossible;
- duplicate minimal edges;
- add connector edges;
- split into the smallest practical number of strokes.

### Important distinction

**This is not a style donor and not a rendering donor.** It is useful because it is a logical operator.

### Code-use caution

Treat this primarily as an algorithm / behavior reference unless licensing has been verified. Reimplementation of the graph logic is safer than blindly ingesting source.

---

## 2. DepthFM — perception / domain transformation, not style

Repository: https://github.com/CompVis/depth-fm

DepthFM belongs in perception / geometry inference.

```text
IMAGE
  ↓
FLOW-MATCHED DOMAIN TRANSFORM
  ↓
DEPTH
```

### What matters

- monocular RGB → depth;
- direct learned transport from image space toward depth space using flow matching;
- supports very low-step / single-step inference modes;
- includes depth inpainting functionality;
- includes depth-conditioned synthesis functionality.

### SHADED interpretation

**Operator class:** `PERCEPTION / DOMAIN TRANSFORM`

```text
IMAGE
  ↓
DEPTH_FM
  ├─ DEPTH
  ├─ DEPTH / UNCERTAINTY-RELATED SIGNALS where exposed
  └─ optional transforms
       ├─ INPAINT_DEPTH
       └─ DEPTH_CONDITIONED_SYNTHESIS
```

### Architectural value beyond this exact model

The interesting pattern is more general than depth estimation:

```text
STRUCTURED DOMAIN A
        ↓
LEARNED DIRECT TRANSPORT
        ↓
STRUCTURED DOMAIN B
```

This is relevant to SHADED because it suggests operator designs that transform one meaningful field directly into another rather than always going through a generic noise-to-output generator.

### Important distinction

**Not a painting repo. Not a style repo.** It is a vision / geometry inference operator.

---

## 3. neural-painters-pytorch — differentiable surrogate pattern

Repository: https://github.com/reiinakano/neural-painters-pytorch

This is more important than "neural painting" suggests.

### Core pattern

A real painting program can be non-differentiable and potentially non-deterministic. A neural painter is trained to approximate that process in a differentiable form, enabling optimization / learning through the surrogate.

```text
NON-DIFFERENTIABLE OPERATOR
          │
          ↓ learn
DIFFERENTIABLE SURROGATE
          │
          ↓ gradients
OPTIMIZATION / AGENT
```

### SHADED interpretation

**Operator class:** `META / DIFFERENTIABLE SURROGATE / WRAPPER`

Potentially reusable beyond painting for operators such as:

- fluid simulation;
- erosion;
- particle systems;
- material reaction systems;
- external / black-box donor algorithms;
- any useful transform that cannot conveniently participate in gradient-based optimization.

The general idea is:

> Learn a differentiable stand-in for an otherwise non-differentiable operator so upstream parameters can be optimized through it.

This should not be buried inside a PAINT category; it is a meta-computation pattern.

---

## 4. NVIDIA brushstroke_engine — learned stroke materializer

Repository: https://github.com/nv-tlabs/brushstroke_engine

### Functional signature

```text
STROKE GEOMETRY
+
LATENT MEDIUM / STYLE
+
COLOR
    ↓
LEARNED STROKE GENERATOR
    ↓
STROKE APPEARANCE
```

### What it contributes

- a learned space of brush / medium behavior rather than a fixed list of raster brush tips;
- controllable user stroke geometry;
- controllable color;
- transparent / compositable stroke generation;
- interpolation through learned media / brush behavior;
- learned brush appearance rather than whole-image style filtering.

### SHADED interpretation

**Operator class:** `GENERATIVE MATERIALIZATION / LEARNED STROKE RENDERER`

This is useful where an abstract path or stroke needs to become a material-looking mark.

The strongest architectural interpretation is:

> Separate **what the stroke does geometrically** from **how the medium materializes that stroke**.

That makes a stroke transferable across watercolor, ink, charcoal, oil, mud, snow, scorch, vegetation, etc. without forcing the path-planning layer to know the rendering implementation.

---

## 5. pyautopainter — error-driven reconstruction loop

Repository: https://github.com/Spyduck/pyautopainter

At first glance this is a simple automatic painter. The reusable part is the control loop.

### Functional pattern

```text
TARGET
   ↓
COMPARE CURRENT STATE
   ↓
ERROR > THRESHOLD ?
 ├─ no  → skip
 └─ yes → apply mark
```

### What it contributes

- reference-image-driven iterative painting;
- varying brush scales / marks;
- comparison between current canvas and desired local result;
- skips unnecessary marks when local error is already small;
- can accumulate brush application into a height-like map.

### SHADED interpretation

**Operator class:** `INVERSE RECONSTRUCTION / ERROR-DRIVEN MARK PLACEMENT`

This is useful as a generic architecture for **do work only where the current state materially differs from the target**.

That principle can transfer beyond painting to:

- geometry refinement;
- sparse corrections;
- simulation repair;
- adaptive detail placement;
- local material updates;
- progressive reconstruction.

---

## 6. BrushGaussian — representation transform, not merely style transfer

Repository: https://github.com/Xzzit/BrushGaussian

### Functional view

```text
GAUSSIAN PRIMITIVES
   ↓ augment attributes
TEXTURED GAUSSIANS
   ↓ local transform
DEFORMED GAUSSIANS
   ↓ cluster / prune
COMPACT REPRESENTATION
```

### What matters

- operates on / extends a 3D Gaussian representation;
- introduces per-Gaussian texture-related features;
- texture mapping affects appearance and local geometry;
- allows localized deformation rather than applying only a final-screen filter;
- clustering / pruning can remove redundant representation elements.

### SHADED interpretation

**Operator class:** `3D REPRESENTATION TRANSFORM`

The important idea is that stylization / material appearance can be encoded into the **representation primitives themselves**, rather than being a post-effect applied after rendering.

This makes it relevant to:

- editable radiance / Gaussian representations;
- compact scene representation;
- materialized 3D marks;
- representation-level geometry manipulation;
- world-space stylization that survives viewpoint changes.

---

## 7. Draneria Krita Toolkit — authoring and material-like stroke channels

Repository: https://github.com/Draneria/Toolkit-by-Draneria_Krita-Brushes

This is primarily an authoring-resource / brush-preset donor rather than a runtime renderer.

### Useful concept

A brush does not need to mean only RGBA color. A stroke can conceptually modify several fields:

```text
STROKE
  ├─ color / pigment
  ├─ alpha / coverage
  ├─ height / relief
  ├─ texture
  ├─ flatten / thicken behavior
  └─ erase / modify existing material
```

### SHADED interpretation

**Role:** `AUTHORING ASSETS / MATERIAL STAMP REFERENCE`

The broader SHADED idea is to treat a brush / stamp as a **multi-field material operation**, not just a colored decal.

This connects naturally to sandbox/world stamps where one gesture might change terrain, moisture, thermal state, biology, surface material, or height simultaneously.

---

## 8. CompVis parameterized brushstroke style transfer — inverse stroke solver

Repository: https://github.com/CompVis/brushstroke-parameterized-style-transfer

This is fundamentally different from a normal image filter.

### Functional signature

```text
DESIRED APPEARANCE
      ↓ optimize
EXPLICIT STROKE PARAMETERS
      ↓ differentiable renderer
IMAGE
```

### What it contributes

- explicit brushstroke parameterization;
- optimization occurs over strokes rather than directly over output pixels;
- differentiable rendering allows inverse solving;
- stroke flow / orientation can be influenced externally.

### SHADED interpretation

**Operator class:** `INVERSE STROKE SOLVER`

The key distinction:

> It solves **appearance → strokes**.

That makes it complementary to systems that perform **strokes → appearance**.

---

## 9. lmgonzalves/brushstroke — path-driven temporal compositor

Repository: https://github.com/lmgonzalves/brushstroke

Calling this only a UI effect undersells it.

### Inputs / controls

It can work from things such as:

- SVG-like paths;
- arrays of points;
- direction / curve information;
- image content;
- DOM / HTML content in compositing use cases.

It supports operations such as:

```text
DRAW
ERASE
FILL
```

and exposes stroke-behavior controls around temporal progression and effects such as ink amount / lifting / dripping / splashing depending on configuration.

### SHADED interpretation

**Operator class:** `PATH → SPATIOTEMPORAL MASK / COMPOSITE`

```text
PATH / POINTS
      ↓
TIME-PROGRESSED COVERAGE
      ↓
DRAW / ERASE / FILL / REVEAL
```

Potentially useful for:

- path-driven reveals;
- animated masking;
- construction / destruction traces;
- UI elements that are drawn rather than faded;
- execution visualization for arbitrary paths.

---

## 10. Ramotion/aquarelle — procedural mask transition

Repository: https://github.com/Ramotion/aquarelle

The watercolor look is an application of the mechanism, not the mechanism itself.

### Functional signature

```text
TEXTURE IMAGE
+
MASK IMAGE
+
NOISE EVOLUTION
      ↓
ANIMATED REVEAL / COMPOSITE
```

Typical controls concern noise amplitude, frequency / scale, offsets, mask evolution, and animation over time.

### SHADED interpretation

**Operator class:** `PROCEDURAL MASK DEFORMATION / TRANSITION`

Potential uses extend beyond watercolor:

- organic reveal / dissolve;
- burn / corrosion fronts;
- fog / cloud openings;
- biological spread masks;
- irregular UI transitions;
- world-space or screen-space reveal patterns.

### Important distinction

It is **not a watercolor simulator**. It is a mask-based procedural reveal whose chosen visual treatment resembles watercolor.

---

## 11. WatercolorClouds — iterative stochastic shape compositor

Repository: https://github.com/erdavids/WatercolorClouds

### Functional pattern

```text
SHAPE
  ↓ mutate
SHAPE'
  ↓ translucent composite
REPEAT N TIMES
```

The visual result comes from repeatedly layering slightly changed semi-transparent shapes.

### SHADED interpretation

**Operator class:** `ITERATIVE STOCHASTIC SHAPE COMPOSITOR`

Watercolor is only one application. The same primitive can be repurposed for:

- clouds;
- fog;
- organic borders;
- stains;
- moisture;
- moss / biological spread;
- combustion / scorch spread;
- soft terrain patches;
- procedural accumulation.

This is attractive as a cheap browser / GPU fallback because the principle is simple and compositional.

---

## 12. mattdesl/graphics-resources — research router / donor multiplier

Repository: https://github.com/mattdesl/graphics-resources

This is not a runtime donor in the same sense as the others.

### Actual role

A curated graphics research / implementation index that links onward to techniques and papers across areas such as:

- non-photorealistic rendering;
- stroke-based rendering;
- ink / watercolor behavior;
- rendering and lighting;
- geometry / signed-distance techniques;
- postprocessing;
- optimization;
- general graphics resources.

### SHADED interpretation

**Role:** `SOURCE_NODE / RESEARCH_EXPANSION / DONOR INDEX`

Do not rank it against an algorithm as if they were equivalent objects. Its value is multiplicative:

```text
ONE INDEX
   ↓ mine
MANY PAPERS / IMPLEMENTATIONS / DONORS
```

This repository should be mined recursively rather than merely recorded and forgotten.

---

# Cross-repository architecture patterns

## A. Appearance → strokes vs. strokes → appearance

Two of the strongest donors are almost inverse partners.

### CompVis parameterized brushstrokes

```text
APPEARANCE → STROKES
```

It solves an inverse problem: find explicit marks whose rendering approximates the target appearance.

### NVIDIA brushstroke_engine

```text
STROKES → APPEARANCE
```

It materializes abstract stroke geometry through a learned brush / medium representation.

### Combined SHADED pattern

```text
TARGET / INTENT
      ↓
INVERSE STROKE SOLVER
      ↓
STRUCTURED STROKES
      ↓
LEARNED / PROCEDURAL MATERIALIZER
      ↓
VISIBLE MATERIAL MARKS
```

That is substantially more powerful than "apply watercolor style" because the intermediate representation remains explicit and editable.

---

## B. Stroke and World Stamp can converge

A useful SHADED abstraction is to stop treating a "brush stroke" and a "world edit stamp" as unrelated systems.

Both can be represented as:

```text
PATH / REGION
+
RADIUS / FALLOFF
+
MATERIAL OR FIELD PAYLOAD
+
LOCAL RESPONSE RULES
+
TIME
```

A single gesture could therefore modify multiple fields:

```text
STAMP / STROKE
  ├─ pigment / color
  ├─ alpha / coverage
  ├─ wetness
  ├─ height / displacement
  ├─ roughness
  ├─ temperature
  ├─ moisture / water
  ├─ biology / vegetation
  ├─ impulse / force
  └─ arbitrary custom field
```

This creates a clean bridge between authoring, painting, simulation, material editing, and environmental interaction.

---

## C. Logical path solving should remain separate from materialization

`One-brushstroke` and `brushstroke_engine` illustrate two orthogonal responsibilities:

```text
TOPOLOGY / ORDERING
        ↓
EXECUTABLE PATH
        ↓
MATERIALIZATION
        ↓
VISIBLE / PHYSICAL MARK
```

A path solver should not need to know whether the output will become ink, snow, a road, a cable, vegetation, or a UI reveal.

Likewise, a materializer should not be responsible for solving graph topology.

---

## D. Perception should remain separate from style / material systems

`depth-fm` belongs upstream as structured scene inference:

```text
RGB / OBSERVATION
       ↓
DEPTH / GEOMETRY FIELD
       ↓
WORLD / REPRESENTATION OPERATORS
       ↓
MATERIAL / STROKE / RENDERING OPERATORS
```

Depth can influence stroke scale, orientation, occlusion, world attachment, reconstruction, or deformation without itself being a painting system.

---

## E. Differentiable wrappers are a meta-operator category

The most transferable idea from `neural-painters-pytorch` is not painting at all:

```text
BLACK-BOX / NON-DIFFERENTIABLE OPERATOR
                 ↓ approximate
DIFFERENTIABLE SURROGATE
                 ↓
OPTIMIZATION THROUGH THE OPERATOR
```

Candidate SHADED targets could include simulations or external donor systems that are useful but otherwise difficult to optimize through.

---

## F. Error-driven sparse correction

`pyautopainter` suggests a general sparse-work rule:

```text
CURRENT STATE vs TARGET
          ↓
LOCAL ERROR
          ↓
ONLY OPERATE WHERE ERROR MATTERS
```

This can reduce unnecessary work in reconstruction, simulation correction, geometry refinement, visual matching, or progressive world updates.

---

# Recommended SHADED taxonomy for this batch

```text
TOPOLOGY / PATH
  └─ One-brushstroke

PERCEPTION / DOMAIN TRANSFORMS
  └─ DepthFM

META / DIFFERENTIABLE COMPUTATION
  └─ Neural Painters

INVERSE RECONSTRUCTION
  ├─ Parameterized Brushstrokes
  └─ PyAutoPainter

GENERATIVE MATERIALIZATION
  └─ NVIDIA Brushstroke Engine

REPRESENTATION TRANSFORM
  └─ BrushGaussian

PATH / COMPOSITING
  ├─ lmgonzalves/brushstroke
  ├─ Aquarelle
  └─ WatercolorClouds

AUTHORING / MATERIAL ASSETS
  └─ Draneria Krita Toolkit

RESEARCH DISCOVERY
  └─ mattdesl/graphics-resources
```

---

# Priority summary

## S-tier architectural donors

### CompVis/depth-fm
Direct structured-domain transformation; strong perception / geometry operator pattern.

### reiinakano/neural-painters-pytorch
Differentiable surrogate architecture that generalizes far beyond painting.

### nv-tlabs/brushstroke_engine
Strong stroke-materialization abstraction with learned medium behavior.

### CompVis/brushstroke-parameterized-style-transfer
Explicit inverse solver from desired appearance to structured brushstroke parameters.

### Xzzit/BrushGaussian
Representation-level texture / deformation ideas for 3D Gaussian primitives.

### mattdesl/graphics-resources
Not a runtime algorithm, but an S-tier donor multiplier / research-mining entry point.

## A-tier / useful operator donors

### Spyduck/pyautopainter
Simple but reusable error-driven iterative reconstruction logic, plus height accumulation.

### kanguyen451/One-brushstroke
Small but clean topology / single-path operator concept.

### lmgonzalves/brushstroke
Reusable path-to-temporal-mask/compositing behavior.

## Specialized / cheap-path donors

### Ramotion/aquarelle
Organic procedural mask deformation / reveal.

### erdavids/WatercolorClouds
Cheap iterative stochastic shape layering.

### Draneria Krita Toolkit
Useful authoring/material-channel references, but not primarily a runtime engine.

---

# Core lesson from this batch

The search context was misleading. These repositories should **not** be stored as one "painting" cluster.

The correct systems view is:

> A repository is valuable according to the transformation, representation, constraint, solver, compositor, or research-routing capability it contributes — not according to the aesthetic context in which it was discovered.

For SHADED, the most important result of this batch is therefore not a watercolor stack. It is a small cross-domain operator vocabulary:

```text
OBSERVE
→ INFER
→ SOLVE
→ ORDER
→ REPRESENT
→ MATERIALIZE
→ COMPOSITE
→ REACT
→ OPTIMIZE
```

The same operator graph can support painting, geometry reconstruction, world editing, UI transitions, simulation marks, and procedural environmental changes without collapsing them into one stylistic subsystem.

---

# 2026-09-07 donor batch — planet voxels, procedural CSG, refractive glass

## 13. Benziza/planetcraft — surface-only voxel planet / browser instancing

Repository: https://github.com/Benziza/planetcraft

### Functional interpretation

```text
PLANET / GEO DATA
      ↓
VOXEL OCCUPANCY
      ↓
6-NEIGHBOR INTERIOR REJECTION
      ↓
SURFACE CELLS ONLY
      ↓
INSTANCED RENDERING
```

### SHADED role

**Operator class:** `WORLD REPRESENTATION / SURFACE VOXELIZATION / INSTANCING`

Useful primarily as a compact browser-side implementation reference for:

- voxelizing a planet-like volume;
- dropping fully enclosed cells before rendering;
- rendering repeated surface cells through instancing;
- mapping geographic / biome information onto spatial cells;
- keeping a globe-scale toy world cheap enough for the browser.

### Value

**B as implementation reference; C as unique core technique.**

The useful donor pattern is the cheap surface-only extraction and instancing path, not a sophisticated planetary engine. Verify licensing before any source reuse.

---

## 14. Matvey-Kuk/reopenscad — declarative procedural geometry / CSG pipeline

Repository: https://github.com/Matvey-Kuk/reopenscad

### Functional interpretation

```text
DECLARATIVE MODEL / PARAMETERS
          ↓
PARSE + EVALUATE
          ↓
CSG / IMPLICIT GEOMETRY
          ↓
MESH EXTRACTION
          ↓
PREVIEW / EXPORT
```

### SHADED role

**Operator class:** `PROCEDURAL GEOMETRY / CSG / TEXT-TO-GEOMETRY`

Strong architecture reference for:

- a compact declarative geometry language;
- parameterized procedural modeling;
- union / difference / intersection style composition;
- separating authoring semantics from meshing / rendering;
- browser-side preview and export workflows;
- exposing procedural geometry as an operator graph or prompt-driven construction layer.

The repository ships an explicit language specification (`SPEC_LANG.md`) and a browser workbench. Its GPL license makes it primarily an architecture / behavior / test reference unless SHADED intentionally accepts the corresponding copyleft obligations.

### Value

**A / A− architectural donor.**

The key SHADED abstraction is not “OpenSCAD clone”; it is:

```text
INTENT / PARAMETERS → STRUCTURED GEOMETRY PROGRAM → REAL MESH
```

---

## 15. Dragon Ball shader — refractive scene-reactive glass operator

Source: https://codeblog.farzon.org/dragonball-shader

### Functional interpretation

```text
SCENE COLOR / ENVIRONMENT
        +
GLASS MASK / SURFACE NORMALS
        ↓
FRESNEL
REFLECTION
REFRACTION
INTERNAL RAY TRAVEL
OPTIONAL DISPERSION / CAUSTICS
        ↓
SCENE-REACTIVE GLASS
```

### SHADED role

**Operator class:** `RENDERING / REFRACTIVE GLASS / SCENE-REACTIVE MATERIAL`

This is especially relevant to the SHADED mark: the impossible isometric S does not need to become a physically consistent solid. Its visible faces can act as an optical operator over the already rendered scene.

Possible pipeline:

```text
RENDER SCENE
   ↓
SHADED LOGO MASK + PSEUDO-NORMALS
   ↓
REFRACT BACKGROUND
   + REFLECT ENVIRONMENT
   + FRESNEL EDGE RESPONSE
   + SUBTLE RGB DISPERSION
   ↓
TRANSPARENT LOGO THAT INHERITS THE CURRENT WORLD
```

That preserves the impossible S exactly while allowing the mark to look physically responsive: snow, fire, water, night, vegetation, sky, and lighting all change what the logo reflects and refracts without changing the logo identity.

### Value

**S for SHADED branding/material behavior; A as general rendering donor.**

The important design rule is that the logo should not own a fixed color. Its identity is **geometry + scene response**.

---

# 2026-09-10 donor batch — self-healing local rules + GPU-native WebGPU editing

## 16. smoothyy3/tardigrade — neural cellular automata / self-healing local field rules

Repository: https://github.com/smoothyy3/tardigrade

### Functional interpretation

```text
CELL STATE (16 values)
      +
3x3 LOCAL NEIGHBOURHOOD
      ↓
LEARNED CONVOLUTION + 2-LAYER MLP
      ↓
LOCAL STATE UPDATE
      ↓ repeated everywhere
EMERGENT STABLE GLOBAL FORM
```

### SHADED role

**Operator class:** `EMERGENT SIMULATION / NCA / SELF-HEALING LOCAL FIELDS`

The useful abstraction is not the terminal creature itself. Every cell runs the same small learned local rule; the desired global shape is an attractor / stable state of that rule rather than a stored image. Damage can therefore be repaired by the surviving local state.

Useful SHADED transfer paths:

- regenerative vegetation, moss, fungus, tissue, crusts or other biological fields;
- destructible structures that locally reorganize toward a target morphology;
- material systems where global form emerges from cheap neighbourhood updates;
- active-region simulation in which only disturbed cells and their neighbourhood need updates;
- learned local rules as an alternative to explicitly scripting every global repair or growth process.

The shipped creatures use 16 values per cell, one 3x3 learned convolution and a two-layer MLP; each creature is represented by about 24k parameters / 96 KB of weights. Training is offline in PyTorch/NCAtorch, while runtime inference is implemented directly in Go and checked against a fixed PyTorch-derived forward-pass fixture.

### Value

**S architectural donor.**

Core lesson:

```text
DO NOT STORE THE FORM
STORE / LEARN THE LOCAL LAW WHOSE STABLE STATE IS THE FORM
```

MIT licensed, but still treat the algorithmic pattern and tests as the primary donor value rather than blindly transplanting implementation details.

---

## 17. playcanvas/supersplat v3.0.0 — GPU-native WebGPU editor architecture

Repository: https://github.com/playcanvas/supersplat
Release: https://github.com/playcanvas/supersplat/releases/tag/v3.0.0

### Functional interpretation

```text
CHUNKED GPU-RESIDENT SPLAT DATA
        ↓
GPU PROJECT
        ↓
FRUSTUM CULL
        ↓
COMPACT
        ↓
GPU RADIX SORT
        ↓
INDIRECT DRAW
        ↓
INTERACTIVE EDIT / SELECT / PICK / EXPORT
```

### SHADED role

**Operator class:** `WEBGPU ARCHITECTURE / GPU-RESIDENT EDITOR / COMPUTE CULL-SORT-DRAW`

SuperSplat 3.0 rewrites both renderer and editor data model around WebGPU. Projection, culling, compaction, depth sorting and draw submission all execute on the GPU; the previous CPU sort worker and WebGL2 renderer are removed from the 3.x editor.

Architectural donor points for SHADED:

- chunked GPU storage instead of retaining full floating-point scene copies in JavaScript;
- small editable per-instance state layered over largely static GPU-resident data;
- GPU compute for histogram, range selection, colour matching, bounds and selection intersections;
- streamed chunk-by-chunk serialization / export instead of rematerializing an entire scene in RAM;
- indirect draw and GPU radix sort as a reusable browser-native large-set pipeline;
- asynchronous edit / selection work isolated from later camera changes;
- GPU depth picking for interactive tools;
- adaptive `Stochastic Alpha`: sort-free stochastic transparency while movement is expensive, then return to exact sorted blending when the view settles.

The release reports large JavaScript-heap reductions on its 4.4M-splat / 990 MB PLY benchmark, including idle scene memory dropping from 1,557 MB in v2 to 105 MB in v3 and 1080p video rendering from 1,673 MB to 142 MB.

### SHADED transfer pattern

```text
GPU RESIDENCY
→ CHUNKED STORAGE
→ COMPUTE CULL / COMPACT
→ GPU SORT WHEN NEEDED
→ INDIRECT DISPATCH / DRAW
→ GPU-NATIVE EDIT OPERATIONS
→ STREAMED SERIALIZATION
```

This pattern is relevant beyond Gaussian splats: large voxel surfaces, particles, sparse cells, material-field instances and other high-count editable primitives can use the same division of labour.

### Constraint

SuperSplat Editor 3.0 intentionally requires WebGPU. For SHADED, treat that as a high-end reference path rather than an argument to remove the existing Reference / WebGL / fallback ladder.

### Value

**S architectural donor.**

The strongest donor value is the editor architecture, not Gaussian splatting by itself.
