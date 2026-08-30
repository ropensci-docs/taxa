# Set and get taxon authority dates

Set and get the taxon authority dates in objects that have them, such as
[taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_date(x)

# S3 method for class 'taxa_classification'
tax_date(x) <- value

tax_date(x)

tax_date(x) <- value

# S3 method for class 'taxa_taxon'
tax_date(x)

# S3 method for class 'taxa_taxon'
tax_date(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_date(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_date(x)

# S3 method for class 'taxa_taxonomy'
tax_date(x)

# S3 method for class 'taxa_taxonomy'
tax_date(x) <- value
```

## Arguments

- x:

  An object with taxon authority dates.

- value:

  The taxon authority dates to set. Inputs will be coerced into a
  [character](https://rdrr.io/r/base/character.html) vector.

## Examples

``` r
x <- taxon_authority(c('Cham. & Schldl.', 'L.'),
                     date = c('1827', '1753'))
tax_date(x)
#> [1] "1827" "1753"
tax_date(x)[1] <- "1984"
tax_date(x) <- c(NA, '1800')
```
