## How to use this repo

1. Fork this repo. 

1. In your forked churnometer repo click on the green **Code** button. 

1. Then, from the Codespaces tab, click **Create codespace on main**.

1. Wait for the workspace to open. This can take a few minutes.

1. Open a new terminal and `pip3 install -r requirements.txt`

1. Click the kernel button and choose Python Environments.

1. Choose the kernel Python 3.12.1 as it inherits from the workspace, so it will be Python-3.12.1 as installed by Codespaces. To confirm this, you can use `! python --version` in a notebook code cell.

Your workspace is now ready to use. When you want to return to this project, you can find it in your Cloud IDE Dashboard. You should only create 1 workspace per project.


## Dataset Content

The dataset is sourced from [Kaggle](https://www.kaggle.com/datasets/annarosencrantz/gyminsights). We then created a fictitious user story where predictive analytics can be applied in a real project in the workplace.  

Each row represents a customer, and each column contains a customer attribute. The dataset includes information about:  

- Services that each customer has signed up for, such as membership type, personal training, class attendance, and contract length.  
- Customer information, such as how long they have been a member, whether they have churned, their preferred payment method, and monthly charges.  
- Customer demographics, such as age, gender, and whether they have family memberships.  

| Variable         | Meaning                                             | Units                                          |
|------------------|-----------------------------------------------------|------------------------------------------------|
| customerID       | Customer identification                            | Unique identifier (numbers & letters)         |
| gender           | Customer gender                                    | Female or Male                                |
| age             | Customer's age                                      | Numeric (years)                               |
| tenure           | Number of months the customer has been a member    | Numeric (0 to X months)                       |
| membership_type  | Type of membership                                 | Monthly, Quarterly, Annual                    |
| personal_training | Whether the customer has personal training        | Yes or No                                     |
| classes_attended | Number of classes attended per month               | Numeric                                       |
| contract_length  | Length of the contract                             | Monthly, Yearly, No contract                  |
| payment_method   | Preferred payment method                           | Credit Card, Bank Transfer, Cash              |
| monthly_fees     | Monthly membership fee                             | Numeric ($ or local currency)                 |
| total_spent      | Total amount spent at the gym                      | Numeric ($ or local currency)                 |
| churn           | Whether the customer has churned                    | Yes or No                                     |



# Project Terms & Jargon

- **Member**: A person who has an active gym membership.
- **Prospect**: A potential member who has shown interest in the gym but has not yet subscribed.
- **Churned Member**: A gym member who has canceled their membership.
- **Tenure**: The number of months a member has been active at the gym before churning.

# Business Requirements

As a Data Analyst, you are tasked with helping a gym chain predict customer churn and improve member retention. The gym wants actionable insights to:

- Identify key factors correlated with member churn.
- Predict whether a prospect will churn and estimate their tenure.
- Segment members into clusters to personalize retention strategies.

# Hypothesis and Validation

- **Members with low tenure are more likely to churn**
  - Validated through correlation analysis.
  
- **Members who visit less frequently are more likely to churn**
  - Verified using visit frequency data.
  
- **Members on short-term contracts have higher churn rates**
  - Confirmed via contract length analysis.
  
- **Members who joined through promotional offers have a higher churn risk**
  - Investigated through membership acquisition sources.

# Mapping Business Requirements to Data Analysis & ML Tasks

## Business Requirement 1: Data Exploration & Visualization

- Inspect gym membership data.
- Conduct correlation analysis on churn-related factors.
- Visualize churn trends based on tenure, visit frequency, contract type, and payment method.

## Business Requirement 2: Predictive Modeling & Clustering

- **Churn Prediction**: Build a classification model to predict if a member will churn.
- **Tenure Prediction**: Use regression to estimate how long a prospect will remain a member before churning.
- **Customer Segmentation**: Implement clustering to categorize members into different risk groups for churn prevention strategies.

# Machine Learning Models

## Predict Churn (Classification Model)

- **Goal**: Predict whether a member will churn based on historical data.
- **Success Metrics**:
  - 80% recall for churn prediction.
  - The model fails if false positives exceed 30%.
- **Training Data**:
  - **Features**: Age, contract type, payment method, visit frequency, tenure.
  - **Target**: Churn (1 = churned, 0 = active).

## Predict Tenure (Regression Model)

- **Goal**: Estimate how long a prospect will stay before churning.
- **Success Metrics**:
  - R² score of at least 0.7.
  - Model fails if predictions are off by 50% more than 30% of the time.
- **Training Data**:
  - **Features**: Age, contract type, membership type, attendance frequency.
  - **Target**: Tenure (in months).

## Customer Segmentation (Clustering Model)

- **Goal**: Group members into clusters based on churn risk.
- **Success Metrics**:
  - Silhouette score of at least 0.45.
  - Model fails if it suggests more than 15 clusters (too complex to interpret).
- **Training Data**:
  - **Features**: Age, visit frequency, contract type, membership type.
  - **Target**: Cluster assignment.

# Dashboard Design (Streamlit App UI)

## Page 1: Quick Project Summary

- **Project Overview**
- **Key Business Terms & Dataset Description**
- **Stated Business Requirements**

## Page 2: Member Churn Analysis

- **State Business Requirement 1**
- Data summary (number of members, key statistics)
- Correlation study (factors influencing churn)
- **Visualizations**:
  - Churn rates by membership type, tenure, visit frequency
  - Parallel plot showing relationships between churn and correlated features

## Page 3: Prospect Churn Predictor

- **State Business Requirement 2**
- Input widgets for a prospect’s profile (age, membership type, visit frequency, etc.)
- **"Run Predictive Analysis" button**:
  - Predict churn probability
  - Estimate tenure if the prospect is likely to churn
  - Identify the customer cluster the prospect belongs to

## Page 4: Hypothesis Validation

- Summary of validated hypotheses:
  - Churn vs tenure correlation
  - Impact of visit frequency on churn
  - Effect of contract type on churn likelihood

## Page 5: Churn Prediction Model

- Explanation of ML pipeline for churn prediction
- Feature importance ranking
- Model performance metrics

## Page 6: Tenure Prediction Model

- Explanation of ML pipeline for tenure prediction
- Feature importance ranking
- Model performance metrics

## Page 7: Customer Segmentation Analysis

- Explanation of clustering approach
- Silhouette plot for cluster validation
- Distribution of clusters across churn levels
- Percentage of churn risk in each cluster
- Key features defining each cluster profile
