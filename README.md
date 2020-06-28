# Coursera Capstone: Analyzing New York ATM data
---
## Introduction/Business Problem
As a newcomer in finance industry, I want to deploy new **ATM infrastructures** inside **NY state**.

I'm looking for places where people are likely to withdraw money AND looking for places where people don't have yet any other good option to do so. 

- Using data science, I want to analyze ATM data, understand **where the needs are**. 
- I  want to understand **how my competitors thinks about it**. 
- And given that, I want to find **where to deploy** my new pounds in order to bring the most value out of it.
---
## Data

### NY state base map and county boundaries

I use this geojson file a base for most of my maps.
Contains the 62 counties of New York State and their spatial extents

https://raw.githubusercontent.com/codeforamerica/click_that_hood/master/public/data/new-york-counties.geojson

### A list of all bank owned or in-bank ATMs located in New York State.

This dataset is provide by Department of Financial Services and publicly available on

https://data.ny.gov/Government-Finance/Bank-Owned-ATM-Locations-in-New-York-State/ndex-ad5r

This dataset is well documented on their webside, including summary and limitations.


### Population in NY state

Population for each counties in New York

https://www.newyork-demographics.com/counties_by_population

### Wealth data

Wealth data for each counties in New York

https://en.wikipedia.org/wiki/List_of_New_York_locations_by_per_capita_income

I will use median houshold income for every county.


### Location surrounding data

I will use the explore API endpoint to retrieve informations about venues in the surrounding of ATM locations.

I will also use the category API endpoint, to get a complete list of their categories.

foursquare API: https://api.foursquare.com/

---

## Methodology 

I try to understand where ATMs are located and in the state of New York and the reasons that drive the choice for their location. 
The dataset containing the list of all ATMs is the most important one for that project.

There is two main axis I will follow when analysing those ATM data:
1) per county
2) per institution

#### County analysis
In this first part, analye per county, efforts will be put in enriching that dataset with additionnal informations.
We will use various visualization technique as well as linear regression in order to get the most value out of this ATM dataset.
Some questions I would like to answer during the course of my analysis are:
- Do we find more ATM in large counties than small ?
- How many ATM are present in each counties ?
- Where should I plan to install a new one ?


#### Institution analysis
Second part of the analysis. I want to discover patterns in data that are specific to an institution. As a newcomer in finance industry, those institutions are my competitors. If I can understand the strategies that competitors are using, this will give us a great competitive avantage for the future.

We will try understand how they come up with a new location, what are the factors that drives the choice of a new ATM location. 
Some questions I would like to answer during the course of my analysis are:
- Does institution-A place ATM location systematically close to restaurant ?
- May be instituion-B ATMs are always placed close transportation service ?

We will use foursquare API to gather data about suroundings, then apply clustering on venues and categories. 
## Results
We've combined ATM data with geodata to visualize the repartition of ATM.
This allowed us to identify that ATM are not distributed uniformely inside the state of New York.
Nassau County and New York County have large number of ATM and small surface area.
By introducing another dataset and population information per county we identify a mostly linear relation between the population and number of ATM per county. 
We introduce one more dataset to investigate the relation between wealth and ATM density but that was a rather unsuccesful exploration.
During the second step of this analysis (per institution), we've gathered surrounding information for a sample of our ATM dataset. We apply dimensionnality reduction by recategorizing venues using parent category.
We've found that most ATMs are surrounded mainly by Food and Shopping store, but could find any pattern that would be specific to one institution.
## Discussion

One big limitation comes from the ATM dataset itself:  ATM locations listed refer to bank owned ATM. Non-bank ATMs are not included. 
I would need to collect more data and analyze more potential features, such as crimes, cashless habits, ... 
It would be really nice to also have ATM dataset that includes performance metrics such as transactions per day or amount per day. Those are probably not public, so it may be safe to assume that long-time underperforming ATMs have been dismantled

## Conclusion
To improve that project I would fully focus on getting better data. A simple algorithm with good data out performs a complex one with bad data. But in practice good data might not be available.


