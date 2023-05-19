# Does climate region in the us influences power outages ?
Using the dataset furnished in Data on major power outage events in the continental U.S. at the [adress](https://www.sciencedirect.com/science/article/pii/S2352340918307182), we will try to understand if major power outages are related to the climate region of the US.

## Introduction

## Cleaning and EDA

> This raw dataset is not easy to read at this point, let's clean it up a little:
-  The first 4 lines represents the title in the excel file, we are only intersted by the fursished tab below. Moreover, we notice we don't have title for our columns because of that, looking depper the columns titles are at the line index 4. 
- The unit columns is useless, and the first line of the dataset is annoying for future manipulation, we will normalize proportions and for densities denote them in their respective column title. Numeric values will remain the same as the information of numeric seems to be quite obvious facing numbers.
- we have two columns for start time (date and time separately) and the same goes on for the restoration date, let's merge this two columns into a signle information.

We will denote this three steps as Cleaning step 1, Cleaning step 2, and Cleaning step 3.