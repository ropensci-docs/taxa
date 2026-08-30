# taxa casting functions

Functions used internally for casting taxon objects to other types. They
have to be exported to work, but they are not intended to be directly
used by most users.

## Usage

``` r
# S3 method for class 'taxa_classification'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_classification(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_classification'
vec_cast.taxa_classification(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_classification'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_classification'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_classification'
vec_cast.integer(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon'
vec_cast.taxa_taxon(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxon(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_authority'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_authority(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_authority'
vec_cast.taxa_taxon_authority(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon_authority(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_authority'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxon_authority(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_authority'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'integer'
vec_cast.taxa_taxon_authority(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_authority'
vec_cast.data.frame(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_db(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db'
vec_cast.taxa_taxon_db(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon_db(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxon_db(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db_def'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_db_def(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_db_def'
vec_cast.taxa_taxon_db_def(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'integer'
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.integer(x, to, ..., x_arg, to_arg)

# S3 method for class 'double'
vec_cast.taxa_taxon_id(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.double(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_id'
vec_cast.data.frame(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_rank(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast.taxa_taxon_rank(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon_rank(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxon_rank(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'double'
vec_cast.taxa_taxon_rank(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast.double(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank'
vec_cast.data.frame(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank_level'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxon_rank_level(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank_level'
vec_cast.taxa_taxon_rank_level(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxon_rank_level(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon_rank_level'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxonomy'
vec_cast(x, to, ..., x_arg, to_arg)

# Default S3 method
vec_cast.taxa_taxonomy(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxonomy'
vec_cast.taxa_taxonomy(x, to, ..., x_arg, to_arg)

# S3 method for class 'character'
vec_cast.taxa_taxonomy(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxonomy'
vec_cast.character(x, to, ..., x_arg, to_arg)

# S3 method for class 'factor'
vec_cast.taxa_taxonomy(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxonomy'
vec_cast.factor(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxon'
vec_cast.taxa_taxonomy(x, to, ..., x_arg, to_arg)

# S3 method for class 'taxa_taxonomy'
vec_cast.taxa_taxon(x, to, ..., x_arg, to_arg)
```
