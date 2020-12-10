# Forecasting_Citywide_Crowd_Flows


This repository contains notebook files to experiment and validate the clustered LSTM model for forecasting citywide crowd flows in the city of Chicago.

The experiment was conducted using taxi historical records from January 1st 2015 to end of December 2016.  


The data comes from the Chicago Open data website located at:

https://data.cityofchicago.org/browse?category=Transportation

Note: Due to the size of the dataset (over 10 Gigabytes), it's preferable to download them and store them inside a folder outside of Git repository.


The road network for Chicago was extracted from https://overpass-turbo.eu/


The experiment is conducted in the following steps:

1 - Download the road network of Chicago, composed of the highways and primary streets only. Build a high resolution image of the road network.

2 - Perform dilation and thinning transformations on the images, to fuse various lanes from a single road segment into a single lane representing the road segment.

3 - Perform a segmentation to the image. Each segment corresponds to a semantic region. 

4 - Download the taxi trip records. Remove entries where a pickup or dropoff location information is missing. Create a time series with 1h time intervals.

5 - Map the taxi trips GPS coordinates (pickups and dropoffs) to the regions found at step 3.

6 - Create a Spearman's correlation matrix between pairs of regions, using the first 3 months from the time series. 

7 - Cluster the regions based on their Spearman's correlation values.

8 - Feed the clustered regions' time series to a LSTM model for forecasting taxi trips for each region.



