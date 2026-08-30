# Check if something is a [taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md) object

Check if an object is of the
[taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md) class

## Usage

``` r
is_taxon_id(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi')
is_taxon_id(x)
#> [1] TRUE
is_taxon_id(1:3)
#> [1] FALSE
```
