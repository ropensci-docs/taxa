# Set and get taxon IDs

Set and get the taxon IDs in objects that have them, such as
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_id(x)

# S3 method for class 'taxa_classification'
tax_id(x) <- value

tax_id(x)

tax_id(x) <- value

# S3 method for class 'taxa_taxon'
tax_id(x)

# S3 method for class 'taxa_taxon'
tax_id(x) <- value

# S3 method for class 'taxa_taxonomy'
tax_id(x)

# S3 method for class 'taxa_taxonomy'
tax_id(x) <- value
```

## Arguments

- x:

  An object with taxon IDs.

- value:

  The taxon IDs to set. Inputs will be coerced into a
  [taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md)
  vector.

## Examples

``` r
x <- taxon(name = c('Homo sapiens', 'Bacillus', 'Ascomycota', 'Ericaceae'),
           rank = c('species', 'genus', 'phylum', 'family'),
           id = taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi'),
           auth = c('Linnaeus, 1758', 'Cohn 1872', NA, 'Juss., 1789'))

tax_id(x)
#> <taxon_id[4]>
#> [1] 9606 (ncbi) 1386 (ncbi) 4890 (ncbi) 4345 (ncbi)
tax_id(x) <- paste0('00', tax_id(x))
tax_id(x)[1] <- '00000'
```
