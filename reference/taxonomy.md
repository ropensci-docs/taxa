# Taxonomy class

**experimental lifecycle** Used to store information about a set of taxa
forming a taxonomic tree.

## Usage

``` r
# S3 method for class 'taxa_classification'
x[...]

# S3 method for class 'taxa_classification'
x[[i]]

taxonomy(taxa = taxon(), supertaxa = NA, .names = NULL)

# S3 method for class 'taxa_taxonomy'
names(x)

# S3 method for class 'taxa_taxonomy'
names(x) <- value

# S3 method for class 'taxa_taxonomy'
x[..., subtaxa = TRUE, supertaxa = FALSE, invert = FALSE]

# S3 method for class 'taxa_taxonomy'
x[[i, ..., subtaxa = TRUE, supertaxa = FALSE, invert = FALSE]]
```

## Arguments

- taxa:

  A [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vector or
  something that can be converted to a
  [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vector.

- supertaxa:

  The indexes of `taxa` for each taxon's supertaxon.

- .names:

  The names of the vector (not the names of taxa).

## Value

An `S3` object of class `taxa_taxon`

## See also

Other classes:
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))

x <- taxonomy(taxon(name = c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                             'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
                    rank = c('order', 'family', 'genus', 'species',
                             'species', 'family', 'genus', 'species'),
                    id = taxon_id(c('33554', '9681', '9688', '9689',
                                    '9694', '9632', '9639', '9644'),
                                  db = 'ncbi'),
                    auth = c('Bowdich, 1821', 'Fischer de Waldheim, 1817', 'Oken, 1816', 'L., 1758',
                             'L., 1758', 'Fischer de Waldheim, 1817', 'L., 1758', 'L., 1758')),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
names(x) <- letters[1:8]

# Subset taxonomy vector
x[2] # By default, all subtaxa are included
#> <taxonomy[4]>
#> 1[b]: 9681|Felidae Fischer de Waldheim 1817|family
#> └─2[c]: 9688|Panthera Oken 1816|genus
#>   ├─3[d]: 9689|Panthera leo L. 1758|species
#>   └─4[e]: 9694|Panthera tigris L. 1758|species
#> Rank levels: order < family < genus < species
x['b'] # Names can also be used
#> <taxonomy[4]>
#> 1[b]: 9681|Felidae Fischer de Waldheim 1817|family
#> └─2[c]: 9688|Panthera Oken 1816|genus
#>   ├─3[d]: 9689|Panthera leo L. 1758|species
#>   └─4[e]: 9694|Panthera tigris L. 1758|species
#> Rank levels: order < family < genus < species
x[2:3, subtaxa = FALSE] # Disable subtaxa
#> <taxonomy[2]>
#> 1[b]: 9681|Felidae Fischer de Waldheim 1817|family
#> └─2[c]: 9688|Panthera Oken 1816|genus
#> Rank levels: order < family < genus < species
x[3, supertaxa = TRUE] # include supertaxa
#> <taxonomy[5]>
#> 1[a]: 33554|Carnivora Bowdich 1821|order
#> └─2[b]: 9681|Felidae Fischer de Waldheim 1817|family
#>   └─3[c]: 9688|Panthera Oken 1816|genus
#>     ├─4[d]: 9689|Panthera leo L. 1758|species
#>     └─5[e]: 9694|Panthera tigris L. 1758|species
#> Rank levels: order < family < genus < species
x[is_leaf(x)] # Subset by logical vector
#> <taxonomy[3]>
#> 1[d]: 9689|Panthera leo L. 1758|species
#> 2[e]: 9694|Panthera tigris L. 1758|species
#> 3[h]: 9644|Ursus arctos L. 1758|species
#> Rank levels: order < family < genus < species

# Get parts of the taxonomy vector
tax_name(x)
#>                 a                 b                 c                 d 
#>       "Carnivora"         "Felidae"        "Panthera"    "Panthera leo" 
#>                 e                 f                 g                 h 
#> "Panthera tigris"         "Ursidae"           "Ursus"    "Ursus arctos" 
tax_rank(x)
#> <taxon_rank[8]>
#>       a       b       c       d       e       f       g       h 
#>   order  family   genus species species  family   genus species 
#> Rank levels: order < family < genus < species
tax_id(x)
#> <taxon_id[8]>
#>            a            b            c            d            e            f 
#> 33554 (ncbi)  9681 (ncbi)  9688 (ncbi)  9689 (ncbi)  9694 (ncbi)  9632 (ncbi) 
#>            g            h 
#>  9639 (ncbi)  9644 (ncbi) 
tax_db(x)
#> <taxon_db[8]>
#>    a    b    c    d    e    f    g    h 
#> ncbi ncbi ncbi ncbi ncbi ncbi ncbi ncbi 
tax_auth(x)
#> <taxon_authority[8]>
#>                        a                        b                        c 
#>             Bowdich 1821 Fischer de Waldheim 1817                Oken 1816 
#>                        d                        e                        f 
#>                  L. 1758                  L. 1758 Fischer de Waldheim 1817 
#>                        g                        h 
#>                  L. 1758                  L. 1758 
tax_author(x)
#>                     a                     b                     c 
#>             "Bowdich" "Fischer de Waldheim"                "Oken" 
#>                     d                     e                     f 
#>                  "L."                  "L." "Fischer de Waldheim" 
#>                     g                     h 
#>                  "L."                  "L." 
tax_date(x)
#>      a      b      c      d      e      f      g      h 
#> "1821" "1817" "1816" "1758" "1758" "1817" "1758" "1758" 
tax_cite(x)
#>  a  b  c  d  e  f  g  h 
#> "" "" "" "" "" "" "" "" 

# Set parts of the taxonomy vector
tax_name(x) <- tolower(tax_name(x))
tax_rank(x)[1] <- NA
tax_id(x) <- '9999'
tax_db(x) <- 'itis'
tax_auth(x) <- NA
tax_author(x)[2:3] <- c('Joe', 'Billy')
tax_date(x) <- c('1999', '2013', '1796', '1899',
                 '1997', '2003', '1996', '1859')
tax_cite(x)['c'] <- 'Linnaeus, C. (1771). Mantissa plantarum altera generum.'

# Convert to table
tibble::as_tibble(x)
#> # A tibble: 8 × 8
#>   supertaxon tax_name        tax_rank tax_id tax_db tax_author tax_date tax_cite
#>        <int> <chr>           <chr>    <chr>  <chr>  <chr>      <chr>    <chr>   
#> 1         NA carnivora       NA       9999   itis   NA         1999     NA      
#> 2          1 felidae         family   9999   itis   Joe        2013     NA      
#> 3          2 panthera        genus    9999   itis   Billy      1796     Linnaeu…
#> 4          3 panthera leo    species  9999   itis   NA         1899     NA      
#> 5          3 panthera tigris species  9999   itis   NA         1997     NA      
#> 6          1 ursidae         family   9999   itis   NA         2003     NA      
#> 7          6 ursus           genus    9999   itis   NA         1996     NA      
#> 8          7 ursus arctos    species  9999   itis   NA         1859     NA      
as_data_frame(x)
#>   supertaxon        tax_name tax_rank tax_id tax_db tax_author tax_date
#> 1         NA       carnivora     <NA>   9999   itis       <NA>     1999
#> 2          1         felidae   family   9999   itis        Joe     2013
#> 3          2        panthera    genus   9999   itis      Billy     1796
#> 4          3    panthera leo  species   9999   itis       <NA>     1899
#> 5          3 panthera tigris  species   9999   itis       <NA>     1997
#> 6          1         ursidae   family   9999   itis       <NA>     2003
#> 7          6           ursus    genus   9999   itis       <NA>     1996
#> 8          7    ursus arctos  species   9999   itis       <NA>     1859
#>                                                  tax_cite
#> 1                                                    <NA>
#> 2                                                    <NA>
#> 3 Linnaeus, C. (1771). Mantissa plantarum altera generum.
#> 4                                                    <NA>
#> 5                                                    <NA>
#> 6                                                    <NA>
#> 7                                                    <NA>
#> 8                                                    <NA>

# Get taxonomy attributes
subtaxa(x)
#> $a
#> b c d e f g h 
#> 2 3 4 5 6 7 8 
#> 
#> $b
#> c d e 
#> 3 4 5 
#> 
#> $c
#> d e 
#> 4 5 
#> 
#> $d
#> named integer(0)
#> 
#> $e
#> named integer(0)
#> 
#> $f
#> g h 
#> 7 8 
#> 
#> $g
#> h 
#> 8 
#> 
#> $h
#> named integer(0)
#> 
subtaxa(x, value = tax_name(x))
#> $a
#>                 b                 c                 d                 e 
#>         "felidae"        "panthera"    "panthera leo" "panthera tigris" 
#>                 f                 g                 h 
#>         "ursidae"           "ursus"    "ursus arctos" 
#> 
#> $b
#>                 c                 d                 e 
#>        "panthera"    "panthera leo" "panthera tigris" 
#> 
#> $c
#>                 d                 e 
#>    "panthera leo" "panthera tigris" 
#> 
#> $d
#> named character(0)
#> 
#> $e
#> named character(0)
#> 
#> $f
#>              g              h 
#>        "ursus" "ursus arctos" 
#> 
#> $g
#>              h 
#> "ursus arctos" 
#> 
#> $h
#> named character(0)
#> 
subtaxa(x, value = as_taxon(x))
#> $a
#> <taxon[7]>
#>                                    b                                    c 
#>         9999|felidae Joe 2013|family       9999|panthera Billy 1796|genus 
#>                                    d                                    e 
#>    9999|panthera leo NA 1899|species 9999|panthera tigris NA 1997|species 
#>                                    f                                    g 
#>          9999|ursidae NA 2003|family             9999|ursus NA 1996|genus 
#>                                    h 
#>    9999|ursus arctos NA 1859|species 
#> Rank levels: order < family < genus < species
#> 
#> $b
#> <taxon[3]>
#>                                    c                                    d 
#>       9999|panthera Billy 1796|genus    9999|panthera leo NA 1899|species 
#>                                    e 
#> 9999|panthera tigris NA 1997|species 
#> Rank levels: order < family < genus < species
#> 
#> $c
#> <taxon[2]>
#>                                    d                                    e 
#>    9999|panthera leo NA 1899|species 9999|panthera tigris NA 1997|species 
#> Rank levels: order < family < genus < species
#> 
#> $d
#> <taxon[0]>
#> Rank levels: order < family < genus < species
#> 
#> $e
#> <taxon[0]>
#> Rank levels: order < family < genus < species
#> 
#> $f
#> <taxon[2]>
#>                                 g                                 h 
#>          9999|ursus NA 1996|genus 9999|ursus arctos NA 1859|species 
#> Rank levels: order < family < genus < species
#> 
#> $g
#> <taxon[1]>
#>                                 h 
#> 9999|ursus arctos NA 1859|species 
#> Rank levels: order < family < genus < species
#> 
#> $h
#> <taxon[0]>
#> Rank levels: order < family < genus < species
#> 
n_subtaxa(x)
#> a b c d e f g h 
#> 7 3 2 0 0 2 1 0 
supertaxa(x)
#> $a
#> named integer(0)
#> 
#> $b
#> a 
#> 1 
#> 
#> $c
#> b a 
#> 2 1 
#> 
#> $d
#> c b a 
#> 3 2 1 
#> 
#> $e
#> c b a 
#> 3 2 1 
#> 
#> $f
#> a 
#> 1 
#> 
#> $g
#> f a 
#> 6 1 
#> 
#> $h
#> g f a 
#> 7 6 1 
#> 
n_supertaxa(x)
#> a b c d e f g h 
#> 0 1 2 3 3 1 2 3 
leaves(x)
#> $a
#> d e h 
#> 4 5 8 
#> 
#> $b
#> d e 
#> 4 5 
#> 
#> $c
#> d e 
#> 4 5 
#> 
#> $d
#> named integer(0)
#> 
#> $e
#> named integer(0)
#> 
#> $f
#> h 
#> 8 
#> 
#> $g
#> h 
#> 8 
#> 
#> $h
#> named integer(0)
#> 
n_leaves(x)
#> a b c d e f g h 
#> 3 2 2 0 0 1 1 0 
is_leaf(x)
#>     a     b     c     d     e     f     g     h 
#> FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE  TRUE 
stems(x)
#> $a
#> named integer(0)
#> 
is_stem(x)
#>     a     b     c     d     e     f     g     h 
#> FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE 
roots(x)
#> a 
#> 1 
is_root(x)
#>     a     b     c     d     e     f     g     h 
#>  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE 
internodes(x)
#> b f g 
#> 2 6 7 
is_internode(x)
#>     a     b     c     d     e     f     g     h 
#> FALSE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE 
```
