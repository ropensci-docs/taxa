# Minimal taxon_rank constructor

Minimal taxon_rank constructor for internal use. Only use when the input
is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_rank(rank = character(), levels = taxon_rank_level())
```

## Arguments

- rank:

  Zero or more taxonomic rank names. Inputs will be transformed to a
  `character` vector.

- levels:

  A named numeric vector indicating the names and orders of possible
  taxonomic ranks. Higher numbers indicate for fine-scale groupings.
  Ranks of unknown order can be indicated with `NA` instead of a number.

## Value

An `S3` object of class `taxa_taxon_rank`
