# Number of leaves per taxon

Get the number of leaves per taxon. A leaf is a taxon with no subtaxa.

## Usage

``` r
n_leaves(x)
```

## Arguments

- x:

  The object to get leaves for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object

## See also

Other leaf functions:
[`is_leaf()`](https://docs.ropensci.org/taxa/reference/is_leaf.md),
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
n_leaves(x)
#> [1] 3 2 2 0 0 1 1 0
```
