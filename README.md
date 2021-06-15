# Reduce Traffic Mortality in U.S.


## Traffic Mortality in US

<p><img src="https://s3.amazonaws.com/assets.datacamp.com/production/project_462/img/car-accident.jpg" alt=""></p>

<p>While the rate of fatal road accidents has been decreasing steadily since the 80s, the past ten years have seen a stagnation in this reduction. Coupled with the increase in number of miles driven in the nation, the total number of traffic related-fatalities has now reached a ten year high and is rapidly increasing.</p>
<p>Per request of the US Department of Transportation, we are currently investigating how to derive a strategy to reduce the incidence of road accidents across the nation. By looking at the demographics of traﬃc accident victims for each US state, we find that there is a lot of variation between states. Now we want to understand if there are patterns in this variation in order to derive suggestions for a policy action plan. In particular, instead of implementing a costly nation-wide plan we want to focus on groups of  states with similar profiles. 

<b>How can we find such groups in a statistically sound way and communicate the result effectively?</b></p>

<p>This data was originally collected by the National Highway Traffic Safety Administration and the National Association of Insurance Commissioners. This particular dataset was compiled and released as a <a href="https://github.com/fivethirtyeight/data/tree/master/bad-drivers">CSV-file</a> by FiveThirtyEight under the <a href="https://github.com/ﬁvethirtyeight/data">CC-BY4.0 license</a>.</p>

### Attribute Information

* <code>State:</code> Name of the state
* <code>drvr_fatl_col_bmiles:</code> fatalities of drivers in billion miles
* <code>perc_fatl_speed:</code> percent of fatalities caused due to speed
* <code>perc_fatl_alcohol:</code> percent of fatalities caused due to drinking alcohol
* <code>perc_fatl_1s_time:</code> percent of fatalities recorded first time



### Exploration

![pairplot](https://github.com/nischaybikramthapa/reduce-traffic-mortality/blob/main/imgs/pair.JPG)

We can see some potentially interesting relationships between the target variable (the number of fatal accidents) and the feature variables (percentage of fatalities).

![corrleation](https://github.com/nischaybikramthapa/reduce-traffic-mortality/blob/main/imgs/corr.JPG)

<p> We see that the amount of fatal accidents is most strongly correlated with alcohol consumption. But in addition, we also see that some of the features are correlated with each other, for instance, speeding and alcohol consumption are positively correlated. We, therefore, want to compute the association of the target with each feature while adjusting for the effect of the remaining features. This is done using multivariate linear regression. We learnt that alcohol consumption is weakly associated with the number of fatal accidents across states. This lead us to conclude that alcohol consumption should be a focus for further investigations and maybe strategies should divide states into high versus low alcohol consumption in accidents. But there are also associations between alcohol consumptions and the other two features, so it might be worth trying to split the states in a way that accounts for all three features.</p>

### PCA and KMeans Clustering

The first two principal components enable visualization of the data in two dimensions while capturing a high proportion of the variation (79%) from all three features: speeding, alcohol influence, and first-time accidents. This enables us to use our eyes to try to discern patterns in the data with the goal to find groups of similar states. However, it was not entirely clear how many groups in which the states cluster. To assist with identifying a reasonable number of clusters, we used KMeans clustering resulting in three clusters.

![pca](https://github.com/nischaybikramthapa/reduce-traffic-mortality/blob/main/imgs/cluster.JPG)

It is clear that different groups of states may require different interventions. Since resources and time are limited, it is useful to start off with an intervention in one of the three groups first. Which group would this be? To determine this, we included data on how many miles are driven in each state, because this will help us to compute the total number of fatal accidents in each state. When we combined we found 22 states in cluster 1 with higher number of drivers involved in road accidents.

![state](https://github.com/nischaybikramthapa/reduce-traffic-mortality/blob/main/imgs/state_1.JPG)

### Recommendation

Based on the information, it is recommended to apply policy intevention to states under cluster 1 followed by other two clusters. This way we coould speculate what percentage of fatalities could be controlled. In addition, more data related to states and fatalities can be added to identify simlaritites between states and prioritise them.
