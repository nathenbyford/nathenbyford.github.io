---
layout: project
title: "Healthcare Analytics Dashboard"
subtitle: "Predicting Patient Readmission Rates"
tech: [R, Shiny, Random Forest, PostgreSQL]
icon: "fas fa-heartbeat"
github: "https://github.com/yourusername/healthcare-analytics"
demo: "https://healthcare-dashboard.shinyapps.io/demo/"
date: 2024-12-15
excerpt: "Built a comprehensive analytics platform for a regional hospital system to predict patient readmission rates using machine learning and statistical modeling."
---

# Healthcare Analytics Dashboard

This project involved building a comprehensive analytics platform for a regional hospital system to predict patient readmission rates using machine learning and statistical modeling.

## Problem Statement

Hospital readmissions within 30 days are a key quality metric and significant cost driver. The hospital system needed:

- Accurate prediction of high-risk patients
- Actionable insights for intervention strategies
- Real-time monitoring dashboard for clinical staff

## Methodology

### Data Collection
- Electronic Health Records (EHR) data
- 50,000+ patient records over 3 years
- 150+ clinical variables including demographics, diagnoses, procedures, and vital signs

### Feature Engineering
- Created composite risk scores
- Temporal features (length of stay, time since last admission)
- Interaction terms between key clinical indicators

### Model Development
1. **Exploratory Data Analysis**: Identified key risk factors
2. **Feature Selection**: Used LASSO regression for variable selection
3. **Model Training**: Compared Random Forest, XGBoost, and Logistic Regression
4. **Model Validation**: 5-fold cross-validation with temporal splits

## Results

- **Model Performance**: AUC of 0.82 on test set
- **Clinical Impact**: 15% reduction in readmissions through targeted interventions
- **Cost Savings**: Estimated $2.3M annual savings

## Dashboard Features

The Shiny dashboard includes:
- Real-time risk scoring for admitted patients
- Interactive visualizations of risk factors
- Historical trend analysis
- Customizable alerts for high-risk patients

## Technical Implementation

```r
# Example model training code
library(randomForest)
library(caret)

# Train Random Forest model
rf_model <- randomForest(
  readmission_30d ~ ., 
  data = train_data,
  ntree = 500,
  mtry = sqrt(ncol(train_data) - 1),
  importance = TRUE
)

# Evaluate performance
predictions <- predict(rf_model, test_data, type = "prob")[,2]
auc_score <- auc(test_data$readmission_30d, predictions)
```

## Lessons Learned

1. **Domain Expertise**: Close collaboration with clinicians was crucial for feature engineering
2. **Data Quality**: Significant effort required for cleaning and standardizing EHR data
3. **Interpretability**: Model explainability was as important as performance for clinical adoption

## Future Work

- Integration with hospital's EHR system
- Expansion to other outcome measures (mortality, length of stay)
- Implementation of federated learning across hospital networks