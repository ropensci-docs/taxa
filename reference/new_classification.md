# Minimal classfication constructor

Minimal classfication constructor for internal use. Only use when the
input is known to be valid since few validity checks are done.

## Usage

``` r
new_classification(taxonomy = taxonomy(), instances = integer())
```

## Arguments

- taxonomy:

  A [`taxonomy()`](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object.

- instances:

  The indexes of each instance of a taxon in the taxonomy. Can be any
  length.

## Value

An `S3` object of class `taxa_classification`
