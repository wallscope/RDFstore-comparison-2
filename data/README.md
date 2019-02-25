# Constructing the Dataset

This dataset is a subset of DBpedia connected to a subset of Yago.

## DBpedia

I downloaded the following localized sections of DBpedia in English from [here](https://wiki.dbpedia.org/downloads-2016-10):

- Article Categories
- Category Labels
- Disambiguations
- Genders
- Geo Coordinates
- Geo Coordinates Mappingbased
- Geonames Links
- Homepages
- Images
- Instance Types Stdtyped Dbo
- Instance Types Transitive
- Labels
- Long Abstracts
- Mappingbased Literals
- Mappingbased Objects
- Short Abstracts
- SKOS Categories
- Specific Mappingbased Properties

## Yago

I then downloaded the following sections of [Yago](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/yago/downloads/):

From TAXONOMY:
- yagoSchema
- yagoTypes
- yagoTaxonomy

From CORE:
- yagoLabels
- yagoFacts

From LINK:
- yagoDBpediaInstances
- yagoDBpediaClasses

## Cleaning

Yago is very messy so I had to clean it using the following command from the directory containing the `.ttl` files:

``` sed -i 's/|/-/g' ./* && sed -i 's/\\\\/-/g' ./* && sed -i 's/–/-/g' ./* ```

## Splitting

I then split all of the `.ttl` files into multiple `.ttl` files that contained 100k triples each (maximum) using Stardog's split tool.

I gzipped each of these for storage space and transportation.

## Final dataset stats

This process should result in a directory conatining 2,491 `.ttl.gz` files with a total size of 5.3GB.