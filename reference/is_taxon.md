# Check if something is a [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) object

Check if an object is of the
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) class

## Usage

``` r
is_taxon(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxon(c('A', 'B', 'C'))
is_taxon(x)
#> [1] TRUE
is_taxon(1:2)
#> [1] FALSE
```
