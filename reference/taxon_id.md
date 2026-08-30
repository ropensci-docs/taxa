# Taxon ID class

**maturing lifecycle** Used to store the ID corresponding to taxa,
either arbitrary or from a particular taxonomy database. This is
typically used to store taxon IDs in
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects.

## Usage

``` r
taxon_id(id = character(), db = "", .names = NULL)
```

## Arguments

- id:

  Zero or more taxonomic ids. Inputs will be transformed to a
  [character](https://rdrr.io/r/base/character.html) vector if possible.

- db:

  The name(s) of the database(s) associated with the IDs. If not `NA`
  (the default), the input must consist of names of databases in
  [db_ref\$get()](https://docs.ropensci.org/taxa/reference/db_ref.md).

- .names:

  The names that will be applied to the vector.

## Value

An `S3` object of class `taxa_taxon_id`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

# Making new objects
x <- taxon_id(c('A', 'B', 'C'))
x <- taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi')
x <- taxon_id(c('9606', '1386', '4890', '4345'),
              db = c('ncbi', 'ncbi', 'itis', 'itis'))
names(x) <- c('a', 'b', 'c', 'd')

# Manipulating objects
as.character(x)
#>      a      b      c      d 
#> "9606" "1386" "4890" "4345" 
x[2:3]
#> <taxon_id[2]>
#>           b           c 
#> 1386 (ncbi) 4890 (itis) 
x[2:3] <- 'ABC'
x[c('a', 'c')] <- '123'
x[['b']] <- taxon_id('123423', db = 'ncbi')
tax_db(x)
#> <taxon_db[4]>
#>    a    b    c    d 
#>      ncbi      itis 
tax_db(x) <- 'nbn'
c(x, x)
#> <taxon_id[8]>
#>            a            b            c            d            a            b 
#>    123 (nbn) 123423 (nbn)    123 (nbn)   4345 (nbn)    123 (nbn) 123423 (nbn) 
#>            c            d 
#>    123 (nbn)   4345 (nbn) 

# Using as columns in tables
tibble::tibble(x = x, y = 1:4)
#> # A tibble: 4 × 2
#>   x                y
#>   <tax_id>     <int>
#> 1 123 (nbn)        1
#> 2 123423 (nbn)     2
#> 3 123 (nbn)        3
#> 4 4345 (nbn)       4
data.frame(x = x, y = 1:4)
#>              x y
#> 1    123 (nbn) 1
#> 2 123423 (nbn) 2
#> 3    123 (nbn) 3
#> 4   4345 (nbn) 4

# Convert to tables
tibble::as_tibble(x)
#> # A tibble: 4 × 2
#>   tax_id tax_db
#>   <chr>  <chr> 
#> 1 123    nbn   
#> 2 123423 nbn   
#> 3 123    nbn   
#> 4 4345   nbn   
as_data_frame(x)
#>   tax_id tax_db
#> 1    123    nbn
#> 2 123423    nbn
#> 3    123    nbn
#> 4   4345    nbn

# Trying to use an invalid ID with a specified database causes an error
#taxon_id('NOLETTERS', db = 'ncbi')
```
