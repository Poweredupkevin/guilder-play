# public/cdn-assets/models/characters/

The walk-mode builders: `mira.glb` (registry key `avatar_mira`) and `bram.glb` (`avatar_bram`). Until they exist the game uses tinted capsules (`src/game/walk.ts`).

- About 1.75 m tall, origin at the feet (bottom-center), Y-up, **facing −Z** (the walker's forward; the capsule's tool pouch shows the front).
- One shared rig for both is ideal. Include `idle`, `walk` and `run` clips (the walker doesn't play them yet; see docs/replace-later.md).
- Budget: ≤ ~8k tris, one 1024² texture.
- Original characters only (Mira and Bram from `public/images/builder-*.webp`). Record them in `/LICENSES.md`.
