# Get leaves

Get leaves indexes for each taxon or another per-taxon value. Leaves are
taxa with no subtaxa.

## Usage

``` r
leaves(x, value = NULL, ...)
```

## Arguments

- x:

  The object to get leaves for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object

- value:

  Something to return instead of indexes. Must be the same length as the
  number of taxa.

- ...:

  Additional arguments.

## See also

Other taxonomy functions:
[`internodes()`](https://docs.ropensci.org/taxa/reference/internodes.md),
[`roots()`](https://docs.ropensci.org/taxa/reference/roots.md),
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md),
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md),
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

Other leaf functions:
[`is_leaf()`](https://docs.ropensci.org/taxa/reference/is_leaf.md),
[`n_leaves()`](https://docs.ropensci.org/taxa/reference/n_leaves.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
leaves(x)
#> [[1]]
#> [1] 4 5 8
#> 
#> [[2]]
#> [1] 4 5
#> 
#> [[3]]
#> [1] 4 5
#> 
#> [[4]]
#> integer(0)
#> 
#> [[5]]
#> integer(0)
#> 
#> [[6]]
#> [1] 8
#> 
#> [[7]]
#> [1] 8
#> 
#> [[8]]
#> integer(0)
#> 
leaves(x, value = tax_name(x))
#> [[1]]
#> [1] "Panthera leo"    "Panthera tigris" "Ursus arctos"   
#> 
#> [[2]]
#> [1] "Panthera leo"    "Panthera tigris"
#> 
#> [[3]]
#> [1] "Panthera leo"    "Panthera tigris"
#> 
#> [[4]]
#> character(0)
#> 
#> [[5]]
#> character(0)
#> 
#> [[6]]
#> [1] "Ursus arctos"
#> 
#> [[7]]
#> [1] "Ursus arctos"
#> 
#> [[8]]
#> character(0)
#> 
```
