# owf-data-co-municipal-water-providers #

This repository contains the [Open Water Foundation (OWF)](http://openwaterfoundation.org) dataset for Colorado municipal water providers.
This is a foundational dataset that provides unique identifiers and other data for municipal water providers.
The identifiers can be used to link other datasets, such as municipalities.
OWF has created and is maintaining this dataset to facilitate work on various data analysis and visualization projects in Colorado.

## Repository Contents ##

The repository contains the following:

```text
.gitignore                      		Git configuration file to ignore files that should not be committed to the repository.
.gitattributes                  		Git configuration file indicate repository configuration, in particular handling
												of line-ending and binary files.
build/
						Folder used by TSTool to create products for publication.
data/                           		Folder containing data files.
  Colorado-Municipal-Water-Providers.xlsx     	Simple Excel file containing core data.
  Colorado-Municipal-Water-Providers.csv      	The Excel file contents from the Water_Providers worksheet converted to a csv file, useful for automated processing.
  Providers-in-Multiple-Counties.csv		The Excel file contents from the Providers_in_Multiple_Counties worksheet converted to a csv file, useful for automated processing.
doc/
  ?                             		Additional documentation for the dataset.
TSTool/                         		TSTool software command files to process data into useful forms.
  README.md                     		Explanation of TSTool command files used to process the core data into other products.
```

### Colorado-Municipal-Water-Providers.xlsx Contents ###

The core Excel workbook that serves as the master data contains the following data columns within the **Water_Providers** worksheet.

* **Water_Provider_Name** -- name of the water provider
* **FIPS_ID** -- [Federal Information Processing Standard](https://www.census.gov/geo/reference/codes/place.html) code, to link federal datasets
* **DOLA_ID** -- identifier used by Colorado's [Department of Local Affairs (DOLA)](https://dola.colorado.gov/lgis/municipalities.jsf), to link DOLA datasets
* **BNDSS_ID** -- Basin Needs Decision Support System identifier, also used in [Water Efficiency Data Portal](http://cowaterefficiency.com/unauthenticated_home), to link Colorado Water Conservation Board datasets
* **PWS_ID** -- [Public Water System](https://ofmpub.epa.gov/apex/sfdw/f?p=108:1:::NO:::) identifier, to link Environmental Protection Agency and Colorado Department of Public Health and Environment datasets
* **BusinessEntity_ID** -- state-assigned identification number for a business entity, from the [Colorado Information Marketplace](https://data.colorado.gov/Business/Business-Entities-in-Colorado/4ykn-tg5h/data), to link state datasets
* **LocalGovtType** -- indication of the type of local government entity or if private
* **County** -- county in which the water provider is contained.  Several water providers serve more than one county.  In these cases, the county is listed as "Multiple".  The actual county names can be found in the **Providers_in_Multiple_Counties** worksheet.
* **Number_of_Counties** -- number of counties the water provider serves.  This is a quick way to determine if the entity serves multiple counties and if so, the counties can be found in the **Providers_in_Multiple_Counties** worksheet.
* **Comment** -- any other information about the water provider

Descriptions of identifiers are also provided in the **Notes** worksheet within the workbook.
  
## Attribution ##

The data sources for this dataset are listed below.

* Data available from the [U.S. Census Bureau](https://www.census.gov/geo/reference/codes/place.html) includes municipal Federal Information Processing Standard (FIPS) codes.  The FIPS code is for municipalities only, not other types of water providers such as water and sanitation districts.
* The Colorado Department of Local Affairs (DOLA)'s [Local Government Information System](https://dola.colorado.gov/lgis/municipalities.jsf) uses a local government ID (LG ID).  OWF is using DOLA_ID instead of LG ID to add more description to the identifier.
* The Environmental Protection Agency (EPA)'s [Safe Drinking Water Information System (SDWIS)](https://ofmpub.epa.gov/apex/sfdw/f?p=108:1:::NO:::) contains information about Public Water System IDs (PWS ID).  PWS IDs are used for water quality reports.  The Colorado Department of Public Health and Environment (CDPHE)'s Water Quality Control Division also uses the PWS ID.
* The BNDSS ID is from the Basin Needs Decision Support System, which was initially developed as a project for the Colorado Water Conservation Board (CWCB) from 2009-2011.  The BNDSS resulted in a prototype gap analysis 
(the difference between water demand and available supply for Colorado) and a prototype database and website to manage water provider and Identified Projects and Processes data.  The BNDSS ID is included in this dataset
so that it can be potentially linked to datasets that result from the Statewide Water Supply Initiative (SWSI) Update.

## How to Use the Data ##

The Colorado Municipal Water Providers dataset provides a complete statewide list of municipal water providers assembled from multiple sources.  There are several unique identifiers for each water provider and the dataset allows cross-referencing the identifiers
so that other datasets can be joined.  For example, the [Colorado Municipalities dataset](owf-data-co-municipalities) uses municipal water provider
identifiers and can be used to link additional data.

The Excel or csv forms can be used as tabular datasets as is, to create filtered lists or to link to other datasets.

The format and contents of the dataset will change over time.  It is recommended to save a copy of the dataset.

## License ##

The license is being determined.  All the data are public so there are not really any restrictions on use.

## Contributing ##

The Open Water Foundation is currently working on an initial release of the dataset to support a
data visualization project for the South Platte Basin of Colorado.
If you use the dataset and have comments, please contact the maintainers and/or use the GitHub issues to provide feedback.

## Maintainers ##

Kristin Swaim (@kswaim, kristin.swaim@openwaterfoundation.org) is the primary maintainer at the Open Water Foundation.

Steve Malers (@smalers, steve.malers@openwaterfoundation.org) is the secondary contact.

## Contributors ##

None yet, other than OWF staff.
