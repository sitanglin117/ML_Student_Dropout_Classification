Machine Learning Project (Classification)
Multi-Class Classification Approach to Student Academic Success Prediction
=====================================================

During this group project(classification and regression), several revisions and improvements were proposed to better align the work with the course objectives. However, these suggestions were not adopted, resulting in a final outcome that differed from my original expectations. This note is provided to supplement my individual contributions and learning process, and I respectfully request individual consideration during evaluation.

Author:
- Si Tang Lin

-----------------------------------------------------
1. Environment
-----------------------------------------------------

- Python version: 3.10
- Tested on: Python 3.10.x
- Operating systems: Linux / macOS / Windows

-----------------------------------------------------
2. Setup Instructions
-----------------------------------------------------

1. Create a virtual environment (recommended):
   python3.10 -m venv

2. Activate the virtual environment:
   - Linux / macOS:
     source venv/bin/activate
   - Windows:
     venv\Scripts\activate

3. Install required packages:
   pip install -r requirements.txt

-----------------------------------------------------
3. Reproducibility
-----------------------------------------------------

- Random seeds are fixed to ensure reproducible results.
- All preprocessing steps are included in the code.

-----------------------------------------------------
4. Project Overview
-----------------------------------------------------

This project addresses a **multi-class classification problem** which aimed at predicting student academic outcomes. Its goal is to explore data preprocessing, model selection, evaluation and interpretation.

-----------------------------------------------------
5. Dataset Description
-----------------------------------------------------

Dataset name: Predict Students' Dropout and Academic Success
Source: UCI Machine Learning Repository

Number of instances: 4424
Number of features: 36

Feature types: Real, Categorical, Integer
Task type: Classification
Subject area: Social Science

-----------------------------------------------------
6. Data Preprocessing
-----------------------------------------------------

- Data splitting into train/validation/test
- Variable typing: Restore to original data type
- Feature assessment: Near Zero Variance to remove little predicted power and chi-square method to test the association between two variable.
- PCA to reduce collinearity variables
- Preprocess for numerical and numerical features separately
-- Kruskal–Wallis test tests whether the distributions of a numerical variable differ significantly across multiple target classes.
-- For modeling purpose no scaling applied
-- Cramér’s V, measure of association between two categorical variables.
-- Encoded - Target encoding for high-cardinality variable
           - One-hot encoding for low-cardinality nominal variables
           - Numerical variables are passed through unchanged
- EDA

-----------------------------------------------------
7. Ethical consideration
-----------------------------------------------------

Potential ethical concerns include:
- Bias in historical academic data
- Risk of unfair labeling of students
- Misuse of predictions without human oversight


-----------------------------------------------------
8. Model use + Class Imbalance Handling
-----------------------------------------------------

- Gradient Boosting + Undersampling
- XGBoost with sample weighting
- Random Forest with class weighting
- XGBoost with early stopping

-----------------------------------------------------
9. Evaluation Metrics
-----------------------------------------------------

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score

Metrics were chosen to account for class imbalance and to better
evaluate model performance beyond accuracy alone.

-----------------------------------------------------
10. Results Summary
-----------------------------------------------------

In this project, a multi-class classification approach was applied to predict
students’ academic outcomes using a real-world higher education dataset.

Several machine learning models were explored and compared, including Gradient
Boosting, Random Forest, and XGBoost. Special attention was given to handling
class imbalance through undersampling, class weighting, and sample weighting
strategies. The experimental results indicate that **XGBoost with imbalance-aware techniques**, achieved
balanced performance across all outcome classes.

Future work could include incorporating additional features, applying more
advanced imbalance handling techniques, or exploring interpretable models to
better understand the factors influencing student outcomes.


-----------------------------------------------------
11. Error Analysis
-----------------------------------------------------

Most misclassifications occurred between outcome categories with similar academic
profiles. Suggesting overlapping feature distributions and highlights the
difficulty of predicting academic success based solely on historical data.

-----------------------------------------------------
12. Bibliography
-----------------------------------------------------
https://dl.acm.org/doi/10.1145/2939672.2939785

https://christophm.github.io/interpretable-ml-book/

https://dl.acm.org/doi/10.1145/3287560.3287596

https://ieeexplore.ieee.org/abstract/document/5128907
-----------------------------------------------------
13. Code Structure
-----------------------------------------------------

- machine learning-classification.ipynb
- machine learning-classification.html
  Main notebook containing preprocessing, model training, and evaluation.

- requirements.txt
  List of required Python packages.

- readme.txt
  Project documentation.
------------------------------------------------------------------------------------------------

Machine Learning Regression Project: Predicting Calories Burned

Overview

This project applies several machine learning regression models to predict **Calories Burned** using activity and environmental data collected from wearable devices. Calories burned are used as a proxy for physical stress during daily activities.

The goal is to compare the performance of multiple regression algorithms and identify which factors most significantly influence caloric expenditure.

Problem Statement

The objective is to use wearable device and environmental data to predict **Calories Burned** during daily activities. This is framed as a **regression problem** because the target variable is continuous.

Accurate calorie prediction can help improve:
- Activity tracking
- Fitness recommendations
- Personalized health insights

Dataset

The dataset contains **10,000 observations** collected from wearable devices and environmental sensors.

Features

**Physical Activity Metrics:**
- Steps
- Distance Covered
- Exercise Duration

**Exercise Context:**
- Exercise Type
- Exercise Intensity

**Environmental Conditions:**
- Ambient Temperature
- Altitude
- UV Exposure

**Device Status:**
- Battery Level

Target Variable

- Calories_Burned (continuous)

Data Characteristics

- The dataset includes both numerical and categorical variables
- Some activity-related variables contain missing values (treated as "Unknown" category)
- Calories burned are approximately uniformly distributed across 0-1,000 calories
- No severe skewness or extreme outliers present

Models Implemented

The project evaluates five different regression approaches:

1. **Linear Regression (Baseline)**
   - Achieves near-perfect performance with R² ≈ 1.0
   - Indicates strong linear relationship between predictors and target

2. **Decision Tree Regression**
   - Captures non-linear relationships
   - Performs comparably to linear regression

3. **Random Forest Regression**
   - Ensemble of 200 trees
   - Excellent generalization and stability
   - Marginal improvement over simpler models

4. **Tuned Random Forest Regression**
   - Hyperparameter optimization via GridSearchCV
   - No significant improvement over default configuration

5. **Gradient Boosting Regression**
   - High R² score but slightly higher RMSE than Random Forest
   - Suggests boosting is less suited for this dataset

6. **Neural Network (MLP Regressor)**
   - Two hidden layers (64, 32 units)
   - Exceptional performance after feature scaling
   - Does not outperform simpler models

Evaluation Metrics

- **Root Mean Squared Error (RMSE)**: Measures average prediction error magnitude
- **R² Score**: Measures proportion of variance explained (range: 0-1)

Key Results

All models achieved **exceptionally high predictive performance**:
- R² values extremely close to 1.0 across all models
- Very small RMSE values
- Consistent performance suggests highly predictable target variable

Feature Importance Analysis

Feature importance reveals clear priorities:

1. **Distance Covered** - Dominant predictor
2. **Steps** - Second most important feature
3. **Environmental factors** - Minimal contribution once movement variables included

**Interpretation:** Caloric expenditure is directly linked to physical movement. Environmental factors play a secondary role, explaining why simpler models perform as well as complex ones.

Methodology

Data Preprocessing

1. **Remove identifiers**: User_ID and Timestamp removed as non-predictive
2. **Handle missing values**: Missing categories treated as "Unknown"
3. **Encode categorical variables**: One-hot encoding for Exercise_Type and Exercise_Intensity
4. **Train/test split**: 80% training (8,000 samples), 20% testing (2,000 samples)
5. **Feature scaling**: Standardization applied for neural network (tree-based models are scale-invariant)

Model Training

- Fixed random seed (42) for reproducibility
- All models evaluated on identical train/test split
- Cross-validation (5-fold CV) used for hyperparameter tuning

Error Analysis

Residual Analysis

- No clear systematic patterns detected
- Residuals randomly scattered around zero
- No evidence of bias or heteroscedasticity
- Errors appear independent and evenly distributed

Actual vs. Predicted

- Points tightly clustered along diagonal line
- Excellent agreement across full range of calorie values
- Visual confirmation of strong predictive accuracy

Important Limitations

Target Leakage Concern

The exceptionally high performance may indicate **target leakage**:
- Steps and Distance are closely tied to how calories are computed in practice
- Models may be learning near-direct representations rather than generalizable patterns
- Performance may be lower with incomplete or noisy activity data

Generalizability

- Models trained on this dataset may not generalize to:
  - Different user populations
  - Different activity contexts
  - Scenarios with incomplete activity measures

Installation & Usage

Requirements

pip install -r requirements.txt

**Key dependencies:**
- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn

Running the Analysis

python Machine\ Learning\ Regression.py

Or run the Jupyter notebook:
jupyter notebook "Wearables Project For Regression Analysis.ipynb"

Reproducibility

- All models use fixed random seed (SEED = 42)
- Package versions specified in requirements.txt
- Data preprocessing and feature engineering documented in notebook

Ethical Considerations

⚠️ **Important Disclaimers:**

- **Educational Purpose Only**: This project is for learning and research purposes
- **Not for Medical Diagnosis**: Predictions should never be used for medical or psychological diagnosis
- **Data Privacy**: Wearable data may contain sensitive health information requiring informed consent
- **Bias Awareness**: Data collection may reflect demographic and behavioral biases
- **Fairness**: Consider fairness implications when applying to diverse populations
- **Ethical Use**: Respect user privacy and follow data protection regulations

Conclusions

Key Findings

1. **Strong Predictability**: Calories burned are highly predictable given available features
2. **Simpler is Better**: Linear Regression performs as well as complex models
3. **Movement Dominates**: Steps and Distance are far more important than environmental factors
4. **Model Consistency**: All models achieved similar high performance

Recommendations

1. **Model Selection**: Prefer Linear Regression or Random Forest for interpretability and performance balance
2. **Feature Engineering**: Focus on accurate measurement of movement-related features
3. **Further Investigation**: Explore models using only indirect predictors to improve generalizability
4. **Validation**: Test on external datasets and diverse user populations

Future Work

- Explore models relying on indirect predictors (environmental conditions, activity type, physiological signals)
- Incorporate more diverse user demographics
- Test performance across different activity contexts
- Evaluate generalization on external datasets
- Investigate causes of target leakage
- Develop calibrated models for real-world deployment

References

Géron, A. (2022). *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow* (3rd ed.). O'Reilly Media.

James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). *An Introduction to Statistical Learning* (2nd ed.). Springer.

---

**Project Status**: Complete  
**Last Updated**: January 2026  
**Dataset**: 10,000 observations from wearable devices and environmental sensors


