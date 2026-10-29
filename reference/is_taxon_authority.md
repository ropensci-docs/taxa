# Check if is a [taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)

Check if an object is of the
[taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
class

## Usage

``` r
is_taxon_authority(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxon_authority(c('Cham. & Schldl.', 'L.'),
                     date = c('1827', '1753'))
is_taxon_authority(x)
#> [1] TRUE
is_taxon_authority(1:3)
#> [1] FALSE
```
