# Analyzing and Predicting Wildfires in Colorado's US Forests

## PURPOSE
The purpose of this project is to demonstrate proficiency in core data science (e.g., data collection and prep, exploratory data analysis and machine learning) and geographic information systems (GIS) principles and skills at the graduate school level. The project heavily uses Python, an open-source programming language, along with select Python libraries, and ArcGIS Pro, a ubiqitious GIS software platform. 

The project explores if wildfires can be predicted in US Forests in Colorado using machine learning (RandomForest classification).

## BACKGROUND
Colorado technically has 9 National Forests. However, Carson National Forest lies almost entirely outside of the state, just touching southern Colorado, and has been excluded from this project. A custom built dataset was built from raw geological and meteorological data between 2016 and 2021 to inform, or train, the RandomForest model, in order to predict the number of fires in each forest for that 5-year period of record. Such a short period of record was necessary given the time constraints of this project and the amount of work required to pre-process the geospatial data (rasters) in ArcGIS. Ideally, a 30 year record, corresponding to meteorological "climate normal data", would have been used to inform the model. 

A Jupyter Notebook (.ipynb) file is included with Python code, as well as a GIS_SUPPLEMENT.doc file, which demonstrates some (but not all) of the steps taken to acquire and manipulate the geospatial data used in this project. In addition, numerous maps, graphs, tables and charts have been created, using both ArcGIS and Python, to best visualize and understand the data.

## THE DATA

These geospatial data were collected, cleaned, processed and staged for analytics and machine learning using ArcGIS and Python. The resulting data set is unique. To my knowledge, no such data set exists for the exact boundaries of each forest.

*Data derived from the National Fire Interagency Center:*

- Fire freqeuncy
- Fire location
- Fire date (year)

*Data derived from 1/3 arc-length USGS Digital Elevation Models:*

- Max, min, mean elevation for each forest
- Max, mean slope

*Data derived from 2001 and 2019 National Land Cover Datasets:*

- Percent forested land
- 5-year percent change in forested land
- 5-year percent change in barren land
- 5-year percent change in scrub brush land

*Data derived from NOAA National Center for Environmental Information Climatological data:*

- Avgerage end-of-winter snowpack
- Annual temperature anomalies
- Annual precipitation anomalies

*Data derived from the US Drought Monitor:*

- Annual max drought categories

## ANALYSIS

Analysis starts with exploratory data analysis in order to understand fire behavior in each forest, year-over-year.

Here is bar plot looking at the number of fires occurring each year in each forest.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fires_byforest_byyear_barplot.PNG)

And here are two maps showing a general overview of fires from 2016-2020.

This first map shows the Arapaho and Roosevelt and Pike and San Isabel National Forest have had the most fires and represent the largest percentage of all fires, in all forests.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview.png)

This second map shows the total acreage burned in each forest, compared to the total acreage of each forest. Many of the forests have suffered significant loss.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview2.png)

The percent of each forest that has burned can be compared this way, too.
 
![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/per_burned.png)

Finally, looking at all fires, all forests, summed up across the 5-year period. Again, the Arapaho and Pike Forests have had the most fires.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/totalfires_byforest_plot.PNG)

## THE MODEL

## CONCLUSION

## FUTURE RESEARCH






