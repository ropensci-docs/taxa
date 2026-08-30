# Valid taxonomy databases

This defines the valid taxonomic databases that can be used in
[taxon_db](https://docs.ropensci.org/taxa/reference/taxon_db.md) objects
and objects that use
[taxon_db](https://docs.ropensci.org/taxa/reference/taxon_db.md)
objects, such as
[taxon_id](https://docs.ropensci.org/taxa/reference/taxon_id.md) and
[taxon](https://docs.ropensci.org/taxa/reference/taxon.md). `db_ref$get`
can be used to see information for the databases. Users can add their
own custom databases to the list using `db_ref$set`. For each database
the following information is included:

- The URL for the website associated with the database

- A short description

- The regular expression that defines valid taxon IDs

- The ranks used in the database if specified

## Usage

``` r
db_ref
```

## Format

An object of class `list` of length 3.

## Attribution

This code is based on the code handling options in the knitr package.

## Examples

``` r

# List all database definitions
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

# Get a specific database definition
db_ref$get('ncbi')
#> <taxon_db_def[1]>
#>    _____________________ ncbi ______________________
#>    url:         http://www.ncbi.nlm.nih.gov/taxonomy
#>    desc:        NCBI Taxonomy Database              
#>    id_regex:    [0-9]+                              
#>    rank_levels:                                     

# Add or overwrite a database definition
db_ref$set(
  name = "my_new_database",
  url = "http://www.my_tax_database.com",
  desc = "I just made this up",
  id_regex = ".*"
)

# Reset definitions to default values
db_ref$reset()
```
