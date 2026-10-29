# taxa comparison functions

Functions used internally for casting taxon objects to other types. They
have to be exported to work, but they are not intended to be directly
used by most users.

## Usage

``` r
# S3 method for class 'taxa_taxon'
vec_proxy_equal(x, ...)

# S3 method for class 'taxa_taxon_authority'
vec_proxy_equal(x, ...)

# S3 method for class 'taxa_taxon_id'
vec_proxy_equal(x, ...)

# S3 method for class 'taxa_taxon_rank'
vec_proxy_compare(x, ...)

# S3 method for class 'taxa_taxon_rank'
vec_proxy_equal(x, ...)

# S3 method for class 'taxa_taxon_rank'
Ops(e1, e2)

# S3 method for class 'taxa_taxonomy'
vec_proxy_equal(x, ...)
```
