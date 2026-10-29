# Get internodes

Get internodes indexes for each taxon or another per-taxon value. An
internode is a taxon with exactly one supertaxon and one subtaxon. These
taxa can be removed without losing information on the relationships of
the remaining taxa.

## Usage

``` r
internodes(x)
```

## Arguments

- x:

  The object to get internodes for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object.

## See also

Other taxonomy functions:
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md),
[`roots()`](https://docs.ropensci.org/taxa/reference/roots.md),
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md),
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md),
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

Other internode functions:
[`is_internode()`](https://docs.ropensci.org/taxa/reference/is_internode.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
internodes(x)
#> [1] 2 6 7
```
