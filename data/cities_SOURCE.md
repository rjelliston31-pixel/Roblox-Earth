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

## Trimming history (2026-10-13)
`cities.csv` went through a few sizes before landing at 10,000:
50,000 -> 25,000 -> **10,000** (current), each time compared against the
original game's city count (started ~10,000, pruned down to 6,698 final).

Current `cities.csv`: the first 10,000 of the 34,135 "large" (>=15000 pop)
cities, in file order. This is large-tier only -- no medium/small cities --
which fits the original's stated focus on urban population and significance
rather than small towns.

Caveat (applies to every trim above): there are no real population numbers
within a tier to rank by, so "first 10,000 in file order" is *a* set of
significant cities, not provably the *biggest* 10,000. If that precision
matters later, either hand-curate or revisit once a real population source
is reachable.

Because the set is now large-tier only, there's currently no data to drive a
small/medium size-variation in markers (e.g. circle vs square) -- every city
in the current set is the same tier. Worth keeping in mind when the marker
rendering gets built: either accept uniform markers for now, or pull in some
medium-tier cities later for visual variety.

The untrimmed 170,942-city set (all three tiers in full) is kept at
`cities_full.csv` in case the full set or a different trim is wanted later.
