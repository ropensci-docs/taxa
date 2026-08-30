# Minimal taxon_authority constructor

Minimal taxon_authority constructor for internal use. Only use when the
input is known to be valid since few validity checks are done.

## Usage

``` r
new_taxon_authority(
  .names = NULL,
  author = character(),
  date = character(),
  citation = character()
)
```

## Arguments

- .names:

  The names of the vector.

- author:

  Zero or more author names.

- date:

  Zero or more dates.

- citation:

  Zero or more literature citations.

## Value

An `S3` object of class `taxa_taxon_authority`
