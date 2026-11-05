---
name: insydium-kb
description: Knowledge base for INSYDIUM tools — X-Particles (CPU xp*), NeXus GPU (nx*) in Cinema 4D and Blender, MeshTools, TerraformFX, Taiao, Jidou — plus Top Tip Tuesday recipes. Use when building or debugging any particle, fluid, smoke/fire, cloth, MPM, trail, terrain, plant or procedural-mesh effect with INSYDIUM Fused or NeXus for Blender.
---

# INSYDIUM knowledge base (X-Particles · NeXus · Fused)

Paraphrased reference built from docs.insydium.ltd (Fused 2025 + NeXus 2026.1 Beta 3, checked 2026-11-03) and INSYDIUM's public YouTube tutorials (Top Tip Tuesday etc.). Not official documentation — when something matters, open the linked source page.

## How to answer with this skill
0. **Lead with the newest tools.** Read `references/whats-new.md` first. By default propose the NeXus 2026.1 route (nxMPM, nxOcean, nxWarp, nxShatter, nxSpawn, nxBioLogic, new falloffs, FLIP non-Newtonian…), then the stable Fused 2025.4 route, then legacy CPU — and say which is beta. Use the release dates there to tell the user when a tip/tutorial is outdated.
1. **Identify host and generation** (read `references/legacy-vs-nexus.md`):
   - Cinema 4D CPU X-Particles (`xp*`), NeXus inside X-Particles (`nx*` on an orange xpEmitter), or NeXus 2026 (`nxEmitter`, C4D beta / Blender).
   - If the user doesn't say, ask which host + version, or give the modern NeXus path first and the CPU fallback second.
2. **Find the effect** in `INDEX.md` (task → objects → recipe files).
3. **Read the object references** you need from `references/` and any matching `recipes/` files — `grep -i <tool or effect> recipes/README.md` finds them (309 recipes, newest first; Blender recipes are tagged `blender-` / Host: Blender).
4. **Answer as a build recipe:** scene hierarchy (tree), objects in order, the few parameters that matter with starting values, how to cache/mesh/render, and common gotchas. Say which generation each step uses. Convert units for Blender (C4D cm/Y-up → Blender m/Z-up).
5. If a recipe is from an older version, flag what changed (see "Things that changed" in legacy-vs-nexus.md).
6. Don't invent parameter names. If a name isn't in these files, say so and suggest checking the docs page.

## Files
- `references/whats-new.md` — release timeline (2022 → 2026.1 Beta 3) + "newest way" cheat sheet. **Read first.**
- `INDEX.md` — effect/task index.
- `references/legacy-vs-nexus.md` — generations, xp→nx mapping table, breaking changes.
- `references/video-facts.md` — parameters, defaults and behaviours gathered from ~310 INSYDIUM videos (2023–2026), plus `references/legacy-catalog/` — a short catalog of ~220 older 2017–2022 videos (X-Particles 3.5/4, Premium/Maintenance Training) with what each shows and today's equivalent, grouped by generation. Use for "what does this setting do / default" questions.
- `references/c4d/xp-emitter.md` — xpEmitter all tabs.
- `references/c4d/xp-system-cache-control.md` — xpSystem, xpCache, project settings, Questions/Actions, data mapping, QuickTools, xpPainter.
- `references/c4d/xp-modifiers-motion.md` — CPU motion modifiers table (+xpSpawn).
- `references/c4d/xp-modifiers-control-generate.md` — CPU control/generate/sprite modifiers.
- `references/c4d/xp-generators-dynamics.md` — generators (xpGenerator, xpTrail, meshers, xpShatter…), CPU dynamics (ExplosiaFX, fluids, cloth, Bullet), tags.
- `references/c4d/xp-utilities-render.md` — utilities, groups/actions, rendering & shaders.
- `references/c4d/nexus-core.md` — NeXus concepts, nxConstraints, nxFluids, nxExplosiaFX, nxMesher.
- `references/c4d/nexus-dynamics-logic.md` — nxFoam/Splash/Wave, nxQuestion (GLSL), Mapping, nxFalloff, prefs, nxTurbulence.
- `references/c4d/nexus-modifiers.md` — all nx modifiers.
- `references/c4d/meshtools.md`, `terraformfx.md`, `taiao-jidou.md`.
- `references/blender/nexus-blender.md` — NeXus for Blender setup, Blender-only objects, 2026.1 Beta (nxMPM, nxOcean, nxWarp, nxShatter, nxSpawn…).
- `recipes/` — one file per tutorial/Top Tip: goal, scene tree, steps, version, link.
