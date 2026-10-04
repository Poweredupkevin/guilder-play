# public/cdn-assets/models/walls/

Wall pieces (straight, corner, T, doorway, window, arch, half walls, battlements). Standard (confirmed by Kevin Sep 29, 2026): 4 m wide x 3 m tall, origin bottom-center, length along X (see ../README.md).

- Format: `.glb`, meters, Y-up, facing +Z.
- **The ~100 KB rule:** models are usually over ~100 KB, so they live here on the CDN. Only tiny files under ~100 KB would go in `public/`.
- Load with `RundotGameAPI.cdn.fetchAsset('models/walls/<file>.glb')` + GLTFLoader.
