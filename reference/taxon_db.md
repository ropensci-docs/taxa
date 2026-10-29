# Taxon database class

**maturing lifecycle** Used to store the names of taxon databases
defined in [db_ref](https://docs.ropensci.org/taxa/reference/db_ref.md).
Primarily used in other classes like
[taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md) to
define databases for each item.

## Usage

``` r
taxon_db(db = character(), .names = NULL, ...)
```

## Arguments

- db:

  Zero or more taxonomic database names. Should be a name contained in
  [db_ref](https://docs.ropensci.org/taxa/reference/db_ref.md). Inputs
  will be transformed to a
  [character](https://rdrr.io/r/base/character.html) vector if possible.

- .names:

  The names of the vector.

- ...:

  Additional arguments.

## Value

An `S3` object of class `taxa_taxon_db`

## See also

Other classes:
[`[.taxa_classification()`](https://docs.ropensci.org/taxa/reference/taxonomy.md),
[`classification()`](https://docs.ropensci.org/taxa/reference/classification.md),
[`taxon()`](https://docs.ropensci.org/taxa/reference/taxon.md),
[`taxon_authority()`](https://docs.ropensci.org/taxa/reference/taxon_authority.md),
[`taxon_id()`](https://docs.ropensci.org/taxa/reference/taxon_id.md),
[`taxon_rank()`](https://docs.ropensci.org/taxa/reference/taxon_rank.md)

## Examples

``` r

# Making new objects
x <- taxon_db(c('ncbi', 'ncbi', 'itis'))
x
#> <taxon_db[3]>
#> [1] ncbi ncbi itis

# Manipulating objects
as.character(x)
#> [1] "ncbi" "ncbi" "itis"
x[2:3]
#> <taxon_db[2]>
#> [1] ncbi itis
x[2:3] <- 'nbn'
names(x) <- c('a', 'b', 'c')
x['b']
#> <taxon_db[1]>
#>   b 
#> nbn 
x['b'] <- 'nbn'
x[x == 'itis'] <- 'gbif'

# Using as columns in tables
tibble::tibble(x = x, y = 1:3)
#> # A tibble: 3 × 2
#>   x            y
#>   <tax_db> <int>
#> 1 ncbi         1
#> 2  nbn         2
#> 3  nbn         3
data.frame(x = x, y = 1:3)
#>      x y
#> 1 ncbi 1
#> 2  nbn 2
#> 3  nbn 3

# Converting to tables
tibble::as_tibble(x)
#> # A tibble: 3 × 1
#>   tax_db
#>   <chr> 
#> 1 ncbi  
#> 2 nbn   
#> 3 nbn   
as_data_frame(x)
#>   tax_db
#> 1   ncbi
#> 2    nbn
#> 3    nbn

# Trying to use an invalid database generates an error
# x <- taxon_db(c('ncbi', 'ncbi', 'my_custom_db'))
# x[x == 'itis'] <- 'my_custom_db'

# Listing known databases and their properties
db_ref$get()
#> <taxon_db_def[8]>
#>    _____________________ ncbi ______________________
#>    url:         http://www.ncbi.nlm.nih.gov/taxonomy
#>    desc:        NCBI Taxonomy Database              
#>    id_regex:    [0-9]+                              
#>    rank_levels:                                     
#> 
#>    _____________________________ gbif _____________________________
#>    url:         http://www.gbif.org/developer/species              
#>    desc:        GBIF Taxonomic Backbone                            
#>    id_regex:    [0-9]+                                             
#>    rank_levels: kingdom < phylum < order < family < genus < species
#> 
#>    _________________________________ bold _________________________________
#>    url:         http://www.boldsystems.org                                 
#>    desc:        Barcode of Life                                            
#>    id_regex:    [0-9]+                                                     
#>    rank_levels: phylum < class < order < family < subfamily < genus < spec…
#> 
#>    ___________________ col ___________________
#>    url:         http://www.catalogueoflife.org
#>    desc:        Catalogue of Life             
#>    id_regex:    [a-z0-9]{32}                  
#>    rank_levels:                               
#> 
#>    ______________ eol ______________
#>    url:         http://eol.org      
#>    desc:        Encyclopedia of Life
#>    id_regex:    [0-9]+              
#>    rank_levels:                     
#> 
#>    ____________________ nbn ____________________
#>    url:         https://nbn.org.uk              
#>    desc:        UK National Biodiversity Network
#>    id_regex:    [A-Z]{5}[0-9]{10}               
#>    rank_levels:                                 
#> 
#>    ________________ tps ________________
#>    url:         http://www.tropicos.org/
#>    desc:        Tropicos                
#>    id_regex:    [0-9]+                  
#>    rank_levels:                         
#> 
#>    _______________________ itis _______________________
#>    url:         http://www.itis.gov                    
#>    desc:        Integrated Taxonomic Information System
#>    id_regex:    [0-9]+                                 
#>    rank_levels:                                        

# Adding and using a new database
db_ref$set(name = 'my_custom_db', desc = 'I just made this up')
db_ref$get()
#> <taxon_db_def[9]>
#>    _____________________ ncbi ______________________
#>    url:         http://www.ncbi.nlm.nih.gov/taxonomy
#>    desc:        NCBI Taxonomy Database              
#>    id_regex:    [0-9]+                              
#>    rank_levels:                                     
#> 
#>    _____________________________ gbif _____________________________
#>    url:         http://www.gbif.org/developer/species              
#>    desc:        GBIF Taxonomic Backbone                            
#>    id_regex:    [0-9]+                                             
#>    rank_levels: kingdom < phylum < order < family < genus < species
#> 
#>    _________________________________ bold _________________________________
#>    url:         http://www.boldsystems.org                                 
#>    desc:        Barcode of Life                                            
#>    id_regex:    [0-9]+                                                     
#>    rank_levels: phylum < class < order < family < subfamily < genus < spec…
#> 
#>    ___________________ col ___________________
#>    url:         http://www.catalogueoflife.org
#>    desc:        Catalogue of Life             
#>    id_regex:    [a-z0-9]{32}                  
#>    rank_levels:                               
#> 
#>    ______________ eol ______________
#>    url:         http://eol.org      
#>    desc:        Encyclopedia of Life
#>    id_regex:    [0-9]+              
#>    rank_levels:                     
#> 
#>    ____________________ nbn ____________________
#>    url:         https://nbn.org.uk              
#>    desc:        UK National Biodiversity Network
#>    id_regex:    [A-Z]{5}[0-9]{10}               
#>    rank_levels:                                 
#> 
#>    ________________ tps ________________
#>    url:         http://www.tropicos.org/
#>    desc:        Tropicos                
#>    id_regex:    [0-9]+                  
#>    rank_levels:                         
#> 
#>    _______________________ itis _______________________
#>    url:         http://www.itis.gov                    
#>    desc:        Integrated Taxonomic Information System
#>    id_regex:    [0-9]+                                 
#>    rank_levels:                                        
#> 
#>    _________ my_custom_db _________
#>    url:         NA                 
#>    desc:        I just made this up
#>    id_regex:    NA                 
#>    rank_levels:                    
x <- taxon_db(c('ncbi', 'ncbi', 'my_custom_db'))
```
