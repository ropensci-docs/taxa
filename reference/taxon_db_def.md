# Taxon database definition class

Used to store information on taxonomic databases that is used to
validate information in other classes.

## Usage

``` r
taxon_db_def(
  name = character(),
  url = NA_character_,
  desc = NA_character_,
  id_regex = NA_character_,
  rank_levels = rep(list(NULL), length(name))
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
