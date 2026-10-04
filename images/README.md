# public/images/: small, bundled images (under ~100 KB each)

What goes here: small UI art that must be there on the first frame. Examples: button icons, the PoweredUp! Games studio-splash logo, the title logo, cursor/tool icons (rotate, grid, undo, delete), and tiny piece-picker thumbnails.

- Prefer **WebP** (or PNG for crisp UI), sized for the largest display at 2× at most.
- Reference them with relative paths: `./images/icon-rotate.webp`.
- **The ~100 KB rule:** anything bigger than ~100 KB (full-screen art, big textures, models, audio) goes in `public/cdn-assets/` instead.
- Record the source and license of every asset in `/LICENSES.md`.
