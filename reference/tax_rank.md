# Set and get taxon ranks

Set and get the taxon ranks in objects that have them, such as
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_rank(x)

# S3 method for class 'taxa_classification'
tax_rank(x) <- value

tax_rank(x)

tax_rank(x) <- value

# S3 method for class 'taxa_taxon'
tax_rank(x)

# S3 method for class 'taxa_taxon'
tax_rank(x) <- value

# S3 method for class 'taxa_taxonomy'
tax_rank(x)

# S3 method for class 'taxa_taxonomy'
tax_rank(x) <- value
```

## Arguments

- x:

  An object with taxon ranks.

- value:

  The taxon ranks to set. Inputs will be coerced into a
  [taxon_rank](https://docs.ropensci.org/taxa/reference/taxon_rank.md)
  vector.

## Examples

``` r
x <- taxon(name = c('Homo sapiens', 'Bacillus', 'Ascomycota', 'Ericaceae'),
           rank = c('species', 'genus', 'phylum', 'family'),
           id = taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi'),
           auth = c('Linnaeus, 1758', 'Cohn 1872', NA, 'Juss., 1789'))

tax_rank(x)
#> <taxon_rank[4]>
#> [1] species genus   phylum  family 
#> Rank levels: phylum < family < genus < species
tax_rank(x) <- 'species'
tax_rank(x)[1] <- taxon_rank('family')
```
