---
title       : Bird distribution data from eBird.
subtitle    : A Shiny app for migrating birds observations across the US, using data from Ebird.
author      : This presentation was created with Slidify by fss14142@gmail.com
date:         November 2014.
job         : A project for the Johns Hopkins Coursera Developing Data Products Course.
framework   : io2012
highlighter : highlight.js  
hitheme     : tomorrow       
url:
    lib: ../../librariesNew #Remove new if using old slidify
    assets: ../../assets
widgets     : [mathjax, quiz, bootstrap]
mode        : selfcontained # {standalone, draft}
ext_widgets : {rCharts: ["libraries/highcharts","libraries/nvd3", "libraries/morris", "libraries/leaflet", "libraries/rickshaw"]}
---

## Bird populations data using the eBird API.

You can see the Shiny app at [https://fss14142.shinyapps.io/test01/](https://fss14142.shinyapps.io/test01/).

1. In 2002 the [Cornell Lab of Ornithology](http://birds.cornell.edu/) created [eBird](http://ebird.org/), an online database which provides information about bird species populations. The data is provided by thousands of birders (not just in the US, but in many other countries as well) using an easy web interface. The eBird services include an [API](https://confluence.cornell.edu/display/CLOISAPI/eBirdAPIs) which I have used for this project. 

2. The eBird API can be used to obtain information about thousands of bird species, across many countries. However, for the course puroposes, I have decided to limit the application to the analysis of data about a few (four) relevant and well known migratory species in the United States (Snow Goose, Sandhill Crane, Common Goldeneye and Mallard).

3. The goal of my Shiny app is to showcase the use of R and Shiny to programatically access and analyze the eBird data. It is a simple proof-of-concept app, but it can be easily extended for improved functionality.

--- .codefont

## Getting the data from the eBird API.

The eBird API provides updated data in JSON or XML format (or even csv files for some queries).  In my Shiny application the `jsonlite` library connects to the API and converts the data into an R data frame. For example a query for *Snow Geese* observations in the state of Arkansas during the last 7 days gives a result like this (only the first two records are partially shown):


```
##      comName howMany   lat    lng    locID                                           locName locationPrivate
## 1 Snow Goose   30000 35.67 -90.79 L2503204                       Senteney Rd. (Poinsett Co.)           FALSE
## 2 Snow Goose     300 34.55 -92.62  L283622 Cherry Gingles/Saline River at Benton/Sunset Lake            TRUE
## 3 Snow Goose     350 34.98 -90.95 L3172815                                              I 40            TRUE
## 4 Snow Goose       1 35.14 -92.45  L365158                                   Beaverfork Lake           FALSE
```

For further details on the eBird API check  [https://confluence.cornell.edu/display/CLOISAPI/eBirdAPIs](https://confluence.cornell.edu/display/CLOISAPI/eBirdAPIs). 


--- .outfont

## Showing the data for a state in a map.

I have used Leaflet (via RChart) to plot the resulting data in an interactive map. For example, let me use Snow geese observations for the last week in the State of Arkansas, at the time when this slidify document was last compiled (2014-11-23 17:50:34 CET). In the map included in this slide you can zoom in /out, pan or click any of the popups to see the associated information for that observation (site name, coordinates, number of birds, date). 

The original application uses the interactivity provided by Shiny to give the user the choice of state, bird species and the number of days to display in the map (in this online Slidify presentation that functionality is not included). 


<iframe src="fig/stateMap.html"  height=400></iframe>


---

## Conclusions and References.

The GitHub repository for the application, containing the code, documentation and references can be found at [https://github.com/fss14142/DevelopingDataProductsProject](https://github.com/fss14142/DevelopingDataProductsProject).

* The eBird data can be easily accessed using R and dinamically visualized using Shiny and RCharts.  

* The functionality in this application can be improved by adding further eBird API calls and more advanced Shiny controls. For example including an animated plot of bird observations along several days could help illustrate bird migration.

* The eBird API provides a wealth of bird information. However, the ability to select and customize the information is very interesting. Imagine, for example, a hotel in a birding hotspot, that wishes to include in their webpage the latest observations in the surrounding area... there are many such possibilities for an application like this.


Thank you.

