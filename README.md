# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal is to leverage data from multiple APIs using visualizations and statistical modeling to derive meaningful insights between city bikes and restaurants in Toronto. 

## Process
1. Accessed data from CityBikes API for bike stations in Toronto and parsed the returned JSON response into a dataframe. Review the retrieval process on [city_bikes.ipynb](notebooks/city_bikes.ipynb)
2. Retrieved restaurant data within 1000 meter radius of each bike station using the Foursquare and Yelp APIs. The JSON responses from both APIs calls were parsed into two separate dataframes. Review the retrieval process on [yelp_foursquare_EDA.ipynb](notebooks/yelp_foursquare_EDA.ipynb)
3. EDA was performed on the merged CityBikes and Yelp dataframe. Find the details on the data joining, cleaning and exploration process on [joining_data.ipynb](notebooks/joining_data.ipynb)
4. Modeled the CityBikes/Yelp dataframe using the OLS method to investigate the relationship between the 'Number of Bikes' and the characteristics of nearby restaurants. Evaluate the hypotheses, model output and assumptions tests on [model_building.ipynb](notebooks/model_building.ipynb)

## Results
* Based on the restaurant characteristics parsed from the APIs, Yelp returned more detailed/relevant information than Foursquare. For example, Yelp provides the rating, number of reviews and price point for each restaurant which allows users to draw deeper insights when evaluating the data. Therefore, Yelp’s API would be recommended over Foursquare’s API.
* The results of the regression suggest that there is a statistical significance (p-value<0.05) between the ‘Number of Bikes’ at a bike station and the selected characteristics of the surrounding restaurants (e.g. distance, rating and number of reviews). However, the low Adjusted R-Squared value (0.2%) indicates that the model is not capable of predicting future trends or outcomes. Additionally: 
  * The OLS output and correlation matrix confirm that the Number of Bikes:
    * Has a very weak positive correlation to Distance
    * Has a very weak negative correlation with Ratings and the Number of Reviews
  * Plotting the residuals shows that the model failed the normality and homoscedasticity assumption tests. 
  * Based on the model and residual plots, the null hypothesis was rejected however, the data did not provide sufficient evidence to accept the alternative hypothesis. Further exploration is required before the alternative hypothesis can be accepted.
* Although the model doesn’t have predictive power, the data itself yields interesting prescriptive insights for tourists/locals in Toronto. For example:
  * The data can return the average restaurant rating within 1,000 meters radius of a specified bike station. As a result, the users of the data can select/avoid bike stations according to the likelihood of finding a quality restaurant nearby.
  * The data can find the top restaurants in Toronto according to their rating and number of reviews which would help users with choosing a highly rated/reviewed restaurant.
  * The data revealed that most bike stations have 0 bikes available which indicates that city bike users should research their chosen bike station to ensure there will be a bike available for use.

## Challenges 
* Creating the functions to retrieve the data from each API and then parsing the responses into a dataframe.
* Identifying patterns and drawing business insights when the model output is not conclusive.

## Future Goals
* Explore more points of interests and experiment with more independent variables to improve the statistical model’s performance.
* Evaluate the data using alternative models (e.g. Logistic Regression, Multinomial Regression, etc.)
* Craft alternative hypotheses in order to analyze multiple questions about the dataset (e.g. What are the best dates/times to get a bike from a specific station?)
