# Taxon rank class

**maturing lifecycle** Used to store taxon ranks, possibly associated
with a taxonomy database. This is typically used to store taxon ranks in
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects.

## Usage

``` r
taxon_rank(
  rank = character(),
  .names = NULL,
  levels = NULL,
  guess_order = TRUE
)
```

## Arguments

- rank:

  Zero or more taxonomic rank names. Inputs will be transformed to a
  [character](https://rdrr.io/r/base/character.html) vector.

- .names:

  The names of the vector

- levels:

  A named numeric vector indicating the names and orders of possible
  taxonomic ranks. Higher numbers indicate for fine-scale groupings.
  Ranks of unknown order can be indicated with `NA` instead of a number.

- guess_order:

  If `TRUE` and no rank order is given using numbers, try to guess order
  based on rank names.

## Value

An `S3` object of class `taxa_taxon_rank`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md)

## Examples

``` r

# Making new objects
x <- taxon_rank(c('species', 'species', 'phylum', 'family'))

# Specifiying level order
taxon_rank(c('A', 'B', 'C', 'D', 'A', 'D', 'D'),
           levels = c('D', 'C', 'B', 'A'))
#> <taxon_rank[7]>
#> [1] A B C D A D D
#> Rank levels: D < C < B < A
taxon_rank(c('A', 'B', 'C', 'D', 'A', 'D', 'D'),
           levels = c(D = NA, A = 10, B = 20, C = 30))
#> <taxon_rank[7]>
#> [1] A B C D A D D
#> Rank levels: A < B < C ? D
names(x) <- c('a', 'b', 'c', 'd')

# Manipulating objects
as.character(x)
#>         a         b         c         d 
#> "species" "species"  "phylum"  "family" 
as.factor(x)
#>       a       b       c       d 
#> species species  phylum  family 
#> Levels: phylum family species
as.ordered(x)
#>       a       b       c       d 
#> species species  phylum  family 
#> Levels: phylum < family < species
x[2:3]
#> <taxon_rank[2]>
#>       b       c 
#> species  phylum 
#> Rank levels: phylum < family < species
x[x > 'family'] <- taxon_rank('unknown')
x[1] <- taxon_rank('order')
x['b']
#> <taxon_rank[1]>
#>       b 
#> unknown 
#> Rank levels: phylum < order < family < species ? unknown
x['b'] <- 'order'

# Using as columns in tables
tibble::tibble(x = x, y = 1:4)
#> # A tibble: 4 × 2
#>   x              y
#>   <tax_rank> <int>
#> 1 order          1
#> 2 order          2
#> 3 phylum         3
#> 4 family         4
data.frame(x = x, y = 1:4)
#>        x y
#> 1  order 1
#> 2  order 2
#> 3 phylum 3
#> 4 family 4

# Converting to tables
tibble::as_tibble(x)
#> # A tibble: 4 × 1
#>   tax_rank
#>   <chr>   
#> 1 order   
#> 2 order   
#> 3 phylum  
#> 4 family  
as_data_frame(x)
#>   tax_rank
#> 1    order
#> 2    order
#> 3   phylum
#> 4   family

# Trying to add an unknown level as a character causes an error
#x[2] <- 'superkingdom'

# But you can add a new level using taxon_rank objects
x[2] <- taxon_rank('superkingdom')
```
