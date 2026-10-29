# Minimal taxonomy constructor

Minimal taxonomy constructor for internal use. Only use when the input
is known to be valid since few validity checks are done.

## Usage

``` r
new_taxonomy(taxa = taxon(), supertaxa = integer())
```

## Arguments

- taxa:

  A [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vector.

- supertaxa:

  The indexes of `taxa` for each taxon's supertaxon.

## Value

An `S3` object of class `taxa_taxon`
