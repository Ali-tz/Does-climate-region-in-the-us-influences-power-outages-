# Does climate region in the us influences power outages ?
Using the dataset furnished in Data on major power outage events in the continental U.S. at the [adress](https://www.sciencedirect.com/science/article/pii/S2352340918307182), we will try to understand if major power outages are related to the climate region of the US.

## Introduction
> The dataset we are considering here describes various information about major outtage patterns, and characteristics of the states in the continental U.S , including their climate and topographical characteristics, electricity consumption patterns, population, and land-cover characteristics.
This data will be used to answer the following questoin : Are the major outtages distributed according to the climate of the region considered in the country.
The dataset contains 56 rows. We will look in particular at a few ones which are the YEAR, the MONTH, the CLIMATE.REGION, the CLIMATE.CATEGORY which states if it's warm, cold, or normal, the ANOMALY.LEVEL which states the el Nino level, the CAUSE.CATEGORY describing the category of the event causing the major power outages, the POPDEN_UC (persons per square mile) the population density of the urban clusters, the U.S._STATE, the DEMAND.LOSS.MW (Megawatt) describing the amount of peak demand lost during an outage event , CUSTOMERS.AFFECTED counting the number of customers affected by the power outage event, and OUTAGE.RESTORATION.TIME wich is the moment of outage restoration event.
.


## Cleaning and EDA
> At first the dataframe didn't even look like a dataframe, the columns didn't have any title, some columns were all null and then some values appearede in these columns.
-  We first found the columns title and put them at their right place and deleted the empty lines. 
- We normalize percentage columns to make it easier to read and indicate in the columns titles the different densities when needed.
- we merged the time columns that were redondant and created just one out of each.

```py
print(pow_outage[['YEAR', 'MONTH', 'OUTAGE.START.DATE (Day of the week, Month Day, Year)', 'OUTAGE.START.TIME (Hour:Minute:Second (AM / PM))', 'ANOMALY.LEVEL (numeric)', 'CAUSE.CATEGORY', 'POPDEN_UC (persons per square mile)', 'U.S._STATE', 'CLIMATE.REGION', 'CLIMATE.CATEGORY', 'CAUSE.CATEGORY', 'CUSTOMERS.AFFECTED', ]].head().to_markdown(index=False))
```

|   YEAR |   MONTH | OUTAGE.START        | OUTAGE.RESTORATION.TIME   |   ANOMALY.LEVEL (numeric) | CAUSE.CATEGORY     |   POPDEN_UC (persons per square mile) | U.S._STATE   | CLIMATE.REGION     | CLIMATE.CATEGORY   | CAUSE.CATEGORY     |   CUSTOMERS.AFFECTED |
|-------:|--------:|:--------------------|:--------------------------|--------------------------:|:-------------------|--------------------------------------:|:-------------|:-------------------|:-------------------|:-------------------|---------------------:|
|   2011 |       7 | 2011-07-01 17:00:00 | 2011-07-03 20:00:00       |                      -0.3 | severe weather     |                                1700.5 | Minnesota    | East North Central | normal             | severe weather     |                70000 |
|   2014 |       5 | 2014-05-11 18:38:00 | 2014-05-11 18:39:00       |                      -0.1 | intentional attack |                                1700.5 | Minnesota    | East North Central | normal             | intentional attack |                  nan |
|   2010 |      10 | 2010-10-26 20:00:00 | 2010-10-28 22:00:00       |                      -1.5 | severe weather     |                                1700.5 | Minnesota    | East North Central | cold               | severe weather     |                70000 |
|   2012 |       6 | 2012-06-19 04:30:00 | 2012-06-20 23:00:00       |                      -0.1 | severe weather     |                                1700.5 | Minnesota    | East North Central | normal             | severe weather     |                68200 |
|   2015 |       7 | 2015-07-18 02:00:00 | 2015-07-19 07:00:00       |                       1.2 | severe weather     |                                1700.5 | Minnesota    | East North Central | warm               | severe weather     |               250000 |


### Univariate Analysis

<iframe src="assets/Cause category count.html" width=800 height=600 frameBorder=0></iframe>

### Bivariate Analysis

<iframe src="assets/Anomaly level per month.html" width=800 height=600 frameBorder=0></iframe>
<iframe src="assets/Mean Anomaly level per U.S State.html" width=800 height=600 frameBorder=0></iframe>

### Interesting Aggregates

"|   ('ANOMALY.LEVEL (numeric)', 'equipment failure') |   ('ANOMALY.LEVEL (numeric)', 'fuel supply emergency') |   ('ANOMALY.LEVEL (numeric)', 'intentional attack') |   ('ANOMALY.LEVEL (numeric)', 'islanding') |   ('ANOMALY.LEVEL (numeric)', 'public appeal') |   ('ANOMALY.LEVEL (numeric)', 'severe weather') |   ('ANOMALY.LEVEL (numeric)', 'system operability disruption') |   ('DEMAND.LOSS.MW (Megawatt)', 'equipment failure') |   ('DEMAND.LOSS.MW (Megawatt)', 'fuel supply emergency') |   ('DEMAND.LOSS.MW (Megawatt)', 'intentional attack') |   ('DEMAND.LOSS.MW (Megawatt)', 'islanding') |   ('DEMAND.LOSS.MW (Megawatt)', 'public appeal') |   ('DEMAND.LOSS.MW (Megawatt)', 'severe weather') |   ('DEMAND.LOSS.MW (Megawatt)', 'system operability disruption') |\n|---------------------------------------------------:|-------------------------------------------------------:|----------------------------------------------------:|-------------------------------------------:|-----------------------------------------------:|------------------------------------------------:|---------------------------------------------------------------:|-----------------------------------------------------:|---------------------------------------------------------:|------------------------------------------------------:|---------------------------------------------:|-------------------------------------------------:|--------------------------------------------------:|-----------------------------------------------------------------:|\n|                                         -0.878947  |                                              -0.831579 |                                           -0.740984 |                                  -1.06667  |                                      -0.809091 |                                       -0.791213 |                                                      -0.913514 |                                              483.286 |                                                  743.636 |                                              0.537037 |                                      25.4667 |                                          61.6667 |                                           543.752 |                                                          600.029 |\n|                                         -0.0857143 |                                              -0.15     |                                           -0.209735 |                                  -0.2      |                                      -0.120588 |                                       -0.070904 |                                                      -0.174576 |                                              352.5   |                                                  393     |                                             16.3372   |                                    1190.08   |                                         560.25   |                                           612.185 |                                                         1387.86  |\n|                                          0.7       |                                               1.28     |                                            1.33857  |                                   0.914286 |                                       0.9      |                                        1.00783  |                                                       0.986667 |                                              352.143 |                                                  165.2   |                                              5.75556  |                                      66.9167 |                                       41788      |                                           733.281 |                                                          317.65  |"







