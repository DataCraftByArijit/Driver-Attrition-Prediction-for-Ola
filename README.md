# Driver Attrition Prediction for Ola (Industry: Transportation / Ride-Hailing)
This project utilizes ensemble learning techniques to predict driver churn for Ola, a major ride-hailing service. By analyzing demographic, tenure, and performance data, the project identifies at-risk drivers and provides actionable insights to improve retention and reduce the high costs associated with driver recruitment.

# Project Overview
Ola faces a critical challenge with high driver attrition, which destabilizes operations and increases costs, as acquiring new drivers is significantly more expensive than retaining current ones. This project analyzes a dataset of 19,104 entries covering 2019 and 2020 to build predictive models. By implementing Bagging (Random Forest) and Boosting (XGBoost) algorithms, the goal is to proactively identify drivers likely to leave and suggest targeted interventions such as incentives or support programs.

# Problem Statement
Ola is struggling with high attrition rates among its drivers. This churn leads to high recruitment costs, resource-intensive onboarding, and inconsistent service quality. The business needs a data-driven approach to predict which drivers are at risk of leaving based on their historical performance (ratings, income trends) and demographics.

# Objectives
 * Predict Driver Attrition: Build a binary classification model to identify drivers likely to churn (target value 1).
 * Data Preprocessing: Handle missing values (Age, Gender) using KNN Imputation and address significant class imbalance.
 * Feature Engineering: Derive new features such as "Rating Increase," "Income Increase," and "Reporting Rate" to better capture driver sentiment.
 * Model Comparison: Evaluate the performance of Bagging (Random Forest) and Boosting (XGBoost, LightGBM, AdaBoost) to select the most reliable model for business deployment.

# Data Set
The dataset contains monthly reporting information for drivers. 
 * MMMM-YY: Monthly reporting date (renamed to Reporting_Date).
 * Driver_ID: Unique identifier for each driver.
 * Age: Driver's age (Range: 21 to 58).
 * Gender: Encoded as Male (0) or Female (1).
 * City: Category codes for 29 distinct cities.
 * Education_Level: 0 (10+), 1 (12+), or 2 (Graduate).
 * Income: Monthly average income.
 * DateOfJoining: Date the driver joined Ola.
 * LastWorkingDate: Date the driver left (null if still active).
 * Joining Designation: Initial designation level (1 to 5).
 * Grade: Current grade level of the driver (1 to 5).
 * Total Business Value: Monthly value acquired by the driver.
 * Quarterly Rating: Performance rating (1 to 5).

# Milestones
 * Data Exploration: Identified 19,104 rows and 14 initial columns; observed 67.87% churn rate in the aggregated data.
 * KNN Imputation: Used KNNImputer ($n\_neighbors=5$) to fill missing values in Age and Gender.
 * Data Aggregation: Grouped data by Driver_ID to create a single record per driver, capturing "first" and "last" snapshots for trend analysis.
 * Feature Engineering: Created churn (Target), Rating_increase, and Income_increase columns.
 * Class Imbalance Treatment: Applied SMOTE to balance the training data, as churned drivers were the majority in the aggregated set.
 * Model Tuning: Utilized RandomizedSearchCV to optimize hyperparameters for Random Forest and XGBoost. Evaluation:
 * Generated Confusion Matrices, ROC-AUC curves, and Classification Reports.

# Findings
 * High Attrition Rate: In the aggregated driver dataset, approximately 67.87% of drivers have left the company.
 * Income Stagnation: A staggering 98.19% of drivers did not receive an income increase during their tenure, which strongly correlates with dissatisfaction.
 * Performance Correlation: Retained drivers have a significantly higher median Total Business Value (~2.64M) compared to churned drivers (~465K).
 * Rating Trends: 84.96% of drivers did not see a quarterly rating increase. Drivers with a rating of 1 are at the highest risk of leaving.
 * Model Performance: XGBoost outperformed Random Forest with a test accuracy of 0.94 and a higher recall for churned drivers (0.96 vs. 0.94).
 * Key Predictors: The most important features for predicting churn are Rating_increase, Year_of_joining, and Reportings.

# Recommendations
 * **Improve Incentive Structures:** Since 98% of drivers see no income growth, Ola should implement tiered bonuses linked to Total Business Value and Quarterly Ratings to reward top performers.
 * **Enhance Early Tenure Support:** High churn is noted among recent joiners. Introducing tailored onboarding and mentorship for drivers in their first year can reduce early exits.
 * **Performance Rehabilitation:** Instead of allowing low-rated drivers to churn, Ola should provide training programs for those with a Quarterly Rating of 1 to help them improve their business value.
 * **Regional Strategy:** Address city-specific churn (e.g., City C20) by conducting localized studies on competitor rates and demand management.
 * **Deploy XGBoost Model:** Utilize the XGBoost model for operational churn prediction as its high recall (96%) ensures that very few at-risk drivers are missed.

# Colab Link
 * https://colab.research.google.com/drive/18xzJUdFWBZa3IpMqBEHF82xeBTrxRG40

# Data Link
 * https://drive.google.com/file/d/1GxMjz6i9_BMDdivh7XPSr25YzvbTOOOl/view?usp=drive_link
