# public/cdn-assets/models/: Kevin's 3D building pieces (.glb)

| Folder | What goes here |
|---|---|
| `walls/` | Wall pieces: straight, corner, T, end cap, doorway, window, arch, half-height, battlement/crenellation |
| `floors/` | Floor/ceiling tiles, stairs, ramps, basement/dungeon floor, trapdoors |
| `props/` | Decorations: banners, tables, benches, shelves, barrels, rugs, statues, guild crests |
| `lighting/` | Light-emitting decor: sconces, torches, candelabras, chandeliers, braziers, lanterns |
| `roofs/` | Roof slopes, peaks and caps (v7) |
| `characters/` | The walk-mode builders `mira.glb` and `bram.glb` (v7) |

Models are large, so they belong on the CDN (**the ~100 KB rule:** over ~100 KB goes in `cdn-assets/`; tiny files under ~100 KB may go in `public/`). Load them with `RundotGameAPI.cdn.fetchAsset('models/walls/<file>.glb')` + `GLTFLoader` (see `../README.md`).

## Piece standard (confirmed by Kevin, Sep 29, 2026)
_Confirmed. Every piece follows this so pieces snap cleanly._

- **Format:** `.glb` (glTF binary), **1 unit = 1 meter**, **Y-up**, facing **+Z** (the template convention). Apply transforms before export.
- **Walls:** **4 m wide × 3 m tall**, ~0.3 m thick. The origin is at the **bottom-center** of the wall, and the length runs along **X** (from −2 m to +2 m).
- **Half pieces:** 2 m wide (and 1.5 m tall for half-height walls), so everything lines up on the 1 m hidden grid.
- **Floor tiles:** 4 m × 4 m, with the origin at the tile center and the top surface at y = 0.
- **Storey height:** 3 m (wall height). Floor 1 is at y = 0, floor 2 at y = 3, and the basement at y = −3.
- **Snap sockets:** optional empty nodes named `socket_*` (e.g. `socket_left`, `socket_right`, `socket_top`). The game reads them as connection points. If there are none, it uses the defaults (wall ends at x = ±2, y = 0).
- **Lighting props:** an empty named `light_*` marks where the game adds a point light/glow (lights are added in code, not exported from Blender).
- **Budgets (phones):** walls/floors ≤ ~2–5k tris, props ≤ ~1–3k, textures ≤ 1024² (512² for small props), shared atlases/materials so there are fewer draw calls.
- **Naming:** `category_material_variant.glb`, e.g. `wall_stone_straight.glb`, `wall_stone_door.glb`, `floor_wood_4x4.glb`, `light_iron_sconce.glb`.
- **Compression:** Draco/Meshopt is fine, but the decoder must be served locally from `public/` (external URLs are blocked).
- Record each model in `/LICENSES.md`, even when it's Kevin's own work (source file, date).

## Registry keys (v7)
Every piece, decoration and avatar has a **registry key** and a target file (`src/game/models.ts`). A Vite plugin lists the `.glb` files in this folder; **drop a file in with the exact name below and restart `npm run dev` (or rebuild) and it replaces the placeholder everywhere**. If it fails to load, the placeholder stays. The full table with status is in `docs/replace-later.md` §1.

- **walls/**: `wall_stone_straight`, `wall_stone_door`, `wall_stone_window`, `wall_dungeon_straight`, `pillar_stone_round`; v13: `gate_iron_double` (4 m), `wall_estate_stone` / `wall_estate_spiked` (4 × 3.72 × 0.6 m, sockets at the ends), `pier_estate_lantern` (1.2 m, socket at the centre), `gate_grand_iron` (12 m: 8 m opening + two 2 m piers, sockets at ±6 m)
- **floors/**: `floor_wood_4x4`, `floor_dungeon_4x4`, `stairs_wood_straight`
- **roofs/**: `roof_clay_slope`, `roof_clay_peak`, `roof_clay_cap`
- **props/**: `decor_forge`, `decor_fireplace`, `decor_potted_plant`, `decor_table`, `decor_chair`, `decor_barrel`, `decor_crate`, `decor_rug`, `decor_bookshelf`, `decor_banner_guild`, `decor_banner_blue`, `decor_banner_gilded`, `decor_tree_oak`, `decor_tree_pine`, `decor_tree_blossom`, `decor_bush`, `decor_flower_bed`, `decor_fence`, `decor_bed` (v13); v15 (Meshy): `decor_crest` (1 m guild crest, back-centre origin; also mounted on the Grand Gate), `decor_tree_oak_grand`, `decor_tree_dead`, `decor_tree_blossom_grand`, `decor_tree_cypress`
- **lighting/**: `light_wall_sconce`, `light_chandelier`, `light_lantern`, `light_lamp_post` (add `light_*` empties where the flame/light goes)
- **characters/**: `mira` (key `avatar_mira`), `bram` (key `avatar_bram`)

**Alternate models (v14):** `walls/gate_grand_iron_meshy.glb` is an opt-in Meshy-generated Grand Gate, listed in `ALT_MODELS` (`src/game/models.ts`). It's used only with `?alt=gate_grand_iron` or when the key is in `USE_ALT_MODELS`; `?procedural=<key>|all` forces the procedural model.

**Meshy decor (v15):** `props/decor_crest.glb` and the four `props/decor_tree_*` above are the default models for their keys (regular registry files); `?procedural=decor_crest` (or `FORCE_PROCEDURAL`) switches any of them back to the procedural stand-in. See `docs/replace-later.md` §2c.

The file name is `<key>.glb` except for characters. Wall finishes (Workshop) tint placeholder walls only; see `docs/replace-later.md` for how real walls should expose a `finish` material.
