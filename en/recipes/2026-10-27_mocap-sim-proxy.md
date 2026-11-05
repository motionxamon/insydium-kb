# Live low-poly sim proxy for a mocap character (fire / collisions)

- Source: Top Tip Tuesday — Mocap Sim Proxy — https://www.youtube.com/watch?v=C0P7UtWroDo (2026-10-27)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX, GPU) + C4D Character tools; xpOpenVDBMesher (CPU) for the proxy
- Goal: a character on fire whose smoke/fire source and collider is a light, skinned proxy that stays live when you swap the mocap clip.

## Scene tree
```
nxExplosiaFX domain
  Sources: Remesh (proxy)      Colliders: Remesh (proxy)   ← hierarchy options off
Walking/Stumbling Loop null (mocap asset, animated in Z)
  ├─ mocap joints (Character Definition tag)
  └─ Male Puppet (Maxon asset browser ▸ Motion Capture ▸ Model)
       ├─ Character Solver tag  (Source Character = mocap Character Definition)
       ├─ Mocap Rig Target null → joints
       ├─ high-poly mesh parts (render)
       └─ Remesh (low poly proxy) + Weight tag + Skin  (bound to the same joints)
```

## Steps
1. Bring in the Maxon Motion Capture puppet + a mocap clip. Drag the clip's **Character Definition** tag into the puppet's **Character Solver** tag → Source Character. Put the puppet under the clip's animated null so it also travels. [▶ 3:20](https://youtu.be/C0P7UtWroDo?t=200)
2. Problem: the detailed body as EFX source and collider is very slow. Rule: **sources and colliders should be low-poly proxies**; render the high-poly. [▶ 5:38](https://youtu.be/C0P7UtWroDo?t=338)
3. Build the proxy: set Character Solver to **Reference Pose** (T-pose) and detach the clip temporarily. Ctrl-drag a copy of the mesh parts. [▶ 6:33](https://youtu.be/C0P7UtWroDo?t=393)
4. **xpOpenVDBMesher** with the copy as child → voxel size ~3 for a watertight hull; raise **Iso value** so thin parts (hands) stay. Make editable (C). [▶ 8:24](https://youtu.be/C0P7UtWroDo?t=504)
5. Parent it under a Maxon **Remesh** object (Symmetry X, moderate polygon size) → make editable → clean low-poly hull in the same pose. [▶ 8:46](https://youtu.be/C0P7UtWroDo?t=526)
6. Bind: select the joint hierarchy (first joint → right-click **Select Children**), Ctrl-select the remeshed proxy → **Character ▸ Bind** → Weight tag + Skin deformer. [▶ 10:21](https://youtu.be/C0P7UtWroDo?t=621)
7. Put the proxy under the puppet null, re-link the clip in the Character Solver, re-parent under the clip's null. Proxy and high-poly now follow any clip (shown swapping to a zombie walk). [▶ 13:37](https://youtu.be/C0P7UtWroDo?t=817)
8. nxExplosiaFX: replace the high-poly in **Sources** and **Colliders** with the proxy; turn off hierarchy options → much faster sim and caching. [▶ 12:04](https://youtu.be/C0P7UtWroDo?t=724)

## Notes
- Same technique for particle and fluid collisions (static or animated).
- Newest alternative: nxMesher can also produce a hull from emitted particles, but for skinned characters the VDB-mesh → Remesh → Bind proxy stays the cleanest.
