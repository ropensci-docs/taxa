# Get root taxa

Get the indexes of root taxa in a taxonomy.

## Usage

``` r
roots(x, subset = NULL)
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

Other taxonomy functions:
[`internodes()`](https://docs.ropensci.org/taxa/reference/internodes.md),
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md),
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md),
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md),
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

Other root functions:
[`is_root()`](https://docs.ropensci.org/taxa/reference/is_root.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
roots(x)
#> [1] 1
roots(x, subset = 2:8)
#> [1] 2 6
```
