# public/cdn-assets/skybox/

Skybox art for the four skies: `sky_day.ktx2`, `sky_sunset.ktx2`, `sky_night.ktx2`, `sky_storm.ktx2` (equirect or cubemap, KTX2/Basis). The paths are already in `src/game/sky.ts` (`SKIES[id].file`); until the files arrive the skies are procedural (gradient dome, clouds, stars, rain and lightning).

- The KTX2 transcoder must be served locally from `public/` (external URLs are blocked on RUN).
- Keep each file ≤ ~2 MB for phones; 2048×1024 equirect is plenty.
