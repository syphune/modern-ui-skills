---
name: creative-web-orchestrator
description: Coordinate creative website and product-interface work across installed design, React, GSAP, R3F, Penpot, Blender, and browser QA capabilities. Use for building immersive sites or coherent product UIs, integrating a design-to-code pipeline, or validating a creative frontend.
---

# Creative web orchestration

Inspect the user's repository, instructions, package manager, lockfile, available skills and tool connections. Preserve existing framework and dependency choices unless the requested outcome needs a change. This skill coordinates specialists; it does not replace their implementation guidance.

## Choose an experience

- **Immersive**: brand stories, showcases, exploration. Establish one visual thesis, a content sequence, and two or three purposeful interactions before building. Typography, material and spatial composition lead; effects support the story.
- **Productivity**: dashboards, search, frequent workflows and forms. Prioritize task completion, information hierarchy, keyboard use, error recovery and loading states. Introduce WebGL or elaborate motion only when it improves the actual task.

Write a small plan appropriate to scope; do not force every pipeline stage. Resolve reversible details autonomously. For consequential art-direction ambiguity, build a concrete prototype and seek feedback while continuing independent implementation. Prototype approval is not a mandatory stop for ordinary authorized work; public deployment, spending, new access and destructive actions retain their normal authorization boundaries.

## Route by capability

Read only relevant installed skills, using [the catalog](references/catalog.md) for names and provenance:

| Need | Capability |
|---|---|
| Art direction and composition | Existing `frontend-skill`, otherwise `frontend-design` |
| React architecture | `vercel-react-best-practices`, `vercel-composition-patterns` |
| UX/accessibility review | `web-design-guidelines` |
| Editable boards, tokens, design inspection | Existing official Penpot MCP |
| Authoring geometry and exporting GLB | Official Blender Python and built-in glTF exporter |
| Live 3D, loaders, events, materials, shaders | Relevant `r3f-*` skills from one coherent collection |
| Sequencing and scroll | Relevant official `gsap-*` skills |
| Browser exploration | Existing Playwright MCP; repository tests use Playwright Test |
| Asset and performance gates | glTF Transform, Khronos glTF Validator, axe, Lighthouse |

Check connection state with a read-only tool call. Penpot must have an authenticated, active plugin tab. Record BLOCKED when unavailable; never substitute fabricated design tokens for a claimed extraction. Use locally defined tokens and clearly label their origin when design access is unavailable.

## Integration invariants

- React owns semantic state. GSAP owns DOM choreography and the scroll-progress scalar. R3F owns object transforms and uniforms. Connect these through refs or a small shared motion signal; do not animate the same transform from multiple systems.
- Keep heavy 3D code behind a dynamic import and a visible static fallback. A reduced-motion or save-data preference takes priority over decorative animation. Essential content and controls remain usable without WebGL.
- Demand rendering is preferred for a scene that can rest. External mutations invalidate frames; damping invalidates only until settled. Unmount listeners, ScrollTriggers and owned GPU resources. Do not dispose shared loader-cache geometry per consumer.
- Use Blender's exporter, glTF Transform and Khronos validation rather than replacing them. Verify actual mesh/material names. Clone mutable per-instance materials; honor asset budgets and loader decoder compatibility.
- Match testing to the change. For substantive creative work, check keyboard/touch, narrow layouts, reduced motion, missing/lost WebGL context, runtime errors, accessibility, animation cleanup and asset loading in a real browser.

## Performance is part of delivery

Build for responsive interaction from the first implementation; performance is
not a cleanup task deferred until the user reports lag. For substantive motion,
WebGL or scroll work, read [quality-preserving performance](references/performance.md)
when choosing the rendering approach and again when validating the result.

- Preserve the agreed visual quality. Optimize redundant computation, rendering,
  event processing and resource lifetime before reducing visible detail. When
  quality must be preserved, do not lower DPR, texture resolution, geometry,
  antialiasing or visible effects to meet a performance target. Do not silently
  introduce adaptive degradation.
- Establish representative desktop and mobile flows and existing performance,
  asset and bundle budgets. Profile loading and sustained scroll/drag/scene
  transitions, plus idle/resume behavior. A good Lighthouse load score does not
  establish smooth interaction; fewer draw calls alone do not establish a speedup.
- Compare before/after at the same viewport, fixed visual preset and canvas
  dimensions. Verify the resulting images and interactions as well as frame
  timings. Record quality adaptation separately from equivalent-quality gains.
- Validate the actual delivery build when available, honoring the repository's
  deployment instructions. Report the measurement environment, observed gains,
  regressions and untested hardware honestly. Do not raise budgets or reduce
  test quality to obtain a passing result.

## Kit discovery and commands

If a toolkit checkout is available, locate its `manifest.json` and `scripts/kit.py` from the project or the user's specified kit location; do not assume a machine path. Use `python3 scripts/kit.py doctor`, `install-project`, `validate`, `update`, and `package` from that checkout as appropriate. A missing kit checkout does not block use of the installed specialist skills and MCP tools.

Keep project-specific settings in `.creative-web-kit.json` and tokens in project source. Never overwrite an existing `AGENTS.md`. The portable installer emits a separate `AGENTS.creative-web.md`; normal project instructions still take precedence.

Report changed behavior, actual tests, budgets and material limitations. Use PASS / FAIL / BLOCKED / NOT_TESTED precisely. Lighthouse navigation does not establish field INP; axe does not certify all WCAG requirements; browser emulation does not certify physical mobile hardware or 60 FPS.
