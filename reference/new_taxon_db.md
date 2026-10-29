# Minimal taxon_db constructor

Minimal taxon_db constructor for internal use. Only use when the input
is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_db(db = character(), ...)
```

## Arguments

- db:

  Zero or more taxonomic database names. Should be a name contained in
  `names(db_ref)`. Inputs will be transformed to a `character` vector.

- ...:

  Additional arguments.

## Value

An `S3` object of class `taxa_taxon_db`
