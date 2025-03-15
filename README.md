# Report
- December 4, 2024
- Yerim Oh

## Title
2023 Global Development & Prosperity Analysis by K-Means Clustering

## Abstract
This study employs an unsupervised machine learning model to analyze the level of prosperity across countries based on the 2023 Legatum Prosperity Index data. The dataset includes various economic and social indicators (12 numerical variables) for 167 countries worldwide. The aim of this analysis is to cluster countries according to their prosperity levels and identify the key factors driving disparities in prosperity between nations. In an increasingly globalized world, understanding the factors that contribute to prosperity gaps is crucial. By utilizing the K-means clustering algorithm, this research groups countries with similar characteristics, emphasizing not only economic power but also the influence of various social factors on national prosperity. This approach seeks to provide deeper insights into the multi-dimensional aspects that shape prosperity beyond simple economic measures.

## Datasets

__2023 Global Country Development & Prosperity Index__ https://index.prosperity.com/rankings 

This dataset contains rankings and indicators from the 2023 Legatum Prosperity Index, assessing various dimensions of prosperity and development across countries. There are 167 observations according to 167 countries and 12 numerical variables:

• `SafetySecurity`: Freedom from conflict, terrorism, and crime

• `PersonelFreedom`: Right to speech, assembly, and individual autonomy

• `Governance`: Quality of democracy, rule of law, and government eﬀectiveness

• `SocialCapital`: Strength of personal relationships and civic engagement

• `InvestmentEnvironment`: Conditions for private investment and credit access

• `EnterpriseConditions`: Business environment and market competition

• `MarketAccessInfrastructure`: Ease of trade and quality of infrastructure

• `EconomicQuality`: Macroeconomic stability and employment quality

• `LivingConditions`: Standard of living and access to basic services.

• `Health`: Population health and healthcare access.

• `Education`: Quality and accessibility of education.

• `NaturalEnvironment`: Environmental quality and sustainability.

📍 Excluded the `AverageScore` variable, since it is the overall average score of the country across all indicators.

## Exploratory Data Analysis + Visualization

K-means clustering does not assign a response variable. Therefore, all the variables used in the analysis are considered "explanatory" and are used to determine cluster assignments.

1. ggpair plot of all explanatory variables ![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/ggpairs.png)

2. Histogram for each variable ![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/histogram.png)

3. Density plot for each variable ![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/density%20plot.png)

4. Boxplot for each variable ![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/box%20plot.png)

5. Correlation matrix ![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/correlation%20matrix.png)
   * We could see that most of the variables, except for PersonalFreedom and NaturalEnvironment, have a strong linear correlation.

## Data Processing
We have to normalize the variables to express them in the same range of values by adjusting values measured on diﬀerent scales to a common scale.
![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/normalization.png)

The points in the normalized data are the same as the original one. The only thing that changes is the scale of the axis.

## K-means Execution
Clustering methods that divides a data set into K distinct, non-overlapping clusters
- assigns data points to one of the K clusters depending on their distance from the center of the clusters

### Algorithm
The K-means clustering algorithm works through an iterative process to find the optimal placement of cluster centroids
1. Randomly choose K centroids.
2. Calculate the Euclidean distance between data points and centroids. Assign each data point to the cluster.
3. Recalculate the centroid of each cluster. Update the centroids.
4. Iterate two steps above until the centroids no longer change or for a specified number of iterations.
5. Outputs the final cluster centroids and the assignment of the data points.

__Note.__ In K-means clustering, we do not choose a "response variable" because the goal is to group data points based on their similarities across multiple variables, not to predict a single outcome. Therefore, all the variables used in the analysis are considered "explanatory" and are used to determine cluster assignments, not a single response variable.

#### Advantages
- Simplicity: Easy to implement and identify unknown groups of data from complex datasets
- Efficiency: Linear time complexity, can handle large datasets conveniently
- Flexibility: Can easily adjust to changes. An instance can change the cluster

#### Disadvantages
- Difficulty in determining the optimal number of clusterings
- Sensitivity to initial conditions
- Sensitivity to outliers
- Limited to linear boundaries

### Knitr Package
`cluster`: A vector of integers indicating the cluster to which each point is allocated.

`centers`: A matrix of cluster centers.

`size`: The number of points in each cluster.

`betweenss`: The between-cluster sum of squares. In an optimal segmentation, one expects this ratio to be as higher as possible, since we would like to have heterogeneous clusters.

`withinss:` Vector of within-cluster sum of squares, one component per cluster. In an optimal segmentation, one expects this ratio to be as lower as possible for each cluster, since we would like to have homogeneity within the clusters.

`tot.withinss`: Total within-cluster sum of squares.

`totss`: The total sum of squares.

### Find optimal K by Elbow Method
![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/elbow%20method.png)

#### Elbow Method:
We should choose a number of clusters so that adding another cluster does not give much better partition of the data. The number of clusters, K, is chosen at the point where the gain will drop giving an angle in the graph. As k increases, W(within-cluster sum of squares) decreases. We look for the “elbow” point, which is the point where the rate of decrease in W starts to level off. Therefore, our optimal value for k is 3. The total within-cluster sum of squares drops sharply at this point and then begins to level off, suggesting that adding more clusters beyond this point does not significantly improve the variance explained.

## Analysis

The ggpair plot that clearly shows the observations are divided into 3 clusters.
![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/ggpairs%20clustered.png)

#### Cluster Plot
![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/clusterplot.png)

The visualization of K-Means clustering with 3 clusters using different ellipse types shows the general distribution and separation of the clusters. Each plot shows that while clusters are forming, there is some degree of overlap between them. The Euclid ellipse type, which aligns with the distance metric used in K-Means clustering, offers the most distinct representation of the clusters. This indicates that while the clustering captures significant patterns in the data, some similarities between clusters persist. Overall, the clusters provide a clear understanding of their distribution.

### Mean values and Standard Deviation of each cluster
![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/mean%20and%20sd%20of%20clusters.png)

- Cluster 1 - Developed Nations: This cluster is characterized by high average scores in most dimensions, indicating well-developed and prosperous countries. Safety and security, personal freedom, and governance scores are significantly higher, reflecting stable and free societies with eﬀective governance structures. Economic quality, living conditions, and education are also high, suggesting a high standard of living and strong educational systems. The lower standard deviation values indicate that countries in this cluster are more homogenous, with similar high scores across various dimensions. This cluster can be named “Developed Nations,” as it includes countries that are leaders in multiple areas of prosperity.

- Cluster 2 - Developing Nations: This cluster includes countries with moderate scores across most dimensions. The average scores for safety and security, personal freedom, and governance are balanced, indicating a transitional state of development. Economic quality and living conditions are relatively strong, suggesting a decent standard of living and economic environment. The standard deviation values suggest moderate variability within this cluster, with countries having consistent scores across diﬀerent dimensions. This cluster can be named “Developing Nations,” representing countries that are progressing towards higher levels of prosperity but still face significant challenges.

- Cluster 3 - Underdeveloped Nations: Countries in this cluster exhibit lower scores across most dimensions compared to Cluster 1. The average scores for safety and security, governance, and economic quality are notably lower, reflecting substantial challenges in these areas. Personal freedom and social capital are also lower, indicating issues related to individual liberties and societal trust. The higher standard deviation values in this cluster indicate greater variability among countries, highlighting significant diﬀerences within the group. This cluster can be referred to as “Underdeveloped Nations,” as it comprises countries that are still working towards improving their overall prosperity.

Overall, the clustering analysis suggests that 3 clusters eﬀectively capture the diﬀerences in global prosperity among countries. These clusters align with the classic literature categorization of countries into underdeveloped, developing, and developed nations. This natural separation within the data confirms that the traditional distinctions are grounded in the actual metrics of prosperity and development. The analysis reinforces the validity of these categories by showing that the diﬀerences in dimensions such as safety and security, governance, and economic quality are significant enough to group countries naturally into these three well-defined clusters.

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/choropleth%20map.png)

The map highlights the clustering results of the K-Means algorithm applied to the Global Prosperity Data:

• __Developed (pink)__: These regions include North America, Western Europe, and parts of Oceania, reflecting high prosperity and well-being.

• __Developing (Green)__: Central and South America, parts of Eastern Europe, and much of Asia fall into this category, showing moderate levels of prosperity.

• __Underdeveloped (blue)__: Most of Africa and parts of South Asia are classified here, indicating lower levels of prosperity and development.

## Summary
Due to the nature of the K-means clustering model, there is no clear evaluation metric like accuracy/error. However, the optimal number of clusters, K, was determined using the Elbow Method, which measures the variability within clusters. The analysis revealed that not only economic factors but also social factors such as health, education, and safety have a complex impact on a country's prosperity level. For instance, countries with high education and health indicators were grouped together, while countries with low economic indicators and limited access to health and education were placed in a different cluster. 

Additionally, by comparing the means and standard deviations of key variables within each cluster, the specific characteristics of each cluster were identified, confirming that various factors play an important role in national prosperity.

## Reference
- Xie, Y. (2024, November 8). A general-purpose package for dynamic report generation in R [R package knitr version 1.49]. The Comprehensive R Archive Network. https://cran.r-project.org/web/packages/knitr/index.html 
- Massicotte, P. (2023, December 15). World map data from Natural Earth [R package rnaturalearth version 1.0.1]. The Comprehensive R Archive Network. https://cran.r-project.org/web/packages/rnaturalearth/index.html 
- Xvivancos. (2024, November 16). Tutorial: Clustering wines with K-means. Kaggle. https://www.kaggle.com/code/xvivancos/tutorial-clustering-wines-with-k-means/report 
James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). K-means Clustering. In An introduction to statistical learning : with applications in R (2nd ed., pp. 515–519). essay, Springer. Retrieved December 1, 2024,.
- Eric J. K-Means Clustering: 7 Pros and Cons Uncovered. Datarundown. https://datarundown.com/k-means-clustering-pros-cons/
- Juliana D. (2021, March 12). Supervised versus unsupervised learning: What's the difference?. IBM https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning
- parvezcs20. (2023, Dec 09). Demonstration of K-Means Assumptions. Geeksforgeeks https://www.geeksforgeeks.org/demonstration-of-k-means-assumptions/
