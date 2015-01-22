---
title       : MT Cars Dataset Exploratory Analysis
subtitle    : Coursera Developling Data Products Pitch Presentation Assignment
author      : Marco Lunardi
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## 2: The MTCars Dataset

1. It's available into the "datasets" package in R
2. At the R console prompt, type "library(datasets)" and then "? mtcars" to know more about it
3. It gathers data about 32 cars from 1974
4. Its main aim is to know which variable has the bigger influence on fuel consumption (MPG)

--- .class #id 

## 3: My Shiny App

1. My App is designed to perform a very basic exploratory analysis on mtcars data
2. You can choose the cylinders number and the transmission type

---

## 4: Graph with all cars in the dataset




```r
data <- mtcars
data$am <- sub(0, "Automatic", data$am)
data$am <- sub(1, "Manual", data$am)
data$am <- as.factor(data$am)
mpgmean <- mean(data$mpg)
wtmean <- mean(data$wt)
plot(cars$wt, cars$mpg, col=cars$am, xlim=c(1,6), ylim=c(10,40), 
     ylab="MPG = Miles per Gallon", xlab="Weight (lbs/1000)", cex.main=1,
     main="MPG by Weight; Orange Lines =  mean weight and MPG for all cars",
     pch=16, cex=3)
abline(h = mpgmean, col="orange", lwd=4)
abline(v = wtmean, col="orange", lwd=4)
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 
