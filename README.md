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
