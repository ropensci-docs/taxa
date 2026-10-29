# Get supertaxa

Get supertaxa indexes for each taxon or another per-taxon value.
Supertaxa are taxa a taxon is contained in.

## Usage

``` r
supertaxa(
  x,
  subset = NULL,
  max_depth = NULL,
  include = FALSE,
  value = NULL,
  use_na = FALSE,
  ...
)
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

- value:

  Something to return instead of indexes. Must be the same length as the
  number of taxa.

- use_na:

  Add a NA to represent the root of the taxonomy (i.e. no supertaxon)

- ...:

  Additional arguments.

## See also

Other taxonomy functions:
[`internodes()`](https://docs.ropensci.org/taxa/reference/internodes.md),
[`leaves()`](https://docs.ropensci.org/taxa/reference/leaves.md),
[`roots()`](https://docs.ropensci.org/taxa/reference/roots.md),
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md),
[`subtaxa()`](https://docs.ropensci.org/taxa/reference/subtaxa.md)

Other supertaxa functions:
[`n_supertaxa()`](https://docs.ropensci.org/taxa/reference/n_supertaxa.md)

## Examples

``` r
# Generate example data
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))

# The indexes of all supertaxa (with supertaxa of supertaxa, etc) for each taxon
supertaxa(x)
#> [[1]]
#> integer(0)
#> 
#> [[2]]
#> [1] 1
#> 
#> [[3]]
#> [1] 2 1
#> 
#> [[4]]
#> [1] 3 2 1
#> 
#> [[5]]
#> [1] 3 2 1
#> 
#> [[6]]
#> [1] 1
#> 
#> [[7]]
#> [1] 6 1
#> 
#> [[8]]
#> [1] 7 6 1
#> 

# Return something other than index
supertaxa(x, value = tax_name(x))
#> [[1]]
#> character(0)
#> 
#> [[2]]
#> [1] "Carnivora"
#> 
#> [[3]]
#> [1] "Felidae"   "Carnivora"
#> 
#> [[4]]
#> [1] "Panthera"  "Felidae"   "Carnivora"
#> 
#> [[5]]
#> [1] "Panthera"  "Felidae"   "Carnivora"
#> 
#> [[6]]
#> [1] "Carnivora"
#> 
#> [[7]]
#> [1] "Ursidae"   "Carnivora"
#> 
#> [[8]]
#> [1] "Ursus"     "Ursidae"   "Carnivora"
#> 

# Include each taxon with its supertaxa
supertaxa(x, value = tax_name(x), include = TRUE)
#> [[1]]
#> [1] "Carnivora"
#> 
#> [[2]]
#> [1] "Felidae"   "Carnivora"
#> 
#> [[3]]
#> [1] "Panthera"  "Felidae"   "Carnivora"
#> 
#> [[4]]
#> [1] "Panthera leo" "Panthera"     "Felidae"      "Carnivora"   
#> 
#> [[5]]
#> [1] "Panthera tigris" "Panthera"        "Felidae"         "Carnivora"      
#> 
#> [[6]]
#> [1] "Ursidae"   "Carnivora"
#> 
#> [[7]]
#> [1] "Ursus"     "Ursidae"   "Carnivora"
#> 
#> [[8]]
#> [1] "Ursus arctos" "Ursus"        "Ursidae"      "Carnivora"   
#> 

# Only return data for some taxa (faster than subsetting the whole result)
supertaxa(x, subset = 3)
#> [[1]]
#> [1] 2 1
#> 
```
