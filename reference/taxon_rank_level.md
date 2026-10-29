# Taxon rank level

Used to store taxon rank level information. This is used in
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)
objects.

## Usage

``` r
taxon_rank_level(
  level = character(),
  order = NULL,
  guess_order = TRUE,
  impute_na = FALSE
)
```

## Arguments

- level:

  Zero or more taxonomic rank names. If a named numeric is applied, the
  names are used for levels and the numeric values are used for the
  order. Inputs will be transformed to a `character` vector.

- order:

  Integers that determine the relative order of taxonomic levels. Inputs
  will be transformed to a `integer` vector. `NA`s can be used to
  indicate that the order is not known.

- guess_order:

  If `TRUE` and no order is given, try to guess order based on rank
  names.

- impute_na:

  If `TRUE`, fill in NAs based on nearby values (assumed in ascending
  order).

## Value

An `S3` object of class `taxa_taxon_rank_level`
