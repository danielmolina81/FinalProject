# Project-4-Happiness Index
# The World Happiness Report

## Project Overview
The goal of this project is to determine whether living conditions can influence the level of happiness. By leveraging both individual and group contributions, we will thoroughly analyze various datasets that impact a country's happiness score. Our aim is to identify and understand the key factors that make a country happy or unhappy. The objective is to develop a comprehensive understanding of which countries are the happiest and least happy, identify the most significant features contributing to national happiness, and determine the best model for predicting happiness. This analysis will provide deeper insights into assessing a country's happiness score.

The main findings are targeted towards government officials, policymakers, businesses, and anyone interested in learning about the factors that contribute to a country's happiness. The results will highlight which features affect happiness the most, the least, or have an average impact.

Our analysis will feature a dashboard focused on the logistic regression model and will allow users to:

1. Input scores from any category within a specified range to see how that factor contributes to the happiness of a region.
2. Determine whether a region is happy or unhappy based on the scores.
3. Compare similarities and differences between models to better understand the accuracy of the predictions.

## Presentation link
https://docs.google.com/presentation/d/1OLYXT3qZrvakpfUAAf72BuSIRfQNrr3w8HYSeFhkGK4/pub?start=false&loop=false&delayms=3000&slide=id.p

## Instructions
- Clone the project repository to your local machine
- Open and execute the notebook 'cleaning code.ipynb' using Jupyter Notebook
- Explore the folders to find the series of analysis performed on the data
- For the Initial Data Analysis section, you can also visit our tableau dashboard (link below)
- For the Logistic Regression model. After running the file 'Logistic model midpoint.ipynb', open your web browser and navigate to http://127.0.0.1:8050/ to access the Dash application.

## General steps followed
- Gathered more datasets and downloaded each file in csv format
- Created a Jupyter Notebook and imported data set
- Cleaned the data and created a clean pandas Data frame that was extracted into a SQlite data base
- Queried the data base to obtain the data needed for the analysis and visualizations
- Queried the data base to obtain the data needed for the modeling different methods, using sklearn library
- Prepared data needed for the visualizations in Tableau
- Created the Dash application and coded each one of the visualizations
- Created an interactive dashboard to predict whether a given country is happy / unhappy

## Detailed steps

### Data Cleaning
- The data cleaning process involved several key steps to ensure consistency and integrity across the dataset. First, many columns were renamed to maintain consistency across all tables. Next, formatting adjustments were made to remove trailing spaces, and data types were converted as needed to maintain the integrity of the data.
- Once these steps were completed, the cleaned data was merged into the main cleaning code file. The relevant columns were then identified, and any missing data with null values was removed to ensure completeness.
- Finally, the cleaned data was saved as a CSV file and an SQLite file was created to serve as our database connection.

### Initial Data Analysis
- Importing and analysing data
- Analysis of Happiest and unhappiest countries in 2023 and creating visualizations (bar plots with top and bottom 10 countries; World map showing regions with different happiness score; scatter plot with happiness score and log GDP per capita comparison by countries via regions; plot with all variables for each top 10 countries as well bottom 10 countries).
- Region Analysis (analysis of how many countries in each region have happiness score greater than 6; Happiness by region shown in box plot based on happiness score; creating Kernel Density Estimate (KDE) plot of Happiness score distribution by region).
- Correlation Matrix Heatmap for 2023.
- Relationship between all variables and happiness score shown in 12 scatter plots.
- Distribution of 2 set variables presented through box plot highlighting outliers in each set.

### Tableau worksheets and dashboards
- Link: https://public.tableau.com/app/profile/jelena.r2636/viz/CountriesHappiness2023-project/Dashboard1?publish=yes
- World Happiness Map with a dropdown to choose to show happy countries (happiness score >7) as well as unhappy countries (happiness score <4)
- Top 10 Happiest countries 2023
- 10 Unhappiest countries 2023
- Countries and happiness score with an option to select and search for a country
- Main variables top 10 countries
- Europe happiest countries
- Happiness and population density
- Happiness score and Log GDP per capita by countries via regions in 2023
- Dashboard 1
- Dashboard 2

### Exploratory Linear Regression 
- The idea behind the linear regression is to explore the correlation between the happiness score and various factors. Since this is an exploratory step, the goal is to determine whether there is a strong variance as well as identify which factors contribute the most to a happy region. At the end of the analysis, we compute the linear model’s key metrics: score, R², MSE, RMSE, and standard deviation.
- R² explains the variance of the independent variables in the dependent variable. The closer R² is to 1, the better the model fits the data.
- **Alcohol**: 0.3650
- **Avg temperature**: 0.2557
- **Freedom life choice**: 0.4316
- **Generosity**: 0.0092
- **Gini coefficient**: 0.0666
- **Healthy life**: 0.5957
- **Logged GDP**: 0.6250
- **Median age**: 0.4909
- **Perceptions of corruption**: 0.2467
- **Population density**: 0.2557
- **Social support**: 0.7220
- **Unemployment**: 0.0442
- As we can see from the test results in each file, "Social support" with an R² of 0.72196 (or 72%) has a relatively strong dependence on happiness. "Logged GDP" comes in with a R² of 0.62 (or 62%) and "Healthy life" comes in at 0.60 or (62%).
- By comparing R² values, we observe that "Social support," "Logged GDP," and "Healthy life" are the strongest predictors in this model. 
- On the other hand, variables like "Median age" and "Freedom of choice" are moderate predictors, while "Generosity," "Unemployment," and the "Gini coefficient" are weak predictors.
- In summary, our regression model suggests that "Social support," "Logged GDP," and "Healthy life" are the most significant predictors of happiness, while "Generosity" and "Unemployment" contribute little to the model's predictive power

### Linear Regression with multiple variables
- Define X and Y ("ladder_score" as independent variable)
- Split the data into train and test train for the Linear Regression Model
- Train the linear regression model
- Evaluate the model
- Calculate coefficients
- Make predictions with split test data
- Run the model mean error and r score
- Conclusion: A negative coefficient suggests that as the independent variable increases, the dependent variable tend to decrease. The highest dependent variables in the linear regression model are social support, freedom_life_choices and GDP per capita. The mean absolute error is close to 0 (0.4). According to r score (0.82) there is a strong correlation between the independent variable and all dependent variables. However, the model has a higher margin of error, compared to logistic regression model.

### Random Forest model
- Define X and Y ("happiness" as independent variable)
- Define 0 and 1 in the binary classification (midpoint + 1 = 1 "Happy", else = 0 "Unhappy")
- Drop any columns that are object type
- Split the data into train and test train (test size: 20%, random state of 98 countries (80% of the total))
- Fitting the Random Forest Model using 50 estimators with 16 maximum leaves and 42 random states
- Making predictions with testing data
- Evaluating the data
- Print confusion matrix, classification report, and level of importance for each X variable
- Graph first 3 decision trees from the forest
- Conclusion: 84% of accuracy predicting happy countries in and unhappy countries in 83%.
- The model can find 62% of all objects of the target class 0 and 89 & of class 1.
- The overall 84% accuracy shows that RF does not seem to be the most efficient and best predicting model compared to logistic regression.

### Logistic Regression Model
- After importing the dependencies, the data was pulled from SQLite data base
- To classify the target variable, a midpoint between the highest and the lowest happiness score was calculated and defined as threshold for happiness.
- Unnecessary columns were drop, the target variable was defined as well as the features
- The data was split between train and test
- The features were scaled using 'sklearn'
- The logistic regression model was fit, and predictions were obtained
- Finally, the accuracy and the classification report were generated, as well as the coefficients to determine the importance of the features
- The model has an accuracy of 87%, which means that 87% of the predictions were correct.
- Precision. 75% of predicted unhappy countries were actually unhappy and 95% of the predicted happy countries were actually happy
- Recall. 90% of the happy countries were correctly predicted as happy and 86% of the unhappy countries were correctly predicted as unhappy
- There was other 2 instances of this model where two different thresholds were used to classify the target variable. The first one used a score of 4 and the second one use the median of the scores. None of them resulted in a higher accuracy, precision and recall than the one where the midpoint was used.
- A Dash application was developed where the model was deployed. Users can input different values for the features and the application predicts if the target variable is 1 or 0 (happy or unhappy)  

## Sources

### Data Set
- https://databank.worldbank.org/metadataglossary/gender-statistics/series/SI.POV.GINI#:~:text=The%20Gini%20index%20measures%20the,of%20100%20implies%20perfect%20inequality. Aug 06, 2024
- https://www.cia.gov/the-world-factbook/references/guide-to-country-comparisons/ Aug 06, 2024
- https://www.worldbank.org/en/about/leadership#:~:text=The%20World%20Bank%20is%20like,policymakers%20at%20the%20World%20Bank. Aug 06, 2024
- https://tradingeconomics.com/country-list/temperature Aug 05, 2024
- https://www.worldbank.org/en/about/leadership#:~:text=The%20World%20Bank%20is%20like,policymakers%20at%20the%20World%20Bank. Aug 07, 2024

### Further references
- https://github.com/vivek2319/Linear-Regression-Prediction/blob/master/Linear_Regression_Scikit_learn.py
- https://statisticsbyjim.com/regression/interpret-coefficients-p-values-regression/
- https://www.datacamp.com/tutorial/random-forests-classifier-python
- https://togroundcontrol.com/blog/creating-a-problem-statement/ Aug 07, 2024
- https://stock.adobe.com/images/multicultural-students-jumping-happiness-success-happy-young-people-vector-flat-cartoon-university-students-or-college-and-school-friends-jump-up-with-raised-hands-and-happy-smiles-of-celebration/380929173 Aug 07, 2024
- https://www.redbubble.com/shop/funny+thought+bubble+posters Aug 14, 2024
- https://github.com/vivek2319/Linear-Regression-Prediction/blob/master/Linear_Regression_Scikit_learn.py
- https://pixers.ca/posters/don-t-worry-be-happy-42945128 Aug 15, 2024

## Team Members
- Laura Roa
- Daniel Molina
- Jelena Raonic
- Mohammed Ali