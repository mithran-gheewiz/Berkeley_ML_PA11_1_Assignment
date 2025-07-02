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






