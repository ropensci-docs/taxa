# Set and get taxon authorities

Set and get the taxon authorities in objects that have them, such as
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) objects. Note
that this sets all the authority information, such as author name, date,
and citations. To set or get just one of part of the authorities, use
[tax_author](https://docs.ropensci.org/taxa/reference/tax_author.md),
[tax_date](https://docs.ropensci.org/taxa/reference/tax_date.md), or
[tax_cite](https://docs.ropensci.org/taxa/reference/tax_cite.md)
instead.

## Usage

``` r
# S3 method for class 'taxa_classification'
tax_auth(x)

# S3 method for class 'taxa_classification'
tax_auth(x) <- value

tax_auth(x)

tax_auth(x) <- value

# S3 method for class 'taxa_taxon'
tax_auth(x)

# S3 method for class 'taxa_taxon'
tax_auth(x) <- value

# S3 method for class 'taxa_taxonomy'
tax_auth(x)

# S3 method for class 'taxa_taxonomy'
tax_auth(x) <- value
```

## Arguments

- x:

  An object with taxon authorities.

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

tax_auth(x)
#> <taxon_authority[4]>
#> [1] Linnaeus 1758 Cohn 1872     NA            Juss. 1789   
tax_auth(x) <- tolower(tax_auth(x))
tax_auth(x)[1] <- 'Billy'
```
