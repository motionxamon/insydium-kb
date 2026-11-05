# X-Particles — Control, Generate and Sprite modifiers (CPU, `xp*`)

Source: docs.insydium.ltd/x-particles/modifiers/* (Fused 2025, checked 2026-11-03). Paraphrased. All have Mode Independent / Action-Controlled, Groups, Falloff/Fields, Mapping.

## Control
- **xpBlend** — mix radius/mass/color/scale/rotation between neighbours within Distance; Strength, Max Blend (end frame), Weight curve. → nxBlend (much faster).
- **xpChangeGroup** — move particles to New Group (required), optional color/speed/mass change; Threshold, Probability. Fast particles + low probability may never switch.
- **xpColor** — Immediate / Fade Between / Gradient / Random…; also can change display shape. Threshold 100% blocks changes. "Set Color" ramps only inside a falloff. → nxColor.
- **xpCustomData** — Increment/Decrement or Set Value on emitter Custom Data items (Data Type must match). Matrix/String not mappable.
- **xpFreeze** — stop movement/spin/scale (tick at least one), Freeze/Unfreeze, Set Speed to Zero. Fast particles can slip through falloff.
- **xpHistory** — replay each particle's past motion from At Time (needs **Rewind Data** in emitter Extended Data); Freeze During Playback. Use: rewind/reverse effects.
- **xpInfectio** — spread from Seed Object(s) (required); Search Radius, Max Infected, Incubation by particle color, Immunity, Infected Lifespan 10 s. → nxInfectio.
- **xpInherit** — copy velocity/color/radius/position from particles of a **Target Emitter**; Distance Relative/Absolute, Time, Immediate; Probability, Weight. Use: particles "becoming" another formation.
- **xpKill** — Outside Bounds (default) / Inside / Objects / Outside Camera FOV / Clamp to Max; Only Born; Isolated + Distance. → nxKill.
- **xpLife** — Kill / Increase-Decrease / Set New Lifespan / Set Relative to Age; New Lifespan < age = instant death.
- **xpNegate** — clear flags: frozen, stuck/sticky, source attachment, break constraints; Cover Modifier link to stop re-grab.
- **xpPhysical** — change temperature, smoke, fuel, fire, bounce, friction over time/set/shader (default temp +100/frame — lower it!). Feeds xpExplosiaFX.
- **xpPython** — Python per particle in field (`import xparticles; help(xparticles)` in console for API).
- **xpScale** — Radius (default) / Scale / Mass; Operation Set Value, Falloff, Jiggle (scale only), Spline, Speed, Shader. Radius ≠ geometry scale. → nxScale.
- **xpSound** — drive params from .wav frequency/loudness (FFT, dB range, freq bands, Map Sound). Doesn't play audio — add a C4D sound track.
- **xpTrailsMod** — Shrink / Expand / Grow (needs xpTrail Length Mode Time) / Pulse trail length; Rate in trail points.
- **xpTransform** — particles copy a linked object's position/scale/rotation movement.
- **xpTriggerAction** — fire Actions (or toggle Action-Controlled modifiers) when entering a falloff; Probability, Trigger Count. Listed modifiers must be Action-Controlled.
- **xpUnlinkTP** — detach Thinking Particles (irreversible).
- **xpWeight** — extra strength control for other modifiers by Age/Lifespan/Color/Speed/Shader (Weight Parameter default None = no effect).

## Generate
- **xpSpawn** — see motion table (needs Spawning Emitter).
- **xpMultiSpawn** — multi-level spawning *inside the same emitter* (each level spawns from the one above): Spawn Count per frame, Frames, Start At Age, Kill Source, child Life/Speed/Direction. Use: fireworks. Exponential growth — keep levels/counts low.
- **xpBranch** — procedural branching for xpTrail / xpSplineMesher; needs child **Sub-Branch** object; Length Method Time 3 s, Bending Zigzag, Curl Angle <5°. Use: lightning, trees, cracks, roots.
- **xpTendril** — stream tendril particles from each source (tentacles); Interval 1 F, Tendril Length, Follow Source (ignores other modifiers), Max Tendril Particles.
- **xpDynamicParticles** — temporary filler particles that fade in/out by radius to keep density (fluids); don't use the source emitter as spawning emitter; Maintain Count + Max Count.
- **xpGeometry** — switch which child object of xpGenerator a particle shows (Index of Child Object; invalid = vanish); Threshold.
- **xpMorph** — morph generator objects between targets (Morph Target Index from 1; Rate of Change). Threshold 100% may fail with subframes >1 → use 98–99%.

## Sprites (with xpSprite generator)
- **xpLight** — animate brightness/inner distance of sprite lights via splines (Particle Age or Step Count).
- **xpSpriteControl** — swap sprite type/material (Material Index) per particle.
- **xpSpriteShaderControl** — controls the xpSpriteShader on sprites.
- **xpText** — change text on text sprites (letters/numbers/user text, increment, case) — overrides xpSprite text settings. Use: counters, falling-code text.
