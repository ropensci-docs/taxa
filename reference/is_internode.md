# Check if taxa are internodes

Check if each taxon is an internode. An internode is a taxon with
exactly one supertaxon and one subtaxon. These taxa can be removed
without losing information on the relationships of the remaining taxa.

## Usage

``` r
is_internode(x)
```

## Arguments

- x:

  The object to get internodes for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object.

## See also

Other internode functions:
[`internodes()`](https://docs.ropensci.org/taxa/reference/internodes.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
is_internode(x)
#> [1] FALSE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE
```
