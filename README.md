# Franchise-Decision-to-Invest-in-Prominent-Location
Franchise Decision to Invest in Prominent Location

## Comparison of Neighbourhoods of Cairo, Chicago and Sheffield




## Introduction
The problem I am considering is to compare the neighborhoods of three cities in three different countries. The cities I have selected are Cairo in Egypt, Chicago in USA and Sheffield in England, the reasons of select Cairo is to deal with data around us, Chicago and Sheffield due to the pictures below, Attempt will be made to check which neighborhoods of the 3 cities are similar.
The target audience for this project is the owners of a restaurant chain which might already have their franchises set up in Cairo and who want to enter new markets in Europe. They might consider other prominent tech cities in Europe since their target customer is the tech community. Since Chicago and Sheffield have many MNCs and have a large tech community, they are the target of this project.

## Data Sources
The neighborhood data of the four cities is taken from Wikipedia pages. 

https://en.wikipedia.org/wiki/Category:Districts_of_Cairo

https://en.wikipedia.org/wiki/List_of_neighborhoods_in_Chicago

https://en.wikipedia.org/wiki/Category:Suburbs_of_Sheffield

Beautiful Soup library will be used to web-scrap from the Wikipedia pages. The geocode library to be used is geopy. Care is taken to limit the calls to be less than 1call/sec to meet the term of use of the library. Folium library will be used to represent the data on maps. And scikit-learn will be used to utilize machine learning. And Foursquare API will be used to gather neighborhood data.
Cairo has 34 neighborhoods, Chicago has 247 neighborhoods and Sheffield has 59 neighborhoods
Note that Cairo has more neighborhoods than which exists in Wikipedia, but we assume those are the whole neighborhoods as a Wikipedia reference.

## Importing Data
Importing data is divided into 3 stages. The first stage is getting list of neighbourhoods of the four cities from the above Wikipedia links. The second stage is getting location of neighbourhoods. The final stage is getting the venues in the neighbourhoods from Foursquare.
Neighbourhood lists of Cities
We already have the links of the Wikipedia pages from which we can get the list of neighbourhoods in each city. Beautiful Soup library is used to extract the information from the wikitables in the pages. This data is stored in a pandas dataframe. Along with the neighbourhoods, the city name, the state name and the country name are stored.
Geolocation of the Neighbourhoods
The geopy library is used to get the location data of the Neighbourhoods. Now in geopy library, Nominatim service is used. For using the free service of Nominatim, there is a restriction of 1call per sec to the service. To avoid ‘timeout’ error, there needs to be at least 1 sec gap in each call even if a for loop is used. To provide a sufficient gap to accommodate network delay, a gap of 2 sec is provided. The gap is provided by calling the sleep function.
Timeout Errors
Even after providing a 2 sec gap in calls, there are timeout errors. So, to handle these errors is simple. Simply call the Nominatim service again for these locations after checking for network connectivity.
Missing/No Coordinates
Some locations will not resolve into coordinates. This can happen because some locations may have different spellings. These can be rectified by using different spellings. Some locations will not resolve despite that. Then that data is procured manually searching on Google Maps.

## Complete Clustering Results
The complete clustering gives some interesting results. The most common cluster between the 3 cities is cluster 4,  
The big takeaway from this is that there are three clusters with Neighbourhoods from all the locations (0,1,3,4,6). So, these Neighbourhoods can be considered similar based on the venues present in them.


## Discussion
The objective of this analysis was that if there is a restaurant franchise in Cairo and we want to open a new franchise in Chicago and Sheffield then in which Neighbourhoods of the cities they should open. Based on Complete Clustering Neighbourhoods in clusters 0,1,3 and 6 are similar Neighbourhoods. So, if the restaurant in the Neighbourhoods of these clusters in Chicago and Sheffield then a new franchise can be opened in the Neighbourhoods of the same clusters in Cairo. Since majority of the Neighbourhoods of all the locations are in these three clusters then there is a good probability of finding a match.
## Conclusion
The result showed that the restaurant franchise can be opened in Chicago and Sheffield in places which in cluster 0, 1, 3 and 6, though more data and analysis is needed. More data like the customer rating and pricing details will help but with the free Foursquare API there is limited access to the required data. 

