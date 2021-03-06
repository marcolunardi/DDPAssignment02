---
title       : MT Cars Dataset Exploratory Analysis
subtitle    : Coursera Developing Data Products - Pitch Presentation Assignment
author      : Marco Lunardi  -  Please use arrow keys on your keyboard to move through slides, thank you !
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- {bg: LightYellow}

## The MTCars Dataset

The MTCars Dataset is available into the "datasets" package in R.

At the R console prompt you can type "library(datasets)", and then "? mtcars" to see a brief description about it.

This dataset gathers data about 32 cars from a 1974 issue of Motor Trend Magazine (quite old data actually), showing values for 11 variables.

The main aim of the dataset is to analyze the influence on the efficiency of cars by some relevant variables (weight, transmission, engine size, acceleration, ...),
and in particular which type of transmission (manual or automatic) was the best in terms of fuel saving.

The measure adopted to evaluate the cars efficiency is MPG (= Miles per US Gallon).

So, the more efficient cars have a higher MPG and then lower fuel consumption.


--- {bg: LightYellow}

## My Shiny App

You can run the app at: https://marcolunardi.shinyapps.io/DDP01APP

My App is designed to perform a very basic exploratory analysis on mtcars data, in order to get a first view
about the interactions among the most relevant variables within the mtcars dataset.

On the upper left side of the app page you can set the values for the engine size, through the cylinders number (from 4 to 8), and for the transmission type: manual or automatic.
Once you chose these two values, the app dynamically changes the content on the right side of the app page:
it changes the content of the title reflecting your choices, it computes the average weight and MPG for the cars corresponding to your criteria, and it draws a scatterplot of the cars you selected through your settings (red dots if "manual transmission", black dots if "automatic").

The following slide computes the averages of weights and MPGs for all the cars in the dataset, and the fifth and last slide uses R code to plot the same scatterplot shown in the app, but this time containing all cars within the dataset. You can then compare the results from the app to these plot and values to draw your first basic conclusions about mtcars data.

--- {bg: LightYellow}

## Weight and MPG averages for all cars in the dataset



Weights average (lbs/1000):

```r
mean(mtcars$wt)
```

```
## [1] 3.21725
```

MPGs (Miles per US Gallon) average:

```r
mean(mtcars$mpg)
```

```
## [1] 20.09062
```

--- .codefont

## Scatterplot for all cars within the mtcars dataset


```r
mpgmean<-mean(mtcars$mpg); wtmean<-mean(mtcars$wt); mtcars$am<-as.factor(mtcars$am)
plot(mtcars$wt, mtcars$mpg, col=mtcars$am, xlim=c(1,6), ylim=c(10,40), 
     ylab="MPG = Miles per Gallon", xlab="Weight (lbs/1000)", cex.main=1,
     main="MPG by Weight; Orange Lines =  mean weight and MPG for all cars", pch=16, cex=2)
abline(h = mpgmean, col="orange", lwd=4); abline(v = wtmean, col="orange", lwd=4)
```

![plot of chunk unnamed-chunk-4](assets/fig/unnamed-chunk-4-1.png) 
