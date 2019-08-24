# HRace_Slides

title : Race Horse Prediction subtitle : Using linear regression to predict horse race outcomes author : Ian McCarthy  framework : io2012 # {io2012, html5slides, shower, dzslides, ...} highlighter : highlight.js # {highlight.js, prettify, highlight} hitheme : tomorrow # widgets : [] # {mathjax, quiz, bootstrap} mode : selfcontained # {standalone, draft} knit : slidify::knit2slides ---.class #id

Horse Racing Prediction Model

This is a simple model built using R and Slidify for predicting horse race outcomes using general regression.

The method used

Successful horse racing betters are able to 'read the form' of diferent horses and make predictions on how they will run against each another. In this application I have used a general linear regression model fitted to a data set of Australian horse racing events during 2013.

The model predicts how long it will take each horse to run a future race using the horse's last race performance and characteristics of the future race . The predicted times for each horse to complete the race enables a ranking of their finishing place to be predicted.

--- .class #id

The model's input variables

The input variables (delta of last race and future race) used in the regression model are as follows:

Race distance - the farther the race the longer it takes to finish.
The Going - how hard (faster) or soft (slower) a track is.
Weight - each horse carries a jockey and often a weight handicap
This is the general form of the R code for fitting the model and then predicting a horse's finish time:

prediction_model <- lm(finish_time ~ distance + weight + going, data = aust_races_2013)

predicted_time <- (prediction_model, data = horses_last_race)
The outcome of this is not shown.

--- .class #id

The effect of distance on average winning times

dist <- seq(1000, 2000, by=100)
time <- 0.070*dist
plot(dist, time, main="Average winning race times by distance", 
     xlab="Race Distance (m)", ylab="Time (s)", pch=19)
abline(lm(time~dist), col="red")
--- .class #id

The web app

I have created an online shinyapps model that can be viewed here: https://ianmccarthy.shinyapps.io/HorseRace/

The web app can make predictions for up to 5 horses, the race outcomes change as the data is changed.
