# Check if taxa are stems

Check if each taxon is a stem. A stem is any taxa from a root to the
first taxon with multiple subtaxa.

## Usage

``` r
is_stem(x)
```

## Arguments

- x:

  An object with taxonomic relationships, like
  [taxonomy](https://docs.ropensci.org/taxa/reference/taxonomy.md)
  objects.

## See also

Other stem functions:
[`stems()`](https://docs.ropensci.org/taxa/reference/stems.md)

## Examples

``` r
x <- taxonomy(c('Carnivora', 'Felidae', 'Panthera', 'Panthera leo',
                'Panthera tigris'),
              supertaxa = c(NA, 1, 2, 3, 3))
is_stem(x)
#> [1]  TRUE  TRUE FALSE FALSE FALSE
```
