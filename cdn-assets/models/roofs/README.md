# public/cdn-assets/models/roofs/

Roof tiles that sit on top of a storey (4 m × 4 m footprint like a floor tile, 2 m tall, origin at the tile's bottom center, which sits on the wall tops):

- `roof_clay_slope.glb`: a lean-to slope rising 2 m from +Z to −Z, with closed triangular gable ends.
- `roof_clay_peak.glb`: both slopes meeting in a ridge along X at 2 m, with gable ends.
- `roof_clay_cap.glb`: a four-sided pyramid cap (hip roof for a single tile or a tower), with a finial on top.

Same conventions as the rest (see ../README.md): meters, Y-up, facing +Z. Gable ends must be closed on both faces, because they're seen from outside and from the attic. The registry loads them for you (`models/roofs/<file>.glb`).
