# City dataset source & attribution

- Source: https://github.com/joelacus/world-cities (GeoNames-derived)
- License: Creative Commons Attribution 4.0 (https://creativecommons.org/licenses/by/4.0/)
- Underlying data: GeoNames (https://www.geonames.org/datasources/)
- Fetched: 2026-10-13

## Files
- `cities.csv` — merged/tiered dataset, columns: country (ISO2), name, lat, lng, tier
  - tier is a size proxy built from which population-threshold file (1000 / 5000 / 15000)
    each city appears in, NOT a real population number (the repo's ready-made files don't
    include one; fetching real populations needs a live GeoNames/geocode fetch, which this
    session's network policy blocks).
  - small  = appears only in the >=1000 pop list  (101,247 cities)
  - medium = also appears in the >=5000 pop list  (35,560 cities)
  - large  = also appears in the >=15000 pop list  (34,135 cities)

## Still open
- No "hex / megacity" tier yet for true 10M+ metros -- that needs either a short
  hand-curated list of ~40 known cities, or a later real-population fetch once
  network access allows it.
- Not yet joined to the country polygon data / WorldData.pointInCountry to stamp
  a BaseCountry per city -- that's a Studio-side step for when Studio's back up.
