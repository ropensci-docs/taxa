# Set and get taxon authority citations

Set and get the taxon authority citations in objects that have them,
such as
[taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_cite(x)

# S3 method for class 'taxa_classification'
tax_cite(x) <- value

tax_cite(x)

tax_cite(x) <- value

# S3 method for class 'taxa_taxon'
tax_cite(x)

# S3 method for class 'taxa_taxon'
tax_cite(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_cite(x) <- value

# S3 method for class 'taxa_taxon_authority'
tax_cite(x)

# S3 method for class 'taxa_taxonomy'
tax_cite(x)

# S3 method for class 'taxa_taxonomy'
tax_cite(x) <- value
```

## Arguments

- x:

  An object with taxon authority dates.

- value:

  The taxon citations to set. Inputs will be coerced into a
  [taxon_authority](https://docs.ropensci.org/taxa/reference/taxon_authority.md)
  vector.

## Examples

``` r
x <- taxon_authority(c('Cham. & Schldl.', 'L.'),
                     date = c('1827', '1753'),
                     citation = c(NA, 'Species Plantarum'))
tax_cite(x)
#> [1] NA                  "Species Plantarum"
tax_cite(x)[1] <- "Cham. et al 1984"
```
