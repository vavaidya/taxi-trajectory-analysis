# taxi-trajectory-analysis
[Link to Kaggle dataset](https://www.kaggle.com/crailtap/taxi-trajectory)
[Taxi Img](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Taxi_Img.jpg)

## INTRODUCTION
Uber for a while made its way in the legal grey areas of Portugal. Until only recently in 2019 did Uber begin legal operations in the city of Porto. But was this the first that the city had interacted with cabs? In 2013-14 alone a small fleet of 442 taxi's in Porto, Portugal made 1.7 Million trips throughout the city. Could a data oriented approach back then have helped city planning and reduce taxi times in today's traffic ruled roads?

## PROBLEM TO EXPLORE
Although we can accurately talk about each ride duration based on the polyline feature that captures lat/long every 15 secs for each trip. However, at the point the taxi is hailed, we have only a rough estimate of areas it will travel through.
The real question is, how much of the duration can be predicted solely from the geographic information.(Independent of time of day, holidays)

## APPROACH AND CONCEPTS
The meat of the problem lies in how we set this up for analysis.
* Dividing the city of Porto into a rectangular grid of lat/long, using a large bin size (about 1 Million)
* Restricting our bin considerations to those that are frequently travelled - threshold of 30,000 taxis travelling the area in a year - reducing our considered bins to approximately 1000
* Creating binary variables for each of these bins, marking whether the route passed through them or not

## RESULTS
* Simple linear regression on these binary bins accounts for 61.3% of the variance in trip duration
* Coefficients of this regression can be used to identify areas of the city that are most likely to add to trip duration - important metric for city planning to create overhead bridges, speed lanes, underpasses etc.

## LEARNINGS
* On trying different computation heavy models like Random Forest, gradient boosting the linear regression actually outperformed in terms of R-squared and was computationally way cheaper.
* Also, the ease of interpretibility of the regression coefficients in a set up like this was priceless

## REPOSITORY DETAILS
[Taxi Route Read](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Taxi%20Route%20Read.ipynb) - this file process the original CSV file and writes a pandas dataframe into a pickle file. 

[Starting with Pickle](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Starting%20With%20Pickle.ipynb) - this file bins our coordinate data for use in a predictive model

[Binning](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Binning.ipynb) - predictive model used to determine geographic areas prone to cause high duration taxi rides

[Heatmaps](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Heatmaps_vav.ipynb) - interactive heatmap of routes stratified by different features

[Taxis LF](https://github.com/vavaidya/taxi-trajectory-analysis/blob/master/Taxis_LF.ipynb) - interactive map of taxi routes
