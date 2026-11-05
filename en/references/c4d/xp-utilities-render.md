# X-Particles — Utilities, Actions, Groups, Rendering

Source: docs.insydium.ltd/x-particles/{utilities,x-particles-render-settings-materials-shaders-a}/* (Fused 2025, checked 2026-11-03). Paraphrased.

## Utilities
- **xpGroup** — particle groups targeted by modifiers/actions. Unique Group Number; Mode Standard / Display Only / **Extended** (mass, friction etc. only here). Emitter must list it in **Groups to Use**. Particle sphere/circle size still from emitter.
- **xpAction** — what happens when a Question passes (or collision fires). Types: Object (Change Emitter / Generator / Trails), Control Modifier (toggle modifiers), Direct (Change Geometry, Change Group), Dynamics (Sheeter), Other (Output to Console, Stop Following Spline, Unlink TP, Unstick from Source); Change Editor Display. Actions created from menus aren't auto-linked to a Question.
- **xpDeformer** — mesh vertices follow particles (child of the mesh; emitter Points + One Particle Per Source Element, Emit All Frames off). Use: turn any mesh into particle-driven deformation (melt, blow-away with turbulence).
- **xpTrailDeformer** — wiggle/flow xpTrail splines with per-axis formulas (`u` along length, degrees), Amplitude, Wavelength, shader displacement (Mix default 0%!). Top Tip #1 subject (natural flowing trails).
- **xpSplineGrowth** — grow/shrink splines/trails (child of spline): Point-by-Point / Whole / Section, Invert, random Min Length. Use: animated line drawing.
- **xpVertexMap** — animated vertex maps from seeds/particles/shaders/speed/curvature/occlusion layers (growth maps for MeshTools/Taiao/shaders). No hierarchies.
- **xpVolumeEmit** — start/stop emitter when it (or an object) is inside/outside closed volumes.
- **xpCirclePacker** — fill space with non-overlapping circles/spheres (Min/Max Radius, Separation). Raise Birthrate (rejected particles are deleted).
- **xpJoin** — merge objects into one source/collider (only same types). Use with cloners/many objects (e.g. xpRainRig hits).
- **xpMetaGroup** — group groups.
- **xpDataExporter / xpDataImporter** — CSV snapshot export/import (position, direction, color, rotation). **xpOpenVDBImporter** — bring VDBs in.
- **xpConsole** — particle data console/debug.

## Rendering
- **X-Particles Material** (native, Physical/Standard renderer): renders particles, splines and volumes without geometry. Color by Age/Speed etc., transparency, Size (Particle Radius / World / Screen), **Filling** (render-only extra particles), Volumetric. Apply to a Group to render only it. Splines need linked xpTrail. With GI set Self Illumination > 0.
- **X-Particles Gaseous** — native fire/smoke shading (voxel size, smoke/fire gradients, Black Body).
- Render Settings effect (auto-added): blending, shadow thresholds, volume step (not bigger than smallest volume), Best AA, multipass normals/position. High Q Render ignores Physical DOF.
- Shaders: **xpSampleShader** (color surfaces by nearby particle data — speed/age/custom), **xpProximityShader** (grayscale by distance to particles — wet trails, glowing contact), xpDistanceShader, xpObjectShader (needed for some xpDisplayRender polygons), xpSoundShader, xpSpriteShader, **xpWetMapShader** (with xpWetMap tag), Noise/Particles/Shader Falloff.
- **Third-party renderers** (Redshift, Octane, Arnold, Cycles 4D/Cycles): the docs pages don't cover them. General practice (verify in your renderer's docs): render particles as geometry via xpGenerator (instances/render instances) or meshers (nxMesher / xpOpenVDBMesher); trails via xpSplineMesher or the renderer's hair/spline object; smoke/fire by caching xpExplosiaFX/nxExplosiaFX to **OpenVDB** in xpCache and loading the VDB in the renderer's volume object; particle data (color, velocity) via vertex color / UV tags exported by nxMesher or the renderer's particle-data nodes.
- X-Particles Render Info post effect = burn-in watermark (frame, particle count, time).
