# taxa printing functions

Functions used internally for printing information in taxon objects.
They have to be exported to work, but they are not intended to be
directly used by most users.

## Usage

``` r
# S3 method for class 'taxa_classification'
format(x, ...)

# S3 method for class 'taxa_classification'
obj_print_data(x, ...)

# S3 method for class 'taxa_classification'
obj_print_footer(x, ...)

# S3 method for class 'taxa_classification'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_classification'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_classification'
pillar_shaft(x, ...)

# S3 method for class 'taxa_taxon'
format(x, ...)

# S3 method for class 'taxa_taxon'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon'
obj_print_footer(x, ...)

# S3 method for class 'taxa_taxon'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon'
pillar_shaft(x, ...)

# S3 method for class 'taxa_taxon_authority'
format(x, ...)

# S3 method for class 'taxa_taxon_authority'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_authority'
pillar_shaft(x, ...)

# S3 method for class 'taxa_taxon_db'
format(x, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_db_def'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon_db_def'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_id'
format(x, ...)

# S3 method for class 'taxa_taxon_id'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_id'
pillar_shaft(x, ...)

# S3 method for class 'taxa_taxon_rank'
format(x, ...)

# S3 method for class 'taxa_taxon_rank'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon_rank'
obj_print_footer(x, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_rank'
pillar_shaft(x, ...)

# S3 method for class 'taxa_taxon_rank_level'
format(x, ...)

# S3 method for class 'taxa_taxon_rank_level'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxon_rank_level'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxon_rank_level'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxon_rank_level'
toString(x, ...)

# S3 method for class 'taxa_taxonomy'
format(x, ...)

# S3 method for class 'taxa_taxonomy'
obj_print_data(x, ...)

# S3 method for class 'taxa_taxonomy'
obj_print_footer(x, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype_abbr(x, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype_full(x, ...)

# S3 method for class 'taxa_taxonomy'
pillar_shaft(x, ...)
```
