# SHADED OCEAN — VISUAL TARGET

**Purpose:** art-direction supplement for `SHADED_OCEAN_HANDOFF.md`.

## Target look

The ocean should read as a **stylized, graphic, highly legible animated world**, not as a photorealistic water showcase.

Key visual traits:

- broad turquoise / cyan / teal water masses with depth darkening toward deep petrol/blue-green;
- clean separation between sky, surface and underwater volume;
- large readable silhouettes rather than dense micro-detail;
- bright, sparse crest/foam lines that describe wave shape clearly;
- soft underwater light shafts / broad illumination bands rather than noisy caustic glitter;
- strong atmospheric depth and silhouette falloff underwater;
- restrained reflections/refraction;
- simplified, coherent material response rather than highly detailed PBR noise;
- low-frequency surface structure dominates; high-frequency normals should be subtle;
- visual hierarchy should survive at a glance: surface first, major forms second, small particles last.

The visual reference is a **look-language target**, not a requirement for a permanent 2D cutaway camera. In 3D, preserve the same graphic hierarchy and palette logic.

## Donor priority adjustment

### Keep as primary simulation references

- GLM 5.3 special 512x512 GPU heightfield / ping-pong water implementation.
- Fable 099 `water-ripple-reflection`.
- Qwen 27B 005 `tideglass-water`.
- DeepSeek v4 050 `cursor-ripple`.

These define the interactive surface state. Their output should be rendered in the stylized visual language above rather than used to justify photorealistic shading.

### Keep as backend / field architecture references

- Fable high-effort `Synesthesia` — GPU field pipeline reference, not visual target.
- Fable 016 `fluid-smoke-touch` — independent CPU/solver reference, not direct ocean look.

### Use selectively for interface optics

- Fable 082 `prism-light-dispersion` — keep only the physically useful refraction/reflection/TIR logic.
- Do not turn the water into glass. Prefer restrained distortion and a readable boundary over aggressive refraction.

### Surface material / foam direction

Foam should be derived from simulation state such as local wave energy, curvature, impact energy or velocity and rendered as **clean bright bands / patches / streaks**.

Avoid making foam primarily from dense independent particles.

Qwen 27B 069 `leaf-storm` remains conceptually useful for the pattern `moving material -> persistent surface state`, but the visual treatment should stay sparse and graphic.

### Underwater direction

Prefer:

- depth-based color absorption;
- soft volumetric light bands;
- large silhouette layers;
- restrained suspended particles;
- simplified material shading;
- strong near/mid/far depth separation.

Avoid:

- high-frequency screen-space glitter;
- dense caustic noise;
- excessive micro-normal detail;
- chrome/glass-like water;
- photorealistic foam clutter;
- particle fog thick enough to obscure major forms.

## Rendering principle

**Simulation can be physically richer than the image. Rendering should expose only the information that improves readability.**

The desired result is not "less simulation". It is **real world-state rendered with deliberate reduction**.
