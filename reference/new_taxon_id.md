# Minimal taxon_id constructor

Minimal taxon_id constructor for internal use. Only use when the input
is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_id(.names = NULL, id = character(), db = taxon_db())
```

## Arguments

- .names:

  The names to apply to the vector

- id:

  Zero or more taxonomic ids. Inputs will be transformed to a
  `character` vector.

- db:

  The name(s) of the database(s) associated with the IDs. If not `NA`
  (the default), the input must consist of names of databases in
  [database_ref](https://docs.ropensci.org/taxa/reference/database_ref.md).
  The length must be 0, 1, or equal to the number of IDs.

## Value

An `S3` object of class `taxa_taxon_id`
