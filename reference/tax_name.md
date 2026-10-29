# Set and get taxon names

Set and get the taxon names in objects that have them, such as
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects. Note
that this is not the same as adding vector names with
[names](https://rdrr.io/r/base/names.html).

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_name(x)

# S3 method for class 'taxa_classification'
tax_name(x) <- value

tax_name(x)

tax_name(x) <- value

# S3 method for class 'taxa_taxon'
tax_name(x)

# S3 method for class 'taxa_taxon'
tax_name(x) <- value

# S3 method for class 'taxa_taxonomy'
tax_name(x)

# S3 method for class 'taxa_taxonomy'
tax_name(x) <- value
```

## Arguments

- x:

  An object with taxon names.

- value:

  The taxon names to set. Inputs will be coerced into a
  [character](https://rdrr.io/r/base/character.html) vector.

## Examples

``` r
x <- taxon(name = c('Homo sapiens', 'Bacillus', 'Ascomycota', 'Ericaceae'),
           rank = c('species', 'genus', 'phylum', 'family'),
           id = taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi'),
           auth = c('Linnaeus, 1758', 'Cohn 1872', NA, 'Juss., 1789'))

tax_name(x)
#> [1] "Homo sapiens" "Bacillus"     "Ascomycota"   "Ericaceae"   
tax_name(x) <- tolower(tax_name(x))
tax_name(x)[1] <- 'Billy'
```
