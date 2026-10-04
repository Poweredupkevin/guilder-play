# public/cdn-assets/images/: large images (over ~100 KB)

Examples: big textures and texture atlases for pieces, skyboxes/backgrounds, guild crests and commission artwork, collectible card art, full-screen title art.

- Load with `RundotGameAPI.cdn.fetchAsset('images/<file>')` → `URL.createObjectURL(blob)`.
- Prefer WebP or KTX2 (KTX2 needs its transcoder served locally from `public/`). Textures should be 1024² at most for pieces and 512² for small props, to stay within phone GPU memory.
- **The ~100 KB rule:** small UI images (under ~100 KB) go in `public/images/` instead.
