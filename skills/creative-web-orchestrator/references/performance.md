# Quality-preserving interactive performance

Use for substantial animation, 3D and scroll-driven frontend work. Keep the
chosen visual experience and interaction quality as constraints while removing
wasted work. Apply the relevant parts; a small static edit needs no 3D benchmark.

## Establish the comparison

- Define representative flows early: first usable scene, sustained native
  scrolling, pointer/touch drag, view transitions, resize/orientation, rest and
  resume. Recheck the affected flows after significant scene additions.
- Record the actual viewport, device scale, canvas buffer dimensions, texture
  sizes, geometry detail and visible effects. Retain existing budgets; use the
  project's targets rather than inventing universal pixel or polygon ceilings.
- With an existing implementation, capture a baseline. For a new site, measure
  the representative flows against the chosen budgets before handoff. A loading
  audit alone is insufficient for an interactive scene.
- Run comparable probes sequentially on the same build mode, renderer and
  quality preset. Avoid competing browser jobs/builds. Keep scroll distance,
  duration and input sequence comparable; save raw timings and matched views.
- Hold resolution fixed for an equivalent-quality comparison. An adaptive
  fallback may make a frame test faster by blurring the image. Document such
  product behavior separately, and do not add it when quality preservation was
  requested. Test that slow frames do not secretly change the agreed preset.

## Find the expensive work

Separate startup, main-thread, GPU/render and compositing costs using traces or
profiling evidence. Check frame-time distributions and sustained interactions,
not just averages. Missing main-thread tasks over 50ms does not prove a GPU
bottleneck: repeated shorter tasks can still miss the frame budget. Draw calls,
triangles and memory counts explain work but are not substitutes for timing.

Inspect first context creation, shader compilation and texture upload separately
from steady-state rendering. Native driver/extension calls can synchronize GPU
work. Introduce warm-up or workers only for a measured problem, with bounded
startup, cancellation, cleanup and a normal initialization fallback.

## Remove work while preserving the image

- **Rendering lifetime:** keep expensive modules lazy; use demand rendering when
  the scene can rest. Wake for input and damping, stop after settling, and pause
  when hidden/inactive. Preserve static, reduced-motion and save-data paths.
- **Stable state:** reuse buffers, geometries, materials, textures, scratch
  vectors and uniform containers. Mutate frame values through refs; keep React
  updates for semantic state. Avoid repeated media queries, resource creation
  and redundant DOM/style/telemetry writes inside frame loops.
- **Shader work:** skip procedural shading that a loaded map replaces. Skip
  provably invisible fragments only when depth/blend behavior stays equivalent.
  Keep lighting spaces, color conversion and exposure consistent.
- **Static expensive layers:** consider an owned GPU cache when the result is
  static or depends on a small explicit set of inputs. Preserve radiance/alpha,
  useful resolution and invalidation behavior. Restore render target, viewport
  and scissor state; dispose owned resources without disposing shared caches.
- **Submissions:** share geometry/materials or batch/instance compatible objects
  when measurement justifies it. Preserve transforms, picking, normals,
  per-object colors and transparency/depth ordering. Fewer draws can still be
  slower or change the image; verify both.
- **Covered pixels:** a CSS mask/clip may leave the entire WebGL buffer being
  shaded. Where applicable, mirror its visible bounds with a GPU scissor. Round
  outwards for physical-pixel conversion, including separate origin/extent
  flooring and DPR below one. Restore full drawing on scene changes and resize.
- **Events/layout:** limit raycasts to interactive surfaces; retain accessible
  DOM/keyboard alternatives. Batch layout reads before writes and coalesce
  scroll work. Preserve native vertical touch scrolling and gesture ownership.

Do not replace an expensive effect with a cheaper-looking approximation and
describe that as quality-preserving optimization. Geometry, texture, MSAA and
resolution reductions are visual trade-offs, not equivalent-quality gains.

## Validate and hand off

- Check the affected desktop and mobile flows, actual shader/runtime errors,
  visual detail, native touch behavior and applicable resource cleanup. Use
  targeted regressions for meaningful invariants such as fixed quality under
  slow frames, clipping boundaries and restoration, or no rendering at rest.
- Compare matched poses/views and preserve animation behavior. Freeze time only
  in controlled comparison fixtures when useful; also test normal playback.
- Verify the delivery build and existing asset/bundle budgets. Follow project
  instructions for local deployment; this reference grants no external deploy
  authorization.
- Report what became faster and what did not, with viewport/quality and renderer
  context. Distinguish software-GPU browser emulation from physical hardware,
  RAF intervals from GPU timer measurements, and lab tests from field INP.
  Do not claim universal smoothness, physical mobile compatibility or 60fps from
  a loading score or a single emulated run. Investigate material regressions;
  disclose unresolved limits rather than cherry-picking a favorable scene.
