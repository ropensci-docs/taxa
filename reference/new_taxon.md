# Minimal taxon constructor

Minimal taxon constructor for internal use. Only use when the input is
known to be valid since few validity checks are done.

## Usage

``` r
new_taxon(
  .names = NULL,
  name = character(),
  rank = taxon_rank(),
  id = taxon_id(),
  auth = taxon_authority(),
  ...
)
```

## Arguments

- .names:

  The names of the vector.

- name:

  The names of taxa as a
  [character](https://rdrr.io/r/base/character.html) vector.

- rank:

  The ranks of taxa as a
  [taxon_rank](https://docs.ropensci.org/taxa/reference/taxon_rank.md)
  vector.

- id:

  The ids of taxa as a
  [taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md)
  vector.

- auth:

  The authority of the taxon as a
  [taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
  vector.

## Value

An `S3` object of class `taxa_taxon`
