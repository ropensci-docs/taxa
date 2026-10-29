# Get subtaxa

Get subtaxa indexes for each taxon or another per-taxon value. Subtaxa
are taxa contained within a taxon.

## Usage

``` r
subtaxa(x, subset = NULL, max_depth = NULL, include = FALSE, value = NULL, ...)
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
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md),
[`supertaxa()`](https://docs.ropensci.org/taxa/reference/supertaxa.md)

Other subtaxa functions:
[`n_subtaxa()`](https://docs.ropensci.org/taxa/reference/n_subtaxa.md)

## Examples

``` r
# Generate example data
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))

# The indexes of all subtaxa (with subtaxa of subtaxa, etc) for each taxon
subtaxa(x)
#> [[1]]
#> [1] 2 3 4 5 6 7 8
#> 
#> [[2]]
#> [1] 3 4 5
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
#> [1] 7 8
#> 
#> [[7]]
#> [1] 8
#> 
#> [[8]]
#> integer(0)
#> 

# The indexes of immediate subtaxa (without subtaxa of subtaxa, etc) for each taxon
subtaxa(x, max_depth = 1)
#> [[1]]
#> [1] 2 6
#> 
#> [[2]]
#> [1] 3
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
#> [1] 7
#> 
#> [[7]]
#> [1] 8
#> 
#> [[8]]
#> integer(0)
#> 

# Return something other than index
subtaxa(x, value = tax_name(x))
#> [[1]]
#> [1] "Felidae"         "Panthera"        "Panthera leo"    "Panthera tigris"
#> [5] "Ursidae"         "Ursus"           "Ursus arctos"   
#> 
#> [[2]]
#> [1] "Panthera"        "Panthera leo"    "Panthera tigris"
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
#> [1] "Ursus"        "Ursus arctos"
#> 
#> [[7]]
#> [1] "Ursus arctos"
#> 
#> [[8]]
#> character(0)
#> 

# Include each taxon with its subtaxa
subtaxa(x, value = tax_name(x), include = TRUE)
#> [[1]]
#> [1] "Carnivora"       "Felidae"         "Panthera"        "Panthera leo"   
#> [5] "Panthera tigris" "Ursidae"         "Ursus"           "Ursus arctos"   
#> 
#> [[2]]
#> [1] "Felidae"         "Panthera"        "Panthera leo"    "Panthera tigris"
#> 
#> [[3]]
#> [1] "Panthera"        "Panthera leo"    "Panthera tigris"
#> 
#> [[4]]
#> [1] "Panthera leo"
#> 
#> [[5]]
#> [1] "Panthera tigris"
#> 
#> [[6]]
#> [1] "Ursidae"      "Ursus"        "Ursus arctos"
#> 
#> [[7]]
#> [1] "Ursus"        "Ursus arctos"
#> 
#> [[8]]
#> [1] "Ursus arctos"
#> 

# Only return data for some taxa (faster than subsetting the whole result)
subtaxa(x, subset = 3)
#> [[1]]
#> [1] 4 5
#> 
```
