# Customer Churn Prediction Project

## Table of Contents (Optional but helpful for long READMEs)
* [Objective](#objective)
* [Data Source](#data-source)
* [Project Structure](#project-structure)
* [Setup Instructions](#setup-instructions)
* [Workflow](#workflow)
* [Results](#results)
* [Interpretation & Business Insights](#interpretation--business-insights)
* [Limitations](#limitations)
* [Future Work](#future-work)
* [Technologies Used](#technologies-used)


## Objective
To build a machine learning model that predicts customer churn for a telecom provider and identifies key drivers of churn using the IBM Telco Customer Churn dataset.

## Data Source
The dataset used is the **IBM Telco Customer Churn** dataset, obtained from Kaggle:
[https://www.kaggle.com/datasets/blastchar/telco-customer-churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

The raw data file (`WA_Fn-UseC_-Telco-Customer-Churn.csv`) is stored in the `data/raw/` directory (and excluded from Git version control via `.gitignore`).

## Project Structure
```plaintext
churn_prediction_project/
├── data/
│   └── raw/
│       └── WA_Fn-UseC_-Telco-Customer-Churn.csv (ignored by git)
├── venv/  # Virtual environment (ignored by git)
├── .git/
├── .gitignore
├── README.md
└── requirements.txt
```


## Setup Instructions
1.  **Clone the repository:**
    ```bash
    git clone <your-github-repo-url>
    cd churn_prediction_project
    ```
2.  **Create and activate a virtual environment:** (Recommend using Python 3.8+)
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # Linux/macOS
    # venv\Scripts\activate  # Windows
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **(If data isn't tracked by Git)** Download the dataset from the [Kaggle link](#data-source) and place `WA_Fn-UseC_-Telco-Customer-Churn.csv` into the `data/raw/` directory.

## Workflow
The key steps followed in the project:
1.  **Data Loading & Initial Exploration:** Loaded data, checked types, missing values, basic stats.
2.  **Data Cleaning:** Handled `TotalCharges` conversion, addressed missing values (if any), dropped irrelevant columns.
3.  **Exploratory Data Analysis (EDA):** Visualized distributions, explored relationships between features and churn using countplots, histograms, boxplots, bar plots (churn rate). Analyzed correlations.
4.  **Feature Engineering:** Created new features like `TenureGroup`, `NumOptionalServices`, `HasInternet_NoAddons` based on EDA insights.
5.  **Preprocessing:** Encoded categorical features (One-Hot Encoding) and scaled numerical features (StandardScaler). Split data into training and testing sets (stratified).
6.  **Modeling:**
    *   Established a baseline model (Logistic Regression).
    *   Trained an advanced model (Random Forest) using techniques to handle class imbalance (`class_weight='balanced'`).
7.  **Evaluation:** Compared models using relevant metrics for imbalanced classification (Precision, Recall, F1-Score for Churn class, AUC-ROC, AUC-PR) and Confusion Matrix.
8.  **Interpretation:** Used LIME to understand global feature importance and explain individual predictions.

## Results
# Model Performance Comparison

| Model               | Recall (Churn=1) | Precision (Churn=1) | F1-Score (Churn=1) | AUC-ROC | AUC-PR (Avg Precision) |
|---------------------|------------------|---------------------|--------------------|---------|------------------------|
| Logistic Regression | *Value from Task 9* | *Value from Task 9*  | *Value from Task 9* | *Value from Task 9* | *Value from Task 9*     |
| Random Forest       | *Value from RF Eval* | *Value from RF Eval*  | *Value from RF Eval* | *Value from RF Eval* | *Value from RF Eval*     |
| LightGBM            | *Value from LGBM Eval*| *Value from LGBM Eval*| *Value from LGBM Eval* |*Value from LGBM Eval*| *Value from LGBM Eval*   |


**Observations:**
* Compare the Recall for the Churn class - did the advanced models improve significantly over the baseline in catching churners?
* Compare the F1-scores for the Churn class.
* Compare AUC-ROC and especially AUC-PR scores.
* Which model seems to offer the best trade-off based on the project goals (e.g., prioritizing Recall vs. Precision)?
*   State which model performed best based on key metrics (e.g., "Random Forest significantly outperformed the baseline, particularly in Recall for the Churn class and AUC-PR score.").
*   Optionally, embed key plots like the confusion matrix or PR curve for the best model. (Upload images to GitHub repo, maybe in an `images/` folder, and link them: `![Confusion Matrix](images/confusion_matrix.png)`)

## Interpretation & Business Insights
*   **Summarize the findings from Task 15.**
*   List the **Key Drivers of Churn** identified by SHAP (e.g., Contract type, Tenure, Monthly Charges).
*   Describe the profile of a **High-Risk Customer**.
*   Present the **Actionable Business Recommendations** (e.g., Target Month-to-Month, Enhance Onboarding, Promote AutoPay).

## Limitations
*   Mention the **Correlation vs. Causation** limitation.
*   Discuss **Data Scope** limitations (based only on available features, external factors ignored).
*   Acknowledge the **Static Nature** of the model (needs retraining).

## Future Work
Suggest potential next steps:
*   Incorporate more data sources (e.g., customer support logs, satisfaction scores).
*   Experiment with other models or more advanced feature engineering.
*   Perform more rigorous Hyperparameter Tuning (e.g., using Optuna or Hyperopt).
*   Deploy the model as an API for real-time predictions.
*   Implement MLOps practices for monitoring and retraining.

## Technologies Used
*   Python 3.x
*   Pandas
*   NumPy
*   Scikit-learn
*   Matplotlib
*   Seaborn
*   LIME
*   Jupyter Notebooks

