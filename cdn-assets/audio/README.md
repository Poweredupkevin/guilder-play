# public/cdn-assets/audio/: music, ambience and SFX (over ~100 KB)

Examples: title/menu music, building ambience, "commission complete" stingers, placement/snap/rotate SFX packs (tiny one-shot SFX under ~100 KB may go in `public/` instead).

- Load with `RundotGameAPI.cdn.fetchAsset('audio/<file>')`. Prefer `.ogg`/`.m4a` (or `.mp3`) at a sensible bitrate.
- Every audio cue that carries information needs a visual/caption equivalent (accessibility).
- **The ~100 KB rule:** small files go in `public/`, large files go here.
