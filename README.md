# Black-Friday-Sales-Prediction-Model
Black Friday Sales Prediction
This repository contains my solution to the Black Friday Sales Prediction problem, a machine learning project from Analytics Vidhya's Black Friday Hackathon. The goal of this project is to predict the purchase amount for customers based on their demographics and product details, which can be used by the retail company, "ABC Private Limited," to personalize offers and improve customer engagement.

Problem Overview
"ABC Private Limited," a retail company, aims to understand and predict customer purchase behavior for various high-volume products. The provided dataset includes:

Customer demographics (such as age, gender, marital status, city category, and years of stay in the current city)

Product details (product ID and product categories)

Target variable: Purchase, which represents the total amount spent by each customer last month.

By building a predictive model, we can estimate the purchase amount for each customer-product combination. This will allow the company to personalize offers for different customer segments and optimize sales strategies.

Data Dictionary

Variable	Definition

User_ID	Unique identifier for each customer

Product_ID	Unique identifier for each product

Gender	Sex of the customer

Age	Age group of the customer (in bins)

Occupation	Customer's occupation (masked)

City_Category	Category of the city (A, B, or C)

Stay_In_Current_City_Years	Number of years spent in the current city

Marital_Status	Marital status of the customer

Product_Category_1	Main category of the product (masked)

Product_Category_2	Secondary category of the product (masked)

Product_Category_3	Tertiary category of the product (masked)

Purchase	Purchase amount (target variable)

The model performance is evaluated on a separate test dataset (test.csv), which contains similar fields but excludes the Purchase variable.

Approach

1. Data Loading and Basic Exploration
Imported essential libraries and read the training, test, and sample submission datasets.
Checked the shape and previewed the data to understand its structure and key attributes.

2. Data Preprocessing
Saved User_ID and Product_ID from the test dataset for final submission.
Transformed categorical variables (User_ID and Product_ID) using LabelEncoder.
Identified and handled missing values:
Dropped Product_Category_2 and Product_Category_3 due to a high percentage of missing values.

3. Feature Engineering
Converted categorical variables to dummy variables using pd.get_dummies, creating a more usable format for machine learning algorithms.

4. Splitting the Data for Validation
Created a validation set (20% of the training data) to evaluate models and avoid overfitting.

5. Model Selection and Evaluation
Implemented and evaluated multiple models to predict Purchase:

a. Linear Regression
Applied linear regression as a baseline model.
Calculated the RMSE score to measure initial model performance.

b. Lasso Regression
Used Lasso regression to improve performance and prevent overfitting.
Tuned hyperparameters with RandomizedSearchCV to optimize for mean absolute error.
Reported top models from cross-validation and compared RMSE with baseline linear regression.

c. XGBoost Regressor
Experimented with XGBoost, tuning several hyperparameters to optimize for the best RMSE.
Achieved the best RMSE with XGBoost, which became the final model for prediction.

d. Neural Network
Tested a simple neural network with MLPRegressor.
Although initial results didn’t improve over XGBoost, tuning hidden layer sizes could improve performance, though infrastructure limitations restricted experimentation.

6. Final Model Training and Submission
Retrained the XGBoost model on the entire training set, predicted the Purchase variable for the test data, and created a CSV submission file.
Saved predictions for the test dataset in Krish_Black_friday_sales_prediction.csv.

Summary of Model Performance
The XGBoost model achieved the best RMSE score (2,666), showing significant improvement over baseline models. While neural networks didn’t perform as well, they could be explored further with more complex architectures.
