# Predicting Student Health 🩺📊

## Overview

This project uses machine learning to predict student health conditions from health-related and lifestyle features. The goal is to build a multiclass classification model that identifies health-condition categories using patterns in the available data.

Using Python, feature engineering, class weighting, and LightGBM, the notebook develops a predictive pipeline and generates predictions for the competition test dataset.

**Reported model score: 0.89228 (89%)**

## Objectives

- Explore and prepare the training and test datasets.
- Engineer meaningful features from health and lifestyle measurements.
- Address class imbalance using balanced sample weights.
- Train a multiclass classification model using LightGBM.
- Tune hyperparameters using Optuna.
- Evaluate model performance using stratified cross-validation.
- Generate predictions and export a submission file.

## Technologies Used

- **Python** — primary programming language
- **Pandas & NumPy** — data manipulation and numerical computation
- **LightGBM** — gradient-boosting classification
- **Scikit-learn** — preprocessing, stratified cross-validation, label encoding, and evaluation metrics
- **Optuna** — hyperparameter optimization
- **Kaggle** — notebook execution and competition dataset

## Machine Learning Approach

### 1. Data Preparation

The notebook loads the training, test, and sample submission datasets. The target variable is `health_condition`, which is encoded into numerical labels for model training.

### 2. Feature Engineering

Additional features are created to capture relationships between health and lifestyle measurements, including:

- Activity per minute
- Calories per step
- Water intake relative to BMI
- Sleep duration combined with BMI
- Heart rate relative to sleep duration
- BMI squared
- Exercise and hydration ratios
- BMI and heart-rate buckets

These engineered features provide the model with additional representations of the original data.

### 3. Handling Class Imbalance

The notebook calculates class weights from the training-label distribution and applies sample weights during model fitting. This helps reduce the influence of majority classes and encourages the model to learn from underrepresented classes.

### 4. Model Training and Optimization

A LightGBM multiclass classifier is trained using stratified cross-validation. Optuna searches for suitable hyperparameters, including learning rate, tree depth, number of leaves, and regularization settings.

The notebook also tests prior-adjusted class probabilities to improve balanced classification performance.

### 5. Evaluation

The notebook evaluates predictions using **balanced accuracy**, alongside confusion-matrix analysis. It compares ordinary probability-based predictions with prior-adjusted predictions to assess performance across the different classes.

The reported score of **0.89228** represents the result achieved during the project. The exact metric should be confirmed against the notebook output before interpreting it as ordinary accuracy or balanced accuracy.

### 6. Prediction and Submission

The trained cross-validation models generate averaged probabilities for the test dataset. Final predictions are converted back into the original health-condition labels and exported to `submission.csv`.

## Results

- **Reported score:** 0.89228
- **Model:** LightGBM multiclass classifier
- **Validation strategy:** Five-fold stratified cross-validation for the main training stage
- **Optimization:** Optuna hyperparameter search
- **Feature engineering:** Derived numerical ratios, interactions, and health-related buckets
- **Output:** `submission.csv` containing predicted health-condition labels

## Key Learnings

Through this project, I explored:

- Building an end-to-end machine learning classification pipeline.
- Engineering features from domain-related measurements.
- Managing imbalanced classes using sample weights.
- Applying stratified cross-validation.
- Tuning gradient-boosting models.
- Evaluating multiclass predictions with balanced accuracy and confusion matrices.
- Generating competition-ready prediction files.

## Future Improvements

- Increase the number of Optuna trials to explore a wider hyperparameter space.
- Compare LightGBM against CatBoost and XGBoost.
- Analyze class-specific precision, recall, and F1-scores.
- Inspect feature importance and use explainability methods to understand model behavior.
- Validate the final model on an independent holdout set.

## Conclusion

This project demonstrates an end-to-end approach to multiclass machine learning, from data preparation and feature engineering to model optimization, evaluation, and prediction generation.

It strengthened my practical experience with Python, LightGBM, feature engineering, cross-validation, and model evaluation.

**Disclaimer:** This is a machine learning prediction project for educational and experimental purposes. Its predictions should not be used as medical diagnoses or as a substitute for professional healthcare advice.
