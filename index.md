---
title       : Developing Data Products Project
subtitle    : Predicting MPG of a Vehicle
author      : Sarada Bhasker
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Application Details

This demo application helps predict the MPG of a vehicle. The prediction algorithm uses the glm train method  available in caret package. The data for prediction algorithm comes from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973-74 models) 


The following features of a vehicle are used to predict the MPG

1. The tranmission type (Automatic or Manual)
2. Number of Cylinders
3. Weight of Car
4. HP of Car

--- .class #id 

## Implementation

The application is implemented using shiny framework and is deployed on shinyapps server on Rstudio. The application can be accessed on the following link
https://dataproductproject.shinyapps.io/Project/


```r
library(caret)
data(mtcars)
head(mtcars, n=1)
```

```
##           mpg cyl disp  hp drat   wt  qsec vs am gear carb
## Mazda RX4  21   6  160 110  3.9 2.62 16.46  0  1    4    4
```

The prediction algorithm has been implemented using glm model. 


---  . 
## Regression model 

```r
library(caret)
data(mtcars)
modFit <- train(mpg~factor(am)+factor(cyl)+wt+hp, data= mtcars, method="glm")
mt1 <- subset(mtcars, select=-c(mpg))
yhat <- predict(modFit, mt1)
```
## Prediction Function

```r
predictMileage <- function(am1, cyl1, wt1, hp1){
p1 <- predict(modFit, newdata=data.frame(am=am1, cyl=cyl1, wt=wt1, hp=hp1))
 }
```
The values that user enters are passed to the predictMileage Function to get the prediction for mpg  

---  . 
## Plot to show accuracy
The plot below shows the prediction accuracy of the application.
![plot of chunk mod4](assets/fig/mod4-1.png) 
---






