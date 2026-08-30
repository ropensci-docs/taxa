# Number of subtaxa per taxon

Get the number of subtaxa per taxon.

## Usage

``` r
n_subtaxa(x, subset = NULL, max_depth = NULL, include = FALSE)
```

## Arguments

- x:

  The object to get subtaxa for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object.

- subset:

  The subset of the tree to search. Can be indexes or names.

- max_depth:

  The number of ranks to traverse. For example, `max_depth = 1` returns
  only immediate subtaxa. By default (NULL) information for all subtaxa
  is returned (i.e. subtaxa of subtaxa, etc).

- include:

  If `TRUE`, include information for each taxon in the output.

## See also

Other subtaxa functions:
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md)

## Examples

``` r
# Generate example data
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))

# Find number of subtaxa (including subtaxa of subtaxa, etc)
n_subtaxa(x)
#> [1] 7 3 2 0 0 2 1 0

# Find the number of subtaxa one rank below each taxon
n_subtaxa(x, max_depth = 1)
#> [1] 2 1 2 0 0 1 1 0

# Only return data for some taxa (faster than subsetting the whole result)
n_subtaxa(x, subset = 1:3)
#> [1] 7 3 2
```
