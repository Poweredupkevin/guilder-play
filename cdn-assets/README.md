# public/cdn-assets/: large assets served from the RUN CDN (over ~100 KB)

`rundot deploy` uploads this folder to the RUN.world CDN, with versioning and cache-busting handled for you. In `npm run dev`, the files are served locally. The deployed game is limited to **32 MB**; the CDN is how you go past that.

| Folder | What goes here |
|---|---|
| `models/walls/`, `models/floors/`, `models/roofs/`, `models/props/`, `models/lighting/` | Kevin's `.glb` building pieces and decor (see `models/README.md` for the size standard and registry keys) |
| `models/characters/` | Walk-mode builders `mira.glb` / `bram.glb` |
| `skybox/` | Sky art (`sky_day/sunset/night/storm.ktx2`) |
| `images/` | Large textures, backgrounds, commission/guild art, collection-card art |
| `audio/` | Music, ambience and long SFX |
| `videos/` | The house promo video `house-promo.mp4` (~30 s, H.264 + AAC; path set in `src/promo/housePromo.config.ts`) |

**Loading in code** (always wrapped, because an unhandled rejection crashes the game):
```ts
import RundotGameAPI from '@series-inc/rundot-game-sdk/api'
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js'

const blob = await RundotGameAPI.cdn.fetchAsset('models/walls/wall_stone_straight.glb') // path under cdn-assets/
const url = URL.createObjectURL(blob)
const gltf = await new GLTFLoader().loadAsync(url)
URL.revokeObjectURL(url)
```

**Rules:**
- **The ~100 KB rule:** small files (under ~100 KB) go in `public/images/`, large files go here.
- **No external URLs.** The game can only load from its own origin (this folder included), Google Fonts, and URLs returned by SDK calls. Don't hot-link models, textures or decoders.
- If a `.glb` uses **Draco/KTX2/Meshopt** compression, ship the decoder files in `public/` and point the loader at the local path (for example `dracoLoader.setDecoderPath('./draco/')`). The default gstatic decoder URL is blocked.
- Record every asset in `/LICENSES.md`.
