# Analyzing and Predicting Wildfires in Colorado's US Forests

## PURPOSE
The purpose of this project is to demonstrate proficiency in core data science/machine learning and geographic information systems (GIS) principles and skills at the graduate school level. The project heavily uses Python, an open-source programming language, along with select Python libraries, and ArcGIS Pro, a ubiqitious GIS software platform. 

The project explores if wildfires can be predicted in US Forests in Colorado using machine learning (RandomForest classification).

A Jupyter Notebook (.ipynb) file is included with Python code, as well as a GIS_SUPPLEMENT.doc file, which demonstrates some (but not all) of the steps taken to acquire and manipulate the geospatial data used in this project. In addition, numerous maps, graphs, tables and charts have been created, using both ArcGIS and Python, to best visualize and understand the data.

## BACKGROUND
Colorado technically has 9 National Forests. However, Carson National Forest lies almost entirely outside of the state, just touching southern Colorado, and has been excluded from this project. A custom built dataset was built from raw geological and meteorological data between 2016 and 2021 to inform, or train, the RandomForest model, in order to predict the number of fires in each forest for that 5-year period of record. Such a short period of record was necessary given the time constraints of this project and the amount of work required to pre-process the geospatial data (rasters) in ArcGIS. Ideally, a 30 year record, corresponding to meteorological normal data, would have been used to inform the model. 

Here is bar plot looking at the number of fires occurring each year in each forest.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fires_byforest_byyear_barplot.PNG)

And here are two maps showing a general overview of fires from 2016-2020.

This first map shows the Arapaho and Roosevelt and Pike and San Isabel National Forest have had the most fires and represent the largest percentage of all fires, in all forests.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview.png)

This second map shows the total acreage burned in each forest, compared to the total acreage of each forest. Many of the forests have suffered significant loss.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview2.png)

This percent of each forest can be visualized another way.
 
![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/per_burned.png)

Finally, looking at all fires, all forests, summed up across the 5-year period. 

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/totalfires_byforest_plot.PNG)






