# Set and get taxon ID databases

Set and get the taxon ID databases in objects that have them, such as
[taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md)
objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_db(x)

# S3 method for class 'taxa_classification'
tax_db(x) <- value

tax_db(x)

tax_db(x) <- value

# S3 method for class 'taxa_taxon'
tax_db(x)

# S3 method for class 'taxa_taxon'
tax_db(x) <- value

# S3 method for class 'taxa_taxon_id'
tax_db(x)

# S3 method for class 'taxa_taxon_id'
tax_db(x) <- value

# S3 method for class 'taxa_taxonomy'
tax_db(x)

# S3 method for class 'taxa_taxonomy'
tax_db(x) <- value
```

## Arguments

- x:

  An object with taxon authority dates.

- value:

  The taxon citations to set. Inputs will be coerced into a
  [taxon_db](https://docs.ropensci.org/taxa/reference/taxon_db.md)
  vector.

## Examples

``` r
x <- taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi')
tax_db(x)
#> <taxon_db[4]>
#> [1] ncbi ncbi ncbi ncbi
tax_db(x) <- 'nbn'
tax_db(x)[2] <- 'itis'
```
