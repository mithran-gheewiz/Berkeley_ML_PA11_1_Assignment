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
As a general rule of thumb, I would propose that used car dealerships stock vehicles with 6, and 8 cylinders.  These vehicles can be sold at a higher price with the greater profit margin. Used car dealership should also stock 4 cylinder vehicles because this car is in demand by customers. 

![image](https://github.com/user-attachments/assets/760a44ab-4761-4048-85f5-1c8aa83cf056)
Fig. 2. Box and whisker plot of price versus age (bins)

From the above graph, we can see that cars that are less than 10 years old can fetch the highest price with a median of $23,000. As the age of the vehicle increases, the price keeps moving downwards until about 30 years of age. After 30 years of age, we see that the median price tends to creep up again. One factor for this is well-maintained vintage cars that can fetch a handsome price in the used car market.

![image](https://github.com/user-attachments/assets/d401e99c-e822-4b17-9ac1-c71b62fc8257)


