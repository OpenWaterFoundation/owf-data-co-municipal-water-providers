# owf-data-co-municipal-water-providers #

This repository contains the [Open Water Foundation (OWF)](http://openwaterfoundation.org) dataset for Colorado municipal water providers.
This is a foundational dataset that provides unique identifiers and other data for municipal water providers.
The identifiers can be used to link other datasets, such as municipalities.
OWF has created and is maintaining this dataset to facilitate work on various data analysis and visualization projects in Colorado.

## Repository Contents ##

The repository contains the following:

```text
.gitignore                      Git configuration file to ignore files that should not be committed to the repository.
.gitattributes                  Git configuration file indicate repository configuration, in particular handling
                                of line-ending and binary files.
build/
                                Folder used by TSTool to create products for publication.
data/                           Folder containing data files.
  ?.xlsx                        Simple Excel file containing core data.
  ?.csv                         The Excel file contents converted to a csv file, useful for automated processing.
doc/
  ?                             Additional documentation for the dataset.
TSTool/                         TSTool software command files to process data into useful forms.
  README.md                     Explanation of TSTool command files used to process the core data into other products.
```

### ?.xlsx Contents ###

The core Excel workbook that serves as the master data contains the following,
which is also listed in the ? worksheet:

* Kristin fill out...

## Attribution ##

The data sources for this dataset are listed below.

* Kristin include list and links.

## How to Use the Data ##

The Colorado municipal water providers dataset provides a complete statewide list of municipal water providers assembled from multiple sources.
There are several unique identifiers for each water provider and the dataset allows cross-referencing the identifiers
so that other datasets can be joined.
For example, the [Colorado municipalities dataset](owf-data-co-municipalities) dataset uses municipal water provider
identifiers can be used to link additional data.

The Excel or csv forms can be used as tabular datasets as is, or to link to other datasets.

## License ##

The license is being determined.
All the data are public so there are not really any restrictions on use.

## Contributing ##

The Open Water Foundation is currently working on an initial release of the dataset to support a
data visualization project in the South Platte Basin of Colorado.
If you use the dataset and have comments, please contact the maintainers and/or use the GitHub issues to provide feedback.

## Maintainers ##

Kristin Swaim (@kswaim, kristin.swaim@openwaterfoundation.org) is the primary maintainer at the Open Water Foundation.

Steve Malers (@smalers, steve.malers@openwaterfoundation.org) is the secondary contact.

## Contributors ##

None yet, other than OWF staff.
