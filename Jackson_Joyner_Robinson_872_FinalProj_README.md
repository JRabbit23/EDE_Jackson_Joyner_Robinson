# EDE_Jackson_Joyner_Robinson
Repository for Fall 2023 ENVIRON 872L Class Final Project

## Summary
This dataset was prepared in Fall 2023 as part of a final project for Environmental Data Analytics (ENV 872) at Duke University's Nicholas School of the Environment.

The repository contains 10 years of data (2010-2020) detailing the United State's renewable energy generation capacity by governing state political party.

The purpose of the project is to analyze the relationship between renewable energy growth at the state-level by political party leadership (using governor as a proxy). The research questions to be answered are:

(1) What is the relationship between the percent penetration of renewable technology (i.e., solar, wind) and state governor?

(2) Has renewable penetration grown in any states that have had a single-party governor over a longer period of time?

We employed three types of analysis in order to answer these questions: (1) linear regression, (2) time series analysis, and (3) spatial analysis.

## Investigators

Jonathan Joyner - Duke Nicholas School of the Environment
Email: jbj41@duke.edu

Aditi Jackson - Duke Nicholas School of the Environment
Emial: apj22@duke.edu

David Robinson - Duke Nicholas School of the Environment
Email: dhr20@duke.edu

## Keywords

* *Generation Asset* refers to a single energy-producing facility (aka a power plant)
* *Renewable Energy* refers to energy generated from assets that use natural resources (i.e. sun, wind) as fuel.
* *Nameplate Capacity* refers to the maximum rated amount of energy generation of a particular asset, measured in Megwatts;
* *Blue States* refer to states with long histories of Democratic party control
* *Red States* refer to states with long histories of Republican party control
* *Purple States* refer to states with oscillations in the controlling party

## Database Information

Data were accessed from two different sites.

_(1) US Governors Data:_
https://www.openicpsr.org/openicpsr/project/102000/version/V3/view?path=/openicpsr/102000/fcr:versions/V3/united_states_governors_1775_2020.csv&type=file

Data were collected from Open ICPSR - an open source database. The file contains records for state governor by political party affiliation and years in office spanning 1775 - 2020. More info can be found here: https://www.openicpsr.org/openicpsr/project/102000/version/V3/view

Data were downloaded directly from ICPSR's website using the first link provided above. From the link:
* Download This File (top right button)

File was downloaded and saved as a CSV file.

Data accessed on 2023-11-15.

_(2) eGRID 2010-2020:_
https://www.epa.gov/egrid/download-data

Data were collected from the U.S. Environmental Protection Agency's Emissions & Generation Resource Integrated Database (eGRID), which contains data on generation capacity and emissions factors associated with almost all power generating assets in the U.S.. More information can be found here: https://www.epa.gov/egrid

Note: eGRID data is released every two years. To amass ten years of data we aggregated the datasets for 2020, 2018, 2016, 2014, 2012, and 2010.

Data were collected directly from the EPA eGrid site (https://www.epa.gov/egrid). The following steps were taken from this homepage:
* Download Detailed Data (scroll down, button in center of page)
* Historical eGRID Data (scroll down, button at bottom of page)
* Download eGRID2020, eGRID2018 as Excel files
* Download eGRID Historical Files 1996-2016 as zip file
* Open zipped file and select eGRID2016, eGRID2014, eGRID2012, eGRID2010

Five files were saved as `eGRID2020.xlsx`, `eGRID2018.xlsx`, `eGRID2016.xlsx`, `eGRID2014.xlsx`,`eGRID2012.xlsx`,`eGRID2010.xlsx` 

Data accessed on 2023-11-15.

## Folder structure, file formats, and naming conventions

_(1) Data Folder contains the following:_
* Raw
--> eGRID data: DatabaseYear.xlsx
--> Governor data: Database_StartYear_EndYear.csv
--> US state data: DatabaseName.shp

* Processed Folder contains the following:
--> Combined data set of all U.S. renewable energy: Database_StartYear_EndYear_EnergyType.csv 
--> Final dataset with eGRID and political data: DatabaseA_DatabaseB_StartYear_EndYear.csv

_(2) Output Folder contains the following:_
* Final RMD file containing analysis: Jackson_Joyner_Robinson_ENV872_Project.RMD
* Final PDF file containing analysis: Jackson_Joyner_Robinson_ENV872_Project.pdf

## Metadata

_Columns in Raw eGRID files (PLNT tabs)_
* Only the PLNT tab was utilized for each eGRID dataset. The PLNT tab contains plant-level data for U.S. generation assets.
* Please see pages 42 - 57 of eGRID's technical guide for descriptions of column names for the plant tab used in analysis: https://www.epa.gov/system/files/documents/2023-01/eGRID2021_technical_guide.pdf
* Columns used in analysis include:
--> PNAME: Name of generation asset; class = character
--> PSTATABB: U.S. state abbreviation; class = charater
--> NAMEPCAP: Nameplate capacity of generating asset in Megawatts (MW); class = numeric
--> PLFUELCT: The fuel category for the primary fuel of the plant (e.g. wind, solar, nuclear, biomass, hydro); class = character
--> ORISPL: Office of Regulatory Information Systems Plant code; class = numeric
--> LAT: Plant latitude; class = character
--> LON: Plant longitude; class = character


_Columns in Raw US_Governors file_
* governor: Name of state governor; class = character
* state: Full U.S. state name; class = character
* time_in_office: Time governor held office (term); class = character
* party: Democrat, Republican, Independent, New Progressive Party (Puerto Rico), etc.; class = character
* year: year in office; class = integer

## Scripts and code
*readxl: Used for reading in Excel files (.xlsx)
*tidyverse: Used for data wrangling
*dplyr: Used for data manipulation
*lubridate: Used for manipulating calendar dates
*ggplot2: Used for data visualization
*sf: Used for working with spatial dataframes
*mapview: Used for visualizing spatial data
*leaflet: Used for mapping spatial data
*zoo: Used for working with time series objects
*kendall:Used for computing the Kendall rank correlation and Mann-Kendall trend test
*tseries: Used for manipulating time series data


## Quality assurance/quality control
* Checked dimensions to ensure data was cut appropriately
* Graphed data to check for jumps or holes
* Checked for N/As to ensure no large sets of missing values
* Verified unique values and data structures using unique() and class()
