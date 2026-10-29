# Set and get taxon authors

Set and get taxon authors in objects that have them, such as
[taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_author(x)

# S3 method for class 'taxa_classification'
tax_author(x) <- value

tax_author(x)

tax_author(x) <- value

# S3 method for class 'taxa_taxon'
tax_author(x)

# S3 method for class 'taxa_taxon'
tax_author(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_author(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_author(x)

# S3 method for class 'taxa_taxonomy'
tax_author(x)

# S3 method for class 'taxa_taxonomy'
tax_author(x) <- value
```

## Arguments

- x:

  An object with taxon authors.

- value:

  The taxon authors to set. Inputs will be coerced into a
  [character](https://rdrr.io/r/base/character.html) vector.

## Examples

``` r
x <- taxon_authority(c('Cham. & Schldl.', 'L.'),
                     date = c('1827', '1753'))
tax_author(x)
#> [1] "Cham. & Schldl." "L."             
tax_author(x)[1] <- "Billy"
tax_author(x) <- tolower(tax_author(x))
```
