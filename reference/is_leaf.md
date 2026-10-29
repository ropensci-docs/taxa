# Check if taxa are leaves

Check if each taxon is a leaf. A leaf is a taxon with no subtaxa.
subtaxa.

## Usage

``` r
is_leaf(x)
```

## Arguments

- x:

  The object to get leaves for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object

## See also

Other leaf functions:
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md),
[`n_leaves()`](https://docs.ropensci.org/taxa/reference/n_leaves.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
is_leaf(x)
#> [1] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE  TRUE
```
