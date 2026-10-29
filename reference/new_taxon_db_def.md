# Minimal taxon_db_def constructor

Minimal taxon_db_def constructor for internal use. Only use when the
input is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_db_def(
  name = character(),
  url = character(),
  desc = character(),
  id_regex = character(),
  rank_levels = list()
)
```

## Arguments

- name:

  Name of the database in lower case. Inputs will be transformed to a
  `character` vector.

- url:

  URL of the database website. Inputs will be transformed to a
  `character` vector.

- desc:

  Description of the database. Inputs will be transformed to a
  `character` vector.

- id_regex:

  A regular expression for taxon IDs of the database. Inputs will be
  transformed to a `character` vector.

- rank_levels:

  Valid taxonomic ranks for the database. Should be a list of `numeric`
  vectors named by taxonomic ranks.

## Value

An `S3` object of class `taxa_taxon_db_def`
