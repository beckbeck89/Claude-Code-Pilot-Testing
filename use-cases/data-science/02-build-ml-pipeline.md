# Use Case: Build an ML Pipeline

## Objective

Ask the AI tool to build an end-to-end machine learning pipeline from data loading through model evaluation. Tests the tool's ML knowledge, best practices awareness, and ability to produce production-quality data science code.

## The Task

Build a complete ML pipeline for a **classification task** using the Titanic dataset (or a similar tabular classification dataset).

### Pipeline Should Include

1. **Data loading and exploration** (brief — not a full EDA)
2. **Feature engineering**: Create at least 2 new meaningful features
3. **Preprocessing**: Handle missing values, encode categoricals, scale numerics
4. **Train/test split**: Proper splitting with stratification
5. **Model training**: Train at least 2 different model types (e.g., Random Forest + Logistic Regression)
6. **Hyperparameter tuning**: Grid search or similar on at least one model
7. **Evaluation**: Accuracy, precision, recall, F1, confusion matrix, ROC curve
8. **Model comparison**: Clear comparison of the models with a recommendation

## Acceptance Criteria

- [ ] Pipeline runs end-to-end without errors
- [ ] No data leakage (preprocessing fit on train only, applied to test)
- [ ] At least 2 engineered features that are meaningful
- [ ] At least 2 model types compared
- [ ] Evaluation uses multiple metrics (not just accuracy)
- [ ] Results are clearly presented with visualizations
- [ ] Code follows sklearn patterns (Pipeline, ColumnTransformer, etc.)

## Suggested Prompt

> "Build a complete ML classification pipeline for the Titanic dataset. Include feature engineering, preprocessing, train at least two models, do hyperparameter tuning, and compare the models using multiple evaluation metrics. Follow sklearn best practices and avoid data leakage."

## What to Observe

- Does it use sklearn Pipeline/ColumnTransformer or do preprocessing manually?
- Does it avoid data leakage (a common AI coding tool mistake)?
- Are the engineered features genuinely useful or trivial?
- Does it explain the model choice and hyperparameter decisions?
- How does it handle class imbalance (if applicable)?
- Does it produce a clear model comparison at the end?
- Does it suggest next steps (feature importance, more models, deployment)?
