# owf-data-co-municipal-water-providers #

This repository contains the [Open Water Foundation (OWF)](http://openwaterfoundation.org) dataset for Colorado municipal water providers.
This is a foundational dataset that provides unique identifiers and other data for municipal water providers.
The identifiers can be used to link other datasets, such as municipalities.
OWF has created and is maintaining this dataset to facilitate work on various data analysis and visualization projects in Colorado.

The following sections provide a summary of the project repository:

* [Repository Contents](#repository-contents)
* [`Colorado-Municipal-Water-Providers.xlsx` Contents](#colorado-municipal-water-providersxlsx-contents)
    + [Worksheet Columns](#worksheet-columns)
    + [Identifier Conventions for BNDSS_ID and OWF_ID](#identifier-conventions-for-bndss_id-and-owf_id)
    + [Data Flags](#data-flags)
    + [Worksheet Conventions](#worksheet-conventions)
    + [Worksheets in Workbook](#worksheets-in-workbook)
* [How to Use the Data](#how-to-use-the-data)
* [Attribution](#attribution)
* [Dataset Workflow](#dataset-workflow)
* [Disclaimer](#disclaimer)
* [License](#license)
* [Maintainers and Contributing](#maintainers-and-contributing)

## Repository Contents ##

The repository contains the following:

```text
data/                                       Folder containing data files.
  co-municipal-water-providers.xlsx         Excel file containing core data.
  co-municipal-water-providers.geojson      The Excel file contents from the Water_Providers worksheet converted to a GeoJSON file,
  co-municipal-water-providers.csv          The Excel file contents from the Water_Providers worksheet converted to a csv file,
                                            useful for automated processing.
  co-municipal-water-providers-county-relate.csv
                                            The Excel file contents from the WaterProvider_County_Relate worksheet converted to a csv file,
                                            useful for automated processing.
data-orig/                                  Folder containing original data files downloaded from agency websites.
  Colorado-FIPS-Places.xlsx                 The data file containing original data download from the
                                            U.S. Census Bureau containing FIPS IDs.
  Colorado-GNIS-Civil.csv                   The data file containing original data download from the
                                            Geographic Names Information System containing GNIS IDs.
  Colorado-LocalGovernment-IDs.csv          The data file that is the attribute table of the GIS shapefile downloaded from the
                                            Special Districts website that contains local government IDs (DOLA_LG_ID)
  Colorado-Municipal-Boundaries.geojson     Exported spatial data file from the Colorado Information Marketplace's
                                            Municipal Boundaries in Colorado map.
  Colorado-Municipality-PointLocation.csv   Saved attribute table of Colorado-Municipal-Boundaries.geojson that contains
                                            coordinates of the centroid of each municipality's boundaries.
  Colorado-PWS-IDs.csv                      The data file containing original data download from the
                                            EPA's Safe Drinking Water Information System containing PWS IDs.
  Colorado-Special-Districts.geojson        Exported spatial data file from the Colorado Information Marketplace's
                                            All Special Districts in Colorado map.
  Colorado-WaterProvider-PointLocation.csv  Saved attribute table of Colorado-Special-Districts.geojson that
                                            contains coordinates of the centroid of each district's boundaries.
  README.md                                 Explanation of folder contents, description of data files,
                                            and the methodology used to obtain the data and mapping to the joined dataset.
data-orig-workflow/                         Folder containing workflows to process manual and automated downloaded files for data files.
  process-original-data-to-csv.tstool       TSTool command file to automate processing original data into csv.
doc/
workflow/                                   TSTool command files to process data into useful forms.
  01-convert-formats.tstool                 TSTool command file that processes the core dataset from .xlsx to .geojson and .csv.
.gitattributes                              Git configuration file indicate repository configuration,
                                            in particular handling of line-ending and binary files.
.gitignore                                  Git configuration file to ignore files that should not be committed to the repository.
README.md                                   Explanation of repository contents, data files and sources and
                                            TSTool command files used to process the core data into other products.
```

## `co-municipal-water-providers.xlsx` Contents ##

### Worksheet Columns ###

The core Excel workbook that serves as the master data contains the following data columns within the ***WaterProvider*** worksheet.

| **Column** | **Description** |
| -- | -- |
| **WaterProviderName** | Name of the water provider. |
| **FIPS_ID** | [Federal Information Processing Standard](https://www.census.gov/geo/reference/codes/place.html) code, to link federal datasets. |
| **FIPS_ID_Flag** | Data status of FIPS_ID values; see more detail below. |
| **GNIS_ID** | [Geographic Names Information System](https://geonames.usgs.gov/apex/f?p=138:1:9185633219989) identifier, to link federal datasets. |
| **GNIS_ID_Flag** | Data status of GNIS_ID values; see more detail below. |
| **DOLA_LG_ID** | Identifier used by Colorado's [Department of Local Affairs (DOLA)](https://dola.colorado.gov/lgis/municipalities.jsf), to link DOLA datasets. |
| **DOLA_LG_ID_Flag** | Data status of DOLA_LG_ID values; see more detail below. |
| **BNDSS_ID** | Basin Needs Decision Support System identifier, also used in [Water Efficiency Data Portal](http://cowaterefficiency.com/unauthenticated_home), to link Colorado Water Conservation Board datasets. |
| **BNDSS_ID_Flag** |  Data status of BNDSS_ID values; see more detail below. |
| **PWS_ID** | [Public Water System](https://ofmpub.epa.gov/apex/sfdw/f?p=108:1:::NO:::) identifier, to link Environmental Protection Agency and [Colorado Department of Public Health and Environment](https://www.colorado.gov/pacific/cdphe/data) datasets. |
| **PWS_ID_Flag** | Data status of PWS_ID values; see more detail below. |
| **BusinessEntity_ID** | State-assigned identification number for a business entity, from the [Colorado Information Marketplace](https://data.colorado.gov/Business/Business-Entities-in-Colorado/4ykn-tg5h/data), to link state datasets. |
| **BusinessEntity_ID_Flag** | Data status of BusinessEntity_ID values; see more detail below. |
| **OWF_ID** | Unique text identifier created by OWF to ensure that one type of ID contains values for every water provider. |
| **OWF_ID_Flag** | Data status of OWF_ID values; see more detail below. |
| **LocalGovtType** | Indication of the type of local government entity or if a company.  Filled by selecting from a drop-down list.  Choices are explained in the **LocalGovtType** worksheet. |
| **EntityStartYear** | Year the provider began operation or was incorporated **TO BE ADDED**. |
| **EntityStartYear_Flag** | Data status of EntityStartYear values **TO BE ADDED**. |
| **EntityEndYear** | Year the provider ceased operations or was dissolved, if applicable  **TO BE ADDED**. |
| **EntityEndYear_Flag** | Data status of EntityEndYear values **TO BE ADDED**. |
| **County** | County in which the water provider's service area is contained.  Several water providers serve more than one county.  In these cases, the county is listed as "Multiple".  The actual county names can be found in the **WaterProvider_County_Relate** worksheet. |
| **NumCounty** | Number of counties the water provider serves.  This is a quick way to determine if the entity serves multiple counties and if so, the counties can be found in the **WaterProvider_County_Relate** worksheet. |
| **Latitude** | Latitude of provider's point location in decimal degrees. |
| **Longitude** | Longitude of provider's point location in decimal degrees. |
| **Lat_Long_Flag** | Indication of how latitude and longitude were determined; g1 = coordinates are based on the mailing address of the provider. |
| **Website** | Website URL of the provider. |
| **Website_Flag** | Data status of Website values; see more detail below. |
| **Comment** | any other information about the water provider. |

### Identifier Conventions for BNDSS_ID and OWF_ID ###

The following conventions are used to create BNDSS_IDs and OWF_IDs.

| **Abbrevation** | **Long Version** |
| --------------- | ---------------- |
| `MD`            | Metropolitan District |
| `WD`            | Water District |
| `WSD`           | Water and Sanitation District |
| `WCD`           | Water Conservation District |
| `WA`            | Water Authority |
| `WC`            | Water Company |
| `MWC`           | Mutual Water Company |
| `WS`            | Water System |

| **Abbrevation** | **Long Version** |
| --------------- | -- |
| `Co`            | County |
| `Crk`           | Creek |
| `Hls`           | Hills |
| `Hts`           | Heights |
| `Mt`            | Mount |
| `Mtn`           | Mountain |
| `Spgs`          | Springs |
| `St`            | Saint |
| `Vlg`           | Village |
| `Vly`           | Valley |
| `Ft`            | Fort |
| `N`             | North |
| `E`             | East |
| `W`             | West |
| `S`             | South |

### Data Flags ###

Some data columns have an accompanying second column with the same name and `_Flag` appended to the original column name.
These columns are an indication of data status as it relates to missing data.  The following conventions are used:

| **Flag Value** | **Description** |
| -------------- | -- |
| `G`            | Value is known/good. |
| `g`            | Value is estimated (but good).  The associated cell is also highlighted in yellow. |
| `N`            | Value is not applicable for the provider and a blank cell is expected. |
| `M`            | Value is known to be missing in original source and therefore a blank cell indicates that a value cannot be provided. |
| `m`            | Value is estimated to be missing.  The associated cell is also highlighted in gray. |
| `z`            | Value is unable to be confirmed.  A value is possible but cannot be confirmed one way or the other.  The associated cell is also highlighted in orange. |
| `x`            | OWF has not made an attempt to populate the cell at this time. The value is missing because OWF has not attempted to find the value.  The associated cell is also highlighted in black. |
| `C`            | OWF_ID has been created based on BNDSS_ID naming conventions. |
| `D`            | ID is a known/good value but provider has dissolved (currently applies only to BusinessEntity_ID). |

Single-character flags may also be followed with a number, as in `g1`.
These flags are specific to certain columns and are detailed above in the descriptions of the data columns.  

### Worksheet Conventions ###

Colors are visible only in `xlsx` files and not `csv` files.

Column names are taken from original sources if possible.
For clarity and attribution, agency abbreviations may be added to the original column name.
Column name length is not restricted, therefore, some data representations such as Esri shapefiles may contain truncated column names.
In such cases, alternative formats such as GeoJSON are recommended.

Descriptions of identifiers are also provided in the **Notes** worksheet within the workbook.
This worksheet also details how the original data were downloaded and where to find those files.

### Worksheets in Workbook ###

Worksheets within the workbook are as follows:

| **Worksheet** | **Description** |
| -- | -- |
| ***WaterProvider*** | Main dataset.  Municipal Water Providers in Colorado, described above. |
| ***WaterProvider_County_Relate*** | Water providers whose service areas are in more than one county.  This worksheet is organized so that each county served by a water provider is its own record.  Therefore, the same water provider may be listed in more than one row and be associated with a different county.  This will allow for the establishment of one-to-many relationships when linking to and processing other datasets. |
| ***County*** | Counties in Colorado.  It is used to fill in county data in other worksheets to ensure data consistency, i.e., no grammatical errors when typing in a county name. |
| ***LocalGovtType*** | Local government types or if the water provider is a company.  It is used to fill in local government type data in other worksheets to ensure data consistency. |
| ***ChangeLog*** | Changes made to the dataset, the date they occurred and who made the changes. |
| ***Metadata_WaterProvider*** | Metadata for data columns in the ***WaterProvider*** worksheet. |

## How to Use the Data ##

The Colorado Municipal Water Providers dataset provides a complete statewide list of municipal water providers assembled from multiple sources.
There are several unique identifiers for each water provider and the dataset allows cross-referencing the identifiers
so that other datasets can be joined.
For example, the [Colorado Municipalities dataset](https://data.openwaterfoundation.org/state/co/owf/municipalities/)
uses municipal water provider identifiers and can be used to link additional data.

The Excel and csv files can be used as tabular datasets as is,
to create filtered lists or to link to other datasets.
Data-processing software such as TSTool can be used to link this dataset to other datasets.
Datasets can be used within GIS software to create maps.

The format and contents of the dataset may change over time.  It is recommended to save a copy of the dataset.

## Attribution ##

The data sources for this dataset are listed below.

| **Data Source** | **Description** |
| -- | -- |
| [U.S. Census Bureau](https://www.census.gov/geo/reference/codes/place.html) | Includes municipal Federal Information Processing Standard (FIPS) codes.  The FIPS code is for municipalities only, not other types of water providers such as water and sanitation districts.  OWF manually cross-referenced the PLACENAME column to the WaterProviderName. |
| U.S. Geological Survey (USGS)'s [Geographic Names Information System (GNIS)](https://geonames.usgs.gov/apex/f?p=138:1:9185633219989) | GNIS is the Federal and national standard for geographic nomenclature.  The USGS developed the GNIS in support of the U.S. Board on Geographic Names as the official repository of domestic geographic names data.  OWF manually cross-referenced the Feature Name column to the WaterProviderName. |
| The Colorado Department of Local Affairs (DOLA)'s [Local Government Information System](https://dola.colorado.gov/lgis/municipalities.jsf) uses a local government ID (LG ID). | Data were copied from the website.  GIS shapefiles containing the local government ID are available from the [Special Districts](https://demography.dola.colorado.gov/CO_SpecialDistrict/) website from the State Demography Office.  OWF manually cross-referenced the LGNAME column to the WaterProviderName.  OWF is using DOLA_LG_ID instead of LG ID to add more description to the identifier.  The Special Districts dataset was also the source for website URLs for many water providers.  For water providers that are municipalities, website URLs come from the [Colorado Municipalities](https://github.com/OpenWaterFoundation/owf-data-co-municipalities) dataset. |
| Environmental Protection Agency (EPA)'s [Safe Drinking Water Information System (SDWIS)](https://ofmpub.epa.gov/apex/sfdw/f?p=108:1:::NO:::) contains information about Public Water System IDs (PWS ID). | PWS IDs are used for water quality reports.  The Colorado Department of Public Health and Environment (CDPHE)'s Water Quality Control Division also uses the PWS ID.  OWF manually cross-referenced the PWS Name column to the WaterProviderName.  If names did not match exactly, it was sometimes necessary to search for the website of the provider and then search for water quality reports that contain the PWS ID. |
| BNDSS_ID is from the Basin Needs Decision Support System | The BNDSS was initially developed as a project for the Colorado Water Conservation Board (CWCB) from 2009-2011.  The BNDSS resulted in a prototype gap analysis (the difference between water demand and available supply for Colorado) and a prototype database and website to manage water provider and Identified Projects and Processes data.  The BNDSS_ID is included in this dataset so that it can be potentially linked to datasets that result from the Statewide Water Supply Initiative (SWSI) Update, now a part of the Colorado Water Plan. |
| The BusinessEntity_ID is from the [Colorado Information Marketplace](https://data.colorado.gov/Business/Business-Entities-in-Colorado/4ykn-tg5h/data) and is a state-assigned identification number.  Because there are not a large number of water providers that are considered businesses, OWF manually entered the ID where appropriate.
| Open Water Foundation OWF_ID | OWF_ID was created for each water provider by OWF in order to ensure that at least one type of identifier contains values for every water provider.  The OWF_ID is needed to potentially link every water provider to other datasets.  OWF_ID is used in "Relate" worksheets and csv files as the identifier for this reason. |
| Latitude and Longitude coordinates from the [Colorado Information Marketplace](https://data.colorado.gov/). | Latitude and Longitude coordinates were found for most providers by accessing Colorado Information Marketplace maps:  [Municipal Boundaries in Colorado](https://data.colorado.gov/Municipal/Municipal-Boundaries-in-Colorado/u943-ics6) and [All Special Districts in Colorado](https://data.colorado.gov/Government/All-Special-Districts-in-Colorado/dm2a-biqr).  The maps were downloaded as GeoJSON files. |

## Dataset Workflow ##

This dataset began as a list of water providers from the BNDSS project and each water provider had its own unique text identifier, the BNDSS ID.
Approximately 430 water providers were in this dataset.
OWF then received a dataset from the CWCB in January 2017 that contained population and water use data for over 400 water providers as part of its Covered Entities Database.
Many of the water providers overlapped with the BNDSS list of water providers,
but approximately 100 providers needed to be added to the BNDSS list, for an overall total of 531 water providers.
Once this initial dataset was created, OWF then manually cross-referenced water providers to the identifiers
described above for FIPS, GNIS, DOLA, PWS and Business Entities.  From here, the general workflow is as follows:

1. The dataset is saved in `.xlsx` format:
    1. Data flags are created for many of the data columns that indicate data status as described above.
    2. The data are formatted as a table to allow for data filtering.
2. The TSTool command file
    [(`01-convert-formats.tstool`)](workflow/01-convert-formats.tstool)
    is run to convert the dataset into GeoJSON and CSV format.

See also the [`data-orig-workflow/README.md`](data-orig-workflow/README.md) documentation, which provides more details.

## Disclaimer ##

OWF has attempted to create a complete statewide dataset of municipal water providers.
OWF will attempt to fill data gaps as the dataset is used for analysis and funding allows for more data review.
OWF provides no guarantee as to the accuracy of the data.
**Use this dataset at your own risk.**  OWF welcomes feedback to improve the dataset.

## License ##

This dataset is distributed using the
[Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0) License](https://creativecommons.org/licenses/by-sa/4.0/).
Please provide attribution.

## Maintainers and Contributing ##

This dataset is maintained by the Open Water Foundation.
The Open Water Foundation is adding value by cross-referencing datasets.
If you use the dataset and have comments, please contact the maintainers and/or use the GitHub issues to provide feedback.
