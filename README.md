# Forecasting_Citywide_Crowd_Flows


This repository contains notebook files to experiment and validate the clustered LSTM model for forecasting citywide crowd flows in the city of Chicago.

The experiment was conducted using taxi historical records from January 1st 2015 to end of December 2016.  



The data comes from the Chicago Open data website located at:

https://data.cityofchicago.org/browse?category=Transportation


The road network for Chicago was extracted from https://overpass-turbo.eu/

#### Note: Due to the size of the dataset (over 10 Gigabytes), it's preferable to download them and store them inside a folder outside of Git repository.


# Work steps:

## The experiment is conducted in the following steps:

1 - Download the road network of Chicago, composed of the highways and primary streets only. Build a high resolution image of the road network.

2 - Perform dilation and thinning transformations on the images, to fuse various lanes from a single road segment into a single lane representing the road segment.

3 - Perform a segmentation to the image. Each segment corresponds to a semantic region. 

4 - Download the taxi trip records. Remove entries where a pickup or dropoff location information is missing. Create a time series with 1h time intervals.

5 - Map the taxi trips GPS coordinates (pickups and dropoffs) to the regions found at step 3.

6 - Create a Spearman's correlation matrix between pairs of regions, using the first 3 months from the time series. 

7 - Cluster the regions based on their Spearman's correlation values.

8 - Feed the clustered regions' time series to a LSTM model for forecasting taxi trips for each region.


# Bibliography:

This work is based on the following research papers:

[1] Thiago H Silva, Aline Carneiro Viana, Fabrício Benevenuto, Leandro Villas, Juliana Salles, Antonio Loureiro, and Daniele Quercia. Urban computing leveraging location-based social network data: a survey. ACM Computing Surveys (CSUR), 52(1):17, 2019. 

[2] Yu Zheng, Licia Capra, Ouri Wolfson, and Hai Yang. Urban computing: Concepts, methodologies, and applications. ACM Trans. Intell. Syst. Technol., 5(3):38:1–38:55, September 2014. 

[3] Minh X. Hoang, Yu Zheng, and Ambuj K. Singh. FCCF: Forecasting Citywide Crowd Flows Based on Big Data. Proceeding of the 24rd ACM International Conference on Advances in Geographical Information Systems (ACM SIGSPATIAL 2016), October 2016. Published by ACM SIGSPATIAL 2016

[4] Yu Zheng, Yanchi Liu, Jing Yuan, and Xing Xie. Urban Computing with Taxicabs, ACM Ubicomp, 16 September 2011.

[5] Nicholas Jing Yuan, Yu Zheng and Xing Xie, Segmentation of Urban Areas Using Road Networks, MSR-TR-2012-65, 2012.

[6] Yu Zheng. Methodologies for cross-domain data fusion: an overview, IEEE Transactions on Big Data, vol. 1, no. 1, pp. 16-34, 1 March 2015. 

[7] Y. Ye, Y. Zheng, Y. Chen, J. Feng, and X. Xie. Mining individual life pattern based on location history. 2009. 

[8] J. Zheng and L. M. Ni. An unsupervised framework for sensing individual and cluster behaviour patterns from human mobile data. In UbiComp, 2012.

[9] J. Shang et al. Inferring gas consumption and pollution emission of vehicles throughout a city. In KDD, 2014. 

[10] Y. Wang, Y. Zheng, and Y. Xue. Travel time estimation of a path using sparse trajectories. In KDD, 2014. 

[11] S. Sun, C. Zhang, and G. Yu. A bayesian network approach to traffic flow forecasting. IEEE Transactions on ITS, 7(1), 2006. 

[12] R. Silva, S. M. Kang, and E. M. Airoldi. Predicting traffic volumes and estimating the effects of shocks in massive transportation systems. PNAS, 112(18), 2015. 

[13] Junbo Zhang, Yu Zheng, and Dekang Qi. Deep Spatio-Temporal Residual Networks for Citywide Crowd Flows Prediction. Proceeding of the Thirty-First AAAI Conference on Artificial Intelligence (AAAI-17), November 2016

[14] Zheyi Pan, Yuxuan Liang, Weifeng Wang, Yong Yu, Yu Zheng, Junbo Zhang. Urban Traffic Prediction from Spatio-Temporal Data Using Deep Meta Learning. Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1720–1730. July 2019. https://doi.org/10.1145/3292500.3330884

[15] Huaxiu Yao, Xianfeng Tang, Hua Wei, Guanjie Zheng, Zhenhui Li. Revisiting Spatial-Temporal Similarity: A Deep Learning Framework for Traffic Prediction. The Thirty-Third AAAI Conference on Artificial Intelligence (AAAI-19). March 2018 https://arxiv.org/abs/1803.01254
