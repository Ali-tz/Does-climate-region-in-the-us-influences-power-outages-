# Does climate region in the us influences power outages ?
Using the dataset furnished in Data on major power outage events in the continental U.S. at the [adress](https://www.sciencedirect.com/science/article/pii/S2352340918307182), we will try to understand if major power outages are related to the climate region of the US.

## Introduction
> The dataset we are considering here describes various information about major outtage patterns, and characteristics of the states in the continental U.S , including their climate and topographical characteristics, electricity consumption patterns, population, and land-cover characteristics.
This data will be used to answer the following questoin : Are the major outtages distributed according to the climate of the region considered in the country.
The dataset contains 56 rows. We will look in particular at a few ones which are the YEAR, the MONTH, the CLIMATE.REGION, the CLIMATE.CATEGORY which states if it's warm, cold, or normal, the ANOMALY.LEVEL which states the el Nino level, the CAUSE.CATEGORY describing the category of the event causing the major power outages, the POPDEN_UC (persons per square mile) the population density of the urban clusters, the U.S._STATE, the DEMAND.LOSS.MW (Megawatt) describing the amount of peak demand lost during an outage event , CUSTOMERS.AFFECTED counting the number of customers affected by the power outage event, and OUTAGE.RESTORATION.TIME wich is the moment of outage restoration event.
.


## Cleaning and EDA

> This raw dataset is not easy to read at this point, let's clean it up a little:
-  The first 4 lines represents the title in the excel file, we are only intersted by the fursished tab below. Moreover, we notice we don't have title for our columns because of that, looking depper the columns titles are at the line index 4. 
- The unit columns is useless, and the first line of the dataset is annoying for future manipulation, we will normalize proportions and for densities denote them in their respective column title. Numeric values will remain the same as the information of numeric seems to be quite obvious facing numbers.
- we have two columns for start time (date and time separately) and the same goes on for the restoration date, let's merge this two columns into a signle information.

We will denote this three steps as Cleaning step 1, Cleaning step 2, and Cleaning step 3.

