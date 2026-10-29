# Check if something is a [taxon_rank](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

Check if an object is of the
[taxon_rank](https://docs.ropensci.org/taxa/reference/taxon_rank.md)
class

## Usage

``` r
is_taxon_rank(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxon_rank(c('species', 'species', 'phylum', 'family'))
is_taxon_rank(x)
#> [1] TRUE
is_taxon_rank(1:3)
#> [1] FALSE
```
