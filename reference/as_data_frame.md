# Convert a taxa object to a `data.frame`

Convert the information in a taxa object to a `data.frame` using base R
vectors as columns. Use
[`tibble::as_tibble()`](https://tibble.tidyverse.org/reference/as_tibble.html)
to convert to tibbles.

## Usage

``` r
as_data_frame(
  x,
  row.names = NULL,
  optional = FALSE,
  ...,
  stringsAsFactors = FALSE
)
```

## Arguments

- x:

  An object defined by taxa, such as
  [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) or
  [taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md)

- row.names:

  `NULL` or a character vector giving the row names for the data frame.
  Missing values are not allowed.

- optional:

  logical. If `TRUE`, setting row names and converting column names (to
  syntactic names: see
  [`make.names`](https://rdrr.io/r/base/make.names.html)) is optional.
  Note that all of R's base package
  [`as.data.frame()`](https://rdrr.io/r/base/as.data.frame.html) methods
  use `optional` only for column names treatment, basically with the
  meaning of
  [`data.frame`](https://rdrr.io/r/base/data.frame.html)`(*, check.names = !optional)`.
  See also the `make.names` argument of the `matrix` method.

- ...:

  additional arguments to be passed to or from methods.

- stringsAsFactors:

  logical: should the character vector be converted to a factor?

## Examples

``` r
x <- taxon(name = c('Homo sapiens', 'Bacillus', 'Ascomycota', 'Ericaceae'),
           rank = c('species', 'genus', 'phylum', 'family'),
           id = taxon_id(c('9606', '1386', '4890', '4345'), db = 'ncbi'),
           auth = c('Linnaeus, 1758', 'Cohn 1872', NA, 'Juss., 1789'))
as_data_frame(x)
#>       tax_name tax_rank tax_id tax_db tax_author tax_date tax_cite
#> 1 Homo sapiens  species   9606   ncbi   Linnaeus     1758         
#> 2     Bacillus    genus   1386   ncbi       Cohn     1872         
#> 3   Ascomycota   phylum   4890   ncbi       <NA>                  
#> 4    Ericaceae   family   4345   ncbi      Juss.     1789         
```
