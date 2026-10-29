# Check if something is a [taxon_db](https://docs.ropensci.org/taxa/reference/taxon_db.md)

Check if an object is of the
[taxon_db](https://docs.ropensci.org/taxa/reference/taxon_db.md) class

## Usage

``` r
is_taxon_db(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxon_db(c('ncbi', 'ncbi', 'itis'))
is_taxon_db(x)
#> [1] TRUE
is_taxon_db(1:3)
#> [1] FALSE
```
