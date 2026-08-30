# Check if something is a [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)

Check if an object is of the
[taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md) class

## Usage

``` r
is_taxonomy(x)
```

## Arguments

- x:

  An object to test

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
is_taxonomy(x)
#> [1] TRUE
is_taxonomy(1:2)
#> [1] FALSE
```
