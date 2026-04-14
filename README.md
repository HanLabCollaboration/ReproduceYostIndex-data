# ReproduceYost-data

Pre-computed Yost Index data files for the [ReproduceYost](https://github.com/HanLabCollaboration/ReproduceYost) R package.

## Structure

Data are distributed as GitHub Release assets — one gzip-compressed CSV per `(geo × scope × year)` combination:

| geo | scope | years |
|---|---|---|
| county | national, state | 2011–2023 |
| tract | national, state | 2011–2023 |
| block group | national, state | 2013–2023 |

**74 files total.** File naming: `yost_{geo}_{scope}_{year}.csv.gz`

## Columns

`GEOID`, `year`, `geo`, `scope`, `Yost`, `YostQuintile`, `YostShrunk`, `YostShrunkQuintile`, `YostImputed`, `YostImputedQuintile`, `YostShrunkImputed`, `YostShrunkImputedQuintile`

## Usage

These files are consumed automatically by `getYost()` in the ReproduceYost package. You do not need to download them manually.
