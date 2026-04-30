# ReproduceYost-data

Pre-computed Yost Index data files for the [ReproduceYost](https://github.com/HanLabCollaboration/ReproduceYost) R package.

## Structure

Data are distributed as GitHub Release assets in two formats per `(geo x year)` combination:

### CSV (gzip-compressed) — one file per `(geo x scope x year)`

| geo | scope | years |
|---|---|---|
| county | national, state | 2011–2024 |
| tract | national, state | 2011–2024 |
| block group | national, state | 2013–2024 |

**80 files.** File naming: `yost_{geo}_{scope}_{year}.csv.gz`

### GeoPackage — one file per `(geo x year)`

| geo | years |
|---|---|
| county | 2011–2024 |
| tract | 2011–2024 |
| block group | 2013–2024 |

**40 files.** File naming: `yost_{geo}_{year}.gpkg`

## Columns

`GEOID`, `year`, `geo`, `scope`, `Yost`, `YostQuintile`, `YostShrunk`, `YostShrunkQuintile`, `YostImputed`, `YostImputedQuintile`, `YostShrunkImputed`, `YostShrunkImputedQuintile`

## Usage

These files are consumed automatically by `getYost()` in the ReproduceYost package. You do not need to download them manually.
