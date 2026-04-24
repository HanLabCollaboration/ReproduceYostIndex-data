# ReproduceYostIndex-data

Pre-computed Yost Index data files for the [ReproduceYostIndex](https://github.com/HanLabCollaboration/ReproduceYostIndex) R package.

## What's included

Data are distributed as GitHub Release assets — one gzip-compressed CSV and one GeoPackage per `(geo × year)` combination, covering all four Yost variants in a single wide file.

### CSV files (`yost_{geo}_{scope}_{year}.csv.gz`)

74 files total — one per `(geo × scope × year)`:

| geo | scope | years |
|---|---|---|
| county | national, state | 2011–2023 |
| tract | national, state | 2011–2023 |
| block group | national, state | 2013–2023 |

### GeoPackage files (`yost_{geo}_{year}.gpkg`)

37 files total — one per `(geo × year)`, scope-agnostic (geometry is identical for national and state scope):

| geo | years |
|---|---|
| county | 2011–2023 |
| tract | 2011–2023 |
| block group | 2013–2023 |

## Columns (CSV)

| Column | Description |
|---|---|
| `GEOID` | Census geographic identifier |
| `NAME` | Geographic name |
| `year` | ACS 5-year estimate end year |
| `geo` | Geography level (`county`, `tract`, `block group`) |
| `scope` | Quintile scope (`national` or `state`) |
| `Yost` | Yost Index |
| `YostQuintile` | Quintile (1 = least deprived, 5 = most deprived) |
| `YostStabilized` | Empirical Bayes–stabilized Yost Index |
| `YostStabilizedQuintile` | Quintile of stabilized index |
| `YostImputed` | Yost Index with missing values imputed |
| `YostImputedQuintile` | Quintile of imputed index |
| `YostStabilizedImputed` | Stabilized + imputed Yost Index |
| `YostStabilizedImputedQuintile` | Quintile of stabilized + imputed index |

## Usage

These files are consumed automatically by `getYostIndex()` in the ReproduceYostIndex package. You do not need to download them manually.

```r
# Install the package
remotes::install_github("HanLabCollaboration/ReproduceYostIndex")

# Retrieve pre-computed data — no Census API key required
library(ReproduceYostIndex)

# All US counties, 2022
county_yost <- getYostIndex(geo = "county", year = 2022)

# Tracts for California, state scope
ca_tracts <- getYostIndex(geo = "tract", year = 2022,
                          states = "CA", scope = "state")

# Block groups with geometry (sf object)
bg_sf <- getYostIndex(geo = "block group", year = 2021, geometry = TRUE)
```

Files are cached locally after the first download (`tools::R_user_dir("ReproduceYostIndex", "cache")`), so repeat calls are instantaneous.

## Release

Current release: **data-v2026.04**  
See [Releases](https://github.com/HanLabCollaboration/ReproduceYostIndex-data/releases) for all available versions.
