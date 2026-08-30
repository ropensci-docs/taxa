# Taxon class

**experimental lifecycle** Used to store classifications in reference to
a taxonomic tree.

## Usage

``` r
classification(x = NULL, taxonomy = NULL, .names = NULL)
```

## Arguments

- x:

  One of:

  - A list where each item represents a series of nested taxa. The
    contents of the list can be in any form that can be converted to a
    [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vector.

  - The indexes/names of each instance of a taxon in a
    [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
    object specified by the `taxonomy` option. Can be any length, but
    must consist of valid indexes for taxa in the `taxonomy` object.

- taxonomy:

  A [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  object. Only needed if taxon indexes are supplied as the first
  argument.

- .names:

  The names of the vector.

## Value

An `S3` object of class `taxa_classification`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

# Create classification vector with a list
x <- classification(list(
  c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo'),
  c('Carnivora', 'Felidae', 'Panthera', 'Panthera tigris'),
  c('Carnivora', 'Ursidae', 'Ursus', 'Ursus arctos'),
  c('Carnivora', 'Ursidae', 'Ursus', 'Ursus arctos'),
  c('Carnivora', 'Felidae', 'Panthera', 'Panthera tigris')
))


# Create classification vector with indexes and a taxonomy
x <- classification(c(3, 4, 4, 5, 5, 6, 8, 8, 2, 5, 6, 2),
                    taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                               'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
                             supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7)))

x <- classification(c(3, 4, 4, 5, 5, 6, 8, 8, 2, 5, 6, 2),
                    taxonomy(taxon(name = c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                                            'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
                                   rank = c('order', 'family', 'genus', 'species',
                                            'species', 'family', 'genus', 'species'),
                                   id = taxon_id(c('33554', '9681', '9688', '9689',
                                                   '9694', '9632', '9639', '9644'),
                                                 db = 'ncbi'),
                                   auth = c('Bowdich, 1821', 'Fischer, 1817',
                                            'Oken, 1816', 'L., 1758',
                                            'L., 1758', 'Fischer, 1817',
                                            'L., 1758', 'L., 1758')),
                             supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7)))
names(x) <- letters[1:12]


# Get parts of the classification vector
tax_name(x)
#>                 a                 b                 c                 d 
#>        "Panthera"    "Panthera leo"    "Panthera leo" "Panthera tigris" 
#>                 e                 f                 g                 h 
#> "Panthera tigris"         "Ursidae"    "Ursus arctos"    "Ursus arctos" 
#>                 i                 j                 k                 l 
#>         "Felidae" "Panthera tigris"         "Ursidae"         "Felidae" 
tax_rank(x)
#> <taxon_rank[12]>
#>       a       b       c       d       e       f       g       h       i       j 
#>   genus species species species species  family species species  family species 
#>       k       l 
#>  family  family 
#> Rank levels: order < family < genus < species
tax_id(x)
#> <taxon_id[12]>
#>           a           b           c           d           e           f 
#> 9688 (ncbi) 9689 (ncbi) 9689 (ncbi) 9694 (ncbi) 9694 (ncbi) 9632 (ncbi) 
#>           g           h           i           j           k           l 
#> 9644 (ncbi) 9644 (ncbi) 9681 (ncbi) 9694 (ncbi) 9632 (ncbi) 9681 (ncbi) 
tax_db(x)
#> <taxon_db[12]>
#>    a    b    c    d    e    f    g    h    i    j    k    l 
#> ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi 
tax_auth(x)
#> <taxon_authority[12]>
#>            a            b            c            d            e            f 
#>    Oken 1816      L. 1758      L. 1758      L. 1758      L. 1758 Fischer 1817 
#>            g            h            i            j            k            l 
#>      L. 1758      L. 1758 Fischer 1817      L. 1758 Fischer 1817 Fischer 1817 
tax_author(x)
#>         a         b         c         d         e         f         g         h 
#>    "Oken"      "L."      "L."      "L."      "L." "Fischer"      "L."      "L." 
#>         i         j         k         l 
#> "Fischer"      "L." "Fischer" "Fischer" 
tax_date(x)
#>      a      b      c      d      e      f      g      h      i      j      k 
#> "1816" "1758" "1758" "1758" "1758" "1817" "1758" "1758" "1817" "1758" "1817" 
#>      l 
#> "1817" 
tax_cite(x)
#>  a  b  c  d  e  f  g  h  i  j  k  l 
#> "" "" "" "" "" "" "" "" "" "" "" "" 

# Manipulate classification vectors
x[1:3]
#> <classification[3]>
#>                                       a                                       b 
#>              Carnivora|Felidae|Panthera Carnivora|Felidae|Panthera|Panthera leo 
#>                                       c 
#> Carnivora|Felidae|Panthera|Panthera leo 
#> Rank levels: order < family < genus < species
x[tax_rank(x) > 'family']
#> <classification[8]>
#>                                          a 
#>                 Carnivora|Felidae|Panthera 
#>                                          b 
#>    Carnivora|Felidae|Panthera|Panthera leo 
#>                                          c 
#>    Carnivora|Felidae|Panthera|Panthera leo 
#>                                          d 
#> Carnivora|Felidae|Panthera|Panthera tigris 
#>                                          e 
#> Carnivora|Felidae|Panthera|Panthera tigris 
#>                                          g 
#>       Carnivora|Ursidae|Ursus|Ursus arctos 
#>                                          h 
#>       Carnivora|Ursidae|Ursus|Ursus arctos 
#>                                          j 
#> Carnivora|Felidae|Panthera|Panthera tigris 
#> Rank levels: order < family < genus < species
# c(x, x)
# x['b'] <- NA
is.na(x)
#>  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
# as.data.frame(x)
# tibble::as_tibble(x)

# Use as columns in tables
tibble::tibble(x = x, y = 1:12)
#> # A tibble: 12 × 2
#>    x                                              y
#>    <classif>                                  <int>
#>  1 Carnivora|Felidae|Panthera                     1
#>  2 Carnivora|Felidae|Panthera|Panthera leo        2
#>  3 Carnivora|Felidae|Panthera|Panthera leo        3
#>  4 Carnivora|Felidae|Panthera|Panthera tigris     4
#>  5 Carnivora|Felidae|Panthera|Panthera tigris     5
#>  6 Carnivora|Ursidae                              6
#>  7 Carnivora|Ursidae|Ursus|Ursus arctos           7
#>  8 Carnivora|Ursidae|Ursus|Ursus arctos           8
#>  9 Carnivora|Felidae                              9
#> 10 Carnivora|Felidae|Panthera|Panthera tigris    10
#> 11 Carnivora|Ursidae                             11
#> 12 Carnivora|Felidae                             12
data.frame(x = x, y = 1:12)
#>                                             x  y
#> 1                  Carnivora|Felidae|Panthera  1
#> 2     Carnivora|Felidae|Panthera|Panthera leo  2
#> 3     Carnivora|Felidae|Panthera|Panthera leo  3
#> 4  Carnivora|Felidae|Panthera|Panthera tigris  4
#> 5  Carnivora|Felidae|Panthera|Panthera tigris  5
#> 6                           Carnivora|Ursidae  6
#> 7        Carnivora|Ursidae|Ursus|Ursus arctos  7
#> 8        Carnivora|Ursidae|Ursus|Ursus arctos  8
#> 9                           Carnivora|Felidae  9
#> 10 Carnivora|Felidae|Panthera|Panthera tigris 10
#> 11                          Carnivora|Ursidae 11
#> 12                          Carnivora|Felidae 12
```
