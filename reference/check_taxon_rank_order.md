# Check that order is ascending

Check that order is ascending and reorder the orders and their levels if
needed.

## Usage

``` r
check_taxon_rank_order(level, order, warn = FALSE)
```

## Arguments

- level:

  Zero or more taxonomic rank names.

- order:

  Integers that determine the relative order of taxonomic levels.

- warn:

  If `TRUE`, issue a warning when not in ascending order.
