# Number of supertaxa per taxon

Get the number of supertaxa each taxon is contained in.

## Usage

``` r
n_supertaxa(x, subset = NULL, max_depth = NULL, include = FALSE)
```

## Arguments

- x:

  The object to get supertaxa for, such as a
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object.

- subset:

  The subset of the tree to search for roots to that subset. Can be
  indexes or names.

- max_depth:

  The number of levels to traverse. For example, `max_depth = 1` returns
  only immediate supertaxa. By default (NULL) information for all
  supertaxa is returned.

- include:

  If `TRUE`, include information for each taxon in the output.

## See also

Other supertaxa functions:
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

## Examples

``` r
# Generate example data
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))

# Find number of supertaxa each taxon is contained in
n_supertaxa(x)
#> [1] 0 1 2 3 3 1 2 3

# Only return data for some taxa (faster than subsetting the whole result)
n_supertaxa(x, subset = 1:3)
#> [1] 0 1 2
```
