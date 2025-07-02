# Berkeley_ML_PA11_1_Assignment
## Business Understanding
The objective is to analyze the provided dataset of 426,000 used cars to identify which features most strongly influence the vehicle's price.
This involves performing univariate and bivariate analyses by comparing the target variable (price) with individual predictor variables (i.e., mileage, year, brand, fuel type).
I will generate graphical summaries (i.e., boxplots, histograms, scatter plots) and numerical summaries (i.e., means, medians, correlations) to understand the distribution and relationships between price and other variables.
The goal is to uncover patterns and trends that can inform pricing strategies and highlight what car attributes consumers value most in the used car market.

## Data Understanding
### Data Cleaning and Exploratory Data Analysis
After refining the business understanding, we proceed with constructing a clean and reliable dataset suitable for modeling.
During the data cleaning phase, we address several integrity issues: we identify and handle missing values through appropriate imputation strategies, remove any duplicate records that may bias our results, and detect and address outliers that could distort model training. We also correct incorrect data types to ensure compatibility with modeling tools and fix or remove invalid entries (i.e., impossible mileage or negative prices).
Following cleaning, we conduct exploratory data analysis (EDA) to better understand the dataset.
We begin with univariate analysis, examining the distribution of price and other individual features such as mileage, year, and brand. This is followed by bivariate analysis, where we explore how price relates to other variables using both graphical summaries (i.e., boxplots, scatter plots, and histograms) and numerical summaries (i.e., means, medians, and correlation coefficients).
These steps help us uncover meaningful patterns and relationships in the data, which guide feature engineering and transformation steps—such as scaling, normalization, or applying logarithmic transformations—in preparation for modeling with tools like scikit-learn.
We will look primarily at the top factors that affect car price: cylinders, age, model, manufacturer, odometer, title_status and condition¶
In order to make the columns cylinders numerical, I removed the "other" feature and converted all the string into numerical values (i.e. 6 cylinders converts to 6).
In addition, I converted the year feature to an age feature by subtracting 2024 from the column year. This allowed me to get an interpretable data on age versus price.
With regards to the odometer, I noticed that there was a large number of unique values (48,452). In order to make the box and whisker plots more meaningful, I created the bins with increments of 10,000, 20,000, etc. and plotted to see the effects of odometer on price.
The columns that are numerical include age, cylinders, and odometer. The columns that are categorical include model, manufacturer, title status, and condition.

![image](https://github.com/user-attachments/assets/2773a77c-5907-483a-8785-587a0d197fd7)
Fig. 1. Box and whisker plot of price versus cylinders

From the above graph, we can see that cars with four cylinders have a tight range with a median of around $8000. However, it has a huge number of outliers that go all the way up to approximately $50,000.
Another interesting thing from the graph, cars with six cylinders have a median of approximately $13,000 with the third quartile (75%) of the data at $28,000. Vehicles with 8 cylinders have a median value of $15,000 and a spread that is similar to the cars with 6 cylinders. Vehicles with 10 to 12 cylinders have median values that are less than cars with 6 or 8 cylinders.
I would propose that used car dealerships stock vehicles with 6, and 8 cylinders.  These vehicles can be sold at a higher price with the greater profit margin. Used car dealership should also stock 4 cylinder vehicles because this car is in demand by customers. 

![image](https://github.com/user-attachments/assets/760a44ab-4761-4048-85f5-1c8aa83cf056)
Fig. 2. Box and whisker plot of price versus age (bins)

From the above graph, we can see that cars that are less than 10 years old can fetch the highest price with a median of $23,000. As the age of the vehicle increases, the price keeps moving downwards until about 30 years of age. After 30 years of age, we see that the median price tends to creep up again. One factor for this is well-maintained vintage cars that can fetch a handsome price in the used car market.

![image](https://github.com/user-attachments/assets/d401e99c-e822-4b17-9ac1-c71b62fc8257)
Fig. 3. Box and whisker plot of price versus top 10 models

The graph above shows the top 10 models versus price. The graph shows that models like GMC, RAM, Dodge (which are usually pickup trucks), and Jeep have higher median prices. Vehicles by Toyota also shown to have a median range of about $10,000.
Used car dealership could do well to stock pickup trucks and specific vehicle models that have higher median prices like Toyota's, and BMWs

![image](https://github.com/user-attachments/assets/75561120-3757-4362-a05e-39ce433d7238)
Fig. 4. Box and whisker plot of price versus odometer range (bins)

The graph above shows the odometer range (bins) versus price. Here we see that vehicles with under 10,000 miles have a wide range of values with the first quartile at approximately $12,000 and a third quartile at approximately $39,000 with a median of approximately $32,000. Intuitively, we see that the median values decline as the odometer range increases. Therefore, it would be a good idea to stock vehicles with lower mileage numbers, especially, vehicles under 60,000 miles. We see a significant drop in the median price after the 60,000 mile mark. 

![image](https://github.com/user-attachments/assets/9acb1ce7-b4cd-440e-9c84-92931f79057e)
Fig. 5. Box and whisker plot of price versus condition

The graph above shows the condition versus price. We can see that the vehicles that are good, excellent, like new and new have the highest median prices. Vehicles that are salvage and a fair condition have significantly less value. 
It is best for used car dealership to stock vehicles that are good, excellent and like-new in the lots.

![image](https://github.com/user-attachments/assets/3ed81eaf-88dd-4d53-8cd1-b9ef47b638ba)
Fig. 6. Box and whisker plot of price versus title status

The graph shows the relationship between price and title status. Vehicles that have a clean title and lien have the highest median values of approximately $15,000 and $12,000 respectively. Vehicles with missing or parts only title staters have the lowest median values. This is an expected result because cars with a clean title usually have higher prices.


## Data Preparation
For the data preparation stage, now wanted to clearly understand the outliers in the price. I went ahead and filtered the data frame for price under $55,000 which represents the 99th percentile of prices.
This was followed by a univariate linear regression of the numerical values/columns. I started with cylinders versus price.After fitting the model, I noticed that the RMSE was really huge at approximately 11,400. This shows that the model is not fitting well with the data.
In order to understand further, I scatterplot the price versus cylinders to see if a linear model can fit the data. The graph is shown below in Figure 7. 

![image](https://github.com/user-attachments/assets/0d396067-0b0b-4fef-ba5e-f10c518a6a06)
Fig. 7. Scatterplot of price versus cylinders

Just looking at the scatter plot from price and cylinders, we know that a linear regression model will not work. The data is not linear at all!

I built a linear regression model of price versus odometer and the scatterplot is shown below in Figure 8. 
![image](https://github.com/user-attachments/assets/94a34eee-fc0c-4a9d-934a-884addc0c936)

The graph shows that there are outliers in the far right of the graph with 10,000,000 miles. This seems really unrealistic for a car and must be bad data.I decided to drop all data are above 200,000 miles and the scatterplot is shown below.

![image](https://github.com/user-attachments/assets/52fa7186-c94a-4490-9508-c910b3c1ba90)
Fig. 8. Scatterplot of price versus odometer

Even this data is nonlinear and a linear regression model did not provide any meaningful results.

![image](https://github.com/user-attachments/assets/7204b008-d7f4-40f8-89fb-4b3d2511d746)
Fig. 9. Scatterplot of price versus age (60 years)

I proceeded to build the linear model for price versus age. In the scatter plot shown in Figure 9, I noticed that the data is definitely nonlinear. Especially for vehicles after 40 years, the prices were all over the place.

Therefore, I decided to truncate the data to only include vehicles that were 40 years old. The scatter plot is shown in Figure 10 below. This to did not provide any good linear regression results because the data was not linear.

![image](https://github.com/user-attachments/assets/990c9728-001e-4120-9e1c-6412af687445)
Fig. 10. Scatterplot of price versus age (40 years)

Since the price data was nonlinear, I decided to look at creating the log of price. With this transformation, I reran the linear regression and noticed that the results were much better with the RMSE at 0.63. 
Based on this result, I one hot encoded the categorical columns and appended that to the numerical columns and assigned that as X. the log of price on the other hand was assigned as y. This is the basis for the linear regression models.

## Modeling 
The test – train split was done at 20% – 80%. This was done using the sklearn library. 
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

Building a Linear regression pipeline. My machine does not have enough RAM to handle the data during model fitting. 
Specifically, the matrix being created is ~110,000 rows × ~11,490 columns, which is extremely large. Using PCA, I was able to reduce the dimensionality and the gradient descent converged. Example of the pipeline and used:
scaled_pipe = Pipeline([
     ('scaler', StandardScaler()), 
    ('pca', PCA(n_components=100)), 
    ('regression', LinearRegression())

After fitting the pipeline, I obtained the following result for the train – test MSE: 
Train MSE: 0.22215343295568166
Test MSE: 0.2168855420688496
------
#Train RMSE: 0.47
#Test RMSE: 0.47

This was followed by a Ridge regression with the default alpha set to 1.
The pipeline model for the Ridge regression is shown below: 
scaled_pipe = Pipeline([
    ('scaler', StandardScaler()),
    ('ridge', Ridge())  #using standard alpha = 1
    ])

After fitting the pipeline, I obtained the following results: 
Train MSE: 0.08314456849462178
Test MSE: 0.10860095836211478
------
Train RMSE: 0.29
Test RMSE: 0.33

The last regression used is Lasso regression with the default alpha set to 1. 
The pipeline for the Lasso regression is shown below: 
scaled_pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('lasso', Lasso()) 
])

After fitting the pipeline I obtained the following results:
Train MSE: 0.08314454893567798
Test MSE: 0.10871220357714158
------
Train RMSE: 0.29
Test RMSE: 0.33

All three models show a good value for the RMSE showing that the model could be used to predict the log of price by looking at the coefficients.

## Evaluation
Using the log of price(y) and all the other features (as X), I am getting pretty good test and train RMSE values. The results showed that both the Ridge and Lasso models could be used to predict the car price. This can be done by using the coefficients from the model. Since I used StandardScaler, the coefficients are based on standardized features, not raw ones. This means that:
They are still useful for ranking feature importance, but not directly interpretable in dollars for the price.
In order to make them interpretable in dollars, I need to store the mean and std from StandardScaler and applying the inverse transformation to coefficients (beyond the scope here)
I will also need to find the inverse log of the price, to make the price results interpretable in dollars. This conversion was made to make the data linear.

## Deployment 
Based on the EDA and the regression analysis we can conclude the following: 
As a general rule of thumb, I would propose that used car dealerships stock vehicles with 6, and 8 cylinders.  These vehicles can be sold at a higher price with the greater profit margin. Used car dealership should also stock 4 cylinder vehicles because this car is in demand by customers. 
Used car dealership should only keep vehicles that are 10 years old. This is to ensure that they can get the best price for these vehicles. Vehicles that are more than 10 years old to not fetch a good price.
Used car dealership could do well to stock pickup trucks and specific vehicle models that have higher median prices like Toyota's, and BMWs
It would be a good idea to stock vehicles with lower mileage numbers, especially, vehicles under 60,000 miles. We see a significant drop in the median price after the 60,000 mile mark. 
It is best for used car dealership to stock vehicles that are good, excellent and like-new in the lots.
On the data and analysis side, one major issue that I noticed is that the data pattern is  nonlinear. Therefore, the techniques used such as linear regression, Ridge regression and lasso regression may not be the most suitable for modeling this data set. By converting the price to the log of price, we obtain some resemblance of linearity which allowed me to create better models that could predict the log of price versus the features. However, since the coefficients are based on standardized features, they are useful for ranking feature importance but not directly interpretable in dollars. Also, by taking the log of price, then needs to be some conversion to make the price results interpretable in dollars.






