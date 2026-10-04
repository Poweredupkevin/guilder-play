# public/cdn-assets/models/floors/

Floor/ceiling tiles, stairs, ramps, basement/dungeon floors, trapdoors. Standard (confirmed by Kevin Sep 29, 2026): 4 m x 4 m tiles, top surface at y = 0; storey height 3 m (see ../README.md).

- Format: `.glb`, meters, Y-up, facing +Z.
- **The ~100 KB rule:** models are usually over ~100 KB, so they live here on the CDN. Only tiny files under ~100 KB would go in `public/`.
- Load with `RundotGameAPI.cdn.fetchAsset('models/floors/<file>.glb')` + GLTFLoader.
