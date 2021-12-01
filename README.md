# Analyzing and Predicting Wildfires in Colorado's US Forests

![Cover](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/cover.PNG)

## PURPOSE
The purpose of this project is to demonstrate a high level of proficiency at the graduate school level in core data science and GIS principles and applications using Python and ArcGIS Pro.

The project explores if wildfires can be predicted in US Forests in Colorado using a RandomForest classifier.

## BACKGROUND
Colorado technically has 9 National Forests. However, Carson National Forest lies almost entirely outside of the state, just touching southern Colorado, and has been excluded from this project. A custom dataset was built from raw political, geological, biological and meteorological [geospatial]data between 2016 and 2021 to inform, or train, the RandomForest Calssifier model, in order to predict the number of fires in each forest for that 5-year period of record. Such a short period of record was necessary given the time constraints of this project and the amount of work required to collect and process hundreds of geospatial data (e.g., rasters) files in ArcGIS. Ideally, a 30 year record, corresponding to meteorological "climate normals", would have been used to inform the model. 

Fires have steadily been on the rise in Colorado. 

![Fire Trends](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_trend_plot.png)

This project will focus on fires from 2016 to 2020 in Colorado's US Forests only.

![Colorado Forests](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/forests_overview.png)

![Number of Fires](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/num_fires_plot.png)

![Acres Burned](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/acres_burned_plot.png)

Here's a final look at the number of fires binned by years across all 8 forests.

![All fires, All Years (Number)](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/allfires_num_byyear.png)

![All fires, All Years (Total Acres)](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/allfires_acres_byyear.PNG)   

A Jupyter Notebook (.ipynb) file is included with Python code, as well as a GIS_SUPPLEMENT.doc file, which shows some (but not all) of the steps taken to acquire and manipulate the geospatial data used in this project. In addition, numerous maps, graphs, tables and charts have been created, using both ArcGIS and Python, to best visualize and understand the data.

## ABOUT THE DATA

These geospatial data were collected, cleaned, processed and staged for analytics and machine learning using ArcGIS and Python. The resulting data set is unique. To my knowledge, no such data set exists for the exact boundaries of each forest.

*Data derived from the National Fire Interagency Center:*

- Fire freqeuncy
- Fire location
- Fire date (year)

*Data derived from 1/3 arc-length USGS Digital Elevation Models:*

- Max, min, mean elevation for each forest
- Max, mean slope

*Data derived from 2001 and 2019 National Land Cover Datasets:*

- Percent forested land (2019)
- Percent change in forested land (2001-2019)
- Percent change in barren land (2001-2019)
- Percent change in scrub brush land (2001-2019)

*Data derived from NOAA National Center for Environmental Information's climate data archives:*

- Avgerage end-of-winter snowpack
- Annual temperature anomalies
- Annual precipitation anomalies

*Data derived from the US Drought Monitor:*

- Annual max drought categories

## ANALYSIS

Analysis starts with exploratory data analysis in order to understand fire behavior in each forest, year-over-year.

*Visuals*

Here is bar plot looking at the number of fires occurring each year in each forest.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fires_byforest_byyear_barplot.PNG)
 
And here are two maps showing a general overview of fires from 2016-2020.

This first map shows the Arapaho and Roosevelt and Pike and San Isabel National Forests have had the most fires and represent the largest percentage of all fires, in all forests.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview.png)

This second map shows the total acreage burned in each forest, compared to the total acreage of each forest. Many of the forests have suffered significant loss. Note: The number of fires has been exaggerated/enlarged on the map for display purposes.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/fire_overview2.png)

The percent of each forest that has burned can be compared this way, too.
 
![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/per_burned.png)

*Building the master dataframe for machine learning*

The final data frame has all 8 forests broken down by year (2016-2020) for a total of 40 input rows into the model. Again, yes, this is a small sample, but given the large number of training attributes, it remained possible they might offset any model degradation from a small sample size. 

The data were also scaled or normalized using sklearn.preprocessing's StandardScaler method in Python, then split into test and training datasets.

## THE MODEL

A random forest classifier was chosen given its simplicity and typically superior performance other machine learning algorithms, like descision trees and linear regressions.

The model was run twice. The first time it was run with the predictand being the number of fires. This yielded a low accuracy. So, in order to improve the model output I binned the number of fires into 4 numerical categories. Rerunning the model this way returned an accuracy of 50% but looking at features of importance still failed to outmatch random number generation. In other words, the model was really good at guessing (since there were only 4 choices now) but overall still had very low skill.

![Model results](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/model_plot4.PNG)

Finally, a third model was run, this time a random forest regression. The mean absolute error was very high in this case since really the number of fires should be treated as categories. 

Additional inspection of the data gave some insight into why model performance was so poor. There were weak relationships between the training variables and the number of fires (predictand). I think the relationships were so weak because yes, these variables inform whether a fire is likely, but not necessarily the frequency of fires each year. Sure, drier and warmer years, with less winter snowpack, can produce more fires, but the relationship is much more ambiguous than if I was just trying to predict a fire, yes or no, based on those same variables. So I think trying to predict the number of fires for the period of record I chose was doomed right out of the gate. Also, there was a large amount of multicollinearity among the variables, meaning the variables had some relation to each other, as well as the predictand. As a result, the model could not distinguish the proper weights each variable has on the predictand.


## CONCLUSION 

The project shows unique approaches to building, analayzing and exporting custom data sets from raw geospatial data in ArcGIS.

The model demonstrates a capacity to try and predict forest fires given a variety of political, meteorological, geological and biological geospatial data that have some perceived influence on forest fires. However, the model fails to return a result that could benefit fire predictions. The model needs more data to inform itself that has a stronger relationship to the number of fires. I was suprised variables like drought, temperature and precipitation did not seem to have a stronger relationship to the frequency of fires. Binning the number of fires into four categories to be predicted instead of the number (integer) of fires improved the model results.

Upon reflection the model output should be binary, and a logistic regression would have been more appropriate, where 0 = "No fire" and 1 = "Fire". However, running my data through that type of model wouldn’t make a whole lot of sense since there were fires every year from 2016-2020 and my data were stagged annually. So, the best I can predict is yes or no a fire is likely in a given year, forests aside, which isn't very useful information in my opinion. A binary prediction could have been possible if my data were on a daily or weekly timescale. Unfortunately, the meteorological geospatial data is not produced on such a small timescale and whole new approach would be required to develop those datasets. 

While the model may not be ready for prime time, the data exploration alone has given useful insight into fire behavior in CO US forests over the last 5 years. Of note, the largest fires in Colorado history have been within the last 5 years.

![alt text](https://github.com/sunnysidedenver/regis_msds_practicum2/blob/main/largest_fires.png)

## FUTURE EFFORTS

I believe a larger data set is needed with at least 30 years of data. I think binning the number of fires will continue to improve the model accuracy, since you are giving the model some leeway with a range of fires within that bin. Also, decision makers aren't that interested in the precise number of fires, but rather, if there is going to be a little or a lot of fire activity in the upcoming season, and how big they might get. It is highly unlikely a model like this would ever precicsely capture the number of fires anyway given the weak relationship to fire frequency, which was already discussed. Also, there's just too much uncertainty in fire ignition. More (and better) predictor variables are also needed. 

If this model then can outperform a random guess with a high degree of accuracy, seperate predictions could be run for each forest. Also, one could try and predict how many acres could burn in an upcoming season, in addition to the total number of fires.

Or daily, weekly or perhaps monthly meteorological data could be collected and processed to train a logistic regression model to determine if a fire is likley in a specific forest over a determined period of time. Compiling the data on this timescale will ensure a more robust sample size.







