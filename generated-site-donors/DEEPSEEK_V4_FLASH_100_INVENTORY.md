# DEEPSEEK V4 FLASH — FULL 100/100 INVENTORY

Companion to [`DEEPSEEK_V4_FLASH_100.md`](DEEPSEEK_V4_FLASH_100.md).

**Source pass:** all 100 numbered HTML files were statically inspected. Page names/prompts are metadata only; grades are based on implementation present in HTML/CSS/JS.

| ID | Page | Grade | Actual computational value | Assessment | Relation to earlier collections |
|---:|---|:---:|---|---|---|
| 001 | `aurora-glass` | **B** | day/night/light-glass gradient and pointer parallax | Visual lighting/material response; no aurora physics. | visual overlap |
| 002 | `neon-cyberpunk` | **B** | procedural neon skyline / rain / glitch state | Scene/particle presentation only. | visual overlap |
| 003 | `kinetic-type` | **B** | kinetic typography interpolation and motion state | Animation donor, not simulation. | generic |
| 004 | `particle-field` | **A-** | swirl/vortex particle field + mouse repulsion + damped integration + local links | Reusable particle steering; handcrafted field. | overlap: particle/flow |
| 005 | `brutalist-poster` | **C** | brutalist poster interactions/layout | Presentation only. | non-donor |
| 006 | `neumorphic-panel` | **B** | tactile mixer controls + meters | Interaction/control surface; no verified DSP core. | weaker audio/UI overlap |
| 007 | `liquid-metal` | **A-** | metaball-like liquid-metal blobs with merge/orbit/morph heuristics | Useful implicit blob/merge visual; not fluid dynamics. | overlap: Fable liquid metal |
| 008 | `paper-cut` | **B** | layered paper-cut parallax / scroll state | Visual composition donor. | visual |
| 009 | `dataviz-orbit` | **B** | orbital dataviz layout + linked hover state | Data-visualization geometry; not orbital mechanics. | generic |
| 010 | `ascii-dream` | **B** | ASCII raster panorama / animation | Raster/presentation donor. | generic |
| 011 | `editorial-luxury` | **C** | editorial carousel/reveal | Presentation only. | non-donor |
| 012 | `mandala-lab` | **A-** | radial symmetry mandala generator + export | Reusable procedural drawing primitive. | overlap: radial geometry |
| 013 | `fluid-wave` | **B** | three prescribed layered wave curves with interactive amplitude | Wave look only; no wave equation. | false friend |
| 014 | `glass-orb` | **B** | glass-orb material/pointer response | Visual material donor. | visual |
| 015 | `wireframe-3d` | **A** | dependency-free 3D wireframe shape generation, rotations, projection and depth-sorted edges | Compact 3D projection/geometry reference. | overlap, but useful |
| 016 | `vaporwave` | **C** | vaporwave parallax/scene effects | Presentation only. | non-donor |
| 017 | `hologram-ui` | **B** | holographic tactical UI / radar-like effects | Interface/presentation; no sensing model. | false friend |
| 018 | `emoji-physics` | **A** | 2D rigid-ish emoji balls with gravity, fling, spatial-hash pair collisions and shock impulses | Compact collision sandbox; approximate but reusable. | overlap: Qwen/Fable rigid toys |
| 019 | `chrono-canvas` | **A-** | clock-driven sky interpolation, sun/moon arcs and stars | Useful temporal environment-state mapping. | overlap |
| 020 | `grain-halftone` | **A-** | grain/halftone image treatment | Reusable raster effect; not a physical donor. | overlap image processing |
| 021 | `iso-city` | **A-** | isometric city placement, inverse isometric picking and procedural buildings | Useful spatial editor/projection primitive. | partial new |
| 022 | `dot-matrix` | **A-** | dot-matrix glyph sampling + pointer ripple deformation | Reusable raster/glyph field interaction. | partial overlap |
| 023 | `jelly-physics` | **A-** | ring-point soft body using neighbour springs, radial pressure restoration and Verlet-like integration | Good visual soft-body sketch, but spring accelerations are overwritten rather than accumulated and the named GRAV term is applied to x; not a trustworthy solver. | NEW idea, implementation flawed |
| 024 | `scroll-story` | **B** | scroll-driven scene/story interpolation | Presentation orchestration. | generic |
| 025 | `magnetic-nav` | **B** | magnetic navigation attraction/hover behavior | UI spring/attraction metaphor; no magnetics. | false friend |
| 026 | `meteor-shower` | **B** | meteor particle spawning/trails/barrages | Particle presentation only. | overlap |
| 027 | `barcode-type` | **A-** | barcode-style typography/raster encoding | Reusable typography/raster primitive. | generic |
| 028 | `tokyo-rain` | **B** | rain particles / Tokyo scene | Atmospheric visual only. | overlap |
| 029 | `gradient-cards` | **B** | interactive gradient cards | Material/UI response. | generic |
| 030 | `waveform-vis` | **A** | WebAudio sequencer/synth: oscillator voices, noise, filter, kick/bass/pad/arp scheduling + waveform visualization | Real browser audio/DSP orchestration. | overlap: Fable/DeepSeek audio |
| 031 | `tartan-lab` | **A-** | procedural tartan/weave layer construction + tile export | Useful textile pattern generator. | overlap: Astra weave, distinct visual |
| 032 | `maze-gen` | **A-** | randomized DFS visitation + wall-bitfield intent + shortest-path search | Major bug: walls start at 0 and carving only clears bits, so solver sees an effectively wall-free grid. Keep generation/search concepts separately, not the combined maze as oracle. | FALSE FRIEND / broken topology |
| 033 | `conway-art` | **A** | Conway cellular automaton with multiple seeds and decay-memory rendering | Correct reusable cellular automaton. | overlap: Fable Life |
| 034 | `spectral-room` | **A** | WebAudio generative song scheduler coupled to a perspective room visualizer | Useful audio/event orchestration compound donor. | overlap audio, new coupling |
| 035 | `lissajous-garden` | **A-** | Lissajous curve sampling used as parametric floral geometry | Compact harmonic-to-geometry primitive. | partial overlap |
| 036 | `topo-terrain` | **A+** | mutable seeded heightfield + sculpt/flatten stamps + Marching Squares contour extraction + hillshade + peak finding | Excellent field authoring → contours → shading pipeline. | stronger overlap: Fable 040 |
| 037 | `rose-curves` | **A-** | rose/rhodonea curve sampling and progressive drawing | Reusable parametric-curve primitive. | partial overlap |
| 038 | `rule30` | **A** | Rule-30 / configurable elementary cellular automaton with history and injections | Correct 1D CA primitive. | NEW |
| 039 | `voronoi-bloom` | **A** | nearest-site Voronoi distance field + Lloyd-style centroid relaxation | Useful centroidal relaxation; the optional second pass moves toward stale centroids rather than recomputing a true second Lloyd iteration. | NEW vs Fable Voronoi |
| 040 | `thread-art` | **B** | interactive thread-art segment construction with afterglow | Drawing interaction; no optimization like Fable string-art. | weaker overlap |
| 041 | `rope-swing` | **A** | Verlet rope with constraints, floor collision, wind and release projectile | Useful rope/constraint dynamics. | overlap: Fable/Qwen constraints |
| 042 | `elastic-trail` | **A** | spring point-chain ribbon with taper, shockwave displacement and Catmull-style smoothing | Reusable elastic trail / chain primitive. | partial new |
| 043 | `word-cloud` | **A-** | collision-avoidant weighted word-cloud layout | Useful 2D packing/layout heuristic. | generic |
| 044 | `type-foundry` | **B** | type specimen controls | Typography UI. | non-core |
| 045 | `color-field` | **A-** | interactive persistent color-field painting with snapshots/undo and soft bloom layers | Useful authoring/state primitive. | generic |
| 046 | `glitch-portrait` | **B** | glitch portrait channel/distortion effects | Image-effect donor. | overlap |
| 047 | `crt-tv` | **B** | CRT scanline/noise/distortion simulation | Display post-effect donor. | overlap |
| 048 | `conic-blend` | **B** | conic gradient blending | Color/UI donor. | generic |
| 049 | `scroll-hue` | **B** | scroll-mapped hue transforms | Presentation/color mapping. | generic |
| 050 | `cursor-ripple` | **A+** | discrete heightfield ripple solver with ping-pong buffers, damping, impulses and displaced-texture rendering | Strong wave-surface primitive; comparable to Fable 099. | strong overlap |
| 051 | `ink-water` | **A** | value-noise/curl-field ink particles with viscous damping and persistent trails | Useful advection/ink heuristic; not diffusion PDE. | overlap: Fable 070 |
| 052 | `lava-lamp` | **A-** | metaball lava blobs with temperature-like warm-rise/cool-sink buoyancy heuristic and confinement | Interesting buoyancy toy; not fluid/thermal solver. | partial new |
| 053 | `sunset-skyline` | **B** | procedural skyline/daylight scene | Presentation only. | visual |
| 054 | `aurora-borealis` | **B** | noise/ribbon aurora visualization | No magnetosphere/plasma physics. | false friend |
| 055 | `warp-drive` | **B** | warp-speed starfield | Projection/particle visual. | overlap |
| 056 | `black-hole` | **B** | black-hole lensing-style visual | No GR/geodesic solver verified. | false friend |
| 057 | `supernova` | **B** | supernova/firework particle burst | Particle visual; no stellar physics. | false friend |
| 058 | `kaleidoscope` | **A-** | kaleidoscope symmetry drawing transforms | Reusable symmetry transform. | overlap |
| 059 | `mosaic-light` | **A-** | grid BFS-like radial wave propagation with decay | Useful discrete wavefront propagation; not physical heat/light diffusion. | partial new |
| 060 | `stained-glass` | **B** | stained-glass geometry/light-beam interaction | Stylized light; no validated refraction. | false friend |
| 061 | `silk-flow` | **A** | curl-noise ribbon advection with cohesion, depth and injected radial gusts | Useful strand/flow-field primitive. | partial overlap |
| 062 | `waving-flag` | **A+** | 2D Verlet cloth grid with structural + shear constraints, pinning, wind/gravity and facet shading | Strong cloth surface primitive; lacks Qwen's cutting but adds shading/UV cloth. | strong overlap |
| 063 | `smoke-study` | **A-** | buoyant smoke particles in curl noise with altitude-dependent turbulence and gusts | Useful smoke heuristic; no Navier–Stokes. | partial overlap |
| 064 | `ember-glow` | **B** | ember glow particles / heat-look | Visual only; no combustion/thermal field. | false friend |
| 065 | `caustic-light` | **A-** | sampled procedural caustic intensity from drifting sine gratings + radial interference | Useful cheap caustic-light approximation; not optics solver. | NEW visual math |
| 066 | `marble-ink` | **A+** | marbling particles advected by curl noise plus animated differential comb shear using snapshot/read-write separation | Distinct surface-pattern/material transform primitive. | NEW/strong |
| 067 | `jellyfish` | **A-** | jellyfish locomotion/tentacle wave ropes + population dynamics | Useful kinematic biological/rope visual; weaker than constraint donors. | overlap |
| 068 | `fireflies` | **B** | firefly steering/random drift | Lightweight agent visual. | overlap |
| 069 | `moon-phases` | **A** | per-pixel Lambert shading of a spherical moon for phase control, deterministic texture/craters, hemisphere flip | Useful illumination-on-sphere primitive; not ephemeris. | NEW/partial |
| 070 | `solar-toy` | **A-** | elliptical planet paths with first-order Kepler-equation offset and real-period scaling | Better than CSS orbits but only approximate Kepler solution. | partial new, below astronomy ground truth |
| 071 | `ring-of-saturn` | **A-** | Saturn ring particle bands with differential band speed and impact shock displacement | Useful ring/annulus particle heuristic; not orbital ring dynamics. | partial new |
| 072 | `comet-catch` | **B** | Bezier comet trajectory + catch interaction | Prescribed path; no orbital mechanics. | false friend |
| 073 | `gravity-sandbox` | **A** | ball sandbox with spatial-hash collision broadphase, impulse resolution and inverse-square-ish black-hole attraction | Useful compact collision + field sandbox. | overlap: Qwen gravity/rigid |
| 074 | `boids-flock` | **A** | Boids cohesion/alignment/separation with spatial bins and predator repulsion | Strong flocking primitive. | overlap: Fable 080 |
| 075 | `ant-colony` | **A+** | ant agents with forward pheromone probes, food pickup/home bias, field deposition, evaporation and box-blur diffusion | Strong agent↔scalar-field feedback system. | NEW/strong |
| 076 | `tree-forest` | **A** | hierarchical branching tree generation + seasonal leaf-state interpolation + wind | Useful procedural tree/environment system. | overlap: Fable L-system, distinct hierarchy |
| 077 | `coral-growth` | **A** | occupancy-grid guided coral branching with candidate-angle scoring and stochastic branching | Useful constrained growth / space-competition heuristic. | NEW/partial |
| 078 | `lightning-fork` | **A-** | recursive/fractal lightning polyline branching with flicker passes | Useful branching-discharge visual generator; no electrodynamics. | partial overlap |
| 079 | `tornado-vortex` | **A-** | vortex particle funnel with radial/orbital motion and debris | Useful vortex heuristic; no fluid/atmospheric solver. | partial new |
| 080 | `dune-wind` | **A** | mutable sand heightfield with wind-carried grains and slope-sensitive erosion/deposition heuristic | Major SHADED idea, but not mass-conserving: several branches add more height than they remove. Treat as aeolian visual heuristic, not sediment physics. | NEW/strong heuristic |
| 081 | `paper-flight` | **A** | paper-plane particles driven by numerically sampled curl wind, drag, gravity and bank/heading smoothing | Useful lightweight aerodynamic/flow-coupling heuristic. | NEW/partial |
| 082 | `orbit-lab` | **A** | mutual inverse-square softened gravity for planet+ship with circular-speed initialization and semi-implicit Euler | Real two-body/multi-body acceleration loop; Muse N-body is stronger. | overlap: Muse 023 |
| 083 | `pendulum-wave` | **A-** | prescribed pendulum-wave oscillator frequency/phase construction | Useful synchronization pattern; not integrated pendulum physics. | overlap: Qwen 030 |
| 084 | `chladni-plate` | **A** | Chladni modal field + gradient-biased grain motion toward nodes | Strong nodal-pattern primitive; frequency mapping remains approximate. | overlap: Fable 076 |
| 085 | `ferris-jelly` | **B** | ferris-wheel kinematics + jelly wobble in rotating capsule frame | Interesting local-frame visual heuristic; not a general solver. | partial new |
| 086 | `coaster-ride` | **A-** | spline-sampled coaster track with slope/angle and car progression | Useful path/spline kinematics; not rigid-body coaster dynamics. | generic |
| 087 | `particle-falls` | **A-** | waterfall/geyser particle emitters, branching streams, mist and ripples | Useful particle water visual; no fluid solver. | overlap visual |
| 088 | `balloon-pop` | **A-** | balloon inflation/float/pop state with gravity/buoyancy-like velocity and audio | Useful interactive state/particle toy; not gas mechanics. | partial |
| 089 | `slime-mold` | **A+** | Physarum-style agents with tri-sensor trail following, trail deposition, diffusion/decay and food interaction | Strong emergent agent↔field morphogenesis primitive. | NEW/strong |
| 090 | `gray-scott` | **A+** | Gray-Scott reaction-diffusion with two float fields, Laplacian, feed/kill and toroidal boundaries | Strong chemical-pattern field primitive. | overlap: Fable 086 |
| 091 | `light-trail` | **B** | long-exposure light-trail drawing | Visual authoring effect. | generic |
| 092 | `letter-physics` | **A** | letter rigid-ish bodies + circle collision impulses coupled to a damped deformable trampoline line | Distinct coupled body↔1D-field/net toy. | NEW/partial |
| 093 | `zen-sand` | **B** | rake grooves, stone placement, breeze erasure | Surface-authoring visual; no granular mechanics. | overlap false friend |
| 094 | `cocktail-builder` | **C** | cocktail recipe/composition UI | No chemistry. | non-donor |
| 095 | `travel-journal` | **C** | travel journal/stamp UI | Presentation only. | non-donor |
| 096 | `recipe-cards` | **C** | recipe-card UI/timers | Routine application logic. | non-donor |
| 097 | `stats-pride` | **C** | statistics dashboard / pride presentation | No computational SHADED donor of note. | non-donor |
| 098 | `type-anim` | **B** | scramble/resolve typography animation | Text animation donor. | generic |
| 099 | `tilt-card` | **B** | pointer tilt/specular card response | Material/UI interaction. | generic |
| 100 | `finale-fireworks` | **A-** | multi-pattern firework particle emitter with scheduler and synthesized bang/crackle audio | Useful event/particle orchestration; no explosive physics. | overlap visual |
