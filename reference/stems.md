# Get stems

Get stem indexes for each taxon or another per-taxon value.

## Usage

``` r
stems(x, value = NULL, ...)
```

## Arguments

- x:

  An object with taxonomic relationships, like
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  objects.

- value:

  Something to return instead of indexes. Must be the same length as the
  number of taxa.

- ...:

  Additional arguments.

## See also

Other taxonomy functions:
[`internodes()`](https://docs.ropensci.org/taxa/reference/internodes.md),
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md),
[`roots()`](https://docs.ropensci.org/taxa/reference/roots.md),
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md),
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

Other stem functions:
[`is_stem()`](https://docs.ropensci.org/taxa/reference/is_stem.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris'),
              supertaxa = c(NA, 1, 2, 3, 3))
x <- c(x, x)
stems(x)
#> [[1]]
#> [1] 1 2
#> 
#> [[2]]
#> [1] 6 7
#> 
stems(x, value = tax_name(x))
#> [[1]]
#> [1] "Carnivora" "Felidae"  
#> 
#> [[2]]
#> [1] "Carnivora" "Felidae"  
#> 
```
