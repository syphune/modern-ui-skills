# Installed capability catalog

Sources reviewed 2026-10-28. Locate skills in the runtime's discovered skill roots before requesting another installation. Existing differently versioned skills are preserved and reported; the kit's upstream lock records the portable installation baseline separately.

- Design: `frontend-skill` already present in this host; portable fallback `frontend-design`, [Anthropic](https://github.com/anthropics/skills/tree/dbd4588f9e1033efb41dad4bef2f7947c8993d44/skills/frontend-design), Apache-2.0.
- React/UX: `vercel-react-best-practices`, `vercel-composition-patterns`, `web-design-guidelines`, [Vercel](https://github.com/vercel-labs/agent-skills/tree/1a2c79d4e6c4a2283dc2c614b6538cbe1ed5ca62/skills), MIT declarations in skill metadata.
- Motion: `gsap-core`, `gsap-timeline`, `gsap-scrolltrigger`, `gsap-react`, `gsap-performance`, `gsap-plugins`, [GreenSock](https://github.com/greensock/gsap-skills/tree/aed9cfd3277740755f6bfc1155c7aa645403b760/skills), MIT skills. GSAP runtime has its own [standard license](https://gsap.com/standard-license/).
- Real-time 3D: `r3f-fundamentals`, `r3f-geometry`, `r3f-materials`, `r3f-lighting`, `r3f-textures`, `r3f-loaders`, `r3f-animation`, `r3f-shaders`, `r3f-postprocessing`, `r3f-interaction`, [EnzeD](https://github.com/EnzeD/r3f-skills/tree/4a11805f097396fb0b893172efd1e359e8051f92/skills). MIT declared in upstream README; preserve that declaration with installed files.
- Browser: existing [Microsoft Playwright MCP](https://github.com/microsoft/playwright-mcp), no additional browser-agent server. Playwright Test in consuming repositories serves a separate, reproducible regression-test role.
- Design: [official Penpot MCP](https://help.penpot.app/mcp/); never create a replacement server or copy authentication keys into project files.
- Asset authoring: [official Blender Python](https://docs.blender.org/api/current/), no socket server. [glTF Transform](https://gltf-transform.dev/) and [Khronos Validator](https://github.com/KhronosGroup/glTF-Validator) handle optimization and validation.

The installed UI/UX Pro Max CLI is an optional research resource. Its current repository includes extra capabilities and executable scripts; do not auto-install the expanded suite merely to obtain typography or palette advice. Shader recipes use the existing Three.js/R3F stack; SVG choreography uses GSAP. No additional framework is required for either.
