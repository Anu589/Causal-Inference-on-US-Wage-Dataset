# Causal Inference on US Wage Dataset

## Project Overview
This project analyzes the US wage dataset using causal inference and machine learning techniques. The goal is to understand the causal effect of **gender (sex)** on wages while controlling for education, experience, occupation, industry, and region.

---

## Dataset
- Source: [CausalAIBook GitHub](https://raw.githubusercontent.com/CausalAIBook/MetricsMLNotebooks/main/data/wage2015_subsample_inference.csv)  
- Number of rows: 5,150  
- Key variables:  
  - **wage** – Raw wage/salary  
  - **lwage** – Log of wage  
  - **sex** – Gender indicator  
  - **Education categories:** shs, hsg, scl, clg, ad  
  - **Region dummies:** mw, so, we, ne  
  - **Experience terms:** exp1, exp2, exp3, exp4  
  - **Occupation/Industry codes:** occ, occ2, ind, ind2  

---

## Methods

### Feature Engineering
- Combined occupation (`occ`, `occ2`) and industry (`ind`, `ind2`) into broader categories.
- Created an overall **education** variable (1–5 scale).
- Created **region** and **occupation** labels based on dummy indicators.
- Built design matrix with **pairwise interactions** and **sex-specific interactions** using Patsy.

### Machine Learning Models
- **LassoCV** – L1 regularized regression  
- **RidgeCV** – L2 regularized regression  
- **ElasticNetCV** – Combination of L1 & L2  
- **Double Lasso** – Selected treatment and outcome variables using Lasso, followed by linear regression

### Evaluation Metrics
- **R² (Coefficient of Determination)**  
- **MAE (Mean Absolute Error)**  
- **RMSE (Root Mean Squared Error)**  
- **MAPE (%)**  

---

## Key Results

### R² Scores
| Model         | R²        |
|---------------|-----------|
| Lasso         | 0.294737  |
| Ridge         | 0.301882  |
| ElasticNet    | 0.294746  |
| Double Lasso  | 0.292639  |

### Causal Estimate
- Using DoWhy backdoor linear regression: **Causal effect of sex on wage:** -3.072  
- Placebo refutation: p-value = 0.9 (not significant under placebo)

---

## Visualizations
- Coefficients plots for Lasso, Ridge, ElasticNet, and Double Lasso  
- Wage vs Experience by gender  
- Propensity score distribution by gender  

*(Add saved plots as images to the repo and reference them here.)*

---

## How to Run the Code
1. Clone the repository:
```bash
git clone https://github.com/Anu589/Causal-Inference-on-US-Wage-Dataset.git
```

## Install Dependencies
```bash 
pip install -r requirements.txt```
