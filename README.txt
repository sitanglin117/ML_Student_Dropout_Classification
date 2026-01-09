Machine Learning Project (Classification)
Multi-Class Classification Approach to Student Academic Success Prediction
=====================================================

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
