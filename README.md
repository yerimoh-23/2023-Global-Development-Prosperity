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

1. ggpair plot of all explanatory variables

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/ggpairs.png)

2. Histogram for each variable

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/histogram.png)

3. Density plot for each variable

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/density%20plot.png)

4. Boxplot for each variable

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/box%20plot.png)

5. Correlation matrix

![alt text](https://github.com/yerimoh-23/2023-Global-Development-Prosperity/blob/main/Graphs/correlation%20matrix.png)
    * We could see that most of the variables, except for PersonalFreedom and NaturalEnvironment, have a strong linear correlation.



## Analysis

<img width="830" alt="Screenshot 2025-03-01 at 9 47 49 PM" src="https://github.com/user-attachments/assets/ad1c097f-5f51-412d-8a00-cf76b6dc8004" />

<img width="829" alt="Screenshot 2025-03-01 at 9 48 09 PM" src="https://github.com/user-attachments/assets/62bf9eb1-87a5-4148-9bea-4ca250cba4a4" />

• Cluster 1 - Developed Nations: This cluster is characterized by high average scores in most dimensions, indicating well-developed and prosperous countries. Safety and security, personal freedom, and governance scores are significantly higher, reflecting stable and free societies with eﬀective governance structures. Economic quality, living conditions, and education are also high, suggesting a high standard of living and strong educational systems. The lower standard deviation values indicate that countries in this cluster are more homogenous, with similar high scores across various dimensions. This cluster can be named “Developed Nations,” as it includes countries that are leaders in multiple areas of prosperity.

• Cluster 2 - Developing Nations: This cluster includes countries with moderate scores across most dimensions. The average scores for safety and security, personal freedom, and governance are balanced, indicating a transitional state of development. Economic quality and living conditions are relatively strong, suggesting a decent standard of living and economic environment. The standard deviation values suggest moderate variability within this cluster, with countries having consistent scores across diﬀerent dimensions. This cluster can be named “Developing Nations,” representing countries that are progressing towards higher levels of prosperity but still face significant challenges.

• Cluster 3 - Underdeveloped Nations: Countries in this cluster exhibit lower scores across most dimensions compared to Cluster 1. The average scores for safety and security, governance, and economic quality are notably lower, reflecting substantial challenges in these areas. Personal freedom and social capital are also lower, indicating issues related to individual liberties and societal trust. The higher standard deviation values in this cluster indicate greater variability among countries, highlighting significant diﬀerences within the group. This cluster can be referred to as “Underdeveloped Nations,” as it comprises countries that are still working towards improving their overall prosperity.

Overall, the clustering analysis suggests that 3 clusters eﬀectively capture the diﬀerences in global prosperity among countries. These clusters align with the classic literature categorization of countries into underdeveloped, developing, and developed nations. This natural separation within the data confirms that the traditional distinctions are grounded in the actual metrics of prosperity and development. The analysis reinforces the validity of these categories by showing that the diﬀerences in dimensions such as safety and security, governance, and economic quality are significant enough to group countries naturally into these three well-defined clusters.

#### K−Means Clustering Results on World Map

<img width="766" alt="Screenshot 2025-03-01 at 9 51 15 PM" src="https://github.com/user-attachments/assets/2b62cc20-7710-4048-8793-3a19bf48f17f" />

The map highlights the clustering results of the K-Means algorithm applied to the Global Prosperity Data:

• __Developed (pink)__: These regions include North America, Western Europe, and parts of Oceania, reflecting high prosperity and well-being.

• __Developing (Green)__: Central and South America, parts of Eastern Europe, and much of Asia fall into this category, showing moderate levels of prosperity.

• __Underdeveloped (blue)__: Most of Africa and parts of South Asia are classified here, indicating lower levels of prosperity and development.
