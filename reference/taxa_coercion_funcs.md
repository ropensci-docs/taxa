# taxa coercion functions

Functions used internally for coercing taxon objects and other objects
to common data types. They have to be exported to work, but they are not
intended to be directly used by most users.

## Usage

``` r
# S3 method for class 'taxa_classification'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_classification(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_classification(x, y, ...)

# S3 method for class 'taxa_classification'
vec_ptype2.taxa_classification(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_classification(x, y, ...)

# S3 method for class 'taxa_classification'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_classification(x, y, ...)

# S3 method for class 'taxa_classification'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon(x, y, ...)

# S3 method for class 'taxa_taxon'
vec_ptype2.taxa_taxon(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon(x, y, ...)

# S3 method for class 'taxa_taxon'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxon(x, y, ...)

# S3 method for class 'taxa_taxon'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon_authority(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon_authority(x, y, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype2.taxa_taxon_authority(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon_authority(x, y, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxon_authority(x, y, ...)

# S3 method for class 'taxa_taxon_authority'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon_db(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon_db(x, y, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype2.taxa_taxon_db(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon_db(x, y, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxon_db(x, y, ...)

# S3 method for class 'taxa_taxon_db'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon_id(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon_id(x, y, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype2.taxa_taxon_id(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon_id(x, y, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxon_id(x, y, ...)

# S3 method for class 'taxa_taxon_id'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon_rank(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon_rank(x, y, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype2.taxa_taxon_rank(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon_rank(x, y, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxon_rank(x, y, ...)

# S3 method for class 'taxa_taxon_rank'
vec_ptype2.factor(x, y, ...)

# S3 method for class 'taxa_taxon_rank_level'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxon_rank_level(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxon_rank_level(x, y, ...)

# S3 method for class 'taxa_taxon_rank_level'
vec_ptype2.taxa_taxon_rank_level(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxon_rank_level(x, y, ...)

# S3 method for class 'taxa_taxon_rank_level'
vec_ptype2.character(x, y, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype2(x, y, ...)

# Default S3 method
vec_ptype2.taxa_taxonomy(x, y, ..., x_arg = "", y_arg = "")

# S3 method for class 'vctrs_unspecified'
vec_ptype2.taxa_taxonomy(x, y, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype2.taxa_taxonomy(x, y, ...)

# S3 method for class 'character'
vec_ptype2.taxa_taxonomy(x, y, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype2.character(x, y, ...)

# S3 method for class 'factor'
vec_ptype2.taxa_taxonomy(x, y, ...)

# S3 method for class 'taxa_taxonomy'
vec_ptype2.factor(x, y, ...)
```
