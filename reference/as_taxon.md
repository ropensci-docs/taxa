# Convert to a [taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vector

Convert other objects to
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md) vectors.
Compatible base R vectors can also be converted using the [taxon
constructor](https://docs.ropensci.org/taxa/reference/taxon.md).

## Usage

``` r
as_taxon(x, ...)
```

## Arguments

- x:

  An object to be converted to a taxon vector

- ...:

  Additional parameters.

## Examples

``` r

# Convert a taxonomy object to a taxon vector
x <- taxonomy(taxon(name = c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                             'Panthera tigris', 'Ursidae', 'Ursus', 'Ursus arctos'),
                    rank = c('order', 'family', 'genus', 'species',
                             'species', 'family', 'genus', 'species'),
                    id = taxon_id(c('33554', '9681', '9688', '9689',
                                    '9694', '9632', '9639', '9644'),
                                  db = 'ncbi'),
                    auth = c('Bowdich, 1821', 'Fischer de Waldheim, 1817', 'Oken, 1816', 'L., 1758',
                             'L., 1758', 'Fischer de Waldheim, 1817', 'L., 1758', 'L., 1758')),
              supertaxa = c(NA, 1, 2, 3, 3, 1, 6, 7))
names(x) <- letters[1:8]
as_taxon(x)
#> <taxon[8]>
#>                                            a 
#>           33554|Carnivora Bowdich 1821|order 
#>                                            b 
#> 9681|Felidae Fischer de Waldheim 1817|family 
#>                                            c 
#>                9688|Panthera Oken 1816|genus 
#>                                            d 
#>            9689|Panthera leo L. 1758|species 
#>                                            e 
#>         9694|Panthera tigris L. 1758|species 
#>                                            f 
#> 9632|Ursidae Fischer de Waldheim 1817|family 
#>                                            g 
#>                     9639|Ursus L. 1758|genus 
#>                                            h 
#>            9644|Ursus arctos L. 1758|species 
#> Rank levels: order < family < genus < species

# Convert base R vectors
as_taxon(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo'))
#> <taxon[4]>
#> [1] Carnivora    Felidae      Panthera     Panthera leo
as_taxon(factor(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo')))
#> <taxon[4]>
#> [1] Carnivora    Felidae      Panthera     Panthera leo
```
