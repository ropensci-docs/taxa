# Taxon authority class

**maturing lifecycle** Used to store information on taxon authorities,
such as author names, date, and citation.

## Usage

``` r
taxon_authority(
  author = character(),
  date = "",
  citation = "",
  .names = "",
  extract_date = TRUE
)
```

## Arguments

- author:

  Zero or more author names.

- date:

  Zero or more dates.

- citation:

  Zero or more literature citations.

- .names:

  The names of the vector.

- extract_date:

  If `TRUE` (the default), then if a date is detected in the `author`
  input and no `date` input is given, then the date is separated from
  the author input.

## Value

An `S3` object of class `taxa_taxon_authority`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_db()`](https://docs.ropensci.org/taxa/reference/taxon_db.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

# Making new objects
x <- taxon_authority(c('A', 'B', 'C'))
x <- taxon_authority(c('Cham. & Schldl.', 'L.'),
                     date = c('1827', '1753'))

# Manipulating objects
as.character(x)
#> [1] "Cham. & Schldl. 1827" "L. 1753"             
x[2]
#> <taxon_authority[1]>
#> [1] L. 1753
x[2] <- 'ABC'
names(x) <- c('a', 'b')
x['b'] <- 'David Bowie'
tax_author(x)[1] <- tolower(tax_author(x)[1])
tax_author(x)
#>                 a                 b 
#> "cham. & schldl."     "David Bowie" 
tax_date(x) <- c('2000', '1234')
tax_date(x)
#>      a      b 
#> "2000" "1234" 
tax_cite(x)[2] <- c('Linnaeus, C. (1771). Mantissa plantarum altera generum.')
tax_cite(x)
#>                                                         a 
#>                                                        "" 
#>                                                         b 
#> "Linnaeus, C. (1771). Mantissa plantarum altera generum." 

# Using as columns in tables
tibble::tibble(x = x, y = 1:2)
#> # A tibble: 2 × 2
#>   x                        y
#>   <tax_auth>           <int>
#> 1 cham. & schldl. 2000     1
#> 2 David Bowie 1234         2
data.frame(x = x, y = 1:2)
#>                      x y
#> 1 cham. & schldl. 2000 1
#> 2     David Bowie 1234 2

# Converting to tables
tibble::as_tibble(x)
#> # A tibble: 2 × 3
#>   tax_author      tax_date tax_cite                                             
#>   <chr>           <chr>    <chr>                                                
#> 1 cham. & schldl. 2000     ""                                                   
#> 2 David Bowie     1234     "Linnaeus, C. (1771). Mantissa plantarum altera gene…
as_data_frame(x)
#>        tax_author tax_date
#> 1 cham. & schldl.     2000
#> 2     David Bowie     1234
#>                                                  tax_cite
#> 1                                                        
#> 2 Linnaeus, C. (1771). Mantissa plantarum altera generum.
```
