# Taxon class

**maturing lifecycle** Used to store information about taxa, such as
names, ranks, and IDs.

## Usage

``` r
taxon(name = character(0), rank = NA, id = NA, auth = NA, .names = NA, ...)
```

## Arguments

- name:

  The names of taxa. Inputs with be coerced into a
  [character](https://rdrr.io/r/base/character.html) vector if anything
  else is given.

- rank:

  The ranks of taxa. Inputs with be coerced into a
  [taxon_rank](https://docs.ropensci.org/taxa/reference/taxon_rank.md)
  vector if anything else is given.

- id:

  The ids of taxa. These should be unique identifier and are usually
  associated with a database. Inputs with be coerced into a
  [taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md)
  vector if anything else is given.

- auth:

  The authority of the taxon. Inputs with be coerced into a
  [taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
  vector if anything else is given.

- .names:

  The names of the vector.

- ...:

  Additional arguments.

## Value

An `S3` object of class `taxa_taxon`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

# Create taxon name vector
x <- taxon(c('A', 'B', 'C'))
x <- taxon(name = c('Homo sapiens', 'Bacillus', 'Ascomycota', 'Ericaceae'),
           rank = c('species', 'genus', 'phylum', 'family'),
           id = taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi'),
           auth = c('Linnaeus, 1758', 'Cohn 1872', NA, 'Juss., 1789'))
names(x) <- c('a', 'b', 'c', 'd')

# Get parts of the taxon name vector
tax_name(x)
#>              a              b              c              d 
#> "Homo sapiens"     "Bacillus"   "Ascomycota"    "Ericaceae" 
tax_rank(x)
#> <taxon_rank[4]>
#>       a       b       c       d 
#> species   genus  phylum  family 
#> Rank levels: phylum < family < genus < species
tax_id(x)
#> <taxon_id[4]>
#>           a           b           c           d 
#> 9606 (ncbi) 1386 (ncbi) 4890 (ncbi) 4345 (ncbi) 
tax_db(x)
#> <taxon_db[4]>
#>    a    b    c    d 
#> ncbi ncbi ncbi ncbi 
tax_auth(x)
#> <taxon_authority[4]>
#>             a             b             c             d 
#> Linnaeus 1758     Cohn 1872           NA     Juss. 1789 
tax_author(x)
#>          a          b          c          d 
#> "Linnaeus"     "Cohn"         NA    "Juss." 
tax_date(x)
#>      a      b      c      d 
#> "1758" "1872"     "" "1789" 
tax_cite(x)
#>  a  b  c  d 
#> "" "" "" "" 

# Set parts of the taxon name vector
tax_name(x) <- tolower(tax_name(x))
tax_rank(x)[1] <- NA
tax_name(x)['b'] <- 'Billy'
tax_id(x) <- '9999'
tax_db(x) <- 'itis'
tax_auth(x) <- NA
tax_author(x)[2:3] <- c('Joe', 'Billy')
tax_date(x) <- c('1999', '2013', '1796', '1899')
tax_cite(x)[1] <- 'Linnaeus, C. (1771). Mantissa plantarum altera generum.'

# Manipulate taxon name vectors
x[1:3]
#> <taxon[3]>
#>                                 a                                 b 
#>         9999|homo sapiens NA 1999         9999|Billy Joe 2013|genus 
#>                                 c 
#> 9999|ascomycota Billy 1796|phylum 
#> Rank levels: phylum < family < genus < species
x[tax_rank(x) > 'family']
#> <taxon[2]>
#>                      <NA>                         b 
#>                        NA 9999|Billy Joe 2013|genus 
#> Rank levels: phylum < family < genus < species
x['b'] <- NA
x[c('c', 'd')] <- 'unknown'
is.na(x)
#> [1] FALSE  TRUE FALSE FALSE

# Use as columns in tables
tibble::tibble(x = x, y = 1:4)
#> # A tibble: 4 × 2
#>   x                             y
#>   <taxon>                   <int>
#> 1 9999|homo sapiens NA 1999     1
#> 2 NA                            2
#> 3 unknown                       3
#> 4 unknown                       4
data.frame(x = x, y = 1:4)
#>                           x y
#> 1 9999|homo sapiens NA 1999 1
#> 2                        NA 2
#> 3                   unknown 3
#> 4                   unknown 4

# Converting to tables
tibble::as_tibble(x)
#> # A tibble: 4 × 7
#>   tax_name     tax_rank tax_id tax_db tax_author tax_date tax_cite              
#>   <chr>        <chr>    <chr>  <chr>  <chr>      <chr>    <chr>                 
#> 1 homo sapiens NA       9999   itis   NA         1999     Linnaeus, C. (1771). …
#> 2 NA           NA       NA     NA     NA         NA       NA                    
#> 3 unknown      NA       NA     NA     NA         NA       NA                    
#> 4 unknown      NA       NA     NA     NA         NA       NA                    
as_data_frame(x)
#>       tax_name tax_rank tax_id tax_db tax_author tax_date
#> 1 homo sapiens     <NA>   9999   itis       <NA>     1999
#> 2         <NA>     <NA>   <NA>   <NA>       <NA>     <NA>
#> 3      unknown     <NA>   <NA>   <NA>       <NA>     <NA>
#> 4      unknown     <NA>   <NA>   <NA>       <NA>     <NA>
#>                                                  tax_cite
#> 1 Linnaeus, C. (1771). Mantissa plantarum altera generum.
#> 2                                                    <NA>
#> 3                                                    <NA>
#> 4                                                    <NA>
```
