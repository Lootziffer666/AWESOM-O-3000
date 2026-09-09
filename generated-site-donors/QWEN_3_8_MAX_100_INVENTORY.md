# QWEN 3.8 MAX — FULL 100/100 INVENTORY

Companion to [`QWEN_3_8_MAX_100.md`](QWEN_3_8_MAX_100.md). Grades and relation labels are based on a complete static pass over all 100 numbered HTML files.

| ID | Page | Grade | Actual computational value | Assessment | Relation to earlier collections |
|---:|---|:---:|---|---|---|
| 001 | `aurora-glass` | **B** | pointer-driven card tilt/specular highlight | Material/UI response only; no aurora physics. | OVERLAP / visual |
| 002 | `floating-planets` | **B** | procedural drifting circles/planets + click scan pulse | Useful simple parallax/orbit presentation; no orbital dynamics. | FALSE FRIEND / visual |
| 003 | `dreamlike-gradients` | **B** | eased gradient/orb interpolation + click bloom | Motion/color donor only. | VISUAL |
| 004 | `neon-cyberpunk-city` | **B** | procedural skyline + rain particles | Scene generator/particle presentation; no weather physics. | VISUAL |
| 005 | `brutalist-manifesto` | **C** | scroll reveal + cursor telemetry + runtime grain | Presentation only. | NON-DONOR |
| 006 | `neumorphic-sound-panel` | **B** | knob/fader interaction + simulated VU meters | Control-surface interaction; no real DSP/audio graph. | FALSE FRIEND |
| 007 | `editorial-magazine` | **C** | editorial interaction/layout | No meaningful computational donor. | NON-DONOR |
| 008 | `futuristic-hud` | **B** | procedural HUD/radar/sparkline drawing | Useful instrumentation rendering patterns, not simulation. | VISUAL |
| 009 | `organic-blob-flow` | **A-** | damped spring-back blob deformation + click impulse/ripple | Compact spring interaction heuristic; not fluid dynamics. | NEW-ish / heuristic |
| 010 | `experimental-type-poster` | **B** | kinetic typography motion | Animation donor only; gravity naming is visual. | VISUAL |
| 011 | `particle-constellation` | **A-** | particle constellation with pairwise links/bursts and simple steering | Reusable particle/network interaction, but no spatial acceleration. | OVERLAP: Fable particles |
| 012 | `liquid-background` | **B** | chaser-chain particles following pointer/previous particle | Useful follow-chain motion heuristic; not liquid simulation. | FALSE FRIEND / heuristic |
| 013 | `morphing-gradient-orbs` | **B** | orbital gradient-orb interpolation/morph | Visual state interpolation only. | VISUAL |
| 014 | `elegant-dashboard` | **A-** | smoothed chart curves + data animation/tooltip logic | Reusable chart interpolation/rendering; not SHADED-core. | GENERIC |
| 015 | `premium-landing` | **C** | count-up + spotlight cards | Routine landing-page interaction. | NON-DONOR |
| 016 | `portfolio-showcase` | **B** | cursor follower + floating preview with inertia-like easing | Reusable interaction motion only. | GENERIC |
| 017 | `interactive-art-canvas` | **A+** | seeded 2D value noise + fBm flow field + particle advection + pointer vortex | Strong deterministic flow-field primitive; not a fluid solver. | OVERLAP: Fable 013, stronger implementation detail |
| 018 | `dataviz-pulse` | **B** | synthetic time-series generator + smooth multi-series canvas chart | Visualization donor; data are synthetic. | GENERIC |
| 019 | `motion-hero` | **B** | depth-weighted pointer parallax | Presentation motion only. | VISUAL |
| 020 | `creative-navigation` | **C** | navigation overlay state | Routine UI. | NON-DONOR |
| 021 | `loading-symphony` | **B** | timeline/loading state machine + dust motes | Useful choreography/timing pattern. | GENERIC |
| 022 | `microinteractions-playground` | **B** | magnetic/toggle/like/checkbox/progress microinteraction set | Interaction donor; not physics despite magnetic styling. | GENERIC |
| 023 | `scroll-story` | **B** | scroll-driven chapter palette + particle transitions | Scene-state choreography only. | VISUAL |
| 024 | `infographic-climate` | **B** | synthetic climate-anomaly formula + color mapping + animated infographic | Useful scalar→color visualization, but not climate data/model. | FALSE FRIEND / synthetic |
| 025 | `immersive-hero-nebula` | **A-** | 3D spiral-arm particle distribution + manual perspective projection + radius-dependent angular drift | Useful procedural galaxy/projection donor; not accretion/orbital physics. | OVERLAP: Fable 041/029 |
| 026 | `generative-art-gallery` | **A** | rejection circle packing + recursive subdivision + random walk + recursive branching | Multiple compact generative algorithms in one gallery. | PARTLY NEW: circle packing |
| 027 | `css-only-artwork` | **C** | CSS-only artwork | No computational donor. | NON-DONOR |
| 028 | `canvas-physics` | **A-** | gravity + wall collision/restitution + drag/throw velocity for balls | Compact kinematic toy; no ball-ball collision or robust rigid body solver. | WEAKER OVERLAP: Fable 077 |
| 029 | `svg-animation-scene` | **B** | SVG balloon animation + pointer parallax | Presentation motion only. | VISUAL |
| 030 | `physics-pendulum` | **A** | pendulum-wave construction using prescribed oscillator frequencies/phases | Good oscillator/phase synchronization primitive; not integrated pendulum dynamics. | NEW distinct from Fable 033 |
| 031 | `zen-pomodoro` | **B** | Pomodoro state + WebAudio chime/breath animation | Timing/audio utility. | GENERIC |
| 032 | `weather-glass` | **B** | weather icon/temperature/rain visual state | Weather presentation only; no meteorological model. | FALSE FRIEND |
| 033 | `habit-tracker` | **A-** | habit heatmap + streak computation + state persistence | Useful discrete streak/temporal-state logic; generic. | GENERIC |
| 034 | `music-visualizer` | **A+** | WebAudio synth: sequencer scheduling, oscillator voices, filter envelopes, delay feedback, compressor, FFT visualization | Strong browser audio/signal compound donor. | OVERLAP: Fable 032/089; still strong |
| 035 | `color-lab` | **A** | seeded palette generation + HSL↔RGB/hex conversions + harmony modes | Reusable deterministic color-math/palette primitive. | OVERLAP: Fable 046, broader palette generation |
| 036 | `typography-specimen` | **C** | typography controls | Routine presentation. | NON-DONOR |
| 037 | `calculator-neo` | **A** | safe arithmetic tokenizer + recursive-descent expression parser/evaluator | Real compact parser algorithm; generic rather than SHADED-core. | NEW generic |
| 038 | `markdown-notes` | **A-** | small Markdown parser + escaping + local persistence | Useful compact text parser/state primitive; generic. | NEW generic |
| 039 | `chess-board` | **A** | chess pseudo-legal move generator with ray sliding, capture, promotion | Real discrete board topology logic; omits check/castling/en-passant. | NEW generic |
| 040 | `synth-keyboard` | **A** | WebAudio polyphonic keyboard + MIDI→Hz + attack/release envelopes + oscilloscope | Real synth primitive; less extensive than Fable 089. | OVERLAP: Fable 089 |
| 041 | `ocean-waves` | **B** | multi-sine layered ocean surface with pointer/wind modulation | Useful stylized wave geometry; no wave PDE/ocean solver. | FALSE FRIEND / overlap |
| 042 | `starry-night-sky` | **B** | procedural star field + constellation layout + shooting-star animation | Astronomy presentation only. | WEAKER OVERLAP: Fable 097 |
| 043 | `fireflies-forest` | **B** | firefly random drift + cursor avoidance | Simple steering/particle heuristic. | OVERLAP: particle donors |
| 044 | `rainy-window` | **B** | window wiping via destination-out + refogging + kinematic raindrop trails | Good surface/condensation visual interaction; no coalescence/material transport. | WEAKER OVERLAP: Fable 052 |
| 045 | `cherry-blossom-fall` | **B** | petal fall particles with wind/drift | Particle-motion heuristic. | OVERLAP |
| 046 | `desert-dunes` | **B** | harmonic dune silhouettes + time-of-day palette interpolation | Visual terrain profile; no erosion/sediment transport. | FALSE FRIEND |
| 047 | `northern-lights` | **B** | multi-sine aurora curtain field + additive rendering | Procedural aurora visual only; no plasma/magnetosphere physics. | FALSE FRIEND |
| 048 | `underwater-jellyfish` | **B** | kinematic jellyfish pulse/drift + sinusoidal tentacles + cursor avoidance | Visual organism motion; no Verlet/constraints/fluid coupling. | WEAKER OVERLAP: Fable 090 |
| 049 | `autumn-leaves` | **B** | falling/settling leaf particles | Particle heuristic only. | OVERLAP |
| 050 | `sunrise-timelapse` | **B** | keyframed sunrise palette + procedural clouds/stars/birds | Environment state interpolation; no atmospheric/solar model. | VISUAL |
| 051 | `geometric-abstraction` | **B** | random geometric composition | Procedural composition only. | OVERLAP: Fable 018 |
| 052 | `truchet-tiles` | **A-** | Truchet tile topology + eased orientation changes + diagonal wavefront queue | Useful tile connectivity/propagation choreography. | NEW-ish |
| 053 | `moire-patterns` | **A-** | constructive Moiré interference from concentric rings/line grids | Useful geometric interference primitive, not wave physics. | NEW visual/math |
| 054 | `spirograph` | **A** | damped multi-frequency harmonograph / spirograph curve generator | Real oscillator superposition with exponential decay. | OVERLAP: Fable 062 |
| 055 | `voronoi-mosaic` | **A** | raster Voronoi by brute-force nearest-site classification + animated sites + boundary detection | Real Voronoi field rasterizer; less exact/elegant than Fable polygon clipping. | WEAKER OVERLAP: Fable 024 |
| 056 | `cellular-automata` | **A** | Conway-style cellular automaton with double buffer, age field and pattern stamps | Reusable cellular update primitive. | OVERLAP: Fable 043 |
| 057 | `fractal-tree` | **A+** | seeded recursive branching tree + depth-controlled growth + hierarchical wind sway | Strong procedural growth geometry. | OVERLAP: Fable 057 |
| 058 | `golden-spiral` | **A** | golden-angle/Fermat phyllotaxis r∝√i plus optional golden-rectangle spiral guide | Real compact packing/plant arrangement math. | OVERLAP: Astra 040 |
| 059 | `waves-interference` | **A+** | 2D radial wave-source superposition field sampled per pixel-cell | Strong interference-field primitive; distinct from 1D harmonic wave demos. | NEW / complementary |
| 060 | `kaleidoscope` | **A** | kaleidoscopic wedge rotation/reflection replication | Reusable symmetry transform for drawing/geometry. | OVERLAP: Fable 068 |
| 061 | `vaporwave-sunset` | **C** | CSS vaporwave scene | No computational donor. | NON-DONOR |
| 062 | `art-deco-poster` | **C** | art-deco poster presentation | No meaningful computational donor. | NON-DONOR |
| 063 | `japanese-wabisabi` | **B** | procedural irregular line/path drawing | Minor visual geometry donor. | VISUAL |
| 064 | `memphis-playground` | **B** | procedural Memphis SVG/geometric shape composition | Procedural graphics only. | VISUAL |
| 065 | `synthwave-outrun` | **B** | procedural synthwave grid/mountains/road animation | Projection/presentation donor only. | VISUAL |
| 066 | `art-nouveau-frame` | **B** | procedural SVG art-nouveau frame/mosaic rings | Parametric ornament geometry; low SHADED relevance. | VISUAL |
| 067 | `pixel-arcade` | **A-** | arcade projectile/asteroid collision + particle explosions + difficulty scaling | Compact game-loop/collision primitive; generic. | GENERIC |
| 068 | `ukiyoe-waves` | **C** | static/CSS ukiyo-e wave art | No water simulation. | FALSE FRIEND |
| 069 | `stained-glass` | **B** | parametric radial stained-glass/petal geometry | Useful radial procedural ornament. | OVERLAP: Fable 081 |
| 070 | `paper-cut-layers` | **C** | paper-cut layered presentation | No fold/material mechanics. | FALSE FRIEND |
| 071 | `crypto-dashboard` | **B** | synthetic crypto dashboard/ticker updates | Visualization only; synthetic market behavior. | SYNTHETIC |
| 072 | `analytics-realtime` | **B** | synthetic real-time analytics chart + event spikes | Streaming visualization pattern; synthetic data. | GENERIC |
| 073 | `task-kanban` | **C** | Kanban state management | Routine UI. | NON-DONOR |
| 074 | `fitness-rings` | **B** | SVG progress-ring geometry + eased animation | Generic radial gauge primitive. | GENERIC |
| 075 | `smart-home-ui` | **C** | smart-home heating dial/state UI | No thermal model. | FALSE FRIEND |
| 076 | `music-player` | **B** | simple WebAudio player/oscillator state | Real audio but minimal and UI-centric. | WEAKER OVERLAP |
| 077 | `flight-dashboard` | **C** | flight dashboard preset/status animation | No flight/navigation dynamics. | FALSE FRIEND |
| 078 | `stock-ticker` | **B** | synthetic stock ticker + sparkline generation | Visualization only; synthetic market behavior. | SYNTHETIC |
| 079 | `project-timeline` | **C** | project timeline UI | Routine application state. | NON-DONOR |
| 080 | `network-graph` | **A+** | force-directed graph layout: inverse-square repulsion + spring edges + damping + center force | Strong compact spatial graph-layout primitive. | NEW |
| 081 | `fluid-simulation` | **B** | noise/sine-derived flow-angle field + particle advection | Named fluid simulation but is only flow-field particles. | FALSE FRIEND; Fable 016 is real fluid |
| 082 | `cloth-simulation` | **A+** | 2D Verlet cloth grid + iterative distance constraints + pinning + wind + interactive cutting | Excellent deformable-surface primitive; extends Fable rope/tentacle donor into cuttable cloth. | NEW EXTENSION / strong |
| 083 | `gravity-wells` | **A+** | multi-well inverse-square attraction field + particle orbital injection + absorption | Strong compact n-body-like test-particle gravity primitive; idealized units/time step. | NEW |
| 084 | `boids-flocking` | **A** | Boids cohesion/alignment/separation + pointer predator/bait + speed bounds | Correct flocking rules but O(N²), weaker scaling than Fable spatial-grid version. | WEAKER OVERLAP: Fable 080 |
| 085 | `sandbox-particles` | **A+** | cellular falling-sand solver with sand/stone/erase, downward/diagonal movement and scan-order alternation | Strong minimal granular-material primitive. | NEW; fixes Fable's fake sand gap |
| 086 | `drawing-canvas` | **A-** | pressure-like variable-width drawing canvas with undo/history | Useful authoring/raster interaction; generic. | OVERLAP: Fable 039 |
| 087 | `audio-reactive` | **A** | WebAudio analyser with drone/microphone inputs, FFT radial bars and time-domain waveform | Real audio-reactive signal primitive; no beat detector. | OVERLAP: Fable/DeepSeek audio |
| 088 | `terrain-flyover` | **A+** | Voxel-Space-style heightfield renderer: procedural height function + front-to-back column ray casting + distance stepping/fog | Excellent lightweight terrain-rendering primitive. | NEW |
| 089 | `raymarcher-shader` | **A+** | CPU sphere tracing over signed-distance fields + finite-difference normals + diffuse/specular/fog shading | Strong dependency-free SDF/raymarch reference despite low resolution. | NEW |
| 090 | `lissajous-lab` | **A** | Lissajous curve synthesis from orthogonal oscillators with guide projections | Clean oscillator/parametric-curve primitive. | NEW-ish / related to Fable 062 |
| 091 | `luxury-watch-landing` | **B** | procedural watch ticks + real-time hand angles | Parametric time geometry only. | GENERIC |
| 092 | `coffee-brand` | **C** | coffee brand page | No computational donor. | NON-DONOR |
| 093 | `travel-explorer` | **C** | travel explorer scene/content switching | Presentation only. | NON-DONOR |
| 094 | `saas-gradient` | **B** | gradient SaaS mockup + pointer tilt | Presentation/material response. | VISUAL |
| 095 | `crypto-exchange` | **B** | synthetic exchange order-book/feed updates | Streaming table visualization; synthetic data. | SYNTHETIC |
| 096 | `fashion-editorial` | **C** | fashion editorial page | No computational donor. | NON-DONOR |
| 097 | `architecture-studio` | **C** | architecture studio page | No computational donor. | NON-DONOR |
| 098 | `perfume-atelier` | **C** | perfume atelier page | No chemistry/material simulation. | FALSE FRIEND |
| 099 | `culinary-menu` | **C** | culinary menu page | No cooking/thermal/chemical model. | NON-DONOR |
| 100 | `organic-wave-lab` | **A-** | multi-sine layered wave surface + localized Gaussian pointer wake + crest riders | Useful deformable surface/wake visual heuristic; not a water PDE. | NEW visual heuristic / overlap |
