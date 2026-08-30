# Test if taxa are roots

Check if each taxon is a root. A root is a taxon with no supertaxon.

## Usage

``` r
is_root(x, subset = NULL)
```

## Arguments

- x:

  An object containing taxonomic relationships, such as
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  objects.

- subset:

  The subset of the tree to search for roots to that subset. Can be
  indexes or names.

## See also

Other root functions:
[`roots()`](https://docs.ropensci.org/taxa/reference/roots.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
is_root(x)
#> [1]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
is_root(x, subset = 2:8)
#> [1] FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
```
