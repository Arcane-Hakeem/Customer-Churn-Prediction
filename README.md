## Customer Churn Prediction

An end-to-end Machine Learning project that predicts whether a telecom customer is likely to churn based on customer demographics, services, contract details, and billing information.

## Project Overview

Customer churn is an important business problem for subscription-based companies. Identifying customers who are likely to leave can help businesses take preventive retention actions.

This project builds a Machine Learning pipeline that:

- Cleans and preprocesses customer data
- Performs Exploratory Data Analysis (EDA)
- Compares multiple classification models
- Handles class imbalance
- Optimizes the classification threshold
- Predicts churn probability for new customers
- Provides an interactive Streamlit web application

## Dataset

The project uses the **IBM Telco Customer Churn dataset**.

The dataset contains customer information such as:

- Gender
- Senior citizen status
- Partner and dependents
- Tenure
- Phone and internet services
- Online security and support services
- Contract type
- Payment method
- Monthly charges
- Total charges

The target variable is:

```text
Churn
```

- `Yes` → Customer churned
- `No` → Customer stayed

## Exploratory Data Analysis

The project analyzes relationships between customer characteristics and churn, including:

- Churn distribution
- Contract type vs churn
- Tenure vs churn
- Monthly charges vs churn
- Internet service vs churn
- Online security and technical support
- Payment method vs churn
- Numerical feature correlations

Some important observations include:

- Customers with month-to-month contracts show higher churn.
- Customers with shorter tenure are more likely to churn.
- Electronic check customers show higher churn.
- Customers without online security or technical support show higher churn.
- Fiber optic customers show relatively higher churn.

> These findings represent associations in the dataset and should not be interpreted as causal relationships.

## Machine Learning Models

The following classification models were evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Balanced Logistic Regression

## Model Performance

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 80.55% | 65.72% | 55.88% | 60.40% | 84.21% |
| Decision Tree | 72.11% | 47.55% | 49.20% | 48.36% | 64.77% |
| Random Forest | 78.35% | 61.86% | 48.13% | 54.14% | 82.06% |
| Balanced Logistic Regression | 73.81% | 50.43% | 78.34% | 61.36% | 84.16% |

## Handling Class Imbalance

The dataset contains more customers who stayed than customers who churned.

To improve the detection of churn customers, **class-weighted Logistic Regression** was used.

This improved churn recall from:

```text
55.88% → 78.34%
```

Although accuracy and precision decreased, the model became much better at identifying customers who are actually likely to churn.

## Threshold Optimization

The default classification threshold of `0.50` was evaluated along with several alternative thresholds.

The selected threshold was:

```text
0.55
```

This threshold provided a better balance between precision and recall for the churn prediction use case.

### Final Model Performance

| Metric | Score |
|---|---:|
| Accuracy | 75.30% |
| Precision | 52.43% |
| Recall | 75.13% |
| F1 Score | 61.76% |
| ROC-AUC | 84.16% |

### Confusion Matrix

```text
[[780, 255],
 [ 93, 281]]
```

Where:

- **True Negatives:** 780
- **False Positives:** 255
- **False Negatives:** 93
- **True Positives:** 281

The model identifies a large proportion of customers who are likely to churn, making it useful for prioritizing customer retention efforts.

## Feature Insights

Important features associated with churn in the Logistic Regression model include:

### Higher Churn Association

- Month-to-month contracts
- Fiber optic internet service
- Electronic check payment method
- Lack of online security
- Lack of technical support
- Shorter customer tenure

### Lower Churn Association

- Two-year contracts
- Longer customer tenure
- DSL internet service
- Customers with dependents

> Logistic Regression coefficients represent associations within the model and should not be interpreted as proof of causation.

## Streamlit Application

The project includes an interactive **Streamlit** web application.

Users can enter customer information such as:

- Demographics
- Tenure
- Internet services
- Security and support services
- Contract type
- Payment method
- Monthly charges
- Total charges

The application returns:

- **Churn Probability**
- **Prediction**
- **Likely to Churn / Likely to Stay**

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib
- Streamlit

## Project Structure

```text
Customer-Churn-Prediction/
│
├── Customer_Churn_Prediction.ipynb
├── app.py
├── customer_churn_model.pkl
├── churn_threshold.pkl
├── requirements.txt
├── .gitignore
└── README.md
```

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Arcane-Hakeem/Customer-Churn-Prediction.git
```

### 2. Navigate to the project

```bash
cd Customer-Churn-Prediction
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit application

```bash
streamlit run app.py
```

The application will open in your browser.

## 🔮 Future Improvements

- Hyperparameter tuning
- Cross-validation
- XGBoost / LightGBM comparison
- SHAP-based model explainability
- Model deployment
- Customer retention recommendation system
- Automated model monitoring

## Author

**Hakeem Shaik**

Computer Science Engineering | AI & Machine Learning

---

⭐ If you find this project useful, feel free to explore the repository and give it a star!
