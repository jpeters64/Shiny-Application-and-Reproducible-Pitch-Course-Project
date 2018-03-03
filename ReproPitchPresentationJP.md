
Vehicle Braking Distance Prediction Shiny Application
========================================================
author: Jeremy Peters
date: March 3, 2018
autosize: true

Overview
========================================================
Braking Distance Prediction Application Overview

The analysis of the relationship between vehicle speed and braking distance can impact the lives of individuals in regard to changes in speeding laws and car design

This 'Shiny' web application predicts the vehicle stopping distance based on the vehicle speed as specified by the user

Cars dataset, containing fifty speed and stopping distance observations from the 1920s, from the r datasets package, is used to train a simple linear regression model

This presentation contains documentation for the 'Shiny' web application found here:[Shiny App] (https://je94pe98.shinyapps.io/VehicleBrakingDistancePredictionShinyApplication)


The Shiny server.R and ui.R application code and Rstudio Presenter code can be found on github here:[GitHub repo](https://github.com/jpeters64/Shiny-Application-and-Reproducible-Pitch-Course-Project)


Cars Dataset
========================================================
Cars dataset from the r datasets package gives the speed of cars and the distances taken to stop recorded in the 1920s

The dataset has 50 observations and two variables:

1. speed	numeric	Speed (mph)

2. dist	numeric	Stopping distance (ft)


```
'data.frame':	50 obs. of  2 variables:
 $ speed: num  4 4 7 7 8 9 10 10 10 11 ...
 $ dist : num  2 10 4 22 16 10 18 26 34 17 ...
```

```
     speed           dist       
 Min.   : 4.0   Min.   :  2.00  
 1st Qu.:12.0   1st Qu.: 26.00  
 Median :15.0   Median : 36.00  
 Mean   :15.4   Mean   : 42.98  
 3rd Qu.:19.0   3rd Qu.: 56.00  
 Max.   :25.0   Max.   :120.00  
```

Application User Interface
========================================================
User selects vehicle speed

Predicted Stopping Distance  displayed

Scatterplot of Car Stopping Distance vs Speed and Regression Line is displayed

![Main screenshot](ShinyUserInterface.png)

Regression Model
========================================================
Run simple linear regression model

modfit <- lm(data = cars, dist ~ speed)

Predict the stopping distance

modpred <- predict(modfit, newdata = data.frame(speed = input$mph))
