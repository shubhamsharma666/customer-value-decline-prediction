# Customer Value Decline Prediction using Machine Learning

## Overview

Developed an end-to-end machine learning solution to identify customers at risk of future revenue decline using historical transaction data.

The project leverages rolling customer snapshots, behavioral feature engineering, and predictive modeling to detect declining customer value before significant revenue loss occurs.

## Business Problem

Customer value decline rarely happens suddenly. It is often preceded by changes in purchasing behavior such as reduced spending, lower purchase frequency, and increasing time gaps between orders.

The objective of this project is to predict future customer revenue decline early enough to support proactive customer retention strategies.

## Dataset

* Dataset: Online Retail II
* 1,067,371 transaction records
* Customer-level purchase history
* Time-based feature engineering framework
* Rolling observation and prediction windows

## Project Architecture

```text
Raw Transactions
      ↓
Data Cleaning
      ↓
Rolling Snapshot Creation
      ↓
Feature Engineering
      ↓
Target Engineering
      ↓
Model Training
      ↓
Model Evaluation
      ↓
Business Insights
```

## Methodology

### 1. Customer Snapshot Generation

Created rolling customer snapshots to capture customer behavior at multiple points in time.

### 2. Feature Engineering

#### RFM Features

* Recency
* Frequency
* Monetary Value
* Average Order Value (AOV)

#### Trend Features

* Spend Trend
* Frequency Trend
* AOV Trend

#### Customer Lifecycle Features

* Customer Age

#### Gap Features

* Average Gap Between Orders
* Maximum Gap Between Orders
* Gap Variability

### 3. Target Engineering

Future customer revenue was calculated using a forward-looking prediction window.

Customers experiencing significant future revenue reduction were labeled as decline cases.

### 4. Model Development

The following models were evaluated:

* Logistic Regression
* Random Forest
* Random Forest + Gap Features
* XGBoost

## Results

| Model                        | ROC-AUC |
| ---------------------------- | ------- |
| Logistic Regression          | 68.43%  |
| Random Forest                | 75.84%  |
| Random Forest + Gap Features | 78.68%  |
| XGBoost                      | 77.00%  |

## Final Model

### Selected Model: Random Forest + Gap Features

Performance Metrics:

* Accuracy: 71.25%
* F1 Score: 72.51%
* ROC-AUC: 78.68%

## Key Insights

* Purchase gap behavior emerged as one of the strongest predictors of future customer value decline.
* Customers with increasing intervals between purchases were significantly more likely to reduce future spending.
* Gap-based behavioral signals improved predictive performance beyond traditional RFM metrics.
* Combining behavioral trends with purchase gap features produced the highest model performance.

## Top Predictive Features

* Recency
* Average Gap Between Orders
* Maximum Gap Between Orders
* Monetary Value
* Frequency Trend

These features contributed most to identifying customers at risk of future value decline.

## Technology Stack

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* Matplotlib
* Jupyter Notebook

## Repository Structure

```text
customer-revenue-decline-prediction/

├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│
├── models/
│
├── outputs/
│
├── reports/
│
└── README.md
```

## Business Impact

This solution can be used as an early warning system for customer retention initiatives. By identifying customers at risk of future value decline, businesses can launch targeted interventions, reduce revenue loss, and improve customer lifetime value.
