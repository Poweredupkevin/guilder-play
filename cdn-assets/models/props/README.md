# public/cdn-assets/models/props/

Decorations: banners, furniture, rugs, shelves, barrels, statues, guild crests (~1-3k tris each).

- Format: `.glb`, meters, Y-up, facing +Z.
- **The ~100 KB rule:** models are usually over ~100 KB, so they live here on the CDN. Only tiny files under ~100 KB would go in `public/`.
- Load with `RundotGameAPI.cdn.fetchAsset('models/props/<file>.glb')` + GLTFLoader.
