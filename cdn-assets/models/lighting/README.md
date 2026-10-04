# public/cdn-assets/models/lighting/

Light-emitting decor: sconces, torches, candelabras, chandeliers, braziers, lanterns. Mark the flame/bulb with an empty named light_* so the game can add the light in code.

- Format: `.glb`, meters, Y-up, facing +Z.
- **The ~100 KB rule:** models are usually over ~100 KB, so they live here on the CDN. Only tiny files under ~100 KB would go in `public/`.
- Load with `RundotGameAPI.cdn.fetchAsset('models/lighting/<file>.glb')` + GLTFLoader.
