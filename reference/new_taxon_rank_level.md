# Minimal taxon_rank_level constructor

Minimal taxon_rank_level constructor for internal use. Only use when the
input is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_rank_level(level = character(), order = numeric())
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

## Value

An `S3` object of class `taxa_taxon_rank_level`
